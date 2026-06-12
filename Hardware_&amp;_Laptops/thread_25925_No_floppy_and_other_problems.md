---
title: "No floppy and other problems"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Erkkimon on 2005-04-11
I'm from Finland and I have heard many good news 'bout Ubuntu Linux. Well, first I had a problem installing Ubuntu coz I have a laptop (FujitsuSiemens Amilo) and there was no no-floppy mode in boot options. So I just switched to expert mode and never downloaded floppy modules. Are there any easier ways to disable floppy drive?

After that I could go through the floppy error and it didn't complain about floppy anymore. After that it started to cry something about system volumes. What is it and what's wrong with my computer then?

Thank you for the answers already. :)

---

### Post by heimo on 2005-04-11
Hi!

I don't know why you get error messages for not having floppy drive. :-/ :-\ I don't have floppy drive on my desktop PC and the isntallation from (pre-release) 5.04 CD didn't give errors about floppy drive. Can you give spesific error message? What did the error cause and at what spesific point of installation process?

And same question to the "system volumes" error, could you elaborate? After what does this happen and what is the exact error message? If that's during installation, you can get more spesific information by selecting different console (CTRL+ALT+F3) or is it F4, I can't remember. If it's after installation, you could check boot log (I'm not at my Linux box, so I can't give you more spesific instructions).

If you didn't manage to install Ubuntu and you don't need to worry about losing data on the hard disk, you could try to find access mode setting in BIOS - change it to LBA. Laptop BIOS however... can be very limited, at least my Thinkpads is.

---

### Post by Erkkimon on 2005-04-11
The error appeared while installing the base system. It said like that: 

*nips 
insmod /lib/modules/2.6.8.1-3-386/kernel/drivers/net/via-rhine.ko 
insmod /lib/modules/2.6.8.1-3-386/kernel/drivers/block-floppy.ko 
FATAL: Error inserting floppy (/lib/modules/2.6.8.1-3-386/kernel/drivers/block/floppy.ko): No such device 
insmod /lib/modules/2.6.8.1-3-386/kernel/drivers/block/floppy.ko 
FATAL: Error inserting floppy (/lib/modules/2.6.8.1-3-386/kernel/drivers/block/floppy.ko): No such device 
No matching physical volumes found 
No volume groups found 
Reading all physical volumes. This may take a while... 
No matching physical volumes found 
No volume groups found 
Reading all physical volumes. This may take a while... 
No matching physical volumes found 
No volume groups found 
Reading all physical volumes. This may take a while... 
No matching physical volumes found 
No volume groups found 
Reading all physical volumes. This may take a while... 
cp: Read Error: Input/output error 
*naps

So first it complained about floppy, I fixed da prob (but badly) and now it didn't get stuck with da floppy. Now it only complains about the system volumes. I have heard that there could be probs with my partitions... Well, I really dunno what would be wrong with the partitions coz I let the installer compare my hard disk into partitions automatically, itself.

Yeah. I don't need to be afraid of losing info, anymore, coz I already lost the info. ;) Well, I have veeeery bad BIOS on my lappy and it isn't too good laptop, but I have got 4 Linuxes to work on it, so it shouldn't be impossible. :) But I try to find. Thank you.

---

### Post by Erkkimon on 2005-04-11
I dunno what I did but now it doesn't complain about the floppy anymore. I'll write all it says:

Base system installation error

The debootstrap program exited with an error (return value 1).

Check /var/log/messages or see virtual console 3 for the details.

[There's an option "Continue" and I choose it]

Failed to install the base system

The base system installation into /target/ failed.

Check /var/log/messages or see console 3 for the details.


[There's an option "Continue" and I choose it]

Installation step failed

An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Install the base system.

And virtual console 3 looks like this:

insmod /lib/modules/2.6.10-5-386/kernel/drivers/block/floppy.ko
FATAL: Error inserting floppy (/lib/modules/2.6.10-5-386/kernel/drivers/block/floppy.ko): No such device
insmod /lib/modules/2.6.10-5-386/kernel/drivers/block/floppy.ko
FATAL: Error inserting floppy (/lib/modules/2.6.10-5-386/kernel/drivers/block/floppy.ko): No such device
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No volume groups found
  Reading all physical volumes. This may take a while...
cp: Read error: Input/output error
cp: Read error: Input/output error
cp: Read error: Input/output error
cp: Read error: Input/output error
cp: Read error: Input/output error

---

### Post by robododge on 2005-06-29
Erkkimon,

Did you find a solution to the Volume Group Input/output error?

Thanks
Steve

---

### Post by robododge on 2005-06-29
Yep, I figure out my problem.

```
cp: Read error: Input/output error
``` 


If you watch console #3 while *installing the base system* is in progress, this error pops up and the whole install quits.  I my case, the error ment a problem copying data from cd to the harddrive.  This happened in the same place each time.  For kicks, I re-burned an ISO on a different burner and tried again.  The second disk was successful! \\:D/

---

