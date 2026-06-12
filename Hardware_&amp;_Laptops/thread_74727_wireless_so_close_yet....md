---
title: "wireless so close yet..."
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by dotdot on 2005-10-12
hi folks 'just' another wireless question or two.

ok  first off .. i'm running 504 on a sony vaio  ltop - all ok so far.
I have a dlink g122 usb port along with a G604 router.

I have followed a few routes.
1/ install ndiswrapper from cd.. all ok.
2/ enable wlan activate wlan etc.. following
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

only problem now is ...
I can ping myself 
i can ping google..

my firefox simply doesn't connect anywhere.

oh and i can connect to the router.

..any idea pointers people ?

thanks in adv.

---

### Post by mlomker on 2005-10-12
Are you pinging Google by name or by number?  Verify the contents of the /etc/resolv.conf file, where the DNS server settings are kept.

---

### Post by dotdot on 2005-10-12
i'm pinging google - by name.

resolv.conf content =
nameserver 192.168.1.1

-- hope this helps

---

### Post by mlomker on 2005-10-12
If name resolution works then the problem must be firefox-specific.  I guess I'd try going into Synaptic and removing and adding it back in.

---

### Post by dotdot on 2005-10-12
ok removed then re-installed - then just for good measure - rebooted.

enabled wifi then off we go..

i can ping google.com

however, again, when inserting - [www.google.com](www.google.com) it just sits there ...

..however if i put in the ip adress i got back from the ping.. hey presto.

..alas - for a simple search .. of course in this case for ubuntu..

I can't connect to the site - as it's a name not an ip address :!!!

..we're close... but not quite yet.. !!!

..people ?

---

### Post by mlomker on 2005-10-12
The next thing I'd look into is the about:config settings in Firefox.

Start at [this thread.]("http://ubuntuforums.org/showthread.php?t=70642")

---

### Post by dotdot on 2005-10-12
why thank you - all sorted now.

i must say how useful this exercise has been.

..more.. yes questions - later on .. something else i'm sure :)

..cheers

---

