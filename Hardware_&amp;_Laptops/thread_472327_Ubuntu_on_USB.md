---
title: "Ubuntu on USB"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by jmcfadyen on 2007-06-12
I have Ubuntu loaded on my 1GB USB key.  When I boot, I have the option of selecting USB, Live, plus other options.  Live doesn't save changes., and I want to save changes for my own docs, as well as config changes ie: wireless settings... plus ie: new installed apps... and I believe that the USB startup option should do that.

When I use USB, I get an error message when logging in with the default Ubuntu userid:
(gnome session:7506) WARNING ** Unable to lock ICE authority file: /home/ubuntu/.ICEauthority.
Previous posts have suggested to use chown to fix... 
I entered the terminal session, and tried, but this did not fix problem.

Ideas welcome... thanks

---

### Post by spleencheesemonkey on 2008-02-09
I am also having this message on startup.  I am running off a 4gb usb which worked fine until i checked for updates and installed them.  Do you think this issue is due to lack of space after I ran the updates - or that a specific update has caused this error??


The message I get is:

 "The GNOME session manager was unable to lock the file '/home/<username>/.ICEauthority'.  Please reqport this as a GNOME bug.  Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is."

Any help would be greatly appreciated.

---

### Post by feest on 2008-02-20
I can confiirm this I'm facing the same problem here....

---

### Post by MacKai on 2008-04-02
im having this same error.. it started after downloading updates as well... did anyone find a fix?

---

### Post by Syke on 2008-04-02
Persistence is pretty buggy. Sometimes it works, but more than often there is a problem. Maybe Hardy will bring some bug fixes.

---

### Post by bluecaterpillar on 2008-07-22
I've been running 7.10 on a 2GB flash drive and have encountered the same problem. I tried:

```
sudo chown -R ubuntu /home/ubuntu/*
```

but no dice. Here's my workaround -- it's inelegant, but it works every time, and restores persistent mode without losing any of my customizations or files:

1. Power off completely, then reboot. When you get to the first screen, select "Start Ubuntu in Live mode".
2. (I usually do this partly in the GUI File Browser and partly in the Terminal, but do whatever works for you): Open /home/ubuntu either in the terminal or the file browser, then copy that version of .ICEauthority to the folder /media/casper-rw/home/ubuntu :

```
cp /home/ubuntu/.ICEauthority /media/casper-rw/home/ubuntu
```

3. Then get rid of any residual .ICEauthority-related files:

```
sudo rm /media/casper-rw/home/ubuntu/.ICEauthority-c
```

That should do it. Basically all that does is replace the "bad" version of .ICEauthority in the persistent partition (casper-rw) with the "good" version from the Live partition.

I've seen some other sites that recommend just writing a script to delete .ICEauthority automatically, but that's a bit over my head! Hope this helps.

---

