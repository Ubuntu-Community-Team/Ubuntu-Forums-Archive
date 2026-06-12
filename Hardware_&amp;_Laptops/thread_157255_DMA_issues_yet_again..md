---
title: "DMA issues yet again."
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by darkness_nz on 2006-04-08
I'm having problems setting DMA on for my new install. I've been scouring the forums looking for problems like this, but none of the solutions are helping me. 

Hardware:
P4 3.0
Albatron Intel 865PE Pro II motherboard. 
120Gb SATA harddrive
Sony IDE DVD Rom. 
AOpen IDE CDRW. 

**Result of lspci**:
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:03.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to CSA Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)
0000:03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:03:01.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
0000:03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
0000:03:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:03:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

**Results of hdparm**:
/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 14593/255/63, sectors = 234441648, start = 0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

/dev/scd1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device


I have added the dma=on setting in hdparm.conf, but no joy. I have also recompiled a custom kernel with what I believe is the right settings for my hardware. but it still doesn't want to recognise things. 

I have heard there are issues when running a base on a SATA drive with optical drives. 

Have I missed something?

---

### Post by hajk on 2006-04-09
Have you missed something? Yes, you have: hdparm settings have no effect on "SCSI" disks. All your disks are treated as such, as is evident from the /dev/s** device names. So, no need to do anything here.:-D

---

### Post by darkness_nz on 2006-04-09
I figured as much. 

but is this right considering the optical drives are IDE? and I'm getting choppy dvd playback. So is there any course of action to improve that since they are being defined as scsi.

---

### Post by darkness_nz on 2006-04-10
any further ideas from anyone?

---

### Post by stanz on 2006-04-10
> **darkness_nz]any further ideas from anyone?[/quote] 
Hi All....
Have Ya Googled Around? I've used " [this info]("http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1") " for tweaking. It be a start.

My Question to ask, is how or if- I can edit the: 
    /etc/init.d/hdparm =application/x-shellscript ?

[quote]*_Small example of file:_*:
case $KEY in
         read_ahead_sect[COLOR=SeaGreen]) [/COLOR]
       set_option -a[COLOR=Blue]$[/COLOR][COLOR=Blue]VALUE  [COLOR=Black](IS "VALUE" WHERE I REPLACE WITH MY: "-a16" ? )[/COLOR][/COLOR]
      [COLOR=SeaGreen]  said:**
>  The advice & info on that site, mentions: 
Placing these changes to a new text file-   I can do that.
Saving this file & making it a script-    I'm getting lost at script.
Placing file in the directory- one normally runs linux... */rc5.d/S20hdparm.local* ?

I'll save the rest of my questions, till i get a sign of life here....
Thanks All... later!

---

### Post by Ensnared on 2006-04-10
[QUOTE=stanz]The advice & info on that site, mentions: 
Placing these changes to a new text file-   I can do that.
Saving this file & making it a script-    I'm getting lost at script.
Placing file in the directory- one normally runs linux... */rc5.d/S20hdparm.local* ?[/QUOTE]
Not really sure what you're trying to do here, but to answer these questions:

A script is simply a textfile that contains shell-commands (that is, commands you would normally simply type in on the command prompt). So usually, to make a shell script, you make a file that contains this:```
#!/bin/sh
command_1
command_2
command_3
etc...
```
The first line indicates which shell the script is supposed to run in, which more often than not is the bash-shell, or sh-shell, which is the default shell in most distros. They are both the same shell now (sh was the first one, made by a guy named Bourne, and when it was improved they called it the Bourne Again Shell, or bash), but are accessible as both sh and bash to maintain backwards compatibility.
To make it executable, you simply do the following:```
chmod +x myscript
``` "myscript" being the name of the file containing the commands. You will then be able to execute it like any other command/script/program, and in doing so all the commands in it will be executed in sequence.

The second part - /rc5.d/S20hdparm.local - refers to the SysV init-style which is used by many (most?) Linux distros today. The way it works is, Linux has 7 runlevels (labeled 0-6), which you can say are modes of operation. The difference between them is simply which startup-programs and -daemons are started. For all distros, runlevel 0 is halt (e.g. stop the system) runlevel 1 is single-user, and runlevel 6 is reboot. Anything in between varies from distro to distro - in Ubuntu, the default runlevel is 2, which is the one I'm sure 99% of Ubuntu-users are running in most of the time.
The way the system controls which items are started or shut down in a runlevel is through the files located in the /etc/rcX.d directories, X being the number of the runlevel. In these directories, each script has a name starting with S or K, and a two-digit number, usually followed by the actual name of the script.
The letter (S or K) tells wether the script is to be started or stopped in the runlevel (Started or Killed).
The two-digit number shows where in the sequence the script is to be executed - S01 is started first, S99 is started last.
The rest of the name is as I said the actual name of the script. The point is that all these scripts in the various runlevels, are usually just symbolic links to the actual scripts, which are located in /etc/init.d - in that directory they are only named their actual name, no S or K or two-digit number.

Now, in order to add your script the way you're indicating in Ubuntu, you could do one of two things:
1: Put the script in the /etc/rc2.d directory, and name it S20hdparm.local
2: Put it in the /etc/inid.d directory and just name it hdparm.local, then execute the command "update-rc.d hdparm.local defaults 20". This will create the necessary symbolic links in the /etc/rcX.d directories, and make it start in runlevels 2-5, and stop in runlevels 0, 1 and 6.

Of these two, the first is obviously the easiest, while the second is the "more proper" way of doing it. Usually, these scripts should also accept a "start" and "stop" parameter when executed, but for the one you're trying to do that really isn't necessary as all you're doing is setting device-parameters on IDE-devices, and you can't really "stop" that kind of operation ;)

Now, there is a cleaner way to set such parameters, and that is by editing the /etc/hdparm.conf file. This file contains entries for the devices which will be configured on boot. For instance, to enable DMA for hdc, you would put the following into /etc/hdparm.conf:```
hdc {
    dma = on
}
```
Simple, isn't it? You can set any parameter that hdparm understands here - see the manual page for hdparm.conf for a complete list (e.g. type "man hdparm.conf" - scroll using arrowkeys or page down/page up, hit q to exit the manpage)

Hope that helps :)

---

### Post by stanz on 2006-04-10
Hi All... Hi Ensnared,
I'm trying to use hdparm- for what it can do.
My 'Join Date', is my introduction to learning linux and working my pc- for real.
I try to use & work, information gathered- best i can...for a newbie.. :rolleyes:

From other posts & [links like this- detailed on hdparm]("http://www.die.net/doc/linux/man/man8/hdparm.8.html"), I've tried to improve my graphic & hd performance.
When i scroll quickly down a page and letters turn into lines- i'm not liking whats in my box.
I've edited the *hdparm.conf* file- a few times before, with good results, but- I'm still goofing up other things, which usually results in another fresh install.  :???:

This time- changes weren't taken and i wondered why.
In searching around my files and here, I've come to find- [EasyUbuntu]("http://easyubuntu.freecontrib.org/get.html"), has my changes in **it's** directory files, and my  */etc/init.d/hdparm.conf* - is not configured by my adjustments. I'm not liking that doubling up thing!
Anyway~ That was after i found that "*application/x-shellscript*", and thought- that
would be the one, to modify...kinda?

So, I'm going back to square one...& removing EasyUbuntu.
Your reply told me much- Thank you... So to say- I've learnt from it! 
It will be printed & read twice- before my next attempt...
Will post my results & shell script !  Thanks again...

---

### Post by darkness_nz on 2006-04-16
i've tried the solutions listed here but no joy. hdparm.conf does nothing. 
and the output of hdparm -d 1 is 
HDIO_SET_DMA failed: Inappropriate ioctl for device

from what the first poster said this is because of the drives being recognised as SCSI. I just don't know why. they are 2 standard IDE optical drives running off the IDE of the motherboard. 

I'm going to play with motherboard settings to see if that helps. the board has SATA raid, IDE RAID and regular IDE which is where the drives are plugged in.

---

### Post by stanz on 2006-04-20
hey darknes nz ... any joy yet?

---

