---
title: "TSSTCorp IDE DVD-Drive: no DMA possible"
date: 2008-07-14
forum: Hardware
---

### Post by mad.man on 2008-07-14
Hello there,

since i upgraded from Gutsy to Hardy (with a fresh install) my DVD-Drive won't read or burn DVD's. CD's still work. The DVD-drive itself is still okay, because Windows works.

I've tried [FONT="Courier New"]hdparm -d1 /dev/scd0[/FONT] (after checking in fstab that it was correct. But I just receive the error message:
 [FONT="Courier New"]setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device[/FONT]

I've put [FONT="Courier New"]piix[/FONT] in /etc/modules. Also no joy. 

I've added [FONT="Courier New"]pata_atiixp[/FONT] and [FONT="Courier New"]blacklist ata_generic[/FONT] to my [FONT="Courier New"]/etc/initramfs-tools/modules[/FONT]. That didn't help either.

I suspect the problem is with the SCSI recognition of the drive with Hardy. How do I set it back to a PATA? I've a feeling that I may have falsely checked an option during the install without looking.

Thanks for any help. I'm really stuck here and I hate going back to windows.

#madman

---

### Post by mad.man on 2008-07-15
Bump Bump..:)

Nix with Google. There was a short comment on Kerneltrap about TSSTCorp drives having problems. Anyone know anything more about this?

---

