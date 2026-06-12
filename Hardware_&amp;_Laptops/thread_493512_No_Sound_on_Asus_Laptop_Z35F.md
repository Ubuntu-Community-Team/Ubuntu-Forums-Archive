---
title: "No Sound on Asus Laptop Z35F"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by mrdav1e on 2007-07-05
Hello,
The install of Ubuntu 7.04 64-bit edition went great except there's no sound.  The Intel 82801G ICH7 High Def Audio Controller is installed under Device Manager.

I have tried various solutions such as changing the volume control preference to PCM from the default install CD preference.  This worked on a desktop to get sound working.
I also have tried 
   1. Edit the file /etc/default/acpid as root (e.g. sudo gedit /etc/default/acpid)
   2. You should see a line with MODULES="all" at the bottom
   3. Put a # in front of it to comment it out
   4. There's a line further up with #MODULES="battery ac processor button fan thermal"
   5. Remove the # in front to uncomment it
   6. Save the file & reboot (make sure ACPID service is enabled again, ACPI=off option removed)
except the acpi=off, I didn't know where this was located.

This is the same laptop that system76 uses for it's Darter Ultra laptop.

Please advise.
Thanks!
Dave

---

### Post by hardyn on 2007-07-05
maybe try the darters driver package?

---

### Post by mrdav1e on 2007-07-06
I installed the system 76 driver package to no avail, the graphics look better though.  I'm still seeking help with this issue.  Thanks.

---

### Post by mrdav1e on 2007-07-06
Correction to O/S, it's the 32 bit edition of 7.04, not the 64 bit edition.

Also, I tried installing Windows XP HE to see if the speakers work and they do.

I tried installing Fedora Core and FreeSpire with the same results, no sound.

I will try OpenSuse and Mandriva next.  This problem has to be solvable, I just have to figure out how to load the drivers I believe.  Thanks, Dave

---

### Post by mrdav1e on 2007-07-08
I followed these instructions in Ubuntu 7.04 i386:

1.  gksu gedit /etc/modprobe.d/alsa-base

2.  I added this line to the bottom of the file:
     options snd-hda-intel model=asus

3.  sudo rmmod snd_hda_intel  (even with no sound apps running i did receive an error msg saying the sound card was in use, i just ignored this msg)

4.  sudo modprobe snd_hda_intel

5.  Restart computer.

---

