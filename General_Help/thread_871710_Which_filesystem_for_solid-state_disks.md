---
title: "Which filesystem for solid-state disks"
date: 2008-07-27
forum: General Help
---

### Post by thecas on 2008-07-27
I just ordered myself a computer with the new (relative cheap) OCZ solid-state disks. While waiting now on delivery I saw [a Digg item about Flash file systems]("http://digg.com/linux_unix/Anatomy_of_Linux_flash_file_systems"). Now I wonder if I should use ext3 and if this would damage the disks and how seriously. I found out that there are newer flash file systems like logfs and ubifs but I couldn't find them in mainline 2.6.26 kernel nor the ubuntu 8.10 kernel. I'm a little stuck what I should do, try to compile my own kernel with ubifs/logfs (or some other flash file system). Or just use ext3 and lack about the damage it could cause.
Also I want to put two of these disks in software Raid 0 mode but I don't think this matters.
Does anyone have some tips for me, maybe some Asus Eee users that already investigated about this matter?
[edit]
Found some information on the Eee wiki about this problem: [http://wiki.eeeuser.com/ssd_write_limit](http://wiki.eeeuser.com/ssd_write_limit)
[/edit]

---

### Post by jonian_g on 2008-07-27
Ext3 is fine. Just don't create a swap partition in the ssd. 

You can find some more info here to make disks live longer:

[http://www.ubuntu-eee.com/index.php5?title=User_Guides](http://www.ubuntu-eee.com/index.php5?title=User_Guides)

My Eeepc setup:

4GB SSD - "/"
8GB FlashCard - "/home"

I don't use a swap partition.

---

### Post by thecas on 2008-07-27
Thanks jonian_g, I the Ubuntu Eee wiki is quite helpful for this and I guess I would have setup a swap if you didn't warned me.

---

### Post by sdennie on 2008-07-27
I would personally avoid ext3 for an SSD.  If you expect the machine to be stable (which, it should be) and it has a battery, ext3 will probably not provide many benefits for you and the default 5 second commit interval is a lot of disk writes.  Alternatively, you could go with ext3 and use a guide to reduce the frequency which writes happen: [HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

