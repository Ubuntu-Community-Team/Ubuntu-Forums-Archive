---
title: "Mounting NTFS and Automount"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by penguinchrissy on 2006-11-02
I have both an NTFS partaion and a thumb drive that I use quite frenquently. 
I followed this guide to try and get my NTFS partition up [http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)
but when ever I try and mount it I get this error
mount: according to mtab, /dev/sda2 is already mounted on /media/windows

mount failed

which is where the drive is mounted according to my fstab but why not on mtab
I also get the same problem when I do a sudo modprobe fuse, sudo umount -a, sudo mount -a. I thought that was supposed to rewrite the mtab.

also my tumb drive doesn't automount any more I have to do it by hand :(. 

If you need a copy of my mtab and fstab I can post them let me know I just don't want to do it if not necessary.

Thanks for your help.

---

### Post by taurus on 2006-11-02
What's the output of this command from a terminal, Applications -> Accessories -> Terminal, then?

```
df -h
```

---

### Post by gerowen on 2006-11-02
I'm using Edgy and it shipped with NTFS support.  All I did was make a folder to mount it in with:
```
sudo mkdir /media/windows
```
And then I added this to my fstab:
```
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```
Of course the /dev/hda1 in mine may be different in yours, but in general that is the label for your Windows hdd.  After adding that to your fstab run:
```
sudo mount -a
```
This will mount everything in your fstab and should put your windows hdd in /media/windows

---

### Post by gerowen on 2006-11-02
Oh yeah, when adding that to your fstab, make sure to enter a carriage line after it, just press Enter to bump down one line below the last entry and that's all a carriage line is.  You can edit it with:
```
sudo gedit /etc/fstab
```

---

### Post by taurus on 2006-11-02
> **marcusdean.adams said:**
> Oh yeah, when adding that to your fstab, make sure to enter a carriage line after it, just press Enter to bump down one line below the last entry and that's all a carriage line is.  You can edit it with:
```
sudo gedit /etc/fstab
```
Actually, you want to use "gksudo" with gedit instead of regular "sudo"!

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

```
gksudo gedit /etc/fstab
```

---

### Post by gerowen on 2006-11-03
Yeah I read that a while back, I keep forgetting all about it.  In the older distros I used I rarely used sudo, I just became root full on with "su", so if I make a mistake regarding the proper usage of sudo from time to time, that's why, :p, sorry.

---

### Post by penguinchrissy on 2006-11-03
Thank you all very much for you replys everything took care of itself after I did an update I don't know what was taken care of but everything thing is working like it should! Oh and by the way I'm running Drapper Drake

---

