---
title: "No sound on Thinkpad 600E"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by Mankal on 2006-06-08
The Thinkpad 600E is pretty old, is anyone familier with getting the sound working on older laptops?

---

### Post by kebajonathan on 2006-06-09
[*First written on June 9, 2006*]
[*Edited June 12, 2006:* Added the info from Rikostan to my howto (see below) and two links (at the end) that give some helpful infos.]
[*Edited June 21, 2006*: CHANGED Mwave modem configuration. There were some wrong tips... It still doesn't work the way it should, but it's much better...]
**[*Edited June 23, 2006*: CHANGED Mwave modem configuration. It now WORKS!!!]**

**Note, this is now quite old and ther have been several changes. I won't update this any further since I'm putting it on my web page. Please read it there: [http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html"). You'll also find a deb-package for the modem driver there.**

**Sound**

(That's what I did with Ubuntu 5.10, I adapted it to 6.06, but I'm sure if it works... I found it in [http://www.ubuntuforums.org/showthread.php?t=94414](http://www.ubuntuforums.org/showthread.php?t=94414))

	A) disable Quickboot in the BIOS (Press F1 to enter BIOS setup on boot), you may also have to select initialise (still in the BIOS)
	*Next thing in the booted Ubuntu System: *
	B) add these lines to /etc/modules:
```
sound
ad1848
uart401
snd-cs4236
```
	C) Blacklist the incorrect sound card in /etc/modprobe.d/blacklist. Add lines for
```
blacklist snd-cs46xx
blacklist cs46xx
```
	      as written above - with the xx's

	D) Add the following lines into /etc/modprobe.d/alsa-base
```

		alias char-major-116 snd
		alias char-major-14 soundcore
		alias snd-card-0 snd-cs4236
		options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
		alias sound-slot-0 snd-card-0
		alias sound-slot-1 snd-card-1

		alias sound-service-0-0 snd-mixer-oss
		alias sound-service-0-1 snd-seq-oss
		alias sound-service-0-3 snd-pcm-oss
		alias sound-service-0-8 snd-seq-oss
		alias sound-service-0-12 snd-pcm-oss

		alias /dev/mixer snd-mixer-oss
		alias /dev/dsp snd-pcm-oss
		alias /dev/midi snd-seq-oss

		options snd cards_limit=1
```

	   NOTE: [I]When copying and pasting the above, make sure that the line starting with
	    'options...' is one line ending with '...dma2=0'.[/I]

	E) Reboot.

Note: This worked with Ubuntu 6.06 Flight 7, and I haven't tried since. Also it didn't work on another 600e, but I haven't reinitialised my BIOS yet...

Here are some other things you may want to know:

**Get PCMCIA to work:**
Add the following to your kernel options in /boot/grub/menu.lst:
```
acpi=force pci=noacpi
```
It seems that to get wlan (wireless) cards to see the router you need to totally disable acpi.
```
acpi=off pci=noacpi
```
for 1024x768px on statup, add
```
vga=0x317
```

**Mwave Modem:**
Please read [http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html") for more infos.
There also is a deb package for the modem driver.

**disable IPv6:**
change the following line in /etc/modprobe.d/aliases from
```
net-pf-10 ipv6
```
to
```
net-pf-10 off
```

**Speed up Ubuntu:**
select 16bit colours instead of 24bit in /etc/X11/xorg.conf, change 
```
DefaultDepth 24
``` to ```
DefaultDepth 16
```
Select the other apt repositories in Synaptic
Install a i686 kernel using the konsole:
```
sudo apt-get install linux-686 linux-restricted-modules-686
```

Note: *This is mainly Ubuntu 5.10 Stuff. If it doesn't work for you don't clame me, post the corrections so that others can profit...*
Note(2): *suspend and hibernate may not work, you may need a hibernation partition (FAT16) with a hibernation file on it... see [http://pepper.linuxfocus.org/~guido/gentoo-tp600e/]("http://pepper.linuxfocus.org/~guido/gentoo-tp600e/") for more infos.*

Also look at this: [http://www.ubuntuforums.org/showthread.php?t=188736&highlight=thinkpad+600e](http://www.ubuntuforums.org/showthread.php?t=188736&highlight=thinkpad+600e)
Got some more links:
Laptop Testing Team, just as an info:
[https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600E?highlight=%28600e%29](https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600E?highlight=%28600e%29)
**Important:** You may not need to disable ACPI and this script enables sound with almost no user interaction!:
[http://ubuntuforums.org/showpost.php?p=974031&postcount=12](http://ubuntuforums.org/showpost.php?p=974031&postcount=12)

I hope this has been helpful to you...
Greets

---

### Post by Rikostan on 2006-06-11
Just an FYI, this worked on a 600e I installed edubuntu on this morning.
To get a dlink wireless card to actually see the router, I had to add acpi=off to kopt, but that was it. Everything else seems to work fine on this machine.

---

### Post by kebajonathan on 2006-06-12
Just edited the howto a little bit. Have fun.
Keba

---

### Post by zooz on 2006-06-13
Thank you kebajonathan, after trying some howto's that didn't worked yours is the one that saved me.

Thank you, Thank you Thank you.

There's, however, one problem. The sound volume is pretty low. I tried fiddling with the mixer (both sw and hw) and it's still low.

I can live with that if thats the max volume available but perhaps you know a solution to that annoyance?

---

### Post by kebajonathan on 2006-06-13
Have you tried Fn+Home ?
Greets

---

### Post by zooz on 2006-06-15
[QUOTE=kebajonathan]Have you tried Fn+Home ?
Greets[/QUOTE]


Sure, thats what I ment by "hw" when I writen
> I tried fiddling with the mixer (both sw and hw);) 

Anyway it's fine. I just listen on headphones (much better sound anyway) and the volume is fine. Might be hardware problem.

---

### Post by FoggyMtn on 2006-06-16
[QUOTE=kebajonathan][First written on June 9, 2006]
[Edited June 12, 2006: Added the info from Rikostan to my howto (see below) and two links (at the end) that give some helpful infos.]

[

**Speed up Ubuntu:**
select 16bit colours instead of 24bit in /etc/X11/xorg.conf, change 
```
DefaultDepth 24
``` to ```
DefaultDepth 16
```
Greets[/QUOTE]


Hey Ya'll

I'm running xubuntu on my 600e.  When I did the above (reset to 16) and logged out and back in, I lost my panel (I think that's what u call it, the border around my desktop, that shows open apps and clock and menu, etc)

How do I get this back?  What went wrong?

Thanks!

Rob

---

### Post by FoggyMtn on 2006-06-16
I should add I'm running Dapper.  It's proly got something to do with me running xubuntu instead of ubuntu.  Also, I tried the "panels" setting on the desktop, but it won't open anything

At least This got the sound going for me! :D

Rob

---

### Post by kebajonathan on 2006-06-18
Stange... I don't know what could have happened there since this only changes from 24bit-colors to 16bit (That's not a good as 24, but I think it looks much better on these old laptops...)

---

### Post by FoggyMtn on 2006-06-18
Well, that's what I thought ! LOL!!  I'm sure it's nothing in the directions, just my fat fingers pressed what shouldn't have been pressed!

I'm not sure what I screwed up, or where, but something killed my panel...  I tried copying the panel directory from a working user, but that failed.  I wouldn't think that it's in the /etc/ setup, because I would think that was system wide (and other users work).  I've tried starting it manually but it dies on me.

I did try posting a new thread over in the Desktop forums ([http://ubuntuforums.org/showthread.php?t=198469)](http://ubuntuforums.org/showthread.php?t=198469)).  I hated to hijack this one wiht my problems! lol

Oh well, if I can't figure it out or get some help, looks like yet another fresh install!!  :)
(or at least a new user)

---

### Post by RealmMaster on 2006-06-19
Thank you kebajonathan!  I'd been having so much trouble getting things to work on this Thinkpad 600E and I finally switched to 6.06 and 99% of everything worked right after the install (had SO much trouble with Wifi previously), and that 1 last percent?  Yep, the sound.  This did it though. Thanks!

---

### Post by kebajonathan on 2006-06-21
For those who didn't see it: I've just edited the howto. The new version is now on [http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html"). I have mainly edited the modem section and adapted it to Ubuntu 6.06 Final. Have fun.

---

### Post by kebajonathan on 2006-06-23
Hey guys, I got the mwave modem to work!
Read [http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html") for a howto. Have fun.

---

### Post by Newbiejohn on 2006-07-12
I've got a TP 600 that I just installed 6.06 on. I'm also expiriencing the "no sound" problem. I tried to edit the etc/modules file with the text editor, but when I tried to save it, I was told I didn't have permission to do so. How can I do this? Also, does anybody know of a way to enable video hardware acceleration? I had a heck of a time just getting higher than 800x600 resolution.
Thanks!

---

### Post by zooz on 2006-07-13
Newbiejohn,
You need to be root to edit this file.
I recommend reading this - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you just want a short answer:
using console run:
gksudo gedit /etc/modules
You'll be asked for your password - your normal password and be able to edit the file.

About video acceleration. Do you mean 3d? as far as I know there's no 3d accel for this card. Not because of linux. Hardware itself does not have means of 3d accel.

---

### Post by freshman on 2007-04-18
Hello,

I did modify config files as described abow and still don't
have sound in my 600e

Gnome does see the ALSA-mixer and OSS-mixer correctly,
I can change volume level. But when I try to open mp3
in, for instance, XMMS, it reports about problems with
sound device or possibility to such a device to be busy.

I've reinitialized BIOS and disables Quick-boot - same
problems.

Any suggestions?

Thanks in advance!

---

### Post by king20878 on 2007-04-19
Check the XMMS preferences to see what output it is using.  You may need to switch it to the OSS or ALSA output.  Do you have system sounds in gnome?

---

### Post by freshman on 2007-04-20
Hi,
no I don't have Gnome system sounds.
When I try to test sound devices (all of them) from Preferences->Sounds,
I have such an error:
**audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.**

Could it be HW problem?

---

