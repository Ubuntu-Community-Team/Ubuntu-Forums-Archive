---
title: "Disable Back Button on V200 Mouse"
date: 2008-05-04
forum: Hardware
---

### Post by Javafox on 2008-05-04
I have a Logitech V200 cordless mouse, which has 7 buttons.  2 of these are triggered by the scroll wheel tilting left and right.  By default, the left scrolltilt button is the Back command in Firefox.  I want to disable both the scrolltilt buttons because they get in my way and enable the scrollclick button so it does the same thing in windows (it pops up the little arrow picture and then you can scroll by moving the cursor).

I've looked for hours, but I can't get anything to work.  Here's my xorg.conf file:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Can someone give me a hand?

---

### Post by Javafox on 2008-05-12
Anyone?

---

### Post by biscombe on 2009-05-10
I recently installed Ubuntu on my laptop at home and was having the exact same problem with my V200 mouse. The good news is that after several hours of searching, I've finally found a solution that seems to work. 

Most of the other 'solutions' I found suggested making changes either to Firefox settings (via about:config) or xorg.conf, but none of that worked. Try this instead:

1. Install xinput:```
sudo apt-get install xinput
```This is basically a command line tool for making configuration adjustments. There's some more info at [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

2. Now enter:```
xinput set-button-map "Configured Mouse" 1 2 3 4 5 6 7 0 0
```replacing "Configured Mouse" with the appropriate name for your mouse. You can find this from ```
xinput list
``` if you don't know it; I believe it will be the same as in your /etc/X11/xorg.conf file (it is in my case, anyway).

Note that this will completely disable the left and right tilt functions of the mouse. For me this is not a problem because I've never used them for anything, but if you intend to use them in applications other than Firefox, you might need to try something else...

3. The xinput settings do not persist across sessions, so you need to get that code to run at startup. You can do this easily via System > Preferences > Sessions. In the Startup Programs tab click Add, then paste the above command into the Command field, and add whatever name you like (I used Mouse Config) to the Name field. Click OK and you're done.

Alternatively, it may be possible to add the line to your /etc/rc.local file, although this didn't work for me.


Note that the above method *should* also work for other mice. You just need to alter the button mapping to work correctly with your mouse, replacing the numbers corresponding to tilt functions with zeros. You should find the xev command helpful for identifying your buttons.

I know it's been a while since the original post, but I hope someone out there will find this useful.

---

