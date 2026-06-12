---
title: "Disable extra mouse buttons."
date: 2012-10-01
forum: Hardware
---

### Post by FilesUnknown on 2012-10-01
My system is fine but I wanted to refine the ease of use.
Google chrome has a nice feature in Ubuntu that you can switch tabs by mouse scrolling while your mouse is in the tab-bar. And a nice feature that you can middle click close tabs in the tab-bar. But the problem arises that my mouse has a side scroll if you tilt the scroll wheel  that would change the tabs as I middle click.

My mouse is the Logitech MX Performance. and I am running Ubuntu 12.04 64 bit. I was wondering if this could be accomplished by an option in xorg.conf or if I have to chose a driver that doesn't auto map and manually specify all the keys I wan't except for 6, and 7.

I want to **disable** the middle **horizontal tilt** buttons 6, and 7.
while keeping my middle scroll buttons 4, and 5.
I just don't know how to disable those.
**or** any work around to get **chrome not to respond to horizontal scroll**.

Thank you to any one that can help!


Side note xbindkeys works great at making one of my keys start the terminal. It actually worked no problem after the upgrade from 11.04 to 12.04 where as my compiz mouse shortcut broke but that for another day and I can figure it out I believe.

---

### Post by FilesUnknown on 2012-10-01
I believe I found my answer here: [http://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10](http://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10)

I tried it and it seems to be working the only problem is that there were two entries for my mouse. I tried modifying the entry. that had 24 buttons which was much more than the 7 buttons (not enough to explain a working mouse) of the other entry. and changing 6 and 7 (horizontal scroll) to 0 and 0 worked like in the tutorial.

Now I got that straightened out and have the zoom key mapped via compiz to run the terminal, the app key to 'scale' which splays all the windows that are open. every thing seems to be working now.It is nice not to need xbindkeys for launching the terminal anymore.

Hopefully this helps any other people that come along.
```
eric@eric-desktop:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:101a	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:4002	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]


eric@eric-desktop:~$ xinput list 9
Logitech Unifying Device. Wireless PID:101a	id=9	[slave  pointer  (2)]
	Reporting 7 classes:
		Class originated from: 9. Type: XIButtonClass
		Buttons supported: 24
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Forward" "Button Back" "Button Task" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
		Button state:
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0
		Class originated from: 9. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )


eric@eric-desktop:~$ xinput get-button-map 9
1 2 3 4 5 0 0 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 


eric@eric-desktop:~$ xinput set-button-map 9 1 2 3 4 5 0 0 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
``` 
And like the guy said it works.

---

