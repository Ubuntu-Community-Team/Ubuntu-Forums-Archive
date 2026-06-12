---
title: "Customise the linux installation package"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by techie_india on 2009-06-24
Hi all ,
I want to make an offline installation of Ubuntu 9.04 , making a CD /DVD . This DVD should contain the basic ubuntu version , but with some  3rd party software like :
jre - version Sun JRE 6u14
Mysql server 5.1.35 ...

While installation of the ubuntu these software also get automatically installed .

Is there anyway to customise the appearance / flash screen of the Ubuntu 9.04.

Thanks and regards
Anshuman Srivastava

---

### Post by dsavi on 2009-06-24
The Ubuntu disk comes with the Ubuntu installation compressed in a "Squashfs" file system. During installation, the contents of that file system are copied to the hard drive with the settings specified during installation set. It is a simple matter, then, for you to unsquashfs the file system, chroot into it and apt-get install the required packages.
```
$ sudo apt-get install squashfs-tools
(...)
sudo mkdir /mnt/ubuntulive
sudo mount [ubuntusquashname].sqsh /mnt/ubuntulive -t squashfs -o loop
sudo chroot /mnt/ubuntulive
sudo apt-get install [packages]

```
I don't remember where on the Ubuntu Live CD the .sqsh is located; You may have to download the ISO, uniso it and do a bit of hunting (But it isn't hard to find).

Thanks, Linux Format! :D
Edit: Oops, forgot to tell you how to squash it again.
```
$ mksquashfs /mnt/ubuntulive ubuntu.sqsh
```
Then replace the original .sqsh that was on the Ubuntu disk, ISO it and burn it and you're good to go.

---

### Post by Bucky Ball on 2009-06-24
If you're intending to sell the OS on CD I would look into the legality of doing so beforehand.

---

### Post by dsavi on 2009-06-24
^ It is legal- As long as you make the source code easily accessible and downloadable so as not to violate the GPL. (Which would also involve telling the people you're selling it to that it is freely available).

And he/she might not be wanting to sell it, just remix it- Very useful for doing multiple installations that need additional programs that don't come by default with Ubuntu.

---

### Post by Bucky Ball on 2009-06-24
> **dsavi said:**
> he/she might not be wanting to sell it

... which is why I said 'if'.

---

### Post by dsavi on 2009-06-24
Sorry, read your post wrong.

---

