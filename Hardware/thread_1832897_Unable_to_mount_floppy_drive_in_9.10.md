---
title: "Unable to mount floppy drive in 9.10"
date: 2011-08-25
forum: Hardware
---

### Post by A Traveller on 2011-08-25
Hi all.

I am unable to mount a floppy drive in Ubuntu 9.10. I have tried the following without success.

sudo mkdir /mnt/floppy
sudo mount -t msdos /dev/fd0 /mnt/floppy

sudo mount /dev/fd0 /floppy

mount /media/floppy0

mkdosfs /dev/fd0
sudo mount -t msdos /dev/fd0 /media/floppy

The floppy disk light comes on, I can hear it whirring inside and it makes the usual loud clunking noises like a normal working floppy drive when it's accessing info, however, then it stops and nothing happens, no icon on the Desktop and clicking the icon in Places only cause it to whir for a about four seconds and then stops, no clunking noises.

Does it work fine with the latest Ubuntu?

Any help would be appreciated.

Thanks.

---

### Post by coffeecat on 2011-08-25
Try:

```
udisks --mount /dev/fd0
```

---

### Post by A Traveller on 2011-08-25
Hi coffeecat, thanks for your reply. It says "udisks: command not found".

---

### Post by coffeecat on 2011-08-25
I feared that might happen. I couldn't remember whether that would work in 9.10 - it certainly does in 10.04 and later releases.

9.10 is now unsupported - no more updates, no more security patches. You might want to think about upgrading to 10.04 at least. Floppy handling still doesn't work as it should in later releases, but that udisks command will.

---

### Post by A Traveller on 2011-08-25
Ok, thanks coffeecat. I'll be installing the latest one, 11.04 on my new pc. The reason I wanted a floppy disk was that I may have to flash my new motherboard and I thought having the update on a floppy would be simpler for the computer to deal with upon startup than a USB drive. I will be using the GA-890GPA-UD3H rev. 2.1 with an AMD Phenom II X6 1100T CPU. If I cannot even access the BIOS flash screen, then I may have to remove the CPU and attach an older one, update BIOS with that, then remove that CPU and re-attach the new CPU! I could attach the old CPU first and flash BIOS first, but I'm thinking that if the new CPU happens to work with the motherboard just out of the box, it'd save me any of the trouble.

---

