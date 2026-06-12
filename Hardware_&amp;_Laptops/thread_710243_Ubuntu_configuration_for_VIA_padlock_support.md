---
title: "Ubuntu configuration for VIA padlock support"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by rawphi on 2008-02-28
How do you configure your Ubuntu on VIA's EPIA platforms?  I would like to offload the major encryption users (openssl and kernel) to the builtin padlock engine, but information is a bit thin on this topic ;) Please comment this post if you know some tricks I don't!

(Note: I did the tests using a standard Ubuntu 7.10 server install on a board with VIA's C7 CPU, 1.5GHz, 2GB DDR2 533 RAM)

[SIZE="4"]cipher/hash kernel modules[/SIZE]
the appropriate kernel modules for padlock's cipher and hash algortihms are not loaded automatically, which are:
```

modprobe padlock_aes padlock_sha

```
you can put them into /etc/modules as they are always available anyway, but the Right thing(r) would probably be a udev script to load them automatically if a C3/C7 cpu is present

[SIZE="4"]/dev/hwrng, /dev/random[/SIZE]
Also, the Random Number Generator is not used by default. one needs to load the kernel module for VIA's builtin RNG:
```

modprobe via_rng

```
or put it into /etc/modules. This module (& udev) gives you /dev/hwrng, which you can use to spice up /dev/random with entropy:
```

apt-get install rng-tools

```
This will install rngd, which checks the randomness of hwrng data and forwards them into the kernel's pseudo-RNG. Maybe you want to set the options in /etc/default/rng-tools to:
```

RNGDOPTIONS="--hrng=via"

```
Try out creating keys with ssh-keygen, dnssec, openssl certificate generation, pgp keys.. you're gonna love the speed :)

[SIZE="4"]openssl library[/SIZE]
This is the main issue. almost everything including the kitchen sink and ssh uses openssl for encryption.
It seems that padlock engine support is built in in gutsy, but not used by default:
for a test you can run: 
 openssl speed -evp aes-128-cbc 
 openssl speed -evp aes-128-cbc -engine padlock
The -evp tells openssl to use the high-level EVP routines instead of the low-level ones. Without, padlock can't accelerate.
Here are the results on my machine:
```

type             16 bytes     64 bytes    256 bytes   1024 bytes   8192 bytes
aes-128-cbc      15248.87k    20421.21k    22403.33k    22971.39k    23167.74k    (default)
aes-128-cbc      71636.51k   239605.20k   570536.96k   876639.38k  1029400.77k    (padlock engine)

```
It's a pity it isn't used by default, given the 5-50x speed increase ;)

I tried out the engine configuration of openssl.conf, but didn't succeed. One way is to patch openssl with the  [patch]("http://www.logix.cz/michal/devel/padlock/contrib/openssl-0.9.8e-engine.diff") from [ here]("http://www.logix.cz/michal/devel/padlock/index.xp"). 
(Note: haven't tried the patch on ubuntu's package yet.)

Of course, I could patch openssl myself and use the package, but then I would lose the distro update/maintenance convenience. Which, given the importance of openssl, is a bad thing.


[SIZE="4"]openssh[/SIZE]
openssh uses openssl for encryption, and the default is aes-128-cbc, which should be ok
so I probably just need to set the preferred ciphers to something padlock supports. currently, a quick check with:
```

dd if=/dev/zero count=50 bs=1M | ssh -c aes128-cbc localhost "cat >/dev/null"

```
gives me:
52428800 bytes (52 MB) copied, 4.79563 seconds, 10.9 MB/s  (AMD athlon XP 1700 for reference)
52428800 bytes (52 MB) copied, 7.23772 seconds, 7.2 MB/s  (VIA C7 1.5GHz)
Well, sems like padlock engine isn't used by ssh too, by default. :/

[SIZE="4"]Other stuff[/SIZE]
what else? didn't check out disk encryption, ipsec, openvpn configuration. However, those are all kernel-level things, so this should be fairly easy as long as the padlock modules are loaded.

---

### Post by Duncan Pierce on 2008-03-04
Thanks for a great post - it saved me loads of time.

I've spent a painful couple of hours reading OpenSSL docs and source and come up with the following. This needs to be added to your /etc/ssl/openssl.cnf near the top before any of the named sections [like_this] start:

```
openssl_conf = openssl_def

[openssl_def]
engines = openssl_engines

[openssl_engines]
padlock = padlock_engine

[padlock_engine]
default_algorithms = ALL
```

When I run:

```
openssl speed -evp aes-128-cbc
```

Before I make this config change I get:

```
type             16 bytes     64 bytes    256 bytes   1024 bytes   8192 bytes
aes-128-cbc      11615.79k    15490.05k    16981.01k    17469.86k    17569.17k
```

After I make it I get:

```
type             16 bytes     64 bytes    256 bytes   1024 bytes   8192 bytes
aes-128-cbc      57916.77k   191760.36k   457728.09k   708649.86k   838235.94k
```

---

### Post by Duncan Pierce on 2008-03-04
My previous post doesn't seem to get me faster SSH. I guess the SSH I have on Ubuntu 7.10 does not use OpenSSL's  EVP functions - perhaps it's directly calling the non-overridable low-level OpenSSL software-based AES functions.

But maybe it will help someone make some more progress on this.

---

### Post by rawphi on 2008-03-06
thanks Duncan for the openssl.conf snippet. It also works on my via :) One more clarification: you need to insert the snippet BEFORE any [section] but AFTER the "general configuration options:

```

"# Extra OBJECT IDENTIFIER info:
#oid_file               = $ENV::HOME/.oid
oid_section             = new_oids

#enable padlock engine by default:
openssl_conf = openssl_def

[openssl_def]
engines = openssl_engines

[openssl_engines]
padlock = padlock_engine

[padlock_engine]
default_algorithms = ALL
#end of crazy configfile syntax

[ new_oids ]


```

**ok, so the quest continues:**

It seems that ssh and openssl are using the libcrypto library instead of libssl (which are both part of the openssl source). As I currently understand, openssl can be configured via the configfile, but programs like ssh don't care about the underlying engine (damn right so!). Unfortunately this is not the view of the openssl developers who explicitely state that every application should select the appropriate engine. I'm currently trying to patch libcrypto the same way as the libssl patch , to enable padlock engine by default for any sw using it.

I also found out that mozilla.org has it's own encryption lib, called NSS, "Network Security Service". Haven't had time yet to check for padlock support there, and it's low on my priorit list (my via board is a server, after all)

---

### Post by toojays on 2008-04-19
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/119295](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/119295) is a bug about getting OpenSSH to use Padlock.

---

