---
title: "External Monitors and Hybrid graphics on Dell L502x"
date: 2014-02-01
forum: Hardware
---

### Post by thelost on 2014-02-01
Hi there,

So I have a dell xps 15 (model l502x) which has hybrid graphics with intel hd 3k/nvidia 540m gfx. 

I want to be able to use my laptop with an external monitor, via HDMI or display port. I've only tried the HDMI port so far, but with a default, clean ubuntu install it's far from obvious how to do this.

Ideally I want to be able to either extend my desktop and have dual monitors, or show my desktop on the external monitor only. 

Although I've done a lot of digging, googling, searching through these forums, info seems sketchy at best at what is currently achievable with hybrid graphics on laptops, and what you need to do to achieve a given set of results.

There seems to be a few things I need to know/understand.

1) Can I achieve these results using the Intel HD 3000 graphics adapter only?

2) Do I need bumblebee? (do I need the proprietary nvidia drivers)

3) Can I perhaps achieve the results I need using Nouveau and xrandr?

4) Where does xorg.conf come into it these days?

5) Is it possible to actually use function keys to switch monitor modes. Ie in windows the FN+F1 allows you to switch monitor mode from normal/extend/mirror/external. Can this be done in ubuntu?

6) Why is this still so hard to do (moan moan moan).

So, moan over, I'd really like to know if I can do this. If there's any further info that's needed I can provide it. As a note, I was able to get the desktop to extend using arandr so that the external monitor was acting as a second one, but the refresh rate seems extremely low, leaving cursor/window images ghosting all over the screen, like the redraw rate was extremely low. Also, checking xrandr -q shows a third input connected which makes no sense as there should only be the hdmi, the laptop's own screen, but then there's this third input with its own set of resolutions, which shows up in arandr's gui and complicates everything.

---

### Post by jp734 on 2014-02-01
I am using two video cards and a custom xorg.conf. The only difference is that I have two somewhat identical AMD video cards. So  both using the same fglrx driver. I am not familiar with hybrid graphics but I would think it's possible.

I would recommend trying to install a xrandr version 1.4 as that version supports two cards. If that doesn't work, you still can use /etc/X11/xorg.conf file but the recommended is to have a separate config files for each section (monitor, card, screen , etc....) and saved at /usr/share/X11/xorg.conf.d folder.

does it use one BusId or two (one for intel and one for nvidia)?

---

### Post by thelost on 2014-02-02
I already have xrandr as this is a fresh install of ubuntu 13.10. I tried running Xorg -configure but it baulks at my hardware and wont generate an xorg.conf.

Do you think laptop hybrid graphics and crossfire graphics cards are similar enough to be comparable? I will have to check on the BusId. As it is I am hoping there are others who have had the same problem. There must be loads of people using laptops with hybrid graphics cards.

---

### Post by jp734 on 2014-02-02
If you would like to try to solve it by using xorg.conf file, I can give you a copy of mine and edit it.

Can't really give you a comparison between hybrids and crossfire. Not familiar with any.

---

### Post by thelost on 2014-02-02
hi there

I've just managed to solve it using xrandr, but thanks for your help :)

I used the command xrandr --output LVDS1 --off --output DP1 --auto

pretty simple really. So I just put it in a file which runs on login. 

There are still a lot of questions I have about hybrid graphics, intel, nvidia, nouveau, life, the universe and everything, but I'm pretty sure that they are all easily researched and there's plenty written on them.

cheers

---

### Post by jp734 on 2014-02-02
That's great!

---

