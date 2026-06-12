---
title: "No sound for compaq presario B1800 (ubuntu 8.04)"
date: 2008-05-08
forum: Hardware
---

### Post by tanle on 2008-05-08
Hi all,

I've just made a fresh install of ubunt 8.04 on my laptop (Compaq Presario B1800), everything is working perfectly fine except there is no sound, or it cannot fine the correct sound card, does anyody have a solution/patches for this please let me know.

thanks heaps guys,

Tan

---

### Post by MaindotC on 2008-05-08
Looks like the last BIOS was released in February of 2006.  Do you have the latest BIOS version F.09A?

---

### Post by tanle on 2008-05-08
thanks for the reply strAlan,

No i dont have the latest version of F.09A, but i know where to download it, however i dont know how to install it using Ubuntu, as the BIOS file is give as exe file format, if you have any lead, please help.

thanks again,

Tan

---

### Post by MaindotC on 2008-05-09
The BIOS installer is made to be run in a Windoze environment.  The BIOS upgrade looks to be a .exe so you can do a couple things:  If you have a Windoze partition run it from there.  If you don't, but you have an identical hard drive with Windoze on it, you can stick that hard drive in there (but I think Windoze will get all antsy about a hardware change).  You can try running it in wine but be prepared for this to not work.  The last option I can think of is to install something called virtualbox and run the .exe from a windoze virtual environment.  Please try any of the above options and if you can't, and you're not familiar with virtual machines, we'll go from there.  I'll be on here for another few hours.

---

### Post by tanle on 2008-05-09
Oh wow that was a quick reply :) i think i like the virtual machine idea, i am going to do it this way, how sure are you that this is the problem Ubuntu cannot get my sound driver to work though? so that i can weigh up my option, whether to install virtual machine or live withouth sound :( 

thanks for any advice.

kind regards,
Tan

---

### Post by MaindotC on 2008-05-09
It's very difficult to tell because I don't know how to read the outputs of commands like

```
lspci
```

so I'm shooting from the hip here, but the first step I'm trying to take is determine if it's a hardware or software issue.  I helped [this guy]("http://ubuntuforums.org/showthread.php?t=769850&page=3) with a similar situation.  If the BIOS upgrade doesn't resolve it, then we'll have to try installing different sound drivers which can be done through the repositories.

I'm assuming that's going to take you some time so I'm going to bed.  See you in the morning!

---

### Post by tanle on 2008-05-09
Okay Great,

Thanks for the advice, i read this post: [https://help.ubuntu.com/community/VirtualBox#head-4864eba9f3e39b9139a1615a696676368ca69977](https://help.ubuntu.com/community/VirtualBox#head-4864eba9f3e39b9139a1615a696676368ca69977)

on how to install virtualbox but it doesn't seem to work, do you have a better way of doing it ? it seem that the server is missing some files when i run the command on 8.04.

kind regards,
Tan

---

### Post by MaindotC on 2008-05-09
Did you try any of the other suggestions?

---

### Post by Glucklich on 2008-05-09
Tanle, what's your doubt about virtualbox? On installing it or on how to get the OS emulated?
Well, I had a similar problem with my BIOS. Because I am an unexperienced user the easiest way I found to upgrade my BIOS was formating the PC, installing windows, install the BIOS and get back on Ubuntu. All other options were a bit difficult for me to understand. Dunno if that's your case, but this could be an option to consider if you don't have much experience on this stuff.

---

### Post by tanle on 2008-05-10
Hi all,

StrAllan: I am going to try and do the virtual machine methods so i didn't try the other one because i wanted to set up virtualbox on this computer any :)

Glucklich: if i cant get virtualbox to work, then your method would have to be the one :)

thanks guys for the help, very much appreciated.

Tan

---

### Post by MaindotC on 2008-05-10
Dude check out [this thread]("http://www.nu2.nu/bootcd/#clean") to create a bootable cd solely for the purpose of doing a BIOS upgrade.  Gluck, sorry I didn't find this sooner so you wouldn't have had to do all that VirtualBox stuff.  This is the section of which I think you should be interested:

 Clean Bootable CD-Rom (for BIOS upgrade) [updated! may 6, 2005]

People ask me if it is possible to create a bootable CD-Rom to update/flash their BIOS, on a system that has no floppy disk drive. I realize that some new PC's nowadays also don't have a floppy drive so this problem may affect more people in future... I have re-done this CD, so that it will be easier to use (single download package). It uses an updated version of BCD and BFD.
This Clean Bootable CD-Rom can be used for flashing your BIOS or other programs that need to be run from a "clean-booted" Dos operating system.

The steps to create are:

   1. Download Clean Boot CD package v2.0 (596KB) and unpack it into any directory you like.

   2. Add your own files, needed to upgrade your BIOS, to the cds\clean\bootdisk\ folder. You have about 2.5MB available space on the bootimage (the CD uses 2.88MB floppy emulation). Do not add your files to cds\clean\files\ folder!
      Optionally you can edit the file cds\clean\bootdisk\autorun.bat and append a line to automatically run your flash program.

   3. When you're done customizing, run "build-clean.cmd" to build your ISO image and burn it to your CD writer.

Warning: Use this Clean Bootable CD-Rom at your own risk!

---

### Post by Glucklich on 2008-05-10
Tanle, I had the same thought as you, and tried upgrading the BIOS through the emulated OS, but couldn't get any results. I hope it will work out for you.
Alan, I've tried creating a bootcd, but I couldn't get the setup to work. Maybe because of the winphlash thing... but all worked out, what else could I wish for? Maybe it was the dumb way, but it was also the safest way for me :P

---

### Post by tanle on 2008-05-10
Hi guys,
I have install win xp and tried to upgrade the bios version f.09a from HP but windows gave me an error saying the BIOS is not for this computer. I don't know if its because of virtual machine or not. I also tried installing the new sound driver to win xp but still there is no sound, the weird thing I don't get is that both Linux and windows detected the sound driver, all the volume control button work but just no sound, so now I guest it could be hardware issue.
regards

Tan

---

### Post by Glucklich on 2008-05-10
I didn't understood a thing, correct me if I'm wrong please. You tried to upgrade the BIOS on a emulated OS, right? If so, maybe you better move to the real thing. It will take a bit of time to install the XP, but when it get installed it's pretty fast.
If you were working on the real thing, maybe the BIOS file is not the one you got. Try to go to the manufacturer's site to get the real deal.

---

### Post by tanle on 2008-05-10
hehehe sorry Glucklich i was replying to that post with my iphone so typing on it made not much sense :) 

Yes i was trying to update the BIOS with the emulated OS (Win XP), the BIOS version i got is definitely for this computer because i got it from HP with the right model number etc... But i think it doesn't work because its in a virtual environment, i also tried to install the graphic driver as well but win XP didn't like the setting that it has so it doesn't do it.

I can however install the sound driver on the emulated OS (Windows XP), everything was successful except there is no sound coming out. now i wonder if it could be the hardware.

regards,
Tan

---

### Post by tanle on 2008-05-10
Hi guys,

I found out that my BIOS version is NOT the latest one:

BIOS Information
	Vendor: Phoenix
	Version: F.09    
	Release Date: 12/01/2005
	Address: 0xE86C0
	Runtime Size: 96576 bytes
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		USB legacy is supported
		Smart battery is supported
		BIOS boot specification is supported

System Information
	Manufacturer: Hewlett-Packard
	Product Name: Presario B1800 (EG002PA#ABG)    
	Version: F.09    
	Serial Number: CNC541009H                      
	UUID: EA9A915F-AAA7-5DCD-5FC9-FFF8DAFCFBFC
	Wake-up Type: Power Switch

Base Board Information
	Manufacturer: HP
	Product Name: 309A
	Version: 50.0E
	Serial Number: 0123456789012345 

thanks to this command:

```
sudo dmidecode -q | less
```

so i think the BIOS is the problem here :(

which mean i have to re-install windows and upgrade the BIOS, more time wasting :)

regards,
Tan

---

### Post by MaindotC on 2008-05-11
I find it odd that you couldn't do it from a virtual environment because that's what Gluck did, but whatever works.  It is a big hassle but if only Toshiba would spend a couple of their billion dollars to make a linux binary you wouldn't have to do all that.  Get that BIOS updated and then put Ubuntu back on and let's see where that goes.

---

### Post by tanle on 2008-05-11
Hi StrAllan,

- I've wipe everything and install a fresh copy of XP
- Download the updated BIOS and successfully updated it
- download the sound driver and it works fine on XP
- install Ubuntu parralel to windows, and the same thing happen, no sound at all on Ubuntu.

So i am definitely sure that Ubuntu is not supporting this laptop sound driver properly.

i think i would have to live with windows for now until Ubuntu support hardware better :)

---

### Post by MaindotC on 2008-05-11
There are several sound drivers available in the repsitories.  Check out the ESD and PulseAudio drivers which you can download by:

```

sudo apt-get install vlc-esd
#this is specific to VLC media player
#or

sudo apt-get install pusleaudio


```

You may also want to try to install restricted drivers by typing:

```

sudo apt-get install ubuntu-restricted-extras

```

You can try installing the windows sound driver in Ubuntu using a program called ndiswrapper.

---

### Post by tanle on 2008-05-11
Hi strAllan,

I tried installing everything u showed me and still it doesn't work, so i tried using ndiswrapper, but i get this error when executing the command: 

```
ndiswrapper -i driver.inf

Error: no ndiswrapper utils found!
```

do you know what i have to do to get the utils working ?

thanks heaps,

Tan

---

### Post by MaindotC on 2008-05-12
First, when you installed the other drivers did you go to System -> Prefereces -> Sound and try selecting the different drivers?  You should have seen PulseAudio as well as ALSA in there.

---

### Post by tanle on 2008-05-12
yes i have :) tested every single one of them...let me restart and try again.

---

### Post by Yellow Pasque on 2008-05-12
Here are some commands that may be helpful:
```
sudo apt-get install ndiswrapper-utils
sudo lshw -C multimedia
aplay -l
```

---

### Post by tanle on 2008-05-12
Hi i excuted your command and the follow results occurs:

```
ttm@tanle-laptop:~$ sudo apt-get install ndiswrapper-utils
[sudo] password for ttm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
ttm@tanle-laptop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ttm@tanle-laptop:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
ttm@tanle-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ttm@tanle-laptop:~$ 

```

---

### Post by tanle on 2008-05-12
now the sound is working woo hooo :) thanks to a chinese friend who searches on the chinese Ubuntu forum:

In the terminal run:

```
alsamixer
```

change External -> MM instead of 00

save it with
```
alsactl store 0 
```

and whoala!!! 

:) thanks for all the helps guys.

kind regards,
Tan

---

### Post by MaindotC on 2008-05-12
Tanle congratulations.  Can you explain why you change it to MM instead of 00 and what that means?  I can't seem to get mine to change - did you do it using the up and down arrow keys?

---

### Post by tanle on 2008-05-12
Hi strAllan,

I dont know why you have to change it to MM, its just one of those things that i follow from the forum, they didn't explain.

after i launch the alsamixer in the terminal i scroll to the far right using the right arrow, and then use 'm' button on the keyboard to change it to MM.

save it then it works right away.

kind regards,
Tan Le

---

