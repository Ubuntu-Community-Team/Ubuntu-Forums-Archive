---
title: "Anyone know a way to increase screen resolution beyond what windows supports?"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by systemintheglitch on 2006-02-03
My laptop only goes up to 12xx by 7xx resolution on windows, cant remember the tens and the ones place.:confused: 


But,  I would like to know if it is at all possible to go higher than that on ubuntu.. i just need more space on my laptop, even if stuff starts to look a little wierd, i still want smaler windows/buttons/everything! 

Thanks you all..

I know there are some threads explaining how to do this, but i dont want to break anything if i add a resolution that is not traditionally supported by my monitor.


Using gnome or KDE?

---

### Post by systemintheglitch on 2006-02-12
Does anyone know of a workaround, at leaste to get some extra screen space? I want my application windows to be smaller and everything scaled down..

---

### Post by lloydkirk on 2006-02-12
You could try something like 3ddesktop.

---

### Post by systemintheglitch on 2006-02-12
I dont think that 3ddesktop alters screen resolution in the manner i wish..

Im very surprised noone has made anything that overrides your maximum screen resolution.. I heard that messing with it is dangerous though.. Maybe noone wants to risk it..

Now that i think about it.. Why would i want to risk it on my laptop lcd?

---

### Post by penvzila on 2006-02-12
Windows is probably displaying the maximum resolution that your video card can display, although I think sometimes it will check what the monitor is capable of also.

You can increase the resolution on an lcd screen all you want, but I think all it will do is give you a "scrollable" desktop (at least that's what my laptop does if I set it past the native res).

---

### Post by engla on 2006-02-12
If you have a laptop you have an LCD-type display that really has only one native resolution, and I'm pretty sure this is what Windows suggests. There is no way to "override" this and get a higher resolution, since it's a hardware limitation.

---

### Post by chele on 2006-02-12
Go to System > Preferences > Font & set the font size really small. Do the same in Firefox. 

The previous poster is correct, laptop screens (actually all LCD's) have 1 native resolution. Use that and adjust the sizes of fonts and windows seperatly.

---

### Post by penvzila on 2006-02-13
so no one else has the option of spanning above the native res? interesting.

---

### Post by systemintheglitch on 2006-02-13
The operating system should build this feature in it! Sounds like a job for ubuntu!

---

### Post by chele on 2006-02-13
> The operating system should build this feature in it!What are the advantages of using a 'pretend' screen resolution? 

Why is that better then changing the Font size?

---

### Post by lcg on 2006-02-13
[QUOTE=systemintheglitch]The operating system should build this feature in it! Sounds like a job for ubuntu![/QUOTE]
There is nothing the operating system can do.

On any LCD screen, there exist only a limited number of pixels (e.g. 1024x768 for 15", 1280x1024 on 17" and 19" and 1600x1200 on 20"). Let's assume for the moment we are using a 15" notebook screen with a resolution of 1400x1050. Let's further assume, that the OS would be sending 1600x1200 to that display (which most display subsystems will refuse to do).
The display now has two possibilities:
1) Display only a 1400x1050 area of the 1600x1200. This way, each pixel sent to the display is displayed as exactly one pixel. But everything outside the 1400x1050 area is lost, so you didn't really gain anything.
2) Scale down the 1600x1200 to 1400x1050 and display the scaled down version. In the scaling process, you map a larger amount of pixels to a lower one, effectively losing information. Again, you didn't gain anything from the higher resolution.

If you need more space, your OS' display subsystem might already be able to help you: E.g. in X you can define a virtual screen area. This is very similar to number 1 above, as the X server only sends part of that virtual area to the screen and scrolls accordingly if your mouse hits the borders of that area. (Unlike number 1 above, the outside area is not lost but can be reached via scrolling, so you did in fact gain screen space that way.)
Or you could adjust to the idea of switching between different workspaces. This does not directly give you more screen space but instead allows you to organize your programs on different workspaces.

HTH,
Lars

---

### Post by nmsmith on 2006-02-13
I have had similar screen size problems: I feel cramped using my laptop's 1024*768 screen after being spoiled by 1280*1024 on the desktop. Is there some way to tell Gnome to make everything 'smaller' (as I know the native resolution of LCDs is hard-wired) so to speak?

I.e. is there a dpi setting somewhere? I have tried the settings menu but can't find a global font change as referred to by earlier posters.

---

### Post by chele on 2006-02-13
>  I.e. is there a dpi setting somewhere?Go to the System menu > Preferences > Font > Details.

There is a resolution setting there. Try setting it down to 72 dpi, that makes everything tiny on this system.

---

### Post by nmsmith on 2006-02-13
Wow thanks! I hadn't seen the 'details' button. That's made a huge difference, pun intended.

---

### Post by stevoo on 2007-08-13
[http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/](http://www.simplehelp.net/2007/04/30/how-to-increase-the-screen-resolutions-available-to-ubuntu-while-running-in-parallels-for-os-x/)

but watch out if you monitor doesnt support it then youll have to recover like me !

---

### Post by shad0w_walker on 2007-08-13
I wouldn't recommend including this feature, outside of the native resolutions things tend to go two ways. 

A. Blurry compressed image that hurts to look at
or
B. The screen will display the part of the image that fits, the rest being off screen and inaccessible.

The reason windows has a limit on your setting is because thats as high as you monitor or graphics card will support. It is there for a reason and it is a very good one.

---

