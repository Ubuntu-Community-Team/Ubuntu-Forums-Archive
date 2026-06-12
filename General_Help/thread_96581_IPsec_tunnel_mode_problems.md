---
title: "IPsec tunnel mode problems"
date: 2005-11-29
forum: General Help
---

### Post by mk1970 on 2005-11-29
I'm having problems with manually confgured IPsec tunnel. Here's what I've tried so far:
```
# echo 1 > /proc/sys/net/ipv4/ip_forward
# iwconfig eth1 essid XXX
# ifconfig eth1 10.0.0.254 netmask 255.255.255.0 up
# route add default gw 10.0.0.1
# setkey -f /etc/ipsec.conf

```
The ipsec.conf file looks like this:
```
flush;
spdflush;

# SA
add     10.0.0.254 10.0.0.1 esp 1001
        -E rijndael-cbc "0x111111111111111111111111111111"
        -A hmac-sha1 "xxxxxxxxxxxxxxxxxxxx";
add     10.0.0.1 10.0.0.254 esp 1002
        -E rijndael-cbc "0x111111111111111111111111111111"
        -A hmac-sha1 "xxxxxxxxxxxxxxxxxxxx";

# SPD
spdadd  10.0.0.254 10.0.0.1   any -P out none;
spdadd  10.0.0.1   10.0.0.254 any -P in  none;
spdadd  10.0.0.254 0.0.0.0/0  any -P out
        ipsec esp/tunnel/10.0.0.254-10.0.0.1/require;
spdadd  0.0.0.0/0  10.0.0.254 any -P in
        ipsec esp/tunnel/10.0.0.1-10.0.0.254/require;
```
This is how my routing table looks like:
```
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
```
Now, if I try to ping 10.0.0.1 it works just fine because the policy says "none". But if I ping anything behind the default gateway it fails. If I then flush the IPsec SA and SPD databases it works just fine. 
```
# ping 192.168.0.65
connect: No such process

# setkey -F
# setkey -FP
# ping 192.168.0.65
PING 192.168.0.65 (192.168.0.65) 56(84) bytes of data.

```
Any ideas why I get that "No such process" error? The same ipsec.conf works fine when using it on my NetBSD laptop so the other end (10.0.0.1) is configured correctly (SPIs, keys etc).

---

### Post by mk1970 on 2005-12-21
The manual page for setkey says this:
```
    add [-46n] src dst protocol spi [extensions] algorithm ... ;
...
     extensions
             take some of the following:
             -m mode     Specify a security protocol mode for use.  mode is
                         one of following: transport, tunnel, or any.  The
                         default value is any.
```
The "-m any" setting does not work (at least with ipsec-tools 0.6-1ubuntu1.1) and you can't ignore the "-m mode" setting as it defaults to "any" so you really should specify "tunnel" as the mode. As a summary, the configuration file should look like this.
```
flush;
spdflush;

# SA
add     10.0.0.254 10.0.0.1 esp 1001
        [COLOR="Red"]-m tunnel[/COLOR]
        -E rijndael-cbc "0x111111111111111111111111111111"
        -A hmac-sha1 "xxxxxxxxxxxxxxxxxxxx";
add     10.0.0.1 10.0.0.254 esp 1002
        [COLOR="Red"]-m tunnel[/COLOR]
        -E rijndael-cbc "0x111111111111111111111111111111"
        -A hmac-sha1 "xxxxxxxxxxxxxxxxxxxx";

# SPD
spdadd  10.0.0.254 10.0.0.1   any -P out none;
spdadd  10.0.0.1   10.0.0.254 any -P in  none;
spdadd  10.0.0.254 0.0.0.0/0  any -P out
        ipsec esp/tunnel/10.0.0.254-10.0.0.1/require;
spdadd  0.0.0.0/0  10.0.0.254 any -P in
        ipsec esp/tunnel/10.0.0.1-10.0.0.254/require;
```

---

