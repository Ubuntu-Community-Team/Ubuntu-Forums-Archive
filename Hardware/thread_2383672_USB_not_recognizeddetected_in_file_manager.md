---
title: "USB not recognized/detected in file manager"
date: 2018-01-28
forum: Hardware
---

### Post by jl2414 on 2018-01-28
Hello, I'm quite new to Ubuntu.

I have a USB-stick Cruzer Edge 64 GB.
It used to be recognized/detected automatically in file manager. 
I think the problem begun when I selected the option "Do nothing" when asking about what to do when the USB-stick is inserted in the computer.
I can see the USB-stick in "Start Disc Creator" and also in "Discs".

Do I need to revert the option "Do nothing", if so how to do it?

Grateful for any help.

---

### Post by Dennis N on 2018-01-28
For Ubuntu 17.10:

Try **dconf-editor** utility. Navigate to **org > gnome > desktop > media-handling** to see the switches for the settings. **automount** and **automount-open** are turned on in initial installation.

---

### Post by jl2414 on 2018-01-28
I have Ubuntu 16.04 LTS

I do not know where to find the **dconf-editor** utility. (I did not find it in **Applications** or **System Settings**.)

How is it to be found?

---

### Post by Dennis N on 2018-01-28
> **jl2414 said:**
> I have Ubuntu 16.04 LTS

I do not know where to find the **dconf-editor** utility. (I did not find it in **Applications** or **System Settings**.)

How is it to be found?

You would need to install **dconf-editor** if it's not on your system. It's in the Ubuntu repositories. I have Ubuntu 17.10, so I can't be sure the solution applies to you with 16.04 Unity desktop. But, nothing to lose by trying.

---

### Post by jl2414 on 2018-01-29
I found out how to download it.

Quick installation of dconf-editor
**   Step 1: Update system:** 
      sudo apt-get update
**   Step 2: Install:  dconf-editor**
      After updating the OS run following command to install the package:
         sudo apt-get install dconf-editor

I tried **dconf-editor** utility, navigated to **org > gnome > desktop > media-handling** and saw the switches for the settings. **automount** and **automount-open** and thy were already turned on in initial installation.

Logged out then in again but no change.

Continue not recognize/detect the USB in the file manager.

---

### Post by Dennis N on 2018-01-29
Can you test with another USB stick to see if it mounts when inserted? Did you try using another USB port? These tests might narrow down the problem.

---

### Post by jl2414 on 2018-02-01
Problem solved...

Other USB, ext.HD and SD cards all fine so I resolved to make a partition image of the USB content and format it and then restore the partition image using Discs program.
Now the USB works as there never were a problem.

Thanks for all help and support Dennis N.

Now just to mark this thread solved. And that I don't know how to do ... :(

So is some Good Samaritan could tell me I would be grateful.

---

