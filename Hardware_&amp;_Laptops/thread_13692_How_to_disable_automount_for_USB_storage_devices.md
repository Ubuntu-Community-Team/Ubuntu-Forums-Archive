---
title: "How to disable automount for USB storage devices"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by bez on 2005-02-02
Hi all,

I need to disable automatic mounting of storage devices, connecting to USB ports (external USB HDD, MMC card reader, Flash USB storage).

AFAIK it is done by reconfiguring hotplug scripts, but HOW?

Any help is greatly appreciated. Thank you.

Alexander

---

### Post by MagisterJoe on 2006-03-09
I second this.  I've found some stuff at Mandrake and SuSE forums, but things are in different places and I cannot find them in Ubuntu.  For some external HDDs, I'd really love to turn automounting off, because when I try to use fstab to assign it to a new place, the drive just gets rerecognized as sdb instead of sda, and then all the fstabbing is useless.  Very frustrating.

---

### Post by aysiu on 2006-03-09
```
sudo apt-get remove gnome-volume-manager
```

---

### Post by jozef.kutej on 2006-11-23
> **aysiu said:**
> ```
sudo apt-get remove gnome-volume-manager
```

and the less violent is just run "gnome-volume-properties" and disable the "mount removable *" thinks.

---

### Post by Kulgan on 2006-11-23
FSTab is what controls that kind of thing. Useful guide:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by aselya1 on 2008-01-13
Uninstalling gnome-volume-manager seems really extreme... Simply turning off GVM's automounting of hot-plugged and inserted removable media would be simpler. From the Gnome Panel, click System->Preferences->Removable Drives and Media  and then uncheck the first two boxes on the storage tab. This will turn off automounting for everything not defined in /etc/fstab, and you can turn it back on if desired as easily. If you just wanted to disable automounting of certain devices you could give them their own line in /etc/fstab, making sure that the fourth field of their line include noauto so they are never automounted.

---

### Post by jessedyer on 2008-01-22
One side note; turning these options didn't change anything for me until I killed (HUP)  the **gnome-volume-manager** process.  A reboot would also do the trick, but who wants to do that?

---

### Post by super_hill on 2008-05-07
Hi, After upgrade my ubuntu to 8.04 Hardy. The "storage tab" of "gnome-volume-properties" disappeared.

I know if I change the fstab file will totally disable the automount, but the problem is I need to using "usbmount" to do the automount.

so anyone konw how to disable the gnome automount???

---

### Post by marquivon on 2008-05-14
> **super_hill said:**
> Hi, After upgrade my ubuntu to 8.04 Hardy. The "storage tab" of "gnome-volume-properties" disappeared.

I know if I change the fstab file will totally disable the automount, but the problem is I need to using "usbmount" to do the automount.

so anyone konw how to disable the gnome automount???

I found this while googling

[https://answers.launchpad.net/ubuntu/+question/30501](https://answers.launchpad.net/ubuntu/+question/30501)

---

### Post by init1 on 2008-05-17
> **marquivon said:**
> I found this while googling

[https://answers.launchpad.net/ubuntu/+question/30501](https://answers.launchpad.net/ubuntu/+question/30501)
From that page, this works for me
> 
There is a solution but you will have to enter your password every time you want to mount a removable device:
1. Press Alt+F2 and enter:
polkit-gnome-authorization
2. Go to Storage => Mount file systems from removable drivers
3. Press the "Edit..." button
4. Choose "Active Console: Authentication"
5. Press the "Modify..." button

Thanks for the link, I'm a bit surprised that they didn't make it easier to disable.

---

### Post by Thirtysixway on 2008-05-17
Maybe it's because most people don't need to disable it, makes it harder for someone to break it by accident :p!

---

### Post by super_hill on 2008-06-15
This way works for me:
gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount false

You can refer: [http://ubuntuforums.org/showthread.php?p=4823693](http://ubuntuforums.org/showthread.php?p=4823693)

---

