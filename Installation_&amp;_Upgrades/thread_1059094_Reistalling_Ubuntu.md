---
title: "Reistalling Ubuntu"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by mattylaws on 2009-02-03
I just want to make sure that if I am to reinstall ubuntu without formatting, it wont wipe my file, but just overwrite the system files.

I have some images stored that I don't want to lose, but I can't access them because ubuntu doesn't seem to be working, so I want to reinstall it. (It started playing up when I reinstalled windows, understandably)

---

### Post by taurus on 2009-02-03
You should be able to access your harddrive (and all your files on it) from the LiveCD.

---

### Post by mattylaws on 2009-02-03
Ok thank you, I still want to reinstall ubuntu, so my question is now: do I have to move my images before I reinstall, or can I just reinstal ubuntu without worrying?

---

### Post by Pumalite on 2009-02-03
You need a separate /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Then at installation; you go 'Manual' and pick the old Ubuntu partitions. Choose '/' and format it. Choose /home AND DON`T FORMAT IT; then continue with the installation. You can ignore /swap

---

### Post by icanfly0307 on 2009-02-03
If you install Ubuntu without backing up your files, you WILL lose them and you WONT be able to get them back...

Always, Always, Always take backups before you attempt to install or reinstall Ubuntu. So, yes, you HAVE TO copy over your images to an external storage device BEFORE you reinstall Ubuntu.

---

### Post by maybeway36 on 2009-02-03
You COULD:
1. access the hard drive from the live CD
2. delete everytihng except the "home" directory
3. unmount that partition
4. install Ubuntu to that partiton WITHOUT formatting.
It's like having a seperate /home, but you don't actually have one.

---

### Post by taurus on 2009-02-03
> **icanfly0307 said:**
> If you install Ubuntu without backing up your files, you WILL lose them and you WONT be able to get them back...

Always, Always, Always take backups before you attempt to install or reinstall Ubuntu. So, yes, you HAVE TO copy over your images to an external storage device BEFORE you reinstall Ubuntu.

Not unless you don't format the partition that you install it on.  However, it is not a good idea to reinstall on top of the older one without reformatting the partition.  But you can still install it over the old files without reformatting root filesystem--/.

---

### Post by Pumalite on 2009-02-03
I think he will need that partition to install the new system

---

### Post by mattylaws on 2009-02-03
Thank you every one for your advice. I don't think it's posible to partition the external HDD ubuntu is on, so I'll just transfer all my images over to my main internal HDD and go from there.

---

