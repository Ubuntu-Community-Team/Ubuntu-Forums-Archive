---
title: "MANY problems 9.10 upgrade and clean install"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by tubaking182 on 2009-11-01
Ok so i have been using ubuntu for several years now and so i am very familiar with the upgrading process, and being as i do a clean install once a month i am versed in that as well. i usually make a custom image with my packages already on it so i don't have to find and download them. let's start at the top

first when i saw that 9.10 was released i decided to upgrade, i had looked around and didn't find too many bugs that would cause me major problems and figured if i was unhappy i could just throw my custom disk in and be right back to where i was before upgrading. first i decided that when it said that i should remove some packages that i would keep them and see what happens, well it finished the upgrade and rebooted still using the old 9.04 kernel (2.16 i believe), when i got to the login screen i noticed a HUGE problem, i don't have mouse functionality unless i plug in a mouse via a USB cord. so i got logged in hoping something would change after that, naturally it didn't so i booted to an earlier kernel (2.15) and same issues. 

second issue on this same upgrade was i went to the hardware drivers app and it said i should upgrade my nvidia driver and that i needed to reboot, i went ahead and let it go and upon trying to boot the process stopped and the screen began to flash. after that i was unable to boot again.

i decided it was time to throw in my cd again and fresh install my custom system, immediately after installing i upgraded all my packages to be at the same point as last time. i then started the upgrade process again, this time i let it remove my "out of date" packages even though i use many of them daily. after upgrading and rebooting i used the newest kernel first, i did have use of my mouse this time which was better so i can only assume it's a problem with some new package and the old kernel. this time though text was inverted, menus were inverted, and my wallpaper was inverted, BUT when clicking on Applications and moving down through the menu the pop-out menus acted as if nothing was inverted. to better explain click on applications on your menu, notice that Accessories is at the top and Ubuntu whatever(used to be add/remove programs) is at the bottom, in my menu that was all upside down, yet hovering over the top item brought out the accessories sub-menu(which was also upside down). i thought it was a fluke so i rebooted the computer. after reboot and login it was still the same, so i tried to boot to recovery mode and got to a black screen with a white blinking cursor and nothing more. i tried to enter a few commands and got no text on screen so i was forced to press and hold power to shut down, then i was unable to boot again. 

Lastly i decided that i was going to download a cd image and do a clean install, i downloaded it via bittorrent and burned it to a disk, after burning my program verified and all was good. when i tried to boot the cd i got the first menu(language then what to do) i tried to install and got the white blinking cursor. i decided to try to go to the "try ubuntu without changes to your computer" same result. i checked the cd for defects from the main menu and it came out fine, but i am unable to boot or install from the cd. 

i am using a laptop ASUS UX50V if you guys have any suggestions or other questions i will do what i can to help, unfortunately since i am unable to boot to my ubuntu partition i cannot provide any logs to help out.



EDIT: i decided to try installing in a virtual box from the .iso i downloaded and it seems to be working just fine, so in a generic maching using virtual intel hardware there is no problem at all, which i believe narrows it down to my video card. nVidia GeForce G105m CUDA

---

### Post by jjcv on 2009-11-01
> **tubaking182 said:**
> i am using a laptop ASUS UX50V if you guys have any suggestions or other questions i will do what i can to help, unfortunately since i am unable to boot to my ubuntu partition i cannot provide any logs to help out.

Weird.  I have never heard of this sort of problem.  You might have to do some goggling to see if anyone else with your hardware has had similar problems.   You may have to roll back to your cd copy until you get some definite answer here.   It sounds to me like an X and Nvidia problem so one thing to try is getting the specific drivers for your nvidea card from there website and trying that.

---

### Post by tubaking182 on 2009-11-01
> **jjcv said:**
> Weird.  I have never heard of this sort of problem.  You might have to do some goggling to see if anyone else with your hardware has had similar problems.   You may have to roll back to your cd copy until you get some definite answer here.   It sounds to me like an X and Nvidia problem so one thing to try is getting the specific drivers for your nvidea card from there website and trying that.

that's the other thing, i have been all over google as well as our great forums here, i have been able to logically put off individual problems as one thing or another, like the inverted text being a driver issue, but the system is almost unusable so i am unable to get a different driver, the default driver with the install seems to have done the inversion, but why wouldn't the entire screen be inverted, usually issues like that invert or rotate the screen as a whole, not the individual components. i'm not saying you are wrong just providing another question to ponder, i love riddles and such but this one has me stumped.

---

