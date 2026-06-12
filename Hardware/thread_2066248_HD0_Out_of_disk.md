---
title: "HD0: Out of disk"
date: 2012-10-04
forum: Hardware
---

### Post by EmyrB on 2012-10-04
Hi All,

My dual Windows 7/Ubuntu 12.04 boot PC had a crash some weeks back which resulted in booting to a LiveCD to run e2fsck to repair errors on my Ubuntu root partition.

Since then, I randomly get the error: -

```
hd0: out of disk
press any key to continue...
```

I did a search on the error and best case scenario duff hard disk or worse case duff motherboard (yikes)! Rebooting when the error appears sometimes will allow me to boot to Ubuntu straight away, other times it might take 5 or 6 attempts.

Yesterday I switched on my PC, and the phone rang whilst it was booting. Same error, but as I was on the phone, I didn't do anything and it booted into Ubuntu log in screen.

As it happened, I also had to support a customer remotely and the only way to get into their PC is to run a Windows only software so I rebooted and selected Wndows 7 and nothing, just a black screen for 10 minutes. Rebooted, selected Windows 7 and the same thing happened.

OK here is the crux of the issue. SDA houses Windows 7 partition (SDA1) and Ubuntu / (SDA2) and my /home (SDA3), SDA1 is also flagged as boot. As the Windows 7 partition is borked, I'm assuming this is the cause of the error as I can still boot into Ubuntu. So, I might as well bin the Windows partition (1st time booting into it for 12 months or so) and give the free space to my /home partition. I then want to my root partition to be flagged as boot.

Will this change the SDA numbers on my partitions, so my / becomes SDA1 and my home SDA2? Is this even possible? Will this affect Grub2? Will it bork up Ubuntu? Or should I just wait until 12.10 to be released and start from scratch and bin the entire partition table seeing as Ubuntu still boots and that the Windows partition is the cause of the hd0: out of disk error.

Thanks in Advance

EmyrB

---

