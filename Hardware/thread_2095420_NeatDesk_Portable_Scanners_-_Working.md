---
title: "NeatDesk Portable Scanners - Working"
date: 2012-12-16
forum: Hardware
---

### Post by venuspcs on 2012-12-16
Okay so first let me say I am not a Linux Guru or Driver Geek....I just figured this out by trial/error and lots of reading. I have a Neat Portable Scanner model NR-030108 but this should work for most if not all versions of the Portable Scanner.

Step 1: Download firmware for the scanner from [here]("http://gkall.hobby.nl/cism216.fw") and place it in /usr/share/sane/gt68xx folder - You may have to make the gt68xx folder (I did). To do this open terminal and type:

sudo nautilus /Enter your password and press enter
browse to home/yourusername and copy the cism216.fw to clipboard then browse to /usr/share/sane/gt68xx and paste

Step 2: from terminal type:

sane-find-scanner -v -v

You will have to scroll up a while to find your scanner but when you do find the line that says something like:

device descriptor of 0x07b3/0x0412

Note those two hex codes you will need them in step 3


Step 3: from terminal type sudo gedit /etc/sane.d/gt68xx.conf
At the end of the file add the following lines:

##############################################################################
# Autodetect Plustek OpticSlim M12 and NeatReceipts Scanalizer Professional 2.5
usb 0x07b3 0x0462
override "plustek-opticslim-m12"
#vendor "NeatReceipts"
#model "Scanalizer Professional 2.5"
##############################################################################

Change the two hex codes above to match the ones you got from the sane-find-scanner above.

Then save the file and quit gedit. Now from terminal type:

scanimage -T / Load a piece of paper in first and it should do a test scan.

If it shows a bunch of PASS lines then type:

simple-scan

Go to Document/Preferences and set DPI to 300

For some reason I haven't figured out yet anything lower than that results in BLUE PAGES. You are now ready to scan.

---

### Post by aleblanc2 on 2013-07-31
Nice work!!

---

