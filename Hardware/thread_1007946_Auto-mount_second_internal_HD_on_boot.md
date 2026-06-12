---
title: "Auto-mount second internal HD on boot"
date: 2008-12-10
forum: Hardware
---

### Post by dwieeb on 2008-12-10
Hi I've been following this article: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

But right away I get a 404 error while typing the following script into the terminal:
```
cd
wget http://media.ubuntu-nl.org/scripts/diskmounter
```

So I guess I need a diskmounter script wherever I may find one?

My OS is Ubuntu 8.10.

Sorry I posted in this forum but apparently I don't have access for the General Help forum. >.>

---

### Post by 2hot6ft2 on 2008-12-11
Applications>System Tools>NTFS-Configuration Tool

If it's not there then install it in System>Administration>Synaptic Package Manager by searching for ntfs-config and install it.

Make sure the drive you want to auto mount is UNMOUNTED then open up the NTFS-Configuration Tool then select the drive you want and click Apply in the next window select enable write support and click OK. All done

Now it will auto mount with read/write support after you reboot.

---

### Post by dwieeb on 2008-12-11
NTFS Config doesn't seem to work. All that pops up is the attached file. Nothing else happens no matter what I choose

---

### Post by dwieeb on 2009-01-04
Eh..?

---

### Post by leftoflexo on 2009-07-01
yeah, i have the very same problem. i installed ubuntu 9.04 2 days ago, and ive been having the same problem. i start the ntfs configuration tool and it just shows me that start screen for the program and when i hit okay to get past it and let the program start it closes out and nothing happens...................

---

