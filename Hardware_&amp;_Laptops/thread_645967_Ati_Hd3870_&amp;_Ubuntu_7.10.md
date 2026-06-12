---
title: "Ati Hd3870 &amp; Ubuntu 7.10"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Paladin13 on 2007-12-20
Hi!
I have a problem so I was wondering if someone can help me.
I have an Ati HD 3870 and I just instaled 7.11 Catalyst which is supposed to have Ubuntu 7.10 support.
The result is that I dont have 3d accel. I dont know why but it didn't work for me.
I did a sudo and then I executed the ATI Catalyst 7.11 driver with the sh command.
Any ideas?
Has anyone done successfully the installation?
If so..how?

---

### Post by BogusJoe on 2007-12-23
Have not tried it yet. but thinking about it.
I went ahead and got two of the 3870's and hoping someone has been able to get this to work.

---

### Post by Kingsfan on 2008-01-01
> **BogusJoe said:**
> Have not tried it yet. but thinking about it.
I went ahead and got two of the 3870's and hoping someone has been able to get this to work.

same here, mine should come in thursday...

---

### Post by rabbito on 2008-01-07
well this sucks!! not because the 3870 is not supported yet but because i have been going crazy trying to get my 3870 detected properly using 7.12 drivers. i have just been installing it using the built in installer. I tried using the specialized distribution of 7.10 gutsy but it kept saying unsupported. even after running the installer it still does not show up under restricted drivers so i may be doing something else wrong but i am not sure. If anyone here at least has the driver showing up under the restricted and you have the cat 7.12 with a 3870/3850 let me know. thanks. I just got going with Ubuntu so i am still learning but i am pretty sure i followed all of the steps correctly.

---

### Post by rabbito on 2008-01-10
Wondering if anyone has made any progress with the new ATI cards and their ubuntu setup.  Looking at the Phoronix review of the asus cards they were able to get the cards up and running but every attempt so far with installation has ended with reinstalling Ubuntu because i cant read the screen anymore and i have not figured how to restore.

---

### Post by Kingsfan on 2008-01-10
i got it running with a friend's help, using the 7.12 ATI driver, i'll have to ask my friend again exactly how we did it, but i'll report back!

---

### Post by rabbito on 2008-01-10
You lucky dog! Anyways, if you could be as detailed as you can i would really appreciate it. Do you have full functionality? I want to be able to enable the desktop effects and see what it looks like load some of my games on such as GW but not until i get the graphics worked out.

---

### Post by downhillgames on 2008-01-11
> **Kingsfan said:**
> i got it running with a friend's help, using the 7.12 ATI driver, i'll have to ask my friend again exactly how we did it, but i'll report back!
I'd be ^his friend.

Alright, here's your mini-howto that'll most certainly mess up some Xorg libs until you do pretty much just as much hassle later on (like... months from now) to correct it (but by then everyone will probably upgrade to the April release which should really OWN!).

Graphically:
First, remove the modules (don't blacklist, REMOVE):
- Open Synaptic, search for: linux-

- Sort by status (the far left thing where the shiny squares are, showing whether or not the package is installed)

- Mark For Complete Removal all of the following:
 -- Any linux-restricted-modules (even the metapackages)
**Please note** that removing these also includes **removing** various other restricted drivers. This may be bad if you rely on other drivers than the fglrx (Catalyst) driver. Read below if you use other drivers given by this package (hint: read the description).

- Search for "radeon" and "ati" (separately) and do the same for: 
 -- Any fglrx/radeon/ati -type packages (anything related to AMD/ATi Radeon graphics cards) (xserver-xorg-video-ati, radeontool, etc, etc...)

- might as well make sure "nvidia" stuff isn't installed, either :P though, obviously... anyway... they don't play nice together and yeah... just make sure ;)

- change your driver to "vesa" in xorg.conf (so where it says "fglrx" change that to say "vesa" -- alt+f2 > *gksu gedit /etc/X11/xorg.conf* OR in KDE do: *kdesu kate /etc/X11/xorg.conf*)

- reboot to _properly_ (and automatically :D) unload all the drivers and such.

- open a terminal (note: compiz and such won't be working right now... obviously...)

- cd /path/to/where/you/downloaded/the/ati.run/installer/ (like.. cd /home/downhill/Desktop/)

- chmod a+x ./ati-blah-blah-blah.run

- sudo ./ati-blah-blah.run

- follow that. self-explanatory.
Congrats! You've officially overwritten a lot the OpenGL stuff that Xorg uses! Your install is now sorta borked... but hey, 3d accel on your card will work! -- installed WinXP style, haha... without care.

- change your driver back to "fglrx"

- reboot.

enjoy.

PS: If you're using those extra drivers. Try manually removing the existing one and then installing the driver manually ("change your driver" step and onward after deleting the driver... good luck with that.  :S)

I in no way warranty this procedure. Do it at your own risk. You are, in fact, overwriting some stuff that Xorg ships with in order to attain some 3d accel. That's not the end of the world but... once "official" support arrives (via repos, that is) I highly suggest reinstalling Xorg and/or just formatting. April's release would be good timing, IMO.

peace,
-downhill


oh yeah... terminal junkies:
sudo apt-get remove linux-restricted* radeontool xserver-xorg-video-ati xorg-driver-fglrx xserver-xorg-driver-radeonhd && chmod a+x ./ati-blahblah.run && sudo ./ati-blah-blah.run
^you could get away with doing that... I suggest learning the graphical tools rather than the mess that is the CLI (command line interface)

---

### Post by rabbito on 2008-01-11
thanks a lot for that write up. I will give it a go when i have time this weekend. Hopefully you are right about Hardy giving native support for the new cards which would be nice. I do in fact use another restricted Atheros driver for my wifi card but fortunately you said how to work around that as well. thanks again.

---

### Post by Extera on 2008-01-14
Hey guy's,

I'v tried installing the drivers like discriped above, but CCC does not start when I click on it.

Anyone knows what I do wrong?

---

