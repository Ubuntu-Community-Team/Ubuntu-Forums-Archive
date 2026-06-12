---
title: "Um... I just killed my Grub Loader."
date: 2008-08-11
forum: General Help
---

### Post by JuBeZ on 2008-08-11
So I did a linbaku backup on one of my computers, and I thought I'd try carrying over the settings and all by restoring on another computer. Not a good idea, because the grub menu.lst as well as backup files got overwritten as well. Hmm... yeah I know I'm dumb.

I've booted from the Ubuntu disc and I have access to both drives from there, so that's relieving. I guess all I have to do now is fix the grub menu.lst to what it was originally. Does anyone know how I can get around to doing this? I'm hoping I can just change the root addresses from lets say (hd0, 5) to the proper ones, which shouldn't be too hard. But I don't know how to handle the kernel and other options. 

Thank you for any help you can throw at me

---

### Post by SkonesMickLoud on 2008-08-11
First, check if you have a backup of the menu.lst.  Do:

```
cd /boot/grub/
ls -a

```

And look for a menu.lst~ or menu.lst.bak

Then do:

```
sudo cat menu.lst***
```

If it's the same as your old one, simply:

```
sudo cp menu.lst*** menu.lst
```

If not, in a terminal:

```
sudo grub
```

This will drop you to a grub terminal.  Then:

```
find /boot/grub/stage1
```

Which should return something along the lines of:

```
(hdx,x)
```

If it doesn't, then supply the location of the partition containing your /boot in the same format.  Remember that grub numbers drives starting from 0.

Enter the above return as:

```
root (hdx,x)
```

Then:

```
setup (hdx)
```

---

### Post by sandysandy on 2008-08-11
have a look at this thread on how to install GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


other thread on how to install standalone GRUB

[http://ubuntuforums.org/showthread.php?t=880798](http://ubuntuforums.org/showthread.php?t=880798)

regards

---

### Post by mastergunner on 2008-08-12
subscribe

---

### Post by JuBeZ on 2008-08-12
Thanks for the help guys. From what you showed me, I figured out that the Ubuntu parition is (hd0,4). I tried reinstalling grub, but that didn't work because it didn't change the current settings which are screwed up. I think I'm gonna try manually editing the menu.lst file. So far i've fixed the root and kernel, but I have no clue what to put for UUID. Does anyone have a clue?

---

### Post by louieb on 2008-08-12
to get the UUID run the command **blkid**

---

### Post by JuBeZ on 2008-08-13
Thanks for the help fellas. I ended up just booting from Windows XP CD, fixed the windows boot loader (fixmgr), and then reinstalled ubuntu. Worked like a charm

---

