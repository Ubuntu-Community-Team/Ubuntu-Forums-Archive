---
title: "Acer Aspire 7560-sb416"
date: 2013-12-09
forum: Hardware
---

### Post by britain.dunn on 2013-12-09
Hello all, i am relatively new to Ubuntu and brand new to the Ubuntu forums. I have an acer aspire 7560-sb416 that i want to make a seperate and eventual only ubuntu os machine.
The hardware is:
amd a6-3400m apu
8GB of ddr3 ram
a western digital 500gb hdd
amd radeon hd 6520g gpu
atheros ar5b97 wireless lan card
atheros ar8151 pci-e gigabit ehthernet (NDIS6.20)
Realtek hd audio
hl dt st dvdram gt32n DVD drive(whatever that is...)

i simply need help finding the linux drivers for these as i want to make a 12.04 LTS base install and update/move as necessary. ANY help you guys can provide will be greatly appreciated! Thanks in advance!

---

### Post by papibe on 2013-12-09
Hi britain.dunn. Welcome to the forum ):P

Most drivers are included on the installation DVD/USB.

The only exception would be the AMD driver which could be installed afterwards using 'Additional Drivers'.

You can test how well the drivers would work by using the installation media as a live DVD/USB. Boot into it, but instead of installing Ubuntu choose 'Try Ubuntu without installing it'. You'll get into the desktop, and there you can test the drivers (wireless networking, sound, etc).

I hope that helps. Let us know how it goes.
Regards.

---

### Post by codenine75a on 2013-12-09
If you are kiddish then try a bootable live disk first to see if it supports all your drivers before installing.

---

### Post by mörgæs on 2013-12-10
Changed the title to a more informative one.

---

### Post by britain.dunn on 2013-12-12
Ive use wubi to install it into windows and it works like a charm. the problem is is when i use a live/boot cd/usb, it only loads into a cli style environment which i think is the graphics driver issue but when i go to try to actually install the drivers i get a networking failure that looks like the driver for the nic isnt installed either. so im at a loss as to what to do. and thank you for the welcome!

---

### Post by britain.dunn on 2013-12-12
@codenine75a
Ill try that but what do you mean kiddish?

---

### Post by mörgæs on 2013-12-13
How does a live boot of 13.10 work (with wired internet access)?

---

### Post by britain.dunn on 2013-12-13
Well, this is what it did for me. I should mention that i have NOT installed anything newer than 12.04 LTS. The way I did this was I created a CD to install Ubuntu 12.04 onto my laptop. I popped the disk in, waited for everything to load up to the install. I got to where i had to format my disk and at the time i was just gonna use a dual boot system so i gave Ubuntu i think 40Gb of storage that i formatted to ext 4 i believe and from there it was just point and click i believe. In short, a live boot should be the media in which a specified operating system is installed onto a device/pc, to be cut and dry. im really good with windows but i dont know enough about Ubuntu to have a good general knowledge of how to troubleshoot linux in general. not to mention i dont usually have access to a wired internet connection. ^_^

---

