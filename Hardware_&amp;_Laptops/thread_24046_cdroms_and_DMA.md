---
title: "cdroms and DMA"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by the_thunderbird on 2005-04-05
After installing ubuntu I found my cdroms did not have dma set by default, when trying to access them or copy larger files from them my whole system slows down.... Here is the output from my hdparm... Is this a known problem, do I need to rebuild my kernel t get them working?

> 
ian@nobby:~$ sudo hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
ian@nobby:~$


This is weird...

---

### Post by dusu on 2005-04-05
Yes,

I also have the same problem... I don't know why dma is disabled by default

---

### Post by acascianelli on 2005-04-05
add this to the end of your /etc/hdparm.conf file

```
/dev/hdc {
        dma = on
}
``` 

then go into your /etc/rcS.d folder and change the startup order of hdparm by setting it to S29

```
sudo mv SXXhdparm S29hdparm
```

to test it just execute the S29hdparm script and do a hdparm /dev/hdc.

---

### Post by the_thunderbird on 2005-04-07
[QUOTE=acascianelli]add this to the end of your /etc/hdparm.conf file

```
/dev/hdc {
        dma = on
}
``` 

then go into your /etc/rcS.d folder and change the startup order of hdparm by setting it to S29

```
sudo mv SXXhdparm S29hdparm
```

to test it just execute the S29hdparm script and do a hdparm /dev/hdc.[/QUOTE]

As stated... I have tried enabling DMA manually, it says that the operation is not permitted.

---

### Post by Jad on 2005-04-07
i'll try it and report

---

### Post by TjaBBe on 2005-04-07
Have you built your own kernel? If so, you should compile your IDE/DMA drivers hard in as you don't have an ini file pre-loading these modules. Also make sure you have the specific IDE drivers for your chipset installed.

With the default Ubuntu kernel dma IS enabled by default. If it's not, something else is wrong...

---

### Post by acascianelli on 2005-04-07
you have to be logged in as root and you can't have a cd mounted

---

### Post by Jad on 2005-04-07
Why do I need to be logged in as root to burn data?

---

### Post by TjaBBe on 2005-04-07
[QUOTE=Jad]Why do I need to be logged in as root to burn data?[/QUOTE]

I guess he means you must be root (or offcourse sudo) to enable dma. But this is not the issue because the topicstarter DOES use sudo.

---

### Post by wmcbrine on 2005-04-07
S29 is actually not late enough (the optical drive is not yet available), at least on my system. I copied (not moved) mine to S99. (I left S07 in so that it might speed up booting.)

DMA *is* on by default for my HD, but *not* for my DVD+R. Also, multcount is not enabled by default for the HD; but this has a much smaller effect.

---

### Post by igloo on 2005-04-10
I'm having much the same problem.

I've got the OS on a SATA drive, and I keep all my goodies on 3 IDE drives.  The SATA drive works fine (as I'd expect) but the IDE drives don't want to to into DMA mode.

- If I boot normally then try to turn DMA on using hdparm I get '
HDIO_SET_DMA failed: Operation not permitted'

- If I comment out the ide-generic and ide-disk lines in /etc/modules, reboot, then manually modprobe the modules from bash, hdparm will then set the DMA without fail.

- editing /etc/hdparm.conf does nothing (probably because S07hdparm is called before the ide modules are loaded (by S20module-init-tools and S20modutils, one would presume))

So i'm assuming something is happening during bootup that is breaking either my IDE bus or hdparm.

---

### Post by Leebobs on 2005-04-10
A number of us are discussing the same thing:
[http://www.ubuntuforums.org/showthread.php?t=25541](http://www.ubuntuforums.org/showthread.php?t=25541)

We all have our OS on a SATA drive and cannot enable DMA on our optical PATA drives.

As a Linux n00b, I have no idea why this isn't working. Any help would of course be appreciated!  :-?

---

### Post by the_thunderbird on 2005-04-10
I have a SATA drive for my operating system. My IDE cd+rw/dvd don't work in DMA mode in ubuntu though... I think I may have to grin and bare it and just rebuild my kernel so that it does support them...

---

### Post by the_thunderbird on 2005-04-10
[QUOTE=the_thunderbird]I have a SATA drive for my operating system. My IDE cd+rw/dvd don't work in DMA mode in ubuntu though... I think I may have to grin and bare it and just rebuild my kernel so that it does support them...[/QUOTE]

Soemthing else I forgot to mention, I was using Gentoo before ubuntu (I am not a linux n00b at all) and it worked straight out the box (although I configured the kernel myself), which means its not a bug in the kernel with SATA drives and IDE drives, most probably just a mistake in kernel configuration...

---

### Post by Leebobs on 2005-04-10
[QUOTE=the_thunderbird]Soemthing else I forgot to mention, I was using Gentoo before ubuntu (I am not a linux n00b at all) and it worked straight out the box (although I configured the kernel myself), which means its not a bug in the kernel with SATA drives and IDE drives, most probably just a mistake in kernel configuration...[/QUOTE]

Could you work with the dev's to fix it?!?

---

### Post by the_thunderbird on 2005-04-10
[QUOTE=Leebobs]Could you work with the dev's to fix it?!?[/QUOTE]

Yeah am gonna have a look at the kernel configuration and rework it to be similar but at the same time fix a lot of the DMA bugs  O:) 

I'll sort out a deb file for the kernel for fixing ;)

---

### Post by Leebobs on 2005-04-11
[QUOTE=the_thunderbird]Yeah am gonna have a look at the kernel configuration and rework it to be similar but at the same time fix a lot of the DMA bugs  O:) 

I'll sort out a deb file for the kernel for fixing ;)[/QUOTE]

 \\:D/ Quality... keep us informed!!  :grin:

---

### Post by Cmdr_K00n on 2005-04-13
I am having the same problems!
I have an AMD64 3000+ processor, with a 
200GB WestDigi SATA drive housing ubuntu,
80GB IDE with WinXP on IDE-1  (contains the bootloader)
DVD Burner on IDE-2

I cannot seem to set ide on for ANY of these drives!
<code>
root@nakamura:/home/daniel # hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
root@nakamura:/home/daniel # hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

root@nakamura:/home/daniel # hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
root@nakamura:/home/daniel #
</code>

Has there been any results yet? Is this a kernel config problem or maybe hardware configuraton error?

---

### Post by boo on 2005-04-13
[QUOTE=Cmdr_K00n]I am having the same problems!
I have an AMD64 3000+ processor, with a 
200GB WestDigi SATA drive housing ubuntu,
80GB IDE with WinXP on IDE-1  (contains the bootloader)
DVD Burner on IDE-2
[/QUOTE]
please do a `lsmod | grep amd` and check for the module amd74xx.
if its not there, put it in your etc/modules before everything else. reboot, and it should work fine, you still need to set DMA for your DVD drive manually, since the kernel-option "enable dma only for disks" is checked for some reason.

edit: oh, i somehow assumed that you got an nforce board, if you have a via-based board, you may want to try the via driver (should be something like via82cxxx, not sure about the name, never had one of those chipsets)

---

### Post by jeremy on 2005-04-13
This thread here [http://ubuntuforums.org/showthread.php?t=19519](http://ubuntuforums.org/showthread.php?t=19519) has more info.

---

### Post by Cmdr_K00n on 2005-04-13
root@nakamura:/home/daniel # lsmod | grep amd
amd74xx                15280  1
ide_core              143748  4 amd74xx,ide_generic,ide_disk,ide_cd

Yeah this is on AOK
The othe thing is it is a nforce board. the
Gigabyte K8NS-ULTRA-939
So it is a socked 939 board, and for some reason in device manager it seems to think it is a 754 socket cpu. hmm

---

### Post by Cmdr_K00n on 2005-04-13
OK progress is better!
I can now turn on dma for my ide drives, but the SATA drive still gives me this error:

<code>root@nakamura:/home/daniel # hdparm -d 1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
root@nakamura:/home/daniel # hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
root@nakamura:/home/daniel # hdparm -d 1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
root@nakamura:/home/daniel #
</code>

Has anyone got any ideas?

PS:
Ahh i just spotted sata_nv module, ill try and stick that at the top:

<code>
root@nakamura:/home/daniel # cat /etc/modules

amd74xx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod
nvidia

</code>

---

### Post by Cmdr_K00n on 2005-04-13
Nopes, still the same error
;)
 [-o<

---

### Post by Cmdr_K00n on 2005-04-13
One of the other things that the Dev's may want to look at is that my SATA drive is running from my Nvidia SATA connectors, and lspci seems to not identify a nforce3 chipset? Does anyone know if this has to be done by the user. I looked on the nvidia website, but their ones only cover sound and ethernet.


root@nakamura:/home/daniel # lspci
[B]0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)[/B]
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
**0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)** --This is my Geforce6600GT
0000:02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:02:08.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
0000:02:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
0000:02:0b.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:02:0d.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
0000:02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)

---

### Post by Dr Gonzo on 2005-04-15
Just so you all know, you can't use hdparm to enable DMA on SATA drives, as this is purely an IDE thing and Linux recognizes SATA drives as SCSI devices.

I'm wrestling with the same stupid issue -- OS is on a SATA drive, 2 cdroms on IDE, and I can't seem to load DMA for them.  This is all with the standard kernel.

So, I rebuilt a custom one.  I now have DMA working, but for some reason, I can't seem to get a framebuffer console screen.  It seems to just blank.  This exact configuration worked just fine with Debian, so I'm at a loss to explain why it's not working now.  I just rebuilt my kernel again before leaving the house, but I haven't tried it yet.

It's really pretty damn annoying, though, that I can't seem to get it working correctly with the stock kernel.  I'm pretty much over having to compile my own (especially since every other kernel version seems to break something) and would like to just use the stock kernel provided by Ubuntu.

Their SATA support seems a little shady.  To get it to recognize my SATA controller at all, I had to rebuild my initrd to contain the drivers for it.  Otherwise, the kernel panics looking for the root partition.

I'll let you all know if I figure anything out.

---

### Post by svizi on 2005-04-17
[QUOTE=Dr Gonzo]Just so you all know, you can't use hdparm to enable DMA on SATA drives, as this is purely an IDE thing and Linux recognizes SATA drives as SCSI devices.

I'm wrestling with the same stupid issue -- OS is on a SATA drive, 2 cdroms on IDE, and I can't seem to load DMA for them.  This is all with the standard kernel.

So, I rebuilt a custom one.  I now have DMA working, but for some reason, I can't seem to get a framebuffer console screen.  It seems to just blank.  This exact configuration worked just fine with Debian, so I'm at a loss to explain why it's not working now.  I just rebuilt my kernel again before leaving the house, but I haven't tried it yet.

It's really pretty damn annoying, though, that I can't seem to get it working correctly with the stock kernel.  I'm pretty much over having to compile my own (especially since every other kernel version seems to break something) and would like to just use the stock kernel provided by Ubuntu.

Their SATA support seems a little shady.  To get it to recognize my SATA controller at all, I had to rebuild my initrd to contain the drivers for it.  Otherwise, the kernel panics looking for the root partition.

I'll let you all know if I figure anything out.[/QUOTE]
 Sort of same problems over here.

I can't turn on the dma for all my ide dvd-rom using 

sudo hdparm -d 1 /dev/hdd ....

But when I reboot I should do that thing again.

I put 

/dev/hdd {

              dma =on 
}

but when I get into gnome it freezes.

Can i do something about that?

---

### Post by Dr Gonzo on 2005-04-17
Make sure your IDE chipset's drivers are **first** in /etc/modules, before any of the other ide stuff.  lspci should tell you what chipset that is.

---

### Post by denzilla on 2005-04-17
Here's mine:

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

Which one is the chipset? lp, ide-generic?

---

### Post by heimo on 2005-04-17
[QUOTE=denzilla]Here's mine:

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

Which one is the chipset? lp, ide-generic?[/QUOTE]

None of those. You need to know which module to add - for example piix for Intel ICH5/6 based motherboardds, via82cxxx for Via 8235 / 8237 based motherboards and so on.

---

### Post by denzilla on 2005-04-17
[QUOTE=heimo]None of those. You need to know which module to add - for example piix for Intel ICH5/6 based motherboardds, via82cxxx for Via 8235 / 8237 based motherboards and so on.[/QUOTE]

I got a VIA KT133A/686B according to the DFI site. This is what lspci says:


0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc.: Unknown device b115
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:11.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a2)


So what exactly do I need to add to the modules? Forgive me, you're among the ignorant :) Also, does anything need to be removed?

I'm a little curious as to why the chipset drivers weren't installed during the OS installation.?Ubuntu seems to detect the chipset afterall.

---

### Post by heimo on 2005-04-17
It's most probably via82cxxx. Something like this may work (actually, it's an exact copy of mine, and I have DMA enabled):

 ```

via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

```

---

### Post by svizi on 2005-04-18
[QUOTE=Dr Gonzo]Make sure your IDE chipset's drivers are **first** in /etc/modules, before any of the other ide stuff.  lspci should tell you what chipset that is.[/QUOTE]
 I get these from /etc/modules

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod

My chipset is nvidia nforce2. Does anyone knows what i shall add?

---

### Post by denzilla on 2005-04-18
[QUOTE=heimo]It's most probably via82cxxx. Something like this may work (actually, it's an exact copy of mine, and I have DMA enabled):

 ```

via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

```[/QUOTE]


What happens if its not the right chipset to add? Will my PC still boot? Just want top make sure I can reverse it should it be wrong.

---

### Post by heimo on 2005-04-18
[QUOTE=denzilla]What happens if its not the right chipset to add? Will my PC still boot? Just want top make sure I can reverse it should it be wrong.[/QUOTE]

I'd expect unexpected, but probably the module just fails to load and your computer boots like before. You can always try to load it first with modprobe - for example: *modprobe via82cxxx *and see if you get any errors. If not, you can try *hdparm -d /dev/hda *(or whatever your drive is) to enable DMA, but it doesn't neccessarily work before boot (which is a shame, I hate rebooting - I don't know why this is happening).

Remember to edit */etc/hdparm.conf* to enable dma automaticly and check that it's run during boot - probably link in */etc/rc2.d/S99hdparm*

---

### Post by denzilla on 2005-04-19
I've got entries in the bootmisc file for enabling DMA on bootup. I had an issue where DMA would always be disabled after bootup and that fixed it. I could enable DMA on my DVD Drive after boot and it worked fine, though. I guess the root problem was not having chipset drivers loaded in modules file. 

I used modprobe via82cxxx but after hitting enter, it never really did anything, just dropped down to another input line. That normal?

---

### Post by heimo on 2005-04-19
[QUOTE=denzilla]
I used modprobe via82cxxx but after hitting enter, it never really did anything, just dropped down to another input line. That normal?[/QUOTE]
 
Oh, that's good news. Unix philosophy - "No news is good news." You could have checked with lsmod all the loaded modules and seen via82cxxx listed. In other words, it did load the module, which quite much proves that it was correct one. (I should have explained that better in the first place.)
 
Great you got it working!

---

### Post by denzilla on 2005-04-19
I added it and removed the lines I added to bootmisc to enable DMA. The chipset addition didn't enable DMA at all. I had to re-add the extra lines to bootmisc to get DMA on again.

---

### Post by heimo on 2005-04-19
[QUOTE=denzilla]I added it and removed the lines I added to bootmisc to enable DMA. The chipset addition didn't enable DMA at all. I had to re-add the extra lines to bootmisc to get DMA on again.[/QUOTE]

I'm not sure if I follow. You most probably need the chipset module loaded to be able to enable DMA, where ever the DMA is enabled (hdparm.conf / bootmisc). However just loading the module doesn't automaticly enable DMA. (I may have misunderstood your post, sorry if I'm stating the obvious.)

---

### Post by Turin Turambar on 2005-04-20
I tried adding a hdparm dma settings in hdparm.conf and I got DMA enabled for cdrom/dvd. However, during boot I received this message "/dev/hdc directory or filename does not exist", but DMA was enabled for hdc anyhow. :)
Strange...?

---

### Post by heimo on 2005-04-20
[QUOTE=Turin Turambar]I tried adding a hdparm dma settings in hdparm.conf and I got DMA enabled for cdrom/dvd. However, during boot I received this message "/dev/hdc directory or filename does not exist", but DMA was enabled for hdc anyhow. :)
Strange...?[/QUOTE]

There's compile time kernel setting "Enable DMA only for disks" and it's enabled by default in Ubuntu. (at least in 2.6.10 kernel package). It causes DMA to be enabled for hard disks and not for ATAPI (cdrom) devices.

---

### Post by Turin Turambar on 2005-04-20
[QUOTE=heimo]There's compile time kernel setting "Enable DMA only for disks" and it's enabled by default in Ubuntu. (at least in 2.6.10 kernel package). It causes DMA to be enabled for hard disks and not for ATAPI (cdrom) devices.[/QUOTE]

Thought so. :)
But how come that it said "dir/file not found"?
I have 2 cdrom/dvd devices: hdc & hdd. For the first it said "not found", but the 2nd didn't mention at all (so it was totally ok). However, both devices got DMA enabled!

I tried to remove /dev/hdc, but then /dev/hdd got the same "not found" message. Weird. :)
All is gone now, since I added those lines in bootmisc. I'm just curious why it reports no dir/file.

---

### Post by heimo on 2005-04-20
I tried to bypass that question. ;) I don't know. I haven't looked, but maybe there's not enough time between loading modules like ide_cd and cdrom and that special file /dev/hdc /dev/hdd wasn't there for hdparm .. oh, that doesn't compute.

I don't know. But that error is because there wasn't that file (special file, device) for some command. If you rmmod ide_cd, you'll notice that those cdrom devices disappear (that wasn't the case some time ago, nowadays those files are created on fly).

Maybe yoy have hdparm in hdparm initscript (/etc/init.d/hdparm) earlier in boot sequence and later hdparm in bootmisc and the first one fails because modules haven't been loaded and the latter ... No. I don't understand.

But maybe you got some hints where to look (if you're still interested). It's sometimes educational to find why things happen - and to get rid of those annoying but pointless error messages. That teaches how your system works and the nect problem is easier to solve.

Ah - I love Linux. It's possible to go under hood and see how everyhing works. Boot process is one of those places where you can learn lots of your computer. And there's no big jump to go check what kernel does during boot.

---

### Post by ozeroc on 2005-06-01
Hey all...

  I've been researching this problem and I figured it out.  

- I have an AMD64 on a mobo with nforce3 and I boot off a SATA drive.  

- I was having problems burning DVDs and found I needed to turn on DMA and I got the 'HDIO_SET_DMA failed: Operation not permitted' error.

- I read in Bugzilla that it was due to the ide_* drivers grabbing the devices too soon and setting them to PIO

- The supposed fix was to put AMD74xx first in my /etc/modules file so that it would get  to these ide devices first...  This caused my system to hang on bootup

- My fix was to edit /etc/hotplug/blacklist and add AMD74xx.  This allowed AMD74xx to be assigned from /etc/modules.  

-Command line test of 'sudo hdparm /dev/hda' was successful so I edited /etc/hdparm.conf to turn on DMA automatically at bootup and it works!

Yeah!  \\:D/ 

Oz

---

### Post by Jurgen272 on 2005-10-13
[QUOTE=ozeroc]Hey all...

  I've been researching this problem and I figured it out.  

- I have an AMD64 on a mobo with nforce3 and I boot off a SATA drive.  

- I was having problems burning DVDs and found I needed to turn on DMA and I got the 'HDIO_SET_DMA failed: Operation not permitted' error.

- I read in Bugzilla that it was due to the ide_* drivers grabbing the devices too soon and setting them to PIO

- The supposed fix was to put AMD74xx first in my /etc/modules file so that it would get  to these ide devices first...  This caused my system to hang on bootup

- My fix was to edit /etc/hotplug/blacklist and add AMD74xx.  This allowed AMD74xx to be assigned from /etc/modules.  

-Command line test of 'sudo hdparm /dev/hda' was successful so I edited /etc/hdparm.conf to turn on DMA automatically at bootup and it works!

Yeah!  \\:D/ 

Oz[/QUOTE]

Worked for me with a different AMD64 mbo (nforce2)
I had to change AMD74xx with VIA82xxx

And after that DMA was on :razz:

---

