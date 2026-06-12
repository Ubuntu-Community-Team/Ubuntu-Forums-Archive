---
title: "Where's ms-sys?"
date: 2008-07-23
forum: General Help
---

### Post by gatoz on 2008-07-23
I need to restore the bootloader for vista, ms-sys worked before so i try it now, but the terminal tells me that it can't find it, and i've enabled universal repositories.

---

### Post by Joeb454 on 2008-07-23
Hmm, doesn't look like it's in the repo's ```
apt-cache search ms-sys
``` returned nothing...

Do you have a Vista disc (disk?)

---

### Post by gatoz on 2008-07-23
no,wonderful Acer decided to give me a recovery partition which no longer works.

---

### Post by Joeb454 on 2008-07-23
You could download it from sourceforge.

It can be found here: [http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)

Though you may need to compile it yourself

---

### Post by louieb on 2008-07-23
Wondering too why Ubuntu repositories don't have it. Maybe because Ubuntu is based on Debian unstable. Seems Debian has it in its stable branch. [http://packages.debian.org/search?keywords=ms-sys](http://packages.debian.org/search?keywords=ms-sys)

Just found the why. 
[Why ms-sys was removed on hardy?]("https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349")
Seem some licensing issue with MS

---

### Post by LaRoza on 2008-07-23
> **gatoz said:**
> I need to restore the bootloader for vista, ms-sys worked before so i try it now, but the terminal tells me that it can't find it, and i've enabled universal repositories.

You can always use the super grub disk for that. See the link in my sig.

---

### Post by leorolla on 2010-03-11
Sometimes SGD doesn't load. Its forum is locked. There are no official instructions to make an SGD USB without grub legacy installed.

On the other hand,

Here is one simple way around ms-sys:
[http://ubuntuforums.org/showthread.php?t=1009707](http://ubuntuforums.org/showthread.php?t=1009707)
and here are two other:
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
```
sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/sda

```
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```

In the last solution, installing syslinux is not even important.
What is important is this 512kb file called mbr.bin

---

