---
title: "Drivers for laptop? What do I do?"
date: 2008-12-12
forum: Hardware
---

### Post by outy565 on 2008-12-12
Hey guys. I would really like to install ubuntu on my Toshiba Satelite 1405-S171 laptop (yep its pretty ancient lol). Right now i have windows xp on it but i would like to completely wipe it and only have ubuntu on it. However, what would i have to do as far as drivers for it (especially since its a laptop)? When i go to install it xp would already be off of it cause im going to format my HDD. Any information would be helpful. Thanks

p.s. heres the link to all of the drivers for my laptop from toshiba
[http://www.csd.toshiba.com/cgi-bin/t...=213951|PS140U](http://www.csd.toshiba.com/cgi-bin/t...=213951|PS140U)

---

### Post by securitynut on 2008-12-12
You should be ok with Ubuntu as it picks up most hardware. I installed Ubuntu on my presario v5000 and it picked up all my drivers except for my wireless. What drivers it doesn't pick up and you can't find, you can extract the firmware and compile a driver. That's what I did for my wireless (broadcom bcm4318).

---

### Post by outy565 on 2008-12-13
ok well i installed it on the same partition that xp is on (i didnt get rid of xp yet).  i rebooted and loaded ubuntu.  i get the loading bar thing and then all i get is the background image with the mouse in the center but nothing works. my mouse pad, keyboard, nothing.  the only thing that works is the power button.  what could be the cause of this?

---

### Post by ooobooontooo on 2008-12-13
Corrupt live CD (or whatever you installed Ubuntu from)? Did you check the integrity of the CD? Or maybe it has to do with the fact that you installed it in the same partition as XP...I didn't know you could do that...I always thought it had to be different partitions? Anyway, I wiped out everything I had too and installed Ubuntu and most of my stuff was working (things like headphones and hibernate didn't work) and I have a Sony laptop, which is possibly the most incompatible computer with Ubuntu. If you already have all your files backed up you could try a clean install.

---

### Post by jlochhead on 2008-12-13
The TCP/IP Protocol Suite (the set of protocols the Internet runs on) isn't perfect, therefore data sometimes gets corrupt. Hence, you need to validate important files (such as live cd isos) before you use them.

Many distros encourage you to use MD5SUMS (hashing) to do this. I can't seem to find the MD5SUMS for Ubuntu, but I am sure they will be around somewhere.  

Anyway, an easier approach for new people is to just download the iso as a torrent because torrents are validated automatically. The i386 version (for 32 bit machines) can be found below:
  
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent)

It would probably make your life easier if you freed up some space from xp by downloading the gparted live cd ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) and resizing the xp partition.

Then you can just install Ubuntu automatically in the empty space. The problem is probably arising because you installed Ubuntu to the same partition.

---

### Post by ooobooontooo on 2008-12-13
The md5sums can be located here:
[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

EDIT: To check the md5sum of a iso file. Type:
md5sum [ubuntu-blab-blah].iso into command prompt (replace [ubuntu-blah-blah] with whatever the file actually is...) and compare with the appropriate one in the link above. This is if you have a unix/linux terminal...I don't think md5sum works in windows...you'll have to get some sort of md5sum checker...you could install cygwin (unix terminal emulator) because that comes with md5sum but that would be overkill.

---

### Post by outy565 on 2008-12-13
> **jlochhead said:**
> 
Anyway, an easier approach for new people is to just download the iso as a torrent because torrents are validated automatically. The i386 version (for 32 bit machines) can be found below:
  
[http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-desktop-i386.iso.torrent)



yeah i would download the torrent but im at school right now and their network blocks anything that remotely seems like a torrent.  so how would i be able to check the iso in either xp or vista?

---

### Post by Timbow on 2008-12-13
I just installed 8.04 on an old Toshiba Satellite Pro 4600 (700Mhz, 256Mb). The simple answer to your query is to stick th CD in the drive and test run the live session.

---

### Post by outy565 on 2008-12-13
what do you mean by "test run the live session"?

also if i instal 8.04 can i update it to 8.10 while running ubuntu or would it have to be a clean instal?

---

### Post by ooobooontooo on 2008-12-13
When you stick your cd in the cd drive and start up the computer you should get a menu. What he means by the live session is the option to just try Ubuntu without modifying any of your old computer data. That's what a live CD does. Another option is to check the integrity of the CD to make sure everything was installed properly. I would go ahead and check that first. If it errors, then you need to get a new copy.

I'm not sure what you mean by updating while running Ubuntu, but I'm pretty sure you can upgrade Ubuntu without having it destroy all your old data. Although, you may wish to wait a while. I heard a lot of things broke in 8.10

---

### Post by outy565 on 2008-12-14
> I'm not sure what you mean by updating while running Ubuntu, but I'm pretty sure you can upgrade Ubuntu without having it destroy all your old data.
yeah thats what i meant lol.

right now i have a iso copy of 8.10 but ill try to find one of 8.04 and see if it works any better

---

### Post by networm1230 on 2008-12-14
> **outy565 said:**
> what do you mean by "test run the live session"?

also if i instal 8.04 can i update it to 8.10 while running ubuntu or would it have to be a clean instal?

I have ubuntu 8.04 according to ubuntu you can't update to 8.10 using 8.04 you must have the iso file
burned to a CD or find a program that can run iso files

---

### Post by outy565 on 2008-12-14
yeah i used power iso to burn it.  i just checked the disk and its good.  installing now =)

---

### Post by outy565 on 2008-12-14
ok well the intall loaded but now i can't click anything.  the mouse is unresponsive as well as the keyboard.  i even trying plugging in a usb mouse and it didnt work either.  now what do i do?

---

### Post by ooobooontooo on 2008-12-14
Did you check the integrity of the CD? (either by loading it into a different computer or by checking the md5sum of it)? If you did and it still doesn't work...Then I guess your hardware might just be incompatible with Ubuntu...but I would first try with another CD of 8.04...

---

### Post by outy565 on 2008-12-14
yeah i check the cd and it said that it didnt have any errors.

i was hopeing to run ubuntu instead of xp because it doesnt use as much resourses which would be very beneficial for my laptop since its running
256mb ram
1.5 ghz intel celeron.

over the next week or so im going to add an extra 256mb ram.  if i cant get it to work now then hopefully itll work then.


could there be anything else that could be causeing the problem?

---

### Post by ooobooontooo on 2008-12-14
Oh...You really don't have much memory. You might want to wait until you upgrade your computer or you can install Xubuntu, which requires a bit less memory. Here read this:
[https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

EDIT: It says you need to use the alternate install CD...if you want to install now. I don't recommend it though; I think a lot of things will be broken...

---

### Post by outy565 on 2008-12-15
i tried installing xubuntu before i saw that you posted and i tested the cd and my memory and both said that they were fine.  i went to install it and after the loading bar that goes back and forth finished all i got was a little white X in the middle of the screen and again  nothing would work.

---

### Post by ooobooontooo on 2008-12-15
Props to you for still not giving up. Before you completely throw in the towel, you might want to try installing other distros of Ubuntu. There is one other user that I found who had Breezy 5.10 running on their Toshiba Satellite 1405-s171. Apparently the installation went flawless. So you might try to install a different distro. You might also try to install after you upgrade your computer. If it still doesn't work after that...I'm sorry I couldn't help you.

---

### Post by outy565 on 2008-12-15
yeah i'm probaly going to wait atm until i add a little more ram.  then ill try ubuntu again.  if that doesnt work then ill try breezy.  ill let you know what happens when it happens lol.  thank you so much for all your help and trying to help me figure this out!

---

### Post by ooobooontooo on 2008-12-15
No problem. That's what the Ubuntu Forums are for.

---

### Post by louistan3 on 2008-12-15
have you actually installed ubuntu? or are you just running it off from the cd when it hangs? 

Im thinking that you dont have enough ram for the live cd and is the reason why its hanging.

---

### Post by outy565 on 2008-12-15
i tried running it off the cd and it hang.  and i try installing it and it hangs

---

### Post by louistan3 on 2008-12-15
you could try getting the alternate installer. which is a text based installer.

Its pretty much the same thing, just without the mouse and graphics. :P

---

