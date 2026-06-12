---
title: "1600x1080 resolution with Geforce 7300 LE"
date: 2008-11-27
forum: General Help
---

### Post by Kerrigans_Zerg on 2008-11-27
I have an Nvidia Geforce 7300 LE as the title says. I'm having trouble with the resolution on my fresh install of Ubuntu 8.04. My monitor's native resolution is 1600x1080, but I'd be happy with 1280x1024, right now it's set to 800x600 so everything is very large and annoying. Before posting here I searched online and ran "sudo apt-get install nvidia-glx" and "sudo nvidia-xconfig --add-argb-glx-visuals --composite" based on what I found, but it didn't seem to change anything. I'm more or less completely new to this stuff so please help.

---

### Post by mgmiller on 2008-11-27
I am assuming, as you say, that you are running 8.04 and not 8.10.  The following instructions are for 8.04 only.  This capability has been removed from 8.10 and hopefully will be restored in 9.04.....


Use this command to pop up the gui:
```
gksu displayconfig-gtk
```
then skip to instruction 5 below.

If you want to permanently add it to your menu system and then run it, do the following:


1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select "generic" at the top of the list and on the right find LCD of the correct resolution assuming it's an LCD, otherwise scroll down a bit and use Monitor of the correct resolution for CRT, or try Plug 'N Play.
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

---

