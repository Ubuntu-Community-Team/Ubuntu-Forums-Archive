---
title: "Big problem"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by olabaz on 2009-03-20
K so I had ubuntu, but I was rarely using it.  So I was on windows vista and I went to this thing and I deleted the ubuntu partition and resized my vista one to make it bigger.  Now every time I turn on my computer it's looking for the Ubuntu partition that doesn't exist.  How can I fix this?  IT says "Cannot find GRUB" or something like that.

What do i do?

---

### Post by taurus on 2009-03-20
Boot with your windows disc and fix the MBR or use Super GRUB Disk to remove GRUB from MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by dandnsmith on 2009-03-20
If you were, as I suspect, booting and getting a grub menu (till you interfered by installing ubuntu), then you overwrote the bootloader in the MBR, and need to re-establish it.

I know how to do this for Windows before Vista, but not for Vista

A quick google throws up [this advice](http://forums.techarena.in/vista-help/691963.htm) which points to a utility to do the thing, and several possibilities.

---

### Post by olabaz on 2009-03-20
> **taurus said:**
> Boot with your windows disc and fix the MBR or use Super GRUB Disk to remove GRUB from MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

K super grub seems to be my choice since I don't have the vista disk.  What do I do once I have the files on my flash drive?

---

### Post by chubble10 on 2009-03-20
just launch the vista CD, and select 'repair'

---

### Post by olabaz on 2009-03-20
I don't have a Vista CD.

Also I wrote down the error:

GRUB loading Stage1.5

GRUB loading, please wait

Error 22

I tried the memory stick and it didn't work, but I might have done it wrong.  I don't know.

---

### Post by olabaz on 2009-03-20
K I got the super grub disk working now.  Now how do I remove grub?

---

### Post by meierfra. on 2009-03-20
> I got the super grub disk working now. Now how do I remove grub? 

On the first screen, select :

Win=> MBR  & !WIN!

This  will install a  Windows type MBR and then boot Windows.

---

### Post by olabaz on 2009-03-20
This is still not fixed.  I need to remove grub or have it repaired or something.  I couldn't get the super grub disk working either. I thought I did but I was wrong. It gave me an error. What do I do???

---

### Post by meierfra. on 2009-03-20
It seems our last messages crossed in cyberspace. Did you try the method from my last post?

If that did not work, boot from the Ubuntu Live CD, open a terminal (Applications->Accessories->Terminal)

and type

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Here /dev/sda needs to be replace by the correct device name for hard drive you are booting from. It probably is /dev/sda, but you should double check via "sudo fdisk -lu"

---

### Post by olabaz on 2009-03-21
Well I didn't get to try that method meierfra.  I had fixed it yest late at night.  Thanks for the help anyway.  I think that might've worked.  What I did was download all the  ms-sys.deb files [http://ftp.debian.org/debian/pool/main/m/ms-sys/](http://ftp.debian.org/debian/pool/main/m/ms-sys/) and tried to find one that worked with ubuntu and there was one.  SO everything is sorted out.  Thanks for all the help everyone!

---

### Post by meierfra. on 2009-03-21
>  What I did was download all the ms-sys.deb
I actually used to recommend "ms-sys". But since "ms-sys" is no longer in the in the repositories, I'm now recommending "lilo -M".  Both methods  do essentially the same thing.

Anyway, I'm glad you got your problem resolved, Have fun with Vista.

---

