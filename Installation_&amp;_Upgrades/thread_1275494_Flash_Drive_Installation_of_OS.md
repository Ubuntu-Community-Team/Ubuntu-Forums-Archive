---
title: "Flash Drive Installation of OS"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by ahr8tch on 2009-09-25
I want to install Ubuntu KK on an Asus 900SD.  From what I've seen on the Ubuntu support page, I should be able to install the netbook remix.  The problem is that I can't find any instructions that tell me how to do so (that I understand).  I want to install Ubuntu because the distro on the Asus doesn't provide a way for me to get to a terminal so I can't install software that I need (primarily Citrix client).

I downloaded the ubuntu-9.04-netbook-remix-i386.img file using my windoze laptop.  I bought a new 8GB USB flash (thumb) drive today.  Can I just copy the downloaded file to the flash drive?  Somehow that seems far too easy.

I found what I hoped would be instructions I could follow at [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

The information assumes that the IMG files were downloaded on a Linux system and instructs to install a Linux program to deal with the IMG file.  These instructions don't fit my pistol.

If I DO copy the nearly 1GB IMG file to the flash drive and plug it into the Asus netbook, I don't know how to proceed.  Apparently the distro that is installed on the Asus does NOT have the ability to go to terminal.  (There is no TERMINAL icon under ACCESSORIES.)

If someone could point me to the kind of specific information I need for the ASUS and the netbook distro, I would be eternally grateful.

---

### Post by clonne4crw on 2009-09-25
No, you cannot simply copy the .img file to your flash drive. It is an image of an entire drive, and inside it is the filesystem + boot sector, etc for installation. It is like a .iso for a CD.

To install this, you use the command:
```

# dd if=/dev/(flash drvie) of=/path/to/.img

```

Tell me how it goes :popcorn:

---

### Post by ahr8tch on 2009-09-25
> **clonne4crw said:**
> No, you cannot simply copy the .img file to your flash drive. It is an image of an entire drive, and inside it is the filesystem + boot sector, etc for installation. It is like a .iso for a CD.

To install this, you use the command:
```

# dd if=/dev/(flash drvie) of=/path/to/.img

```Tell me how it goes :popcorn:

Thanks for the response!

I can't get to a terminal in the distro that's on the Asus.  Is there another way to enter the recommended command?

---

### Post by clonne4crw on 2009-09-25
Hmmmm. That's one thing that REALLY pisses me off with these netbook distros. They try to hide the fact that it's linux.

Try ALT + F1 to try to escape Xorg and go to a TTY. Unforunatley, many netbook manufacturers disable this for some odd reason.

Or, you could open up a file browser and go to /usr/bin/xterm , and open that. I would try this first.

---

