---
title: "Will Xubuntu run on an old Pentium/233 with only 32 MB of RAM?"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by doitashimashite on 2005-12-09
Anyone who has Xubuntu up & running on an old machine like a Pentium 233 MHz with only 32 MB of RAM? (and by that, I mean running *nice to work with*, not just running).

If not, what are the absolute minimum system requirements for Xubuntu?

Any experiences?

---

### Post by PMO6022 on 2005-12-09
[quote=doitashimashite]Anyone who has Xubuntu up & running on an old machine like a Pentium 233 MHz with only 32 MB of RAM? 
Any experiences?[/quote] I tried a minimal server install of ubuntu on an old toshiba satellite ~133 MHz with 32 MB RAM, and could not install.  

I ran out of memory during the install process, and it would continually restart. The error tty reported an out of memory error.  Since it was a server install (no DE/WM) I the same would probably have happened with xubuntu, since there are not many differences under the hood, so to speak.  I was able to install slackware, though.  My best advice is to just try it and see what happens!

---

### Post by drummer on 2005-12-09
Give it a try.. but 32mb is the minimum for the installer alone, the text based one, so xfce would probably perform a bit slow. I have a PII 200mhz with 64mb ram.. and I haven't been able to install Ubuntu on it, even just the server install. Warty froze at around 40% numerous times in installing, and Breezy cane up with some sort of error. I don't think it's the hard disk since I've installed DOS and Slackware on it, so my guess now is a lack of memory.

Still give it a go though... your milage may vary.

---

### Post by valfreixo on 2005-12-09
Heya,

I've worked with a Xunbuntu with a Pentium II - 400Mhz and 128 Mb and it worked very very fast. So i guess it will work fine with a pentium 233. I would recommend more RAM. 


//Vx

---

### Post by ubuntu_demon on 2005-12-09
Maybe it will install. But it won't be nice.

maybe icewm is do-able. (it is do-able but slow on a PII 266 with 64 mb ram)

Choose server install from the the boot screen of the install cd.

$sudo apt-get install icewm x-window-system xdm

you might want to install other stuff like :
iceme  (to change icewm menu)
icepref (to change icewm settings)
icewm-gnome-support
epiphany-browser (uses a little bit less memory than firefox but still a lot)
dillo (a fast and light browser which doesn't support frames and a lot of other new stuff)

I would recommend to use the pc as a server. 

With thin client your new machine does all the work and you are able to put your older pc to good use. Dapper may support thin client on 32 mb ram machines see :  [https://wiki.ubuntu.com/ThinClientMemoryUsage](https://wiki.ubuntu.com/ThinClientMemoryUsage)

---

### Post by hrs on 2005-12-09
I've installed it on P166 64Ram it was too slow for work with (a coupple of mins to open the terminal)

---

### Post by utterlyjaded on 2005-12-10
ok, I did a test on an old box I have.  I originally had it as a machine for dos games quite some time ago,  I love my dos games.  Anyway,  With 32 megs of ram and an old Pentium it world not install and kept failing at a different percentages, like it would fail at 30%, or 34%.  I tried it like 4 times because I was bored.  I then put in 128 megs of ram and it did install.  It ran slow as hell, but it worked.  it also took forever to install.  So there, it is probably  memory issue.  Also I used Horay 5.04.

---

### Post by crazydeb8r on 2005-12-10
The RAM will be the sticking point, as many above have said. Right now I'm on a PII 233 with 128 MB RAM. It runs fine once some of the eye candy is diismantled. the installer was slow but ran through without a hitch. So, just for you, I took my older laptop (exactly the same, but with only 64 MB RAM), took out a Ram card, and Installed. And it's still working after almost 3 hours, but it IS working. So like many others have sad, you won't know until you try.

---

### Post by roberttosa on 2005-12-10
I attempted and install to an IBM ThinPad 770 P2-233mhz with 256mb of ram. It would not even start the installer.

---

### Post by Nopposan on 2005-12-10
I've got a Compaq Armada 7750 laptop (without the docking station) that I've installed Xubuntu on.  Currently only 64 mb of RAM but I'll replace it with 128.  Penium MMX processor.  2 GB hard drive.  It's running a bit slower than I'd like, but I'm not sure it's any slower than the Win98 that I replaced.  (I'm having some trouble with mounting the CD rom after install and also with sound, but I think that's pretty normal as it also happened with a normal Ubuntu distribution that I did on a Compaq Presario 700; that one's running SUSE 10.0 eval distribution now 'cause I never could get the sound and the DVD player going well in Ubuntu; whether I ran KDE or gnome only led to different problems.)

I think there's a chance that Ubuntu would work for you, but I'd recommend iceWM; that's what Kanotix uses, and if you've got a CD rom then you really should try out Kanotix with iceWM 'cause it's amazing how it ran on that little old slow laptop!  'Trouble is Kanotix didn't do a clean and easy install to the hard drive and is also quite a new distro without the amazing support you get with Ubuntu forums.

---

### Post by towsonu2003 on 2005-12-10
pentium 300mhz and 64mb ram 180MB swap 4.1GB HDD (about half is empty)- xubuntu worked :) not fast but good. (use abiword for word processing)

---

