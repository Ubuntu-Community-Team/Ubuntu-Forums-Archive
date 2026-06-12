---
title: "how to open the .img file?"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by martinkoo on 2009-05-17
Sorry guys, I know it should be easy as sunday morning, but I begun my sunday morning with this problem: I don't know how to open the **.img** installation file / how to install the update for Ubuntu 9.04.
I could install the update through the update manager, but right now I have the desktop version 8.10, and I need to upgrade to the **netbook** remix version, and I think the upgrade manager would upgrade it to the desktop version.
I tried to open the package as a CD image, it didn't work and then I realised it isn't a cd image file..

Please ;), I know you'll know the answer directly :).

---

### Post by udippel on 2009-05-17
You write the file to a USB-drive to start from (1GB is enough). go to the main page for details, if you don't know how to do that.

---

### Post by Lampi on 2009-05-17
There is a tool to write these img images of Netbook Remix to your stick:

usb-imagewriter

You find it in ubuntu repository.

Please Remember: this destroys all data on your target partition, so be careful you choose the right target partition.

---

### Post by martinkoo on 2009-05-17
Thank you for these, I will try it when I'll have a usb in my hand, but unfortunately now I don't. And beside that, do you think

**sudo apt-get upgrade ubuntu 9.04 netbook remix**

could work for me?

---

### Post by Lampi on 2009-05-17
> **martinkoo said:**
> beside that, do you think
**sudo apt-get upgrade ubuntu 9.04 netbook remix**
could work for me?
There is some sort of howto @ the Netbook wiki site: [Ubuntu 8.10 (Intrepid) UNR Package Installation]("https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation")

But I never tried this - I always use the img file and the writer. You might be able to install the img file to a unused disk partition as well (so you don't need a usb stick).

---

