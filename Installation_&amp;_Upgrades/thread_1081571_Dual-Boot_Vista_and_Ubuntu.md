---
title: "Dual-Boot Vista and Ubuntu"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by zuyx on 2009-02-26
How do you dual-boot Vista and Ubuntu if you have ubuntu first?

---

### Post by Revo___ on 2009-02-26
Possibly you have some partitions set up.
I understand you like that:
On startup you want to either select Ubuntu or Vista.

Have you allready installed both Vista and Ubuntu.
And on startup:
Do you see a thing called 'GRUB'?

---

### Post by smani on 2009-02-26
You'll install vista, which will simply kill grub because vista thinks that it is more important, then you will have to boot a live cd and reinstall grub:
```
sudo grub
find /boot/grub/stage2
#or 
find /grub/stage2 #(if you are using a separate boot partition)

```
you will get something like hdx,y
Then:

```
root (hdx,y)
setup (hdx)# or (hdx,y) if you want to install grub to the MBR of the parition instead of the MBR of the disk
#then
quit
sudo update-grub
```

---

