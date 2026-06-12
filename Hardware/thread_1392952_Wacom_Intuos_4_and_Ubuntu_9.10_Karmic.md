---
title: "Wacom Intuos 4 and Ubuntu 9.10 Karmic"
date: 2010-01-28
forum: Hardware
---

### Post by ilcontegis on 2010-01-28
Guys, I have a really really big confusion...on this forum as on the net, everything is so messed up....do this if you have jaunty, do that if you have karmic, don't do this if you have the bamboo, do that and this if you have the intuos 3 but not if you have the intuos 4.....

I would really appreciate if somebody could be so nice to tell me what should I do for my case. Please.

I have Karmic and a intuos4. The tablet is recognized by ubuntu, but is without any configuration. The pressure is working, but no eraser, and all the buttons (and the led screen) are not working.

Please tell me what should I do, In many guides they say that with the intous4 I should not configure anything (if I try nothing work anymore)....ok but, how can I make it work properly?

The oled screens as well are not working

Thank you very much for your kind attention

---

### Post by Favux on 2010-01-28
Hi ilcontegis,

The OLED's don't work with the default 0.8.4-1 linuxwacom in Karmic.  Do not try to compile 0.8.5-9!  Keep the default linuxwacom.  Although a patch to support OLED's was supposedly added to 0.8.5-8 no one has gotten it to work.  Hopefully they will work in Lucid.

First in Synaptic Package Manager both xserver-xorg-input-wacom (it will be) & wacom-tools are installed.

Use the first or third .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  If something goes wrong you can restore the original .fdi from the backup.

Then follow the link in post #176 to set up wacomcpl (the Wacom Control Panel).  That should give you your stylus buttons and tablet buttons.

The eraser only works in certain programs.  To set it up for Gimp and Inkscape see near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by ilcontegis on 2010-01-29
For now I am using this commands

```
# flip to lefthanded mode (for my honey)
#xsetwacom set 'Wacom Intuos4 6x9' rotate HALF # don't touch
#xsetwacom set 'Wacom Intuos4 6x9 eraser' rotate HALF # don't touch
#xsetwacom set 'Wacom Intuos4 6x9 cursor' rotate HALF # don't touch
#xsetwacom set 'Wacom Intuos4 6x9 pad' rotate HALF # don't touch

# Some of the following values can be changed according your necessities

# stylus 
xsetwacom set 'Wacom Intuos4 6x9' Suppress "4" # don't touch
xsetwacom set 'Wacom Intuos4 6x9' RawSample "4" # don't touch
xsetwacom set 'Wacom Intuos4 6x9' ClickForce "5" # how much you have to press to write values from 1 to 20
xsetwacom set 'Wacom Intuos4 6x9' PressCurve "0 0 100 100" # Modify the different type of pressure (don't touch for now)
xsetwacom set 'Wacom Intuos4 6x9' TPCButton "off" # don't touch
xsetwacom set 'Wacom Intuos4 6x9' mode "Absolute" # don't touch
xsetwacom set 'Wacom Intuos4 6x9' Button3 "Button 3" # button up
xsetwacom set 'Wacom Intuos4 6x9' Button2 "Button 2" # button down
xsetwacom set 'Wacom Intuos4 6x9' Button1 "Button 1" # stylus pen

# eraser
xsetwacom set "Wacom Intuos4 6x9 eraser" Suppress "2" # don't touch
xsetwacom set "Wacom Intuos4 6x9 eraser" RawSample "4" # don't touch
xsetwacom set "Wacom Intuos4 6x9 eraser" ClickForce "6" # how much you have to press to write values from 1 to 20
xsetwacom set "Wacom Intuos4 6x9 eraser" PressCurve "0 0 100 100" # Modify the different type of pressure (don't touch for now)

# touchdial + middle button
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn "CORE KEY +" # clockwise
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp "CORE KEY -" # counterclockwise
xsetwacom set 'Wacom Intuos4 6x9 pad' Button1 "core key 1" # button of touchdial

# pad buttons
xsetwacom set 'Wacom Intuos4 6x9 pad' Button9 "core key  CTRL z" # button 9 is top button
xsetwacom set 'Wacom Intuos4 6x9 pad' Button8 "core key  CTRL y"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button7 "core key 7"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button6 "core key 6"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button5 "core key 5"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button4 "core key  SHIFT"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button3 "core key  ALT"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button2 "core key  CTRL" # button 2 is bottom button
```

and I made a script .sh that I launch every time I want to use the tablet.

There is a major issue this lib libxcb-xlib0_1.1-1.2_i386 is missing in ubuntu and if I install it from debian I have problems after with conflict with another lib.

How can I give the the instructions about buttons and the rest without using this?

---

### Post by Favux on 2010-01-29
Hi ilcontegis,

It looks like you have made progress.

I have libxcb-xlib0 1.1-1.1 in Intrepid.  What error message are you getting that asks for libxcb-xlib0_1.1-1.2?

When we compile linuxwacom the dependencies we use are:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade
```
Again I advise not compiling linuxwacom in Karmic.
> if I install it from debian I have problems after with conflict with another lib.
That makes me hope it is there, just renamed or part of another package.  Maybe as part of one of the dependencies above?

---

### Post by Idefix82 on 2010-01-29
I hope you don't mind me hitch-hiking this thread for a similar problem:

I am trying to get the Intuos4 to work under Jaunty.
I have installed the driver linuxwacom 0.8.5-9 and copied your .fdi, Favux, from your linked post. If I run xsetwacom list, the output is
```

eraser     eraser
cursor     cursor
pad     pad
stylus     stylus

```

In Gimp and in Inkscape I have enabled the eraser as described in the Wacom wiki. Yet, the eraser only draws, just like the normal pen. Pressure sensitivity works, but the eraser doesn't erase. Have you come across this problem?

---

### Post by Favux on 2010-01-29
Hi Idefix82,

It may just still be assigned to a brush or something.  Have you tried assigning the eraser to the eraser tool?  Point the eraser to the the eraser symbol on the tool panel and when it assigns the eraser tool to the eraser end of the stylus Save it.

---

### Post by Idefix82 on 2010-01-29
You are a star, thanks a lot! Thanks also for the .fdi!

I feel stupid but happy now (had already installed 3 different versions of the driver and 3 different .fdis in almost all combinations :)

---

### Post by ilcontegis on 2010-01-29
it says that there are configuration problems with libxcb-xlib0 as libxcb1 (1.4-1) is damaging libxcb-xlib0
then it suggest me to use 
apt-get -f install to correct the problem. If I run it libxxcb-xlib0 will be deleted.

I did not compile anything as you suggested, but I installed those files just in case...

---

### Post by Favux on 2010-01-30
Hi Idefix82,

Don't worry about it.  Gimp is pretty complicated and not necessarily very intuitive.  I'm just glad you're set up.


Hi ilcontegis,

I'm puzzled.  You'd think if there is a conflict between libraries the newer one would have supplanted the older one and would provide its functions.  I guess maybe the code could be calling the specific library version.

If you're going to follow apt-get's suggestion I would recommend carefully recording all the libraries and dependencies that are changed or removed so you can reconstruct things if needed.

---

### Post by ilcontegis on 2010-02-02
the problem is just that lib. if I uninstall it everything works fine.. no other dependencies.
I really have no clue...I guess I should wait for the 10.04 and see if things will improve.

---

### Post by Favux on 2010-02-05
Hi ilcontegis,

We've made some progress on the OLED's.  You could join us on this thread:  [http://ubuntuforums.org/showpost.php?p=8777159&postcount=18](http://ubuntuforums.org/showpost.php?p=8777159&postcount=18)

---

### Post by anti00 on 2010-03-11
I'm pretty sure I'm going to come off as a total idiot, but for the life of me I can't find the answer anywhere. I ask here because I saw "lefthanded" mentioned. I just got the intous4, I run on Karmic, I've changed the .fdi file, everything works... except how in the hell do I flip for left handed use?! The physical tab under the pad doesn't work in linux, right? I've tried it both ways just to be sure... I'm at a loss. Please help. I'm left-handed, dammit! :P

---

### Post by anti00 on 2010-03-12
Ok, I've figured out how to change the pad's alignment to lefty using the following command in the terminal (for anyone who might have my previous problem)...  ```
xsetwacom set pad rotate HALF
```
And I went ahead to try and mess around with the .xinitrc file... ended up in a weird loop... and didn't save the xsetwacom command anyway, so I removed the Startup App, and reversed the chmod. Just wondering if I did something wrong, or if I have to open a terminal every time to flip the orientation.

---

### Post by damagu on 2010-05-29
> **ilcontegis said:**
> ...everything is so messed up....do this if you have jaunty, do that if you have karmic, don't do this if you have the bamboo, do that and this if you have the intuos 3 but not if you have the intuos 4....

I agree completely. Can someone start a wiki page dedicated to tablets? It would be great to see all of the info organised a little better. Perhaps it could be like [this wiki]("https://help.ubuntu.com/community/MacBookPro") for Ubuntu on Macs.

It's organised into hardware versions, ubuntu versions, there are compatibility lists, there are lists showing which features are working it which ones aren't etc. 

I'd love to see something like this for graphics tablets. I can help organise it but I don't know how to start.

---

