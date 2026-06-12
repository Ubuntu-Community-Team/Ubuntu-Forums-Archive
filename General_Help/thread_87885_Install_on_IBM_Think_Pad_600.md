---
title: "Install on IBM Think Pad 600"
date: 2005-11-09
forum: General Help
---

### Post by jwmullins on 2005-11-09
I have been working with computers for some time now and I am just getting started in Linux. I have been checking it out for a while to determine which version to go to. I have a Think Pad 600 laptop. It is a 300 MHz P2 with a 5 Gig HD.

  I have been trying for about 3 days now to install Brezzy Badger on my laptop. It will be the only OS on it, and I will start with the apps that come with Ubuntu. I downloaded Ubuntu 5.10 i386.iso. I made the CD from this and have been trying to install ever since.
  While installing from the CD(during install of base system) I get a window that says:

     [!!] Install the base system
    unable to install the selected kernal
    An error was returned while trying to install the kernal into the target     
    system.

    kernal package: 'linux-386'.
    Check  /target/var/log/bootstrap.log for details.


  I go back, reormat and load base system again. After a while(about 75% on the bar) I get a menu asking which kernal to load. There are three choices. I have chosen all three at different times. It will finish loading the base system, some of the time, and starts coping remaining packages to hard disk.

  I then get a window that says:

             Coping packages failed.

  It says I may have run out of space in the target /var filesystem, or CD drive may have problems reading packages from the CD. Says cleaning drive or burning at a lower speed may help.

  It says to check  /var/log/syslog  or virtual console 4 for details.

  I have tried cleaning CD. First CD was burned @ 12X, I tried another at 10X with no success. I do not know how to check the details as the stated.

  I have even gotten to where it tells me to take the CD out of drive and let the computer boot from HD.
  Would appreciate info that will get me set up so I can make my exit from MS.

---

### Post by Skrewdriver on 2005-11-09
This may not be part of the problem, but how much RAM does your Thinkpad have?
The 600 models have 64Mb as standard, and this may not be enough for a workable Ubuntu laptop.
See [Breezy release notes]("https://wiki.ubuntu.com/BreezyReleaseNotes#head-926b69ab76b39955f2710c42c4bf39122ffdc4e5") for recommended minimum specs.


It sounds to me like it is having trouble reading the CD. This means either your CD has an error, or your CD-ROM drive is mucking up. You say you have tried burning other CDs, and had problems with those as well, so maybe the problem is the CD-ROM. Try running a Live CD on the Thinkpad and let us know how that goes.

Otherwise have a trawl around [http://www.thinkwiki.org]("http://www.thinkwiki.org"), this is a site dedicated to Linux on Thinkpads.

---

### Post by jwmullins on 2005-11-11
[QUOTE=Skrewdriver]This may not be part of the problem, but how much RAM does your Thinkpad have?
The 600 models have 64Mb as standard, and this may not be enough for a workable Ubuntu laptop.
See [Breezy release notes]("https://wiki.ubuntu.com/BreezyReleaseNotes#head-926b69ab76b39955f2710c42c4bf39122ffdc4e5") for recommended minimum specs.


It sounds to me like it is having trouble reading the CD. This means either your CD has an error, or your CD-ROM drive is mucking up. You say you have tried burning other CDs, and had problems with those as well, so maybe the problem is the CD-ROM. Try running a Live CD on the Thinkpad and let us know how that goes.

Otherwise have a trawl around [http://www.thinkwiki.org]("http://www.thinkwiki.org"), this is a site dedicated to Linux on Thinkpads.[/QUOTE]
I have 134+Mb RAM. I have checked the params more than once to make sure I was not missing something. 
 Just to make sure it is clear, when I said I burned other CD's and had problems. I ment the breezy install CDs.
 There is something that might have a bearing on this though. I have a friend download the ISO file for me and he copies it to a DVD, CD-RW, or CD-R. He uses ROXIO and I use NERO. Again, I do not know if this is a problem but it is another area I have thought about.
 Thanks for your reply.

---

### Post by rcerreto on 2005-11-11
I don't think using Roxio or Nero can make any difference.
It looks a defected CD to me.
Did you verify the downloaded iso against md5sum?
It's also a good idea to check the CD after burning, I know that Nero has an option for it and I guess Roxio has it too.

---

### Post by jwmullins on 2005-11-12
I did not check against md5sum. I have seen others talk about it, but I do not know how to do it. Any info on how I can do this would be appreciated. Also, do you have to check the numbers as soon as you D/L, or is it just a list that you can go back to later and check? I have a friend that D/L's the file for me on DSL(I cannot get it where I live yet). I will be there when it D/L's if that is what it takes. My friend has had a few strokes and his short term memory is not very good.
 I have also asked to have some CD's sent to me. I guess I will have to wait for 6 to 8 weeks for them to get here, unless I get something else to try. If someone will inform me about the md5sum I will check that out.

Thank You,

---

### Post by poptones on 2005-11-13
You can get an md5sum checker from here. 

[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

There is an md5sum for every file on the cd in the cd folder md5sum. Point the checker at that folder and it should check the cd

---

### Post by Donnut on 2005-11-13
I'm thinking it could be the cd-rom.  Do you have an external IDE-USB interfase/case?  If you do, try installing it from another CD-rom.  Also, try cleaning your existing cd-rom.

---

### Post by jwmullins on 2005-12-10
I want to thank everyone that that gave me suggestions on my problem. I do not know what the problem was, but I tried installing with a CD from a friend and it went okay. Now I have to get it connected to internet and playing music. If I have problems here, I know I have seen these addressed somewhere on the forum.
 I plan on making Linux my OS from now on and dumping MS as soon as possible.
 THANKS AGAIN!!

John W. Mullins

---

### Post by Gurgeh on 2005-12-17
Ubuntu runs nicely on my Thinkpad 600. But sum questions:

- Does it randomly power up sometimes tho? 
- Have u got the annoying hell-chipset soundcard working?

and you'll have some fun if u've got a wireless network card I tell thee. Oh and another thing dig out a win98 CD (to boot from) and get PS2.exe from IBM, whack it on a floppy and you can tweak A LOT of options that are not in the BIOS ;)

---

### Post by gotaserena on 2005-12-20
I've managed to get the soundcard (and modem) working by using the "setpnp" program. Check also "lspnp" to know which addresses to turn on. I've also checked the [alsa configuration for the cs4236 chip](http://www.alsa-project.org/~valentyn/Alsa-sound-mini-HOWTO-5.html) to modprobe it correctly. I've finally added a script to the rc.S directory that runs the setpnp everytime I boot. It has been working flawlessly ever since.

---

