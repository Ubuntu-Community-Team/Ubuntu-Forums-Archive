---
title: "ATI x1300 Feisty Fawn"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by kungfooguru on 2007-04-23
I just installed Feisty Fawn on a machine with an ATI x1300. I was running Xenwalk and had successfully setup the binary ATI driver (the card requires the binary driver, xorg defaults to vesa for the card). Now that I've switched to Ubuntu I can't figure out why the fglrx drivers completely crash the system. It is not on modprobe but during X starting up. I've followed instructions I've found online, multiple ones. Nothing works. No matter what I try when X starts with fglrx the screen goes blank and the system is completely unresponsive, no ctrl-alt-F1, no sshing in, nothing. 

Has anyone successfully setup a x1300 with the binary drivers in Feisty Fawn? This is with the ati-driver 8.36.5 and the kernel that comes with Feisty Fawn, 2.16.20-5.

Thank you,
Tristan Sloughter

---

### Post by jonnymccullagh on 2007-04-23
I've got a brand new laptop with the ATI x1600 and I am pulling my hair out - I cannot even run the LiveCD never mind installing it!
There is info [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853") which may help you.
Anyway good luck - you are much further on than me!

---

### Post by ~SkyBlue~ on 2007-04-23
You may want to try generic vesa driver. Crap quality but it will do the most basic job.

run
sudo dpkg-reconfigure xserver-xorg

and when it get to driver selection, choose vesa, reboot

---

### Post by @Ndrejjj on 2007-04-25
Hi! I've get the same problem with any ATI driver after 8.32 :( - i.e. black screen of death. But I've noticed :
1. Computer died when loaded  /usr/lib/xorg/modules/linux/libfglrxdrm.so
2. it module compiled for Xorg.7.1, but other modules - for 7.2

---

### Post by guardsman85 on 2007-04-25
Seems there's an old fglrx driver that you have to blacklist.  I followed the instructions at [http://tinyurl.com/2wv7jd](http://tinyurl.com/2wv7jd) and my ATI card has been working just fine for two days now.

---

### Post by @Ndrejjj on 2007-04-25
> **guardsman85 said:**
> Seems there's an old fglrx driver that you have to blacklist.  I followed the instructions at [http://tinyurl.com/2wv7jd](http://tinyurl.com/2wv7jd) and my ATI card has been working just fine for two days now.

I did try that instruction! Result is the same. Actually I tried all of them. 
Then I've done next:
1. Delete all deb fpr 8.36 :
   xorg-driver-fglrx_8.36.5-1*.deb
   fglrx-kernel-source_8.36.5-1*.deb
  dpkg -i fglrx-amdcccle_8.36.5-1*.deb
2. sudo apt-get install xorg-driver-fglrx

Wow! It's working!!!! BUT WITHOUT OPEN GL !!! :mad: 
and now this is my log:
andrejjj@ta4ka:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): GART is not initialized, disabling DRI
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

I've attached xorg.conf and Xorg.0.log
P.S. Sorry for my English

---

### Post by strabes on 2007-04-25
For those of you struggling to run the live CD, you have several options. Once you hit the black screen of death, you can hit ctrl+alt+f1, log in, and run "sudo dpkg-reconfigure xserver-xorg"

Or, you can download and install the alternate install CD from the ubuntu website.

Or, you can install the fglrx drivers from the command line following the steps on the following website, using nano instead of gedit. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by mrThefter on 2007-04-25
Note: Using 64bit Feisty? I've got the same problem in 64bit.

After narrowing it down, the error that happens is a Signal 11. I found that it's very similar to the Signal 11 that occurs when you try to set a manual modeline. Additionally, fglrx causes the Signal 11 after detecting all the modelines your monitor is capable of (module ddc)
The crash happens before the loading of module fb, and it seems the offending driver function is: swlDalHelperValidateModeFromDAL+0x549

After this call, libc tries to do something, which results in a Signal 11.

EDIT: I found out that ddc is the offending module. After reading the modelines for a monitor, then attempting to set a modeline, it crashes. When I disabled the ddc module (hacky method..don't ask for it) I was able to boot into X. However, I don't have acceleration. GART wasn't initialized. Still looking into this.

EDIT2: GART initialization was my problem. Fixed. (fglrx module didn't load. I forgot to do a depmod) Disabling DDC might help, but since NoDDC doesn't work for the fglrx drivers, just comment it out up a bit in xorg.conf, then rename /usr/lib/xorg/modules/libddc.so to something recognizable (so you can restore it later)

---

### Post by PaganBlasphemy on 2007-04-27
I'm another user with a Dell C521, an ATI X1300 card, and a black screen when trying to use the proprietary drivers.

mrThefter, could you explain in a little more basic terms and steps what you found and how you fixed it?

Thanks!

For what it is worth my log file ends with this entry:

  [INDENT]drmGetBusid returned ''
  (II) Loading sub module "fglrxdrm"
  (II) LoadModule: "fglrxdrm"
  (II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
  (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.34.8
        ABI class: X.Org Server Extension, version 0.3[/INDENT]

And then nothing else...

---

### Post by pezmanlou on 2007-04-27
i have an x1300 and the live cd worked fine for me but when i restarted, i got all of these problems and could only do things in command line so i installed gnome and fglrx

```
sudo aptitude install gnome
sudo aptitude install fglrx-driver
```

after that everything seemed fine, but i could not get the resolution past 1024x768 so i used this tutorial to install the proprietary ati drivers.  

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

and now i cant get the resolution past 600x800 and fglrxinfo says its using the mesa driver again.  but at least gnome runs.

---

### Post by mrThefter on 2007-04-27
@ PaganBlasphemy
That's a rather odd log. Nothing, huh?
Well, my problem was 64-bit based, mostly, I think. Setting the screen's mode seems to make my XServer quit with Signal 11. I'm able to boot into X (with DRI) if I remove the ddc module from my modules folder, but I still get the same Signal 11 backtrace if I change monitor modes within an OpenGL application.
As for your problem...there's no error, so that's a toughie..Could try disabling ddc to see if it helps.

---

### Post by KLineD on 2007-04-29
> **mrThefter said:**
> 
EDIT: I found out that ddc is the offending module. After reading the modelines for a monitor, then attempting to set a modeline, it crashes. When I disabled the ddc module (hacky method..don't ask for it) I was able to boot into X. However, I don't have acceleration. GART wasn't initialized. Still looking into this.

EDIT2: GART initialization was my problem. Fixed. (fglrx module didn't load. I forgot to do a depmod) Disabling DDC might help, but since NoDDC doesn't work for the fglrx drivers, just comment it out up a bit in xorg.conf, then rename /usr/lib/xorg/modules/libddc.so to something recognizable (so you can restore it later)

Do you mind telling me how to get GART to initialize correctly? that's what's happening to me GART doesn't initialize, fglrx isn't loaded

---

### Post by EtienneG on 2007-04-30
The best would be for people to report this problem as a bug in Launchpad.  I understand the problem is with a binary driver (and thus cannot be fixed), but at least recording the details somewhere people can refer to would be good.

Searching for "fglrx" in the Ubuntu bugs section of Launchpad, I found two recent reports that look somewhat like the problem being discussed in this thread :

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106600](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106600)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105788](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105788)

---

### Post by Zenchess on 2007-04-30
I am also having this black screen of death issue with my ati radeon x1900 card - I have tried several guides, installed the latest driver, etc. etc. but nothing worked.  I even tried envy, but I didn't expect it to work and it didn't.  

If you find a solution please post a follow up here.

---

### Post by Cloud22 on 2007-04-30
Yes, please post a solution if you get it. I have a x1300 as well and for the life of me (see my only topic) I can't get it to work. I must have spent atleast 15 hours trying to get this thing to work with no success.

---

### Post by kungfooguru on 2007-05-01
The weird thing is I see other people with working x1300 on Feisty. The ones with threads trying to get xgl working or 3d working, when ours don't work at all. Very odd. I hope one of them can shed some light on to what we are doing so wrong.

---

### Post by Cloud22 on 2007-05-01
DMcCann87 has got his to work. He has the exact same card as me. The visiontek version of the X1300 with 512MB ram. I used the same driver he has, installed it the same way, and I even used an exact copy of his conf file, all leading to the black screen!

---

### Post by mrThefter on 2007-05-01
i simply did a depmod -ae after installing the fglrx MODULE to get GART working

---

### Post by Cloud22 on 2007-05-01
So what drivers support our card? The X series.
The radeon/ATI open source don't work.
The ATI fglrx is a pain in the.... to get it to work.
And vesa doesn't support 3D accel.

If anyone found a way to do it, please post here!

---

### Post by kungfooguru on 2007-05-02
I don't need 3D myself. I just want this second monitor not to be bought for nothing :)

---

### Post by mrcoffee09 on 2007-05-03
I've been using ubuntu all of 3 days.  I tried feisty fawn (with my Radeon X1300) and it worked fine.  Then I was like, dude, i need beryl.  So I followed some instructions on some wikipedia look alike site, and I kilt it.  By kilt, I mean Killed x12.  I've just been using the regular [www.ati.com](www.ati.com) drivers.  If you figure out a good driver or something please tell me.  Im rather clueless.

By the way, I decided not to fix ubuntu, i just reformated and reinstalled :P

---

