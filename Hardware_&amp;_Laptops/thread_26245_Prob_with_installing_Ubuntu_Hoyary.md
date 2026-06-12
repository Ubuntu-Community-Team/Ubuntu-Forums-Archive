---
title: "Prob with installing Ubuntu Hoyary"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Erkkimon on 2005-04-12
I'm from Finland and I have heard many good news 'bout Ubuntu Linux. 

I have had the same problems with both Warty and Hoary.

Well, first I had a problem installing Ubuntu coz I have a laptop (FujitsuSiemens Amilo) and there was no no-floppy mode in boot options. So I just switched to expert mode and never downloaded floppy modules. Are there any easier ways to disable floppy drive?

After disabling downloading floppy module I could go through the floppy error and it didn't complain about floppy anymore (I really dunno what I did \\:D/ ). After that it started to cry something about system volumes. What is it and what's wrong with my computer then?

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

Now it complains about some sed. The install crashes and I'll write down all the info I got

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

I don't need to be afraid of losing info, anymore, coz I already lost the info.  Well, I have veeeery bad BIOS on my lappy and it isn't too good laptop, but I have got 4 Linuxes to work on it, so it shouldn't be impossible.

Thx for your answers already. I have asked for help many times from different places but now I think I could get help coz this is a real Ubuntu forum. :)

---

