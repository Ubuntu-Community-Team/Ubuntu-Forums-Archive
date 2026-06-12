---
title: "Dell Laptop Monitor Question"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by Breezy Badger on 2005-11-01
I was wondering how to get this monitor to push 1280x1024 resolution, 1024x768 is simply too big for me.  Is this easy to do, or can this monitor even push that resolution?  I do not know enough about it

thanks

Badger

---

### Post by nickj6282 on 2005-11-01
What size monitor is this? What model Dell do you have? A LCD should be run at it's native resolution all the time. If this is a 1024x768 monitor (like my Inspiron) then running it at 1280x1024 will lose you some of the screen and you'll be using the mouse to scroll around your desktop rather than being able to see it all at once.

-Nick

---

### Post by Breezy Badger on 2005-11-01
yeah that is the problem whe i put the resolution up, it wont fit all in the screen, that is no good to me, kind of a pain in the ass

it is a dell laptop latitude c600

Badger

---

### Post by nickj6282 on 2005-11-01
According to Google, the C600 has a 1024x768 or a 1400x1050 resolution. It really depends on the exact model. I would check the documentation that came with the PC to determine the native LCD resolution of this screen and run at that resolution only. If you go lower the screen will appear magnified or have black bars around it, if you go higher then you get that problem where the whole screen doesn't fit and you scroll around a lot.

---

### Post by Breezy Badger on 2005-11-01
the computer is a latitude C600 laptop, I do not have the original manual as I bought it used.  This is the problem, If i could find out the model # of the monitor I could install the proper monitor driver and see what resolutions im working with.  

right now its using the microsoft default drivers, (yes im using XP for the second, boo boo i know)

Badger

---

### Post by GoodPanos on 2005-11-01
Assuming you have the right video (not monitor) driver installed in XP, XP will give you the maximum resolution you can set your LCD to.

---

### Post by Breezy Badger on 2005-11-01
no it gives me resolutions up to 1600x1200 with a refresh of 75 hz so I know for sure this little lcd cant handle that.

Also when I set the resolution higher than 1024x768 it does not make everything smaller, it just makes the damn desktop bigger and it goes beyond the borders of the screen...its rather stupid.

Also for the default monitor it says "multiple monitors" which is sort of confusing as well.

damn laptops

---

### Post by HJThis on 2005-11-01
Hello,To all

First sorry for stepping all over your thread here but
i need to ask you,i have the same laptop i was about
to install Ubuntu on it when i happen to see this.

could you tell me please if you have a CD-ROM
on your laptop or just the floppy.

Thank you

---

### Post by Breezy Badger on 2005-11-02
> Hello,To all

First sorry for stepping all over your thread here but
i need to ask you,i have the same laptop i was about
to install Ubuntu on it when i happen to see this.

could you tell me please if you have a CD-ROM
on your laptop or just the floppy.

Thank you


I have both, I just made a post recently about problems install ubuntu on that laptop.  Please start new post, thanks

Badger

[http://ubuntuforums.org/showthread.php?t=85140](http://ubuntuforums.org/showthread.php?t=85140)

---

### Post by nickj6282 on 2005-11-02
[QUOTE=Breezy Badger]no it gives me resolutions up to 1600x1200 with a refresh of 75 hz so I know for sure this little lcd cant handle that.

Also when I set the resolution higher than 1024x768 it does not make everything smaller, it just makes the damn desktop bigger and it goes beyond the borders of the screen...its rather stupid.

Also for the default monitor it says "multiple monitors" which is sort of confusing as well.

damn laptops[/QUOTE]

It sounds like 1024x768 is your max resolution. You won't be able to use a higher resolution without extending the desktop beyond the borders of the screen. LCDs don't work like CRTs, they have one native resolution they are designed to work with and that's it. Anything smaller gets blown up and disproportioned, anything bigger and the desktop will extend beyond the borders of the screen. This is simply how LCDs are designed, so you have no choice but to use 1024x768 or deal with the oversized desktop extending beyond the screen borders.

---

### Post by Breezy Badger on 2005-11-02
thanks nick

Do you have anyway how I can find out the monitor model just so I can atleast get the drivers for it so it says my monitor instead of windows default

thanks

Badger

---

### Post by nickj6282 on 2005-11-02
Everybody's best friend Google brought me this:

[http://www.notebookparts.com/products/description.php?II=4042&f1044b](http://www.notebookparts.com/products/description.php?II=4042&f1044b)

Looks like your LCD is manufactured by Hitachi. Chances are there is no driver for it, most monitors and LCDs do not need them therefore nobody makes them. You might be stuck with "default display" as your monitor description. You may be able to change this with a registry hack or something. Google around for it and you may come up with something.

Good luck
-Nick

---

### Post by Breezy Badger on 2005-11-02
thanks so much nick

---

### Post by inigopete on 2005-12-19
The big boxy computer monitors are CRT (Cathode Ray Tube) screens.  They basically work like old TVs - an electron gun at one end of the tube fires particles down the tube at a phosphorescent (glowing) screen.  The stream of electrons is guided to scan across the screen in rows, turning on and off very, very fast to make the image appear on the screen.

Each point where it can be turned on and off (or change colour) is a single pixel.  The resolution refers to the number of pixels: 1024x768 is 1024 pixels wide and 768 high.  The maximum resolution of a CRT is mainly determined by the internal electronics that control the beam and the fine mesh on the inside of the screen: turn it on and off faster, make it scan faster across the screen and you can increase the number of pixels that can be created.

LCD screens (like in laptops) are different.  Each pixel is a tiny electronic component in itself - a big array of them is controlled by the screen's display controller circuits, but the screen is literally made up of pixels.  If your screen is 1024x768, it means it contains an array that's 1024 units wide by 768 high.  It's simply not capable of displaying a higher resolution.  It would be like trying to get your pocket calculator to display 100 numbers at a time - it physically doesn't contain the parts to do it.

This is why you get a bigger desktop when you select 1600x1200 - Windows thinks your desktop area is that size, in pixels, but you can't actually display all those pixels at once because you haven't got them in your screen.

Hope this helps.

---

### Post by noco37 on 2005-12-19
[QUOTE=Breezy Badger]thanks nick

Do you have anyway how I can find out the monitor model just so I can atleast get the drivers for it so it says my monitor instead of windows default

thanks

Badger[/QUOTE]

You can create an account at [http://support.dell.com](http://support.dell.com) and get the config. info from their site.  If you don't feel like making a Dell account just for that, let me know what the service tage number is.  It is a 7 digit alpha numeric located on the bottom of your computer by the modular bay.  Most likely your resolution is 1024x768.  That was the cheep monitor, and since the CXX series was a business series, what ever company originally bought it probably got the cheep version.

---

