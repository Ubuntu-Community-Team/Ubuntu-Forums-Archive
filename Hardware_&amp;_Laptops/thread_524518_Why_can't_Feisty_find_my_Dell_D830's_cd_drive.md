---
title: "Why can't Feisty find my Dell D830's cd drive?"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by christian.convey on 2007-08-13
I've got a new Dell D830 laptop, which uses Intel's Santa Rosa chipset.

I was able to install Ubuntu from the laptop's CD drive just fine.

But now that I'm running Feisty on it, Feisty can't see the CD-ROM.

When I do "ls /dev/sd*", I see sda1...sda4, which I assume is my hard drive.  But nothing like sdb*, sdc, etc.

When I do "ls /dev/hd*", just in case the cd-rom is handled by the ide driver, nothing comes up.

Does anyone know what's going on and/or how I fix it?

Thanks,
Christian

---

### Post by bjarneh on 2007-08-13
when you say feisty can't find your CD-rom do you mean that feisty can't find it, or that you can't find it in the /dev directory?
i think it's called /dev/cdrom or /dev/dvd or something like that (which is just a symlink to the actual device file) and it should be automounted when you stuff something in there....

---

### Post by jb1789 on 2007-08-13
In the terminal, type 

```
sudo gedit /etc/modules
```

and add

```
ide-generic

```
to the end of the file to get your optical drive working.

---

### Post by jb1789 on 2007-08-13
You will also need to restart your computer before you can use the drive.


JB

---

### Post by rydow on 2007-08-13
See also [http://rydow.wordpress.com/2007/08/06/getting-ubuntu-704-to-run-on-a-dell-d830/](http://rydow.wordpress.com/2007/08/06/getting-ubuntu-704-to-run-on-a-dell-d830/) where I have collected some issues had with the d830.

Jonas

---

### Post by christian.convey on 2007-08-13
> **jb1789 said:**
> You will also need to restart your computer before you can use the drive.


JB

Thanks, but a reboot isn't strictly necessary.  To make the change effective during the current booting as well, just run:
```

sudo modprobe ide-generic

```

---

### Post by christian.convey on 2007-08-13
> **jb1789 said:**
> In the terminal, type 

```
sudo gedit /etc/modules
```and add

```
ide-generic

```to the end of the file to get your optical drive working.
That did it!  Thanks!

---

### Post by Yorthegreat on 2007-08-17
Ide-generic ist not the way to go. Won't bring you dma.

So here is a shameless plug: [http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu/more-tuning]("http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu/more-tuning")

Using libata will give you full acceleration.

---

### Post by crasho on 2007-10-07
Instead of ide-generic use piix, than dma works.

crasho

---

### Post by tturrisi on 2007-10-07
I've had only a few small issues w/ a dell d830 & debian sid, dvd/cd was not one of them, it works fine.  So does compiz-fusion & cairo-dock.  My write-up here:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)

---

