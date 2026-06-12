---
title: "Mounting External HDD on feisty?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by MadKAT on 2007-06-08
Hello

I have an external USB hard disk and it won't automatically mount on my Feisty system (upgraded) when I turn it on.  I'm able to mount it only by "pmount /dev/sda1".  This same HDD is automatically mounted on my other system which is still in Dapper.  So how do I configure Feisty to do the same? Or at least, is there a graphical tool that would let me mount?

Thanks

---

### Post by muximus on 2007-06-12
add the line on /etc/fstab... you can find a lot of howtos if you need any help doing that

---

### Post by stchman on 2007-06-12
> **MadKAT said:**
> Hello

I have an external USB hard disk and it won't automatically mount on my Feisty system (upgraded) when I turn it on.  I'm able to mount it only by "pmount /dev/sda1".  This same HDD is automatically mounted on my other system which is still in Dapper.  So how do I configure Feisty to do the same? Or at least, is there a graphical tool that would let me mount?

Thanks

Check to see if the the automount boxes are checked in the Removable devices section under Preferences.

---

### Post by MadKAT on 2007-06-13
> **stchman said:**
> Check to see if the the automount boxes are checked in the Removable devices section under Preferences.

Options:
Mount removable drives when hotplugged
Mount removable media when inserted 
Browse removable media when inserted

are all checked.  I also compared these  settings to the settings in the Dapper machine, and they are all the same.  Also, it's just the HDD that won't mount automatically. My usb CF card reader is  automatically mounted when I plug  it in.  Even an old usb gamepad works if I plug it. Any ideas?

---

### Post by Cwiiis on 2007-06-15
I also get this with one of my external hard disks, very annoying - Does anyone know much about the automatic mounting process so we can debug this?

---

### Post by abburdlen on 2007-06-15
Do you have automatix installed?  I found (with the help of many around here) uninstalling the Automatix read/write & fat32 mounter fixed my issues with my external mounting with fiesty.

---

### Post by Cwiiis on 2007-06-15
I don't even know what automatix is, and a package with that, or a similar name doesn't even seem to exist, so no, I don't think I have that installed. Like the first poster, I only have problems with one particular drive, all my other drives/keys/flash cards/etc. work fine :/

---

### Post by Cwiiis on 2007-06-15
Ah, ends up my problem was two drives with conflicting generated labels. They both wanted to be called 'WDC USB2', so only the first worked and the second failed - I'll file a bug about this.

---

### Post by MadKAT on 2007-06-24
> **abburdlen said:**
> Do you have automatix installed?  I found (with the help of many around here) uninstalling the Automatix read/write & fat32 mounter fixed my issues with my external mounting with fiesty.

I only have one external hard drive so my problem can't be that conflicting labels.

I do have Automatix installed, though. But what is "read/write & fat32 mounter" ? Did you mean uninstall Automatix?

Thanks.

---

### Post by Cwiiis on 2007-06-24
hmm, the conflicting labels problem was just a coincidence, I'm still having this problem... It seems HAL isn't making a mount method for the volume when it gets detected, but I've no idea why that would be :/

---

### Post by wildone on 2007-06-24
> **Cwiiis said:**
> hmm, the conflicting labels problem was just a coincidence, I'm still having this problem... It seems HAL isn't making a mount method for the volume when it gets detected, but I've no idea why that would be :/

use udev rules and name it something you like and then mount it.

---

### Post by dfjcms86 on 2007-06-25
I also have Automatix installed.  i also do not know what "read/write & fat32 mounter" is? and how do u uninstall it.  i am having the same problem i can see my external hard drives but i can not mount them

---

### Post by MadKAT on 2008-05-10
Hmmm... this thread has been out there for a while, and my problem persisted even after I upgraded to gutsy (haven't gone hardy yet :) ).... but anyway, I finally had the chance to move my data to a new drive, so now I am able to reformat this one to ext3. And when I did, the drive automounts now :) So what was the problem? Heck I still don't know, but it works now :)

---

