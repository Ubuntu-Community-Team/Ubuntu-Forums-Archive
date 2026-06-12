---
title: "[Help] Screen Resolutions"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by VoR # on 2007-03-21
Hey Everyone;

I've recently just put the new 6.10 Version of Ubuntu on a fresh full partition on this machine. I've had a little bit of experience with Linux, but not that much.

I have installed my NVidia glx drivers as per the HOWTO on the community support page, and when I boot into Ubuntu, my screen looks just about right (1440x900 is my native). However when I load into my environment, the screen is pushed to the left with about a 1cm wide black line on the far right of the screen. This I'm guessing is because I am using 1280x900 as my screen resolution, rather than 1440x900.

I have followed a couple of guides, editing my X Server etc, and nothing has seemed to fix my problem. Which at the moment is not being able to select 1440x900 under my screen resolutions, only 1280x1024 max. In my "Screen" section of the x server config, it has "1440x1400" as a res after the max 1280 etc, but I don't want to mess with too much without asking someone over here.

Any help would be greatly appreciated; Thanks for your time.

Sam.

---

### Post by VoR # on 2007-03-21
Bump. ;)

---

### Post by gmc1200 on 2007-03-23
Try adjusting the settings on your monitor.  When I do a fresh install, I ususally have to adjust the picture so that its not pushed to the side.

---

### Post by fede on 2007-04-01
Hello,

I think it might be that the refresh frequency is different in your login screen and in your desktop. When the frequency changes, the image is generally displaced in some direction; it happened to me some time ago, the screen mode was changing from 60 to 75 hz and that produced a shift in the image, although the resolution was the same in both modes.

I suggest you try using your monitor buttons to check the refresh rate in both screens and see if this is the case, and if so, find out how to change it - sorry, I don't remember how to do this right now but the forums must have something about it.

The quick hack is to use the auto adjust function in your screen (if present), which should put the image back to its place, although it'll be off again when you go back to the other screen

Hope it helps.

---

### Post by jjordan on 2007-04-02
Open a terminal and type
 **xrandr -q**  

that should give a numbered list of the resolutions X thinks you are capable of.  If 1440X900 is there then type:
**sudo xrandr -s x** x being the number listed beside 1440X900

More likely you will have to edit your Xorg.conf file to get the resolution you want.  I can probably walk you trough it but I will need to be at home.

-j

---

### Post by Kobalt on 2007-04-02
Try to open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.

---

