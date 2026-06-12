---
title: "Sleep mode on Dell Inspiron 4000"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by deluded on 2007-02-11
Got 6.10 running nicely on an old Dell inspiron 4000. Only problem I've found is that when I shut the lid down, the screen doesn't actually turn off - I think it just goes into a login screen.

Also, if left for a while, the screen just goes black rather than turning the backlight off. 

I've checked all the power settings stuff, and it all looks sensible. Power saving worked fine with XP so I don't think there's any problems with the laptop.

Any ideas / patches / updates??

---

### Post by hupjack on 2007-02-11
wish I had an answer for yah, but you are further along than I am..  I was actually hoping you could take a quick peak at [http://ubuntuforums.org/showthread.php?t=358545&highlight=inspiron+4000](http://ubuntuforums.org/showthread.php?t=358545&highlight=inspiron+4000)
since we've got the same inspiron 4000.
did you have to do anything special to get as far as you've got?

Seems like I'm getting stuck around the point where the live cd should init the screen = graphics card trouble?

when you booted from the live CD, your system booted into ubuntu for you right off the bat?  no magic or voodoo required?

---

### Post by deluded on 2007-02-12
No real magic - had a problem with it locking up on bootup, but that was down to the fact I had the laptop sat on the sofa, and the wireless miniPCI card had overheated and Ubuntu was waiting for it to init.

Not managed to get the 3d acceleration working yet - would be nice for google earth.

LiveCD worked first time - I've not found a PC that it hasn't worked on yet.

Mine's got:

256MB Ram
P3-600 CPU
ATI Rage M3 gfx
Intel miniPCI wlan card


Best thing to do is to press esc on bootup, and run it in save / recovery mode (or whatever its called). Then you see what it's doing on bootup - that's how I found the wlan card problem :)

---

### Post by deluded on 2007-02-13
Interestingly..

/etc/acpi/screenblank.sh 

correctly powers off the screen until a key / mouse is pressed.

---

### Post by tbrenneman on 2007-02-17
I have the same problem, the screen will not shut off, but running /etc/acpi/screenblank.sh will turn it off.  I have a dell Inspiron 6000 with an ati x300 graphics card.

---

### Post by Benitez on 2007-02-17
[SIZE="3"]
Hey all, I see you guys have some sleep issue problems.

Not to shamelessly make a plug, but have you guys had a look **[here]("http://www.ubuntuforums.org/showthread.php?t=356054")**?

I have a Dell Latitude C610, and I had the same problem; if you guys have something fairly similar, I think that might work. 

Post up on this thread if you experience massive epic win or epic fail with the method listed.

--Benitez
[/SIZE]

---

### Post by luisito on 2007-02-20
I have an inspiron 4000 too. My screen does turn off when I close the lid. It doesn't turn off after a while though. Like yours, it just goes black without turning off the backlight. Have you been able to suspend/hibernate well? Mine doesn't do a good job on wakeup. I would try a bios update from 
[http://supportapj.dell.com/support/downloads/devices.aspx?c=tw&l=en&s=gen&SystemID=INS_PNT_CEL_4000&os=BIOSA&osl=EN#](http://supportapj.dell.com/support/downloads/devices.aspx?c=tw&l=en&s=gen&SystemID=INS_PNT_CEL_4000&os=BIOSA&osl=EN#)
but I cannot because I completely uninstalled windows. Have you ever done it? Let me know if it helps in any way. If it does I might borrow some friends computer to create the floppys.

I do have 3d acceleration working. I haven't tried google earth, but glxgears works nicely. My xorg.conf is copied in
[http://ubuntuforums.org/showthread.php?t=358545&highlight=inspiron+4000](http://ubuntuforums.org/showthread.php?t=358545&highlight=inspiron+4000)

---

