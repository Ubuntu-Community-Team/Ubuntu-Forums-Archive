---
title: "installing on my WD passport"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by r0k on 2009-04-07
i am trying to install ubuntu on my WD passport and am unsure how to.  i know that i have to go into the bios at start up and change the boot priority to detachable to make my computer boot from the usb port.  What i dont understand is how to install ubuntu on my external because if my comp is booting from the usb port then how am i gonna boot from the cd drive to install?  

please help!

---

### Post by ronparent on 2009-04-07
Most current bios's will allow you to set the order of boot ie cd first, usb hard drive, hard drive, etc. If in this scheme if you have your ubuntu live cd/installcd in the cd drive, your compter will boot on it. Once you boot to the live cd either to run or install your external disk should show up if it contains unallocared space. To be sure you can choose manual partitioning and pick your disk and space to install to(by deleting an unwanted partition if necessay).

---

### Post by ChronoSphere on 2009-04-07
I used to do this all the time.

1. Attach the USB drive, and boot from the CD via the BIOS. The external USB drive doesn't even need to be formatted at this stage. It probably doesn't need to be attached either. You can also attach it in step 2.

2. During the installation choose the USB as the destination and make sure the bootloader is written to the MBR of the external drive.

3. Reboot. It will prompt you to remove the CD.

4. Now, at the BIOS screen, choose the USB as the boot device and you should be OK.

---

### Post by r0k on 2009-04-09
lol ronparent!  we are running almost the same system except mine has only 1.5 gigs of ram! but i have a 7800 gt pro graph card and my asus mb is an a8n-sli!  i dont know which you have but i thought it was kinda funny to find somone running almost the same system as i

---

