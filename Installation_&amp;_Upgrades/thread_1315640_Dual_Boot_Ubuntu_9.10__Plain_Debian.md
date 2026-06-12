---
title: "Dual Boot Ubuntu 9.10 / Plain Debian"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Yeti can't ski on 2009-11-05
Hello there, 

I am currently runnin Karmic Koala (9.10) 32bits on a Dell XPS m1330, with 3GB of RAM and 120 GB of hard-disk. Really satisfied with it after a lot of tweaking. 

I would like to try plain Debian Lenny (5.0) amd64, only for fun and to learn more about Linux. I would like to install it in a partition of my HD.

I don't need to have the two distros using the same home folder.    

I was not able to find any good and up to date tutorials to get a grasp of the issue (it seems that every recent material on the issue refers to Windows/Ubuntu dual boot). 

If anyone could provide me a link to a nice howto, tutorial or relevant documentation it would be great. 

Thanks in advance.

---

### Post by ajgreeny on 2009-11-05
I'm not sure about a tutorial, but what you want to do is in some ways easier than a dual boot with windows.

Run the ubuntu live CD and use partition editor to make a partition of the size you need for debian.  Don't make another swap as that will not be needed; debian can use the same swap as ubuntu (as long as you don't hibernate one and then boot the other, or you will lose everything that you hibernated).  Now install debian to the new empty space, and just make sure you don't format or change anything except the new partition (the swap space that will also probably be noted in the install dialog, but that's OK).

I don't know if the debian grub will be legacy grub or grub 2, but it will not matter too much as you can easily add either one of the OSs to the others grub menu.  Come back again if you don't know how.  Ebian's grub will no doubt take over your boot, but if you prefer to keep ubuntu's grub, you can do that easily as well after booting to the OS.  Once again, come back if you need more info.

---

### Post by Yeti can't ski on 2009-11-05
Thank you so much. Will backup on Saturday morning, burn Lenny CD and then let you know.

---

### Post by Rambar on 2009-11-06
I'm also thinking about making a small partition to try Debian.. How can I keep my current grub (currently dual booting ubuntu and vista) when installing Debian? If I do install it, will the new Grub still have the options to boot into Vista and Ubuntu?

 Thanks a lot :)

---

### Post by Rambar on 2009-11-08
It seems that Lenny's Grub 0.97 takes over Grub 2, and doesnt recognise Ubuntu's EXT4 partition (in fact, Debian itself is unable to mount EXT4). I really have no idea how to put Grub 2 back, or how to be able to boot into Ubuntu again, so I'd like it anyone could give me a hand on this.

Thanks :)

---

### Post by Yeti can't ski on 2009-11-10
> **Rambar said:**
> It seems that Lenny's Grub 0.97 takes over Grub 2, and doesnt recognise Ubuntu's EXT4 partition (in fact, Debian itself is unable to mount EXT4). I really have no idea how to put Grub 2 back, or how to be able to boot into Ubuntu again, so I'd like it anyone could give me a hand on this.

Thanks :)

Rambar, 

Please note that I am a complete newbie and did not find the time to try the dual boot Ubuntu-Debian myself (I must say that your report is not really reassuring ;)). 

Still, a first step you could try is to update to Grub v2 in Debian. This way, you would be able to at least work with tutorials and instructions of a single version of Grub (check first if you need a special version other than grubpc): 

[http://grub.enbug.org/Debian]("http://grub.enbug.org/Debian")

[http://packages.debian.org/lenny/grub-pc]("http://packages.debian.org/lenny/grub-pc")

Then you could try to unlock alternative boots within Debians Grub v2:

[http://manpages.debian.net/cgi-bin/man.cgi?query=update-grub&apropos=0&sektion=0&manpath=Debian+4.0+etch&format=html&locale=en]("http://manpages.debian.net/cgi-bin/man.cgi?query=update-grub&apropos=0&sektion=0&manpath=Debian+4.0+etch&format=html&locale=en")

Please tell if you have any luck!

Any help from more experienced users would be welcome.

---

### Post by Yeti can't ski on 2009-11-10
You could boot trough Ubuntu's Live CD and try this!

[http://www.youtube.com/watch?v=WtBBl6HvdpM&feature=fvsr]("http://www.youtube.com/watch?v=WtBBl6HvdpM&feature=fvsr")

---

