---
title: "Ultimate way to flash BIOS with Linux and free software"
date: 2008-06-03
forum: Hardware
---

### Post by veggiebenz on 2008-06-03
I came up with a slick way to flash the bios, and thought i would share it.  Dont need windows, or MS dos.  dont need floppy drive.  DO need a CD burner and a blank CD.

Bios flashing is a risky thing, and i can't guarantee your success.  I can say that it worked for me on an ASUS board. YMMV

1) get [Ultimate Boot CD]("http://www.ultimatebootcd.com/download.html") -- dont burn the CD yet, put the ISO 
on your desktop

2)  get the BIOS flash utility for DOS and the binary data file for flashing the bios from your motherboard manufacturer.  keep this exe and bin file handy, ie on your desktop

3)  get [ISO Master]("http://www.linux.com/feature/124565")   This was in my ubuntu repositories as "isomaster" 

4)  use ISO master to open up the ISO, create a new folder in there called "bios" or something.  make sure to respect the dos 8 character limit or you wont see "bios" you'll see wacky characters instead.  put the BIOS flash EXE and BIN file in this directory, and get ISO master to save the iso -- this should all be dead simple as i figured it out within 30 seconds of downloading isomaster.

5)  now use your favorite burning tool to burn the ISO to a CD

6)  boot to the cd

7)  navigate to FreeDOS, it asks a lot of questions, just accept all the defaults

8)  select "browse" from the menu, and you will get an elementary file browser.  select your "bios" folder, and run the bios flash EXE, specifying the BIN file

9) reboot, dont forget to remove the CD

---

