---
title: "82830 intel graphics driver"
date: 2008-07-07
forum: Hardware
---

### Post by NoSmokingBandit on 2008-07-07
What do i need to install to get my lappy out of low-graphics mode? Its the intel 82830 chipset. I tried the driver from intel but it says it need some kind of kernel modules, but it doesnt go into any detail so i dont know where to go.

---

### Post by overdrank on 2008-07-07
> **NoSmokingBandit said:**
> What do i need to install to get my lappy out of low-graphics mode? Its the intel 82830 chipset. I tried the driver from intel but it says it need some kind of kernel modules, but it doesnt go into any detail so i dont know where to go.

Hi and if you are using hardy 8.04 have you tried the xfix option in recovery mode from the grub? this could solve your issues because intel graphics usually work great out of the box.

---

### Post by NoSmokingBandit on 2008-07-07
I ran the xfix deal and when i booted the system it just gave me a black screen. I hit ctrl-alt-backspace and logged in via the terminal. I then typed "startx" and it gives me a really weird screwed up screen that slowly shifts color. I can still get back to the terminal though, so ill see what my xorg.conf has going on.

My xorg.conf says this (this isnt the whole thing, just the relevant parts):

Section "Device"
     Identifier     "Configured Video Device"
EndSection

Section "Monitor"
     Identifier     "Configured Monitor"
EndSection

Section "Screen"
     Identifier     "Default Screen"
     Monitor        "Configured Monitor"
     Device         "Configured Video Device"
EndSection

Section "Server Layout"
     Identifier     "Default Layout"
     Screen         "Default Screen"
     Input Device   "Synaptics Touchpad"
EndSection




Edit:
By adding the line 

Driver     "i810"

to the Device section i got her to boot into the native resolution of 1024x768. It seems to be going incredibly slow though, but for now i at least have the correct resolution.


EDIT2:
It runs sooooo slow now. The panel doesnt even show up, but i can open Nautilus from the desktop. Any ideas?
Actually, Nautilus seems to be the only app that open up in a resonable amount of time. I chose to "create a launcher" on the desktop (the only way i can open any programs atm) and it took about 1 minute for the dialog to pop up.

---

### Post by overdrank on 2008-07-07
How much memory does the system have? You could check and see how much is shared by the graphics.

---

### Post by NoSmokingBandit on 2008-07-07
The machine has a whopping 128mb ram, but the bios doest have any option to change how much is shared.
Meh, maybe this laptop just wont play nice with linux. Kinda sucks, but you cant expect perfection form a community-maintained OS.

---

### Post by overdrank on 2008-07-08
> **NoSmokingBandit said:**
> The machine has a whopping 128mb ram, but the bios doest have any option to change how much is shared.
Meh, maybe this laptop just wont play nice with linux. Kinda sucks, but you cant expect perfection form a community-maintained OS.

Well not when the system is below the minimum requirements. :)

---

### Post by NoSmokingBandit on 2008-07-08
The peculiar thing is that PCLOS worked great on it. I just really dont like RPM distros so i tried to make a switch...

---

### Post by overdrank on 2008-07-08
> **NoSmokingBandit said:**
> The peculiar thing is that PCLOS worked great on it. I just really dont like RPM distros so i tried to make a switch...

I understand as I like mandriva but that is what keeps me from fully switching. Which I think I would never really give up on Ubuntu. 
Edit and I have always had better luck with the i810 driver and you may try and use the command ```
gksu displayconfig-gtk
``` and select the i810 driver and also I have heard that Hardy 8.04 does not need the 915 resolution but I always install it maybe as of habit.

---

