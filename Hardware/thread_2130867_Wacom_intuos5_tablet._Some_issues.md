---
title: "Wacom intuos5 tablet. Some issues"
date: 2013-03-30
forum: Hardware
---

### Post by Drew U on 2013-03-30
[B]It worked out of the box, most of it. I do not remember, how But I did manage to get pressure sensitivity in gimp. I could use a refresher on how I need to do that again.

The problems I am having is setting the multi-use buttons on it. 6 buttons, 1 wheel with 4 settings. I want to set them up for certain uses. such as the wheel being able to do brush size. zoom. rotation of canvas. layer switching. [s how do I do that?

Also I'm not sure (have not really tested) but this tablet has angle detection as well and I do not see that happening either(not as important at moment).[/B]

Edit: so I found the settings the map buttons on my tablet. but what is the key settings for brush, zoom, rotation, layer switching, in gimp?

**Edit 2. So Ive been playing around with key mapping in gimp and tablet to get these to work. but it seems none of them are taking. not one is working? not even the button to switch ring modes is. The pen and eraser is about all that is working**

---

### Post by Favux on 2013-03-31
Hi Drew U,

Gimp Pressure
Edit > Preferences > Input Devices > Configure Extended Input Devices.  In Device drop down select stylus or eraser.  Set Mode drop down to Screen for each.

What release of Ubuntu are you using?  I think the Wacom Graphic Tablet applet in System Settings supports the touch ring in the last release or two.

Or if not in your release you can use a touch ring toggle script instead:  [http://ubuntuforums.org/showthread.php?t=1380744&p=12547943&viewfull=1#post12547943](http://ubuntuforums.org/showthread.php?t=1380744&p=12547943&viewfull=1#post12547943)

More information on using xsetwacom commands:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

I'd need more details on what you are doing to figure out why it isn't working.

---

### Post by Drew U on 2013-03-31
I'm running 12.04. The system settings for the tablet has all the button mappings for all my buttons but none of the setting I put for them are taking.

---

### Post by cazazo on 2013-06-13
Drew U, 
Did you solved your problem??? 
I'm having the same sort of problem! 
You try to set a key bind for the buttons and the settings will not apply. Same goes to the wheel and the selection button on the wheel. Really frustrating!
I'm having to use Windows7 as dual boot because of my tablet support. Even the feel of the pen isn't feeling right... the sensitivity in windows is much smoother and precise than under Ubuntu. Even though you can adjust the sensitivity on Gimp, it still feels sort of rough compared to win7 :/.
In short, if I want to get it working properly, I have to restart and boot up Win7.

---

