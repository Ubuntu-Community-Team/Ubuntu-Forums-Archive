---
title: "Setup using Python"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by clinquist on 2009-03-17
I'm new to Ubuntu and have a program that I want to install.  The program is written in Python and exists on a USB drive.  Ubuntu sees the USB drive and the SETUP.PY file.  

I'm so used viewing drives as letters ("D:\") that I can't figure
out how (or where) to move the files onto my hard drive.  I used Konsole to get me to a command prompt, but COPY doesn't work (of course). If I use the GUI to drag the SETUP folder from the USB drive to the (C:\drive?), I get a message that the file cannot be copied. I'm obviously a DOS and Windows user. 

I have read the beginner's guide, but I can't find any reference to Python. Besides, most of the install help talks about downloading programs off the net. That won't work for me this time.  

Can someone tell me what to do?

---

### Post by noper2 on 2009-03-18
You might want to try opening the terminal in your USB folder (should be located at /media/disk or something similar) and typing:
```
sudo cp /media/disk/SETUP.PY /where/you/want/to/paste/it
```
"cp" is the command to copy and paste the file at /media/disk/SETUP.PY to /where/you/want/to/paste/it

Good luck!

---

