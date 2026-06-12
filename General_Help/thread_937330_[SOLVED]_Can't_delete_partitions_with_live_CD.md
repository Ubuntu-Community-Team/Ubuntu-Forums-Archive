---
title: "[SOLVED] Can't delete partitions with live CD"
date: 2008-10-03
forum: General Help
---

### Post by zaponix on 2008-10-03
I installed Hardy twice -dual boot with Vista - because I didn't know there was no desktop GUI. Now I have two sets of partitions. Booted live CD with intent to use GPARTED to remove the Ubuntu partitions and start over. But can't delete the partitions as they are mounted & busy. I tried umount -a form the terminal but GPARTED still won;t allow delete. Any help gratefully appreciated.

---

### Post by caljohnsmith on 2008-10-03
Are you running gparted as the root user? For instance, by pressing ALT + F2 and then typing:
```
gksudo gparted
```

---

### Post by zaponix on 2008-10-04
Thanks, i tries gksudo gparted, but still I can't delete the partitioss, they are shown as busy when I do a 'umount -a'. Is the live cd using or mounting these partitions on drive C? How can I make them not busy?

---

### Post by caljohnsmith on 2008-10-04
Did you do:
```
sudo umount -a
```
Also, when you boot the Live CD, if it finds a swap partition on your HDD, it will typically use it. So when you are in gparted, if you right-click any swap partitions, you can choose "swapoff" so that they are unmounted. If you still have problems, can you post a screen shot of what you see in gparted? Also post:
```
sudo fdisk -lu
```

---

### Post by zaponix on 2008-10-06
Thanks for the suggestion on using swapoff and deleting the swap partitons.
I now have the 2 NFTS Vista partitions - 1 of which is the Recovery partition. There is also a /dev/sda3 partition shown as exteneded. I'm not sure if this is part of Vista and should be removed. I am not sure how to cut & paste the GPARTED screen at this point. Please let me know about the /dev/sda3 extended partition. Also thank you much for the help so far.

---

### Post by caljohnsmith on 2008-10-06
So is Ubuntu currently installed on your HDD or did you delete it? Also, what do you eventually want to accomplish--do you want to get rid of Ubuntu and just have Vista, or do you want to do a dual boot with Vista and Hardy? 

Please post the output of:
```
sudo fdisk -lu
```

---

### Post by zaponix on 2008-10-06
I want to have a dual boot with Visat & Ubuntu server. The failed times installing before was due to letting the screen with the server options slip by when I pressed [enter] and ended up with no desltop GUI. Can you tell me if there is a desktop GUI for the server?:confused:

---

### Post by louieb on 2008-10-06
> **zaponix said:**
> ... Can you tell me if there is a desktop GUI for the server?:confused:
Server doesn't come with a GUI. You can add one.
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install ubuntu-desktop    

```

---

