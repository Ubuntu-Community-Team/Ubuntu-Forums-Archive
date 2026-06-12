---
title: "Obnoxious crackling sound from usb audio speakers"
date: 2008-05-25
forum: Hardware
---

### Post by gnufied on 2008-05-25
Hi folks,

I got these Logitech Audiohub speakers and when connected to laptop running hardy, they seem to work okay( I have to choose "USB Audio" in System->Preferences->Audio ).

But I always get constant crackling sound from the damn speakers. I read somewhere this might be because of frequency mismatch between Alsa output and acceptable frequency of USB audio speakers. So, I played around with .asoundrc file (~/.asoundrc currently looks like this)

```
pcm.usb-audio-hw {
        type plug
        slave.pcm "usbmix"
}

pcm.usbmix {
        type dmix
        ipc_key 18548329
        ipc_key_add_uid true

        slave {
                pcm "hw:1"
                format      S16_LE
                period_time 0
                period_size 1024
                buffer_size 8192
                rate        44100
        }
        bindings {
                0 0
                1 1
        }
}


ctl.usb-audio-hw {
        type hw
        card 1
}

```

But above had no effect on the noise, when I played music using:
```

aplay -vv -D usb-audio-hw shutdown.wav

```

I still get the same noise from speakers.

Also, aplay -l returns:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Speaker [AudioHub Speaker], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Output of /proc/asound/cards is:
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 20
 1 [Speaker        ]: USB-Audio - AudioHub Speaker
                      HOLTEK  AudioHub Speaker at usb-0000:00:1d.7-4.4, full speed

```

Output of lsusb is:
```

Bus 007 Device 006: ID 046d:0a0e Logitech, Inc. 
Bus 007 Device 005: ID 05e3:0607 Genesys Logic, Inc. 
Bus 007 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c040 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

```

Output of lspci is:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

Linuxjournal mentions that, noise could be because of irq conflicts, but I wouldn't know that for love of Johnny Depp. Nonetheless, here is the output of /proc/interrupts, if any of you can decipher it to help me, I shall be grateful.
```

           CPU0       CPU1       
  0:   13827033   13822578   IO-APIC-edge      timer
  1:       2026       2094   IO-APIC-edge      i8042
  8:          4          3   IO-APIC-edge      rtc
  9:         23         26   IO-APIC-fasteoi   acpi
 12:         68         68   IO-APIC-edge      i8042
 14:         54         58   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:    3797453    3793917   IO-APIC-fasteoi   nvidia
 17:          0          0   IO-APIC-fasteoi   eth0
 18:          1          2   IO-APIC-fasteoi   ohci1394
 19:    3573731    3569352   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb3, ehci_hcd:usb7
 20:     165855     165123   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb4, HDA Intel
 21:          1          1   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb6
 22:          6          6   IO-APIC-fasteoi   sdhci:slot0
218:    2227602    2225087   PCI-MSI-edge      iwl3945
219:     168842     169243   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:    7704969    7715603   Local timer interrupts
RES:    7699333    7901504   Rescheduling interrupts
CAL:        828        939   function call interrupts
TLB:      38782      39822   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

Last, my volume is not max and when I switch to USB Audio, mixer offers me only one mixer channel (pcm), and hence I doubt it could be because of one of the mixer channels went haywire.

---

### Post by 11hjpphty76lkjj on 2008-05-29
I have the same problem....sorry I don't have any solution but I'll be watching.

A

---

### Post by 11hjpphty76lkjj on 2008-06-06
*bump*

Anyone have any ideas?

Thanks!

---

### Post by CMEPTb on 2008-06-14
I'm having the same problem, so Bump.

---

### Post by macyo on 2008-06-21
I have the same problem. Have tried all of the above and then some. No joy?! BUMP

---

### Post by Enkaybee on 2008-06-23
I have Logitech speakers too and I have the same problem.  Best of luck.

---

### Post by Bill_Farrow on 2008-06-26
I have the same USB audio chip in my Samsung SyncMaster 225UW LCD monitor, which has a built in webcam, speakers, and microphone.

```
$ lsusb
Bus 007 Device 006: ID 4c2d:2900
Bus 007 Device 005: ID 0ac8:c303 Z-Star Microelectronics Corp.
Bus 007 Device 003: ID 05e3:0607 Genesys Logic, Inc.
```

The speakers had a crackle or clicking sounds when playing videos.  This was due to a mismatch in the audio rates.  Looking at the output of "sudo lsusb -v" the audio should be able to handle several rates, so maybe the problem is in the linux driver not being complete ?  The other thing to back this up is that the microphone capability is not detected.

```
sudo lsusb -v | less
--snip--
        tSamFreq[ 0]        32000
        tSamFreq[ 1]        44100
        tSamFreq[ 2]        48000
--snip--

```

Anyway, to fix up the crackling sound and make the USB audio the default PCM device used (not the on-board sound card) I set up my /etc/asound.conf like this:

```
pcm.!default {
        type plug slave {
                pcm "hw:1,0"
                rate 44100
                format S16_LE
        }
}
```

---

### Post by CMEPTb on 2008-06-27
Thanks for advice, I'll save this setup for future. Sadly, I can't test it because I returned the speakers to the store. Can anyone confirm Bill_Farrow's solution?

---

### Post by Enkaybee on 2008-06-27
I've heard that this can be fixed by going into the .asoundrc file and changing "rate" to 44100.  When I went to try it I couldn't find the .asoundrc file.  (I went to home and then chose to show hidden files and it wasn't there.  Any help on that one?)

---

### Post by gnufied on 2008-07-09
Well, you will have to create ~/.asoundrc file if it doesn't exist. In my case, I dunno, if Bill Farrow solution will fix the problem. I wish, I could return the speakers to the store.

---

### Post by Enkaybee on 2008-07-10
All right, here's what worked for me.  

After changing my audio output rate from 48000 to 44100 I got nothing.  I still heard the crackle.  So I changed it back to 48000 and went to terminal and typed alsamixer.  Hit enter and you get a simple sound control interface.  What I did was crank bass and treble all the way up.  Bass Boost and Auto Gain should be left at 00.  Then turn PCM down until you no longer hear the crackle.  It helps to have a song playing while you're doing this so you can tell just how far you need to turn PCM down. 

Good luck.

---

### Post by zeronothing on 2008-11-03
### this is written using ubuntu 8.10 ####

I'm not sure if this will help anyone at this point. I just bought the logitech audiohub not to long ago and I too suffered from the cracking sounds coming from the speakers. Just to let everyone know, I'm using ubuntu 8.10. even when using 8.10 the problem exists. So happen to be searching for a fix online when I ran across this article online:

[http://bbs.archlinux.org/viewtopic.php?id=41517](http://bbs.archlinux.org/viewtopic.php?id=41517)

This forum post discribes the problem as being an issue with the configuration of the kernel. the issue is with these to configurations in the kernel:

USB_EHCI_ROOT_HUB_TT
USB_EHCI_TT_NEWSCHED

if you google the above configurations you will get an explanation for each one. where you can find the configuration is in the boot directory (/boot/) and the config will be something like config-2.6.27"""""". anyway this is were the problem is that causes the cracking and popping sounds. to fix the issue is kind of long but not difficult. what you have to do is recompile the kernel with "USB_EHCI_TT_NEWSCHED" commented out. the long part about this is it takes sometime to recompile, that is it. if you visit the recompile [[COLOR="RoyalBlue"]page[/COLOR]]("https://help.ubuntu.com/community/Kernel/Compile") ubuntu offers to help you recompile. The basic steps to do this are followed:

1.)download prerequisites, open up terminal:
sudo apt-get install linux-kernel-devel fakeroot build-essential makedumpfile git-core

also do (if your using 8.10)
sudo apt-get build-dep linux

2.)now we need to download the ubuntu kernel from the up-to-date repository, open up terminal:

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git ubuntu-intrepid

3.) once you have downloaded the kernel you will see the directory in you home directory. using the terminal you need to "cd" into the directory. next "cd" into directory "debian". next "cd" into directory "config" next go into the directory that fits your architecture. Their will be a directory for 64-bit or 32-bit. once you are in the directory do "gedit config". this will open the config in gedit the Gnome text editor. no what you need to do from here is look for the line:

CONFIG_USB_EHCI_TT_NEWSCHED

next you need to comment the line out. 

# CONFIG_USB_EHCI_TT_NEWSCHED

now save the file. next you need to go back to the beginning of the directory (not all the way back to your home directory). and enter this command in the terminal:

debian/rules updateconfigs

This will update the config files for the kernel build. 

4.) here is where the magic happens. time to build the kernel. execute this command in terminal:

AUTOBUILD=1 fakeroot debian/rules binary-debs

or you can do this command if you have dual-core processor:

CONCURRENCY_LEVEL=2 AUTOBUILD=1 fakeroot debian/rules binary-debs

now you should just sit back and possibly grab a beer, pop, soda and maybe something to eat because this can sometimes take a while depending on your machine. almost forgot, during the recompile it is going to ask you if you would like to enable CONFIG_USB_EHCI_TT_NEWSCHED. make sure you say no by typing N and hitting enter.

5.) after all of the compiling and building you will see the deb packages of your newly create kernel in your home directory. most likely you don't have to install every package it created. just install your version because their will probably be a generic, server, server headers, generic headers, etc. just make sure you install the linux-image package that is right for your PC's architecture plus the linux-headers of your architecture.

6.) after you install those packages just reboot and on reboot when the theme music plays you shouldn't here the cracking and popping sounds. 

hopefully this will help some. contact me if you need some help. remember these instructions are written for ubuntu 8.10. you might have to do something a little differently for versions below 8.10.

---

### Post by 11hjpphty76lkjj on 2008-12-06
Has anyone else tried this?  

I'm sorta scared to compile my own kernel... lol

---

### Post by CJay554 on 2008-12-25
Ok,
1: This didn't work as i just installed my newly configured kernel and the popping noise is still there..
2: why can't we just Edit the config file in the /boot? Why reinstall a whole kernel just for that? Doesn't make a hint of sense.

---

### Post by gnufied on 2009-01-08
> Ok,
1: This didn't work as i just installed my newly configured kernel and the popping noise is still there..
2: why can't we just Edit the config file in the /boot? Why reinstall a whole kernel just for that? Doesn't make a hint of sense.

Because config file is used as input during compilation of Linux kernel. It won't make sense to just edit the config file and expect it to work. Its like editing a C program and expecting executable to change automagically without recompiling.

Having said that, I will give kernel recompile a shot.

---

### Post by vorostatz on 2009-01-14
Argh I have the same problem with my creative external usb soundcard, I am almost a complete newbie, any chance someone can give me a simple way to do this.  Funny thing is I didn't have it on a previous instalation of Ubuntu 8.10 but when I swapped hard drives (I wanted a new bigger hard drive) and reinstalled 8.10 i got the cracking sound and it's driving me nuts!!!

---

### Post by monkeys on 2009-02-16
I'm having the same issues but I'm a little weary about altering/building/touching kernels -- I know this is an old thread, but did anyone find a solution?

---

### Post by marcelo.g.jordao on 2009-04-04
Worked for me very well with 8.10! Although the compilation/creation of .deb packages in the end i was able to install the generated kernel packages and solved my problem!!! Thank you very much.

Cheers
marcelo

PS: I am trying to perform the same operation with Jaunty beta version.

---

### Post by dcroal on 2009-04-25
Recompile fix works for me on Jaunty final as well.

---

### Post by 11hjpphty76lkjj on 2009-04-25
I did this on Jaunty and it worked for me.

Before you compile your own kernel, it takes a LONG time to compile.

This does work--well worked for me anyway...

If you download the script, be sure to chmod +x script.sh before running ./script.sh

```

#!/bin/bash
echo "What version of Ubuntu are you using?"
echo "A) Hardy 8.04"
echo "B) Intrepid 8.10"
echo "C) jaunty 9.04"
read UBUNTU

case $UBUNTU in
        A|a)
                echo "Choice was $UBUNTU"
        UBUNTU="hardy"
                ;;
        B|b)
                echo "Choice was $UBUNTU"
        UBUNTU="intrepid"
                ;;
        C|c) 
                echo "Choice was $UBUNTU"
        UBUNTU="jaunty"
                ;;
          *)
                echo "Valid Choices are A,B,C"
                exit 1
                ;;
esac

echo "What sort of system are you on?"
echo "A) i386"
echo "B) amd64"
read SYSTEM

case $SYSTEM in
        A|a)
                echo "Choice was $SYSTEM"
        SYSTEM="i386"
                ;;
        B|b)
                echo "Choice was $SYSTEM"
        SYSTEM="amd64"
                ;;
          *)
                echo "Valid Choices are A,B"
                exit 1
                ;;
esac

echo ""
echo ""
echo "You have selected: $UBUNTU and $SYSTEM are these correct?"
echo ""
echo "Control-C to quit, or wait 20 secs..."
sleep 20
sudo apt-get update
sudo apt-get install fakeroot linux-kernel-devel build-essential makedumpfile git-core build-dep linux debhelper
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-$UBUNTU.git ubuntu-$UBUNTU
cd ~/ubuntu-$UBUNTU/debian/config/$SYSTEM
sed -i 's/CONFIG_USB_EHCI_TT_NEWSCHED/#CONFIG_USB_EHCI_TT_NEWSCHED/g' config
cat config | grep CONFIG_USB_EHCI_TT_NEWSCHED
echo ""
echo "There should be a # in frong of the CONFIG_USB_EHCI_TT, if there isn't quit and figure out why."
echo "Otherwise wait 20 secs to continue.."
echo ""
sleep 20
cd ~/ubuntu-$UBUNTU
echo ""
echo "WARNING: BE SURE TO SELECT N WHEN PROMPTED (EXPERIMENTAL) (USB_EHCI_TT_NEWSCHED)!!!"
echo ""
sleep 10
debian/rules updateconfigs
echo ""
echo "The next step takes awhile..sit back and relax!"
echo ""
AUTOBUILD=1 fakeroot debian/rules binary-debs
cd ~/
ls -l | grep dep
echo ""
echo "Perhaps you want to do dpkg -i linux-image-2.6.28-12-generic_2.6.28-12.43_i386.deb"
echo ""
echo "and dpkg -i linux-headers-2.6.28-12-generic_2.6.28-12.43_i386.deb"
echo ""
echo "If you update your kernel..start over. Good luck."
#cleaning up
rm -rf ~/ubuntu-$UBUNTU
exit
```I have uploaded my deb packages here:

[http://www.aaronalbright.com/packages/kernel/](http://www.aaronalbright.com/packages/kernel/)

I installed this package:

[http://www.aaronalbright.com/packages/kernel/linux-image-2.6.28-12-generic_2.6.28-12.43_i386.deb](http://www.aaronalbright.com/packages/kernel/linux-image-2.6.28-12-generic_2.6.28-12.43_i386.deb)

And it worked for me. It may or may not work for you.

You'll probably want the generic one for i386.  The headers wouldn't install for me--which broke virtualbox.  This deb will only work for the 2.6.28-12 kernel.  Any upgrades will not work (I assume).  DO NOT INSTALL ON ANY SYSTEM THAT CAN'T BE REINSTALLED OR THAT CAN'T BE BROKE.  It's all optional and so forth I take no responsibility if it breaks your Ubuntu.. Just hoping to help someone..

Good luck.

Aaron

---

### Post by Mouth on 2009-04-29
> **kalosaurusrex said:**
> I did this on Jaunty and it worked for me.

Before you compile your own kernel, it takes a LONG time to compile.

This does work--well worked for me anyway...

If you download the script, be sure to chmod +x script.sh before running ./script.sh

~/$ sudo apt-get install fakeroot linux-kernel-devel build-essential makedumpfile git-core build-dep linux debhelper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
E: Couldn't find package linux-kernel-devel

Any idea's?

---

### Post by anapob on 2009-05-03
whoa, thanx enkaybee it worked for me.but i had to increase the pcm and decrease the mic. Now back to Amarok for me

---

### Post by gunnz on 2009-05-09
Ladies and gentlemen, boys and girls!!!
Logitech audio hub works! yes it does...really:guitar:
After 3 long nights searching the internet all over I found the solution and it's really simple...believe me
Go  here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 
Then select v2.6.30 rc4 and inside the folder select the arhitecture of your system
Clik to open with Gdebinstaller then reboot and THAT'S IT :)
I can control separately the volum on the Logitech speakers and my laptop (Acer 5315) + i can play a song on both of them in the same time.To make the settings go to system-preferences-sound but i guess it's obvious already
I forgot I have Ubuntu 9.04
Now go spread the word :)
 
All the best, I'll go sleep now :)

---

### Post by vc_ubu on 2009-06-13
Sorry to drag up an old thread, but it's still very much relevant since I've spent the ENTIRE day trying to fix this problem on my own system.

In this case my USB audio device is a Numark C3USB mixer. I've removed PulseAudio, so ruled that out as a cause. I've messed around with buffer settings in ALSA, no progress. Tried gnufield's ~/.asoundrc trick, with no progress. Tried Enkaybee's alsamixer trick to no avail. I tried gunnz's idea of upgrading to kernel 2.6.30 (which is now a final version, no longer an RC. And BTW, the above required reinstalling the newest version of nvidia drivers-- just a warning).

The 2.6.30 (RC4 or final version) doesn't have the kernel USB settings disabled that zeronothing talked about, so I ended up building the 2.6.30 kernel using his instructions to comment out just the one line:
CONFIG_USB_EHCI_TT_NEWSCHED 

Still no luck!

I'm currently trying building the kernel again with also commenting out the line:
CONFIG_USB_EHCI_ROOT_HUB_TT

We'll see how that goes, but I'm not holding my breath :). Subscribing to this thread in case anyone else comes up with any other ideas, but I think I've given up for now and will have to get a regular sound card-- I'll take regular old analog interference over USB crackling anyday ;)

---

### Post by JSU on 2009-06-18
I tried installing RC4 and RC8. With either of them I cannot get into X11 (startx doesnt work). Any ideas? Thanks!!

---

### Post by vc_ubu on 2009-06-18
> **JSU said:**
> I tried installing RC4 and RC8. With either of them I cannot get into X11 (startx doesnt work). Any ideas? Thanks!!

gunnz suggested trying RC4 because at the time of his post, that was the current/newest RC that was available. The final version of 2.6.30 has now been released, so there's no reason to use the RCs-- use the final version and see if that fixes anything.

If not, you might have a problem with your graphics (especially if using restricted drivers/modules). For me, I was using Nvidia and needed to download the newest nvidia drivers in order to get 2.6.30 to work ([https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639))

If it's not that either, search about how to diagnose an "X doesn't start" problem. There should be tons of posts/pages about how to start diagnosing that, by looking at the content of various X-related log files.

Edit: just remembered-- if you're using Envy check out the FAQ-- you'll have to uninstall the old drivers, restart, then re-install the drivers. [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by nettobr on 2009-11-25
Hi People,

Now on 9.10 its working....  No Compilation...  No modi...

BUT, I had to install Full PulseAudio, to use pavucontrol to change Output.

USB Hub is working...

Sound is pretty good...

Volume knob does not work well, only change master volume for Internal Sound Board, than the very first play is too out loud...  

Well, nothing is truly perfect in this world.

Good Luck!

NettoBr

Bye from Brazil

---

### Post by finnj6 on 2011-03-21
I was having the same problem with Ubuntu 10.10, To fix it I just had to go into System->Preferences->Sound then choose the hardware tab and change the output type I had my bose sound dock set to 5.1 and changing it to 5.0 or 4.1 got rid of the crackling and improved the sound quality

---

