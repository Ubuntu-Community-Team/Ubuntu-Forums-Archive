---
title: "Need help with touchscreen"
date: 2010-11-15
forum: Hardware
---

### Post by Toffefe on 2010-11-15
Hello! 
This is my first post on this forum. I'm running ubuntu 10.10 on my Packard Bell butterfly touch tablet pc and I'm  having trouble with the touchscreen. I think ubuntu detects it as a touchpad unit. Actually every time I start Ubuntu I have to double-click the screen for the mouse button to work.
I'm not new to ubuntu but I have no experience with update/install drivers.(just installed stuff like emacs and scitools for python)

Is there someone whose had the same problem and has a solution?
Please help me. There's also a gravity sensor that changes the screen direction when you flip the pc around( working in windows 7), is there any support for this also in ubuntu 10.10?


regards,
Toffefe

---

### Post by Favux on 2010-11-15
Hi Toffefe,

Welcome to Ubuntu forums!

Let's find out if Maverick sees the touch screen and what it is calling it.  Enter in a terminal:
```
xinput --list
```
and post the output.

---

### Post by Toffefe on 2010-11-15
Thanks!
Here's the output:


Unix:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Cando      11.6                             id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; CNF9011                                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

---

### Post by Favux on 2010-11-15
OK, you have a Cando 11.6 touchscreen.  Now you have something to google with.

It looks like you can get it working.  I see this post:  [http://ubuntuforums.org/showpost.php?p=9960107&postcount=26](http://ubuntuforums.org/showpost.php?p=9960107&postcount=26)  from this thread:  [http://ubuntuforums.org/showthread.php?t=1486671](http://ubuntuforums.org/showthread.php?t=1486671)  The last few posts on the last page or so of the thread seem to indicate more drivers are coming.

There are other threads too, like:  [http://ubuntuforums.org/showthread.php?t=1503442](http://ubuntuforums.org/showthread.php?t=1503442)

---

### Post by bobthebob1234 on 2010-11-20
Woo someone with my laptop!

I don't know if you have managed to do anything yet, but I have some good news. It is possible to get the touchscreen to work as a touchscreen. I got as far as remapping the p button and screwed everything (don't worry, i did something stupid), so I'm just in the process of reinstalling ubuntu. I will be using ubuntu 10.10 64 bit desktop. (May install netbook on top after). I'll post back some full instructions in plain english when it is installed.

---

### Post by bobthebob1234 on 2010-11-20
**Getting the touch screen to act as a touch screen**

[LIST=1]
[*]Update!
[*]open a terminal
[*]Install dpkg dev (Note sure if this is absolutely necessary, but if you don't the step 5 moans.)
```
sudo apt-get install dpkg-dev
```
[*]Install xorg-deb (This is neccessary)
```
sudo apt-get install xorg-dev
```
[*]Download the source for evdev
```
sudo apt-get source xserver-xorg-input-evdev
```
This will create a bunch of folders in the current directory (you home directory if this is a new terminal)
[*]Navigate into the src directory
```
cd xserver-xorg-input-evdec-2.3.2/src
```
[*]Open evdev.c in your favourite editor
```
sudo gedit evdev.c
```
[*] Find the line 
```

if (num_buttons || TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {

``` (Line 1942 for me)
and remove num_buttons || so the line should now look like 
```

if (TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {

```
Save and close
[*]Navigate back
```
cd ..
```
[*]Now the fun bit. Compiling the driver.The following worked for me
```

sudo .configure

```
```

sudo make install

```
This will say a load of stuff, but we are only interested in the line
```

Libraries have been installed in:

```
Mine was /usr/local/lib/xorg/modules/input
[*]Now we need to copy the evdev_drv.so to /usr/lib/xorg/modules/input
[*]But first I made a back up of the original evdev_drv.so in /usr/lib/xorg/modules/input
```

cd /usr/lib/xorg/modules/input
sudo mv evdev_drv.so evdev_drv.old

```
[*]Now copy new evdev_drv.old
```

If you haven't already:
cd /usr/lib/xorg/modules/input

Then

cp /usr/local/lib/xorg/modules/input/evdev_drv.so ./

```
[*]Now apparently you need to remove input-tslib and evtouch, however these weren't present on my system.
```

sudo apt-get purge input-tslib evtouch

```
[*]Finally reboot, and now you have a working touch screen! Yay
[/LIST]
(Sources as above)

---

### Post by Favux on 2010-11-20
Hi bobthebob1234,

Sweet!  Nice job.

If you use the '--prefix=/usr' flag on the configure line the evdev X driver evdev_drv.so will probably end up in the right place:
```
./configure --prefix=/usr
```
Saves you a few steps anyway.

---

### Post by Toffefe on 2010-11-23
Thanks! I tryed the steps and made the mistake of making a backup evdev_drv.old and i rebooted without cp the .so file so the keyboard on my laptop (and usb-keyboards) didn't work. I then tryed recovery mode and " sudo mv evdev_drv.old evdev_drv.so " and now it works!:D thanks for all help with my problem:)


[bobthebob1234]("http://ubuntuforums.org/member.php?u=472408"), do you have multitouch for screen and touchpad in ubuntu 10.10?

---

### Post by bobthebob1234 on 2010-11-23
I haven't got multi touch to work yet, but my touchscreen acts as a touchscreen now instead of a touchpad. Yes I'm using 10.10

---

### Post by Favux on 2010-11-23
Hi guys,

If you want multitouch in Maverick try ginn.  It would be something like the instructions in "1) Maverick:  ...  a)" on the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").  I don't know if your touch screens would require the patched source code to work right or whether the untouched (so to speak) source code would work for you.  Also ginn's actively being worked on so there might be an update already.

---

### Post by bobthebob1234 on 2010-11-23
I tried the instructions quickly, it compiles, installs, runs but doesn't seem to do anything with either firefox or inkscape.

---

### Post by Favux on 2010-11-23
Hi bobthebob1234,

Did you use the patched or unpatched source code?  Beyond verifying that you have a /etc/wishes.xml file I don't know what else to suggest.  I have a link to a launchpad page that links to a bunch of the Maverick multitouch projects.  I could try to find that if you want me to.

---

### Post by bobthebob1234 on 2010-11-23
I just followed the instructions on the link you posted. I didn't change anything. I'm pretty sure it loads the wishes list as when i run ginn it loads a load of stuff. I think it is trying to do something cos the whole system slows down. Other than that I haven't looked at it harder.

---

### Post by Favux on 2010-11-23
I hope you can figure it out.

[https://launchpad.net/canonical-multitouch](https://launchpad.net/canonical-multitouch)

[https://wiki.ubuntu.com/Multitouch/](https://wiki.ubuntu.com/Multitouch/)

---

### Post by bobthebob1234 on 2010-11-23
Me to! Maybe at the weekend though.:D Thanks for the pointers so far

---

### Post by bobthebob1234 on 2011-02-03
ubuntu update just broke my touchscreen, but running through my steps again fixed it

---

### Post by bobthebob1234 on 2011-05-03
Just to update anyone who reads this in the future, multi touch now works out of the box with ubuntu 11.04

---

### Post by Spidey_86 on 2011-05-03
I'm having trouble too to make a touchscreen work, in 11.04. It worked ok in 10.10 using evtouch but it seems that evtouch is not supported now...

I configured a file under /usr/share/X11/xorg.conf.d/ but when I touch any point in the touchscreen it holds the click, instead of making it and releasing when you stop touching. 

What happened with evtouch? It worked flawlessly for me...

---

