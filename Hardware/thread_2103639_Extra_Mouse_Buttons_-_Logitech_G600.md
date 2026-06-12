---
title: "Extra Mouse Buttons - Logitech G600"
date: 2013-01-10
forum: Hardware
---

### Post by Andrew07 on 2013-01-10
Hello! I recently acquired a logitech G600 MMO gaming mouse and have been searching for a way to get all of the extra buttons working. As of right now there are 5 buttons that are working properly and as intended (not including the scrollwheel up and scrollwheel down, but that does work properly). Another 13 buttons work, but they seem to be mapped to an already existing key (IE: the 'G7' key when pressed simply outputs a 'B'). The last two seem to not output anything at all when pressed. 

I've done some googling around and found some answers about changing the /etc/X11/xorg.conf, but it appears that that file is empty now in Ubuntu and most of that info was several years old. 

Any suggestions?

---

### Post by Andrew07 on 2013-01-11
Decided to try and give the 'logitech gaming' software that is used to manage the mouse a shoot through wine. The software runs fine, but it fails to detect the mouse.

---

### Post by 1337_snic on 2013-01-11
Isnt that supposed to just be another number set? is your numlocks on? I know on my naga numlock has to be on in ordger for it to work. 
```

xinput

```Is the device named or is if unknown pointer device?
Also 
```

xev

```
then press the button on it and see if it is even picking it up.

---

### Post by Andrew07 on 2013-01-11
This is the result of xinput. So it does look like it's being detected.

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Gaming Mouse G600              	id=8	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Logitech Gaming Mouse G600              	id=9	[slave  keyboard (3)]
    &#8627; G15 Gaming Keyboard                     	id=10	[slave  keyboard (3)]
    &#8627; G15 Gaming Keyboard                     	id=11	[slave  keyboard (3)]
    &#8627; C-Media Electronics Inc. USB PnP Sound Device	id=12	[slave  keyboard (3)]
    &#8627; G15 Extra Keys                          	id=13	[slave  keyboard (3)]
```

Having numlock on/off seems to make no difference at all. Using xev all but two of the keys output something however.

---

### Post by the193rd on 2013-05-28
I am just finished with playing around with xinput, xbindkeys, udev-keymaps etc. etc.. That took quiet a while... But right now i bound the 12 thumb-buttons to my desired shortcuts and can use the index-, the middle- and the wheel-buttons (the wheel as well) as it was meant to be. i could change the G7-Button too, but i decided to let that alone.  Now that 2 quiet buttons that say really nothing (not in xev not anywhere): I think the G8 shouldnt say anything, because of its g600-profile-switching-function.  But i have no idea why the ring-finger-button doesnt work. Anyone?  The key-issue is that the buttons are devided into a mouse- and a keyboard-device (as you can see in the last post). But i dont even know on which one the ring-finger-butten should appear.

---

### Post by blayster on 2013-11-16
> **the193rd said:**
> I am just finished with playing around with xinput, xbindkeys, udev-keymaps etc. etc.. That took quiet a while... But right now i bound the 12 thumb-buttons to my desired shortcuts and can use the index-, the middle- and the wheel-buttons (the wheel as well) as it was meant to be. i could change the G7-Button too, but i decided to let that alone.  Now that 2 quiet buttons that say really nothing (not in xev not anywhere): I think the G8 shouldnt say anything, because of its g600-profile-switching-function.  But i have no idea why the ring-finger-button doesnt work. Anyone?  The key-issue is that the buttons are devided into a mouse- and a keyboard-device (as you can see in the last post). But i dont even know on which one the ring-finger-butten should appear.
Could you please be more specific? How did you modify them using those tools? How to use udev-keymaps?
Also, the other "silent button" is a modifier.

---

### Post by the193rd on 2014-09-10
I realize that it has been a long time, sorry!
But I had to configure the extra buttons in Arch lately and I wrote down how I did it:
[http://martins-prolog.blogspot.de/2014/09/logitech-g600-in-arch-linux.html](http://martins-prolog.blogspot.de/2014/09/logitech-g600-in-arch-linux.html)
Maybe this is helpful for others too.

---

