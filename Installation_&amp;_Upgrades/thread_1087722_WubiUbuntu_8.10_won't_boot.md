---
title: "Wubi/Ubuntu 8.10 won't boot"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by saul11 on 2009-03-05
I have installed Ubuntu 8.10 using wubi, but after the installation completed I'm left with a black screen with a cursor blinking top left, although not reacting to anything, thus needig me to reboot by pressing the power button. When I then try to boot into Ubuntu I end up in a shell 'paul@ububtu:' just after I get a dump of the message '-BASH: /dev/null : permission denied'. In the shell I can login with the login detail I specified in wubi and I come into a location with a directory 'Examples' contained several pdf, odt, trf and other files.

I'm using a [compaq 6820s]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-89315-3442856.html") (Intel® Core™ 2 Duo Processor T8100 (2.1 GHz, 800 MHz FSB, 3 MB L2 cache), 2048MB, 160GB, WXGA) downgraded from Vista to XP SP2.
I first let Wubi download Ubuntu, which gave me the 'ubuntu-8.10-desktop-amd64' image, then I manually downloaded and tried the 'ubuntu-8.10-desktop-i386.iso' version; both showing the same result described above.
I tried the 8.10 live DVD and testing Ubuntu from it works fine.

The log in %temp%, 'Wubi-8.10-rev515.log' is attached as well as the logs I found in 'C:\ubuntu', 'curl_log.txt' and ''.

I have 'Acronis True Image Home' on my PC, not expecting that to have any influence though.

Thanks for any help.

---

### Post by saul11 on 2009-03-07
Hmm, I do have an ATI (AIT Mobility Radeon X1350), so this might be a 'ATI Blank Screen' problem?

[http://ubuntuforums.org/showthread.php?t=995760](http://ubuntuforums.org/showthread.php?t=995760)
[http://ubuntuforums.org/showthread.php?t=317545](http://ubuntuforums.org/showthread.php?t=317545)
[http://ubuntuforums.org/showthread.php?t=599596](http://ubuntuforums.org/showthread.php?t=599596)

but the '-BASH: /dev/null : permission denie' message seems not related to the ATI problem, [http://ubuntuforums.org/showthread.php?p=6853365](http://ubuntuforums.org/showthread.php?p=6853365)

---

### Post by saul11 on 2009-03-07
Tried editing the xorg.conf, but it has almost nothing in it (only identifier under section 'device')!? Tried adding the driver and vendername, but didn't have permission to save the file. :(

Also tried updating the ATI drivers, but when trying 'wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run)' I got 'unable to resolve host address "a248.e.akamai.net"' :(

So noobie me is at a loss

---

