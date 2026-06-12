---
title: "extend desktop on VIA S3 unichrome Pro IGP integrated graphics"
date: 2011-12-13
forum: Hardware
---

### Post by bobalazs on 2011-12-13
Im using an VIA S3 unichrome Pro IGP integrated graphics on a laptop.
I connected a 1920x1080 capable led monitor - and now got dual display -by default- but with same 1280x800 resolution.
I have read up on the subject, and there are some people who actually did configure the 1920 resolution on linux (using x perhaps) -but details were not given.
on linux-drivers.com the driver is accessible and without installation, after reading the readme file i checked if driver is present, and it is, so installing is not necessary (im using ubuntu 10.4. and its installed by default)

Let me quote one of the posts on viaarena forums: "That's because Windows drivers depend on the VGA BIOS for mode-setting support, which is embedded in the motherboard BIOS, while current Linux drivers can bypass VGA BIOS dependency."


BTw this is what i'm getting for modes:
xrandr
Screen 0: minimum 640 x 400, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       60.0     59.0  
   1024x768       75.0     60.0     70.0  
   1024x600       60.0  
   1024x576       60.0  
   1024x512       60.0  
   832x624        75.0  
   800x600        75.0     60.0     72.0     56.0  
   720x576        60.0  
   856x480        60.0  
   848x480        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        75.0     60.0     73.0  
   720x400        70.0  


Now, this is why i specifically switched to ubuntu on my laptop, since it is possible to change the resolution to 1920x1080? As i said i'm a complete newb when it comes to linux, however, this ubuntu 10.4 is not using X? Is there a guru that could help me with this problem, or perhaps refer me to an appropriate Pro user that could solve this? (maybe connect to my computer and give me help)
Thanks

---

### Post by Bucky Ball on 2011-12-13
Can't remember where it is on Gnome, if you're using that, but get to Settings>Display. There you should be able to select Screen1, set size, then select Screen2, set size. Have you tried that? I'm using Xfce and it appears that simple ... *appears* that simple!

---

### Post by bobalazs on 2011-12-13
only screen1 is available there.

In Gnome:

Monitor is : Unknown  Detect monitor doesn't work. "Same image in both monitors" - option is grayed out.
On this laptop however, once an external monitor is conected, it is cloned. But at same resolution. 1280x800 (by the way, i can't see the mouse on connected external, but flash video etc shows up on it)

I edited xconf manually to 1920x1080 and when i tried logging in it showed up with a 16 color image and stopped loading. (i fixed with recovery mode)

Is there any mode to manually add screen to some config file?

I found drivers here- if anybody want to test- or edit [http://www.openchrome.org/releases/](http://www.openchrome.org/releases/)

---

### Post by bobalazs on 2011-12-16
solved the problem with correctly setting up xconfig.
Apparently using vesa helps a lot because openchrome driver restricted me in using custom resolution.

---

