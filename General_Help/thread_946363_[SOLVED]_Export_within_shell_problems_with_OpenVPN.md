---
title: "[SOLVED] Export within shell problems with OpenVPN"
date: 2008-10-13
forum: General Help
---

### Post by sickanimations on 2008-10-13
I'm new to Linux and I know that there's an attitude that we should solve our own problems but I really can't progress any further.

After installing OpenVPN there's some configuring to do - which I've done before on the ... windows platform *ducks*. 

It seems pretty straightforward. All I need to do is run a script (or shell?) that 'exports' a bunch of variables so it can make some keys.

Problem: 
I use ./vars to execute the shell(?)

Here's a bit of what's in vars:
# easy-rsa parameter settings
export D=`pwd`
export KEY_CONFIG=$D/openssl.cnf
export KEY_COUNTRY=KG
export KEY_PROVINCE=NA
export KEY_CITY=BISHKEK
export KEY_ORG="OpenVPN-TEST"
export KEY_EMAIL="me@myhost.mydomain"

The next part of the key generation doesn't work because it thinks the variables are blank.

After that I try "echo $D" or "echo $KG" and they're blank. 

I'm doing this all in sudo -i, by the way, because I'm working in /etc/openvpn/ which is protected.


Instructions for what I'm trying to do are here:
[http://openvpn.net/howto.html#pki]("http://openvpn.net/howto.html#pki")


Any help will be appreciated.

Thank you :)

I've been trying to solve it for hours and am making no progress. Thanks :)

---

### Post by geirha on 2008-10-13
export sets the variables in the current shell, and will be inherited by programs run from that shell. When you run a script, a new shell is spawned to run the script, and ones it has completed, the shell exits, and all such exports will be lost. You can however do something called sourcing. I'll show by example

foo.bash:
```
#!/bin/bash
export TEST=hello

```

```
~$ echo $TEST

~$ ./foo.bash
~$ echo $TEST

~$ . foo.bash   # alternatively: source foo.bash
~$ echo $TEST
hello
~$ bash --login  # Start a new shell from this shell, $TEST should now be available in that shell
~$ echo $TEST
hello
~$ exit
logout
~$

```

---

### Post by sickanimations on 2008-10-14
Well, that worked and it makes complete sense. I find it very strange that the very popular and commonly-used official OpenVPN howto guide doesn't use that 'source' function.


Relevent snippet:
> Next, initialize the PKI. On Linux/BSD/Unix:

    . ./vars
    ./clean-all
    ./build-ca

See? Wouldn't this problem apply to everybody? 

Thanks :)

---

### Post by Nausser on 2008-12-10
I sadly do not understand. I am unfortunately too "noob" for my own good.

I too am following the instruction on the openvpn site and every time I "source ../vars" or "sudo source ../vars" or "source ./vars" or any other variable thereof spits out this message.
"NOTE: If you run ./clean-all, I will be doing a rm -rf on /etc/openvpn/examples/easy-rsa/2.0/key"
Then I am referred to the precious command when executing the next command on the list. Once again trying every variable of entry with and without sudo. More specifically it spits out:
"Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration."

Please help in noob language.

Thank you in advance!

---

