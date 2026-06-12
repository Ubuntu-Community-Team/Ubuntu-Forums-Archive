---
title: "Can't start Gnome"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by SmallShoes on 2006-12-28
I have a Dell E1505 with a ATI Mobility X1400 graphics card. After setting up xorg and all that and restarting for it to take effect I can't get the screen to show up. It seems to boot fine but then the screen is black. I'm assuming this means my driver isn't working so how do I fix it?  
I'm not super familiar with CLI stuff yet so I don't really know what to do in safemode. I'm not even sure safemode is booting proprerly, at the command prompt I get when I try the ls command or dir command nothing happens. Help?!

---

### Post by bigken on 2006-12-28
if you can boot into safe mode (single user) at the prompt type **sudo dpkg-reconfigure xserver-xorg ;)**

---

### Post by SmallShoes on 2006-12-28
Thanks for the quick reply. Any tips for how I should reconfigure xorg so that the screen works? I think my native is 1680 x 1050 at 60Hz - although the first time running through xorg I put it at 1450 x something at 60Hz so you'd think it'd still work. 
I know people are having trouble with the laptop x1400 card but I don't know how to get back to however the graphics were rendering before (software I think) so that I can try configuring the driver properly.

Thanks!

---

### Post by bigken on 2006-12-28
when your prompted to select your screen res use the space bar to make your selections ;)


also select ati as your video driver

---

### Post by SmallShoes on 2006-12-30
Okay so I selected ati and it still hasn't worked. I noticed that none of my screen resolutions are listed - I have 15.4 inch widescreen lcd on my laptop so the resolutions are a little different but it's not detecting them.
Also, in the log file (I think it's the log file) I have an error at the end that says:
(EE) No devices detected.

Fatal server error:
no screens found

Help anyone?

-M

---

### Post by bigken on 2006-12-31
you could try the vesa driver this will at least get you up and running :-k

---

