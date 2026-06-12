---
title: "raid 5 performance with dm_crypt"
date: 2008-08-02
forum: General Help
---

### Post by hastala on 2008-08-02
hi everybody,

i'm new to ubuntu, have just installed my new system and would like to know if the performance i'm getting from my encrypted raid 5 is ok.

here's my specs
cpu: amd 4850e
board: asus m3a-h/hdmi
hdd: 4 x Samsung HD642JJ for md0 (raid 5)
release: hardy heron

i'm using the onboard SATA connections with AHCI enabled in bios, array and ext3 are used without any special options, chunk size is 64k, encryption of md0 is done with dm_crypt (aes 256bit) and luks

hdparm:

/dev/md0:
 Timing cached reads:   1494 MB in  2.00 seconds = 746.93 MB/sec
 Timing buffered disk reads:  630 MB in  3.01 seconds = 209.49 MB/sec

bonnie++ pic attached

can somebody please comment?

---

### Post by MountainX on 2008-08-06
Your performance is much better than mine and I have a dual Xeon server with 6GB of RAM. These two reports are for single Samsung HD103UJ disks.

```
/dev/nocrypto:
 Timing cached reads:   1392 MB in  2.00 seconds = 695.48 MB/sec
 Timing buffered disk reads:  278 MB in  3.00 seconds =  92.57 MB/sec

/dev/mapper/crypto:
 Timing cached reads:   1380 MB in  2.00 seconds = 689.83 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.36 MB/sec

```

This report is for a RAID-5 array with 4x Seagate 15k RPM Cheetah drives:

```
/dev/mapper/sdX_crypt:
 Timing cached reads:   1356 MB in  2.00 seconds = 677.38 MB/sec
 Timing buffered disk reads:  174 MB in  3.03 seconds =  57.49 MB/sec

```

I think I have problems...

---

### Post by hastala on 2008-08-06
@everybody:
can somebody who knows a little more about raid performance leave some comments?
what could be expected (on relatively new hardware and linux sw raid) for:
4 x RAID 5 using 7200rpm drives
4 x RAID 5 using 15000rpm drives

@MountainX:
have you tried to run hdparm 3 times in a row? without that, or heavy disk usage before, the buffers aren't full enough and don't report the right speed (as far as i know)

can you try running bonnie++ and paste the output?
you can get it converted into readable html by pasting the CSV output (last line of bonnie++ output) into a text file and then run

bon_csv2html < your_textfile > your_html_file

are you using AHCI with NCQ?

---

### Post by fjgaude on 2008-08-06
Without knowing the CPU and memory speed and the drive sequential read, it's hard to say what your thruput should be. I do know that the best of the mainboards working off the PCI-E bus can show over 300MB/sec on hdparm tests.

Here's mine: With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz) 2/26/08, CPU fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v, 4X raid5 (each drive 70MB/sec thruput):

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec

```

Your low cached reads mean that CPU/memory is relatively slow, and likely can't handle the raid5 XORing and such quickly.

---

### Post by MountainX on 2008-08-06
> **hastala said:**
> @everybody:
can somebody who knows a little more about raid performance leave some comments?
what could be expected (on relatively new hardware and linux sw raid) for:
4 x RAID 5 using 7200rpm drives
4 x RAID 5 using 15000rpm drives

You might try asking that question [here]("http://www.hardforum.com/forumdisplay.php?f=29"):
[http://www.hardforum.com/forumdisplay.php?f=29](http://www.hardforum.com/forumdisplay.php?f=29)
On RAID questions I often get faster responses there, and there are guys there who know Linux.


> **hastala said:**
> 
@MountainX:
have you tried to run hdparm 3 times in a row? without that, or heavy disk usage before, the buffers aren't full enough and don't report the right speed (as far as i know)

can you try running bonnie++ and paste the output?
you can get it converted into readable html by pasting the CSV output (last line of bonnie++ output) into a text file and then run

bon_csv2html < your_textfile > your_html_file

are you using AHCI with NCQ?

I did run hdparm 3 times in a row.
I have 6 drives in my server and all are set up a bit differently. 

[LIST]

[*]I have 2 WD Raptors (WD740GD) running on 2 SATA ports on the motherboard.
[*]I have an Areca 1220 SATA controller in a PCI express x8 slot. I have 4 Samsung HD103UJ drives here. Two are in a RAID-0 array and the other two are passthrough drives (each set with different cache options).
[*]I have a LSI MegaRAID 320-2E SCSI controller also in a PCI express slot. I have 4 Seagate 15k rpm Cheetah drives on this controller. 
[/LIST]

Do you not think that this hardware should give better performance than what you listed in the first post in this thread?

I do not have NCQ enabled on all drives because the benchmarks I've seen show that the overhead of NCQ can actually reduce performance in typical desktop usage patterns (and that type of use mostly closely matches what I do.)

Here is my bonnie++ output (but I probably need to rerun it because I do not know which of my 6 drives it defaulted to... probably the Raptor the OS is on.

[HTML]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0//EN" "http://www.w3.org/TR/REC-html40/strict.dtd">
<HTML>
<HEAD><TITLE>Bonnie++ V1.03b Benchmark results</TITLE>
<STYLE type="text/css">
TD.header {text-align: center; backgroundcolor: "#CCFFFF" }
TD.rowheader {text-align: center; backgroundcolor: "#CCCFFF" }
TD.size {text-align: center; backgroundcolor: "#CCCFFF" }
TD.ksec {text-align: center; fontstyle: italic }
</STYLE>
<BODY>
<TABLE ALIGN=center BORDER=3 CELLPADDING=2 CELLSPACING=1>
<TR><TD COLSPAN=2 class="header"></TD>
<TD COLSPAN=6 class="header"><FONT SIZE=+2><B>Sequential Output</B></FONT></TD>
<TD COLSPAN=4 class="header"><FONT SIZE=+2><B>Sequential Input</B></FONT></TD>
<TD COLSPAN=2 ROWSPAN=2 class="header"><FONT SIZE=+2><B>Random<BR>Seeks</B></FONT></TD>
<TD COLSPAN=1 class="header"></TD>
<TD COLSPAN=6 class="header"><FONT SIZE=+2><B>Sequential Create</B></FONT></TD>
<TD COLSPAN=6 class="header"><FONT SIZE=+2><B>Random Create</B></FONT></TD>
</tr>
<TR><TD></TD><TD>Size:Chunk Size</TD><TD COLSPAN=2>Per Char</TD><TD COLSPAN=2>Block</TD><TD COLSPAN=2>Rewrite</TD><TD COLSPAN=2>Per Char</TD><TD COLSPAN=2>Block</TD><TD>Num Files</TD><TD COLSPAN=2>Create</TD><TD COLSPAN=2>Read</TD><TD COLSPAN=2>Delete</TD><TD COLSPAN=2>Create</TD><TD COLSPAN=2>Read</TD><TD COLSPAN=2>Delete</TD></TR><TR><TD COLSPAN=2></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>K/sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD><TD class="ksec"><FONT SIZE=-2>/ sec</FONT></TD><TD class="ksec"><FONT SIZE=-2>% CPU</FONT></TD></TR>
<TR><TD class="rowheader"><FONT SIZE=+1><B>MyHardySrvr</B></FONT></TD><TD class="size">12G</TD><TD>12292</TD><TD>28</TD><TD>13040</TD><TD>6</TD><TD>9985</TD><TD>3</TD><TD>34330</TD><TD>74</TD><TD>63192</TD><TD>8</TD><TD>540.2</TD><TD>1</TD><TD>16</TD><TD>+++++</TD><TD>+++</TD><TD>+++++</TD><TD>+++</TD><TD>+++++</TD><TD>+++</TD><TD>+++++</TD><TD>+++</TD><TD>+++++</TD><TD>+++</TD><TD>+++++</TD><TD>+++</TD></TR>
</TABLE>
</BODY>
</HTML>[/HTML]

(I'll fix this formatting once I figure out the best way to post html here.)

---

### Post by MountainX on 2008-08-06
> **fjgaude said:**
> Without knowing the CPU and memory speed and the drive sequential read, it's hard to say what your thruput should be. I do know that the best of the mainboards working off the PCI-E bus can show over 300MB/sec on hdparm tests.

Here's mine: With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz) 2/26/08, CPU fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v, 4X raid5 (each drive 70MB/sec thruput):

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec

```

Your low cached reads mean that CPU/memory is relatively slow, and likely can't handle the raid5 XORing and such quickly.

Interesting feedback.
Here's my desktop system:
Asus A8N5X, Athlon 64X2 3800+, 4GB CORSAIR XMS DDR500 RAM, GeForce 8600GT 256MB GDDR3 PCIe x16 SLI, WD1500ADFD 150GB 10000 RPM Raptor HDD. No RAID (sw or hw).

And here's hdparm output for it:
/dev/mapper/sdX_crypt:
 Timing cached reads:   1488 MB in  2.00 seconds = 744.27 MB/sec
 Timing buffered disk reads:  172 MB in  3.01 seconds =  57.23 MB/sec

That seems well below what would be expected for that hardware doesn't it? Could it be the dm-crypt+LUKS?

It is also interesting that my Intel Server with dual Xeon CPUs and 6GB RAM and fairly high end hardware RAID controllers doesn't perform any better. (This system isn't doing any software RAID.)

---

### Post by MountainX on 2008-08-06
I just ran the Windows version of hdparm on an older server running Windows 2003. This is a much slower hardware platform than my Ubuntu server. It runs a similar RAID controller, though: an Areca 1120 with WD RE drives (7k rpm).

Here are the hdparm results. Notice the buffered disk read performance is better than any of my Ubuntu boxes even though this is a older/slower server.

```
C:\Documents and Settings\Administrator>hdparm -tT hdb

hdb:
 Timing cached reads:   1184 MB in  2.02 seconds = 587.42 MB/sec
 Timing buffered disk reads:  1200 MB in  3.02 seconds = 397.93 MB/sec

C:\Documents and Settings\Administrator>hdparm -tT hdb

hdb:
 Timing cached reads:   1196 MB in  2.02 seconds = 593.37 MB/sec
 Timing buffered disk reads:  1216 MB in  3.02 seconds = 403.24 MB/sec

C:\Documents and Settings\Administrator>hdparm -tT hda

hda:
 Timing cached reads:   1182 MB in  2.02 seconds = 586.43 MB/sec
 Timing buffered disk reads:  1184 MB in  3.02 seconds = 392.63 MB/sec

C:\Documents and Settings\Administrator>hdparm -tT hda

hda:
 Timing cached reads:   1192 MB in  2.02 seconds = 591.39 MB/sec
 Timing buffered disk reads:  1162 MB in  3.02 seconds = 385.33 MB/sec
```

I had already run these tests several times before capturing this output.

---

### Post by fjgaude on 2008-08-06
Well, MountainX, it's all a matter of performance... my memory and CPU is well over twice as fast as yours, and I have four 70MB/sec drives in raid5. Such raid should be three times one drive, which it is.

I've noticed over the last two or so years that Intel CPUs are much quicker than AMDs. The CPU I have the 42nm type, which is so good. I've been an AMD user since 1989 but no more.

Your Raptor is doing about what I have seen with them, going up to about 65MB/sec on hdparm. I have four of them, dated 2003 for two of them, 2004, 2005. The only one that is 75MB/sec is the 2005. I'm sure the very latest will go to about 115. Just not enough considering the price.

---

### Post by MountainX on 2008-08-06
> **fjgaude said:**
> Well, MountainX, it's all a matter of performance... my memory and CPU is well over twice as fast as yours, and I have four 70MB/sec drives in raid5. Such raid should be three times one drive, which it is.


Thanks for the feedback! So my desktop system performs about as you would expect. That's good to know.

But what about my server. I have a RAID-5 array with 4 Seagate Cheetah 15k rpm drives on an LSI MegaRAID 320-2E card in a system with dual Xeons and 6 GB of RAM. I'm getting results like this, which look terrible for that hardware:

```
/dev/mapper/sdX_crypt:
 Timing cached reads:   1378 MB in  2.00 seconds = 688.89 MB/sec
 Timing buffered disk reads:  166 MB in  3.01 seconds =  55.12 MB/sec

/dev/mapper/sdX_crypt:
 Timing cached reads:   1368 MB in  2.00 seconds = 683.69 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.37 MB/sec
```

What should I try next?

---

### Post by hastala on 2008-08-06
**@fjgaude:**

You seem to know about performance.
Do you think bonnie++ read 90MB/sec & write 70MB/sec is good enough (see my first attached pic above)?

My system:
- non-OC'd AMD 4850e @ 2,5Ghz DualCore
- Asus M3H-HDMI board
- 4 x Samsung HD642JJ on the onboard SATA, using AHCI, NCQ enabled (think it's an AMD 780G chipset) 

I'm using software raid5 with 64k chunks, dm-crypt with AES 256bit, no LVM on top

Somebody posted a benchmark pic showing 90MB read time on a single one of these disks, so i guess my 90MB read with raid 5 are rather bad?!
[http://dyski.cdrinfo.pl/benchmark/hdtune/hdtune-655-39580-30.png]("http://dyski.cdrinfo.pl/benchmark/hdtune/hdtune-655-39580-30.png")

```
/dev/md0:
Timing cached reads: 1494 MB in 2.00 seconds = 746.93 MB/sec
Timing buffered disk reads: 630 MB in 3.01 seconds = 209.49 MB/sec
```


**@fjgaude, MountainX:**

Do you think one can rely on hdparm? Isn't bonnie++ used with files twice your memory size a more real-life like test?

**@MountainX:** 

Maybe you don't have DMA enabled on these drives? Just run a hdparm without options and it should tell you.```

```

---

### Post by MountainX on 2008-08-06
> **hastala said:**
> 

Do you think one can rely on hdparm? Isn't bonnie++ used with files twice your memory size a more real-life like test?


First, I would appreciate any tips on how you use bonnie++.

Second, Google showed me this:
[http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO-9.html](http://unthought.net/Software-RAID.HOWTO/Software-RAID.HOWTO-9.html)

"Bonnie++ seems to be more targeted at benchmarking single drives that at RAID"

"Few real-world programs do what bonnie does, and although these I/O numbers are nice to look at, they are not ultimate real-world-appliance performance indicators. Not even close."

---

### Post by fjgaude on 2008-08-06
You might try running **hdparm** on each drive in the raid5 array. You can do that with the drives still assembled as an array... use the individual /dev/sd[nn] names.

hdparm is very good with testing the speed, thruput of CPU combined with memory. It's good for relative sequential reads on drives. Always run it three times and use the last reading, making sure there is no other activities going on in the background.

**bonnie** is good too, but I see no need to use it for what uses I have for speed tests.

Do so reading on all this and become your own expert. <smile>

---

