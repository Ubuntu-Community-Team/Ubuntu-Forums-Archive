---
title: "nVidia Quadro Driver on D830"
date: 2008-04-28
forum: Hardware
---

### Post by qusai.alhaddad on 2008-04-28
Dear All, 
I have Installed Ubuntu 8.04 in my Dell Latitude D830, i face a problem with Video and Sound. Do any one  know from where i can download these drivers, My VGA is nVidia Quadro NVS 140M.


Thanks Indeed, 

QA

---

### Post by Mit kebes on 2008-04-28
do you get the same problem when running other operating systems?

---

### Post by qusai.alhaddad on 2008-04-29
With Fedora, Redhat, FreeBSD, works fine, and crapy Vista.

---

### Post by marc_spafford@hotmail.com on 2008-05-08
If have the NVS 135 Quadro i use the new Beta drivers from Nvidia to run on my Ubuntu 8.04 hardy. It seems to work great and i can use all the awesome desktop effects.

---

### Post by phelps on 2008-05-18
Go here to download the drive that works for the Quadro NVS cards.
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

You will need to turn off xserver. open a terminal window and type:
sudo apt-get install rcconf  (enter your password when prompted)
sudo rcconf

You should see a gui in the terminal. Use the arrow keys to go down to "gdm" and click the spacebar to unselect it. Then restart. You will now be in terminal mode with no gui. cd to the dir where you downloaded the driver and type:

sudo sh NVIDIA-Linux-x86-169.12-pkg1.run

After this install, go back to rcconf and re-check "gdm" and restart.

---

