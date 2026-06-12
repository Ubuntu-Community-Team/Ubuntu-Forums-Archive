---
title: "Japanese Keyboard"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by robcarr2 on 2007-02-13
Hello, well I bought a new keyboard unfortunately I didn't know it had the japanese layout, which comes as a bit of a problem when i need to use the backslash key as I have no way of using it. Is there anyway that i can use the japanese layout but have it produce English characters when the keys are pressed?

---

### Post by dmizer on 2007-02-13
you just need to set up the keyboard as japanese in xorg.

in terminal, do the following:
```
sudo dpkg-reconfigure xserver-xorg
```
do not change any settings until you see this screen (click thumbnail for larger image)

by using the arrow keys, change it to "yes"

next you will see this screen (yours probably says uk, but you get the point)
change it to jp

then you will see this screen.
change it to "jp106"
go through the rest of the process without changing anything else, and make sure to save the settings.

you'll need to either reboot, or restart xorg (ctrl + alt + bksp) and your keyboard will then type the correct keys as they are displayed on your japanese keyboard.

---

### Post by robcarr2 on 2007-02-14
I have tried doing this (i did it through system > prefereces >keyboard ) but it didn't show up with correct characters, I believe there are two japanese layouts, 106 being the most popular, and the one im using being obsolete from the looks of things as no one seems to have the same layout as I do.

Looks like I am going to have to just pick up a new keyboard on the weekend!

---

### Post by dmizer on 2007-02-14
you sure you changed it to "jp106" rather than "pc106"?  that was my problem for the longest time.  the slash character wouldn't work, and the reverse bracket -> ] also would not work (among others) until i entered jp106.  after i did that, everything worked perfectly including zenkaku/hankaku and the kanji switching key (above the tab).

btw .. doing this through system > preferences > keyboard ... does not work.

the above has worked for me on AT type keyboards that go back as far as the early 90's  ... so i doubt your problem is that you have an obscure layout.

---

### Post by vultaire on 2007-02-16
Here's what I had to do.  Since I've figured this out I've been able to do several Japanese systems with Dapper Drake.

System > Preferences > Keyboard:
- Go to the "Layouts" tab
- For the top box, where it says Keyboard Model, press the "..." button and select "Japanese 106-key".
- In the box below, if there is not already a layout named "Japan", press "Add...", and scroll down and select "Japan".  Ignore the PC98xx version.
- Check a default layout if you want
- Press "Close"... you're done!

And of course, the obvious possibility: if the standard layout doesn't work, and your keyboard truly is a dinosaur... maybe try the other layout I mentioned above?

Best of luck.

-
Paul Goins
Assistant Language Teacher
Himeji-shi

---

### Post by robcarr2 on 2007-02-16
I have tried both of these methods but they didn't work, I am back to using my UK keyboard at the moment and think I will just stick with it :)

---

