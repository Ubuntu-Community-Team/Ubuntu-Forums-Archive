---
title: "Harddisk about to die"
date: 2010-06-10
forum: Hardware
---

### Post by anonbeat on 2010-06-10
I have 3 Seagate ST31500341AS with firmware CC1H and one of them started a few months back to do a click sound. Every time the click is heard the whole system gets frozen and its starting to be very annoying.

I checked in the output log file /var/log/messages and /var/log/dmesg for some information about which of the disks is causing the problem but there is nothing in that files.

Anyone know where to check or how to enable this output into log files so I know what of the files is about to dead ?

Thanks in advance
J.Rios

---

### Post by tango_ninja on 2010-06-10
> **anonbeat said:**
> I have 3 Seagate ST31500341AS with firmware CC1H and one of them started a few months back to do a click sound. Every time the click is heard the whole system gets frozen and its starting to be very annoying.

I checked in the output log file /var/log/messages and /var/log/dmesg for some information about which of the disks is causing the problem but there is nothing in that files.

Anyone know where to check or how to enable this output into log files so I know what of the files is about to dead ?

Thanks in advance
J.Rios

Sorry, can't really help much.  But according to the [Seagate help forums]("http://forums.seagate.com/t5/Barracuda-XT-Barracuda-and/ST31500341AS-Seagate-worst-nightmare/m-p/16442;jsessionid=8F3BA3CABA4E296A0E85454CD0B5A1E5") this seems to be a common problem with the model.  Everyone there has advised contacting Seagate support directly.  Good luck..

---

### Post by Hreinsi on 2010-06-10
I would gess hes crassing how old is the disk

---

### Post by Hreinsi on 2010-06-10
Have you done any disk tests like norton chost or similar

---

### Post by limestone on 2010-06-10
The klick and freeze is the computer telling you it's time to buy new stuff ^^

---

### Post by anonbeat on 2010-06-10
> **tango_ninja said:**
> Sorry, can't really help much.  But according to the [Seagate help forums]("http://forums.seagate.com/t5/Barracuda-XT-Barracuda-and/ST31500341AS-Seagate-worst-nightmare/m-p/16442;jsessionid=8F3BA3CABA4E296A0E85454CD0B5A1E5") this seems to be a common problem with the model.  Everyone there has advised contacting Seagate support directly.  Good luck..

Yes they told me as this firmware revision dont have the common problem of this model its just a disk with a failure. I need to identify the disk and return it to seagate to get it replaced.

This is what Im trying to do.

> **Hreinsi said:**
> Have you done any disk tests like norton chost or similar

Its in a raid 5 setup and its not easy task to backup around 4TB of data. Im worried in case while Im doing a test and removed a good disk the other dies and makes my data useless so I want to find other way to detect which one is failing.

---

### Post by anonbeat on 2010-06-10
> **pont.andersson said:**
> The klick and freeze is the computer telling you it's time to buy new stuff ^^

They are in warranty till 2013 so I can get it replaced it. Just need to find out which is the faulty one.

---

### Post by Hreinsi on 2010-06-10
I have had to do this twice with seagate disks only few months old 
Took it to the dealer i bougth it from and he sent them for me and i got new one.:)

---

### Post by anonbeat on 2010-06-10
> **Hreinsi said:**
> I have had to do this twice with seagate disks only few months old 
Took it to the dealer i bougth it from and he sent them for me and i got new one.:)

And got again a 7200.11 ? I think it should be better receive a 7200.12

---

### Post by Hreinsi on 2010-06-10
Im using Seagate ST31000528AS Barracuda 7200.12 Hard Drive - 1TB, 7200

works great

---

### Post by efflandt on 2010-06-10
You might try SeaTools for DOS on bootable CD-ROM or floppy.

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD)

---

### Post by tgalati4 on 2010-06-10
smartmontools may be able to read the SMART errors as they are stored on the disk.  The RAID controller (at least on my Dell PERC controllers) store disk health information that you can access through Dell's OMSA linux utilities.

If nothing else, check the temperatures of the disks.  Usually the hotest one will fail first.

---

### Post by anonbeat on 2010-06-11
> **tgalati4 said:**
> smartmontools may be able to read the SMART errors as they are stored on the disk.  The RAID controller (at least on my Dell PERC controllers) store disk health information that you can access through Dell's OMSA linux utilities.

If nothing else, check the temperatures of the disks.  Usually the hotest one will fail first.

All the disks reports more or less the same temp, hour used, errors, etc

---

### Post by soravis on 2010-06-11
You can try [hdsentinel]("http://www.hdsentinel.com/hard_disk_sentinel_linux.php"), it's a handy little terminal application, displaying the basic infos about your drive, and most of all, an estimated lifetime, based on a large smart attribute database. It's quite accurate.

But, what I recommend more, is also smartmontools.
Look for critical smart attributes and a quick health check with smartctl -H /dev/<device>
Full attribute table: smartctl -A
You can list logged smart errors with smartctl -l error
Results of selftests: smartctl -l selftest
You can run selftests with: smartctl -t <TEST>
   where <TEST> can be "offline" - a standard smart test., "short" (quick performance test), and "long" (a thorough scan test of the drive). In your case, I would recommend the long test. YOu can monitor the progress with smartctl -l selftest, (or if it's not working, with smartctl -c), and get the result with smartctl -l error and smartctl -l selftest. Hopefully, the dying disk will throw an error, or in the worst case freeze during test...
...and of course there's the manual for more info.
Hope it helps!

---

### Post by mr clark25 on 2010-06-11
when you send your drive in to get it replaced, will they transfer your data onto the new one?

it sounds like you have plenty of space to backup one of the drives...



now the harder part: which drive is failing?

can you open up your case and listen to the drives? or are they to close together to tell which one it is?

---

### Post by anonbeat on 2010-06-11
> **soravis said:**
> You can try [hdsentinel]("http://www.hdsentinel.com/hard_disk_sentinel_linux.php"), it's a handy little terminal application, displaying the basic infos about your drive, and most of all, an estimated lifetime, based on a large smart attribute database. It's quite accurate.

But, what I recommend more, is also smartmontools.
Look for critical smart attributes and a quick health check with smartctl -H /dev/<device>
Full attribute table: smartctl -A
You can list logged smart errors with smartctl -l error
Results of selftests: smartctl -l selftest
You can run selftests with: smartctl -t <TEST>
   where <TEST> can be "offline" - a standard smart test., "short" (quick performance test), and "long" (a thorough scan test of the drive). In your case, I would recommend the long test. YOu can monitor the progress with smartctl -l selftest, (or if it's not working, with smartctl -c), and get the result with smartctl -l error and smartctl -l selftest. Hopefully, the dying disk will throw an error, or in the worst case freeze during test...
...and of course there's the manual for more info.
Hope it helps!

I tried the smartmontools but the results are almost identical for all the drives.
I just want to know a way to get errors from disks in the linux log as while its making click sound there must be unexpecting behaivour and linux should log it

---

### Post by anonbeat on 2010-06-11
> **mr clark25 said:**
> when you send your drive in to get it replaced, will they transfer your data onto the new one?

it sounds like you have plenty of space to backup one of the drives...



now the harder part: which drive is failing?

can you open up your case and listen to the drives? or are they to close together to tell which one it is?

I tried touching the disks and listenning but I cant tell which of them is doing it.

---

### Post by soravis on 2010-06-12
hdsentinel scores are all the same? And neither of the smart selftests revealed errors?
...strange.
Try running an fsck.

[COLOR=DimGray]You said when the drive 'clicks', the whole system freezes. Maybe this is why there are no errors in the log files?[/COLOR]

---

### Post by CharlesA on 2010-06-12
If you aren't sure what drive is going out, replace them all, one at a time and rebuild the array after each one is replaced.

I had a Seagate 7200.11 drive go out on me a couple weeks ago and it has been a royal pain in the *** to get it replaced, and it will only be replaced with a "remanufactured" drive.

---

### Post by tgalati4 on 2010-06-12
Linux will only log errors if the drive fails to deliver a requested IO block.  Then the error will show up in dmesg and your IO-Wait times will go up and everything else will slow down on the system.  

If the disk is performing a self-test (which modern drives do every several hundred hours) or if it's moving data around for performance reasons, then it doesn't get reported to the OS.

The clicking noise could be a recalibration procedure that the drive is going through, or simply parking of the heads due to idle conditions.

If you don't see critical errors:

dmesg | grep error

or

smartctl -a /dev/sda1

Then it's possible that the drives are OK.  Run top and watch the 0.0%wa statistic.  If it goes up during your freeze-out, then you know that your system is waiting for IO.  It could be a SATA controller problem, a wonky SATA cable (try swapping and replugging all cables).

I had a loose power cable on one of my drives that caused a similar symptom.  No error messages at all, but long IO wait times.  Linux is patient.  If a disk drive is deprived of power, it can't deliver data.  Replugging the drive fixed the problem.  This particular system had been running for 4 years non-stop.  Vibration loosening of cables can mimic software and hardware problems!

---

### Post by mr clark25 on 2010-06-13
if you are using 10.04 (your account ifo says you are), you can run the hard drive speed tester from system>administration>disk utility. select your drive and then select "benchmark".

from your description, one drive should slow down when it starts clicking.


hope this helps!

---

### Post by cqc on 2010-06-13
I have similar problem with my old HDD (samsung 80GB) i can also hear click sound and after that system stop working. My HDD has a lot of bad sectors, because its old.

---

