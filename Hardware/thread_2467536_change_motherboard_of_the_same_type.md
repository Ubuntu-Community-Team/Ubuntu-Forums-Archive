---
title: "change motherboard of the same type"
date: 2021-09-30
forum: Hardware
---

### Post by ramster2 on 2021-09-30
if I replace broken motherboard with a new one, but of the same brand, type & model (completely identical), do I need to reinstall Ubuntu 20.04?
Or do I just move the rest of components (such as CPU, GPU, HDDs), and put them onto the new motherboard and happy sailing from there?

---

### Post by CharlesA on 2021-09-30
It should work fine. Ubuntu isn't like Windows where it needs to grab third party drivers to work on different hardware.

Just make sure the new board supports the CPU and memory you want to use from the old board.

---

### Post by guiverc on 2021-09-30
I've had boxes where I've replaced a motherboard with a like one from a same brand/model/year box & had issues (*it booted, and ran, I just wasn't happy with the results as performance wasn't what it was*), a re-install fixed it though.

But I've also had no problems at all (*including with motherboards that I knew were very different thus was expecting issues* *and thus expected to need to re-install*).

If the motherboards are even a few months apart in production, components can have changed that can easily be missed by visual inspection, or results such as `lshw` that I tend to rely on (*how many of us actually read the component numbers for each chip - I sure don't which maybe my failing*).

If it's a desktop install; a *upgrade via re-install*, or *repair installation* is quick & super easy to do, so I'd give it a go of *simple* swap, and then just re-install (**no-format**) if issues are encountered - it's what I do anyway.

My 2c is you can *best-guess*, but I've had issues where I didn't expect any, and no-issues when I did expect some.... 

Are you sure they're identical motherboards; did you scan all chipsets?

---

### Post by Autodave on 2021-09-30
I always have a hard drive sitting around with Xubuntu on it.  The reason for this is that if I get a machine that won't boot and I am not sure why, I can always throw the Xubuntu drive in and see if it will boot up and run.  If it does boot and run, I just leave it in, change the user name and password and give it back to the person that owns it.  I have gotten a bunch of Linux converts that way!  

I would still make a back up of all your important stuff (which you should already have anyway) and see what happens.  You probably will not have any issues at all.

---

### Post by oldfred on 2021-09-30
If a newer UEFI based system, the UEFI boot entry is in the motherboard.
You can totally reinstall grub, or maybe just need to use efibootmgr to add entry into UEFI.
See:
man efibootmgr

Entry depends on which partition is ESP and if sdX or NVMe type drive.
To see entries:
sudo efibootmgr -v 

sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.

---

