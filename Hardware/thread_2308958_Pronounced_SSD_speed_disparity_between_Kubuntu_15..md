---
title: "Pronounced SSD speed disparity between Kubuntu 15.10 and Windows 10"
date: 2016-01-06
forum: Hardware
---

### Post by Kevin_Cain on 2016-01-06
[FONT=Arial]I've been using 'tiny' OTG SSD drives (128GB, 256GB and 512GB, actually) with Kubuntu and Windows 10.  Strangely, I am seeing less than half of the speed on Kubuntu; below I compare sequential read speeds on both:[/FONT]
[FONT=Arial]*sudo hdparm -t /dev/sdd*:  [/FONT]**[FONT=Arial]~189 MB/sec[/FONT]**[FONT=Arial], formatted EXT4, Kubuntu 15.10, USB3.0 bus[/FONT]
[FONT=Arial]Sequential read via AS SSD Benchmark: [/FONT][FONT=Arial] **~402 MB/sec**[/FONT][FONT=Arial], formatted NTFS, Windows 10, USB3.0 bus
The manufacturer shows sequential read benchmarks via USB 3.0 at **~428 MB/sec** ([FONT=Verdana]http://mydigitalssd.com/mobile-ssd.php[/FONT]).

In both cases, I'm simply plugging the SSD into a single USB 3.0 port (no hub).  [/FONT][FONT=Arial]While the OTG SSD seqential read value from[/FONT]* hdparm*[FONT=Arial] is ~189 MB/sec, as above, the SATA boot SSD on the same machine tests at ~600 MB/sec using an identical* hdparm -t *command.  So the system has no trouble with an internal SSD (again, SATA) running at advertised speeds, but over USB 3.0 I'm seeing less than half of the ~428 MB/sec speeds quoted above.[/FONT]

[FONT=Arial]Notes:[/FONT]

[LIST]
[*]I see that Kubuntu is using the UAS driver, which I believe should be the correct approach:  *lsusb -t* (tree view) returns &#8216;Driver=uas, 5000M&#8217; (lsusb lists buses/devices)
[*]I also see that TRIM is indeed supported for the OTG drive under Linux:  hdparm -I /dev/sda | grep TRIM returns &#8216;TRIM supported (limit 8 blocks)
[/LIST]
[FONT=Arial]Some consider EXT+TRIM as perhaps the ideal file system for SSD [/FONT][FONT=Arial]([/FONT][COLOR=#1155CC]_[http://superuser.com/questions/228657/which-linux-filesystem-works-best-with-ssd](http://superuser.com/questions/228657/which-linux-filesystem-works-best-with-ssd)_[/COLOR][FONT=Arial]), however  &#8220;Solid State Drives (SSDs) are not PnP devices. Special considerations such as partition alignment, choice of file system, TRIM support, etc. are needed to set up SSDs for optimal performance.&#8221; ([/FONT][COLOR=#1155CC]_[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)_[/COLOR][FONT=Arial]).  Other links on the above page suggest trim settings can have the opposite effect intended.[/FONT]

---

### Post by matt_symes on 2016-01-06
Hi

Interesting post indeed ! 

I don't own any external USB 3 SSD drives, only internal ones, so i can't verify your metrics.

Is there a support question or are you just posting your metrics ?

I wonder if Windows 10 is caching and Linux is not ? I must read the man page for hdpram again. 

Kind regards

---

### Post by Kevin_Cain on 2016-01-08
To make a more direct comparison, I ran my Windows 10 / Kubuntu 15.10 transfer tests on the same computer, with the same OTG SSD drive.  The results for sequential read:

[COLOR=#000000][FONT=Arial]*sudo hdparm -t:  * [/FONT][/COLOR][B][FONT=Arial]~125 MB/sec[/FONT][FONT=Arial], formatted EXT4, Kubuntu 15.10, USB3.0 bus[/FONT]
[FONT=Arial]AS SSD Benchmark: [/FONT][FONT=Arial]**~402 MB/sec**[/FONT][FONT=Arial], formatted NTFS, Windows 10, USB3.0 bus
[/FONT][/B]
My question is simply:  am I looking at this wrong, or does the same drive over the same hardware bus really perform almost four times faster in Windows 10?  As noted above, *hdparm* reports the *internal* SSD on this system reads sequentially at ~410 MB/sec, about the speed I get for the external USB 3.0 SSD in Windows (~402 MB/sec).

---

### Post by matt_symes on 2016-01-08
Hi

> **Kevin_Cain said:**
> To make a more direct comparison, I ran my Windows 10 / Kubuntu 15.10 transfer tests on the same computer, with the same OTG SSD drive.  The results for sequential read:

[COLOR=#000000][FONT=Arial]*sudo hdparm -t:  * [/FONT][/COLOR][B][FONT=Arial]~125 MB/sec[/FONT][FONT=Arial], formatted EXT4, Kubuntu 15.10, USB3.0 bus[/FONT]
[FONT=Arial]AS SSD Benchmark: [/FONT][FONT=Arial]**~402 MB/sec**[/FONT][FONT=Arial], formatted NTFS, Windows 10, USB3.0 bus
[/FONT][/B]
My question is simply:  am I looking at this wrong, or does the same drive over the same hardware bus really perform almost four times faster in Windows 10?  As noted above, *hdparm* reports the *internal* SSD on this system reads sequentially at ~410 MB/sec, about the speed I get for the external USB 3.0 SSD in Windows (~402 MB/sec).

Your figures look valid but i think something else maybe going on.

I may well be wrong as i have no way to test but, that really looks like it may be Windows 10 caching. Maybe the Windows 10 driver does some magic with that brand of external SSD ?

I really don't know. It's all supposition on my part and maybe Windows 10 is better in this regard.

How many times are you running each test ? Are you taking an average ?

Is it a USB power management issue ? Try switching it off on linux for testing ?

Copy and paste these commands into the terminal, especially the top one to eliminate typos.

```
sudo sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT=\".*[^"]/& usbcore.autosuspend=-1/g' /etc/default/grub
```

```
sudo update-grub
```

```
sudo reboot
```

Then try testing again.

I have not come across such large differences in SSD USB performance, either on the net or in my personal tests with USB (but with spinning rust only and on Windows 7), and that's why i find it hard to believe there's not something else going on.

Hopefully someone else is in a position to rerun your tests and see if there is something going on.

I would be really interested to know the cause myself.

Kind regards

---

### Post by oldfred on 2016-01-08
I do not know about NTFS, but suspect it is not as reliable then.

I have seen these as suggestions for mounting SSD internal drive in fstab. But do not know how USB drive default mount is. Or are you manually mounting with your own parameters.

See man mount for details.
       noatime - Linux writes update times, not required for most appliations, so can be turned off and fewer writes speeds system.
data=writeback - to me this is dangerous, but is speed over reliability. Best to see man mount for details of what setting really does. Windows may be doing something like this.

---

### Post by Kevin_Cain on 2016-01-13
Thanks very much, [[COLOR=#C61919]matt_symes[/COLOR]]("http://ubuntuforums.org/member.php?u=1067998")[COLOR=#000000] [/COLOR], for your good suggestions.

I tried your proposed sed values, but after averaging many runs of *hdparm *I'm still seeing the same transfer speeds in Ubuntu:

[COLOR=#000000][COLOR=#000000][FONT=Arial]*sudo hdparm -t: *[/FONT][/COLOR][/COLOR][B][FONT=Arial]~123 MB/sec[/FONT][FONT=Arial], formatted EXT4, Kubuntu 15.10, USB3.0 bus

[/FONT][/B]I understand your willingness to potentially assign the higher transfer speeds to Windows 10 cache (and therefore not a real speed), but again with my internal SSD on the same laptop I am seeing consistent ~410MB/s speeds reported by *hdparm*.  So it really appears there is an actual, and sizeable, difference between these two SSDs, which based on their spec should perform rather similarly.

I'm inclined to conclude that the Kubuntu UAS driver doesn't see an external USB3 connection in the same way as the internal SATA bus.

---

