---
title: "Partition issue"
date: 2009-09-08
forum: Hardware
---

### Post by beameup on 2009-09-08
My wife has an Acer Aspire One, came with XP. I put Ubuntu Netbook Remix on it on a 20GB extended partition, left 120 for XP. Turns out she loves the Ubuntu so I went to resize the partitions. Booted up with UNR on a USB stick. Using GParted, I shrunk the primary with XP down to 20GB and then added the unallocated space(think it was 109GB) to the extended Ubuntu partition. Also an 800MB swap space and 10GB for the Acer recovery disc. I also decided to make the swap space bigger to 1.5GB (sounded good at the time). Everything went fine until the very end it gave me an error about not being able to complete the tasks. It resized the Ubuntu partition but didn't do the swap. OK no big deal, didn't need it anyway. Then I realized the Ubuntu partition is showing 120GB of data on it with 10GB free. After a bit of research I found where a reboot should fix that issue, so I did. It didn't fix it. When I boot into Ubuntu it still shows the old 20GB file size for the drive in Nautilus. GParted still shows it having 120GB used with 10GB free.

So my guess is that 100GB I added didn't transfer over to the partition table?
I've run the disk check and when it gets to 'resize2fs /dev/sda5' it gives me the message to please run 'e2fsck -f /dev/sda5' 1st. Well i've already run it first. I tried a few more times with GParted and a terminal, same result. Also tried piggybacking the commands but no go, it keeps saying run e2fsck 1st. 

So now i'm stuck and trying not to reformat. Anyone have a similar issue? I've been googling  to no avail, found the Gparted forum but nothing like this in there.

I can post some outputs here if needed. Just tell me what.

Note: my file sizes may be off a little but close enough. I can boot into both OS'es fine. Only ubuntu thinks it's still on a 20GB partition.

Any help will be appreciated.


Update: I'm just going to reformat and reinstall. Sucks but I can't find any other option

---

