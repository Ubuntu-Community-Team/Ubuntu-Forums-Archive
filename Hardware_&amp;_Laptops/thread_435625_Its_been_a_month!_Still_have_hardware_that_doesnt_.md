---
title: "Its been a month! Still have hardware that doesnt work. Please Help"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by aerowinged on 2007-05-07
Hey guys,
I really want to stick with Ubuntu, but i cant if i am not able to get some of these basic hardware issues figures out.
The guys at notebookreview forums have helped me out quite a bit, but these last issues are the biggies no one seems to be able to know. I was told this is the place to go.

1st.    About me: i am a complete newb. brand new to Linux, no experience really, but i am very technically inclined and can follow directions very well. So please explaine simply if you know how to fix these things.

2nd.    My Computer. Its a Chinese brand. No one has heard of it and there are no laptop wiki pages for it. The brand is Haier, the model is W36. Though its a chinese brand, its got all the same mainstream components of the bigger brands. It has a 13.3" widescreen, Core 2 Duo T5600 (1.83), 1 GB RAM, GF 7400

3rd.    The stuff that doesnt work. (First ill just list them by priority, then ill go into more detail) 

CPU Scaling: It doesnt work. My cores are always running at 1.83 and my fan is constantly on medium to high speed. very annoying. BIGGEST ISSUE HERE

Sound: My sound did not work out of the box, despit is a pretty common card. Realtek ACL660. I have sound now with help from other forums, but its my sound control that doesnt work. My FN keys are basically useless. 

Memory Card: Ive got lots of memorycards and i use them a lot. I must get this working. It is a Ricoh 4 in 1 reader (SD, MS/pro, MMC, and XD)

Webcam: I live overseas, i need this to work to communicate with home. Under windows XP it just showed up as a USB 2.0 webcam. It is integrated into my laptop screen.

Svideo: I can get Svideo out, but is just a cloned screen, which obviouly doesnt fit on a normal TV. When i tell it to make a seperate screen, it says it need to restart the X server... so i restart the computer, and everything is back to default/ still doesnt work. This was done from Terminal> Nvidia-settings

4th    What I have done.

CPU Scaling: I have followed someone elses instructions this far, and then never got a response. This is what came up. (Copied from my other thread in another forum)

> Thanks for posting that code and putting it in such simple terms for me! BUT.... When i enter the code i get this

[QUOTE]:$ cd /sys/devices/system/cpu/cpu0/cpufreq
bash: cd: /sys/devices/system/cpu/cpu0/cpufreq: No such file or directory
$ sudo cat scaling_available_frequencies
bash: $: command not found
$ sudo cat scaling_available_governors
Password:
cat: scaling_available_governors: No such file or directory 

When i use the GUI to search for that folder, it doesnt exist under CPU 0. But then i checked CPU1 anyway, and it did have the cpu scaling folder and this is what i got...

> :$ cd /sys/devices/system/cpu/cpu1/cpufreq
:/sys/devices/system/cpu/cpu1/cpufreq$ sudo cat scaling_available_frequencies1826000 1328000 996000 

:/sys/devices/system/cpu/cpu1/cpufreq$ sudo cat scaling_available_governors
conservative userspace ondemand powersave performance 

:/sys/devices/system/cpu/cpu1/cpufreq$ sudo cat scaling_max_freq
1826000

:/sys/devices/system/cpu/cpu1/cpufreq$ sudo cat scaling_governor
performance

:/sys/devices/system/cpu/cpu1/cpufreq$ sudo echo 'ondemand' >scaling_governor
bash: scaling_governor: Permission denied

:/sys/devices/system/cpu/cpu1/cpufreq$ sudo echo `cat cpuinfo_max_freq` >scaling_max_freqbash: scaling_max_freq: Permission denied

:/sys/devices/system/cpu/cpu1/cpufreq$ 

So is it not letting me change it from "performance" to "ondemand"?
And should my CPU0 also have the CPU Frequency folder? Can I just copy and paste the folder from CPU1 to CPU0?[/QUOTE]

When i try to add "CPU Frequency Scaling Monitor" the panal i get this error message

> CPU frequency scaling unsupported
You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

SOUND CONTROLS: 
This thread describes what i had to do to fix my sound in the first place [http://forum.notebookreview.com/showthread.php?t=120123](http://forum.notebookreview.com/showthread.php?t=120123)

The problem now is that my keyboard FN functions are completely independent from the on screen sound controls.

For example. When i press FN and mute. The little integrated volume bar appears on the screen with the mute symbol. But i still have sound. The on screen sound control has not been muted. When i press FN and Vol Up. again, the integrated control pops up, but it is already defaulted to the absolute minimum. As i increase volume, it will actually make the volume increase, but one the bar hits half way (for about 2 notches) it get so load i think it going to blow the speakers. Once i pass that point, it goes back to normal. But still cant decrease the the volume. 

Ive got simular issues with the FN and other function keys. Specifially Wireless, which ALSO has its very own button built into the laptop. which doesnt work.

Memory Card, Webcam, and Svideo: No one else has even gotten me started on these yet. I can retrieve any additional information you guys may need from terminal codes etc, just let me know. 

Thank you guys, i really do like ubuntu and dont want to switch back to windows. But i NEED to get these working.

---

### Post by teaker1s on 2007-05-07
cpu scaling we use either
**powernowd** or** cpufreqd**

sound may either be that your sound or application are not using the same alsa or oss output-or in some cases the laptop needs configuring for the model.

memory card 
The driver for some internal card readers is present in kernel 2.6.17, but is turned off by default. To enable it, do the following:

```
lspci
``` post output and also ```
lsusb
``` lets see if we can also find out about webcam

[COLOR="Blue"]at the moment I'm filling out electrical inspection forms so I'm here but there will be a delay in reply[/COLOR]

your sound issue with keys is an alsa issue, sound can be controled from icon on top panel

---

### Post by aerowinged on 2007-05-07
Sorry, i forgot to mention im on ubuntu 7.04

This is lspci output:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:03.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:03.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

This is lsusb output: 

> Bus 005 Device 002: ID 0c45:627b Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 15d9:0a37  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

For cpu scaling. I found those programs under synaptic package manager. But which one should i try first? I thought CPU Scaling was just an integrated feature into ubuntu. If i NEED to use one of these programs, could it mean that there is something wrong with my hardware. No one else ever mentioned before to just install software. And are they automatic? one mentions it is (i think) but mentions i need other drivers and things enables, including acpci... which isnt working i dont think?
 
For the sound. Controlling the sound using the icon at the top of the panel works fine, but the FN keys have no affect on it. I have switched bewteen HDA Intel and Realtek ALC660

Thanks for your help!

---

### Post by jespdj on 2007-05-07
A webcam can be hard to get working. There's a French guy who is writing drivers for webcams and his drivers seem to be what most people are using to get their webcam working: [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

For me the driver doesn't work correctly with my Microsoft LifeCam VX-3000, even though the page at the moment announces with big letters that this webcam is now supported... :(

---

### Post by teaker1s on 2007-05-07
=aerowinged;2608587]Sorry, i forgot to mention im on ubuntu 7.04


For cpu scaling. I found those programs under synaptic package manager. But which one should i try first? I thought CPU Scaling was just an integrated feature into ubuntu. If i NEED to use one of these programs, could it mean that there is something wrong with my hardware. No one else ever mentioned before to just install software. And are they automatic? 
[COLOR="RoyalBlue"]
Normally ubuntu sets them up for you, I'm am a disadvantage as I have AMD experience, now on ubuntu I use powernowd, you may need cpufreqd there are a few threads about it and trouble setting up on core 2 duo. Also in debian I had to load the powernowd module at boot. I've found a tutorial that may help[/COLOR]
[http://ubuntuforums.org/showthread.php?t=248867&highlight=Core+2+Duo+scaling]("http://ubuntuforums.org/showthread.php?t=248867&highlight=Core+2+Duo+scaling")

one mentions it is (i think) but mentions i need other drivers and things enables, including acpci... which isnt working i dont think?
 
For the sound. Controlling the sound using the icon at the top of the panel works fine, but the FN keys have no affect on it. I have switched bewteen HDA Intel and Realtek ALC660
[COLOR="RoyalBlue"]This is either your shourcuts(top panel>system>preferences>keyboard shortcuts) need setting or an alsa issue[/COLOR]

Thanks for your help!

---

### Post by Sef on 2007-05-07
For sound check, open your terminal (Applications > Accessories > Terminal) and paste here the output of this command:

```
cat /ect/modprobe.d/alsa-base
```

---

### Post by teaker1s on 2007-05-07
Bus 005 Device 002: ID 0c45:627b Microdia **this is yourwebcam I found a couple of things, but I'm not sure of the driver yet**

> Media Card Reader

In most cases, the onboard media card reader will not work without a little persuasion. The driver for internal card readers is present in kernel 2.6.17, but is turned off by default. To enable it, do the following:

lspci

Look for SD/SDIO/MMC/MS/MSPro Host Adapter and note the number at the beginning of the line. For example, 05:05.2. Then run (inserting your number in place of mine):

sudo setpci -s 05:05.2 4c.b=0x02

Now put in an SD card, and it should work. The driver is still buggy, but should perform well nonetheless.

This method is not permenant, we're working on that.

suggested, but untried as my model has no media slot but-you could use "update-rc.d" to determine run levels and automate

---

### Post by aerowinged on 2007-05-07
Jespdj: So do i just download and install the one file at the top? I looked at the "Know Cameras" link on that page, and couldnt seem to find that one that mine is. (Bus 005 Device 002: ID 0c45:627b Microdia ... this one i guess. Should i try it anyway though?)

Sef: This is the output from the code u asked for. Doesnt look good. 
> $ cat /ect/modprobe.d/alsa-base
cat: /ect/modprobe.d/alsa-base: No such file or directory

But when i manually search for it, i see a file named "alsa-base" in that directory... i dont get it? 

EDIT!! Figured it out. Typo in the code. its etc not ect. This is the output

> $ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack

teaker1s: I have set the keyboard shortcuts, still doesnt control properly. 
I will also look at the link for the CPU scaling issue u provided and let you know. 
And for the memory card. When you say this method is "not permenant"... do you mean i have to redo it everytime i restart the computer?

---

### Post by jespdj on 2007-05-07
Here's a thread about the Microsoft webcam, in which I posted what I did: [Microsoft LifeCam VX-3000 thread](http://ubuntuforums.org/showthread.php?p=2587571)

---

### Post by teaker1s on 2007-05-07
yes the media card isn't a permanant solution, we could either create a simple script to click on or I did advise others that we could use update-rc.dto get it to run.
As I said I don't  have a media card slot and as yet nobody has confirmed the update-rc.d works, while I see no reason it won-'t I'd like confirmation before I recommend it as a permanant solution.
 I also would like to know what bugs the driver has before suggesting that it should run at every boot.

I would also like to welcome you to ubuntu:popcorn:

---

### Post by aerowinged on 2007-05-07
So whats the verdict on the CPU Scaling and webcam at least. 
Should i install one of those 2 programs, or try anyhting in the terminal first. And which program should i try first.
And should i install the webcam driver from the french guys page even though my cam isnt listed on the "known cameras" link?

---

### Post by aerowinged on 2007-05-08
I followed this tutorial here, [http://ubuntuforums.org/showthread.php?t=248867&highlight=Core+2+Duo+scali](http://ubuntuforums.org/showthread.php?t=248867&highlight=Core+2+Duo+scali) ng
But when i got to part my CPU0 does not have the directory. So instead i just finished the tutorial with CPU1. But when i restarted the computer, i still got the "CPU Scaling unsupported" message.
Could it not be working because i am missing this directory from my CPU0 folder. Where can i get the necessary files to replace it?

---

### Post by aerowinged on 2007-05-08
I installed cpufreqd. And in the details this is what i got. (just the last 2 lines)

> Setting up cpufreqd 2.2.1-2 ... 
No cpufreq interface installed, not starting cpufreqd

So then i installed powernowd which automatically uninstalled cpufreqd. And this is was it said at the end of the details

> * Starting powernowd...
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Directory nonexistent
* CPU frequency scaling not supported
...done.

So i think that this missing directory i have in CPU0 in the cause of the whole problem. What can i do!? CPU Scaling works fine in windows, so i know its not my hardware.

---

### Post by teaker1s on 2007-05-08
I would suggest posting on the howto thread you followed, I say this because I think your issue is solvable -but I do not know the answer

---

