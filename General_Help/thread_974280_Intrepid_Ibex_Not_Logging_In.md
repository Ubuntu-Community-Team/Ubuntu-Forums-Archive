---
title: "Intrepid Ibex Not Logging In"
date: 2008-11-07
forum: General Help
---

### Post by knowmonger on 2008-11-07
I downloaded "ubuntu-8.10-desktop-i386.iso" and burned it to a CD-ROM at 1x (low speed to make sure no errors creep in). I checked it for data integrity and there wasn't any problems. 

Installation went smooth and everything was normal. But, in the log-in screen, entering my username and password gets me to a blank orange/black screen with just a mouse pointer. :confused:

Tried typing Ctrl+Alt+F1 = No response. 
Used "Recovery Mode" = Problem persists. 
Used "Failsafe-Gnome" = Problem persists.
Reinstalled Ubuntu = Problem persists. :mad:

Pls tell me how to fix this. :(

P.S: Been using Ubuntu right from Dapper. So, its not compatibility problem.

---

### Post by ronz0o on 2008-11-07
Try typing the password with all caps. It sounds like your entering a different username / password. Also, try your name as the username.

---

### Post by knowmonger on 2008-11-07
I'll try that out ASAP. I'm surprised that even if they've done a lot of "work" on this thing, it still malfunctions from the log in screen itself. 

Anyone else have anyother suggestions ?

---

### Post by phidia on 2008-11-07
Did you verify the downloaded iso by running md5sum on it?
The md5sum for the iso you downloaded should match the md5sums for the specific relase you have.

If that checks out you can try Alt+Ctrl+F2 thru F7 to get to a CLI (commnadline).

It sounds like something is wrong with x (your video driver)
If it is an xserver problem boot in recovery mode and type > xfix after that completes reboot.

Note: Typing the wrong name/password won't give you a blank orange screen. If you mistype your login info the login box jiggles and asks you to try again.

---

### Post by knowmonger on 2008-11-07
phidia, I did try xfix on Recovery Mode. It did no good. And if this md5 checksum doesn't match, is there anyway to fix this or should I download it again ?

Anyone else have solutions ? I'm getting pretty annoyed with using Windows right now. I need to get Intrepid work ASAP.

---

