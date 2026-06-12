---
title: "Need Help Installing Lexmark Z11 Printer"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by frankie0 on 2007-04-06
Hi, I need help installing my lexmark z11 printer. I already tried downloading the driver and I think I installed it right but my priner never worked. It doesn't do anything and the computer says it doesn't detect a printer. I use Ubuntu 6.10 Edgy. Any help is appreciated.

---

### Post by jordanmthomas on 2007-04-06
[COLOR="DimGray"][http://bbs.archlinux.org/viewtopic.php?t=10247&highlight=z600](http://bbs.archlinux.org/viewtopic.php?t=10247&highlight=z600)

I used this.  Substitute z600 for z11 and it should work about the same.[/COLOR]

Actually, if your printer isn't even detected this probably won't work.  Sorry about that.

---

### Post by jordanmthomas on 2007-04-10
> Hi thanks for the post, however I couldn't make my z11 printer to work that way also. I downloaded the file, but when I put in the command it said in the forum, my computer said it couldn't open it. Is there anything else I can do?
Which command didn't work?  I can try to "convert it to Ubuntu-ese for you." Some of those commands *won't* work, since that's the Arch Linux forums.  For example, pacman is basically apt-get, and rpmunpack may be named something different in Ubuntu.

---

### Post by ullsig on 2007-04-11
Try the driver from

[http://sourceforge.net/projects/lz11](http://sourceforge.net/projects/lz11)

Works right out of the box

Regards
Ullrich

---

### Post by jordanmthomas on 2007-04-11
> In the forum, it tells me to run the file with:
          sh z600cups-1.0-1.gz.sh -target temp_dir

I put this in and my computer tells me:
          sh: Can't open z600cups-1.0-1.gz.sh

Is this what I am supposed to do or am I supposed to put the file in some folder?

First, I'd try the link ullsig gave you since apparently it works, and I'm just guessing my way will work.

Second, as it turns out my way won't work because Lexmark doesn't even make drivers for the Z11.  I reckon I should have looked first.  :(

---

