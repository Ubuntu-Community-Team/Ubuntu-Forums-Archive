---
title: "Poor Harddisc performance"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by Daniel_D on 2007-04-25
Hello!

I'm with Kubuntu since begining of edgy, upgraded to feisty some days ago. I also had a poor (poorer than with WinXP) performance (subjectiv feeling) when i accessed much files or write big files.

Now with feisty it seems even worser.

First, my setup:
Intel P4 (tryed it with and without HT) 3Ghz
2Gb Ram
A Asus P4P800E DLX Mainboard
with two ICH5 SATA ports
and two Promise TX2 SATA ports

Two Samsung Spinpoints, each 250Gb, on the ICH5 are my system discs - both combined with LVM2 (striped) to a "root" (/) and a home volume. (Prior Feisty, i did not use LVM2 - so this might not be the bottleneck)

Here comes the problems:
eg:

[LIST]
[*] If i open a folder with some pictures in it and the thumbnails are _already_ precached, it takes about **~1sek** per picture to show up. (DigiKam is even slower)
[*] If i copy some files from usbdisk/samba/... to my harddrive, the cpu goes 100% and the system gets very sloopy. If i just try to open a small other file, both transactions stand still for quite a time.
[*]for testing, i tryed:
```
time  dd if=/dev/zero of=test bs=1k count=4M
4194304+0 Datensätze ein
4194304+0 Datensätze aus
4294967296 Bytes (4,3 GB) kopiert, 54,1014 Sekunden, 79,4 MB/s

real    0m55.452s
user    0m2.837s
sys     0m24.066s

```
The througput (79MB/s)  seams okay - but while the file was written, a mp3 playing in juk even started to **stutter**  and cpu was again 100%.


[/LIST]


Things i tryed sofar:
[LIST]
[*] Get the latest kernel (2.6.20.7)
[*] Tryed to renice artsd, to prevent sound stutter - didnt helped anyway
[*] Tryed the "dd"-test to an IDE-drive... same effects (it was slightly better, if i wrote to a FAT32 volume...)
[*] noatime
[*] cfq io-scheduler
[*] enabled rootflags=data=writeback  (as kernelparameter and set ext3 accordingly)
[/LIST]
Sofar: no minor changes in this beavhiour.

Has anyone some recommendations, which i could test or some other hints? I really wolud appreciate it.

TIA Daniel

PS, some outputs:
dmesg: [http://pastebin.ca/458451](http://pastebin.ca/458451)
fdisk, mount and lvs: [http://pastebin.ca/458461](http://pastebin.ca/458461)

---

### Post by Daniel_D on 2007-04-26
Ah... i forgot to paste some outputs:

lspci: [http://pastebin.ca/459065](http://pastebin.ca/459065)
lsmod: [http://pastebin.ca/459066](http://pastebin.ca/459066)

(im using the proprietary nvidia drivers, with dualscreen setup - if it might be somehow important)

tia
Daniel

---

### Post by Daniel_D on 2007-04-29
Updated again to the recent kernel (2.6.21).

No subjective change - still 100%CPU while diskaccesses, still slow display of thumbnails, etc...

No ideas anyone? Any help would be appreciated ... pls

TIA Daniel

---

