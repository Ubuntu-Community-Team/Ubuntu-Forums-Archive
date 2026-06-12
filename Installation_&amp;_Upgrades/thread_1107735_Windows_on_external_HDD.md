---
title: "Windows on external HDD"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by GabrielWolff on 2009-03-27
I know there are a couple of threads about this, but I didn't manage to apply any of the given info to my situation.

I have a WIN partition on an external HDD. Attached is the screenshot of g[arted, looking at the HDD.

What do I have to do in order to make my computer boot from the external HDD whenever it's connected?

Thanks :)

G

---

### Post by mlentink on 2009-03-27
According to Microsoft, this can't be done. I seem to remember reading about people that had done this. 
First thing to try, obviously (and you probably already did this) is to select the external hd at boot time. On my HP, you press F9 at boot time to change the boot order.

Edit: I don't see a partition flagged as boot on that drive, however, so I don't think you're in luck. How did you install Windows on that drive?

---

### Post by logos34 on 2009-03-27
> **mlentink said:**
> According to Microsoft, this can't be done. I seem to remember reading about people that had done this. 


yep

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

Whether it works as advertised is another matter.  I have yet to hear back from any forum members who have have tried it out successfully

---

### Post by GabrielWolff on 2009-03-27
> **logos34 said:**
> yep

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

Whether it works as advertised is another matter.  I have yet to hear back from any forum members who have have tried it out successfully

I read through that article. Did I understand correctly that I would have to reinstall Windows? 

I have my WIN partition on an External HDD already. Any way I can boot from that one, with only changing it slightly?

---

### Post by mlentink on 2009-03-27
Having a windows partition on a drive does not necessarily mean you can boot from it. Windows needs a boot record present and from the picture you included it does not seem you really installed windows on that drive.

---

### Post by GabrielWolff on 2009-03-27
> **mlentink said:**
> Having a windows partition on a drive does not necessarily mean you can boot from it. Windows needs a boot record present and from the picture you included it does not seem you really installed windows on that drive.

Any solution for that? Like: is there some kind of fstab for WIN I can fix?

---

### Post by mlentink on 2009-03-27
I'm afraid I don't  know Windows (XP? Vista?) well enough to give you a definitive answer on that, but I sincerely doubt it. As far as I know, Windows needs to have a mbr (master boot record) on the drive on which it is installed, which you do not have on your external. 

I really think you would have to reinstall.

---

### Post by Mark Phelps on 2009-03-28
That screenshot shows EXACTLY what a drive would look like if:
1) XP was installed first
2) Vista was installed second (which would still boot from the XP partition)
3) XP partition was deleted

Basically, if there ever WAS a boot volume on this drive, it's gone now -- and gone with it are all the boot files.

It's not a simple matter of using GParted to mark the Windows volume as boot, it's a matter of actually installing the boot files.

So, as others have said, the most straightforward way of doing this would be to reinstall windows to the external volume.  That will automatically create the boot volume and associated files.

---

### Post by Bradh616 on 2009-03-30
What if he installed a boot loader to the external drive, like Grub to the external drive?

---

### Post by Mark Phelps on 2009-03-30
> **Bradh616 said:**
> What if he installed a boot loader to the external drive, like Grub to the external drive?

From what I've read, GRUB simply hands you over to the MS Windows boot loader.  So, he would still need MS Windows boot files on the external drive.

---

