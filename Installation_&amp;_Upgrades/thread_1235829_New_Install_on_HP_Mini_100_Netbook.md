---
title: "New Install on HP Mini 100 Netbook"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by xk00zx on 2009-08-09
Hey...
I'm a linux newbie and wanted to know about installing linux on my HP mini 100 netbook. I have no CD drive, but I followed a guide to convert my usb stick into a bootable drive and i put the contents of the latest (9.04) xubuntu on the drive.
I've booted into it and had some questions:
Can I download drivers before I install? (sound/network/wifi/etc) (the "cd" didn't support my sound card - I dont have easy access to try out wifi/network whenever I want)
What are some good Audio/Video Codecs to install? (and whats the easiest way to get them) I need support for everything - i have a rather large library of video/audio that i do NOT want to convert in various encodings (1.6 ghz processor for 200gb+ of mp3s and 700gb+ of video is a bad idea.)
is there linux flash support?
how about java?
PDF reader/creator/editor? (ive normally used FoxIt)
CBR/CBZ reader? (cDisplays what i use for windows - whats the linux equivalent)
ebook reader?
MUD Client?
FTP client?
dos emulator? (i have a selection of old dos games i'd like to play if possible)
messenger that supports aim/msnm?
how about a snes emulator?
can I download all of that prior to installing linux on my machine? - its only got a 16gb harddrive (solidstate) so if i convert, its for good. I dont really see it feasible to leave an xp partition as a backup... although i'm attempting to cut down the space i use for xp right now before i re-partition the drive... - although i've never had good luck with shrinking partitions - always seems to turn my stuff into swiss cheese.
I've already got everything backed up. can i download all of that prior to my install? where can i find what drivers my computer uses for linux?
I'm not even sure I know how to install any of that but i'll figure that out once i can get them downloaded.
 
Thanks for your help!

---

### Post by digitalsp on 2009-08-09
I would suggest installing [Ubuntu Netbook Remix]("http://www.ubuntu.com/GetUbuntu/download-netbook") All the drivers that you need are are included. There are a bunch of distros out there that cater for netbooks. Another good one is Jolicloud - it runs on top of Ubuntu Remix.

---

### Post by aysiu on 2009-08-09
Well, the good news is that Ubuntu (and Xubuntu and Kubuntu, for that matter) come as live/installer CDs (or, this case, USBs).

So you don't have to commit right away, actually.

You can just boot up the live USB and play around with Xubuntu first and see how you like it. This does not affect your SSD in any way until you click the *Install* button.

You can also use Wubi to install Ubuntu inside Windows as a dual-boot with no repartitioning required:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Given the kinds of questions you're asking, I would **highly** recommend against just installing over Windows and wiping it out completely.

---

### Post by jaxxstorm on 2009-08-09
> **xk00zx said:**
> Hey...
I'm a linux newbie and wanted to know about installing linux on my HP mini 100 netbook. I have no CD drive, but I followed a guide to convert my usb stick into a bootable drive and i put the contents of the latest (9.04) xubuntu on the drive.
I've booted into it and had some questions:
Can I download drivers before I install? (sound/network/wifi/etc) (the "cd" didn't support my sound card - I dont have easy access to try out wifi/network whenever I want)


As someone above me said, try the netbook remix, chances are it'll have the correct support for your hardware if its a netbook.

> **xk00zx said:**
> 
What are some good Audio/Video Codecs to install? (and whats the easiest way to get them) I need support for everything - i have a rather large library of video/audio that i do NOT want to convert in various encodings (1.6 ghz processor for 200gb+ of mp3s and 700gb+ of video is a bad idea.)


if, once you've booted and installed, you open a terminal and use the command

```

sudo apt-get install ubuntu-restricted-extras

```

it'll install most if not all the codecs you'll ever need. If you decide to stick with xubuntu, replace the word ubuntu with xubuntu. When you open a file that *doesn't*
 have the correct codecs installed, you'll see the program let you know it can't play, and it'll give you the option to download the correct codec - much easier than windows!

> **xk00zx said:**
> 
is there linux flash support?

yes, the ubuntu restricted extras command above will download and install flash for you.

> **xk00zx said:**
> 
how about java?


open a terminal and do
```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```
and java will be installed.

> **xk00zx said:**
> 
PDF reader/creator/editor? (ive normally used FoxIt)


Foxit is availabe for Linux from [[COLOR="Red"]here[/COLOR]]("http://www.foxitsoftware.com/pdf/desklinux/") - although you'll probably find the PDF reader thats installed suits your viewing needs better. However, a creator editor is trickier, I'm not aware of one that is any good for linux.

> **xk00zx said:**
> 
CBR/CBZ reader? (cDisplays what i use for windows - whats the linux equivalent)


from a terminal again-
```

sudo apt-get install comix

```

> **xk00zx said:**
> 
ebook reader?

have a look [[COLOR="Red"]here[/COLOR]]("http://www.fbreader.org/desktop/debian.php") for an ebook reader

> **xk00zx said:**
> 
MUD Client?


```
 sudo apt-get install gnome-mud
```

> **xk00zx said:**
> 
FTP client?

```
 sudo apt-get install filezilla
```

> **xk00zx said:**
> 
dos emulator? (i have a selection of old dos games i'd like to play if possible)


DosBox works under Linux. You'll have to enable the universe repository, there are instructions for installing DosBox [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/DOSBox").

> **xk00zx said:**
> 
messenger that supports aim/msnm?

Pidgin is installed by default and supports AIM and MSN along with lots of other protocols.

> **xk00zx said:**
> 
how about a snes emulator?


```
 sudo apt-get install zsnes

```

> **xk00zx said:**
> 
can I download all of that prior to installing linux on my machine? - its only got a 16gb harddrive (solidstate) so if i convert, its for good. I dont really see it feasible to leave an xp partition as a backup... although i'm attempting to cut down the space i use for xp right now before i re-partition the drive... - although i've never had good luck with shrinking partitions - always seems to turn my stuff into swiss cheese.
I've already got everything backed up. can i download all of that prior to my install? where can i find what drivers my computer uses for linux?
I'm not even sure I know how to install any of that but i'll figure that out once i can get them downloaded.
Thanks for your help!

I'm willing to bet good money that even after installed all of the above, it only uses approximately 200mb. The biggest download will be the java environment at a guess. You can do all the installs in the live CD environment and try everything out before you go ahead and install, if you decide you **DO** want to install from here, you can install and all the apps you've added will come with you. If you reboot before then, you'll have to add them again.

As for drivers, Ubuntu doesn't work like Windows, you don't have to go and find drivers, they are all built in, you just need to activate the right ones. Its usually done when you first install, but if it isn't there are lots of helpful people on these forums that will help you.

Good luck if you decide to try Ubuntu :guitar:

---

### Post by aysiu on 2009-08-09
The Ubuntu Netbook Remix uses the regular i386 kernel. It does not have better hardware detection of netbooks than regular Ubuntu does. And the lpia kernel (which, again, the UNR does *not* use) isn't for hardware detection but really for better battery life (and only marginally so).

---

### Post by nogeek on 2009-09-11
____________________________________

I'm glad to have found this forum. 

I too am trying to install Ubuntu on a HP 110 1000 netbook. 

Never have I seen so many confusing suggestions and instructions to what I would think should be fairly simple. Or, more likely, I'm not so bright. 

I'd like to install Netbook Remix [I think] 

I have no external CD available. 

I have a 2 GB Hi-speed 2.0 USB drive. 

The HP has XP Home installed on a 160 NTFS non-partitioned hard drive. 

Would someone be so kind as to walk me through this install step by step? Please, please, please, assume I know absolutely nothing about what I need to do. In other words, kindly explain a few things as we go. Like why you suggest this or that needs doing, as opposed to something else. 

Thanks so much. 

nogeek

---

### Post by nogeek on 2009-09-11
Well, used Netbootin to try to download Netbook Remix, not one of the options, so went with Linux Mint, which has been recommended.

Download complete, rebooted, choose USB drive as boot option, pretty Linux Mint screen came on the monitor, and that's it. 

Nothing. Frozen. 

Cold rebooted, [ouch] hit F10 to see which boot option was operating, hard drive, not USB even though I previously chose USB. Windows came up as normal. 

rebooted, change to USB option in compatibility mode, lines of DOS script shows up ending with Loading Hardware drivers, and then IRQ 10 and the flashing curser at the bottom of the screen. Frozen. Again. 

Did notice in one line something about Proprietary **** [something] tainted kernal. 

Again, cold reboot. Windows comes up. Restart, F10, change boot option to USB, save and exit, Windows comes back up. 

Restart, change boot device priority again, run in "Boot from local drive." list of DOS script comes up, then nothing. Noticed some possible problems listed. 

Restart, get End Program CsSvcHSt notice. 

I notice the Boot Device Option won't remain on USB Toshiba Mode, I have to reset each and everytime. 

Did MS program Windows to prevent dual boot options? 


Now what anyone? Any ideas? 

Thanx

____

---

