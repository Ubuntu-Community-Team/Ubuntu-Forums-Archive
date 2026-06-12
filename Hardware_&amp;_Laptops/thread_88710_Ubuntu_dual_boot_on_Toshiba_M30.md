---
title: "Ubuntu dual boot on Toshiba M30"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by daveyl on 2005-11-10
Just a quick rundown of my experience with Ubuntu Hoary and now Breezy on the Toshiba M30.

1. Install was awesome - followed dualboot instructions from Ubuntu guide and worked flawlessly. 
Quick tip - If you dualboot for the purpose of switching over from Windows, its a good idea to create one FAT32 partition on your system, so Win & Ubuntu can share it. 

2. Hardware support is fine - wireless, keyboard functions, cd, sound, video - all work as is. No special tweaks required.

3. Display had problems when in 1280x800 resolution - fonts were really fuzzy (and am currently looking for a solution to that on desktop UbuntuForums)
But a quick fix for me was to go for the 1152x768...otherwise it was great.

UPDATE (05/11/14) - FIXED PROBLEM WITH DISPLAY - search ubuntuforums for threads by daveyl on 'display fuzzy' for easy solution! - now EVERYTHING works perfectly.

4. Update from hoary to breezy was....well, breezy. Again, followed clear instructions on Ubuntu howto.

I imagine it will be only weeks before I wont need windows for anything but VB programming, and months of learning python before I wont need windows at all.

Thank you Ubuntu team.

---

### Post by nab on 2005-11-17
I want to throw in my's two cents worth :-)

I'm working on a m30x-165.

My update from Hoary to Breezy didn't run smootly, but I think that's due to too much playing around without knowing what I'm really doing :-)

In the end I saved my data and installed Breezy fresh parallelly to my win xp. Except for the need for some boot-parameters (hw_detect/start_pcmcia=false noapic nolapic acpi=off vga=790) install was without problem.

Hardware support is fine on my maschine, too  - wireless, keyboard functions, cd, sound, video, display - all worked out of the box. 

I needed some tweaks to get multiple sounds working ([http://ubuntuforums.org/archive/index.php/t-25233.html)](http://ubuntuforums.org/archive/index.php/t-25233.html)). Instead of Asla I have to use ESD. On Skype I have to find a way to get my muted micro loader (max. is set in sound mixer). [Skype problem solved: In volume settings check "Mic Boost" which boosts the signal 20db, if not there go to settings in the menu edit]

Wireless works only with 64bit WEP-key. Next project will be to get WPA working.

Well - all in all Ubuntu just works fine for my daily use.

I can only express my highest gratitude and respect to the Ubuntu team.

---

### Post by Mchipser on 2005-11-18
hello,

well i have a Satellite M35X-S149 and the install was flawless. maybe it cause i have installed various distros before and i am also dual booting with win xp. maybe one day i will be able to let go but i still need some things. since i am deployed to iraq i like to have web cam support for the instant messageing clients so i can see my familly. and maybe some more gameing but i dont really do that much. 

im still trying to figure out a way to use my media buttons on my lappy for play/pause/next/prev. maybe ill be able to use this as well.  who knows. but other than that my wireless and lan all work good. i did install suse and the screen was all jacked up but not with breezy. 

Myk3

---

### Post by daveyl on 2005-11-27
Haha - I didnt go into great detail about the 'little problems' of the install, one of them was getting the media buttons recognized...but since I didnt use them in WinXP, I wasnt too concerned with spending time getting them working in Ubuntu.

One last thing, lately I have been having some problems with GNOME power management - it seems after updating to Breezy, HAL lost some of my hardware info - and now it is really difficult to get good power management in battery mode.
Im looking at solutions now (new version of HAL maybe?), and if I get anywhere on it ill start a new post. 

PS - Mchipster - if you ever do get those buttons working, fill us in!

---

