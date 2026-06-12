---
title: "Tweaking the thinkpad 600"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by gotaserena on 2006-06-04
Hello,

If you have this amazing machine and tried to install ubuntu in it you may have come across some problems. Most of these have to do with pccard support (formely known as pcmcia) and the dreaded sound card. I've managed, through a lot of help from fellow ubuntu'ers, to solve them in a satisfactory manner.

Part of the problem so far is that most of the solutions I've come across involve turning ACPI support off at the kernel level. Aside from disabling part of the BIOS calls which are very useful for laptop users, kernel developpers have also turned APM support off as of 2.6.15. Turning ACPI off is a dead-end street.

Caveat emptor: I can vouch for this instructions on the **thinkpad tp600 alone**. If you have some other model, like 600E or 600X, it may or may not work.

Before start you'll need to disable fast boot at the BIOS level. This can be done by pressing and keep pressed F1 when you turn the machine on. After the start screen you'll see the boot menu. Click on "Config" and then on "Quick Boot". Click on "Disable", go to the main menu and restart. Now that your BIOS is set, on to the solutions:

[LIST=1]
[*]Problem: My video resolution is screwed up.
Cause: Ubuntu tries to use 24bpp for the default 1024x768, which is not supported by the video card.
How to solve it: edit /etc/X11/xorg-conf and find the "Screen" section. Change the DefaultDepth to 16. Now restart the X server (ctr-alt-backspace) and you should be set

[*]Problem: Sound doesn't work.
Cause: Sound card that ships with the thinkpad 600 is made before the dawn of time and needs to be configured manually.
How to solve it: First, edit your /etc/modules and add the line "snd-cs4236" to it. Now back up your /etc/modprobe.d/alsa-base and write this in it instead:
```

alias char-major-116 snd
alias char-major-14 soundcore

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-css
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
alias sound-slot-2 snd-card-2
alias sound-slot-3 snd-card-3

alias sound snd-card-0
alias snd-card-0 snd-card-cs4236

alias snd-minor-oss-0 snd-card-cs4236
alias snd-minor-oss-1 snd-opl3
alias snd-minor-oss-3 snd-pcm-oss

options snd-cs4236 port=0x530 cport=0x538 mpu_port=-1 fm_port=0x388 irq=5 dma1=1 dma2=0 isapnp=0 sb_port=0x220

install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

```

Now run "sudo depmod -a". Open /boot/grub/menu.lst. Find the line that begins with "# kopt="... and append this to it:
```
acpi=force pci=noacpi pnpbios=off pci=usepirqmask
```
As a suggestion, find the line that begins with "# defoptions" and append this to it:
```
 vga=0x316 resume=/dev/hda2
```
save and exit. Now run "sudo update-grub". Reboot. If nobody has changed the IRQ assignment at BIOS, then sound should work while keeping nice ACPI support like suspend to disk, suspend to ram and battery/temperature info.

[*]Problem: My modem doesn't work.
Cause: See item 2. Now the problem is even worse since the modem shares an IRQ with the serial port. Disable the serial and the modem will work. 
How to solve it: Get mwave to work with the serial port on. If I get it I'll post it here.

[*]Problem: Suspend and Hibernate don't work.
Cause: Some modules don't have power management support.
How to solve it: edit /etc/default/acpi-support as follows 
1) Uncomment ACPI_SLEEP:
```

ACPI_SLEEP=true

```

2) Change ACPI_SLEEP_MODE to "standby". I couldn't make suspend-to-ram work with S3 sleep. 
```

ACPI_SLEEP_MODE="standby"

```

3) Find the line beginning with "MODULES". Make it look like:
```

MODULES="snd-cs4236 acx"

```
you should also add known "problematic" modules like those of wlan cards -- acx in my case.

And, last but not least, if you are on GNOME or XFCE, open gnome-power-preferences and go to "general" and select "suspend" or "hibernate" for the default action of the sleep button. KDE users have the analogue klaptopmode with similar capabilities but I don't know how to configure it.
[/list]

Hope this will be useful.

EDIT: I forgot to say that the "pci=noacpi" option at the kernel level was the most important to get the my PCCard working. I've got a D-Link GW-650+ (based on the chip TI100, or the acx module) working *only* after passing this option on at boot.

---

### Post by Sea5446 on 2006-06-04
This is a great resource! but forgive my newbie linux ignorance but some of these files are read only. Can anyone tell me how to change this so i can save these settings? :confused: 
THNKS

---

### Post by stimpsonjcat on 2006-06-04
Sea 5446
read this: [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")
to edit e.g. the file /etc/modprobe.d/alsa-base type
```
gksudo gedit /etc/modprobe.d/alsa-base
```
oh, and welcome to ubuntu! :)

---

### Post by vmoutsop on 2006-06-06
I would like to interject an even more basic question, I have a 600E and cannot even get ubuntu to load/install automatically through a CD boot.  I think I would be able to change the video settings if I could get to them.  

Any ideas on how to boot/install from live or desktop cd (v6.06) and at least be able to install the OS?

Very frustrated.

Thanks:confused:

---

### Post by stimpsonjcat on 2006-06-06
vmoutsop, you can change the video settings at the boot prompt (it's one of the F keys, don't remember which). it's called something like "safe video settings".
you could also try the "alternate" (text mode) install CD.

---

### Post by kebajonathan on 2006-06-09
I think he doesn't even get there. Here is what you have to do:

Press F1 while starting the Computer and keep it hold until the THINKPAD screen disappears. You will get to the BIOS. 
There, choose **start up** (you can now navigate with your built in mouse, use the left mouse button for everything you do inside the BIOS).
Now click on the **Power-ON**-Button
Click on **Reset**. After this, click on the following icons in this odrer:
1) **FDD**
2) **CDROM**
3) **HDD-1**
Now, accept with *OK* and **Exit**, then **Restart** and **OK**.
Your Ubuntu-CD has to be in the drive when the computer boots, so it has to be inside before the THINKPAD screen has disappeared. It will now boot from CD.

Good Luck

BTW: **For IBM Thinkpad [COLOR="Red"]600E[/COLOR] ** (not 600 nor 600X)
I have written a similar Guide to the one above : [http://www.ubuntuforums.org/showthread.php?p=1117587#post1117587](http://www.ubuntuforums.org/showthread.php?p=1117587#post1117587)
It includes the Mwave Modem support infos, PCMCIA support, wlan PCMCIA and a link to a script for getting the sound to work on Thinkpad 600e for those interested.

---

### Post by conxorxa on 2006-06-18
Thanks for posting this.  It was very helpful.  I am also trying to get dapper working on a thinkpad 600.

Unfortunately, I could not get my sound working.  dmesg gives the following error:
CS4236+ soundcard not found or device busy

Also, my wireless card (DLink DWL-G650) works sometimes but not others.  I haven't been able to find a pattern.

Any suggestions?

---

### Post by gotaserena on 2006-06-25
What is the output of:
```
# cat /sys/devices/pnp0/00\:05/resources
# cat /sys/devices/pnp0/00\:06/resources
```

---

### Post by kebajonathan on 2006-06-27
Simply reinitialise your BIOS. Sound should work afterwards. For PCMCIA, see [the 600E page of my home page]("http://www.mueller.ch.vu/misc/tp600e_en.html"). 
cu

---

### Post by conxorxa on 2006-07-10
Thanks for the suggestions.

Reiniting the BIOS fixed the sound but my wireless card is still flaky.

I'm not sure if the sys/devices output was for the sound or the wireless, but here it is:

# cat /sys/devices/pnp0/00\:05/resources
state = active
io 0x538-0x53f

# cat /sys/devices/pnp0/00\:06/resources
state = active
io 0x530-0x537
io 0x388-0x38b
io 0x220-0x233
irq 5
dma 1
dma 0


Is that good or bad?

---

### Post by gotaserena on 2006-07-16
Good that the sound is working for you, I've got to remember the reinitialize the BIOS thing. About your network card, we need to have more information...

What do you mean by "sometimes it works"? Does removing and reinserting (via cardctl eject) the card helps? Or is it a full reboot? What is the PCMCIA/cardbus related output from dmesg in both cases?

I edited the first post to include support to suspend and hibernate.

---

### Post by conxorxa on 2006-07-24
Both.  Occasionally the card will work right after booting.  Occasionally it works after ejecting/reinserting the card many times.  Most of the time it doesn't work after many eject/reinsert attempts.  dmesg isn't particularly helpful.  The only related message I could find is (although there may be related messages that I don't recognize):
pccard: CardBus card inserted into slot 0
When I eject the card (with pccardctl eject) I get:
PCMCIA: socket c8165028: *** DANGER *** unable to remove socket power

When the card isn't working, it isn't even listed in the lspci output and the ath_pci modules aren't loaded.  But when it is working, it is listed and the modules are loaded.

It isn't a hardware problem because the card works consistently under Windows.

---

### Post by gotaserena on 2006-07-28
I may be over my head here, but it may be possible that you either have a problem with the thinkpad configuration (like not being able to share the IRQ 11 that the pccard slot uses) or it may be a problem with hardware -- card or controller. Does the Yenta output from dmesg look OK?

---

### Post by mvd on 2006-08-01
Great resource! All my tp600 features are working. Yet, I think that first one should go to the bios and turn off Quick Boot.


Thanks very much!!

Miguel

---

### Post by mvd on 2006-08-01
Hi, I noticed that the fan keeps working even if the notebook is suspended. Is this normal ? (I made the chanes to acpi-support indicated in the main thread) 

Thanks!

---

### Post by gotaserena on 2006-08-01
this suspend mode is "standby" which doesn't really turn the processor off like "mem" which keeps power to the memory only. When and if I manage to get the S3 suspend-to-ram working I'll post the conf files here.

---

### Post by conxorxa on 2006-08-11
It's not a problem with the hardware because as I said the card works perfectly under Windows.  I'm not sure what that means for sharing IRQ 11.  Is it possible for that to work under Windows but not Linux?

Here's the Yenta output from dmesg:

~> dmesg | grep -i yenta
[10747.417879] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0092]
[10747.417929] Yenta: Enabling burst memory read transactions
[10747.417953] Yenta: Using CSCINT to route CSC interrupts to PCI
[10747.417971] Yenta: Routing CardBus interrupts to PCI
[10747.417998] Yenta TI: socket 0000:00:02.0, mfunc 0xfba97543, devctl 0x62
[10747.648339] Yenta: ISA IRQ mask 0x0698, PCI irq 11
[10747.696100] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0092]
[10747.696151] Yenta: Using CSCINT to route CSC interrupts to PCI
[10747.696170] Yenta: Routing CardBus interrupts to PCI
[10747.696199] Yenta TI: socket 0000:00:02.1, mfunc 0xfba97543, devctl 0x62
[10747.928267] Yenta: ISA IRQ mask 0x0698, PCI irq 11


> **gotaserena said:**
> I may be over my head here, but it may be possible that you either have a problem with the thinkpad configuration (like not being able to share the IRQ 11 that the pccard slot uses) or it may be a problem with hardware -- card or controller. Does the Yenta output from dmesg look OK?

---

### Post by anothertallorder on 2006-08-31
Screen works fine, but having trouble with the sound.
I followed the instuctions and append the menu.lst but on reboot I freeze at "Mounting root file system"
Any idea's I have to 'vi' into the menu and take out the lines to get it to boot.

---

### Post by gotaserena on 2006-09-23
@ conxorxa: Sorry, I'm not sure I can help you there. I for one have a wifi card that works perfectly under windows and my DVD player which runs some isolinux based on kernel 2.4. Never got it to work on my two 2.6 machines

@ anothertallorder: Can you post your /boot/grub/menu.lst and the output of 'sudo fdisk -l /dev/hda'?

---

### Post by pablo180 on 2006-09-25
> **anothertallorder said:**
> Screen works fine, but having trouble with the sound.
I followed the instuctions and append the menu.lst but on reboot I freeze at "Mounting root file system"
Any idea's I have to 'vi' into the menu and take out the lines to get it to boot.

I have the same problem but I can't get it to boot at all! What is 'vi'?

Now I am stuck without my laptop and it looks like I may have to reinstall Ubuntu again.

EDIT: It's OK I figured it out and got it to boot and have taken those lines out of the menu.lst file. It boots but still no sound.

---

### Post by borris.morris on 2006-12-01
I just added acpi=force pci=noacpi to the /boot/grub/menu.lst file so it looked like this:> title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash acpi=force pci=noacpi
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

Now all is well, except sound doesn't work after standby. Anybody else have that problem?

---

### Post by Worbc on 2006-12-05
> **kebajonathan said:**
> Simply reinitialise your BIOS. Sound should work afterwards. For PCMCIA, see [the 600E page of my home page]("http://www.mueller.ch.vu/misc/tp600e_en.html"). 
cu

How do I reinitialise your BIOS?  I've got everything working on this Thinkpad 600X except for the sound card and I have completed all steps above.

thanks,

--terry

---

### Post by MMikeC on 2006-12-11
Your advice worked great! The graphics on my Thinkpad 600 are now crisp and clear and my sound works. Thank you very much! 

I tried to install Ubuntu onto my Thinkpad a few months ago but I could never get past the ready to install because all I got were errors. Last night I decided to try to install Kubuntu and it worked! 

I had SimplyMepus 6 on my laptop for a few months. Which worked good except for the Laptop locking up on me 3 out of 4 times during the bootup. I usually had to unplug the Laptop and take the harddrive out to get the screen darkened. I do have Ubuntu Dapper, SimplyMepis 6, Fedora 5 and WinXP all on my Desktop.

I even tried MepisLite based on Debian Sarge without any problems but there was no support for it even in their community forum.:-D

---

### Post by davinci on 2007-02-27
Thx for the great How-to Gotaserena! 

The harddisc of my TP600 just died and so I replaced it with a new one and installed Edgy (I have used Dapper previously).
 
I made the same changes as in Dapper (basically the same as your howto) but sound did not start working again. After viewing the syslog I noticed that the kernel loads snd-cs4232 at startup which blocks the snd-4236 module.

So I have blacklisted the modules snd-cs4231 and snd-cs4232 in /etc/modprobe.d/blacklist and sound is working again. Hope this helps someone else too. 
  
In addition with the option pnpbios=off my WLAN-card (atheros based) is not working, so I don't use this option.

---

### Post by davinci on 2007-02-28
OK time for the next tweak! :) 

Edgy seemed to be considerably slower than my previous install, so I checked my configs again.

I noticed that Edgy uses "vesa" as video driver, which is considerably slower than the "neomagic" driver (the TP600 uses a Neomagic video-chip). After changing that the desktop is much faster (dragging windows, scrolling, ....) so be sure to check your installation too.

1) Check your /etc/X11/xorg.conf

Search the line "Identifier "Generic Video Card"
The line below should be: "Driver "neomagic"
If the driver is "vesa": Change it!

2) Add the module "neofb" to your "/etc/modules" file

---

### Post by Topdos on 2007-03-31
I got my sound working ok thanks to Gotaserena's great How-to.  After applying the changes, normal boot freezes up, but I can get it to run by going into recovery mode at the Grub menu, let it load up to the root prompt, then typing exit and it completes bootup, with sound working ok.  Weird.  I'm going to try disabling services that I don't use anyway (like bluetooth) and see if that fixes the boot problem. (this is on a ThinkPad 600, 266mhz, 160mb RAM).

I have the same problem as Gotaserena with the modem, thought I'd try dropping in an old hard drive with Win95 and use ThinkPad configuration to disable the serial port.  We'll see how it goes.

---

### Post by freshman on 2007-04-18
> **kebajonathan said:**
> Simply reinitialise your BIOS. Sound should work afterwards. For PCMCIA, see [the 600E page of my home page]("http://www.mueller.ch.vu/misc/tp600e_en.html"). 
cu
Hello,

I did modify config files as described at your site and still don't
have sound in my 600e

Gnome does see the ALSA-mixer and OSS-mixer correctly,
I can change volume level. But when I try to open mp3
in, for instance, XMMS, it reports about problems with
sound device or possibility to such a device to be busy.

I've reinitialized BIOS and disables Quick-boot - same
problems.

In some other thread I've read about problem with sound if acpi 
is enabled. A have acpi=force pci=noacpi option, PCMCIA cards
do not work without it

Any suggestions?

Thanks in advance!

---

### Post by freshman on 2007-04-18
> **gotaserena said:**
> What is the output of:
```
# cat /sys/devices/pnp0/00\:05/resources
# cat /sys/devices/pnp0/00\:06/resources
```
Hello,
I don't have sound as well, after following the configuration
instruction from some thread.

Gnome Volume control does show ALSA and OSS mixer
features correctly. But I can't get any audio program working.
Here is my outputs
```

$ cat /sys/devices/pnp0/00\:05/resources
state = disabled
io 0x3f8-0x3ff
irq 4
dma 3

$ cat /sys/devices/pnp0/00\:06/resources
state = active
io 0x538-0x53f 

```

Any suggestions?

Thanks in advance!

---

### Post by gotaserena on 2007-04-21
Good news, everyone!

After a long last I fixed my tp600 and can continue helping here. The LCD cable (the one that goes on the right hinge) broke and the LCD would not show anything. After a new LCD inverter and a battery (its 4th!) the little thing will be on to its 10th anniversary in style! 

This howto works for feisty as well, and the new version of setpnp seems to work with acpi, so there is a chance of finally getting the modem working. I've also to sort the hibernate stuff. Suspend-to-ram seems to work tho.

@freshman:
Your sound control registers are disabled. You can enable them with
```
echo 'activate' >/sys/devices/pnp0/00\:05/resources
```
Be careful with the number, in feisty (kernel 2.6.20), these numbers are rearranged.

---

### Post by hellion0 on 2007-09-16
Good thread, it helped with the resolution and standby issues at least. However... you guessed it, there's no sound, even after applying the fixes from the first post. (I'm running Feisty now.)

Gnome volume-control does not report a soundcard at all.

Running dmesg | tail at prompt gives me this after trying to manually modprobe for the card (snd-cs4236):
```
[10089.799362] CS4236+ soundcard not found or device busy
```

I tried the two cat commands from earlier as well:
```
taralyn@altaria:~$ cat /sys/devices/pnp0/00\:05/resources
state = disabled
io 0x3f8-0x3ff
irq 4
dma 3
taralyn@altaria:~$ cat /sys/devices/pnp0/00\:06/resources
state = disabled
```

Obviously they're disabled, so I tried activating them as above, but even with sudo I can't get them to work - permission denied in every case.

Sound does work under Win2k, so it's not a hardware issue.

I've hit a brick wall as far as configuring the Thinkpad is concerned, and I'm completely out of ideas. Everything else works, or at least works the way I want it to, but there's no sound. Any ideas or help?

---

### Post by fbollens on 2007-11-02
Fine and very clear tweaking, but I can't find /etc/modules in 7.10

---

### Post by fbollens on 2007-11-03
sorry,for my previous question, perhaps to late at night:oops:
Still my question exists, I carefully did what to do but in 7.10, no sound at all.
With dmesg I see this for the sound:
  58.988000] CS4232 WSS PnP manual resources are invalid, using auto config
[   58.988000] CS4232 WSS PnP configure failed for WSS (out of resources?)
[   58.988000] PnP BIOS detection failed for CS4232
[   59.000000] pnp: Device 00:07 disabled.
Maybe someone has an hint for me

---

### Post by dotsi on 2007-11-10
> **fbollens said:**
> sorry,for my previous question, perhaps to late at night:oops:
Still my question exists, I carefully did what to do but in 7.10, no sound at all.
With dmesg I see this for the sound:
  58.988000] CS4232 WSS PnP manual resources are invalid, using auto config
[   58.988000] CS4232 WSS PnP configure failed for WSS (out of resources?)
[   58.988000] PnP BIOS detection failed for CS4232
[   59.000000] pnp: Device 00:07 disabled.
Maybe someone has an hint for me

I get that too:

```
lauri@ibari:~$ dmesg | grep cs4
[   39.560000] cs4232-pnpbios: probe of 00:07 failed with error -16
[   42.216000] ad1848/cs4248 codec driver Copyright (C) by Hannu Savolainen 1993-1996
lauri@ibari:~$ dmesg | grep CS4
[   39.548000] CS4232 WSS PnP manual resources are invalid, using auto config
[   39.548000] CS4232 WSS PnP configure failed for WSS (out of resources?)
[   39.548000] PnP BIOS detection failed for CS4232
```

EDIT: I don't know what the problem was, but [this script]("http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode") solved it.

---

### Post by Rob_Frohne on 2007-11-20
Thanks for the note above.  I have a few questions though.  

1)  I'm using a 600, not 600E.  What were you using?
2) Did you use the alsa-base file that came with Gutsy or the one from the original article "Tweaking the thinkpad 600?"

I haven't been able to duplicate your success yet.

Thanks,

Rob

---

### Post by richardh9936 on 2007-12-23
Very good info.  
I've used it today to get FluxUbuntu going really well.  FluxUbuntu didn't run in the correct video mode.  

To all those people trying Ubuntu on Thinkpad 600, I recommend FluxUbuntu.

Richard.

---

### Post by bdemers on 2008-02-25
After reading through, and trying virtually all that has been discussed, I still an unable to activate my sound.  One question went unanswered, and this is needed by me, as I have the same issue.  That is I am unable to activate my hardware using the CLI that was given, even using sudo, I get a permission denied. #5 shows a state of disabled.  #6 shows state = active.   I am at a loss as how to proceed, but I am game for most anything.  Does the PIIX4 module have anything to do with this, since the kernel refuses to load it?  A bios check indicates that the audio chip is ok.

---

### Post by gotaserena on 2008-04-03
Greetings, fellow tp600 users!

I had deactivated my thinkpad 600 because of a faulty lcd cable, and last week finally got around to buy a new one. After the upgrade to gutsy I've found that strangely the dma assignments of the sound card had all changed and then the sound wouldn't work even when the alsa module was loaded!

This is the source of the WSS error above. Inspecting the isa devices I've found that:
```
$ sudo cat /sys/bus/pnp/devices/00\:07/resources 
state = active
io 0x388-0x38b
io 0x220-0x233
io 0x530-0x537
irq 5
dma 3
dma 0

```
See: dma1 has changed to 3! That requires the change in the options of the alsa module:
```
$ sudo grep options /etc/modprobe.d/alsa-base 
options snd-cs4236 port=0x530 cport=0x538 mpu_port=-1 fm_port=0x388 irq=5 dma1=3 dma2=0 isapnp=0 sb_port=0x220
```

This is essentially what the script above does, but I couldn't get it to work here. In order to find the right device for the sound card, you need to try all of them:
```
$ for i in 0 1 2 3 4 5 6 7 8 9 a b c d e f; do echo $i: `cat /sys/bus/pnp/devices/00\:0$i/id`; done
0: PNP0c01
1: PNP0a03
2: PNP0700
3: PNP0501
4: PNP0400
5: IBM0071 PNP0511
6: CSC0010
7: CSC0000
8: CSC0001 PNPb02f
9: CSC0003
a: IBM3760
b: PNP0200
c: PNP0800
d: PNP0c02
e: PNP0c04
f: PNP0303
```

Hope this (still) helps.

---

