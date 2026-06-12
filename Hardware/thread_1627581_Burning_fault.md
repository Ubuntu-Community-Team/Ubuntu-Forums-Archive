---
title: "Burning fault?"
date: 2010-11-21
forum: Hardware
---

### Post by blenderfox on 2010-11-21
I'm trying to convert a video file I have into a VCD, and I've used almost all of the programs available on the software centre -- including K3B. The file is a .dat format, so I converted it to a MPG file and put it into a K3B project and burned that. It claimed burn is successful, but when I pop the disc back in again, it shows up as a "Blank CD/DVD", and there's nothing on there. So what exactly was it doing? I'm 100% I didn't select "Simulate" or "Dummy Write".....

---

### Post by blenderfox on 2010-11-22
I guess I'm the only one having this problem, then?

---

### Post by blenderfox on 2010-11-27
I've verified that my drive and burn R and RW DVDs, but not R and RW CDs. Does anyone know why? This is driving me nuts..... >_<

---

### Post by Fafler on 2010-11-27
Try to fiddle aroung with mencoder to convert the file to a valid VCD image and use wodim to burn it. Both using the console.

---

### Post by blenderfox on 2010-11-27
> **Fafler said:**
> Try to fiddle aroung with mencoder to convert the file to a valid VCD image and use wodim to burn it. Both using the console.

The image is valid, because I copied the .bin and .cue to my Windows PC and burned the image on there, and it works.

It is also not restricted to just VCDs. I tried burning the CloneZilla iso onto a CDRW on my Windows PC and it worked, but when I tried to burn the same image using K3B on my laptop, it acted as if it had burned everything (buffer progress bars moved, main progress bar moved), but as soon as I put the disc back in in order to verify, it registers as a blank disc. It's like it's pushing the data, but it's not writing. However, the same application, same iso burns successfully on a DVD+RW. I'm confused.... :P

---

### Post by Fafler on 2010-11-27
I can understand that. It's very rare that drives causes problems like that, but maybe burning something with wodim from the terminal will give some useful feedback.

---

### Post by blenderfox on 2010-11-27
> **Fafler said:**
> I can understand that. It's very rare that drives causes problems like that, but maybe burning something with wodim from the terminal will give some useful feedback.

What is the command I need to use to tell wodim to burn an ISO abc.iso to my CDRW then? I can check for any messages and report back after that.

---

### Post by Fafler on 2010-11-27
wodim abc.iso

---

### Post by blenderfox on 2010-11-27
> **Fafler said:**
> wodim abc.iso

I tried that, and a couple of other options:

```
#:~/Desktop$ wodim -dao clonezilla-live-20101106-maverick.iso 
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 131.00 MiB...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CD/DVDW TS-L632D'
Revision       : 'HH18'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Track 01: Total bytes read/written: 137363456/137363456 (67072 sectors).
```

(Check the disc -- it's still showing blank. Try with no additional options)

```
#:~/Desktop$ wodim clonezilla-live-20101106-maverick.iso 
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 131.00 MiB...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CD/DVDW TS-L632D'
Revision       : 'HH18'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Track 01: Total bytes read/written: 137363456/137363456 (67072 sectors).
```

(Check disc.... still blank)

*headbutts table*

---

### Post by Fafler on 2010-11-27
[FONT=monospace]Weird...

I think it's the drive. Search for the model and see if anyone else experience similar issues.
[/FONT]

---

### Post by blenderfox on 2010-11-28
I found this. Not sure if it'll work, but I guess I'll give it a go...

[http://www.ailis.de/~k/archives/36-dell-firmware-problems-with-tsstcorp-ts-l632d-dvd-drive.html]("http://www.ailis.de/~k/archives/36-dell-firmware-problems-with-tsstcorp-ts-l632d-dvd-drive.html")

---

