---
title: "BIOS will not allow boot from CD."
date: 2011-03-16
forum: Hardware
---

### Post by jkb609gi8 on 2011-03-16
I just purchased a new Toshiba C650D-008 Laptop. It came with Windows 7 out of the box. I downloaded Ubuntu 10.10, burnt a CD with the intention of partitioning the harddrive to a dual boot. I went into the BIOS (BIOS Version Insyde Corp 1.30 ), set it to boot off the CD/DVD drive, saved changes and exited. I tried this a couple times and realized that the changes would not remain or hold, the machine would just go back to booting off the harddrive. Next I tried F12 and enter the boot menu and the same thing happens, the machine just goes back to booting off the harddrive. Does anybody have experince with this type of problem?

---

### Post by coffeecat on 2011-03-16
It's unlikely that a BIOS cannot remember the setting to boot from a CD. Have you tried your CD in another machine? It's possible the CD didn't burn correctly and won't boot in whatever machine. Also, did you check the md5sum of the donwloaded ISO? [Link]("https://help.ubuntu.com/community/HowToMD5SUM"). It could be the ISO was corrupted in download.

---

### Post by Kirboosy on 2011-03-16
I agree with CoffeeCat, but if you still are struggling to get CDs to work you could always make a Flash Drive bootable. Guides for achieving a bootable flash drive can be found [here]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

---

### Post by jkb609gi8 on 2011-03-16
I will try a old Canonical disc (Ubuntu 9.4) I know works and try figure this out tomorrow.

---

### Post by Sina_RJ on 2011-03-16
I had this problem
I did a little dangerous thing and i just wished that it would be ok :D
I deleted boot from HDD from bios and everything just got fixed!
if you're sure about CD and your laptop I think it won't have any problems trying this,but wait for others to respond if they have a better way :)

---

### Post by jkb609gi8 on 2011-03-21
Back once again on this topic. I tried using the Canonical disc (Ubuntu 9.4) and the laptop did boot from this disc using the boot menu (F12) however I was still not able to change the booting order in the BIOS from harddrive to CD/DVD (F2).
 
I also tried downloading Ubuntu 10.10 using a bit torrent program, however the laptop would not boot from this second CD I burnt either. I hope the 10.10 program was not corupted as the bit torrent program was seeding pretty good when I got up in the morning. 
 
I sure would like to know what I am doing wrong with my downloading. I may have to load the old Ubuntu 9.4 and then try up grade from there, however it would have been faster to simply load 10.10. I find it odd that I was unable to burnt a working CD from my downloads. :confused:

---

### Post by jocko on 2011-03-21
How do you burn the cd? It has to be burnt as an image and not just by putting the .iso file on the cd and not by just copying the files from an uncompressed or mounted .iso to the cd.

Make sure you burn the cd at the lowest possible speed, otherwise part of the data on the cd may sometimes be unreadable.

If burning the cd continues to fail, why not just use a usb key instead? Both cheaper and faster (provided you already have a usb key).

---

### Post by jkb609gi8 on 2011-03-22
Yes, I have been burning the CD incorrectly. I used a different program to burn another CD, and now I am able to boot from this latest CD. :popcorn:

---

