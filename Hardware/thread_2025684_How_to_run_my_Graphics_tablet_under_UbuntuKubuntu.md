---
title: "How to run my Graphics tablet under Ubuntu/Kubuntu"
date: 2012-07-14
forum: Hardware
---

### Post by wishingstar on 2012-07-14
Hello all,

I believe this is the right place to ask this. I just got a new Lapazz H640 graphics tablet, and I would like to run it under Ubuntu/Kubuntu to do some photo editing and digital drawing. I am wondering what kind of driver/hardware definitions would I need to make it run. It has 1024 pressure levels and 6 function keys.

Appreciate any help..
-Wishing Star

---

### Post by Favux on 2012-07-14
Hi Wishing Star,

Which version/release of Ubuntu or Kubuntu are you using or planning to use?

I believe that is an UC-Logic Tablet WP8060U.  Run these commands in a terminal:
```
lsusb

xinput list
```
and post the outputs so we can find out for sure what it is?

---

### Post by wishingstar on 2012-07-15
Thanks for responding Favux. I tried to run those commands by installing Kubuntu in VM, but the codes resulting in a list of virtualized mouse and keyboard settings. I am currently on windows, so i'm gonna have to free up some space on my disk and install Kubuntu (or format and install only kubuntu). Just a quick question before I do all that: will I be able to use the tablet in relative mode (like a mouse) in linux? as the current driver for windows does not support that.

Thanks again

---

### Post by Favux on 2012-07-15
I don't believe so.  If things are setup for the tablet correctly in the kernel the X driver it runs on, evdev, will set it up as a tablet with Absolute mode.  If you tried switching it to Relative mode it would probably break it as far as the pen actually writing.  You could try it though.

---

### Post by wishingstar on 2012-07-16
Okay, so in order to avoid any trouble in case I can't run the tablet in relative mode, I booted into Kubuntu 12.04 from a flash disk, and ran the commands after connecting my tablet:

```
kubuntu@kubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 004: ID 04e8:6877 Samsung Electronics Co., Ltd Galaxy S
Bus 001 Device 005: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 002: ID 5543:0083 UC-Logic Technology Corp. 
kubuntu@kubuntu:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWH640                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWH640                           id=10   [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC TWH640                           id=11   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]
    &#8627; Toshiba input device                      id=14   [slave  keyboard (3)]

```

The table would click when I tap with the pen, but it won't move the cursor on screen, I just thought I'd mention that.

I find your mentioning that the tablet would break if i switch to relative mode kind of strange, as I was able to do that by changing a line in a text file with my old Genius tablet. Things may be different for different manufacturers though, so I guess you, having more knowledge about this sort of thing, would know better.

Thanks again.

---

### Post by Favux on 2012-07-16
Looks like I was wrong and it is a new model:
```
Bus 002 Device 002: ID 5543:0083 UC-Logic Technology Corp.
```
Vendor = 5543 = UC-Logic
Product = 0083
Which means it isn't supported yet.  See:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

At a guess the pen is on ID #9.  To check run:
```
xinput list-props 9
```
That should also show if it is on the evdev X driver.
> I find your mentioning that the tablet would break if i switch to relative mode kind of strange, as I was able to do that by changing a line in a text file with my old Genius tablet. Things may be different for different manufacturers though, so I guess you, having more knowledge about this sort of thing, would know better.

Well maybe you were using the WizardPen driver then?  I could be wrong but that's what I've seen recently when using the evdev driver.  It looks like if you tell evdev Relative Mode it treats it like a mouse rather than a tablet.  It appears to only handle tablets as Absolute axes.  Like I said it would be worth looking into.
> The table would click when I tap with the pen, but it won't move the cursor on screen, I just thought I'd mention that.
Sometimes evdev just needs the coordinates, from xinput_calibrator or whatever, and then you can get the tablet "working".

To get the kernel driver for a new model that works with evdev you submit the information on 'Collecting tablet diagnostics' at the [DIGI*mend* project]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend").

---

### Post by wishingstar on 2012-07-16
Bummer! I guess I'll do the diagnostics they require and email them the results, hopefully they can add support for it soon.

Thanks for all the help Favux, I appreciate it :)

---

