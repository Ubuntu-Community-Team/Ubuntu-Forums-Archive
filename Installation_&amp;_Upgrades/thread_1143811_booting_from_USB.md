---
title: "booting from USB"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by ppb7 on 2009-04-30
As it seems that the family is not yet ready to switch to Linux, i wondered whether I shouldn't try to install ubuntu on a USB drive. However, my question is this: it is stated that, when you boot from a live CD alone, the system is > orders of magnitude slower than is the case when Linux is installed on a HDD. How does that compare with installation on a USB drive?

---

### Post by desmane on 2009-04-30
Hi there, 

Live sessions are slower, I experienced a much faster boot and more stability, running a live session from a usb stick but still, it is kinda slow. 
But of course, that totally depends on the USB stick you own. Since 16gb and bigger sticks are coming, by a more expensive one or two gb stick that has good transfere rates. Use USB Creator to make space for a home folder, cause from live cd you'll loose your session after reboot. Also consider disabling kwins compositing effects, which speeds up my computer as well. 

But my suggestion is dual booting, every family member can choose, if things doesn't work out, simply reboot into windows ;-)

Try this: 

```
sudo apt-get install usb-creator -y
sudo usb-creator
```

---

### Post by ppb7 on 2009-04-30
> **desmane said:**
> Hi there, 

But my suggestion is dual booting, every family member can choose, if things doesn't work out, simply reboot into windows ;-)


Thanks for your quick answer, but dual-booting is unfortunately not an option at the moment. You should have seen the looks of horror when I explained what it was.:eek::shock:

---

### Post by desmane on 2009-05-03
ok I see!! A fast usb stick will be a very nice playground then!

---

### Post by boyofford on 2009-05-03
You could actually do a full install to a usb stick, I'd disconnect your hard drive first though just to be safe!
I had juanty running on a USB stick, in ext4 format and ran very fast from memory on a pentium 4!
Did this just to check would work ok with the hardware, as i didn't have a hardrive yet.
I'm a bit of a newby, but whats the worst that can happen? so you may scrap the usb? doubt it though.

---

### Post by ppb7 on 2009-05-04
> **boyofford said:**
> You could actually do a full install to a usb stick, I'd disconnect your hard drive first though just to be safe!
I had juanty running on a USB stick, in ext4 format and ran very fast from memory on a pentium 4!
Did this just to check would work ok with the hardware, as i didn't have a hardrive yet.
I'm a bit of a newby, but whats the worst that can happen? so you may scrap the usb? doubt it though.
Interesting! But what do you mean by disconnecting your hard drive first:?:

---

### Post by Iusedtowearatie on 2009-05-13
Don't want to upset the family, do we...
Here's what I did:
Download the iso and burn it to a CD. This can be done in Windows using e.g. CDBurnerXP (freeware). Boot your computer from the live CD you just created. Insert your (empty, >1GB) USB stick, wait for it to appear on the desktop (shows it is mounted properly). Under "System" in the menus you will find a tool for creating bootable USB sticks. Just run it...
None of this involves any Ubuntu installation on your Windows machine. I did it using 8.10, and have created a couple of USB sticks this way. What you get is a (non updateable) complete Ubuntu system running from the USB stick, with the ability to save docs etc on the stick - persistence.
Performance? Sure, it is a live version, but on my  Dell Celeron oldtimer peformance is completely acceptable once the system has booted.

---

### Post by ppb7 on 2009-05-22
> **Iusedtowearatie said:**
> Don't want to upset the family, do we...
Here's what I did:
Download the iso and burn it to a CD. This can be done in Windows using e.g. CDBurnerXP (freeware). Boot your computer from the live CD you just created. Insert your (empty, >1GB) USB stick, wait for it to appear on the desktop (shows it is mounted properly). Under "System" in the menus you will find a tool for creating bootable USB sticks. Just run it...
None of this involves any Ubuntu installation on your Windows machine. I did it using 8.10, and have created a couple of USB sticks this way. What you get is a (non updateable) complete Ubuntu system running from the USB stick, with the ability to save docs etc on the stick - persistence.
Performance? Sure, it is a live version, but on my Dell Celeron oldtimer peformance is completely acceptable once the system has booted.
I followed the above instructions, but all I get when I try to re-boot from the stick is the error message: boot error. I tried several times to do an install, but nothing happened. I also followed the instructions on [html]http://www.pendrivelinux.com/usb-kubuntu-810-install-via-usb-creator/[/html] to get a tool for creating bootable USB stick as there is no such tool installed by default on kubuntu intrepid. What am I doing wrong?

---

### Post by tryingtolearn on 2009-05-22
Dear all,

I am having trouble getting Ubuntu Netbook Remix to run or install on my netbook.
I am booting from an USB drive (Transcend 4GB).

I had all the steps right to copying the .img file to USB.
It boots and installs fine on my COMPAQ notebook.

But it just doesn't work for my netbook.
My netbook's platform is running Atom N270 with intel chipset.

It goes fine up till the part where I was given choice to either install or boot w/o installing.
After that a bunch of command lines pop up and it dies there.
The last command line is  

[0.644002] ---[ end trace 4eaa2a86a8e2da22] ---

Can anyone help me to what is wrong with my netbook?

---

### Post by Iusedtowearatie on 2009-05-24
> **ppb7 said:**
> I followed the above instructions, but all I get when I try to re-boot from the stick is the error message: boot error. I tried several times to do an install, but nothing happened. I also followed the instructions on [html]http://www.pendrivelinux.com/usb-kubuntu-810-install-via-usb-creator/[/html] to get a tool for creating bootable USB stick as there is no such tool installed by default on kubuntu intrepid. What am I doing wrong?

Well, it's difficult to say what's happening here.
1) Make sure you have managed to load content on the stick. This you can check using your Windows box. On the stick you should see folders named 
/media/disk/casper
/media/disk/dists
/media/disk/install
/media/disk/pics
/media/disk/pool
/media/disk/preseed
/media/disk/syslinux

plus (in my case) files like

/media/disk/autorun.inf
/media/disk/casper-rw
/media/disk/ldlinux.sys
/media/disk/md5sum.txt
/media/disk/README.diskdefines
/media/disk/syslinux.cfg
/media/disk/umenu.exe
/media/disk/wubi.exe

2) Make sure your BIOS is capable of booting from USB stick, not just from USB HDD or something like that. Try the different options you get access to when you interrupt the standard boot procedure using F2, F3, F10 or whatever is the case in your BIOS.

Hope this helps.

---

### Post by ppb7 on 2009-06-01
I wonder whether my problem doesn't lie with the BIOS. From the pendrive linux site I tried to install various distros on USB sticks, all without success. I follow all the steps listed there yet, when I reboot with the right boot order, I always get a boot error message. They tell me, before reboot, that a hidden file (ldlinux.sys?) has been created bur I never see it. I will try again with kubuntu jaunty, but...

---

### Post by Iusedtowearatie on 2009-06-01
I suggest you try to boot somebody else's computer with the sticks you created. That way you may verify the sticks are correct. This starts to look like your BIOS is not capable of booting from a USB stick.

---

### Post by ppb7 on 2009-06-02
> **Iusedtowearatie said:**
> I suggest you try to boot somebody else's computer with the sticks you created. That way you may verify the sticks are correct. This starts to look like your BIOS is not capable of booting from a USB stick.

I tried on another computer (Vista), but nothing, and in both that one and mine I checked in the boot order that there was an entry corresponding to my stick (at least in mine there was; the vista computer only referred to USB Flash).
BTW, in the BIOS under Advanced the option quick boot mode is disabled, and an entry referring to OS/2 is set to no. should I alter those settings?
+ Looking at your list, i have one extra folder (sysl), no umenu.exe or ldlinux.sys files, a txt.cfg file (which recreates the options menu at the start) and a ubuntu file (empty)

---

### Post by Iusedtowearatie on 2009-06-02
To bad it's not working (yet).

Ubuntu version:
I've only tried it with 8.10. Jaunty may be different.

Sticks:
I've used 1 GB and 2 GB sticks, without any problems whatsoever.

BIOS:
In general, only reasonably new computers are able to boot from a USB stick (in practise). Or, for that matter, computers with upgraded BIOS. I have a Dell from 2005 on which it works perfectly. I have also tried it on HP and on slightly older Compaqs - works well. However, I have never managed to fire up any IBM/Lenovo from USB stick, regardless of manufacturing date... Even though the BIOS options seem to indicate it should be possible.
I noticed that some BIOS:es have two settings; One boot order setting and one "temporary boot device" setting. You may have to check this. Also, check that you actually manage to move the USB stick up to the correct position in the boot order list, otherwise you're bound to get a boot error.

More:
Some good information regarding bugs, USB sizes, various experiments:
[http://ubuntuforums.org/showthread.php?t=1172381&highlight=USB+creator](http://ubuntuforums.org/showthread.php?t=1172381&highlight=USB+creator)
[http://ubuntuforums.org/showthread.php?t=1175597&highlight=USB+creator](http://ubuntuforums.org/showthread.php?t=1175597&highlight=USB+creator)

---

### Post by ppb7 on 2009-06-03
> **Iusedtowearatie said:**
> To bad it's not working (yet).

Ubuntu version:
I've only tried it with 8.10. Jaunty may be different.

Sticks:
I've used 1 GB and 2 GB sticks, without any problems whatsoever.

BIOS:
In general, only reasonably new computers are able to boot from a USB stick (in practise). Or, for that matter, computers with upgraded BIOS. I have a Dell from 2005 on which it works perfectly. I have also tried it on HP and on slightly older Compaqs - works well. However, I have never managed to fire up any IBM/Lenovo from USB stick, regardless of manufacturing date... Even though the BIOS options seem to indicate it should be possible.
I noticed that some BIOS:es have two settings; One boot order setting and one "temporary boot device" setting. You may have to check this. Also, check that you actually manage to move the USB stick up to the correct position in the boot order list, otherwise you're bound to get a boot error.

I am finally throwing in the towel. I tried to install intrepid via a live cd, but nothing happened. I can only assume that my computer is too old (6-7 years old), yet the vista computer i tried as well is under 1 year old. neither has got the abilty to set hdd options or alter bios setings as explained [_there_]("http://ubuntuforums.org/showthread.php?t=1172381&highlight=USB+creator") and, although [_this_]("http://ubuntuforums.org/showthread.php?p=7382174") refers to xubuntu, the main factor is that i am not experienced enough to follow [_the bug instrutions_]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") stated.

---

### Post by ppb7 on 2009-06-09
I thought I'd try one more thing.[_This_]("http://www.tombuntu.com") is an interesting site where I found that you can create a bootable USB stick from an .iso file. I tried it with Kubuntu 8.10. But, on my old computer, all I get is first the prompt, > boot:to which I typed *y* and got the message > couldn't find the kernel image: y then, on the next line, > boot: reappears. On the Vista machine, it didn't even try to boot. :? :?:

---

