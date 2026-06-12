---
title: "Bamboo Fun Stylus Not Being Recognized."
date: 2011-05-14
forum: Hardware
---

### Post by The_Orange on 2011-05-14
Right before this most recent OS update, I had my Wacom Bamboo Fun working smoothly. Now it doesn't seem to be able to see the stylus.

What I mean by that is, I can use the stylus, but when options in GIMP are set for pressure sensitivity, it just doesn't do anything. When I go to Edit > Preferences in GIMP, it doesn't come up with a stylus option to edit for an input; just the "Wacbom BambooFun 4x5," which is currently set to screen. I tried both while using my touch pad and while using the stylus.

I've tried this: [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)
And this: [http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom+tablet](http://ubuntuforums.org/showthread.php?t=967147&highlight=wacom+tablet)

I have a feeling it has something to do with this:

chelsea@chelsea-laptop:~$ dpkg -p wacom-tools  | grep Version
Package `wacom-tools' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

But I'm not sure what that means. Do I need to reinstall my tablet?

---

### Post by Favux on 2011-05-14
Hi The_Orange,

Do you mean you upgraded from Maverick to Natty for example?

Post the outputs of *xinput list* and *xsetwacom list* entered in a terminal.

---

### Post by The_Orange on 2011-05-14
Yes, Natty. I wasn't sure what it's name was. The old was was Maverick, I remember. 

chelsea@chelsea-laptop:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; Laptop Integrated Webcam                    id=9    [slave  keyboard (3)]
chelsea@chelsea-laptop:~$ xsetwacom list
The program 'xsetwacom' is currently not installed.  You can install it by typing:
sudo apt-get install xserver-xorg-input-wacom

---

### Post by Favux on 2011-05-14
Well that's weird.  It's like either the wacom.ko or xf86-input-wacom isn't installed because the tablet isn't showing up in xinput list.  Your tablet was plugged in when you ran xinput list, correct?

Check in Synaptic Package Manager or the Software Center that xf86-input-wacom is installed.  It should have been by default so xsetwacom should be installed.  Search wacom.  The package is called xserver-xorg-input-wacom like the error message says.

---

### Post by The_Orange on 2011-05-14
Sorry, no it wasn't. Plugged it in and ran them again:

chelsea@chelsea-laptop:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 4x5                         id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; Laptop Integrated Webcam                    id=9    [slave  keyboard (3)]

chelsea@chelsea-laptop:~$ xsetwacom list
The program 'xsetwacom' is currently not installed.  You can install it by typing:
sudo apt-get install xserver-xorg-input-wacom



I don't ever use the Synaptic Manager, but I think it said it was installed. When I searched for it, it appeared on the left, but nothing appeared on the right. Though when I used the Software Center, I couldn't find it in Installed Items.

I'm going to venture that it's not installed?

---

### Post by Favux on 2011-05-14
With it plugged in it is a least showing up in xinput list so you have the wacom.ko.  I'm guessing it isn't installed because xsetwacom isn't.  Which is weird because it should be installed by default.  Just install it through either or enter in a terminal:
```
sudo apt-get install xserver-xorg-input-wacom 
```
and reboot.

---

### Post by The_Orange on 2011-05-14
Works like a dream. (= Thank you so much!

---

### Post by The_Orange on 2011-05-16
Gah, apparently I was too fast to say it was working. Yes, it works as far as pressure sensitivity, but now I'm unable to pick different tools in the tool bar of GIMP; mouse pad or stylus, neither work. Doesn't make a difference if I open GIMP with the stylus or the mouse; I can't pick different tools.

---

### Post by Favux on 2011-05-17
Not good.  I'll have to look at that in Natty.  It seems to me I was having problems with tool selection in Gimp with Maverick.  The assignments didn't seem to stick like before.  I assumed I was doing, or had done, something wrong with the Gimp Save file but didn't really look into it because with a little finagling I could get it to do what I wanted.  So it could be a Gimp bug, or a GTK+ bug, or a xf86-input-wacom bug, or something else.

---

### Post by The_Orange on 2011-05-18
Hope it's not too big of a bug! (=

---

### Post by Favux on 2011-05-19
It seems a little balky to me.  I'll have to change the focus off the tool palette sometimes before it will let me change tools.

I'm going to guess this is a Natty Unity problem.  So it may go away if you chose Classic.  And maybe turned off effects.

---

### Post by The_Orange on 2011-05-19
I turned off the minimize effects a long time ago. I assume the drop shadow effect is with that, but I can't seem to remember where to go to get rid of it.

---

