---
title: "Unable to mount VERBATIM Error mounting: mount: unknown filesystem type 'exfat'"
date: 2011-10-14
forum: Hardware
---

### Post by jcer93705 on 2011-10-14
Hi I have a usb verbatim 1gb usb drive. It says. Unable to mount VERBATIM Error mounting: mount: unknown filesystem type 'exfat' . 

What next?

---

### Post by WasMeHere on 2011-10-14
Hi jcer93705

I have not tried it myself yet, but there is a remedy on the internet. See the following thread
[[COLOR="RoyalBlue"]_http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm_[/COLOR]]("http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm")

Have fun finding out about Ubuntu :-)
Olle

---

### Post by jcer93705 on 2011-10-15
> **Olle Wiklund said:**
> Hi jcer93705

I have not tried it myself yet, but there is a remedy on the internet. See the following thread
[[COLOR="RoyalBlue"]_http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm_[/COLOR]]("http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm")

Have fun finding out about Ubuntu :-)
Olle

Doestwork

---

### Post by WasMeHere on 2011-10-15
> **jcer93705 said:**
> Doestwork
Then there are two options

- Try to find something that works in Ubuntu. I can't help you, but with a little bit of luck, someone who knows will post a helpful reply.

- Resort to reading and maybe copying the contents in Windows (or Mac) and after that consider if it would be worthwhile to reformat the drive to something readable in most computers. Since it is only 1 GB, there is no problem with FAT32.

---

### Post by alessandrofranca on 2011-10-21
Hello!

I found the link bellow and works fine!

[http://www.tannerjepsen.com/posts/exfat-fuse-module-for-ubuntu-with-readwrite-support](http://www.tannerjepsen.com/posts/exfat-fuse-module-for-ubuntu-with-readwrite-support)

Thks,

Cleofas.

---

### Post by SycloneMedia on 2011-12-06
> **Olle Wiklund said:**
> Hi jcer93705

I have not tried it myself yet, but there is a remedy on the internet. See the following thread
[[COLOR="RoyalBlue"]_http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm_[/COLOR]]("http://apcmag.com/how-to-enable-exfat-in-ubuntu.htm")

Have fun finding out about Ubuntu :-)
Olle

Awesome! Thank you...

for those of you saying it doesn't work, make sure you apt-get update before you add the repo, and then again after you add the repo... it works fine!

---

