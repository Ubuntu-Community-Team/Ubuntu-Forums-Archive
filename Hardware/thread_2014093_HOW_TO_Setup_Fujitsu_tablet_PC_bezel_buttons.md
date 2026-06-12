---
title: "HOW TO Setup Fujitsu tablet PC bezel buttons"
date: 2012-07-01
forum: Hardware
---

### Post by Cobuntu on 2012-07-01
**Participate in developing and testing fujitsu-tablet udev keymaps**

After using a Toshiba Tecra M4 and several HP tx (which all were hot and noisy) I am very pleased with my Fujitsu Lifebook T730 and will definitely go for another Fujitsu Tablet PC when the time has come. As far as I understood all Fujitsu Tablet PC use the same driver for the bezel buttons and those are not working out of the box (yet). I am just a dumb user but there are some experts that make the difference and I am very grateful to them! So I hope I am not the only one being interested in Favux's offer here: 

> [http://ubuntuforums.org/showpost.php?p=11936215&postcount=36](http://ubuntuforums.org/showpost.php?p=11936215&postcount=36)! 
Is anyone interested in looking into the bezel buttons further? Cobuntu  started to on page 1 of this thread. He didn't get a X key code for any  of them in **xev** as I understand him. And no reaction at all from the first 3.

If interested list your model and how many bezel buttons and what each one is suppose to do.

Then enter in a terminal ***/lib/udev/findkeyboards***. The output will show what event# the keyboard is on. Then using that event# enter in a terminal:
Code:
sudo /lib/udev/keymap -i input/event# | less
Then press the bezel button(s) of interest. After pressing the bezel buttons enter ***esc*** to exit, and you will see the scan codes and the associated udev key codes. Enter ***ctrl-z*** to exit **less**. Post that output matching each scan code/key code to your bezel button and intended function list.

We  then should be able to figure out how to get them to work. We can use  rc.local but as I mentioned to Cobuntu we would ultimately like a **fujitsu-tablet** udev keymap to place in /lib/udev/keymaps.

Again I'm using appendix 2 from the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") and the **README.keymap.txt** at /usr/share/doc/udev/README.keymap.txt.bz. The README.keymap.txt is basically the instructions to assemble a udev keymap.So if you have a Fujitsu Tablet PC please post your results here!

Also be aware that MagickRotation already supports Fujitsu Tablet PCs with the latest version 1.6.1: [http://ubuntuforums.org/showthread.php?t=1967982](http://ubuntuforums.org/showthread.php?t=1967982)

                          Fujitsu T730 has five bezel buttons [Physical number=printed above the button___printed (in color) left on the button___printed (in color) right on the button]:
1=1___(in blue) A____(in white) scroll key down
2=2___(in blue) B____(in white) scroll key up
3=3___(in white) screen rotation symbol
4=4___(in blue) Fn
5=ENT___ (in white) ALT

---

### Post by Cobuntu on 2012-07-01
This is how I managed to install fjbtndrv in 12.04 x64 (there might be a better way, but at least I got it working):
< ppa was not working and there are missing packages when you download fjbtndrv-2.3.2 and run ./configure: it gives an error: Package requirements (x11 xi xext xtst) were not met:
No package 'xi' found
No package 'xtst' found this did not work
> according to [http://katastrophos.net/andre/blog/2...0-u2010-u2020/]("http://katastrophos.net/andre/blog/2012/05/29/installing-ubuntu-12-04-precise-pangolin-on-fujitsu-u820-u2010-u2020/") run:
sudo apt-get install libxrandr-dev libxtst-dev libxi-dev libhal-dev
> then download latest driver to desktop: [http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/) and unrar
> cd /home/USER NAME/Desktop/fjbtndrv-2.3.2
> ./configure
> make
> sudo make install (do not forget that!)
> done, reboot
< nothing works in 12.04x64; some scripts are here: /usr/local/lib/fjbtndrv
> go to [https://launchpad.net/~khnz/+archive/ppa]("https://launchpad.net/%7Ekhnz/+archive/ppa")
then open for the latest available: [https://launchpad.net/~khnz/+archive...-archive-extra]("https://launchpad.net/%7Ekhnz/+archive/ppa/+sourcepub/1313773/+listing-archive-extra") and download all 4 available .deb for the correct platform (i386/amd64) and install in the following order (otherwise fjbtndrv will not install): fsc-btns-kernel-source > fscd > fscrotd > fjbtndrv
RESTART





 **Result when testing the buttons according to Favux's instructions ([http://ubuntuforums.org/showpost.php?p=11936215&postcount=36):](http://ubuntuforums.org/showpost.php?p=11936215&postcount=36):)**

xev+BUTTON 1:
KeyPress event, serial 36, synthetic NO, window 0x5a00001,
root 0xae, subw 0x0, time 7093532, (-515,145), root[IMG]http://1.2.3.9/bmi/ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]259,197),
state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False


xev+BUTTON 2:
KeyPress event, serial 36, synthetic NO, window 0x5a00001,
root 0xae, subw 0x0, time 7198570, (-616,124), root[IMG]http://1.2.3.9/bmi/ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]158,176),
state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False


xev+BUTTON 3:
KeyPress event, serial 36, synthetic NO, window 0x5a00001,
root 0xae, subw 0x0, time 7256350, (-328,187), root[IMG]http://1.2.3.9/bmi/ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]446,239),
state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False


xev+BUTTON 4:
KeyPress event, serial 36, synthetic NO, window 0x5a00001,
root 0xae, subw 0x0, time 7321409, (-642,135), root[IMG]http://1.2.3.9/bmi/ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]132,187),
state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False


xev+BUTTON 5:
KeyPress event, serial 36, synthetic NO, window 0x5a00001,
root 0xae, subw 0x0, time 7357163, (-597,212), root[IMG]http://1.2.3.9/bmi/ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]177,264),
state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False




But with the next step I get stuck:
> /lib/udev/findkeyboards
> /lib/udev/findkeyboards: AT keyboard: input/event4
> sudo /lib/udev/keymap -i input/event4 | less
„Then press the bezel button(s) of interest. After pressing the bezel buttons enter esc to exit, and you will see the scan codes and the associated udev key codes. Enter ctrl-z to exit less. Post that output matching each scan code/key code to your bezel button and intended function list.“
< When I press the bezel buttons nothing happens, after pressing ESC it says:
Press ESC to finish, or Control-C if this device is not your primary keyboard
scan code: 0x01 key code: esc
(END)
 
Favux's response so far:
 > I think right now the fjbtn drv is grabbing the keys which is why things aren't working as expected, but is why you are seeing xev keycodes. So nice work on getting it to compile. Although I'm pretty sure you don't need libhal-dev. And its not clear to me what the deb.s did.

Each version of fjbtn drv varied how things were implemented so I'd have to go through it step by step to try and figure out exactly what's happening.

---

### Post by Favux on 2012-07-01
Alright, so far for our sources list we have the following.

**[SIZE="3"]Sources:[/SIZE]**
Basic Instructions:  /usr/share/doc/udev/README.keymap.txt
Original thread:  [http://ubuntuforums.org/showthread.php?t=1967982](http://ubuntuforums.org/showthread.php?t=1967982)
Appendix 2 and elsewhere:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)
And of course Robert Gerlach's stuff


In appendix 3 on the Rotation HOW TO we figured out scroll for the HP Elitebook's jog dial.  So we should be able to do that for your scroll keys.

At this point to get our fujitsu-tablet udev keymap we want to go through step a) and b) in appendix 2 (or my instructions in the quote in your first post) with the fujitsu-tablet.ko from [Magick Rotation]("https://launchpad.net/magick-rotation") installed.  Which means you need to remove the fjbtn stuff you have installed so it isn't interferring with anything.

---

### Post by Cobuntu on 2012-07-01
Favux, I removed fjbtndrv/fscrotd/fscd/fsc-btns-kernel-source via Software Center. I have no idea how to remove my other step:
> cd /home/USER NAME/Desktop/fjbtndrv-2.3.2
> ./configure
> make
> sudo make install

Also isn't fujitsu-tablet.ko getting lost this way - I did not have installed that before I installed any of the fjbtndrv stuff - but in MagickRotation's 'fujitsu-tablet_README.txt' it says that this is required (and not provided for in kernel 3.2)?

---

### Post by Favux on 2012-07-01
Ah, OK.  That means you have the early version of fujitsu-tablet from fjbtndrv.  We definitely don't want that.  We want to determine what the buttons are from the fujitsu-tablet.ko that got accepted to the kernel.  I have to check versions but he fixed the buttons for several models.  So the fujitsu-tablet.ko that first got accepted (3.3 kernel?) is buggy and it is the next kernel (3.4?) where the fixes were applied.  Which is the one Magick uses.

So after you uninstall it use the one in Magick.  Just follow the directions in MagickExtras to install it.

If the Makefile is complete (fingers crossed) what you should be able to do is go back into the folder where you did:
```
sudo make install
```
and to remove it run:
```
sudo make uninstall
```

---

### Post by Cobuntu on 2012-07-02
Ok, sudo make uninstall seemed to work fine, following through  MagickExtras instructions again showed that everything was still there  and MagickRotation was and is working fine. I hope that everything is  removed now, the only thing I noticed was, that already after removing  the fjbtndrv debs after swivelling CellWriter seemed to have reset into  training mode again.

Here is the xev output on Fujitsu T730's five bezel buttons [Physical number=printed above the  button___printed (in color) left on the button___printed (in color)  right on the button]:

(...)

 **pressing button ****1=1___(in blue) A____(in white) scroll key down:**
KeyPress event, serial 36, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 15655825, (-224,245), root:(550,297),
    state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 15655969, (-224,245), root:(550,297),
    state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



**pressing button 2=2___(in blue) B____(in white) scroll key up**:
KeyPress event, serial 37, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 15688707, (-213,196), root:(561,248),
    state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 15688912, (-213,196), root:(561,248),
    state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



 **pressing button ****3=3___(in white) screen rotation symbol**:
KeyPress event, serial 38, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 15870768, (-161,237), root:(613,289),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 15870883, (-161,237), root:(613,289),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



 **pressing button 4=4___(in blue) Fn:**
KeyPress event, serial 41, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 16018411, (-288,251), root:(486,303),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 16018661, (-288,251), root:(486,303),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



 **pressing button 5=DEL___ (in white) ALT:**
KeyPress event, serial 42, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 16068691, (-378,308), root:(396,360),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 43, synthetic NO, window 0x6c00001,
    root 0xae, subw 0x0, time 16068841, (-378,308), root:(396,360),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

(...)

sudo /lib/udev/keymap -i input/event4 | less still does not work, so I  guess either fjbtndrv is not completely removed or I am missing  something. Maybe it were best to make a clean install on an external  harddrive...

---

### Post by Favux on 2012-07-02
Looks good.  Check in /usr/src that the only thing you see that could be related to Fujitsu and Robert Gerlach is fujitsu-tablet-20120404-gerlach.  If so then it all should be cleaned out.

With the emoticons in your last post:  could you edit it and check the don't show emoticon option or else add a space between the symbols its taking as an emoticon?  Also you might want to lable each keypress and keyrelease event pair with the bezel key you listed before.

Let's start with scroll.  The two scroll bezel button aren't working correct?

---

### Post by Cobuntu on 2012-07-02
Ok, I think there is one strange thing, I have the same folder twice, on different levels:
 /usr/src/fujitsu-tablet-20120404-gerlach
 /usr/src/MagickExtras/fujitsu-tablet-20120404-gerlach
 Both contain: dkms.conf, fujitsu-tablet.c, Makefile
 


 And you are correct, none of the buttons are working.

---

### Post by Favux on 2012-07-02
You're OK with the double folder thing.  That's what the dkms does as part of its install routine.

Alright.  I'll have some stuff for scroll here in this post in a bit.


Edit:  OK, let's try to figure out the kernel scan code.  Enter in a terminal:
```
/lib/udev/findkeyboards
```
and post the output.

---

### Post by Cobuntu on 2012-07-02
```
/lib/udev/findkeyboards
```
results in: 
```
AT keyboard: input/event4
```

---

### Post by Favux on 2012-07-02
Well shoot.  So you have the right event number.

So what output do you get when you enter?
```
sudo /lib/udev/keymap -i input/event4
```

And if you haven't already be sure to run:
```
sudo /lib/udev/keymap input/event4 > ~/orig-map.txt
```
so you have a record of the original udev keymap.  And come to think of it, check the contents and make sure the stuff is in it.

---

### Post by Cobuntu on 2012-07-02
The terminal is going nuts and scrolling down endlessly until I press ESC. But I guess this is a good thing?

---

### Post by Favux on 2012-07-02
YES!

Ha, it is sounding like the problem is less isn't installed.  I thought it was by default, but maybe I did it so long ago I forgot?  So let's see what happens when you do:
```
sudo apt-get install less
```

---

### Post by Cobuntu on 2012-07-02
Hmm, I guess not:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
less is already the newest version.
The following packages were automatically installed and are no longer required:
  libhsqldb-java libservlet2.5-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Favux on 2012-07-02
Darn.

OK, it looks like because fujitsu-tablet.ko is assigning the button we can't get the scan code.  So it is styming us even though the assignment it is making is useless to you.

So I need to do a complete rethink on how to do this.  Ouch.

What we know so far is the two bezel scroll buttons are being assigned to:
XF86ScrollDown
and
XF86ScrollUp

The X Server reserves buttons 4 thru 7 for vertical and horizontal scroll.

So I suspect we could get a reaction if we could change:
XF86ScrollDown to Button4 (004)
and
XF86ScrollUp to Button5 (005)

Don't know for sure those are the right ones but not many combinations.  Which is a problem since subtracting 8 from the X keycodes there results in negative numbers for the kernel keycodes which aren't allowed.  But even if we could but then we'd likely get the same problem as the HP Elitebooks.  Since their buttons and not scroll wheels you'd get a keypress and keyrelease and it would only "scroll" one line.  So instead it would be better to use:
XF86ScrollDown to keycode 112 = Prior NoSymbol Prior
and
XF86ScrollUp to keycode 117 = Next NoSymbol Next

Hmmm.

---

### Post by Favux on 2012-07-02
Alright, the logical thing to do is uninstall the fujitsu-tablet.ko from MagickExtras.  The uninstall instructions are in the fujitsu readme.

Then try running the:
```
sudo /lib/udev/keymap -i input/event4 | less
```
command and see if we can get them.  Don't forget to restart once you've cleared it out.

We already know fujitsu-tablet.ko works because Magick works with it.  If that works then in the HOW TO you'll tell folks to do that before they install fujitsu-tablet.

I'm looking at the fujitsu-tablet.c code and it doesn't have the scan codes in it.  The old ones used to (check the dell-wmi.c code in MagickExtras) so I guess when they switched to the short keymap method that changed how they do things.  Making it harder to figure out what's going on.

Edit:  By the way the Rotate bezel button may give a result now before you remove fujitsu-tablet.ko.  You may want to check that.

---

### Post by Cobuntu on 2012-07-02
Hey Favux, I think you lost me with #15 - is there something I should have done in it? 

I uninstalled fujitsu-tablet.ko according to Fujitsu readme but /usr/src/MagickExtras/fujitsu-tablet-20120404-gerlach remains?

None of the buttons gives me any response in xev now and MagickRotation no longer works?

Running 
sudo /lib/udev/keymap -i input/event4 | less
is not doing anything I can see in the terminal, but when I leave it open and go to other applications it seems to scroll down or do something in the background - then when I tried to close the terminal it reopened several terminals and was scrolling down within one of them. When I repeated the command after a restart it was similar with a Nautilus window. In both cases it stopped when I managed to close the original terminal window...?

---

### Post by Favux on 2012-07-02
No, I was just thinking out loud in post #15.

Well that bites.  What am I missing?

What happens if you press one of the bezel keys now and run?
```
sudo dmesg | grep atkbd
```
or
```
sudo dmesg | grep [Uu]nkown
```

---

### Post by Cobuntu on 2012-07-02
I suppose it is also dmesg and not demesg in the second command? With both nothing happens.

---

### Post by Favux on 2012-07-02
Yep, a typo.

See anything in /var/log/kern.log?  Say with:
```
cat /var/log/kern.log
```
after you press a bezel button?

---

### Post by Favux on 2012-07-02
I just discovered that ***/lib/udev/findkeyboards*** may not give you the correct event#.  Apparently there can be two and the one you want may be one higher.  So try running:
```
sudo /lib/udev/keymap -i input/event5
```
You can check if there are two event numbers by running:
```
ls /dev/input/by-path
```
and/or
```
ls /dev/input/by-id
```
Also remember the event number can change with a reboot.  So you should check again that you are using the correct one when you restart.


Edit:  Absolutely beautiful.  I think I figured out how to make it behave without using less!  Apparently the the reason it scrolls away is because the enter you use to enter keeps being seen as a repeating return.  In other words there is no time for a key release of enter.  So you just add a sleep:
```
sleep 1; sudo /lib/udev/keymap -i input/event5
```
And ta da!  Perfect behavior.  Finally, it feels like we might be making some progress.

---

### Post by Cobuntu on 2012-07-03
No changes in kern.log after pressing the bezel buttons.

Nothing happening but also no crazy stuff going on after:
sudo /lib/udev/keymap -i input/event5

```
ls /dev/input/by-path
pci-0000:00:1d.0-usb-0:1.3:1.0-event  platform-i8042-serio-4-event-mouse
platform-i8042-serio-0-event-kbd      platform-i8042-serio-4-mouse
``````
ls /dev/input/by-id
usb-Chicony_Electronics_Co.__Ltd._CNF8248-event-if00
```

No effect after: 
```
sleep 1; sudo /lib/udev/keymap -i input/event5
```


EDIT: I am not sure if this is what we are looking for, I guess this is still just entering a new line after the other all over again but with no additional crazy stuff going on:
```
sleep 1; sudo /lib/udev/keymap -i input/event4
```

---

### Post by Cobuntu on 2012-07-03
I just noticed: I am no longer getting any output on xev from the bezel buttons!

---

### Post by Favux on 2012-07-03
Right, that's because the fujitsu-table.ko isn't installed.  What we want to do is change the X keycodes xev (X event) is showing, since they don't do anything for you.  So we want to change the corresponding kernel keycodes.

Let's move a step back up the chain and see what your results for the **showkey** commands are when you aren't in X <ctrl-alt-F1>.  That's "**a) kernel codes**" in appendix 2 on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").  That'll give us a starting point, and hopefully something to work with.

Next you'll check for other event numbers like I talked about above.  And then you'll re-install the fujitsu-tablet.ko from Magick and see if you can get output with it installed.  With both of these we're looking for the scan codes we can use for setkeycodes.

Found a nice little summary of what we're trying to do:  [https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes)  Wish I had found it ages ago.  Had to figure it out for myself.

---

### Post by Cobuntu on 2012-07-03
Ok, thanx for clearing that up to me.

Unfortunately I am not getting anything from showkey -s or showkey -k after leaving X.
Also my event number never changed so far, no matter when I checked,  /lib/udev/findkeyboards always gave me AT keyboard: input/event4
 
 After reinstalling the fujitsu-tablet.ko from Magick I am getting an output on showkey -s and showkey -k:

 **1=1___(in blue) A____(in white) scroll key down**
 showkey -s:
 0xe0 0x0f
 0xe0 0x8f
 showkey -k:
 keycode 178 press
 keycode 178 release
 
**2=2___(in blue) B____(in white) scroll key up**
 showkey -s:
0x75
 0xf5
 showkey -k:
 keycode 177 press
 keycode 177 release
 
**3=3___(in white) screen rotation symbol**
 showkey -s:
0x6b
 0xeb
 showkey -k:
 keycode 153 press
 keycode 153 release
 
**4=4___(in blue) Fn**
 showkey -s:
0x1d
 0x9d
 showkey -k:
 keycode 29 press
 keycode 29 release
 
**5=ENT___ (in white) ALT**
 showkey -s:
0x38
 0xb8
 showkey -k:
 keycode 56 press
 keycode 56 release

---

### Post by Favux on 2012-07-03
Nice job!  :)

OK, so nothing talks to the bezel keys but fujitsu-tablet.ko and it is mandatory to install if we want to communicate with them.

Which hopefully means the reason we couldn't get anything with 
```
sudo /lib/udev/keymap -i input/event4
```
is /lib/udev/findkeyboards was giving us the wrong event number.  With luck it is one number higher than listed but you can also check with the by-id or by-path commands.  At worst we can just try each event# in /dev/input until we get something.

Also apparently another possibility is the fujitsu-tablet module itself may have an event number.  So run:
```
xinput list
```
and post the output of that.  Check if we see anything.

---

### Post by Cobuntu on 2012-07-03
Favux, do you want me to deinstall fujitsu-tablet.ko again before trying all the numbers in /dev/input instead of      sudo /lib/udev/keymap -i input/event4
I see by-id or by-path in that folder as well, but how do I use those in what command?

```
xinput list
Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
    &#8627; Power Button                                id=11    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=12    [slave  keyboard (3)]
    &#8627; CNF8248                                     id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
```

---

### Post by Favux on 2012-07-03
```

```No, leave it installed for now on.

Ah hah.  I'll bet we want the event number for:
```
&#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
```
in your **xinput list** output!  And that was the problem.

Edit:
Run the following command in a terminal:
```
cat /proc/bus/input/devices
```
and post the output, especially for Fujitsu FUJ02BF.  That will tell us the event number.

---

### Post by Cobuntu on 2012-07-04
```
cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab54
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Fujitsu FUJ02B1"
P: Phys=FUJ02B1/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/FUJ02B1:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=1000300000000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Fujitsu FUJ02E3"
P: Phys=FUJ02E3/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=1000000000c00 300000 0 0

I: Bus=0019 Vendor=1734 Product=0001 Version=0101
N: Name="Fujitsu FUJ02BF"
P: Phys=FUJ02BF/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/FUJ02BF:00/input/input8
U: Uniq=
H: Handlers=sysrq kbd event8 
B: PROP=0
B: EV=100033
B: KEY=10000300000000 6000002000000 0 100000020000000
B: MSC=10
B: SW=22

I: Bus=0003 Vendor=04f2 Product=b169 Version=8911
N: Name="CNF8248"
P: Phys=usb-0000:00:1d.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Dock Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Dock Line-Out"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input14
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input15
U: Uniq=
H: Handlers=mouse0 event15 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103
```

---

### Post by Favux on 2012-07-04
Looks promising.  It says it's got keyboard input and it is on event8:
```
I: Bus=0019 Vendor=1734 Product=0001 Version=0101
N: Name="Fujitsu FUJ02BF"
P: Phys=FUJ02BF/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/FUJ02BF:00/input/input8
U: Uniq=
H: Handlers=sysrq kbd event8 
B: PROP=0
B: EV=100033
B: KEY=10000300000000 6000002000000 0 100000020000000
B: MSC=10
B: SW=22
```

---

### Post by Cobuntu on 2012-07-04
Wow!

```

sudo /lib/udev/keymap -i input/event8
Press ESC to finish, or Control-C if this device is not your primary keyboard
```**pressing button 1=1___(in blue) A____(in white) scroll key down**
```
scan code: 0x04   key code: scrolldown
```
**pressing button ****2=2___(in blue) B____(in white) scroll key up**
```
scan code: 0x05   key code: scrollup
```
**pressing button ****3=3___(in white) screen rotation symbol**
```
scan code: 0x06   key code: direction
```**pressing button ****4=4___(in blue) Fn**
```
scan code: 0x07   key code: leftctrl
```**pressing button ****5=ENT___ (in white) ALT**
```
scan code: 0x0F   key code: leftalt
```

---

### Post by Favux on 2012-07-04
Outstanding!  Nice job hanging in there.  :)

Now is xev showing the same thing as before for the bezel buttons?

After you check that we can start getting them working.  But in the meantime goodnight.

---

### Post by Cobuntu on 2012-07-04
Good Night Favux, you really earned your sleep!

I compared the new output to the one in #2, the lines with "state XXX, keycode XX (keysym ..." are identical, the rest being partly different is to be expected I guess?

```
xev
```[B]pressing button 1=1___(in blue) A____(in white) scroll key down
[/B]```
MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 36, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 1407306, (-504,189), root:(270,241),
    state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 1407456, (-504,189), root:(270,241),
    state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```**pressing button ****2=2___(in blue) B____(in white) scroll key up**
```
MappingNotify event, serial 38, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 38, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 1571728, (-299,242), root:(475,294),
    state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 1571868, (-299,242), root:(475,294),
    state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```**pressing button ****3=3___(in white) screen rotation symbol**
```
MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 36, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 3413038, (-743,513), root:(31,565),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 3413208, (-743,513), root:(31,565),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```**pressing button ****4=4___(in blue) Fn**
```
MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 36, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 3629334, (-627,85), root:(147,137),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 3629509, (-627,85), root:(147,137),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```**pressing button ****5=ENT___ (in white) ALT**
```
MappingNotify event, serial 40, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 40, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 3536285, (-282,351), root:(492,403),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 41, synthetic NO, window 0x6400001,
    root 0xae, subw 0x0, time 3536456, (-282,351), root:(492,403),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by Favux on 2012-07-04
There we go.  Finally there!  :)

I'll take a look in a bit.  Frankly at first glance I don't know why the results of **sudo /lib/udev/keymap -i input/event8** don't work.  I was assembling a preliminary keymap and I noticed that the Thinkpad X220t used ***direction*** for its rotation key also.

Right now I'm seriously distracted by a new discovery.  Apparently there has been a policy change in the ubuntuforums and they are forcing everyone to move their HOW TO's to the wiki.  What they have done is revoke the right to edit a post after 7 days.

The wiki has always had a poor search that made it nearly useless.  And search was incredibly slow.  Looks like they've changed it and search is faster but still worthless.  Also it doesn't allow attachments, which are often crucial.

They claim they have been notifying us of this impending change but that isn't true.  A sticky in the Tips and Tutorial section is not notification in my book.

So HOW TO's I've spent literally years on are worthless now.  I am very unhappy.

---

### Post by Cobuntu on 2012-07-04
Take your time Favux - and if you need my protest vote just tell me - you've been always there when I needed you, people like you make a forum great, not some little search improvement...

---

### Post by Favux on 2012-07-04
Thank you Cobuntu, I may need to take you up on that.

I sent a PM to the administrator (bodhi.zazen) asking him to restore editing priviledges to me for my HOW TO's.  Turns out there are eight of them I have been maintaining, several spread over multiple posts.  Who knew?  Since the administrators can still edit those posts I would think he can do that if he wants to.

OK, back to the matter at hand.  Let me look at your hard won information some more and then lets start with the scroll buttons.

---

### Post by Favux on 2012-07-04
Well I got a quick response saying no.  Move them to the wiki.  When I try to follow the links he gives to the Forum Council meeting that has this on its agenda I'm not allowed to view the meetings agenda.  Not looking good.  Like I feared one way or another I'll have to spend a lot of time on stuff I have zero interest in.  I am absolutely mystified as to why they feel the need to make this drastic change to the forums.


Starting with the scroll buttons let's give this a shot.  In /etc/rc.local using:
```
gksudo gedit /etc/rc.local
```
Change:
```
# By default this script does nothing.

exit 0
```
to:
```
# By default this script does nothing.

setkeycodes 0x04 104
setkeycodes 0x05 109

exit 0
```
and restart.  Do the buttons now "scroll"?

For your rotation button, what do you want it to do.  Rotate through 360 degrees?  Just go right and back?  Just left or inverted?

---

### Post by Cobuntu on 2012-07-04
So this forum will look similar like [https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes?](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes?) And if something changes an admin has to change it? So it is always like ping pong between the administrator and the actual problem solver? Doubles the work and makes information hidden on different levels so I as a dummy will have even more trouble to understand what's going on and who is able to help me? 
A wiki might look more professional but I have my doubts that it will be as vivid and effective...

My rc.local was not empty (hdparm -W0 /dev/sda), I tried it like this, but no scrolling after restart unfortunately (tested in a pdf and in Firefox):

```
# By default this script does nothing.
hdparm -W0 /dev/sda

setkeycodes 0x04 104
setkeycodes 0x05 109

exit 0
```

---

### Post by Favux on 2012-07-04
Well shoot.  Apparently we're not overiding the assignment.  Is it still the same in xev as it was before the rc.local change?

Since the rotate button doesn't seem to have anything assigned lets try adding that and see if you now see XF86Launch5 in xev for it.  Use:
```
setkeycodes 0x06 184
```


Not quite, the administrators have blocked anyone but themselves from editing posts on the forum that are more than 7 days old.  So if now you ask a question you'll be referred to the wiki page if there is one.  Then you come back to the forum and ask another question if you need to.

Yep, it should end up looking more professional because the wiki markup is nicer than the markup the forum posts have.

The problem from my point of view is the time.  Time spend transferring.  Time spent defending it from changes that the Wiki review board wants to make.  You know, "that doesn't belong on that page", "we don't want you to suggest doing this or that".  And so on.

Not to mention the always present potential of getting into editing wars with folks who don't agree with something and want to change page content to what they prefer.

You no longer control your content and are subjected to other's whims now.  I just don't want to spend time dealing with that sort of nonsense.  It does not interest me.

Wikis can be great tools but they aren't and shouldn't be the only option.  One of the big draws the Ubuntu forums has had is it allows options that the other ones don't.  That has made it friendlier.

---

### Post by Favux on 2012-07-04
I posted a poll.  Feel free to cast your vote:  [http://ubuntuforums.org/showthread.php?t=2016879](http://ubuntuforums.org/showthread.php?t=2016879)

---

### Post by Cobuntu on 2012-07-04
It shows "Voters: **4**. You may not vote on this poll" - where can I cast my vote or am I missing something in my profile?

Xev seems to be still identical.

Forgot to answer your question about the rotation button. Since the Gerlach-stuff does Rotate through 360 degrees, I think this would be the best setting.

Result for xev on Rotation Button
```
hdparm -W0 /dev/sda

setkeycodes 0x04 104
setkeycodes 0x05 109
setkeycodes 0x06 184

exit 0
```comming up here after restart:

no changes **pressing button **[B]3=3___(in white) screen rotation symbol
[/B]```
KeyPress event, serial 37, synthetic NO, window 0x5400001,
    root 0xae, subw 0x0, time 73798, (-618,107), root:(156,159),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x5400001,
    root 0xae, subw 0x0, time 73953, (-618,107), root:(156,159),
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by Favux on 2012-07-04
You should be able to select the vote option you want and then hit vote now.  I just voted and it worked fine.  You're over the 50 post limit so I can't imagine there is a restriction on you.


OK, back to the drawing board.  Apparently we don't need a udev keymap at all.  What Robert Gerlach has done in the fujitsu-tablet.ko has supplied all of that.  The only way to change things is probably to edit the fujitsu-tablet.c code.  Which would be ridiculous I suppose.

The problem appears to be although all of the kernel/udev stuff is setup correctly the X Server doesn't appear to know what to do with it.  Now I'm wondering if this means each bezel button needs a "wrap" like I've read about.  I only found one example of that being done and it involved what looked to be some pretty high level scripting.  I'll have to try to dig that up and see if I can make sense of it.

Last night I had found some more stuff on the key mapping chain and once again deluded myself into thinking I finally understood it.  Obviously not.  Oh well.  It's not that it appears so difficult it is that I can't find any complete coherent documentation.  Just bits and fragments.  By the time you find another piece of the puzzle you've begun to forget what you previously learned.

It is looking like the mystery is how the X Server takes the kernel keymap (as supplemented by udev mainly for ACPI related event keys like the bezel buttons) and transfers that information to its own separate keymap (xmodmap) when it starts up.  They aren't using the same keymapping table like you would think.  The X Server has its own separate one from the kernel and does things differently.  Plus it also talks to input devices directly like the kernel does.  No wonder it is such a mess.

---

### Post by Cobuntu on 2012-07-04
Thank you for this explanation, Favux. Can you also make me roughly understand  what the Gerlach-stuff is doing to make the buttons work?

---

### Post by Favux on 2012-07-04
It looks like he hardcoded in both the kernel scan codes and their associated keycodes like 'direction'.  So you don't need a udev keymap to supplement it like you do with say the Thinkpads.

Now the "wraps" I'm seeing are accessing information at **/sys/devices/platform** for example.  Do you see an new directory in there probably called **fujitsu-tablet**?  If you do what are the contents.  I'm not quite clear on how he's accessing the keys for his little function scripts or "wraps".  He's written a couple of udev rules but I'm not sure we need that.  See:  [http://jablonskis.org/author/zooz/](http://jablonskis.org/author/zooz/)

---

### Post by nema.arpit on 2012-07-05
Hi Favux
It been a long time :). I last talked to you regarding the tx2. It's bricked now and I have a T730.
There is only a **fujitsu-laptop** at that location, no **fujitsu-tablet**.
Sad to hear about the mess with the tutorials.

---

### Post by Favux on 2012-07-05
Hi nema.arpit,

It's very good to hear from you again!  Sorry to hear about your TX2, mine's still going strong.  But a Fujitsu T730 is nothing to sneeze at.

Good timing on the purchase with Magick now supporting them.  :)

Thanks for checking that directory.  I didn't think there would be.  When I last looked over the code I didn't see anything about putting output there like the HP's and Thinkpads do.  But Robert's code is so sophisticated I really can't follow it very well so I wasn't positive.  I was thinking of suggesting he add code to support /sys/devices/platform just to get a little consistency going.  That would mean the automatic rotation script could work with Fujitsu's too.  Not real sure why the kernel maintainers don't request that.

Yeah, I am very sorry about the tutorial mess too.  Doesn't appear I'm getting much support either which is even more disappointing.

---

### Post by Cobuntu on 2012-07-05
I can confirm what nema.arpit reported. So Robert Gerlach's button driver is still the only way to do this, right? Is there any clean way to install it at the moment, because the way I installed it was conflicting with MagickRotation I think or not really working on it's own: Scrolling up/down and rotation was working sometimes, but not all the time and rotation never came back after I installed MagickRotation (which is working perfectly).

Again, this was my crude way of getting it installed (before I installed MagickRotation):
This is how I installed in 12.04 x64:
< ppa was not working and  there are missing packages when you download fjbtndrv-2.3.2 and run  ./configure: it gives an error: Package requirements (x11 xi xext xtst)  were not met:
No package 'xi' found
No package 'xtst' found this did not work
> according to [http://katastrophos.net/andre/blog/2...0-u2010-u2020/]("http://katastrophos.net/andre/blog/2012/05/29/installing-ubuntu-12-04-precise-pangolin-on-fujitsu-u820-u2010-u2020/") run:
sudo apt-get install libxrandr-dev libxtst-dev libxi-dev libhal-dev
> then download latest driver to desktop: [http://sourceforge.net/projects/fjbtndrv/](http://sourceforge.net/projects/fjbtndrv/) and unrar
> cd /home/USER NAME/Desktop/fjbtndrv-2.3.2
> ./configure
> make
> sudo make install (do not forget that!)
> done, reboot
< nothing works in 12.04x64; some scripts are here: /usr/local/lib/fjbtndrv
> go to [https://launchpad.net/~khnz/+archive/ppa]("https://launchpad.net/%7Ekhnz/+archive/ppa")
then open for the latest available: [https://launchpad.net/~khnz/+archive...-archive-extra]("https://launchpad.net/%7Ekhnz/+archive/ppa/+sourcepub/1313773/+listing-archive-extra")  and download all 4 available .deb for the correct platform (i386/amd64)  and install in the following order (otherwise fjbtndrv will not  install): fsc-btns-kernel-source > fscd > fscrotd > fjbtndrv
RESTART

---

### Post by Favux on 2012-07-05
I think you're right Cobuntu.

At this point our best move is probably using the Oneiric fjbtndrv and dissasembling it.  If I remember right there were two scripts one of which was the automatic rotation script.  We just don't include that and Magick should work.

We'll have to look to be sure but I don't think we need to compile anything.  In fact we don't want to because that would replace the newer fujitsu-tablet.ko with an older one, which we don't want to do.

Plus that might then teach us enough to figure out how to make the bezel buttons work.

Good idea!  :)

---

### Post by Cobuntu on 2012-07-05
You said "good idea" but actually I have NO IDEA how to do that :-))
But of course I am willing to try anything you say ;-))

---

### Post by Favux on 2012-07-05
OK, let's give it a try.  I'll start taking a look at it.  I have a bunch of stuff on fjbtndrv somewhere from the last time I looked at it.

I'm going to be out and about doing chores so it may be a while.

---

### Post by Favux on 2012-07-05
Hmm.  It looks like we just need to compile and install fscd.c to get at least some of the buttons working.  It does seem like he's using a C program to talk to the bezel buttons.  There's some rotation stuff in there we might not need.  Hopefully we can ignore it and it won't interfere.

I did have a list of where the files went from working with someone else but can't find it now.  Of course.  Maybe I can figure it out from the Makefile.

---

### Post by Favux on 2012-07-05
Let's start off simple.  We'll just compile fjbtndrv and then install the parts we need.  Or think we need anyway, which is fscd.

Go to the fjbtndrv PPA:  [https://launchpad.net/~khnz/+archive/fjbtndrv](https://launchpad.net/~khnz/+archive/fjbtndrv)  and click on 'view package details".  Click on the Oneiric fjbtndrv-2.3.2-1.  Download onto your Desktop fjbtndrv_2.3.2.orig.tar.gz.  Open a terminal and run this command:
```
sudo apt-get install autotools-dev, pkg-config, libhal-dev, libx11-dev, libxi-dev, libxext-dev, libxtst-dev, libxrandr-dev, libxosd-dev
```
We shouldn't need libhal-dev anymore but I didn't try compiling without it.  Once the dependencies are installed right click on fjbtndrv_2.3.2.orig.tar.gz and extract it.  Now in the terminal run:
```
cd /Desktop/fjbtndrv-2.3.2

./configure

make
```
Do not run 'sudo make install'.  Now run the following commands in the terminal:
```
sudo cp src/fscd /usr/local/bin
sudo cp contrib/fscd.desktop ~/.config/autostart
```
And then restart.

---

### Post by Cobuntu on 2012-07-05
After 
```
sudo apt-get install autotools-dev, pkg-config, libhal-dev, libx11-dev, libxi-dev, libxext-dev, libxtst-dev, libxrandr-dev, libxosd-dev
```I am getting:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package autotools-dev,
E: Unable to locate package pkg-config,
E: Unable to locate package libhal-dev,
E: Unable to locate package libx11-dev,
E: Unable to locate package libxi-dev,
E: Unable to locate package libxext-dev,
E: Unable to locate package libxtst-dev,
E: Unable to locate package libxrandr-dev,
```How would you get those with one shot with a fresh installation? I checked all of them in Software Center and only autotools-dev was not installed on my system, so I installed this one via USC.

Everything else went through but I cannot restart for a couple of hours. I will post the result once I restarted.

---

### Post by Favux on 2012-07-05
That is weird.  I had the same problem and chalked it up to having done something to my system.  The couple I didn't have I installed one by one and that went fine.  So I have no idea why it won't do it in one shot.  My guess is one of the packages is to blame, maybe autotools-dev.  But I'm not going to install and uninstall them all in turn trying to find out.  :)

Good luck on the restart.  Here's hoping that at least the scroll buttons work now.  :)

---

### Post by nema.arpit on 2012-07-05
Hi Favux
I am not sure, but I think autostart is not playing well with multiple applications at startup. If I start dropbox daemon,  magick-rotation and following applications don't start. Similarly if I start magick-rotation then guake would not start, no idea about fscd. Maybe I'll add a delay line.
Anyhow, I did what you mentioned. Additionally to be sure, I ran fscd in terminal. I got the following error:
```
x11 initalisation failed

```

---

### Post by Cobuntu on 2012-07-05
Restarted: no buttons working but in xev the output is there and unchanged.

If I understand nema.arpit correctly this would explain perhaps, why after I installed MagickRotation the buttons seemed to no longer work.
I am also getting 
```
x11 initalisation failed
```after running fscd in terminal.

---

### Post by Favux on 2012-07-05
Well lets see, we're looking at for fscd.desktop:
```
[Desktop Entry]
Encoding=UTF-8
Name=fscd
Comment=Tablet PC helper
Icon=exec
Exec=/usr/local/bin/fscd
TryExec=/usr/local/bin/fscd
Terminal=false
Type=Application
Categories=
NotShowIn=
X-KDE-StartupNotify=false
X-KDE-autostart-after=panel
X-GNOME-Autostart-enabled=true
```
So we probably only need:
```

Name=fscd
Comment=Tablet PC helper
Icon=exec
Exec=/usr/local/bin/fscd
Type=Application

```
And then for a delay add:
```
X-GNOME-Autostart-Delay=3
```
at the bottom.

Are you using Gnome Shell 3.4?  It seems to have some autostart bug.
```
gnome-shell --version
```

---

### Post by Favux on 2012-07-05
OK.  We may need to make a directory and add some content to it.  I'm wondering if it is fscd-gui-nogui.o that is needed.  First check if you have a /usr/local/lib/fjbtndrv.  You shouldn't because we didn't do 'sudo make install'.  So make it:
```
sudo mkdir /usr/local/lib/fjbtndrv
```
Then while still in the fjbtndrv-2.3.2 folder run:
```

sudo cp src/fscd-fscd.o /usr/local/lib/fjbtndrv
sudo cp src/fscd-gui-nogui.o /usr/local/lib/fjbtndrv
sudo cp src/fscd-rotation.o /usr/local/lib/fjbtndrv

```

---

### Post by nema.arpit on 2012-07-05
I have **gnome-shell version 3.4.1**. I just made a startup script as a replacement. It does require a small delay or else it does not work correctly.
I **already** **had** the directory in /usr/local/lib/fjbtndrv. However, it was empty so no big deal.
I copied the 3 files. Ran fscd again. [B]No changes
[/B]```
[B]
arpit@arpitT730U:~/Desktop/fjbtndrv-2.3.2$[/B] sudo cp src/fscd-*.o /usr/local/lib/fjbtndrv/
**arpit@arpitT730U:~/Desktop/fjbtndrv-2.3.2$ **cd /usr/local/lib/fjbtndrv
**arpit@arpitT730U:/usr/local/lib/fjbtndrv$** ls
fscd-fscd.o  fscd-gui-xosd.o  fscd-rotation.o
**arpit@arpitT730U:/usr/local/lib/fjbtndrv$ **fscd
x11 initalisation failed


```

---

### Post by Favux on 2012-07-05
Darn.

Are we looking at an ABI, or is it API, change?  Going from the Oneiric to Precise X Server I mean.  I don't see any compile errors.  Did you?

I found a delay of 1 second was all that was needed, but it was needed.  I choose 3 seconds to be safe.

---

### Post by purple_goat on 2012-08-02
Did this ever work? I'm also getting "x11 initialisation failed"

that said I know nothing. Not even how to debug, which brings me to: [http://sourceforge.net/projects/fjbtndrv/forums/forum/695649/topic/4022196](http://sourceforge.net/projects/fjbtndrv/forums/forum/695649/topic/4022196)
I wanted to see if the error was in the same place but I don't know to debug. How do I debug? Could this help?

---

### Post by nema.arpit on 2013-05-18
I recently got the bezel buttons to work. It turns out everything is ok in the driver; the issue is that the X symbols linked to the buttons have no attached actions.
The fix is to reassign the actions associated with the buttons. One way would be to use xmodmap:
```
xmodmap -e "keycode 186 = Next"
```
As an example, the above code will assign page-down action to the A key.
The numerical value after keycode can be found in xev. The symbol after = should be for the action that needs to be performed (look in the keymap , "xmodmap -pke")
This can also be used to execute scripts/binaries. Eg: assign XF86Launch5 to the rotate button and then assign the keyboard shortcut XF86Launch5 to run the desired script ( in the display manager's keyboard settings like Application Shortcuts under xfce).
Hope this helps.

---

### Post by Cobuntu on 2013-05-19
Someone sent me something similar for the Fujitsu T902 I got a couple of month ago. The bezel buttons on the T902 differ, the printed symbols are from left to right:
Windows Button/Volume down/Volume up/Screen Rotation/A/B

Only the Windows Button/A/B seem to be recognized. Create a hidden text file in the home folder an name it ".Xmodmap". Put the following content in it:
   > ! for the panel keys (not all supported 

 ! Windows button 
 keycode 161 = F20 
 ! Button A 
 ! keycode 186 = XF86ScrollDown 
 keycode 186 = F24 
 ! Button B 
 ! keycode 185 = XF86ScrollUp 
 keycode 185 = F25 



Then just like nema.arpit mentioned you can assign actions to this. E.g. I assigned "Unity Grab Handles" to the Windows button.

---

### Post by nema.arpit on 2013-05-21
Hi Cobuntu
I have good news!!
I was able to modify the fujitsu-tablet.c to get all three buttons working.
**DISCLAIMER :** You do this at your own risk, I'm not responsible if something bad happens.

Edit the fujitsu-tablet.c in /usr/src/fujitsu-tablet-20120404-gerlach folder
```
sudo nano /usr/src/fujitsu-tablet-20120404-gerlach/fujitsu-tablet.c
```
Change the following :
```
static unsigned short keymap_Lifebook_Tseries[KEYMAP_LEN] __initconst = {
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_SCROLLDOWN,
    KEY_SCROLLUP,
    KEY_DIRECTION,
    KEY_LEFTCTRL,
    KEY_BRIGHTNESSUP,
    KEY_BRIGHTNESSDOWN,
    KEY_BRIGHTNESS_ZERO,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_LEFTALT
};
```

to
```
static unsigned short keymap_Lifebook_Tseries[KEYMAP_LEN] __initconst = {
    KEY_RESERVED,
    KEY_VOLUMEDOWN,
    KEY_VOLUMEUP,
    KEY_DIRECTION,
    KEY_SCROLLDOWN,
    KEY_SCROLLUP,
    KEY_DIRECTION,
    KEY_LEFTCTRL,
    KEY_BRIGHTNESSUP,
    KEY_BRIGHTNESSDOWN,
    KEY_BRIGHTNESS_ZERO,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_RESERVED,
    KEY_LEFTALT
};
```

then do a dkms remove; dkms build and dkms install again as per the fujitsu-tablet_README. And modprobe fujitsu-tablet
```

sudo rmmod fujitsu_tablet
sudo dkms remove -m fujitsu-tablet -v 20120404-gerlach --all
sudo dkms build -m fujitsu-tablet -v 20120404-gerlach
sudo dkms install -m fujitsu-tablet -v 20120404-gerlach
sudo modprobe fujitsu-tablet

```
The three keys should now show up in **showkey -s** or **xev**

Cheers!!

---

### Post by zottelmann on 2013-06-07
Hi!
I got a Lifebook T730 with Ubuntu 13.04 running. Now i try to get the buttons working, but im stuck while i try to install fjbtndrv. Terminal says:
```
/Desktop/fjbtndrv-2.3.2$ make
make  all-recursive
make[1]: Entering directory `/home/timo/Desktop/fjbtndrv-2.3.2'
Making all in src
make[2]: Entering directory `/home/timo/Desktop/fjbtndrv-2.3.2/src'
Making all in linux
make[3]: Entering directory `/home/timo/Desktop/fjbtndrv-2.3.2/src/linux'
make -C /lib/modules/3.8.0-24-generic/build M=/home/timo/Desktop/fjbtndrv-2.3.2/src/linux modules
make: Entering an unknown directory
make: *** /lib/modules/3.8.0-24-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[3]: *** [fujitsu-tablet.ko] Error 2
make[3]: Leaving directory `/home/timo/Desktop/fjbtndrv-2.3.2/src/linux'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/timo/Desktop/fjbtndrv-2.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/timo/Desktop/fjbtndrv-2.3.2'
make: *** [all] Error 2


```

Well, i'm more or less unexperienced with Ubuntu/Linux so any help would be nice ;)

Regards,

---

### Post by nema.arpit on 2013-06-07
It seems that you do not have the kernel headers
```
make: *** /lib/modules/3.8.0-24-generic/build: No such file or directory. Stop.
```
See here
[http://crunchbang.org/forums/viewtopic.php?id=8463](http://crunchbang.org/forums/viewtopic.php?id=8463)
Change the kernel version to your own (3.8.0-24-generic)

---

### Post by zottelmann on 2013-06-08
> **nema.arpit said:**
> It seems that you do not have the kernel headers
```
make: *** /lib/modules/3.8.0-24-generic/build: No such file or directory. Stop.
```
See here
[http://crunchbang.org/forums/viewtopic.php?id=8463](http://crunchbang.org/forums/viewtopic.php?id=8463)
Change the kernel version to your own (3.8.0-24-generic)

Hi,
thanks for your reply. It worked, but now im getting another error
```
make
make  all-recursive
make[1]: Entering directory `/home/timo/Desktop/fjbtndrv-2.3.2'
Making all in src
make[2]: Entering directory `/home/timo/Desktop/fjbtndrv-2.3.2/src'
Making all in linux
make[3]: Entering directory `/home/timo/Desktop/fjbtndrv-2.3.2/src/linux'
make -C /lib/modules/3.8.0-24-generic/build M=/home/timo/Desktop/fjbtndrv-2.3.2/src/linux modules
make[4]: Entering directory `/usr/src/linux-headers-3.8.0-24-generic'
  CC [M]  /home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.o
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:200:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘input_fujitsu_setup’
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:289:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fujitsu_dmi_matched’
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:299:15: error: ‘fujitsu_dmi_matched’ undeclared here (not in a function)
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:364:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fujitsu_walk_resources’
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:387:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acpi_fujitsu_add’
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:425:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acpi_fujitsu_remove’
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:444:13: error: ‘acpi_fujitsu_add’ undeclared here (not in a function)
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:444:3: error: initializer element is not constant
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:444:3: error: (near initialization for ‘acpi_fujitsu_driver.ops.add’)
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:445:13: error: ‘acpi_fujitsu_remove’ undeclared here (not in a function)
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:445:3: error: initializer element is not constant
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:445:3: error: (near initialization for ‘acpi_fujitsu_driver.ops.remove’)
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:446:3: error: unknown field ‘resume’ specified in initializer
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:243:13: error: ‘input_fujitsu_remove’ defined but not used [-Werror=unused-function]
/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.c:249:20: error: ‘fujitsu_interrupt’ defined but not used [-Werror=unused-function]
cc1: all warnings being treated as errors
make[5]: *** [/home/timo/Desktop/fjbtndrv-2.3.2/src/linux/fujitsu-tablet.o] Error 1
make[4]: *** [_module_/home/timo/Desktop/fjbtndrv-2.3.2/src/linux] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-3.8.0-24-generic'
make[3]: *** [fujitsu-tablet.ko] Error 2
make[3]: Leaving directory `/home/timo/Desktop/fjbtndrv-2.3.2/src/linux'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/timo/Desktop/fjbtndrv-2.3.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/timo/Desktop/fjbtndrv-2.3.2'
make: *** [all] Error 2


```

sadly, i'm too tired at the moment to investigate more on this(mabe tomorrow). If anyone has an idea where to go next, please don't hesitate ;)
Regards,

---

### Post by nema.arpit on 2013-06-08
Can you try compiling the fujitsu-tablet.ko from the Magick-Rotation tarball instead of from the fjbtndrv? I have not installed the fjbtndrv version.
Magick Rotation can be found here : [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation).
Follow the instructions from fujitsu-tablet_README.txt in the folder magick-rotation-1.6.2/MagickExtras/

---

### Post by zottelmann on 2013-06-13
Sorry for the late reply. It seems that magic rotation is not compatible with ubuntu 13.04.. I'm considering switching back to 12.10.

---

### Post by nema.arpit on 2013-06-13
You don't need to install magic rotation, just the fujitsu-tablet from the Magic Extras. I am reasonably sure that should install. It worked on my Debian Unstable install..

---

### Post by zottelmann on 2013-06-15
> **nema.arpit said:**
> You don't need to install magic rotation, just the fujitsu-tablet from the Magic Extras. I am reasonably sure that should install. It worked on my Debian Unstable install..


Hi, thanks again. I followed the instructions in the readme. First it got problems with the linux headers so i installed them. that worked so far and the next step is building it. Well i geot this error(with some steps i did before):
```

timo@timo-LIFEBOOK-T730:/usr/src$ cd fujitsu-tablet-20120404-gerlach/
timo@timo-LIFEBOOK-T730:/usr/src/fujitsu-tablet-20120404-gerlach$ sudo dkms add -m fujitsu-tablet -v 20120404-gerlach

Creating symlink /var/lib/dkms/fujitsu-tablet/20120404-gerlach/source ->
                 /usr/src/fujitsu-tablet-20120404-gerlach

DKMS: add completed.
timo@timo-LIFEBOOK-T730:/usr/src/fujitsu-tablet-20120404-gerlach$ sudo dkms build -m fujitsu-tablet -v 20120404-gerlach

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.8.0-25-generic -C /lib/modules/3.8.0-25-generic/build M=/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build....(bad exit status: 2)
ERROR (dkms apport): binary package for fujitsu-tablet: 20120404-gerlach not found
Error! Bad return status for module build on kernel: 3.8.0-25-generic (x86_64)
Consult /var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/make.log for more information.
timo@timo-LIFEBOOK-T730:/usr/src/fujitsu-tablet-20120404-gerlach$ 



```

i did what it said and looked at the logfile, but for me its not really understandable ;)
```

at Jun 15 16:48:06 CEST 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-25-generic'
  LD      /var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/built-in.o
  CC [M]  /var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.o
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:196:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘input_fujitsu_setup’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:288:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fujitsu_dmi_common’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:295:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fujitsu_dmi_lifebook’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:302:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fujitsu_dmi_stylistic’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:312:15: error: ‘fujitsu_dmi_lifebook’ undeclared here (not in a function)
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:330:15: error: ‘fujitsu_dmi_stylistic’ undeclared here (not in a function)
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:378:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fujitsu_walk_resources’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:401:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acpi_fujitsu_add’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:443:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘acpi_fujitsu_remove’
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:462:13: error: ‘acpi_fujitsu_add’ undeclared here (not in a function)
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:462:3: error: initializer element is not constant
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:462:3: error: (near initialization for ‘acpi_fujitsu_driver.ops.add’)
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:463:13: error: ‘acpi_fujitsu_remove’ undeclared here (not in a function)
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:463:3: error: initializer element is not constant
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:463:3: error: (near initialization for ‘acpi_fujitsu_driver.ops.remove’)
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:464:3: error: unknown field ‘resume’ specified in initializer
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:240:13: warning: ‘input_fujitsu_remove’ defined but not used [-Wunused-function]
/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.c:245:20: warning: ‘fujitsu_interrupt’ defined but not used [-Wunused-function]
make[1]: *** [/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build/fujitsu-tablet.o] Error 1
make: *** [_module_/var/lib/dkms/fujitsu-tablet/20120404-gerlach/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-25-generic'

```

i guess it would be easier, if i would fully understand what i am doing :D Again, any help is welcome.

regards,

---

### Post by nema.arpit on 2013-06-15
It turns out that the newer kernel is the culprit (sort-of). Look here:
[https://bbs.archlinux.org/viewtopic.php?pid=1278183#p1278183](https://bbs.archlinux.org/viewtopic.php?pid=1278183#p1278183)
Essentially, remove all instances of "__devinit" or "__init" or "__devexit" in the code.

---

### Post by zottelmann on 2013-06-16
Hello again,

with the corrections it compiled at least. I still had to "comment out" a .resume field in order to work. Whie doing dkms install, it printed following message:
```

Error! Module version 2.4 for fujitsu-tablet.ko
is not newer than what is already found in kernel 3.8.0-25-generic (2.5).
You may override by specifying --force.

depmod........

DKMS: install completed.



```

after rebooting nothing happend. I did an lsmod and there was a fujitsu_tablet entry. So maybe its just not working in Ubuntu 13.04? Well the error message says that there is a newer version, which is a bit confusing...

---

### Post by nema.arpit on 2013-06-16
Can you check if the tablet buttons give any output with xev? If you can already get keycodes in xev (the fujitsu-tablet.ko module should do this), then you don't need to compile anything. Just proceed to assigning appropriate functions using xmodmap.

---

### Post by zottelmann on 2013-06-17
thank you for your patience ;)

i searched "xev" in a wiki. i used the command " xev | grep keycode" to show only the keycodes. then i pressed the tablet buttons from left to right, which got me:

```

state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    state 0x0, keycode 186 (keysym 0x1008ff79, XF86ScrollDown), same_screen YES,
    state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    state 0x0, keycode 185 (keysym 0x1008ff78, XF86ScrollUp), same_screen YES,
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    state 0x0, keycode 161 (keysym 0x0, NoSymbol), same_screen YES,
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,

```
strangely the buttons seem to be pressed two times... but interestingly they have functions assigned, which are not working. except for the "alt" button.

---

### Post by nema.arpit on 2013-06-17
The buttons show up twice because each button has a keypress and a keyrelease event.
Since the keys show up in xev, you just need to reassign the keys. Either use a keyboard shortcut manager or try xmodmap (see post # 62 in this thread).
For keycode 161, you might want to assign the unused symbol "XF86Launch5". Then you can use this symbol as a shortcut to launch an application or script (like a rotation script).
You can make your xmodmap modifications automatic at reboot by adding the entries in the .Xmodmap file (create if does not exist) in your home folder.

---

### Post by zottelmann on 2013-06-17
> **nema.arpit said:**
> The buttons show up twice because each button has a keypress and a keyrelease event.
Since the keys show up in xev, you just need to reassign the keys. Either use a keyboard shortcut manager or try xmodmap (see post # 62 in this thread).
For keycode 161, you might want to assign the unused symbol "XF86Launch5". Then you can use this symbol as a shortcut to launch an application or script (like a rotation script).
You can make your xmodmap modifications automatic at reboot by adding the entries in the .Xmodmap file (create if does not exist) in your home folder.

Thanks alot for your help. I think i learned much here, even the compiling part was not necessary at the end ;)

---

### Post by msergiu80 on 2014-04-21
Hi guys,

A bit late but I would love my t730 to have auto rotate function. My bezel buttons are working,I have xrotate.py binded to my rotate button, Magick is woking and rotating the screen by sensing tablet mode but there is no way in the worl I can get the display to auto rotate. The Magick Rotation log shows rotations are detected but nothing happens.

23:22:28: cur_state: 3 
23:22:28: old_state: None 
23:22:28: calling rotation b: 
23:22:28: inverted
23:22:28: Change to Tablet mode
23:22:28: checking for rotation
23:22:28: /usr/bin/checkmagick32
23:23:38: killall checkmagick32
23:23:39: cur_state: 143 

Please help :)

---

### Post by broecker on 2014-05-03
You're not alone!
I try to use magick-rotate with a T4410 (nearly same Hardware) but within a week with a T730 too, with xubuntu 14.04 64bit.
In this moment, after nearly two hours, the rotation works, but the digitizer does not understand the direction, so it think, i write right down, while really writing left upper. 
The Buttons doesn't react.
No more time to test now, but i'll be back! :-) (here)

Mark Broecker

---

