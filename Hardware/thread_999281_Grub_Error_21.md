---
title: "Grub Error 21"
date: 2008-12-01
forum: Hardware
---

### Post by dustin_grey on 2008-12-01
I feel like an idiot for asking this. I know the problem on a basic level. You see, I installed Ubuntu 8.10 on my Dell Inspiron 1501 laptop. Installed great, runs great. However, I installed it onto my external harddrive. Now it works fine when my laptop is plugged into the external harddrive. However, if it is not, it cannot load GRUB correctly. It gives me Error 21, and I cannot boot directly into Windows.

Now from what I understand this is because I have part of grub on my internal harddrive and the other part is on the external. The solution I have found is to repair the issue using the windows CD. The only problem with that is that I don't have the CD with me. It's at home and I'm currently at school for the next 2.5 weeks. So is there a way to repair this issue without the Windows CD? Can I move the "mbr" (I believe that's it) to my external drive and avoid having to wait? It would be nice to have my laptop in class without dragging along my external harddrive. 

I would like to keep Ubuntu but I'd be fine with uninstalling Ubuntu for a cleaner install later if it comes to this. Then again, the easiest method is preferred.

Help me out please...

---

### Post by caljohnsmith on 2008-12-01
Fortunately you can reinstall a Windows MBR to your internal Windows drive from Ubuntu. Just open a terminal (Applications > Accessories > Terminal), and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
Next, you'll want to install Grub to the MBR of your external drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, set your BIOS to boot your external drive, and you should get the Grub menu. If you set your BIOS to boot the internal drive, you should be able to go straight into Windows. Also, if you want to boot Windows from the Grub menu, then first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following entry at the very bottom (or replace any existing Windows entry you might all ready have):
```
title	   Windows XP
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And if all goes well, you should be all set. Let me know how it goes or if you run into problems. :)

---

### Post by dustin_grey on 2008-12-01
You, my friend, are beautiful.

I'll try it right after work and I'll post my results tonight.

Thanks!

---

### Post by dustin_grey on 2008-12-02
Thanks so much! It worked perfectly. Took just a couple minutes to enter the proper command. This situation had me scared to death with finals week coming up. This was precisely what I was looking for.

Thanks again.

---

### Post by caljohnsmith on 2008-12-02
Glad to hear everything is working OK again. Cheers and good luck on all your finals. :)

---

