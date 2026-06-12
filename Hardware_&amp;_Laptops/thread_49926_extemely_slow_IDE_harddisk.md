---
title: "extemely slow IDE harddisk"
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by glandula on 2005-07-18
ive got ubuntu set up on a 80 gig sata. in addtition i ahve a 160 gig sata where is tore movies etc. i also have a 120 gig IDE which i use for backup. the problem is that the IDE is soooooo slow in ubuntu, it takes an hour to backup my home dir, and it eats all my cpu power as well. i dont thinkt heres anything wrong with the IDE cos i had ubuntu installed on it before and it was fine, its just cpying to and from the IDE from my satas that are so slow ( sata to/from sata  works fine)

are there any ways to speed it up ? ive played with the dma stuff based on the dvd/cd dma guide but it has made no difference

any help ?

---

### Post by amohanty on 2005-07-18
By any chance is dma disabled on it.?

Try:
>> hdparm /dev/hdxxxx

where hdxxx is the IDE HDD.

If so search the forums, I think there is an extended thread telling you how to turn DMA on for a device.

HTH
AM

---

### Post by glandula on 2005-07-18
[QUOTE=][/QUOTE]
 no luck anywhere it seems. i wonder if i need via drivers, like the hyperion ones for windows?

---

### Post by amohanty on 2005-07-18
What did hdparm return?

---

### Post by mrcbrown on 2005-07-18
[QUOTE=glandula]no luck anywhere it seems. i wonder if i need via drivers, like the hyperion ones for windows?[/QUOTE]
 I have a VIA KT800 board, had no need for any speciality drivers, do the above command "hdparm" and paste the return values - here's an example on how to test the drive:

```
cbrown@bigboy:~$ sudo hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1128 MB in  2.00 seconds = 563.24 MB/sec
 Timing buffered disk reads:  180 MB in  3.02 seconds =  59.63 MB/sec

```

Leaving off the -tT should give you the drive's settings as-is:

```
cbrown@bigboy:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 203928109056, start = 0

```

---

### Post by glandula on 2005-07-19
/dev/hdb:
 Timing cached reads:   1756 MB in  2.00 seconds = 876.82 MB/sec
 Timing buffered disk reads:   14 MB in  3.11 seconds =   4.51 MB/sec
------
/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 120034123776, start = 0
--------

---

### Post by Lord Illidan on 2005-07-19
Your dma is turned off then..

/dev/hdb:
multcount = 0 (off)
IO_support = 0 (default 16-bit)
unmaskirq = 0 (off)
using_dma = 0 (off) ---Lookie here!!
keepsettings = 0 (off)
readonly = 0 (off)
readahead = 256 (on)
geometry = 65535/16/63, sectors = 120034123776, start = 0

Check a bit about hdparm on google and you will see how to enable dma, it will make your drive a lot faster..

---

### Post by luca_linux on 2005-07-19
Try:
```
sudo hdparm -m16 -W1 -d1 -c1 -u1 /dev/hdb
```
Now test the speed:
```
sudo hdparm -Tt /dev/hdb
```

Just add the following int /etc/hdparm.conf to save your hdparm configuration forever:
```

command_line {
       hdparm -q -m16 -q -W1 -q -d1 -q -c1 -q -u1 /dev/hdb
}

```
Enjoy.

---

### Post by glandula on 2005-07-19
[QUOTE=][/QUOTE]
 luca_linux., i tried what u suggested:
~$ sudo hdparm -m16 -W1 -d1 -c1 -u1 /dev/hdb
and it says
/dev/hdb:
 setting 32-bit IO_support flag to 1
 setting multcount to 16
 setting unmaskirq to 1 (on)
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 setting drive write-caching to 1 (on)
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
--
as far as i can see dma is still off?
anyway the speed test:
/dev/hdb:
 Timing cached reads:   1592 MB in  2.00 seconds = 794.93 MB/sec
 Timing buffered disk reads:   26 MB in  3.17 seconds =   8.21 MB/sec
--
after adding to hdparm.conf:
command_line {
       hdparm -q -m16 -q -W1 -q -d1 -q -c1 -q -u1 /dev/hdb
}

i rebooted and did the speed test:
/dev/hdb:
 Timing cached reads:   1608 MB in  2.00 seconds = 802.12 MB/sec
 Timing buffered disk reads:   14 MB in  3.13 seconds =   4.47 MB/sec

did sudo hdparm -m16 -W1 -d1 -c1 -u1 /dev/hdb again and i got:
/dev/hdb:
 Timing cached reads:   1644 MB in  2.00 seconds = 820.48 MB/sec
 Timing buffered disk reads:   26 MB in  3.18 seconds =   8.17 MB/sec



--
the timing buffered disk read speeds have doubled when doing "sudo hdparm -m16 -W1 -d1 -c1 -u1 /dev/hdb"
 but are still really slow arent they?

btw should these settings be for the physical harddisk hdb,  or the partitions, hdb1 and hdb2 ?

---

### Post by luca_linux on 2005-07-19
It sounds like your chipset module is not loaded: try "lsmod" and post the result.

---

### Post by glandula on 2005-07-19
[QUOTE=][/QUOTE]
 thanks for help. here are the results:
$ lsmod
Module                  Size  Used by
isofs                  33720  0
udf                    77060  0
ip_queue               11032  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
ipt_limit               2688  8
iptable_mangle          2944  0
ipt_LOG                 6656  8
ipt_MASQUERADE          3584  0
iptable_nat            24648  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              6528  1
ip_conntrack_irc       71856  0
ip_conntrack_ftp       72624  0
ipt_state               2048  6
ip_conntrack           43668  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          3840  1
ip_tables              17408  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
fglrx                 229568  7
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
i2c_viapro              7436  0
i2c_core               21264  1 i2c_viapro
af_packet              20744  2
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd
via82cxxx              12956  1
8139cp                 19200  0
8139too                24320  0
mii                     4736  2 8139cp,8139too
ohci1394               31876  0
emu10k1_gp              3840  0
gameport                4608  1 emu10k1_gp
snd_emu10k1            81668  2
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9824  3 snd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
via_agp                 9216  1
agpgart                31784  2 via_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12928  1
fat                    37792  1 vfat
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
sbp2                   22408  0
ieee1394              100408  2 ohci1394,sbp2
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_generic             1664  0
ide_disk               18176  3
ide_cd                 38532  0
ide_core              118988  4 via82cxxx,ide_generic,ide_disk,ide_cd
ext3                  120968  3
jbd                    54168  1 ext3
sr_mod                 16036  0
cdrom                  36508  2 ide_cd,sr_mod
sd_mod                 16784  5
sata_via                8196  6
libata                 44548  1 sata_via
scsi_mod              119936  4 sbp2,sr_mod,sd_mod,libata
unix                   26164  770
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

---

### Post by luca_linux on 2005-07-19
Have a look at here: [http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)

---

### Post by glandula on 2005-07-19
[QUOTE=][/QUOTE]
 thanks again. i already studied that thread before, but i did now try to add amd74xx and via82cxxx to /etc/modules in addition to 
command_line {
       hdparm -q -m16 -q -W1 -q -d1 -q -c1 -q -u1 /dev/hdb
}
in hdparm.conf

and the results....

/dev/hdb:
 Timing cached reads:   1596 MB in  2.00 seconds = 797.32 MB/sec
 Timing buffered disk reads:  140 MB in  3.03 seconds =  46.27 MB/sec
 :DD

thank you again :)
man theres a lot of readong to be done to make everything work on linux, but its worth it

---

### Post by glandula on 2005-07-19
[QUOTE=][/QUOTE]
 bah, i just noticed that my dvd-rw drive isnt dma. cd burner is though, and all harddisks

---

### Post by Ethan on 2005-07-19
I've got a similar problem right now and I just can't find a solution:

**hdparm -Tt /dev/hd **

/dev/hda:
 Timing cached reads:   1464 MB in  2.00 seconds = 731.75 MB/sec
 Timing buffered disk reads:   52 MB in  3.00 seconds =  **17.31 MB/sec**

Although applications start/run fairly, the HD is performing way below what it's capable of, and below the 50-70MB/sec numbers I see around here:

**hdparm -i /dev/hda**

/dev/hda:

 Model=WDC WD800JB-00ETA0, FwRev=77.07W77, SerialNo=WD-WMAHL1368725
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode


**System**

AthlonXP 2800+
Asus A7N8X Deluxe (Nforce2)

HDA: WD SE Caviar; 80GB; 7200 RPM; 8MB cache (WD800JB-00ETA0)
HDC: Aopen DUW1608 16x DVD+-RW (week old)
Both have a good 80-pins cable

**/etc/modules**

amd74xx
ide-core
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse

**lsmod | grep -i amd**

amd74xx                14044  1
ide_core              129548  5 ide_cd,via82cxxx,ide_generic,ide_disk,amd74xx


And even though I can/could already set DMA=on using hdparm before adding that amd74xx line.. performance is still poor:

hdparm  -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
sh-3.00#  hdparm  -t /dev/hda

/dev/hda:
 Timing buffered disk reads:   34 MB in  3.13 seconds =  10.87 MB/sec



Any more suggestions for this fairly new Linux user?   :neutral:

---

### Post by glandula on 2005-07-19
[QUOTE=][/QUOTE]
 i really wish this was simpler. im no professor, i just want to play my dvds and stuff

---

### Post by glandula on 2005-07-19
allright, after excessive googling, trying multiple configurations ive managed to get everything to work and dma to be enable at boot on all harddisks, my cd drive and my dvd drive.

in case it could be useful to others, here are my configs. keep in mind im a total newbie and that it may not work for others:

/etc/modules:
i added via82cxxx above ide-cd. if your chipset is not via it will probably be something else
--------------
/etc/hdparm.conf:
#dma 120 gig ide (this makes my IDE hdd use dma):
command_line {
       hdparm -q -m16 -q -W1 -q -d1 -q -c1 -q -u1 /dev/hdb
}
#dma on 80 gig ide (this makes my other IDE hdd use dma):
command_line {
       hdparm -q -m16 -q -W1 -q -d1 -q -c1 -q -u1 /dev/hda
}
# this seems neccesary for dma on cd drive:
command_line {
     hdparm -d1 /media/cdrom0
}
#this seems necessary for dma on my dvd drive
command_line {
   hdparm -d1 /media/cdrom1
}
# this also seems neccesary for dma on cd drive:
/media/cdrom0 {
	dma = on		   
}
#this also seems necessary for dma on my dvd drive
/media/cdrom1 {
	dma = on		   
}
#also seems neccesary for dma on cd
command_line {
     hdparm -d1 /dev/hdc
}
#also seems needed for dma on dvd
command_line {
   hdparm -d1 /dev/hdd
}
# dma on cd
/dev/hdc {
	dma = on		   
}
#dma on dvd
/dev/hdd {
	dma = on		   
}
---------------
im not sure all this is necesary but it works on my system.
as far as i can tell /media/cdrom0 = /dev/hdc and, as im no expert, i dont know if u need commands for both, but it only seems to work for me if i do it like this, and in this order. a different order and it doesent seem to work. but ive tried so many orders that i dont remember what works and what doesent anymore. but this setup works thats for sure, on my computer

ok, im still confused but happy and going to bed :D
thanks to the helpers!

---

### Post by Ethan on 2005-07-21
Absolutely no-one with another suggestion to my problem?!?

---

### Post by glandula on 2005-07-21
[QUOTE=][/QUOTE]
 ethan, make a new thread. it appeares to me that its only brand new threads thats being read by the knowledgeable people (i may be wrong but thats my impression)

---

### Post by luca_linux on 2005-07-21
@Ethan: have you tried to set the other flags or just the dma?

---

### Post by Ethan on 2005-07-21
[QUOTE=luca_linux]@Ethan: have you tried to set the other flags or just the dma?[/QUOTE]

I've tried other flags as well.. basically all those that can be found in $tune_your machine How-To's.

I'm still getting around 15MB/sec on the 2800+... and I just tested a 500MHz Athlon and it does easily 42MB/sec.  (has a modern 160GB, 8MB cache HD).

It's very strange..  ](*,)

---

### Post by frodon on 2005-07-31
[QUOTE=Ethan]I've tried other flags as well.. basically all those that can be found in $tune_your machine How-To's.

I'm still getting around 15MB/sec on the 2800+... and I just tested a 500MHz Athlon and it does easily 42MB/sec.  (has a modern 160GB, 8MB cache HD).

It's very strange..  ](*,)[/QUOTE]
I solve this problem adding **amd74xx** in the first line of /etc/modules file. Other hdparm options didn't solve my problem ... try do add this line and reboot

---

### Post by Ethan on 2005-08-07
(sorry for the belated reply, was away for business for a few days)

I've already tried the amd74xx module and it didn't help.

As suggested earlier in this thread, I've made a new thread regarding my specific problem:

[http://www.ubuntuforums.org/showthread.php?t=51264](http://www.ubuntuforums.org/showthread.php?t=51264)

And since there is still no solution, a friend of me is also trying to find an answer in [another forum](http://www.broadbandreports.com/forum/remark,14038202) 

Short summary of strange events:

Temporarily switched the Western Digital SE Caviar (80GB/7200RPM/8MB cache) for a Hitachi Deskstar (160GB/7200RPM/8MB cache), which had also Ubuntu installed (same version, same kernel, etc)

The install on the Hitachi came from a non-NForce system and didn't have the amd74xx module. However, inserted in the NForce system, the disk immediately returned the following results:

Cached: 927.21 MB/sec
Buffered: 57.87MB/sec

a 400% increase in performance even though we didn't change anything else but the disk! 

(Both disks are dual boot Win2K3/Ubuntu; Ubuntu configs are almost identical as far as we can tell; looking at the modules for example)

So apparently:

- Ubuntu can deal with the NForce board without the amd74xx module
- IDE controller is fine
- cable is fine

Just the disk change mattered?!?

But then again, Win2K3 was already performing perfectly, so the disk is certainly not bad.

So far: no solution, we're still clueless ... any help appreciated!

Other off-site thread started by my friend also contains a lot of information!

---

### Post by luca_linux on 2005-08-07
Ok, first of all, set these flags:
```
hdparm -m16 -W1 -d1 -c1 -u1 /dev/hda
```
Then store the config in /etc/hdparm.conf adding the following line:
```

command_line {
       hdparm -q -m16 -q -W1 -q -d1 -q -c1 -q -u1 /dev/hda
}

```
Now from this configuration, let's make some tests.
1) First of all, try to change "-W1" to "-W0" and see which is better for your hardware by running -Tt.
2) Then try to change "-c1" to "-c3" and see which is better for your hardware by running -Tt.
3) Try to change "-m16" to "-m0" and see which is better for your hardware by running -Tt.

Then let me know.

---

### Post by Ethan on 2005-08-07
Ok:

After 'hdparm -m16 -W1 -d1 -c1 -u1 /dev/hda' and the change to /etc/hdparm.conf, the 'baseline' performance:

hdparm -Tt /dev/hda:

/dev/hda:
 Timing cached reads:   1772 MB in  2.00 seconds = 883.92 MB/sec
 Timing buffered disk reads:   64 MB in  3.01 seconds =  21.25 MB/sec

Well.. at least that is about the highest I've seen so far :)

1) After changing -W1 to W0:

/dev/hda:
 Timing cached reads:   1796 MB in  2.00 seconds = 897.69 MB/sec
 Timing buffered disk reads:   46 MB in  3.05 seconds =  15.08 MB/sec


2) Changing -c1 to -c3 (using -W1 again):

/dev/hda:
 Timing cached reads:   1784 MB in  2.00 seconds = 890.80 MB/sec
 Timing buffered disk reads:   34 MB in  3.07 seconds =  11.09 MB/sec


3) Changing -m16 to -m0 (using -W1 and -c1):

/dev/hda:
 Timing cached reads:   1756 MB in  2.00 seconds = 876.82 MB/sec
 Timing buffered disk reads:   60 MB in  3.00 seconds =  19.97 MB/sec


Generally an improvement over the ~10MB/sec, thank you, .. but still nowhere near the Hitachi drive.. while both drives are in the same class.

---

### Post by luca_linux on 2005-08-07
That's really strange...
1) Try using "-m16" with "-c3" instead of "-c1" and see the performance test.
2) Then also try adding the "--direct" flag and see the performance test.

---

### Post by Ethan on 2005-08-07
**hdparm -m16 -W1 -d1 -c3 -u1 /dev/hda:**

/dev/hda:
 Timing buffered disk reads:   14 MB in  3.09 seconds =   4.53 MB/sec

AUCH!  :???: 

**hdparm -m16 -W1 -d1 -c3 -u1 --direct /dev/hda:**

/dev/hda:
 Timing buffered disk reads:   28 MB in  3.00 seconds =   9.33 MB/sec

**hdparm -m16 -W1 -d1 -c1 -u1 --direct /dev/hda:**

/dev/hda:
 Timing buffered disk reads:   36 MB in  3.15 seconds =  11.44 MB/sec


It's getting stranger and stranger  :|

---

