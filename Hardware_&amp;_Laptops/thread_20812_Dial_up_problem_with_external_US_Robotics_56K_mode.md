---
title: "Dial up problem with external US Robotics 56K modem"
date: 2005-03-18
forum: Hardware &amp; Laptops
---

### Post by tonynewbie on 2005-03-18
I'm a newbie, so forgive this probably stupid question.

I can't get the internet connection to work. Here is what I've done:

1. Manually setup ppp connection during installation (auto-detect did not work).
2. Ran $sudo pon.
Got error message:
/usr/sbin/pppd: pppd is unable to open the /dev/ppp device.
You need to create the /dev/ppp node by executing the following command as root:
mknod /dev/ppp c 108 0
3. Ran the above command as root.
Tried $sudo pon again. Worked!
$sudo poff worked.
Modem lights worked.
Logged out and then logged in.
pon/poff & modem lights still worked.
5. Restarted computer (I'm dual booting with Grub. Windows 98 is on hd1.)
6. pon/poff & modem lights did NOT work.
Got the same error message as before.
7. /dev/ppp had disappeared. (It was there before. I checked.)
How do I correct this?
The permissions of ppp were -rw-r--r-- (644)
Do I change the permissions or "Make Sticky" ?
or modify Grub ? or ???
8. BTW I also tried Dialup Modem Howto from [http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)
with the same results.

Thanks for any help.

---

### Post by tonynewbie on 2005-03-23
Problem solved. I updated to the latest versions of programs on my system (for Warty 4.10) and now my modem settings are remembered.

tonynewbie

---

### Post by elcu on 2005-04-06
Hello, good work in getting it fixed, but I thought I might let you know I have the same modem and got my connection up and working using WVDial.

It comes with the Ubuntu installation CD, and is also packaged with most other Linux distros.  You can also get it here:

[http://open.nit.ca/wiki/?page=WvDial](http://open.nit.ca/wiki/?page=WvDial)

It is an extremely easy way to get connected using a dial-up modem.  Getting connected was a three step process for me, and I was ecstatic after having difficulties with getting a working connection in other distros in the past.

---

