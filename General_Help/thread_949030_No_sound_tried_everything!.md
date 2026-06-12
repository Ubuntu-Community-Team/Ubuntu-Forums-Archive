---
title: "No sound? tried everything!"
date: 2008-10-15
forum: General Help
---

### Post by adduds on 2008-10-15
i've got a audigy 2 zs sound card.
logitech digital 5.1 surround sound.
i have no system sounds and no youtube.com sounds lol nothing not a peep

been to system--preferences--sound
been to alsamixer
also right clicked on speaker icon to open volume control......

i NEED musick to listen to while I'm working on getting things setup properly 

please help.

cheers,
ad.

---

### Post by forger on 2008-10-15
you've been to system -> preferences -> sound and set everything to pulseaudio?
have you rebooted afterwards?

post the output of:
```
sudo lshw -C multimedia
lspci
```

---

### Post by adduds on 2008-10-15
code sudo lshw -C multimedia

adtoes@adtoes-desktop:~$ sudo lshw -C multimedia
  *-multimedia:0 UNCLAIMED
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=20 mingnt=2
  *-multimedia:1 UNCLAIMED
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0

code lspci

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)

---

### Post by Yellow Pasque on 2008-10-15
Note that you might want to disable your onboard audio in the BIOS if you don't intend to use it.

Your sound cards don't have drivers loaded. See [https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel](https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20the%20ALSA%20drivers%20from%20a%20*fresh*%20kernel)

EDIT: If that doesn't work: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by adduds on 2008-10-15
> **Temüjin said:**
> Note that you might want to disable your onboard audio in the BIOS if you don't intend to use it.


how???

---

### Post by Sef on 2008-10-15
>  	Quote:
 	 	 		 			 				 					Originally Posted by **Temüjin** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5973904#post5973904") 				
 				*Note that you might want to disable your onboard audio in the BIOS if you don't intend to use it.*
 			 		 	 	 
how???

When your computer first starts up, you can push a button to get into the BIOS. Usually this button is either F2, Del, F12, or esc.  It will tell you what button to push.  

Once you are in the BIOS, then look for onboard sound and change it to off.  Directions on the screen will tell you how to do that.

---

### Post by adduds on 2008-10-16
K going into the bios should be relatively easy process to turn off onboard sound.

I have a GStream and/or devices error now when i try to right click on the speaker to open sound preferences?

I'm still not getting anywhere i've even gone as far as purging all alsa drivers and re-installing them fresh

---

### Post by theevilhamster on 2008-10-16
to help stop some possible confusion although it may seen obvious, disabling sound in the bios will not help fix it, it will do the opposite, but if you are not using sound its a good idea to disable it.
hope this helps.

---

### Post by Yellow Pasque on 2008-10-16
Have you used this script yet? [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you can't get ALSA to work, you can also try OSS4 (there's a howto in my sig).

---

### Post by Brandon81 on 2008-10-16
I had a problem with no sound and the way I fixed it was to double click the sound icon in the notification area and to unmute PCM. 

Didn't see that anyone suggested that, so I thought I would.

---

### Post by Richard-g8jvm on 2008-10-16
Hi
Have a look and see if you have pulseaudio active, try disabling it, as pulseaudio and alsa dont mix very well yet.

HTH
Richard

---

### Post by adduds on 2008-10-17
I believe turning off my onboard chipset did the trick! :)

thanks to all that helped, i only have left front, right front, centre and sub?

not the two  rears i have?

i have these speakers

[Logitech Z-5300 5.1]("http://xgame.vn/modules.php?name=Catalog&opcase=detailProduct&pid=386&pcid=261&prid=251&menuid=750")

cheers,
ad.

ps! better than nothing! need my musick! lol

---

### Post by adduds on 2008-10-17
disabling the onboard chipset audio definetly did the trick i believe

although i only have 3.1 sound and should be 5.1

[Logitech Z-5300 5.1]("http://www.ocmodshop.com/ocmodshop.aspx?a=978")

any ideas or experiences???

ps. thanks to all who have helped thus far! having musick is 99% of the reason i go on the computer so to have it while i'm tinkering is essential!

cheers,
ad.

---

### Post by adduds on 2008-10-17
So i can get 5.1 with xmms
But when i use Amarok it's only 3.1?

any ideas or plugins?

cheers,
ad.

---

### Post by adduds on 2008-10-17
found the problem

had to go open amarok

settings-->configure amarok-->engine

under configure xine engine (still in engine window)

speaker output was set to autodetect

switch to alsa

then  under speaker arrangement heading (still in engine window)

select 5.1

I've solved the problem and thought i'd share if anyone else has difficulties

cheers,
ad.

---

