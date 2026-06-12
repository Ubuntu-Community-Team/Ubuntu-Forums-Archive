---
title: "dns problems on new install"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by robacarp on 2005-12-30
hello.

I have just installed ubuntu today (my most successfull linux install ever--though it wasnt painless).  I am having a problem with internet programs not being able to use the public dns system.  I have my dns listed in my resolv.conf file (they get put there when I dhclient my wireless card).  I have alittle *nix expirence, but just enough to get my hands real messy when working with it.

Symptoms:  term programs like ping, host, telnet work fine when resolving names to addresses.  Other programs do not.  Firefox, Xchat, even the cmd line irc program dont seem to want to look up a name: the just shoot for ip 1.0.0.0.  If I provide an ip address, the program will work fine (ex: using 82.96.64.4 to connect to the irc channel works fine, but not irc.freenode.net [it resolves to ip:1.0.0.0]).  There is one exception to this: I can type ubuntulinux.org, ubuntuforums.org, ect in firefox and I dont get any problems.

I am connecting with a netgear wireless card that is supported natively in ubuntu - the prism gt chipset.  When I boot, I connect my wireless with this series of commands (where eth1 is my wifi card):
sudo ifconfig eth1 up
sudo iwconfig eth1 ap any
sudo dhclient eth1

I have tried using eth0, my wired port, but nothing changes--all the problems are present still.

Thanks in advance for any / all suggestions you might have. :-)

---

### Post by Jeff12088 on 2005-12-31
This thread might help you out: [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by robacarp on 2005-12-31
jeff.

Thanks.  You have no idea what a luxury it is to type google.com in an address bar until you've had to live without it. :-D

The thing that helped me was this little bit of code to turn off ipv6:
```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

Again, thanks a million

---

