---
title: "Persistent USB install problems."
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by ((( ~ ))) on 2009-05-16
Hi everyone, this is one my first threads here, so please be gentle with me :)

Ok, so before I get my new laptop the 20th, I want to have a persistent USB stick install of Xubuntu, BUT, once I get my laptop > I want to transfer all the files, settings and apps from my USB flash and use it as my main Xubuntu install on my new laptop.


**_What I've already tried (from winXP):_**
- Pendrivelinux.com approach of installing a persistent Xubuntu > gave me an error when booting "Searching for Boot Record from USB RMD-FDD..."
- uNetbootin approach > gave me the same error.
- Formatted it to FAT16 under gparted, and created an image using Ubuntu USB desktop image creator > Boot error (BUT: that was when I sudo apt-install usb-creator, without installing additional components like syslinux and mtools).
- Did the same procedure, but installing the needed components through synaptic, here's the terminal installation log:
[http://pastebin.com/m36aab047](http://pastebin.com/m36aab047)
...and still got the same error...

Note: When formatting to FAT16 in gparted, I got a strange error saying:
```
 Failed to mount "12G Volume".
The enclosing drive for the volume is locked.
Failed to mount "19G Volume".
The enclosing drive for the volume is locked.
```But I managed to open the volume up anyway. Really strange.

/\ Whoops that's because I formatted something different on my HDD (didn't see that at the top-right corner of gparted I could select physical drives hehe).

- So, this time I formatted the right drive with FAT16 and created a liveUSB partition consulting this resource:
[http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/](http://xubuntublog.wordpress.com/2008/11/07/ubuntu-from-your-flash-drive-easier-than-ever-before/)
This time, I get past the bootup screen and into the boot menu, I choose "install xubuntu without change to your computer"... but get this error: [http://paste.ubuntu.com/173795/](http://paste.ubuntu.com/173795/)
After typing 'exit' in the prompt, I get this type of machinejive: [http://img198.imageshack.us/gal.php?g=p5150009.jpg](http://img198.imageshack.us/gal.php?g=p5150009.jpg)
(with at the end a Kernel Panic)


**_ What I think I should do:_**
- Still try to maintain the thought that a GNU/Linux OS can also be operated by humans.


I'm sorry people, but for the last 3 days I'm trying to make a persistent install of xubuntu (kindly ignoring the learning material for my entry exam for my school) and I just lost the count of the number of coffeecups consumed.

So I humbly ask you: What do you think the problem can be and what's the easiest solution to it while still maintaining the option for a persistent USB install?

Kindly thanking you in advance ):P

---

### Post by ((( ~ ))) on 2009-05-16
Oh, and in case you're wondering, I did an MD5 check for the .iso using winMD5sum on XP and it all matched, added to that, every time I put the liveCD to use, I checked the disk integrity and every time it turned out OK (even so with the RAM check). Yes, I are prepared :p

---

### Post by Vinze on 2009-05-16
I'm afraid this might be a problem of your hardware together with the version of Xubuntu you're using. If that's true, it's really bad luck and doesn't really have much to do with the usability of Xubuntu.

Anyway, what you could try is to use an older or newer version of Xubuntu (depending on what you used this time). Also take a look at this bug report (though your issue is probably different): [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192)

---

### Post by Vinze on 2009-05-17
Here's something that could also help you: I just tried to run my USB persistent install here, and when a floppy was still in my floppy drive (admittedly, that floppy has the Grub bootloader I use to boot my normal system installed on it), I got the same error message.

(Yes, there are a ton of reasons that could cause this, but you never know, it might just be this one you're experiencing ;) Also, you should try running from USB on a different PC - that's worked for me in the past, indicating that it was a hardware problem)

---

### Post by ((( ~ ))) on 2009-05-17
Thanks for replying, Vinze :)

I was using i386-desktop edition of the Jaunty (9.04) Xubuntu.
Today I did the same thing with the same release but this time with Ubuntu, yet with the same problem.

Seems that a few people are having this problem as well (and with certain persistence problems):
[9.04 RC Live USB problem]("http://ubuntuforums.org/showthread.php?t=1129123")
[Can't make casper-rw loop persistence file greater than 2.0 GB-Ubuntu 9.04]("http://ubuntuforums.org/showthread.php?t=1135732") = install is unable to be persistent.

Ok, this is what exactly happens on one comp:
Computer On > Choose to boot from USB > Isolinux kernel found > (X)Ubuntu Bootmenu > Choose to "Install (X)Ubuntu without any changes to computer" > See the (X)Ubuntu loading screen where the pointer thingy goes _back and forth_ => after about 2 minutes > BusyBox prompt error.

On the other comp, it just doesn't even find the kernel...

What's also notable to note, is that when I use the USB creator tool in both distro's, the progress bar works until about 20% and then immediately finishes the task. This behavior is also documented in the abovementioned threads.

Is this some kind of a new but undiscovered bug? I've searched around launchpad but haven't really been able to see any relevant results concerning 9.04... strange... :-k

Maybe I should try this method once, but I have no idea how to create multiple partitions on one stick:
[http://ubuntuforums.org/showpost.php?p=7140583&postcount=10](http://ubuntuforums.org/showpost.php?p=7140583&postcount=10)


In any way, I appreciate the effort for taking your time to illuminate me in the depths of Ubuntu :P

---

### Post by Vinze on 2009-05-17
I don't think the multiple partitions thingy will be of benefit to you, unless you have an especially large USB drive (like 16GB, like that poster has).

Anyway, it might be that this is a bug not yet reported, so you can try to report it yourself. In the worst case, it's been reported already and you'll be directed to the other report ;)

(Oh, and of course, you might be *extremely* unlucky to happen to try it on two different hardware setups that don't work :P)

---

### Post by ((( ~ ))) on 2009-05-22
> **Vinze said:**
> I don't think the multiple partitions thingy will be of benefit to you, unless you have an especially large USB drive (like 16GB, like that poster has).

Anyway, it might be that this is a bug not yet reported, so you can try to report it yourself. In the worst case, it's been reported already and you'll be directed to the other report ;)

(Oh, and of course, you might be *extremely* unlucky to happen to try it on two different hardware setups that don't work :P)

Well, another setup is coming along in a few days, so testing on 3 systems will significantly maximize the chance of finding out what made my hair turn grey in a couple of days :P

Here are my specs from xxodd.nl :
```

[B]XXODD XNi860tu 15”

[/B]     * Intel Core 2 Quad Q9000 (2,00Ghz, 1066Mhz, 6Mb) Inclusief Game-pack!
    * 4GB DDR3 1066MHz geheugen (2x 2GB)
    * 128GB SATA Solid State Drive (MLC)
    * DVD-CD +/- burner
    * No Intel Turbo Memory module (<<< I'm planning on using 64bit XP for compatibility purposes and 64bit Ubuntu/Xubuntu as main if I get compatibility going with my audio programs. Hence, I don't really see why I would get this.)
    * Intel 5300AGN 450Mbps WLAN (3 antennes)
    * No Flash Drive
    * No OS
    * No Office 2007
    * No Windows Live OneCare 2.0
    * 2 jaar pick up & return garantie
    * No extended pixelcontrole
    * QWERTY (US, internationaal)
```Yup, this setup makes my head go like  :mrgreen:


Moving on, another friend of mine is saying that it's impossible to make a bootable USB stick if the stick itself is not made specially bootable from the factory. Otherwise, you would need a whole lot of information, including PCI clocking and speed information.
Well, I have my doubts about that since I've seen a lot of people using Ubuntu from regular USB-sticks with no apparent problems.

Anyway, thanks for clarifying a few interesting things, I'll keep this thread updated once I get around my new laptop :)

---

### Post by Vinze on 2009-05-22
> **((( ~ ))) said:**
> Well, another setup is coming along in a few days, so testing on 3 systems will significantly maximize the chance of finding out what made my hair turn grey in a couple of days :P

Here are my specs from xxodd.nl :
```

[B]XXODD XNi860tu 15”

[/B]     * Intel Core 2 Quad Q9000 (2,00Ghz, 1066Mhz, 6Mb) Inclusief Game-pack!
    * 4GB DDR3 1066MHz geheugen (2x 2GB)
    * 128GB SATA Solid State Drive (MLC)
    * DVD-CD +/- burner
    * No Intel Turbo Memory module (<<< I'm planning on using 64bit XP for compatibility purposes and 64bit Ubuntu/Xubuntu as main if I get compatibility going with my audio programs. Hence, I don't really see why I would get this.)
    * Intel 5300AGN 450Mbps WLAN (3 antennes)
    * No Flash Drive
    * No OS
    * No Office 2007
    * No Windows Live OneCare 2.0
    * 2 jaar pick up & return garantie
    * No extended pixelcontrole
    * QWERTY (US, internationaal)
```Yup, this setup makes my head go like  :mrgreen:


Moving on, another friend of mine is saying that it's impossible to make a bootable USB stick if the stick itself is not made specially bootable from the factory. Otherwise, you would need a whole lot of information, including PCI clocking and speed information.
Well, I have my doubts about that since I've seen a lot of people using Ubuntu from regular USB-sticks with no apparent problems.

Anyway, thanks for clarifying a few interesting things, I'll keep this thread updated once I get around my new laptop :)

Yep, your friend's wrong, you can use any ordinary USB flash drive (at least mine are). You do need to specifically set it to be bootable (which the USB Startup Disk Creator does for you).

I'm looking out for your results with the third machine :)

---

### Post by Ohsplat on 2009-08-26
I had no problems at all with the Usb installer, the huge jump you see from 20% to 100% is because 1 of the files is like 600mb and all the rest are small. The 600mb file should be a large percent of the install but it seems the install does not move till that files is done then it moves all at once.
 
As far as the USB boot, I also believe its the verson of Linux you are trying to run having issues with your hardware. I have tried a few and had problems on my Hp Mini 1030nr. Backtrack4 is the only distro I have found of Ubuntu 9.04 that makes my sound work. 
 
"Yep, your friend's wrong, you can use any ordinary USB flash drive (at least mine are)"
 
From what I have seen this is more dependant on your computer, and not the USB stick. Your USB stick would have to be like pre 2000 to not be bootable. So in a way I guess there are NON bootable USB sticks but not the ones you buy new as of 2000. I have a pre 2000 usb stick and it will not boot for nothing. After contacting the vendor (sandisk) they informed me that the stick was made when USB sticks were just comming out and who would have thought you would be booting from them? LOL.
 
Hope this helps.

---

