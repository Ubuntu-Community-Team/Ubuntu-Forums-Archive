---
title: "Giant font trap"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by fatcatthetinker on 2009-03-12
Greetings!
After maybe hours of installing Gutsy and then upgrading to Hardy I ended up with a very tiny 1/16 inch font everywhere. All else appeared to work fine. I surfed with very tiny font on firefox.

Somewhere on the path to catastrophe I changed a dpi (Dots per inch) setting by about half which made some of my adjustment options shrink from barely readable to a thin line..

I right clicked on the task bar and got an option to mess with the font, clicked more or advanced or some such and thoughtlessly rolled the finger wheel on my mouse. 

The font size changed, then became very big, So big that the menu bar and screen overflows with just a few letters.... and the thumb wheel stopped changing the font size. Of course this means all options are shoved off screen.

So I have no way to recover.
Safe boot brings up the same screen with giant letters. Is there a way out without a complete re install? 

Thanks!

---

### Post by Therion on 2009-03-12
You can totally reset your desktop by doing the following...  

Ctrl+Alt+F1
(You'll drop to a command line)
Log in using your login name and password.
Carefully type in the *following:```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
Then Ctrl+Alt+F7 to get back to your desktop.
Log back in and enjoy.





(*Yes, the the oft-warned about rm -rf command!!! OMGZ!!!  See my [source](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/) if you have a problem with this before freaking out and posting about rm -rf.)

---

### Post by fatcatthetinker on 2009-03-12
Therion,

Many thanks for getting me out of my trap.

I think The way I got into the trap  was via system, appearance, preferances, details. Probably a combination of all my actions.

Your fix got me safely back to ground zero, now I'll go see about my tiny fonts.
Fatcatthetinker

---

### Post by Therion on 2009-03-12
You're welcome. Glad you were able to get back on track relatively painlessly.

My suggestion... Stay out of the Fonts Rendering Details.  My spidey-sense tells me something in those menus may have been your undoing.  

To increase your "tiny" fonts, all you should need do is click on the font-size next to each font and select a larger number from the drop down menu.  I'm fond of Verdana for most things and use it around 11 points or so.  But that's just an example.

---

