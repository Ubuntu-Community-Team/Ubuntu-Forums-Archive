---
title: "wacom diferents profiles"
date: 2011-02-21
forum: Hardware
---

### Post by jdrageme01 on 2011-02-21
Hi ubuntu community, i have a question, can i do deferents profiles for my wacom, one for gimp, one for paint, etc.., like windows and macosx, i use diferent configurations for my programs.

If there isn't, can you tell me a way to do that, i find an application that do this but is for KDE.

This is the utility:

[http://kde-apps.org/content/show.php/wacom+tablet?content=114856](http://kde-apps.org/content/show.php/wacom+tablet?content=114856)

---

### Post by Favux on 2011-02-21
Hi jdrageme01,

Welcome to Ubuntu forums!

Which Wacom tablet do you have?

---

### Post by jdrageme01 on 2011-02-21
I have a wacom intuos4 USB small...why?

---

### Post by Favux on 2011-02-21
Too bad, there is an app. for Intuos4 OLEDs that also includes profiles.

Right now you'd have to use a different xsetwacom script for each program and place it in a laucher.  See sample Intuos4 script attached at the bottom of post #2 on the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by jdrageme01 on 2011-02-21
this scripts change all the parameters, so i can create one for every program? only i have to run it when i want to change it?...isn't it?

---

### Post by Favux on 2011-02-21
Correct.  You don't need all of the parameters for each script, just the ones you want to modify for the program, usually just the pad buttons and maybe the pressure curve on the stylus and stylus button assignments.  Then set each one up in a launcher.  I use different icons on the launchers.  On the general tablet script an icon of a tablet, etc.  Also if you drag the launchers into a panel they'll run with a single click.

As the last line in the script I add:
```
notify-send -t 1500 "Xsetwacom Script Ran"
```
which you can change to:
```
notify-send -t 1500 "Gimp Xsetwacom Script Ran"
```
etc., for each program.  Which will give you a notification of the new profile, provided you install lib-notify.

---

### Post by jdrageme01 on 2011-02-22
Amazing!!! Thanks for your help...i only want to change the buttons, so i will change only the pad buttons.

I have another little question, the button of the touchRing doesn't work like windows and macOSX, four diferent fuctions, every time that i touch this button the touchRing configuration change?(brush size, zoom,etc) the led in the touchRing...

---

### Post by Favux on 2011-02-22
I don't understand your question on the touch ring.

The touch ring xsetwacom parameter wasn't fixed until xf86-input-wacom-0.10.11.  Since the default in Lucid (10.4) is 0.10.5 & Maverick (10.10) is 0.10.8 you'd have to either compile the tar or clone the git repository.  I'm not sure the small's touch ring works quite the same as the other Intuous4 touch rings though.  Because of the LED.

---

### Post by jdrageme01 on 2011-02-22
Sorry for all the questions, but i want to use my wacom best i can.

What is the command to see all the configuration of my tablet, what keys are assign to the buttons, and how i know that i have the last update?

---

### Post by Favux on 2011-02-22
Sure.
> What is the command to see all the configuration of my tablet
There isn't one.  Enter *man xsetwacom* in a terminal to see what xsetwacom commands are available.  Or to see all the xsetwacom parameters available:
```
xsetwacom list parameters
```
> what keys are assign to the buttons
Use (from man xsetwacom):
```
xsetwacom get "device name" Button x
```
> how i know that i have the last update? 
If you compile xsetwacom you can see the version # when the module loads in Xorg.0.log (in the /var/log directory).

---

### Post by jdrageme01 on 2011-02-22
i don't understand...where i can see it

---

### Post by jdrageme01 on 2011-02-22
> **jdrageme01 said:**
> i don't understand...where i can see it

i find it...in the ubuntu software center...

version:

1:0.10.8-ubuntu1

....now how i update it to the last version, can i do it in the synaptic package manage?

---

### Post by Favux on 2011-02-22
No, the Maverick default is xf86-input-wacom 0.10.8 and it probably won't be updated.  Have to wait for Natty if you want the official update.

You can update it by either cloning the git repository or compiling the 0.10.11 tar.  See part II. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  That gets you the latest X driver.

HOW EVER DO NOT UPDATE JUST NOW.  There is a bug for the Intuos4 in 0.10.11 that probably includes your model.  They are working on it.  The fix will probably come shortly.  In that case you'll want to clone the git repository for 0.10.11+ and not use the 0.10.11 tar.

I don't know whether you need to update the wacom.ko (the usb kernel driver/module).  That's part I. of the HOW TO.

---

### Post by jdrageme01 on 2011-02-22
Hello again, i will not update the driver.

I'm fighting to map the buttons of the wacom, but nothig happens :(

This is the command that i use:

xsetwacom set "Wacom Intuos4 4x6 pad" Button9 "f1"  (example)...

nothing happens!!!!

i use later the get command and always says "9"

---

### Post by Favux on 2011-02-23
Hi jdrageme01,

You have to tell it it is the key f1 you want.  Try:
```
xsetwacom set "Wacom Intuos4 4x6 pad" Button9 "key f1"
```

---

### Post by jdrageme01 on 2011-02-23
...and for the stylus "right click button"? or is only the number "2"?

---

### Post by Favux on 2011-02-23
Just the number 2 because it isn't considered a key.  Actually it used to be *Button2 "button 2"* with linuxwacom's xsetwacom.  With "2" being short for "button 2".  I don't think that's true with xf86-input-wacom's xsetwacom anymore.

---

### Post by jdrageme01 on 2011-06-09
Hi! Someone know if i can set the mouse wheel in the touch wheel of my wacom intuos4 with xsetwacom or there is another way? 

Another question: can i change the speed of the touch wheel?

---

