---
title: "Bios screen and grub menu do not appear"
date: 2018-02-01
forum: Hardware
---

### Post by marsdenf on 2018-02-01
I had a problem with display settings in settings manager (xubuntu 14.04).  Display mislabeled my computer monitor as my tv display, and vice versa.  (Nvidia xserver settings had it correctly labeled.) It wasn't a big problem, everything worked fine, but like an idiot I decided I would try and fix it.  After googling, read that the problem might be fixed in the bios.  So I fiddled with the bios and also changing the plugging order of the two displays.  (Graphics card has 1 dvi port and 1 hdmi port and also have an hdmi to dvi adapter) Anyway I ended up with the bios screen and grub boot menu not displaying.  (Just a blank screen).  I know that they are "there" because when delete is pressed at bootup,  the linux login screen does not appear, just blank.   When I could see the bios setup screen,  I could press right arrow key 5 times and arrive at "save changes and exit" then press enter twice and boot would resume.  When I do that with the blank screen, then the linux login screen appears after a few seconds.  Also, when I press esc repeatedly on boot up, then there is a blank screen which stays.   Then I press down arrow twice and then enter to get my preferred hard drive, and then the correct login screen appears after a moment. So the grub boot menu is there, it just doesn't show on either display. (Comp has 3 ssds, one loaded with xubuntu 14.04, other with ubuntu mate 16.04 and the other with xubuntu 16.04).  Motherboard is gigabyte z170x-gaming 3 with bios version F5m.  Graphics card is nvidia GeForce GTX 750 Ti.  The .etc/default/grub file is correctly edited to always show grub menu on bootup. 
     I have no way of seeing the bios setup screen, does anyone know some keyboard shortcuts to restore bios defaults for this mobo when the setup is there but can't be seen?  Do I have to take it into the shop so the tech can do something physically to the mobo to reset it? Any ideas?  (I am also posting this on gigabyte forums)

---

### Post by cruzer001 on 2018-02-01
I do not own one, but from what I read, it sounds fairly painless :)

[https://www.google.com/search?client=ubuntu&channel=fs&q=reset+bios+gigabyte+z170&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=reset+bios+gigabyte+z170&ie=utf-8&oe=utf-8)

---

### Post by oldfred on 2018-02-01
Did you change this setting?
> Initial Display Output
Specifies the first initiation of the monitor display from the installed PCI Express graphics card or the onboard
graphics.
IGFX  Sets the onboard graphics as the first display.
PCIe 1 Slot        
Sets the graphics card on the PCIEX16 slot as the first display. (Default)

You may just need to plug monitor into motherboard video port, not nVidia port.

I have similar Gigabyte board, but just use Intel video.
sudo dmidecode > bios.txt

>  BIOS Information

 Vendor: American Megatrends Inc.
Version: F23aSystem Information
Manufacturer: Gigabyte Technology Co., Ltd.
Product Name: Z170N-Gaming 5 



---

