---
title: "dvd-rw drive support issue?"
date: 2009-11-07
forum: Hardware
---

### Post by helamsirrine on 2009-11-07
I am running 32-bit Karmic on a new Acer Aspire X1301 AMD AthlonII x2 215 dual core 3Gb DDR2 on a 200Gb ext3 partition. My issue is with the DVD Multi drive. 
('HL-DT-ST' 'DVDRAM GH41N') 
I think it is an LG. I read cds and dvd's just fine but when I try to burn anything with Kd3 or Brasero, I get a fault, even at the slowest writing speed. This is not a hardware issue as I succesfully burned the Karmic Live cd from Win 7 on my other partition.

For an example I tried to Burn the 64-bit ISO of Karmic to cd with Kd3 and was told I had a buffer underrun.
```
  p, li { white-space: pre-wrap; }  [FONT=DejaVu Sans Mono]Last chance to quit, starting dummy write in    2 seconds.[/FONT]
 [FONT=DejaVu Sans Mono]   1 seconds.[/FONT]
 [FONT=DejaVu Sans Mono]   0 seconds. Operation starts.[/FONT]
 [FONT=DejaVu Sans Mono]Waiting for reader process to fill input buffer ... input buffer ready.[/FONT]
 [FONT=DejaVu Sans Mono]Starting new track at sector: 0[/FONT]
 [FONT=DejaVu Sans Mono]Track 01:    0 of  690 MB written.[/FONT]
 [FONT=DejaVu Sans Mono]Track 01:    1 of  690 MB written (fifo 100%) [buf  96%]   3.7x.[/FONT]
 [FONT=DejaVu Sans Mono]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error[/FONT]
 [FONT=DejaVu Sans Mono]CDB:  2A 00 00 00 02 4D 00 00 1F 00[/FONT]
 [FONT=DejaVu Sans Mono]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=DejaVu Sans Mono]Sense Bytes: 70 00 05 00 00 00 00 0A 2A 30 02 80 21 02 00 00[/FONT]
 **[FONT=DejaVu Sans Mono]Sense Key: 0x5 Illegal Request, Segment 0[/FONT]**
 **[FONT=DejaVu Sans Mono]Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0[/FONT]**
 **[FONT=DejaVu Sans Mono]Sense flags: Blk 0 (not valid) [/FONT]**
 **[FONT=DejaVu Sans Mono]cmd finished after 0.002s timeout 40s[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: The current problem looks like a buffer underrun.[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: Please report.[/FONT]**
 **[FONT=DejaVu Sans Mono]/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.[/FONT]**
 [FONT=DejaVu Sans Mono]write track data: error after 1206272 bytes[/FONT]
 [FONT=DejaVu Sans Mono]Writing  time:   11.764s[/FONT]
 [FONT=DejaVu Sans Mono]Average write speed 402.2x.[/FONT]
 [FONT=DejaVu Sans Mono]Min drive buffer fill was 96%[/FONT]
 [FONT=DejaVu Sans Mono]Fixating...[/FONT]
 **[FONT=DejaVu Sans Mono]WARNING: Some drives don't like fixation in dummy mode.[/FONT]**
 [FONT=DejaVu Sans Mono]Fixating time:   64.250s[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo had 211 puts and 20 gets.[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo was 0 times empty and 7 times full, min fill was 96%.[/FONT]
  [FONT=DejaVu Sans Mono]cdrecord command:[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -tao -dummy driveropts=burnfree -data -tsize=353688s -[/FONT]
 

```I have gotten similar code to this with brasero and running cdrecord directly from the terminal. The bolded stuff is pretty much identical every time. I have tried searching the forums and have noticed that other people have had problems with LG drives. 

Is there some kind of workaround for this?

Is there good burning program available that doesn't use wodim on the back end if that is my problem?
 
Sorry the post is so long but I am tearing my hair out over this one and I don't even know what my problem is. 

Thanks in advance.

[FONT=DejaVu Sans Mono]
[/FONT]

---

### Post by helamsirrine on 2009-11-07
this was in syslog after an attempted cd burn```
Nov  7 21:41:39 helam kernel: [ 3867.243796] sr 2:0:0:0: [sr0] Unhandled sense code
Nov  7 21:41:39 helam kernel: [ 3867.243804] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  7 21:41:39 helam kernel: [ 3867.243813] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
Nov  7 21:41:39 helam kernel: [ 3867.243823] sr 2:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Nov  7 21:41:39 helam kernel: [ 3867.243834] end_request: I/O error, dev sr0, sector 0
Nov  7 21:41:39 helam kernel: [ 3867.243844] Buffer I/O error on device sr0, logical block 0

```sr0 is my drive what does this mean?

---

### Post by helamsirrine on 2009-11-08
-bump-

Please help! Any advice welcome.

---

### Post by gilou on 2009-11-17
Hello

I have the same problem with a sata burning device, brand LG.
It's not sure it's the brand, perhaps the chipset, the kernel in karmic , or more surely wodim is broken.

k3b, brasero, gnomebaker and xfburn fails.

You should try nerolinux if you want. It didn't work for me.

There are somme related post on the subject and I didn't 
find any issue.

Burning is ok and at full speed in debian lenny (separated partition).

I was able to burn in jaunty, it worked in karmil RC and then nothing.

dmesg opr syslog show something wrong on I/O about sr0; it's your device. 


this post about rights of wodim was of no help : you should look :

 [http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34](http://art.ubuntuforums.org/showpost.php?p=7185976&postcount=34)

As for me I'm looking for updates to solve this and I use debian lenny, installed in other partition. Efficient and stable as always.

gilou

---

### Post by jagerhans on 2009-11-19
hello all , after the upgrade to karmic i cant add session to DVD-RW's . Nero linux can't either. i have a SATA LG GH22NS40, firmware (not upgraded) NL00, max UDMA/100 . my system is athlon AMD64x2 4gb ram. i get all kinds of errors , sometimes i can't even start a first session write. no problems with DVD-R , except that it complains my drive not supporting 22x write (false) and increments it to 24x (impossible, the drive max R speed is 22) . to be honest i have k-ubuntu but i think wodim and cdrwtools are same versions. any hint? i'm just about to dump ubuntu and get some other distro.

---

### Post by gilou on 2009-11-20
Hello Jagerhans

kubuntu our ubuntu use same version of course.
My LG writer does not work with nero or k3b in karmic but very good in debian lenny.

It's been two weeks now and there's no updates coming, neither I have seen a bug report. For me karmic is broken, I'm going back to jaunty and will wait for 10.04 ubuntu (LTS), and I use debian lenny on a different partition on the disk with the same /home.

There are, according to the logs, errors in I/O with driver ahci when simulating or burning, though playing dvd works well. I don't know if it's a kernel issue or wodim.

gilou

---

### Post by jagerhans on 2009-11-20
i attempted to boot the old kernels but i get an error complaining about the impossibility of mounting partitions at boot time and the system enters a recovery shell so i couldn't find out if it was a kernel bug. how does one downgrade the install: it is possible to turn back to 9.04 ? 
i messed around with some hdparm settings and other versions of cdrecord - k3b and the best i got is that now i can write a first session of 6x media . wtf.  this is one of the things that stain the good name of linux. i'd like to try a firmware update but can't get access to a sata windows machine to flash the drive with the windows utility provided by LG corp. why manufacturers never take the harassment to release linux binaries or at least give a boot disk version... a DOS  version would be nice . whatever.

---

### Post by gilou on 2009-11-20
Well I'm going to reinstall 9.04 jaunty instead of karmic too, you must get a copy of ubuntu 9.04 iso and reinstall- formatting /. If you have /home on a separated partition, of course we can keep /home unchanged. Usually ther's no harm doing this. Otherwise be sure to make a copy of your personal files and configuration of some programs, such as evolution, firefox...

Personaly I don't believe in updating the firmware of the drive.

---

### Post by gilou on 2009-11-27
Hello

I tested the LG writer in fedora rc12 and other distros, it works fine in debian lenny and  that's all!

Downgrading to jaunty didn't change anything.

I've finally changed the cd/dvd writer for a sony, named as optiarc AD-5240-S in k3b.

I'm running karmic 32 bit and use the same kernel before and after the change of drive : 2.6.34-14-generic.
The new drive is sata also.

All is fine now, the newest kernel of ubuntu seems to unsupport LG drive (burners). But I don't know where is the problem.

So this is not particuliar optimisation or wodim issue but only kernel version.

gilou

---

### Post by jagerhans on 2009-12-01
i had enough with ubuntu, and i'm running it since feisty. switching to debian, good-bye and good luck.

---

### Post by gilou on 2009-12-01
> **jagerhans said:**
> i had enough with ubuntu, and i'm running it since feisty. switching to debian, good-bye and good luck.

Debian is good, and is easy for ubuntu users. I use both and expect that the next ubuntu release would have less issues like this one.

gilou

---

### Post by anv on 2009-12-01
O, others had this problem too, I'm also one unhappy owner of new LG SATA DVD-RW, but it works some if compared to one SAMSUNG SATA DVD-RW which I bought first before change as I believed it would be issue in that new drive. I just wanted to buy one SATA drive instead of my IDE DVD burner (NEC) which works fine. It seems that the issue is related in SATA channell

started just seek know how from official Ubuntuforums, I have been assisted this evening earlier on our national Ubuntu site without solution, and the case is this same as others here have been described earlier in this thread.

well at least I can start to use it as DVD reader even it should be able to burn something

I use Xubuntu "Jaunty", I don't know is this "karmic" but maybe Debian or Arch for me too

---

### Post by robbie d on 2009-12-02
My burning was smooth as silk in jaunty, now I have a laptop running karmic 64 bit and a desktop running karmic 32 bit and all I ever seem to create is blank disks. The laptop drive worked fine before with vista and jaunty (wubi install). The desktop works fine in xp (some major programs not ported) just not with Karmic. I have tried Brasero and K3b (the eye candy of burners imho) and they consume 3.5 mins of time just to say 'oh you have inserted a blank disc, what now'. Slight unhappiness to what was a great OS.

---

### Post by cambesol on 2009-12-22
I am using Karmic and an LG GE20NU10 external USB DVD R/W. I am also seeing problems with k3b.  I compiled k3b (version 1.69) from source and although it runs, when creating an iso image from a DVD, it is incredibly slow (22 HOURS to create a 4.5GB image).

I used the identical hardware on Jaunty without any problems. 

I guess judging by the traffic on this thread, it is not seen as a major
inconvenience, but for me it is a let down.  I amy revert back to Jaunty until this is fixed.

Thanks for any help etc.

---

### Post by cambesol on 2009-12-22
I get repeated errors in my kern.log as follows:

Dec 22 22:34:17 t7-desktop kernel: [ 2994.234865] sr 7:0:0:0: [sr0] Unhandled sense code
Dec 22 22:34:17 t7-desktop kernel: [ 2994.234875] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 22 22:34:17 t7-desktop kernel: [ 2994.234883] sr 7:0:0:0: [sr0] Sense Key : Medium Error [current] 
Dec 22 22:34:17 t7-desktop kernel: [ 2994.234893] sr 7:0:0:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Dec 22 22:34:17 t7-desktop kernel: [ 2994.234906] end_request: I/O error, dev sr0, sector 8576
Dec 22 22:34:17 t7-desktop kernel: [ 2994.234917] Buffer I/O error on device sr0, logical block 1072

I will post more information If I can find any.

---

### Post by bclarky12 on 2010-04-07
i had the same problem as the first posters with the same dvd-drive, the hl... It works in Mandriva as well as Lenny, I use imgburn in mandriva, works well. I know how frustrating it was, strongly recommend the switch to Mandriva

---

