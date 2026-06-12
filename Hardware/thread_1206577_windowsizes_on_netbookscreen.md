---
title: "windowsizes on netbookscreen"
date: 2009-07-07
forum: Hardware
---

### Post by toffifeemann on 2009-07-07
hey,
i just installed ubuntu on my new samsung n110, there are windows that open up too big for the screen, meaning that they are cut off at the bottom... any idea how to change this?

---

### Post by shatterblast on 2009-07-07
System -> Preferences -> Display?  Change your Resolution as desired, but if you see a timer, don't be hasty.

---

### Post by toffifeemann on 2009-07-08
the only thing i could achieve there is not using the widescreen but using the 4:3 resolution, thus giving away a part of the screen...
couldnt change anything else there...
just as an example for the problem: if i leftclick on a folder and click properties, the window that apears is too big for the screen and is cut off at the bottom. u also cant resize so you will never find out whats on the lower part unless you switch to a workspace below which is realy not ideal...

---

### Post by ugm6hr on 2009-07-08
What resolution screen do you have?

On my 9" 1024x600, the Folder Properties fits OK.

In any case: the answer is No, you can't change it, as far as I am aware.  They are Gnome presets.

You can move screens around by using Alt+Left Click.

The only program that causes problems for me on my screen is GIMP (and Inkscape).

---

### Post by toffifeemann on 2009-07-08
i use 1024x600 (16:9) on a 10.1'' and it doesnt fit... weird
maybe a possibility to make every window rezisable?

---

### Post by ugm6hr on 2009-07-08
> **toffifeemann said:**
> i use 1024x600 (16:9) on a 10.1'' and it doesnt fit... weird
maybe a possibility to make every window rezisable?

Probably because I use a single autohiding panel; the Properties box is technically not entirely on the screen, but the whole "Close" button is visible.

I suppose this is technically a bug in nautilus (and many other GTK apps).  I wonder how easy it would be to fix - I am thinking it may be appropriate for the "100 Paper Cuts" initiative.

---

### Post by toffifeemann on 2009-07-08
so i guess for now theres no solution to my problem unless i rearrange my panels...
100 paper cuts? no clue...

---

### Post by ugm6hr on 2009-07-08
> **toffifeemann said:**
> so i guess for now theres no solution to my problem unless i rearrange my panels...
100 paper cuts? no clue...

Use Alt+left click to drag any window that doesn't fit.

100 paper cuts: [https://launchpad.net/hundredpapercuts](https://launchpad.net/hundredpapercuts)

---

### Post by toffifeemann on 2009-07-08
thanks for the alt leftclick thing but it doesnt help because there are windows that cant be any smaller so they still dont fit...

---

### Post by ugm6hr on 2009-07-08
> **toffifeemann said:**
> thanks for the alt leftclick thing but it doesnt help because there are windows that cant be any smaller so they still dont fit...

Sorry, I don't understand.

Alt-Left click and drag allows you to move any window anywhere, including moving the title bar off the top of the screen.

So whatever size the window is, you will always be able to see the contents of the whole window, albeit a part at a time.

---

### Post by toffifeemann on 2009-07-08
oh i see, i thought u were talking about "Resize" not about move...
thanks then!

---

### Post by rjdaggett on 2010-03-10
I am looking for an easy way to stop gnome from being stupid totem and some other gxxx app get cut off. at lower resolutions. This is poor at best, and happens even if I change modes to 800x600 (4:3) when it should not. So this isn't just on my 1024x600 eeePC.

So I created a Xorg.conf file by suting down X, and sudo Xorg -reconfigure, and move to etc/x11/ where it should be but never was.

Then I edit this to add "virtual 1024x768" 

NOTHING ..

The eeePC apci and tray util let me use 1024x768 (compressed) but I would rather be able to scroll. The applet is poor code that breaks by Fn key bindings and screws with Video during boot and resume's.

If open solaris would add APCI suspend/resume then I'd ditch ubuntu completely. I'm sure other new users feel the same way, about their old OS unless it was windows maybe, so how do I set a virtual screen if xorg ignores the .conf ?

ANY IDEAS
[IMG]http://lh3.ggpht.com/_5G7_lBRntYM/S5gSgTIRStI/AAAAAAAABAs/R6ns86_6lhI/s640/Screenshot-1.png[/IMG]

---

### Post by stdb on 2010-07-03
There is a really fast way of changing screen resolutions and doing some other neat and nifty tricks in X without using xorg.conf. The command line tool to use is called "xrandr" - graphical user interface with all the options still not available as far as i know.

I used the following steps to get a screen size of 1024x768 on an Asus eee pc 901 with a maximum physical screen size of 1024x600. This works on Ubuntu 10.04 desktop edition and probably on earlier versions (depends on the version of xrandr).

```
user@host:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1
```LVDS1 is the builtin screen. If you have another netbook - or indeed any other hardware - the name may differ considerably. In short: always use xrandr.

To change the virtual screen size (with scrolling, or more correctly "panning"):
```
xrandr --output LVDS1 --panning 1024x768
```And to change it back - as you've probably guessed already:
```
xrandr --output LVDS1 --panning 1024x600
```xrandr can do nearly anything you can do in xorg.conf, but dynamically (no X restarting!). Find out by using "man xrandr" or "xrandr --help".

Cheers,
Stephen

---

### Post by libssd on 2010-07-03
I don't understand why you would want to use xandr. Yes, the virtual screen got bigger, but the chopped off problem was even worse with the bigger screen, as things disappeared off the top.
(Acer AA1 D150, native 1024x600)

---

### Post by stdb on 2010-07-03
> **libssd said:**
> I don't understand why you would want to use xandr. Yes, the virtual screen got bigger, but the chopped off problem was even worse with the bigger screen, as things disappeared off the top.
(Acer AA1 D150, native 1024x600)

Some programs are stubborn and don't fit their controls dynamically into the screen resolution. That's when I use xrandr to temporarily switch over to 768. I then usually get all the controls of the window. Panning around is slightly annoying but certainly less annoying than not seeing every control on a window ;)
Though I've just noticed that one of my favourite programs (sylpheed) does not have that problem any more. Certain settings windows used to be too high for 600 px.

---

