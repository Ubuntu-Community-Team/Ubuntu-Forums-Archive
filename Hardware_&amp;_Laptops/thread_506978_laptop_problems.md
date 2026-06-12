---
title: "laptop problems"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by totemg on 2007-07-22
I have recently installed Ubuntu on a laptop. I have experience with Ubuntu and i have installed it on my desktop too. I first tried installing it to the laptop with a live CD, but all i got when it booted the live CD was a whole bunch of really huge pixels(so big i could see the red, blue, and green stripes in them) and a few blinking black bars that moved up the screen. So i downloaded and burned the alternate installer and tried that. I put the CD in, booted it and everything worked fine. When i first started it, i could see all the black and white text and the Ubuntu image. But when everything was done installing and i booted from the hard drive, it showed the same thing with the pixels and the bars. So i thought maybe something got messed up in the BIOS and  it was worth a try, so I rebooted and ran BIOS, and I saw that in the video option, it was set to simul, but i didn't think i wanted that, so i set it to LCD. then i rebooted and instead of the pixels and bars, i just got a blank screen. But i could tell that Ubuntu was running because i could hear the statup sounds and even sign in but hitting tab and enter. So i called up my grandpa who knows a lot about linux and he said that it probably has something to do with X and that i should post it here. The laptop is a Dell Inspiron 2500, so hopefully someone out there can help me, because i really need this problem fixed!

---

### Post by Martin Witte on 2007-07-22
could be a videodriver issue, ry to boot in recoverymode, and run lspci - to find information on your video card

---

### Post by w4ett on 2007-07-22
Boot into "recovery mode".  From the command prompt type:
```

sudo dpkg-reconfigure xserver-xorg
```

This will give you the semi-graphical interface to reconfigure your X.  Up and Down cursor keys move cursor, <spacebar> selects, <enter> confirms selections <Esc> will skip the current page without modification.

Select the vesa driver, and then select your desired resolutions.....Skip the keyboard/mouse sections....save and quit.  then from the command prompt type:
```

startx

```

Your GUI SHOULD load.

---

### Post by totemg on 2007-07-22
it worked! thank you so much!

---

### Post by w4ett on 2007-07-22
the first part worked...Good....Now what video card/chipset do you have?...with the vesa driver does not provide 3d capability.   we can tweak your installation if you want to.

---

