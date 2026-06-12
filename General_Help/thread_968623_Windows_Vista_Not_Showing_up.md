---
title: "Windows Vista Not Showing up"
date: 2008-11-02
forum: General Help
---

### Post by ECas123 on 2008-11-02
Alright so I installed Ubuntu 8.10 on my notebook and now I can't boot into it through GRUB. The Vista partition is still on the drive as you can see here.
[IMG]http://i34.tinypic.com/2jcdiyt.png[/IMG]
When I boot I see these options both the windows entrys go to a recovery page that does nothing (used to be for a recovery partition that I erased.) 
[IMG]http://i38.tinypic.com/358p01z.png[/IMG]
can someone give me advice on how to fix this?

---

### Post by tuxxy on 2008-11-02
You may need to just restore GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ECas123 on 2008-11-02
> **tuxxy said:**
> You may need to just restore GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I still see GRUB it just doesn't show me an entry to boot into windows

---

### Post by caljohnsmith on 2008-11-02
How about opening a terminal (applications > accessories > terminal), and doing: 
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title Windows Vista
root (hd0,1)
chainloader +1
```
Reboot, and let me know if that works to boot Vista; if it doesn't, let me know exactly what happens when you select it from the Grub menu.

---

### Post by ECas123 on 2008-11-02
> **caljohnsmith said:**
> How about opening a terminal (applications > accessories > terminal), and doing: 
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title Windows Vista
root (hd0,1)
chainloader +1
```
Reboot, and let me know if that works to boot Vista; if it doesn't, let me know exactly what happens when you select it from the Grub menu.
Okay, I put that in the menu file and when I selected it on GRUB I saw the Windows boot screen scroll
[IMG]http://www.johntp.com/wp-content/uploads/vista-default-boot-screen.jpg[/IMG]

Then the notebook rebooted.

---

### Post by caljohnsmith on 2008-11-02
Did you use Vista's Disk Management to resize Vista's partition, or did you use Ubuntu's partition editor? If you use gparted to resize Vista or other partitions on the HDD, it usually temporarily breaks Vista until you use a Vista Install/Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table, but gparted knows nothing about Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Install/Recovery CD.

So bottom line is, it looks like you need to fix Vista at this point. If you have a Vista Install CD, boot that and simply do the "Vista Repair" option. If you don't have a Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). That will probably be enough to get Vista booting again, but if not, let me know and we can try some other strategies. :)

---

### Post by ECas123 on 2008-11-02
> **caljohnsmith said:**
> Did you use Vista's Disk Management to resize Vista's partition, or did you use Ubuntu's partition editor? If you use gparted to resize Vista or other partitions on the HDD, it usually temporarily breaks Vista until you use a Vista Install/Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table, but gparted knows nothing about Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Install/Recovery CD.

So bottom line is, it looks like you need to fix Vista at this point. If you have a Vista Install CD, boot that and simply do the "Vista Repair" option. If you don't have a Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). That will probably be enough to get Vista booting again, but if not, let me know and we can try some other strategies. :)

kthx. So once I burn an boot it what do I do next?

---

### Post by ECas123 on 2008-11-02
can someone just tell me how I can remove the ubuntu partion and GRUB? I'll give it another go later I just want to get back into windows.

---

### Post by caljohnsmith on 2008-11-03
> **ECas123 said:**
> can someone just tell me how I can remove the ubuntu partion and GRUB? I'll give it another go later I just want to get back into windows.
Did you try doing the "Vista Repair" from the Vista Recovery CD? That may be all it takes to get Vista booting again. The problem if you remove Ubuntu and Grub now is that your Vista will most likely still have the same problem, because you've all ready changed your partitions; as I explained in my previous post, that usually temporarily breaks Vista.

---

