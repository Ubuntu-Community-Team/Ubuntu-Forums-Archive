---
title: "CD player not recogised since 2.6.24-19 kernel was added"
date: 2008-08-28
forum: General Help
---

### Post by davidjmayo on 2008-08-28
This all started after the new kernel was installed from an update.
A very slow boot showed there was a problem and a recovery boot pinned it to the the CD player. Recovery shows the error
 
ata1: port slow to respond forcing hardreset
      errno=-16

I've looked in the forums here and elsewhere and tried a few /kernel/boot options from GRUB ( all_generic_ide  irqpoll  and noprobe=ata1   but none fix the problem (and they only worked for some not all of the other people)

Also it seems a common problem with ASUS motherboards but mine is a TCC (who are they?) 865GVSA but my CD combo is ASUS CB-5216A

If I boot with 2.6.24-16 (don't know where -17 and -18 went if they were there but they are not on my system now and I didn't remove them) the CD combo is still not recognised. It was fine before this new kernel. 

So I thought I'd reinstall but no CD drive available so what to do?
I thought about booting into 2.6.24-16 and deleting 2.6.24-19 but then I saw a post whilst searching "kernel" not to remove the current kernel.

How can I get rid of the current kernel which is causing this problem ?

---

### Post by Taxman415a on 2008-08-28
If booting from the old kernel doesn't help, it sounds more like a hardware problem that was coincidental with the kernel update.

---

### Post by davidjmayo on 2008-08-28
That would be one big coincidence since there was no problem on the previous kernel and I don't run 24/7. The PC is cold started everyday so I don't think that's the problem but it was my first thought until I found many other issues on launchpad with errno=-16 and ASUS being involved. I still think it's the kernel.
There was also another fix I saw to change the BIOS IDE config to ACHI instead of standard IDE but my Award Phoenix BIOS doesn't seem to have that option.
This is why I need to know how to safely remove that kernel as I think something is hanging around in the boot partition but I don't know the boot or shutdown process in detail. In recovery mode I do see a resume image not found.

If I could remove the new -19 kernel and boot successfully that would be conclusive.

---

### Post by Taxman415a on 2008-08-28
You could just go into /boot and move the -19 vmlinuz and initrd files to vmlinuz-2.6.24-19-generic.old or something similar like that so that you don't delete them and can move them back. Then obviously just make sure to choose the older kernels from the grub menu (and test that that works first). Or you could boot from a livecd that would have an older kernel, etc.

---

### Post by davidjmayo on 2008-08-28
> **Taxman415a said:**
> You could just go into /boot and move the -19 vmlinuz and initrd files to vmlinuz-2.6.24-19-generic.old or something similar like that so that you don't delete them and can move them back. Then obviously just make sure to choose the older kernels from the grub menu (and test that that works first). Or you could boot from a livecd that would have an older kernel, etc.

I like the sound of the move idea but if I can't boot I'm stuck. If I can't get the CD drive recognised it won't CD boot so couldn't use a Live CD 
What do vmliuz and initrd do exactly ?

update:
OK I've done a very quick check on vmlinuz and initrd so get the idea of what they do. Hope we don't cross post here

Are you sure the sys will still boot if I move those files ?

---

### Post by Taxman415a on 2008-08-28
> Are you sure the sys will still boot if I move those files ?

No, lots of things are possible, like a typo, etc. But if you test that you can boot from the other kernels from your grub menu and then you go move the two files carefully for the latest one and try to boot from previous ones you should be ok.

The livecd entirely bypasses your installed operating system, so if you can't boot from a livecd, there are bigger problems. Could you previously boot from a livecd and now you can't? You really should test a livecd first.

---

