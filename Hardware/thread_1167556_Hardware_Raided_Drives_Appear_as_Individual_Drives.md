---
title: "Hardware Raided Drives Appear as Individual Drives w/ Clean Ubuntu Install"
date: 2009-05-23
forum: Hardware
---

### Post by grittyminder on 2009-05-23
Hi there. I just purchased a new raid controller (SATARAID5-LPPCI) and I'm trying to do a clean install of Ubuntu Server 8.04. I created a new RAID 5 array, and confirmed that the RAID disk configuration is detected as a bootable device in the bios. However, for the disk detection/configuration portion of the Ubuntu Server install the RAID array is not being detected. Rather, the individual disks are being detected. I do not want to use software RAID because that defeats the purpose of the new hardware raid controller. Any ideas?

---

### Post by sloggerkhan on 2009-05-23
There may be a proprietary driver for your hardware raid ( I can't tell anything from the info you posted, it returns a bunch of chinese sites when googled ), or it could be your bios. You may have also wound up with a card that just gives you more sata ports and relies on some sort of windows software driver for RAID. (As noted, can't really tell from infor posted.)

However, in general, IMO you are better off with linux software raid 99% of the time if you are using linux. Performance is supposed to be within +/-10% of most commercial RAID cards, not to mention you can use the array in any linux machine with enough ports irrespective of any special hardware.

---

### Post by grittyminder on 2009-05-23
> However, in general, IMO you are better off with linux software 
> raid 99% of the time if you are using linux. Performance is 
> supposed to be within +/-10% of most commercial RAID cards, not 
> to mention you can use the array in any linux machine with 
> enough ports irrespective of any special hardware.

This is something that has always confused me a bit. I hear from some folks that you should use software raid for reasons similar to what you mention; from other folks I hear that hardware raid is better because you do not have to deal with the extraneous software layer. I always assumed that hardware raid should be better--but I guess from what you say that depends on the quality of the driver available (or in my situation, whether or not the driver even exists), right?

In any case, software raid may be the easier choice for me right now, and from what you say it doesn't sound like a bad choice either.

---

