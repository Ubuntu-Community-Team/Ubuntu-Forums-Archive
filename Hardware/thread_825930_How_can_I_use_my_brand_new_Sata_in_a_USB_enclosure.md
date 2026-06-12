---
title: "How can I use my brand new Sata in a USB enclosure?"
date: 2008-06-11
forum: Hardware
---

### Post by MichaelDBlake on 2008-06-11
I just recently bought a new drive for my dell inspiron because the old one crashed.  I know a bit about the technology I was dealing with, but not enough...I bought a sata drive instead of the ide that I needed.  I couldn't return it because of incompatibility reasons (company policy) So i just bought another one, but an IDE instead.  I worked fine...installed it and Ubuntu with no issues.  So...I bought a USB sata drive enclosure so that I could use the drive as storage.  I got it in the mail and installed it, powered it and plugged it into my computer with the usb.  It won't show up on the desktop though.  I've never done this, so I'm wondering if it is impossible to just use a brand new, blank sata as storage, without first installing something or partitioning it...  Can someone guide me in the right direction?  I've been searching through postings and google and can't find anything useful.

---

### Post by KingTermite on 2008-06-11
Does it show up when you type:
sudo fdisk -l 

If so, you may just need to mount it manually.

---

### Post by stchman on 2008-06-11
> **MichaelDBlake said:**
> I just recently bought a new drive for my dell inspiron because the old one crashed.  I know a bit about the technology I was dealing with, but not enough...I bought a sata drive instead of the ide that I needed.  I couldn't return it because of incompatibility reasons (company policy) So i just bought another one, but an IDE instead.  I worked fine...installed it and Ubuntu with no issues.  So...I bought a USB sata drive enclosure so that I could use the drive as storage.  I got it in the mail and installed it, powered it and plugged it into my computer with the usb.  It won't show up on the desktop though.  I've never done this, so I'm wondering if it is impossible to just use a brand new, blank sata as storage, without first installing something or partitioning it...  Can someone guide me in the right direction?  I've been searching through postings and google and can't find anything useful.


The reason the drive is doing nothing is that it is unpartitioned.  Once you partition it it will automount.

In Ubuntu install Gnome Partition Editor.

```
sudo apt-get install gparted
```

Once that is done launch gparted.

Select the drive from the drop down menu.  Select your partition size and file system.

If you plan on using this drive in a Windows system FAT32 is compatible with nearly every modern OS.

---

