---
title: "Keyboard killed while trying to fix touchpad on Compaq laptop"
date: 2013-02-15
forum: Hardware
---

### Post by mykdeen on 2013-02-15
running ubuntu 12.04 on compaq cq70 for about 6 months. only major problem i ever had was touchpad only worked for first 10 minutes after install. i just keep usb mouse in my bag.

while trying to fix that issue yesterday i tweaked /etc/default/grub after finding tutorial online. tweak killed my keyboard and never fixed touchpad. revert to backup didnt help.

reinstalled 12.04. then 10.04. then 8.04. then mint 14. then back to 12.04. 

usb mouse works. touchpad and keyboard totally unresponsive.

random gestures are recognized by touchpad (dash opens and open windows get closed) and keyboard works in bios. im typing this very post using a usb mouse and on-screen keyboard. plz help b/c i have to type about 10k words per week for work.

12 hrs later, this on-screen keyboard is for the birds.

thnx
-MDS

---

### Post by mykdeen on 2013-02-16
Bump. And an update:

Keyboard and touchpad still don't work on the Compaq even after an install of Fedora 7. I did notice something funny, however.
 
When installer asks what type of install (Normal, Text-Based, etc) to perform, keys and touchpad still don't work. As soon as I even touch my USB mouse, keystrokes catch up and then keyboard works fine. I'll make a selection then keyboard back to being unresponsive. 

I'm positive it is not a hardware issue but no matter how many installs I do of a wide variety of Linux installs, the problem remains. 

I'm going to get a copy of Windows 7 to temporarily install for this reason: when I first installed 12.04 on the laptop, it was a dual boot 12.04/Vista setup using WUBI. Under Ubuntu I used the WiFi button to disable wireless, only to discover it would not turn back on. When I logged into the Windows side, the button worked and Wireless resumed in both Windows and Ubuntu.

This is only the second major problem I've ever encountered w/ Ubuntu since 9.04, hence the very few posts I've made to UbuntuForums. I've always found resolutions by searching through the forums, but this problem is completely eluding me. 

While I try my recovery thru Windows, any other ideas would be greatly appreciated.
 
-MDS

---

### Post by mykdeen on 2013-02-16
I'm still hammering away at this weird problem. friend recommended using dban to wipe any weird remnant from my drive. can't because i don't have access to keyboard function. then he recommended a debian install.

thanks to some of the tools on there i am now able to get to a command line AND have keyboard function, but not too sure where to go from here. got a desktop running well enough to continue scouring the forums.

---

### Post by mykdeen on 2013-02-17
I'm writing this from the once-disabled CQ70...keyboard and touchpad working flawlessly.

That is because it is currently running the original OS of Vista along with originally shipped drivers. Even after the Windows install the touchpad was continuing to not work.

I finally flashed the BIOS using the last update directly from hp's website. after a rebooot into windows, everything works like brand new.
 
I will go ahead and mark this thread [SOLVED] but I may have to reopen this case once I get ubuntu reinstalled.

---

