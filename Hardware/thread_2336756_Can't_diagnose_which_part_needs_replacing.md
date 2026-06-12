---
title: "Can't diagnose which part needs replacing"
date: 2016-09-10
forum: Hardware
---

### Post by raphytaffy2 on 2016-09-10
Hi all, I'm running 16.04.1 LTS and having a hell of a time diagnosing some issues.

System specs:
[LIST]
[*]Intel DP55SB board
[*]i3 540 3.06Ghz
[*]Corsair Vengeance 16GB (2 x 8GB) DDR3 1600 (upgraded 7/5/16)
[*]Samsung 850 Pro 512GB (brand new)
[/LIST]

I initially tried to run this on an older HDD and started hitting errors, so I assumed the drive was failing and bought an SSD. Installed through a USB flash drive and everything went swimmingly. I started to set up my server, installing SABNzbd, SickBeard, Dropbox, etc. Again, everything went well, my Dropbox downloaded all of my files successfully, I was able to move files around, etc.

Now for some reason, as soon as SABNzbd completes a download and begins the unpacking stage, it seems like my system hits a kernel panic. At this point, my system is set to read-only and a bunch of errors are displayed when booting up. It took me a really long time reinstalling and setting everything up again to narrow down the problem to this, but now I'm stuck.

Could it be my:
[LIST]
[*]SSD? If so, why can I seemingly install the OS along with my applications just fine. I can also move files around, so it seems like I/O is okay. It's also brand new, so I am inclined to rule this out.
[*]SATA ports? I've tried ports 0 and 1. I could continue to cycle through them and try other ports, but it will probably lead to the same result.
[*]PSU? It's quite an old unit and perhaps there's not enough power being supplied during the unpacking stage?
[*]RAM? This is also brand new.
[*]SATA cable? Brand new as well.
[*]CPU? Perhaps the unpacking stage utilizes multiple cores while installing applications/moving files around does not. Could the CPU be partially damaged?
[/LIST]

The only other thing I can think of is that I had quite a hard time getting GRUB to properly install. Due to this and the unpacking issue, I reinstalled a loooot. During the install process, I always opted to use the entire disk, yet on the screen where the changes will be written to the disk, it lists partitions #1 and #5. Not sure if this is normal or not, but perhaps there are some corrupted partitions in #2, #3, or #4? If I choose to use the whole disk, shouldn't that zero out the whole drive anyway? Honestly at a loss and looking for some advice. 

Pictures of errors and install: [http://imgur.com/a/nr7Ks](http://imgur.com/a/nr7Ks)

---

### Post by pqwoerituytrueiwoq on 2016-09-10
set the bios to use ahci not ide since you have a ssd
do a ram test, memtest86+
see if the cpu is stable with mprime (linux version of prime95)
a bad psu can be hard so spot and you never know what damage it may have done, a good unit will not take parts with it when it fails

---

### Post by raphytaffy2 on 2016-09-10
> **pqwoerituytrueiwoq said:**
> set the bios to use ahci not ide since you have a ssd
do a ram test, memtest86+
see if the cpu is stable with mprime (linux version of prime95)
a bad psu can be hard so spot and you never know what damage it may have done, a good unit will not take parts with it when it fails

Brilliant! I think we're getting somewhere. BIOS was already set to use AHCI.

Ran memtest and it isn't even able to complete the tests: [https://streamable.com/szn4](https://streamable.com/szn4)

From the DP55SB [documentation]("http://downloadmirror.intel.com/18130/eng/dp55sb_techprodspec.pdf"):
[LIST]
[*]Support for **DDR3 1600 MHz**, DDR3 1333 MHz, and DDR3 1066 MHz DIMMs
[/LIST]

Taking a peek at the BIOS, my memory settings are:
[LIST]
[*]Multiplier: 10
[*]Speed: 1333 MHz
[/LIST]

When I go into manual override, it only shows the following options:
[LIST]
[*]Auto
[*]10: DDR3-1333
[*]8: DDR3-1067
[*]6: DDR3-800
[/LIST]

My BIOS was currently on version **KGIBX10J.86A.5924.2011.0223.0145**. I updated to the latest version (**KGIBX10J.86A.5936.2011.0630.2250**) thinking it would add an option for DDR3-1600. Alas, to no avail. The manual settings still show the same options.

Should I set it to auto and see what happens? If it is set to the wrong clock speed, this should affect the timing right? Would this cause a kernel panic?

**Edit: **Setting it to **10: DDR3-1333**, my system wouldn't post. Seems setting it to **Auto** is effectively setting it to **DDR3-1600**. Running mprime now.

**Edit2: **Just checked the i3 540 [specs]("http://ark.intel.com/products/46473/Intel-Core-i3-540-Processor-4M-Cache-3_06-GHz"):
[LIST]
[*]Memory types: DDR3 1066/1333
[/LIST]

Problem found? I assume DDR3 1600 is causing compatibility issues since it is running at a higher clock speed than the CPU is listed as being able to handle. Just looking for confirmation.

---

### Post by pqwoerituytrueiwoq on 2016-09-11
I assume that ram you got is rated for 1600 cl 9
id expect it to be able to run  at 1333 cl 8
typically when you underclock memory you can get a low latency out of it without applying additional voltage

if you set it to cl 10 1333 that should be well with the rams ability to operate

can you boot memtest86+ from the grub menu on your ubuntu install?
looked like the monitor just lost the signal or some dumb digital video annoyances

bad ram (or unstable settings) can cause a complete lockup or a black screen in my experience, but that is when running a GUI not a tty only
if you have a full manual timings editor in your bios you can call corsair and they can help you set all the details

you can see what the ram is running as from the OS
[http://www.cyberciti.biz/faq/check-ram-speed-linux/](http://www.cyberciti.biz/faq/check-ram-speed-linux/)
some systems will report the speed at 1/2 of what it really is eg 800 can mean 1600 this is cause the first D in DDR means double

---

### Post by raphytaffy2 on 2016-09-13
> **pqwoerituytrueiwoq said:**
> I assume that ram you got is rated for 1600 cl 9
id expect it to be able to run  at 1333 cl 8
typically when you underclock memory you can get a low latency out of it without applying additional voltage

if you set it to cl 10 1333 that should be well with the rams ability to operate

My RAM is rated for 1600 CL 10.

> **pqwoerituytrueiwoq said:**
> can you boot memtest86+ from the grub menu on your ubuntu install?
looked like the monitor just lost the signal or some dumb digital video annoyances

I can't seem to access memtest86+ from my Grub menu. I'm presented with two options (**Ubuntu** and **Advanced options for Ubuntu**). Inside of the Advanced options for Ubuntu:
[LIST]
[*]Ubuntu, with Linux 4.4.0-36-generic
[*]Ubuntu, with Linux 4.4.0-36-generic (recovery mode)
[*]Ubuntu, with Linux 4.4.0-31-generic
[*]Ubuntu, with Linux 4.4.0-31-generic (recovery mode)
[/LIST]

I'm not sure it is the monitor losing the signal. The test runs up until about 13% and then reboots my system.

> **pqwoerituytrueiwoq said:**
> you can see what the ram is running as from the OS
[http://www.cyberciti.biz/faq/check-ram-speed-linux/](http://www.cyberciti.biz/faq/check-ram-speed-linux/)
some systems will report the speed at 1/2 of what it really is eg 800 can mean 1600 this is cause the first D in DDR means double

Here are the results of **dmidecode**:
```
Handle 0x001D, DMI type 17, 28 bytes
Memory Device
           Array Handle: 0x001B
           Error Information Handle: Not Provided
           Total Width: Unknown
           Data Width: Unknown
           Size: No Module Installed
           Form Factor: DIMM
           Set: None
           Locator: J1MY
           Bank Locator: CHANNEL A DIMM 0
           Type: Unknown
           Type Detail: Synchronous
           Speed: Unknown
           Manufacturer: NO DIMM
           Serial Number: NO DIMM
           Asset Tag: NO DIMM
           Part Number: NO DIMM
           Rank: Unknown


Handle 0x001E, DMI type 17, 28 bytes
Memory Device
           Array Handle: 0x001B
           Error Information Handle: Not Provided
           Total Width: 64 bits
           Data Width: 64 bits
           Size: 8192 MB
           Form Factor: DIMM
           Set: None
           Locator: J2MY
           Bank Locator: CHANNEL A DIMM 1
           Type: DDR3
           Type Detail: Synchronous
           Speed: 1333 MHz
           Manufacturer: 0x029E
           Serial Number: 0x00000000
           Asset Tag: Unknown
           Part Number: 0x434D4C31364758334D324131363030433130
           Rank: Unknown


Handle 0x001F, DMI type 17, 28 bytes
Memory Device
           Array Handle: 0x001B
           Error Information Handle: Not Provided
           Total Width: Unknown
           Data Width: Unknown
           Size: No Module Installed
           Form Factor: DIMM
           Set: None
           Locator: J3MY
           Bank Locator: CHANNEL B DIMM 0
           Type: Unknown
           Type Detail: Synchronous
           Speed: Unknown
           Manufacturer: NO DIMM
           Serial Number: NO DIMM
           Asset Tag: NO DIMM
           Part Number: NO DIMM
           Rank: Unknown


Handle 0x0020, DMI type 17, 28 bytes
Memory Device
           Array Handle: 0x001B
           Error Information Handle: Not Provided
           Total Width: 64 bits
           Data Width: 64 bits
           Size: 8192 MB
           Form Factor: DIMM
           Set: None
           Locator: J4MY
           Bank Locator: CHANNEL B DIMM 1
           Type: DDR3
           Type Detail: Synchronous
           Speed: 1333 MHz
           Manufacturer: 0x029E
           Serial Number: 0x00000000
           Asset Tag: Unknown
           Part Number: 0x434D4C31364758334D324131363030433130
           Rank: Unknown

```

Looks like I accidentally installed the RAM in Channel A/B DIMM 1. I'll move it appropriately to DIMM 0, but is this enough to cause an issue? Still beating my head over how to properly diagnose. Appreciate all of the help thus far.

I ran **mprime **for the first test case (Small FFTs - maximum heat and FPU stress, data fits in L2 cache, RAM not tested much) and it passed all tests successfully.

Currently running it for the second test case (In-place large FFTs - maximum power consumption, some RAM tested) and will report back with results.

---

### Post by raphytaffy2 on 2016-09-14
Instead of installing all of my apps again, I installed **unrar**, copied a rar file to my server, and attempted to extract it:

```

$ unrar e test.part01.rar


UNRAR 5.30 beta 2 freeware      Copyright (c) 1993-2015 Alexander Roshal


Extracting from test.part01.rar


Extracting  test.mkv   2%


Extracting from test.part02.rar


...         test.mkv   5%


Extracting from test.part03.rar


...         test.mkv   8%


Extracting from test.part04.rar


...         test.mkv  11%


Extracting from test.part05.rar


...         test.mkv  14%


Extracting from test.part06.rar


...         test.mkv  17%


Extracting from test.part07.rar


...         test.mkv  20%


Extracting from test.part08.rar


...         test.mkv  22%


Extracting from test.part09.rar


...         test.mkv  25%


Extracting from test.part10.rar


...         test.mkv  28%


Extracting from test.part11.rar


...         test.mkv  31%


Extracting from test.part12.rar


...         test.mkv  34%


Extracting from test.part13.rar


...         test.mkv  37%


Extracting from test.part14.rar


...         test.mkv  40%


Extracting from test.part15.rar


...         test.mkv  42%Connection to 192.168.1.29 closed by remote host.
Connection to 192.168.1.29 closed.

```

Midway through, it closed my **ssh** connection. Attempting it from the box, these error messages showed up: [http://i.imgur.com/s6EZvYZ.jpg](http://i.imgur.com/s6EZvYZ.jpg)

It seems to consistently fail at extracting a file, but I'm still stuck at why. Thoughts on how best to proceed? mprime test #2 continued to succeed.

---

### Post by pqwoerituytrueiwoq on 2016-09-16
it would appear you have a ram stick in the wrong slot, you have slots 2 and 4 in use, you should use slots 1 and 2
look at your boards manual to know what slots are channel A and B, both sticks should be in channel A
that should be a non-fatal issue though, you are running 2 single channel ram sticks you are better off using 1 dual channel

then select memtest86+ from a live cd
alternatively you could add this to [FONT=courier new]/etc/grub.d/40_custom[/FONT]
```
menuentry "Memtest 86+" {
 linux16 /memtest86+.bin
}
```
you can download memtest86+ here
[http://memtest.org/download/5.01/](http://memtest.org/download/5.01/)
just edit [FONT=courier new]/memtest86+.bin[/FONT]
to be the correct path to the bin file
after that run [FONT=courier new]sudo update-grub[/FONT]

---

