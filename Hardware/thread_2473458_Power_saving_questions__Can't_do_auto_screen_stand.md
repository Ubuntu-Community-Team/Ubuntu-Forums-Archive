---
title: "Power saving questions:  Can't do auto screen standby, auto HDD off, help!"
date: 2022-04-05
forum: Hardware
---

### Post by mikeymikec on 2022-04-05
Spec:

Kubuntu 20.04 LTS
i5-4690K
ASUS Z97 PRO GAMER (latest BIOS)
12GB RAM
Samsung 128GB 850 PRO (Kubuntu boot drive)
Samsung 256GB 840 PRO (Win10 boot drive)
Western Digital Blue 4TB WD40EZRZ-22GXCB0
AMD R9 380X 4GB, amdgpu driver
Iiyama XU2292HS 22" wide-screen monitor, connected via HDMI cable

System (S3) sleep mode works (enabled via Settings > Power Management > Activity Settings > Define special behaviour > Always sleep after 15 minutes)

I tried getting auto screen standby/off to work through 'use separate settings' > 'screen energy saving', but that makes the screen go black yet pointer still visible, then the pointer disappears (screen power light still on), then about ten seconds later the screen comes on again automatically.  Ideally I'd like to get the screen to go to sleep after say 5-10 minutes of idle time.

I'd also like the hard drive to automatically go into standby.  I installed the gnome disks utility and tried changing the standby timeout setting for the drive, but it appears to have no effect.

The screen timeout setting doesn't appear to produce any entries in the dmesg output.  At the time that I was playing around with the HDD standby setting, these entries were produced:

```
[ 8342.092425] ata5: link is slow to respond, please be patient (ready=0)
[ 8343.360409] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 8343.384249] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT4._GTF.DSSP], AE_NOT_FOUND (20210331/psargs-330)

[ 8343.384259] No Local Variables are initialized for Method [_GTF]

[ 8343.384260] No Arguments are initialized for method [_GTF]

[ 8343.384262] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20210331/psparse-529)
[ 8343.384901] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT4._GTF.DSSP], AE_NOT_FOUND (20210331/psargs-330)

[ 8343.384910] No Local Variables are initialized for Method [_GTF]

[ 8343.384911] No Arguments are initialized for method [_GTF]

[ 8343.384913] ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT4._GTF due to previous error (AE_NOT_FOUND) (20210331/psparse-529)
[ 8343.385050] ata5.00: configured for UDMA/133

```

ata5 appears to be the HDD.

```
mike@mike-pc:~$ dmesg | grep ata5
[    0.707132] ata5: SATA max UDMA/133 abar m2048@0xf7f35000 port 0xf7f35300 irq 30
[    1.023999] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.024667] ata5.00: ATA-10: WDC WD40EZRZ-22GXCB0, 80.00A80, max UDMA/133
[    1.024669] ata5.00: 7814037168 sectors, multi 16: LBA48 NCQ (depth 32), AA
[    1.025397] ata5.00: configured for UDMA/133
[ 4410.322564] ata5: link is slow to respond, please be patient (ready=0)
[ 4410.926606] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 4410.951061] ata5.00: configured for UDMA/133
[ 8342.092425] ata5: link is slow to respond, please be patient (ready=0)
[ 8343.360409] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[ 8343.385050] ata5.00: configured for UDMA/133

```

I've found one further thing - if I go into the gnome disks utility, select the HDD, go into the menu and select 'standby now', it asks for authentication first then successfully puts the drive to sleep.  Could this be a question of permissions to get the auto feature to work then?

---

### Post by TheFu on 2022-04-05
Western Digital spin down can be supported for SATA using **hdparm -B xyz**.  I think.  From the manpage:
```
       -B     Get/set Advanced Power Management feature, if the drive supports
              it.  A  low  value  means aggressive power management and a high
              value means better performance.  Possible  settings  range  from
              values  1  through  127 (which permit spin-down), and values 128
              through 254 (which do not permit spin-down).  The highest degree
              of  power  management  is  attained with a setting of 1, and the
              highest I/O performance with a setting of 254.  A value  of  255
              tells  hdparm to disable Advanced Power Management altogether on
              the drive (not all drives support disabling it, but most do).
```

I always go out of my way to prevent all my spinning disks from spinning down to limit wear.
I don't know if USB connected HDDs accept hdparm commands. The SATA/eSATA command set has many more features that simple USB-storage.

---

### Post by mikeymikec on 2022-04-06
```
mike@mike-pc:~$ sudo hdparm -B /dev/sdc

/dev/sdc:
 APM_level      = not supported
```

Also:

```
mike@mike-pc:~$ sudo hdparm -S 5 /dev/sdc

/dev/sdc:
 setting standby to 5 (25 seconds)
```
Does nothing (note - I'm only using absurdly short timers for testing)

What did work (only in terms of immediate spindown):
```
mike@mike-pc:~$ sudo hdparm -y /dev/sdc

/dev/sdc:
 issuing standby command
mike@mike-pc:~$ sudo hdparm -C /dev/sdc

/dev/sdc:
 drive state is:  standby
mike@mike-pc:~$ sudo hdparm -C /dev/sdc
```

Then I accessed the drive, causing it to spin up, ran the query again:
```
/dev/sdc:
 drive state is:  active/idle
```

---

### Post by TheFu on 2022-04-06
```
$ sudo hdparm -B /dev/sdc

/dev/sdc:
 APM_level      = _**[COLOR="#FF0000"]not supported[/COLOR]**_
```

What is the connection mode?  USB?

BTW, the '-B' requires a number.  I quoted the manpage.

```
$ sudo hdparm -B 128  /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level      = 128
```

I thought my sda was a WD Blue - but it was replaced a few years ago for a Hitachi HDP725050GLA360. I think that's a cheap desktop equiv HDD.

---

### Post by mikeymikec on 2022-04-06
SATA.  Oops, missed that bit about hdparm!  Trying again:

```
mike@mike-pc:~$ sudo hdparm -B 128 /dev/sdc

/dev/sdc:
 setting Advanced Power Management level to 0x80 (128)
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 40 80 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 APM_level      = not supported
```

---

### Post by TheFu on 2022-04-06
[https://bbs.archlinux.org/viewtopic.php?id=213109](https://bbs.archlinux.org/viewtopic.php?id=213109) has some people saying that automatic spin down isn't supported on WD-Blue. I don't know if that is really true.  Do the WD specs say anything about it?

---

### Post by #&amp;thj^% on 2022-04-06
Just to help, my blue:
```
sudo hdparm -B /dev/sdc

/dev/sdc:
 APM_level	= 128


me on Wed Apr 06 at 05:13 PM in ~ branch: (HEAD) 
>> sudo hdparm -B /dev/sda

/dev/sda:
 APM_level	= 128


me on Wed Apr 06 at 05:13 PM in ~ branch: (HEAD) 
>> sudo hdparm -B 128 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


```
dev/sdc is the blue  /dev/sdc type: USB vendor: Western Digital, and sda is "model: PC S N730 SDBQNTY-256 "SSD
I have also seen folks talk their WD Blues won't spin down, I never followed their posts though.
I'd be curious if some other flags would help:
Examples:
```
hdparm - get/set hard disk parameters - version v9.63, by Mark Lord.

clue=11
Usage:  hdparm  [options] [device ...]

Options:
 -a   Get/set fs readahead
 -A   Get/set the drive look-ahead flag (0/1)
 -b   Get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   Set Advanced Power Management setting (1-255)
 -c   Get/set IDE 32-bit IO setting
 -C   Check drive power mode status
 -d   Get/set using_dma flag
 -D   Enable/disable drive defect management
 -E   Set cd/dvd drive speed
 -f   Flush buffer cache for device on exit
 -F   Flush drive write cache
 -g   Display drive geometry
 -h   Display terse usage information
 -H   Read temperature from drive (Hitachi only)
 -i   Display drive identification
 -I   Detailed/current information directly from drive
 -J   Get/set Western DIgital "Idle3" timeout for a WDC "Green" drive (DANGEROUS)
 -k   Get/set keep_settings_over_reset flag (0/1)
 -K   Set drive keep_features_over_reset flag (0/1)
 -L   Set drive doorlock (0/1) (removable harddisks only)
 -m   Get/set multiple sector count
 -M   Get/set acoustic management (0-254, 128: quiet, 254: fast)
 -n   Get/set ignore-write-errors flag (0/1)
 -N   Get/set max visible number of sectors (HPA) (VERY DANGEROUS)
 -p   Set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   Set drive prefetch count
 -q   Change next setting quietly
 -Q   Get/set DMA queue_depth (if supported)
 -r   Get/set device readonly flag (DANGEROUS to set)
 -R   Get/set device write-read-verify flag
 -s   Set power-up in standby flag (0/1) (DANGEROUS)
 -S   Set standby (spindown) timeout
 -t   Perform device read timings
 -T   Perform cache read timings
 -u   Get/set unmaskirq flag (0/1)
 -U   Obsolete
 -v   Use defaults; same as -acdgkmur for IDE drives
 -V   Display program version and exit immediately
 -w   Perform device reset (DANGEROUS)
 -W   Get/set drive write-caching flag (0/1)
 -x   Obsolete
 -X   Set IDE xfer mode (DANGEROUS)
 -y   Put drive in standby mode
 -Y   Put drive to sleep
 -z   Re-read partition table
 -Z   Disable Seagate auto-powersaving mode
 --dco-freeze      Freeze/lock current device configuration until next power cycle
 --dco-identify    Read/dump device configuration identify data
 --dco-restore     Reset device configuration back to factory defaults
 --dco-setmax      Use DCO to set maximum addressable sectors
 --direct          Use O_DIRECT to bypass page cache for timings
 --drq-hsm-error   Crash system with a "stuck DRQ" error (VERY DANGEROUS)
 --fallocate       Create a file without writing data to disk
 --fibmap          Show device extents (and fragmentation) for a file
 --fwdownload            Download firmware file to drive (EXTREMELY DANGEROUS)
 --fwdownload-mode3      Download firmware using min-size segments (EXTREMELY DANGEROUS)
 --fwdownload-mode3-max  Download firmware using max-size segments (EXTREMELY DANGEROUS)
 --fwdownload-mode7      Download firmware using a single segment (EXTREMELY DANGEROUS)
 --fwdownload-modee      Download firmware using mode E (min-size segments) (EXTREMELY DANGEROUS)
 --fwdownload-modee-max  Download firmware using mode E (max-size segments) (EXTREMELY DANGEROUS)
 --idle-immediate  Idle drive immediately
 --idle-unload     Idle immediately and unload heads
 --Iraw filename   Write raw binary identify data to the specfied file
 --Istdin          Read identify data from stdin as ASCII hex
 --Istdout         Write identify data to stdout as ASCII hex
 --make-bad-sector Deliberately corrupt a sector directly on the media (VERY DANGEROUS)
 --offset          use with -t, to begin timings at given offset (in GiB) from start of drive
 --prefer-ata12    Use 12-byte (instead of 16-byte) SAT commands when possible
 --read-sector     Read and dump (in hex) a sector directly from the media
 --repair-sector   Alias for the --write-sector option (VERY DANGEROUS)
 --sanitize-antifreeze-lock  Block sanitize-freeze-lock command until next power cycle
 --sanitize-block-erase      Start block erase operation
 --sanitize-crypto-scramble  Change the internal encryption keys that used for used data
 --sanitize-freeze-lock      Lock drive's sanitize features until next power cycle
 --sanitize-overwrite  PATTERN  Overwrite the internal media with constant PATTERN
 --sanitize-overwrite-passes COUNT  Number of overwrite passes from 0 to 7, default 0 means 16 passes
 --sanitize-status           Show sanitize status information
 --security-help             Display help for ATA security commands
 --set-sector-size           Change logical sector size of drive
 --trim-sector-ranges        Tell SSD firmware to discard unneeded data sectors: lba:count ..
 --trim-sector-ranges-stdin  Same as above, but reads lba:count pairs from stdin
 --verbose                   Display extra diagnostics from some commands
 --write-sector              Repair/overwrite a (possibly bad) sector directly on the media (VERY DANGEROUS)

```
Like these two:
```
-y   Put drive in standby mode
 -Y   Put drive to sleep
```

---

### Post by mikeymikec on 2022-04-07
> **TheFu said:**
> [https://bbs.archlinux.org/viewtopic.php?id=213109](https://bbs.archlinux.org/viewtopic.php?id=213109) has some people saying that automatic spin down isn't supported on WD-Blue. I don't know if that is really true.  Do the WD specs say anything about it?

They mention standby power usage figures but I haven't seen much else.  I wouldn't know for certain what to look for though.  I ran hdparm -B against an old WD Black I have and it said 'not supported' as well.

---

### Post by #&amp;thj^% on 2022-04-07
> **mikeymikec said:**
> They mention standby power usage figures but I haven't seen much else.  I wouldn't know for certain what to look for though.  I ran hdparm -B against an old WD Black I have and it said 'not supported' as well.
I missed that sorry and forgive my intrusion, TheFu is very capable, I just wanted to add, 
"Possible settings range from values 1 through 127 (which permit spin-down), and values 128 through 254 (which do not permit spin-down).[...]A value of 255 tells hdparm to disable Advanced Power Management altogether on the drive (not all drives support disabling it, but most do)."
My Black spins down, and my Blue spins down.
Hope something useful results.
```
sudo hdparm -C /dev/sdg 

/dev/sdg:
 drive state is:  standby


```
I also tested:
```
sudo hdparm -B 255 /dev/sdg 

/dev/sdg:
 setting Advanced Power Management level to disabled
 APM_level	= off

```
That is the Blue drive:
```
Drives:
  Local Storage: total: 8.65 TiB used: 767.83 GiB (8.7%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB256HBHQ-000L2
    size: 238.47 GiB
  ID-2: /dev/sda vendor: Seagate model: ST1000LM049-2GH172 size: 931.51 GiB
  ID-3: /dev/sdb type: USB vendor: Western Digital
    model: PC S N730 SDBQNTY-256 size: 238.47 GiB
  ID-4: /dev/sdc type: USB vendor: Western Digital
    model: WD My Passport 2627 size: 4.55 TiB
  ID-5: /dev/sdd type: USB vendor: Western Digital
    model: WD My Passport 25E2 size: 1.82 TiB
  ID-6:**_ /dev/sdg type: USB vendor: Western Digital model: WD10EZEX-60WN4A0_**
    size: 931.51 GiB

```

---

### Post by mikeymikec on 2022-04-08
I have the feeling that the WD Blue label isn't indicative of very much at all these days.  When googling the specs of my model drive, I'd get to the WD Blue page, my model would be mentioned there, click on 'datasheet', then my model isn't there.  I eventually found it in another WD Blue data sheet.

I tried hdparm -B 255 on my WD Blue and it still says not supported, so I think it's the blanket response to any value sent to it.

Btw, when I said 'my WD Black', it is a much older one, wd1003fzex (probably 2010-2011 era IIRC).

I have a spare Seagate Ironwolf NAS SATA drive that I queried and that one does support APM.  I'm considering swapping my internal WD Blue for that one as the SG has a less irritating spinning sound seemingly.

---

### Post by TheFu on 2022-04-08
Before you write off the WD-Blue, perhaps trying values that aren't edge conditions would be smart?  255 is definitely an edge condition and disables all APM.  That sorta defeats the purpose of your goal, right?  Pick 3 values below 128 ... which should, in theory, all enable spin-down.

'not supported' doesn't always mean not-supported ever.  It could mean 'disabled', especially if 255 is the option provided.  The returned values may come directly from the firmware of the HDD. I don't know, but that seems like a fairly limited capability on one of the cheapest model HDDs in their lineup.

---

### Post by #&amp;thj^% on 2022-04-08
@TheFu not sure everything is right though.
Same WD Blue that I issued " -B 255 /dev/sdg " the disk has changed names today IE: "/dev/sdc type: USB vendor: Western Digital model: 
WD10EZEX-60WN4A0
"
And to see if that holds:
```
 sudo hdparm -C /dev/sdc
[sudo] password for me: 

/dev/sdc:
 drive state is:  active/idle


me on Fri Apr 08 at 01:43 PM in ~ branch: (HEAD) 
>> sudo hdparm -y /dev/sdc

/dev/sdc:
 issuing standby command


me on Fri Apr 08 at 01:44 PM in ~ branch: (HEAD) 
>> sudo hdparm -C /dev/sdc

/dev/sdc:
 drive state is:  standby


```
I tried looking up the OP's disk drive and it dose support hdparm, so something is fishy here.

####One more time:
```
sudo hdparm -B 255 /dev/sdc
[sudo] password for me: 

/dev/sdc:
 setting Advanced Power Management level to disabled
 APM_level	= off

sudo hdparm -y /dev/sdc

/dev/sdc:
 issuing standby command

sudo hdparm -C /dev/sdc

/dev/sdc:
 drive state is:  standby



```
```
sudo hdparm -B 125 /dev/sdc

/dev/sdc:
 setting Advanced Power Management level to 0x7d (125)
 APM_level	= 125

```

---

### Post by TheFu on 2022-04-08
Poorly supported APM from the disk controller is my next guess.  I'm seeing that with Jmicron and Maxell controllers here. Sometimes, SMART data needs a controller specified to work with those.

---

### Post by mikeymikec on 2022-04-10
@1fallen - how did you find out about my drive and hdparm?  I'm curious about what I ought to have looked for.  Also, as I previously mentioned I can manually spin the drive down using -y, just not with any kind of sensible/automatic basis.

@TheFu - I've tried four numbers below 128, all say not supported.

After your last post, I also tried running sudo hdparm -B /dev/sda and sdb (Samsung 840 PRO and 850 PRO), both said not supported.  I'm not sure whether that's fishy or not!  On one hand, a decent SSD not supporting APM functions, but on the other hand, is it really useful for an SSD to go into standby...

I had a look around the BIOS and found a setting in pch settings labelled 'aggressive lpm management'.  I was nervous about enabling it straight away in case it borks Linux, and also it seems to me that this is a somewhat more extreme feature than I'm looking for.

My board doesn't have any non-Intel storage controllers, general fyi.

---

### Post by TheFu on 2022-04-10
SSD power use is much less than a spinning disk. I wouldn't know what spinning down any SSD would actually mean. It doesn't make sense.

Yesterday, I tested 2 WD-Blue HDDs. Both in a USB2 dock and 1 of those inside an eSATA-PM disk array. None of those connections worked for any setting except 255 (disable APM).  I pulled one of the disks from use over a year ago due to too many bad sectors, so it might have other issues too. I don't have any WD-Blue HDDs connected to internal SATA ports. Sorry.

Does seem there is much else I can help/confuse here. ;)

---

### Post by Yellow Pasque on 2022-04-10
Just a note: Make sure your hard disk is powered using a native SATA power cable and not a Molex->SATA adapter. The adapter allows the drive to function, but it doesn't provide a 3.3V line for the drive, and IIRC, many of them use the 3.3V line for power management and other quirky features.

---

### Post by #&amp;thj^% on 2022-04-10
> **mikeymikec said:**
> @1fallen - how did you find out about my drive and hdparm?  I'm curious about what I ought to have looked for.  Also, as I previously mentioned I can manually spin the drive down using -y, just not with any kind of sensible/automatic basis.

.

I thought you had already looked at it, or I would have posted it: [https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/internal-drives/wd-blue-hdd/data-sheet-wd-blue-pc-hard-drives-2879-771436.pdf](https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/product/internal-drives/wd-blue-hdd/data-sheet-wd-blue-pc-hard-drives-2879-771436.pdf)
You also had a long string of dec's that sent my spidy senses off the charts, I'm still casually researching those. (so i won't mention any possible hardware fails)
Yes this one in post #5
```
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 40 80 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```
I'll just add it here though:
```
Power Management 6
Average power requirements (W)
12VDC ±10% (A, peak)
Read/Write
Idle
Standby and Sleep
1.75
4.8
3.1
0.6
1.75
5.3
3.4
0.4
1.75
4.5
2.9
0.
```

---

### Post by #&amp;thj^% on 2022-04-10
> **Yellow Pasque said:**
> Just a note: Make sure your hard disk is powered using a native SATA power cable and not a Molex->SATA adapter. The adapter allows the drive to function, but it doesn't provide a 3.3V line for the drive, and IIRC, many of them use the 3.3V line for power management and other quirky features.
You are on to something here:
That drive I mention in all my post's here is connected by a [Thermaltake BlackX dock]("https://www.amazon.com/Thermaltake-Drives-Docking-Station-ST0014U/dp/B002MUYOLW").

---

### Post by mikeymikec on 2022-04-11
My drives are natively connected except for the ones I tried out externally (WD Black, Seagate Ironwolf NAS).  My PSU is quite a recent one from Seasonic as well, so I would be surprised if there was anything substandard about its power connectors.

@1fallen - Ok yup we had looked at the same info.  I presumed that meant it supported APM functions, but for all I know about Linux / hdparm (not much) it doesn't tell me whether I should expect it to work on my setup :)

---

### Post by #&amp;thj^% on 2022-04-11
> **mikeymikec said:**
>   I presumed that meant it supported APM functions, but for all I know about Linux / hdparm (not much) it doesn't tell me whether I should expect it to work on my setup :)

You presumed correct, I have a few ideas to throw at ya.
You've already shown it works on the blue drive.
You can add this to systemd as a service IE: 
EDIT>>>"**/etc/systemd/system/hdparm.service"**
```

[Unit]
Description=hdparm sleep

[Service]
Type=oneshot
ExecStart=/usr/bin/hdparm -q -S 120 -y /dev/sdb

[Install]
WantedBy=multi-user.target
```
Change the values to meet your need
and enable it with:
```
sudo systemctl enable hdparm.service
```
if you need/want to check the drive/s condition without waking it use:
```
sudo smartctl -i -n standby /dev/sdd

```
again use your needed value and drive "/sdx"

we also have another unofficial utility is provided by the idle3-tools package. A raw idle3 value is passed as a parameter of the idle3ctl command. The correspondence between this value and the timeout in seconds is provided in the bottom table within idle3ctl. The following sets the timer to 30 seconds:
```
# idle3ctl -s 129 /dev/sdd
```

**Note:**
[list]
    [*]A full power cycle is required for any change to take effect regardless of which program above is used. It means the drive needs to be powered OFF and then ON, a simple reboot does not suffice.
    [*]Some Western Digital Green drives (all of "my" My Books are green drives) are also known to have a different interpretation of hparm's standby timeout parameter, -S 1 resulting in a 10 min timer rather than 5 sec.
    [*]The power consumption of a Green drive is typically around 5.3W during read/write, 4.7W in idle mode and 0.7W in standby mode.[/list]
Here is some of what I have tested and used:

```
sudo hdparm -Y /dev/sdd

/dev/sdd:
 issuing sleep command
SG_IO: bad/missing sense data, sb[]:  f0 00 01 00 50 40 00 0a 80 00 00 00 00 1d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


```
```
me on Mon Apr 11 at 09:48 AM in ~ branch: (HEAD) 
>> sudo smartctl -i -n standby /dev/sdd
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-5.16.18-hardened1-1-hardened] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20SDZW-11JJ8S1
Serial Number:    WD-WX71AB87D9K0
LU WWN Device Id: 5 0014ee 2bb629c4d
Firmware Version: 01.01A01
User Capacity:    2,000,365,379,584 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
TRIM Command:     Available, deterministic
Device is:        Not in smartctl database 7.3/5319
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Apr 11 09:48:41 2022 MDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
Power mode is:    ACTIVE or IDLE


```

```
me on Mon Apr 11 at 09:49 AM in ~ branch: (HEAD) 
>> sudo hdparm -C /dev/sdd

/dev/sdd:
SG_IO: bad/missing sense data, sb[]:  f0 00 01 00 50 40 ff 0a 80 00 00 00 00 1d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 drive state is:  unknown

```

```
sudo hdparm -I /dev/sd{b,c,d} | grep level
	Advanced power management level: 128
	Advanced power management level: 128

```
After my timer went on:
```
sudo smartctl -i -n standby /dev/sdd
[sudo] password for me: 
smartctl 7.3 2022-02-28 r5338 [x86_64-linux-5.16.18-hardened1-1-hardened] (local build)
Copyright (C) 2002-22, Bruce Allen, Christian Franke, www.smartmontools.org

Device is in STANDBY mode, exit(2)


```

---

### Post by mikeymikec on 2022-04-12
@1fallen

I followed your instructions, power cycled, waited 10 minutes, drive was still spinning.  I ran: 
```

mike@mike-pc:~$ sudo journalctl -u hdparm.service
-- Logs begin at Mon 2021-08-30 20:26:52 BST, end at Tue 2022-04-12 14:00:26 BST. --
Apr 12 13:45:52 mike-pc systemd[1]: Starting hdparm sleep...
Apr 12 13:45:52 mike-pc systemd[967]: hdparm.service: Failed to execute command: No such file or directory
Apr 12 13:45:52 mike-pc systemd[967]: hdparm.service: Failed at step EXEC spawning /usr/bin/hdparm: No such file or directory
Apr 12 13:45:52 mike-pc systemd[1]: hdparm.service: Main process exited, code=exited, status=203/EXEC
Apr 12 13:45:52 mike-pc systemd[1]: hdparm.service: Failed with result 'exit-code'.
Apr 12 13:45:52 mike-pc systemd[1]: Failed to start hdparm sleep.

```

It looks like hdparm isn't in /usr/bin but in /usr/sbin.  I'll try updating the service file with that.

- edit - 

success!

```
-- Reboot --
Apr 12 14:06:45 mike-pc systemd[1]: Starting hdparm sleep...
Apr 12 14:06:45 mike-pc hdparm[972]:  issuing standby command
Apr 12 14:06:45 mike-pc systemd[1]: hdparm.service: Succeeded.
Apr 12 14:06:45 mike-pc systemd[1]: Finished hdparm sleep.
mike@mike-pc:~$ sudo smartctl -i -n standby /dev/sdc
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.0-39-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

Device is in STANDBY mode, exit(2)
mike@mike-pc:~$ sudo hdparm -C /dev/sdc

/dev/sdc:
 drive state is:  standby

```

Then I gave the drive a nudge by firing up Dolphin, heard the drive spun up then queried it again:
```
mike@mike-pc:~$ sudo hdparm -C /dev/sdc

/dev/sdc:
 drive state is:  active/idle
mike@mike-pc:~$ 
```

The only thing I'm puzzled about at the moment is the current schedule in which my drive auto powers down.  On the successful attempt I didn't wait ten minutes, I queried the drive within a minute or two after boot-up, yet the hdparm -S 120 setting seems to me like it should be on a ten minute timer?

---

### Post by #&amp;thj^% on 2022-04-12
**NOTE: Beware that it will keep your drives awake if the chosen check interval is shorter than the standby timer.**

I had the chance to talk to a very helpful tech-support person, they informed me that the controllers for all blues, greens, and red drives came with different firmware.
I told him that wasn't an answer, he then went to saying that depending on the date purchased, the same Blue drive that you have now would very likely have a different controller
So this makes a challenge of finding the right settings to use, for mine i played with:
```
sudo hdparm -S 250 /dev/sdd
[sudo] password for me: 

/dev/sdd:
 setting standby to 250 (5 hours)
SG_IO: bad/missing sense data, sb[]:  f0 00 01 00 50 40 fa 0a 80 00 00 00 00 1d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

```
On that particular drive (sdd) before that I used -s121 for the management level:
```
 sudo hdparm -I /dev/sd{b,c,d} | grep level
	Advanced power management level: 128
	Advanced power management level: 121

```
BTW this drive is a "My Passport" drive:
```
sudo hdparm -C /dev/sdd

/dev/sdd:
SG_IO: bad/missing sense data, sb[]:  f0 00 01 00 50 40 ff 0a 80 00 fa 00 00 1d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 drive state is:  unknown

```
Of course we all here know this to be a fact, wd blues are desktop drives not rated for 24/7 operation right.
For Drives running 24/7 I stick to the Reds, even Blacks.
So yes I like mine to spin-down as well.
IMPORTANT: Remember to Power cycle the the drive  with any new changes. (A reboot won't work the drive has to be powered down)

So you will have to play around with it till you achieve your desired settings.

---

