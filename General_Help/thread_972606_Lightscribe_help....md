---
title: "Lightscribe help..."
date: 2008-11-05
forum: General Help
---

### Post by Prominence on 2008-11-05
I've installed the system software and the labeler, but I don't see it anywhere, what do I do? (used the deb packages from the site)

---

### Post by simtaalo on 2008-11-05
try alt+f2 and type name of the program in, it should autocomplete before you finish keying it in.

---

### Post by Prominence on 2008-11-05
Still nothing. Tried typing "lightscribe" and everything close to it and nothin'

---

### Post by simtaalo on 2008-11-05
whats the program called?

---

### Post by Prominence on 2008-11-05
I presume it would be Lightscribe System Software, and Lightscribe Labeler.

---

### Post by simtaalo on 2008-11-05
what was the name of the deb file?

not necessarily going to be called what you think

---

### Post by Prominence on 2008-11-05
lightscribe-1.14.3.2.1-linux-2.6-intel.deb

and 

lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

---

### Post by em007a on 2008-11-07
As far as I know, you need the 4l-gui or 4l-cli in order to use lightscribe.
 I found them here: [http://www.lacie.com/support/drivers/index.htm?id=10011](http://www.lacie.com/support/drivers/index.htm?id=10011)

I had to convert the .rpm's to .deb using alien.

Your versions are newer. Where did you find those versions?

---

### Post by Captain_Falafel on 2008-11-08
I have 4L-gui up and running along with my external USB Samsung lightscribe drive.. but when I get an image and hit print, I get an error that says "You need to select a drive before you can print." There is a place where I can select drives, but it's grayed out. Is there any way to get this working?

---

### Post by salingova on 2008-11-19
I got to the same page as you, and now when I try to print it does the same thing; wants me to choose a drive, but it is grayed out. Is there anybody who knows what to do?

---

### Post by andrew.mckevitt on 2008-11-25
I got the same problem when I moved up to feisty, the problem is a old missing c library, if you open a terminal and type 

sudo 4L-gui

you'll see it fails to find it.

Open synaptic and search for libstdc++5, mark and apply the changes.
Lightscribe should work now. Please note that you do need to use sudo to run this software.

If you want to create a launcher use

gksu 4L-gui

as the command instead. This will open up a window in gnome asking for your password.

Happy burning.

---

### Post by salingova on 2008-11-25
thank you my friend, it works

---

### Post by andrew.mckevitt on 2008-11-25
> **salingova said:**
> thank you my friend, it works

I try and steer clear from the terminal, but it can be very useful, if you're having problems with applications not starting or running correctly, start them in a terminal and read the output, can save you a lot of time on the forums and google.

---

