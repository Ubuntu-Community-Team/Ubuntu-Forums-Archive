---
title: "Cannot loat ubuntu on compaq TC1000"
date: 2008-11-04
forum: General Help
---

### Post by unix1adm on 2008-11-04
I tried to boot the ubuntu live cd on a Compaq TC1000 tablet pc last night. Just wanted to see if it would load. It has an external cd rom. It booted to the cd to the menu and selected boot the os option not install.

It gave me the splash screen but even after an hour the system never came up. the cd stopped spinning and it just sat there.

has anyone ever tried to load ubuntu on a tc1000 tablet pc? I dont care if I lose the tablet functions. I just want it for email on the road etc. xp is a dog on a 900mhz processor it has.

I have tried this CD on several systems. could the distribution i downloaded be bad? I tried it from several mirror site and it ran the check cd option and they all say 1 file was found to be bad. I am guessing this is the issue. But why am i getting a bad iso file?

The download process completes with no errors so I am thinking the file is bad when it comes down.

Can someone point me to a like with a know GOOD iso image?

---

### Post by unix1adm on 2008-11-05
No one has tried to load ubuntu on a tc1000?

---

### Post by unix1adm on 2008-11-07
Still no feed back form anyone on this. Guess Ill try suse

---

### Post by unix1adm on 2008-11-12
bump

---

### Post by rokytnji on 2008-11-12
[http://tuxmobil.org/compaq.html](http://tuxmobil.org/compaq.html)

[http://notes.xiaoka.com/stuff/TC1000/gentoo-on-tc1000.html](http://notes.xiaoka.com/stuff/TC1000/gentoo-on-tc1000.html)

[https://handhelds.org/mailman/listinfo/tc1000-linux](https://handhelds.org/mailman/listinfo/tc1000-linux)

[http://www.ask.com/fr?u=http%3A%2F%2Freverso2.com%2Fri45r%2FASP%2Furl%2Fresult.asp%3Fdirections%3D1040%241033%242%26autotranslate%3Don%26motsinconnus%3Dfalse%26templates%3DGeneral%26url%3Dhttp%3A%2F%2Fwww.rainbowbreeze.it%2Fubuntu-linux-tabletpc-tc1000.htm&s=a&srcl=it&tarl=en&bu=http%3A%2F%2Fwww.ask.com%2Fweb%3Fq%3DUbuntu%2B%2B%2Binstall%2Bon%2B%2BCompaq%2Btc1000%26o%3D101483%26l%3Ddis%26page%3D1%26dm%3Dlang%26advl%3D%26advc%3D&q=Ubuntu+++install+on++Compaq+tc1000&o=101483&l=dis&qt=0&ac=30&dm=lang&ou=http%3A%2F%2Fwww.rainbowbreeze.it%2Fubuntu-linux-tabletpc-tc1000.htm](http://www.ask.com/fr?u=http%3A%2F%2Freverso2.com%2Fri45r%2FASP%2Furl%2Fresult.asp%3Fdirections%3D1040%241033%242%26autotranslate%3Don%26motsinconnus%3Dfalse%26templates%3DGeneral%26url%3Dhttp%3A%2F%2Fwww.rainbowbreeze.it%2Fubuntu-linux-tabletpc-tc1000.htm&s=a&srcl=it&tarl=en&bu=http%3A%2F%2Fwww.ask.com%2Fweb%3Fq%3DUbuntu%2B%2B%2Binstall%2Bon%2B%2BCompaq%2Btc1000%26o%3D101483%26l%3Ddis%26page%3D1%26dm%3Dlang%26advl%3D%26advc%3D&q=Ubuntu+++install+on++Compaq+tc1000&o=101483&l=dis&qt=0&ac=30&dm=lang&ou=http%3A%2F%2Fwww.rainbowbreeze.it%2Fubuntu-linux-tabletpc-tc1000.htm)

your main problem is there are no new links on installing linux on a Compaq tc1000. Xubuntu or Fluxubuntu or Arch Linux might be a better option for your specs.

---

### Post by unix1adm on 2008-11-13
thanx for the links. Guess after reading one of the blogs....

 "Back to Windows XP

I finally decided that a slower, non-free OS with decent applications and a little better look-and-feel and much more functionality would be worth going back to, and reinstalled Windows XP Professional Tablet Edition. However, that process wasn't seamless either. I had an external USB CD-ROM drive, and popped in the CD. It wouldn't boot. I checked the BIOS boot order, and there was no CD-ROM drive listed. How odd! My BIOS was up-to-date.

After brainstorming for several days, I was able to enlist a friend with a Microsoft Remote Installation Services (RIS) server to help me reinstall a working OS. I used a USB flash drive to copy over the drivers so that I could get network connectivity again. And I installed Firefox, Putty, and all of my favorite Windows open source utilities. If I am going to use Windows XP Professional Tablet Edition, at least I'll have some useful applications on it!"


Linux may not be the best or even a much faster option for this hdw. Oh well.

---

### Post by mplexus on 2008-12-23
I have installed ubuntu 8.10 on TC1000. I made a USB (flash) boot disk. Will try to recall the link on how-to do that, but if you do have a working 8.10 ubuntu you could maybe try "create a USB startup disk" from the menu.

Opening new applicaitons together is quite slow cause of only 256 MB memory (actually less than 256 cause some is used by nvidia card). I will install more ram (So-Dimm SDRAM - hard to find nowadays :-) But after a program find its place in the memory it runs with no speed complaints.

Only problem I cannot use glx-96 nvidia drivers. The module exists but does not bring up the X server, fails with error message.

It is good to know that atmel wireless card is supported - altough not tested yet.

Also, altough the iso may download completely it may be downloaded corrupted - not that it is corrupted in the server.. One should check the integrity with software like md5sum, if i'm not mistaken.

---

### Post by joeinbend on 2009-01-19
Hey mplexus,
I also have a TC1000, the only (major) thing that I was not able to get working was the pen driver -- were you able to get that going? if so can you point me in the right direction?

Also I should pass a note back to you -- if you use v8.04 instead of 8.10, you will not have any trouble with the video drivers. ATI and NVidia drivers for 8.10 arent really that great yet!

---

### Post by Herman_Snerd on 2009-05-18
I know it's been a while since this thread was started but I thought I'd jump in none the less.

I was successful in getting 8.04 and 8.10 installed on the TC1000 but like many others I'm unable to get much more than basic laptop functionality out if.  I downloaded the ISO's from

[http://mirrors.gigenet.com/ubuntu/](http://mirrors.gigenet.com/ubuntu/)

The Nvidia drivers for the GeForce2 Go just don't work.  Every time I've tried to enable the drivers I've rebooted to a black screen.  So far I haven't found anyone or any resource that explains how to get this driver working.  I did  see a video (youtube maybe) showing someone with their TC1000 with compiz running, screen rotation, and stylus all working - I just can't find the video again!

I'd LOVE to get my TC1000 up and running with all the bells and whistles.  Can ANYONE put the pieces of this puzzle together?

---

