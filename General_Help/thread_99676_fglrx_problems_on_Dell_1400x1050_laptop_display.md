---
title: "fglrx problems on Dell 1400x1050 laptop display"
date: 2005-12-06
forum: General Help
---

### Post by devwild on 2005-12-06
I have an Inspiron 600m with a radeon 9000 and a 1400x1050 display. Ubuntu properly detects the LCD and runs no problem with the open source ati driver. However the performance is pretty bad, lots of shearing and ghosting, and is cpu intensive, so I tried to make the fglrx drivers work. 

Following the wiki instructions (install driver via apt and switch in xorg.conf) the X server restarted at 1280x1024. The X log file indicates that the fglrx driver didn't bother to look at the resolutions set in the xorg.conf file and made up its own - 1280 pitch, resolutions 640x480 - 1280x1024. 

Since that point I've tried a dozen different configurations (diff monitors, modelines, any related option I can find, and every "fix" I can find from googling), tried fglrxconfig.... and am getting very, very frustrated. Nothing I have done has changed the behavior of the driver's detection of the resolution, nor have I found any way to force it to use what is specified in xorg.conf.

Has anyone else had similar issues? 

Thanks for any help you can provide.

---

### Post by Fittersman on 2005-12-06
ya i used easy ubuntu and it told me that when the driver selector thing came up i should select fglrx but when the selector came up it wasnt listed so then i went to the xorg.conf file and changed it manually and it just screwed up so i had to change the driver to vesa to get the graphical user interface to work but its not really the same problem just fglrx is simmilar ;)

---

### Post by devwild on 2005-12-08
No suggestions? I know I'm not the only one who's fought this based on what I've found here on the forums and google, but none of the suggested changes have changed the driver behavior at all.

---

### Post by Bachstelze on 2005-12-08
I have exactly the same problem here, but I don't really care. The performance with the vesa driver is good enough for me, I'm not a gamer :p

---

### Post by devwild on 2005-12-08
Me neither, at least not on my laptop (though the occasional open source opengl game is nice to try), I was mainly looking for improved window and video performance, and lower cpu usage (my laptop definitely gets hotter running ubuntu than windows, even though speedstep works fine. :))

One of my modeline tweaks at least improved the shearing issues by setting a better refresh with the ati open source driver. So I'm not as concerned now, but it would still be nice.

---

### Post by Bachstelze on 2005-12-08
have you ried adding a 'fglrx' line in the "Load modules" section of your xorg.conf. It inproved my perfs on Armagetron a lot :p

---

