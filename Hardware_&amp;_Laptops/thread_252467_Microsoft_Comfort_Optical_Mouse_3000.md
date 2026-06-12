---
title: "Microsoft Comfort Optical Mouse 3000"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by soundguy24 on 2006-09-06
I have [this mouse]("http://www.microsoft.com/products/info/product.aspx?view=22&pcid=a4e32bc3-7c62-4ae5-a3e6-d056aa79e96c").

On Windows, I can map the little red button on the side (see pic at link) to perform middle-click actions. Can you show me how to do this on Dapper?

'xev' shows this button to be called button 9.

Thanks for anything you can give me!

---

### Post by soundguy24 on 2006-09-09
How 'bout I simplify it--I need to make "button 9" perform the action of "button 2." Still nobody?

---

### Post by ebutton on 2006-11-10
I think there is an answer in the Tips and Tricks forum, but use the top-level forum "Search" feature in the main menu bar (near the top of almost any forum page).  I don't think you'll get info for your specific make/model though.  I just did a search for "Microsoft Comfort Optical Mouse 3000" and yours was the only specific hit.  Instead use some of the technical terms in your post like "xev" and "button 9".

I have seen some info on mapping, so I think you can find what you need.

I searched because I want to buy a new mouse that will be compatible with both XP and Dapper.  I'm using a KVM to switch between two boxes.

Regards and Good Luck!
EdB

---

### Post by floundered on 2007-01-23
Thanks to this post:

[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/52288](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/52288)

by Guilherme Paula, my left/side/thumb button on my Microsoft Comfort Optical Mouse 3000 is now working as a "back" button in FireFox under Ubuntu 6.10 Edgy (and in Xubuntu and the Xfce desktop).

The key is two required settings in your xorg.conf file.  The "Buttons" setting must be set to 8, and the "ButtonMapping" must be set to "1 2 3 8 6 7".  What's strange is that playing with xev showed the left thumb button as button #9, while that number isn't required anywhere in the aforementioned settings.  After I implemented these changes, xev shows the left thumb button as #6.  Go figure.  

The sparse man pages for xorg.conf and the mouse driver were no particular help in figuring this out.  I really bugs me that despite too many hours of reading all available documentation, I ended up just copying someone else's discovery to make it work.  And even then, I don't understand exactly why the solution works, just that it does.

Step-by-step instructions for anyone interested:

1.  Open a terminal window (Applications->Accessories->Terminal)

2.  Hop into the X11 folder and backup your old xorg.conf:
```
cd /etc/X11
 sudo cp xorg.conf xorg.conf.backup
```
3.  Open xorg.conf in an editor to modify the mouse section:
```
sudo gedit xorg.conf
```
4.  Scroll down to the "InputDevice" section for the mouse and make it look like this.  The "Emulate3Buttons" setting can be set to false if you don't want a middle click by pressing the left & right buttons at the same time, other than that I think everything else is required to make it work:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"8"
	Option		"ButtonMapping"		"1 2 3 8 6 7"
EndSection
```
5.  Save the changed file, close the terminal window, and restart your system.  I don't know for certain if restarting is required, as I don't know when the X server slurps in the config settings.

6.  Log in, start FireFox, navigate through a link somewhere, and try going back with the thumb button.

Let us know if this works for you or not.  If anyone figures out how to activate the left & right scrolling with the tilt wheel, please share the knowledge!

Methinks there has to be an easier way to semi-automate pointer configuration with a generic GUI app of some sort.

---

### Post by p_squared on 2007-11-01
Thanks floundered, I tried those instructions in Gutsy and it got my red button working.  With this xorg setting, xev shows the red button is Button 6.

Now compiz is setup to use the Scale plugin whenever i use the red button, w00t!!!

:guitar:

---

### Post by tm6148 on 2007-12-12
> **floundered said:**
> 
The sparse man pages for xorg.conf and the mouse driver were no particular help in figuring this out.  I really bugs me that despite too many hours of reading all available documentation, I ended up just copying someone else's discovery to make it work.  And even then, I don't understand exactly why the solution works, just that it does.



Amen, brother!  I just spent a couple of hours of trial and error after trying several suggested solutions from this forum.  Then I just happened to hit on the right search criterion to find your post.  It worked like a champ.  Thanks!

---

### Post by spiderbatdad on 2007-12-31
i don't think i could talk you yhrough those instructions any better  than they are written...however, if you are just concerned with magnifying web pages...ctrl++ will magnify the page...doing it again will magnify even more...obviously, ctrl-- will reduce magnification. Good luck...dont be afraid of those instructions! woops sorry...see this post finally got some response...i was browsing unanswered posts when i came across it, then while i was looking for you...some responses, finally.

---

### Post by rhvkl on 2008-05-14
Hello, your guide works for me, thanks.

But the going back isn't my prefered action on clicking the red button on the left, i would prefer a close the actual window. is that possible and how?

(linux newbie)

---

### Post by Martodox on 2008-05-18
Hey guys.

Any ideas on how to make it work in hardy?

---

### Post by defendguin on 2008-07-21
After some searching I did this on my own after reading the X.org [documentation]("http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html")  This is a must read if you want to understand what is going on in this section of the file.  I too wanted the  thumb button to be another middle click button because the actual middle click button seems way too stiff for me.  

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Name" "Microsoft Microsoft Optical Mouse with Tilt Wheel"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"   <--  important if you leave it to auto it will probably get assigned to ImPS/2
    Option "Buttons" "9"
    Option "ZAxisMapping" "4 5"

    Option "ButtonMapping" "1 2 3 6 2"   <--  see here how the 5th number is 2 again   this is physical button 9 to the logical button 2  don't ask me why it is this way but it IS!!
EndSection

Sorry I can't get the tilt wheel working.  No matter what I do the tilts to seem to generate any events in xev.  If someone actually gets the tilt wheel working please let me know.  I have filed a bug about them not causing events [here]("https://bugs.launchpad.net/ubuntu/+bug/250424") hopefully we can get this all figured out

---

