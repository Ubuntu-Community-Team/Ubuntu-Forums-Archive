---
title: "Lenovo X230 Tablet Functionality on 12.04"
date: 2012-10-21
forum: Hardware
---

### Post by Dustpaw on 2012-10-21
So I've been plugging away at getting the full tablet functionality and some specific things d

one on this brand new Laptop, and I am kind of stumped.  I've done searches but I can't find anything to reactivating the buttons that are associated with the x230t's touchpad.  

The original purpose of the buttons were:

Power Button
Ctrl-Alt-Delete
Rotate Screen

What I did was research how to identify these buttons in ubuntu and I went to kern.log.  

So here's what kern.log returns.  

> 
Oct 21 00:19:06 DustWarband kernel: [23053.891039] atkbd serio0: Unknown key released (translated set 2, code 0x6c on isa0060/serio0).
Oct 21 00:19:06 DustWarband kernel: [23053.891046] atkbd serio0: Use 'setkeycodes 6c <keycode>' to make it known.
Oct 21 00:19:05 DustWarband kernel: [23052.999808] atkbd serio0: Unknown key released (translated set 2, code 0x67 on isa0060/serio0).
Oct 21 00:19:05 DustWarband kernel: [23052.999815] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.


the 6c part comes up for both the power off and screen rotate button
67 comes up for the ctr-alt-delete button.   

So my question is how do I better identify the keys?  and how would I go about attaching appropriate action to them?  And has all this been done before.  

Also as reference, this is xinput:  

> &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1025    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen stylus                   id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Finger touch                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen eraser                   id=15    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]

ThinkPad Extra buttons looks, interesting?  Any ideas?

---

### Post by Favux on 2012-10-21
Hi Dustpaw,

Welcome to Ubuntu forums!


You look to already pretty much have all you need.  Normally the [thinkwiki.org]("http://www.thinkwiki.org/wiki/ThinkWiki") is a good place to look but I don't see much for your model.  There are a couple of pages on hot key activation.

Anyway information on the bezel buttons is available on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") esp. appendix 2 and 3.  Also description of how to bind a rotation script to a key.

ThinkPad Extra Buttons is what Magick Rotation reads to provide automatic rotation for Lenovo tablets:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Have you found the X230t thread?

---

### Post by Dustpaw on 2012-10-21
I have not found the x230t thread, but that may just be on the part of poor looking/searching.   Do you have a link?  

Thanks for the info from the appendix! should be a good example and I'll take a crack at it later.   

So thinkpad extra buttons records the changes to the screen rotation from the joint on the screen?   Interesting... 

Also I just derped into why the power button doesn't appear to return a code of its own, its already implemented, holding it down vs just pressing it.   

Thanks for the info, I'll post back the script and setup in case other users want it for their x230 Tablet.

While we are here, few extra questions:
- Cursor change based on input?  Is that possible?  I liked the snazzy windows cursors they had vs mouse pointer...  
- I notice cellwriter is magick rotations "suggested" is that accepted as the standard?

---

### Post by Favux on 2012-10-21
Sorry, I meant the X220t thread:  [http://ubuntuforums.org/showthread.php?t=1785015](http://ubuntuforums.org/showthread.php?t=1785015)  Since there doesn't seem to be much on the X230t yet I figured some of the X220t stuff might apply.
> So thinkpad extra buttons records the changes to the screen rotation from the joint on the screen? Interesting... 
We don't actually know where the switch is physically.  For convenience we act as if it is in the hinge and call it the hinge switch.  It may be different for different tablet PCs.
> Also I just derped into why the power button doesn't appear to return a code of its own, its already implemented, holding it down vs just pressing it. 
:)
> Cursor change based on input? Is that possible? I liked the snazzy windows cursors they had vs mouse pointer... 
Don't know, never tried/looked into that.
> I notice cellwriter is magick rotations "suggested" is that accepted as the standard? 
No.  Onboard is the Ubuntu default.  And many folks prefer one of the other OSK (on screen keyboards) available.  However CellWriter is the only one I am aware of that toggles between an OSK and a hand written letter input/recognition mode.  Which is why we suggest it for tablet PCs.

---

### Post by Dustpaw on 2012-10-22
You were a huge help, I decided to utilize easystroke for my gestures (as opposed to ginn).  I now have all the applications I do and don't need at startup running and when it switches seems to get everything swapped up the way I want it.   

Now I just need to figure out those two buttons, onto that next.

---

### Post by Dustpaw on 2012-11-11
Finally getting around to looking at the bezel buttons and I ran into an issue while looking at this: 
[http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

I found that there is a previous keymapping for the lenovo tablet that properly maps the keycodes.   Here's the cat of the keymap:  

0x5D menu
0x63 fn
0x66 screenlock
0x67 cyclewindows # bezel circular arrow
0x68 setup # bezel setup / menu
0x6c direction # rotate screen


The 0x6c and 0x67 is correct based on what I found to be the keycodes for those particular bezel buttons.   My problem is when I try to apply the keymap to the device based it doesn't take.   

I followed the instructions and the dmiencode returns: 
3434CTO

So I tried altering the rules.d/95-keymap file to include this as the product and properly apply the lenovo keymapping similar to the old thinkpad tablet keymap.  Here's what I editted in the 95-keymap.rules file: 

 ENV{DMI_VENDOR}=="LENOVO*", ATTR{[dmi/id]product_version}=="3434CTO", ATTR{[dmi/id]product_version}=="3434CTO", RUN+="keymap $name lenovo-thinkpad_x200_tablet"

What did I miss?

---

### Post by Favux on 2012-11-11
Assuming:
```
ENV{DMI_VENDOR}=="LENOVO*", KERNELS=="input*", ATTRS{name}=="ThinkPad Extra Buttons", RUN+="keymap $name module-lenovo"
```
in the low key code section doesn't cut it then it appears to be this rule:
```
ENV{DMI_VENDOR}=="LENOVO*", ATTR{[dmi/id]product_version}=="ThinkPad X2[02]* Tablet*", ATTR{[dmi/id]product_version}=="* Tablet", RUN+="keymap $name lenovo-thinkpad_x200_tablet"
```
in the high key code section.  Further assuming the product_version's naming conventions are the same (HP uses product_name) then you should just need to change [02] to [023].
```
ENV{DMI_VENDOR}=="LENOVO*", ATTR{[dmi/id]product_version}=="ThinkPad X2[023]* Tablet*", ATTR{[dmi/id]product_version}=="* Tablet", RUN+="keymap $name lenovo-thinkpad_x200_tablet"
```
That will match a ThinkPad X20*, X22*, or X23* to lenovo-thinkpad_x200_tablet in /lib/udev/keymaps.

---

### Post by Dustpaw on 2012-11-11
Was I wrong in using the dmiencode results of "3434CTO" in the keymap rules?

---

### Post by Favux on 2012-11-11
Don't know for sure.  Don't see an example of using baseboard-product-name in 95-keymap.rules.  I doubt using:
```
ATTR{[dmi/id]product_version}=="3434CTO"
```
is going to work and I don't know why you repeated it.  Not sure what the ATTR syntax is for baseboard-product-name.  Maybe?
```
ATTR{[dmi/id]board_name}=="3434CTO"
```
Do you see board_name in /sys/class/dmi/id?  And it says "3434CTO"?

---

### Post by Dustpaw on 2012-11-11
That's correct, same for the product name.  

My understanding was that the rules noted in the 95-keymap are compared to board/product name and the keymaps are then applied.  Is that incorrect?

---

### Post by Favux on 2012-11-11
Ah there it is:
> # HP Pavillion dv6315ea has empty DMI_VENDOR
ATTR{[dmi/id]board_vendor}=="Quanta", ATTR{[dmi/id]board_name}=="30B7", ATTR{[dmi/id]board_version}=="65.2B", RUN+="keymap $name 0x88 media" # "quick play
I was too HP centric.  Instead of:
> The match is made to the Vendor and then the dmi id's product_name and board_version (/sys/class/dmi/id).
I should have worded it more like:
> The match is made to the Vendor and then the dmi id's product_name or product_version (/sys/class/dmi/id).  Or if need be board_version etc., whatever is needed to give a unique match.

---

### Post by Dustpaw on 2012-11-12
Favux,

Thanks for the help.  After I applied the keymapping to it I simply mapped the bezels in keyboard shortcuts to what I needed.  Seems to work perfectly now, I used your xrotate script for the bezel buttons and set the original screen focus (ctrl-alt-delete) to turn the onscreen keyboard on and off.  May change that later.

I think that's it, restored all functionality that this laptop had before and more.  Now to ginn working n tasty for additional fun.

---

### Post by Favux on 2012-11-12
> After I applied the keymapping to it I simply mapped the bezels in keyboard shortcuts to what I needed. Seems to work perfectly now...I think that's it, restored all functionality that this laptop had before and more.
Good.  Nice job.
> set the original screen focus (ctrl-alt-delete) to turn the onscreen keyboard on and off
Sweet.

You might want to post a summary of what you did for others.

---

### Post by MagicMyth on 2012-11-21
Yes please a summary would be really helpful for us other x230t owners :)

---

### Post by Dustpaw on 2012-11-23
Seeing as how while goofing off with my laptop and trying to get league of legends to work (playonlinux T..T) I managed to accidentally purge some important packages...  I grabbed quetzal and stuck that on.  

I'll post a step by step as I do it right now.

Lets start by getting all the keymaps functioning properly... and Favux do correct me if I get any of this wrong.   So originally the bezel buttons included, power, ctrl-alt-dlt, and rotate windows. 

To get that functionality on a fresh install on the x230 lets start by fixing the the x230t's key mappings for those buttons.  Lets start by applying the old key mapping (x200 tablet style laptop keymap) specifically to the the x230t.   Favux covered that with a change to 95-keymap.rules.

```
gksudo gedit /lib/udev/rules.d/95-keymap.rules

Here you will change out the existing rule:  
ENV{DMI_VENDOR}=="LENOVO*", ATTR{[dmi/id]product_version}=="ThinkPad X2[023]* Tablet*", ATTR{[dmi/id]product_version}=="* Tablet", RUN+="keymap $name lenovo-thinkpad_x200_tablet"

With: 
ENV{DMI_VENDOR}=="LENOVO*", ATTR{[dmi/id]product_version}=="ThinkPad X2[023]* Tablet*", ATTR{[dmi/id]product_version}=="* Tablet", RUN+="keymap $name lenovo-thinkpad_x200_tablet"
```This will apply the existing keymap, which after activating we will find will do nothing for existing cycling of windows/direction.  So lets turn those off and set our own custom keycodes and apply them to what we actually want to do.  

```

gksudo gedit /lib/udev/keymaps/lenovo-thinkpad_x200_tablet

Make these changes: 
0x5D menu
0x63 fn
0x66 screenlock
#0x67 cyclewindows # bezel circular arrow
0x67
0x68 setup # bezel setup / menu
#0x6c direction # rotate screen
0x6c

```Notice that I commented out the original bezel and rotate sections.  

Then we need to map said keys to keycodes already associated:
sudo setkeycodes 0x67 148  - maps 0x67 to keycode 156 (Launch 1)
sudo setkeycodes 0x6c 149 - maps 0x6c to keycode 157 (Launch 2)

Because we want these setup each time we start up lets edit our /etc/rc.local script and put them in.  Because rc.local runs pre-user we don't need sudo.  

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

setkeycodes 0x67 148
setkeycodes 0x6c 149
exit 0

```Now we can go ahead and apply these two buttons to whatever purpose we want.  In my case, I went ahead and downloaded ccsm and applied the bezel button  with the circlular arrow to what ubuntu sets to see all open programs (Super+W),  CompizConfig settings manager>scale>bindings>view all windows, grab key, hit the button and you are set.  

For the rotate window, because we want to utilize magick-rotation's x-rotate script, lets begin by getting magick-rotation setup.  This is rather easy, pull from magick-rotation's website:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Grab your download.   Go ahead and untar it in your home directory:  (tar -xf ~/Downloads/magick-rotation-1.6.2.tar.bz2), change directory into it and run the installer.  You will need to perform a system restart, but before we do that, lets create a custom shortcut to utilize xrotate.   

Hit your ubuntu gear in the top right corner>system settings>keyboard>custom shortcuts
Magick-rotation will have installed your xrotate.py script at: "/usr/share/magick-rotation/xrotate.py"

Set that up a custom shortcut (whatever you want to call it with the line above, in quotes, apply the rotate screen bezel, give it a try times 4 (to get back to the original orientation) and lets reboot to be finished with the screen rotation/bezel setup.

Extras to add and configure: 
Firefox add-on: Grab and Drag
Easystroke Gesture Recognition
Cellwriter (haven't set this up yet myself)
Onboard (as opposed to cellwriter)

---

### Post by Orieste on 2013-02-05
hi all,

So I have now the lenovo x230t working fine on Ubuntu 12.10. But I have a major question: which program do you guys use for hand writing recognition and for notes in general, for example pdf notes.... 
I know that Favux is an experted on this questions. I have to say that your posts were incredibly useful.

Thanks,

O.

---

### Post by Favux on 2013-02-05
There is no equivalent to OneNote in linux yet that I know about.

Xournal for notes and PDF annotation.  Some folks like Jarnal.

CellWriter for letter recognition.

---

### Post by cpbl on 2013-10-13
Has anyone experience with these steps using 13.04 or 13.10?  Or is it advised to stick with 12.04 for the X230T?

---

