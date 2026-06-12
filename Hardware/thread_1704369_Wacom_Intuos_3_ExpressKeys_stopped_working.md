---
title: "Wacom Intuos 3 ExpressKeys stopped working"
date: 2011-03-10
forum: Hardware
---

### Post by marcchristopher on 2011-03-10
Long time lurker, first time poster...


Hi all!

This problem has been driving me crazy for weeks now and I can't seem to find a solution in any of the forums. Which is why I'm posting it here...

Up to a few weeks ago, my **Intuos3** tablet was working perfectly. It wasn't straightforward to set it up (especially the ExpressKeys), but in the end everything worked like a charm.

Now, a few (automatic) updates later, the **ExpressKeys** have stopped working completely. And I can't seem to find the problem. To test the tablet itself I even plugged it into my netbook: There my Intuos3 tablet still works perfectly.

In both cases I'm using the command
```
xsetwacom set 'Wacom Intuos3 6x8 pad' Button1 'key c'
``` to set the ExpressKeys. Both my desktop and my netbook are running Ubuntu Maverick with Linux kernel 2.6.35-26 and xserver-xorg-input-wacom version 0.10.8-0ubuntu1. I haven't updated my netbook quite as often, though... so, I'm guessing one of the recent updates must have caused the problem.

But which one?

Any help would be much appreciated.
Thanks in advance,
Marc

---

### Post by Favux on 2011-03-10
Hi marcchristopher,

A lot of folks are having a problem with the recent updates (last week or so) in Lucid and Maverick.  I still haven't figured out what's going on.

Check that your "device name" for the command hasn't changed:
```
xinput list
```
You say you are using xserver-xorg-input-wacom version 0.10.8-0ubuntu1 but if you installed say IRIE's PPA the parameter name for buttons changed, adding a space before the number.  So for example Button1 is now Button 1 starting with xf86-input-wacom-0.10.11.

Using the get command with the device name you can check the current button setting, e.g.:
```
xsetwacom get "Wacom Intuos3 6x8 pad" Button1
```
Some tablets have button mapping issues depending on the kernel.  Usually it happens with Button4 actually being Button8 and Button5 Button9 and so on.  So check that and see if the button mapping got weird.

Also worth checking out the contents of the 50-wacom.conf in /usr/share/X11/xorg.conf.d and make sure they're ok.

---

### Post by marcchristopher on 2011-03-11
Thanks, Favux, for the quick reply.

Originally, I had version 0.10.11 of xserver-xorg-input-wacom installed. When the ExpressKeys stopped working (and I found that the tablet still worked with version 0.10.8 on my netbook) I thought, this new version was the problem. So I removed all PPAs from my sources.list and downgraded the Wacom driver to 0.10.8. No luck, though.

Thank you for your suggestions regarding the space in the parameters and the button mapping issues. I will check that as soon as possible. Frankly, I can't think of a reason why this should be the problem, though... Both the kernel version and the Wacom driver are the same on the desktop and the netbook now. So, I guess, some other package must be causing the problems...

Hmm...

---

### Post by marcchristopher on 2011-03-14
So, I tried adding an additional space to the xsetwacom-command, checked the device name and the button mapping issues you mentioned... still no luck getting my ExpressKeys to work again.

I also tried
```
xsetwacom get "Wacom Intuos3 6x8 pad" Button1
```Strangely, the result ist simply the number 1. And this doesn't change, no matter what I do. For button 2, the result is the number 2, by the way... and so on.

And ideas? What else could I try?

Thanks,
Marc

---

### Post by Favux on 2011-03-14
Well a couple of things have happened in the last few days, so it depends on which xf86-input-wacom you actually have.

First check in /usr/local/bin for the xsetwacom executable binary (it should be in /usr/bin). This may mean you forgot the '--prefix=/usr' flag on the xf86-input-wacom configure line. In which case you may have a xsetwacom executable in both locations and are experiencing version conflict. Delete the one in the wrong location, i.e. /usr/local/bin.  I'd assume the one in /usr/bin is the one from Ubuntu's default xf86-input-wacom-0.10.8 package, so there shouldn't be a version conflict between it and the package.  But you might want to go into Synaptic Package Manager and tell it to reinstall xserver-xorg-input-wacom version 0.10.8-0ubuntu1 to be sure.  Then reboot of course.

If you were still using 0.10.11+ they broke the key (but not number) assignment for the pad.  They're working on the fix which hopefully will be out this evening.  Also the pad may have been broken for the Graphire's and early Bamboo's a while ago and a fix was just submitted yesterday.  Don't know if that applies to your Intuos3 though.

---

### Post by marcchristopher on 2011-03-16
First of all, Favux, thank you very much for your help. Much appreciated.

I checked in /usr/local/bin and indeed found a xsetwacom binary, version 0.10.6. Having deleted this file, I now have my old xsetwacom 0.10.8 back.

Funnily, Button1, Button2 and Button3 are working now. I can't seem to get the other ExpressKeys (4 to 8) to work, though. I always had problems with the Strips (StripLUp, StripRDn and so on), but I do remember that at least all the ExpressKeys did work with version 0.10.8.

So, I tried version 0.10.99 from the IRIE PPA. I'm not sure, however, how I'm supposed to set the buttons now, with the new parameter names. The command
```
xsetwacom set 'Wacom Intuos3 6x8 pad' Button1 'key c'
```doesn't work anymore, and
```
xsetwacom set 'Wacom Intuos3 6x8 pad' Button 1 'key c'
```doesn't seem to do anything. Am I misunderstanding anything here?

---

### Post by marcchristopher on 2011-03-16
I just tried version 0.10.11 of xsetwacom and the commands for setting the buttons now work as expected:
```
> xsetwacom set "Wacom Intuos3 6x8 pad" Button 3 "key c"
> xsetwacom get "Wacom Intuos3 6x8 pad" Button 3
key +c -c 
```Only for buttons 1 to 3, though. Can't seem to get Button 4 to Button 8 to work. Setting them in the usual way gives the same result:
```
> xsetwacom set "Wacom Intuos3 6x8 pad" Button 4 "key c"
> xsetwacom get "Wacom Intuos3 6x8 pad" Button 4
key +c -c 
```Nothing happens, when they are actually pressed, though. The buttons do seem to be functional...

xev for Button 1:
```
KeyPress event, serial 38, synthetic NO, window 0x5600001,
    root 0xb8, subw 0x0, time 7311050, (76,113), root:(836,168),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XmbLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x5600001,
    root 0xb8, subw 0x0, time 7311050, (76,113), root:(836,168),
    state 0x0, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (63) "c"
    XFilterEvent returns: False

MotionNotify event, serial 38, synthetic NO, window 0x5600001,
    root 0xb8, subw 0x0, time 7311050, (76,113), root:(836,168),
    state 0x0, is_hint 0, same_screen YES
```xev for Button 4:
```
ButtonPress event, serial 37, synthetic NO, window 0x5600001,
    root 0xb8, subw 0x0, time 7258730, (138,148), root:(898,203),
    state 0x0, button 8, same_screen YES

MotionNotify event, serial 37, synthetic NO, window 0x5600001,
    root 0xb8, subw 0x0, time 7258730, (138,148), root:(898,203),
    state 0x0, is_hint 0, same_screen YES

ButtonRelease event, serial 37, synthetic NO, window 0x5600001,
    root 0xb8, subw 0x0, time 7259810, (138,148), root:(898,203),
    state 0x0, button 8, same_screen YES
```

---

### Post by Favux on 2011-03-16
My guess would be Button 4 is Button 8 and Button 5 is Button 9 and so on.  That's due to some esoteric button mapping issues that cropped up and are fixed in newer kernels (like 2.6.37? and up).  Luckily xev confirms 4 is button 8 in the press and release events.

---

### Post by marcchristopher on 2011-03-16
Thank you so much!
Programming button 8 indeed worked for button 4. I finally have my ExpressKeys back.

(Now, if only somebody could tell me how to programm the two Strips... ;) but that's a minor problem... I can live without them...)

Thanks again,
best,
Marc

---

### Post by Favux on 2011-03-16
Strips shouldn't be a problem.  What do you want them to do?  Here's a sample:
```
xsetwacom set "Wacom Intuos3 6x8 pad" StripLDn "key minus"  # zoom out
xsetwacom set "Wacom Intuos3 6x8 pad" StripLUp "key shift plus"  # zoom in

xsetwacom set "Wacom Intuos3 6x8 pad" StripRDn "key alt down"  # brush radius (must be mapped in GIMP)
xsetwacom set "Wacom Intuos3 6x8 pad" StripRUp "key alt up"

```
I've got other examples at the linux wacom project mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

### Post by marcchristopher on 2011-03-16
Well, I tried to program the strips a few times, but never got them to work. Not even "back in the days", when I didn't had these version conflicts...

```
> xsetwacom set "Wacom Intuos3 6x8 pad" StripRDn "key minus"
Unknown parameter name 'StripRDn'.
> xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key minus"
> xsetwacom get "Wacom Intuos3 6x8 pad" StripRightDown
0
> xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key a"
> xsetwacom get "Wacom Intuos3 6x8 pad" StripRightDown
0
```

The weirdest thing (to me) is that when I hit the strips a few times (I guess a double click is sufficient), my system performs a "log out" (killing all running programs). So, trying this over and over has got me a bit annoyed.

EDIT: I just noticed, I can kill the system even with a single click on one of the strips... :/

---

### Post by Favux on 2011-03-16
Thanks for reminding me I have to update the strips to the new parameter names.

Hmm.  No clue why a strip is crashing X.  I thought they fixed them and I don't remember that ever being a problem, just them not working. And that's with the latest xf86-input-wacom cloned?

You've verified with *xinput list* that you are using the correct "device name", i.e. "Wacom Intuos3 6x8 pad"?

You could run:
```
xsetwacom set "Wacom Intuos3 6x8 pad" TabletDebugLevel 12
```
and see if the reason for the crash is captured in your Xorg.0.log in /var/log.

---

### Post by marcchristopher on 2011-03-16
Frankly, I don't know, if I'm using the latest xf86-input-wacom cloned. I'm working with version 0.10.11 now; 0.10.99 (from the IRIE PPA) didn't allow me to set the ExpressKeys. And I'm definitely using the correct device name: it's the same as for the buttons, isn't it?

I will look up the crash in the log in a moment...

---

### Post by Favux on 2011-03-16
Right, buttons and strip are on the pad so the same device name.  OK, with IRIE's you are about a week or two behind.  They fixed the key assignment bug last night so a current clone should have everything working.  Don't know about the crash issue.

---

### Post by marcchristopher on 2011-03-16
Okay, here's what happens:

```
> xsetwacom get "Wacom Intuos3 6x8 pad" StripLeftDown
5
> xsetwacom get "Wacom Intuos3 6x8 pad" StripRightDown
5
> xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "key s"
> xsetwacom get "Wacom Intuos3 6x8 pad" StripLeftDown
2
> xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key s"
> xsetwacom get "Wacom Intuos3 6x8 pad" StripRightDown
0
```

Clicking StripRightDown now crashes X. StripLeftDown doesn't. Nothing in /var/log/Xorg.0.log, though.

By the way, is IRIE's a good PPA to use? Should I try a different PPA?

---

### Post by Favux on 2011-03-16
OK the key assignments don't seem to be working with that version of xf86-input-wacom.  Part of the button mapping issue we talked about is Button #'s 4,5,6,7 are reserved for scrolls in Xinput and that seems to be what is being returned.  The driver tries to work around that so Button 4 is 4 and not 8, but it doesn't always work as you've seen.

IRIE's PPA seems pretty good because he's been good about updating it.  Martin Owen just updated his and there's another one around I think.  But it really depends on what you're asking it to do.  For example because he use's input-wacom IRIE's is best for the Bamboo P & T's.

I'm thinking if the strips are important to you you might want to remove the PPA's and clone the xf86-input-wacom git repository.  See part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by Favux on 2011-03-18
Hi marcchristopher,

Jason spotted the bug that's causing the crash with the strip.  A commit on 1-14-11 forgot to include the 'wheel_keys' and 'strip_keys' 
in the update.  He just submitted a fix so the earliest it will be committed would be Sunday evening.

---

### Post by squiregrand on 2011-04-08
Hi All, 

I'm having trouble with the express keys on my intuos3 aswell, but it sounds like a slightly different problem. My right hand expresskeys don't appear to register at all. 'xev' shows no response at all when I press them. 

I'm only just setting it up on Ubuntu for the first time so all the problems are fresh, unlike marcchristopher. I've been following these posts intently and I think I've figured it all out, but another problem has arisen.

  I've tried 
```
xinput query-state "Wacom Intuos3 6x8 pad"
``` whilst holding down the buttons, but nothing there either.
I tried to find out if the buttons where called something else but all I got was this:
```
xinput get-button-map "Wacom Intuos3 6x8 pad"
0 1 3 4 5 6 7 8 9 10 11 12
```I worked out that button 4 was really button 8 because of the result I got when I pressed it, but assigning comands to numbers 9, 10, 11 and 12 haven't worked (nor 4,5,6,7).

Here's the commands which I've given the buttons, it's based on Favux's sample from [']("http://ubuntuforums.org/showthread.php?p=10213575")[B][HOW TO set up a Waltop tablet in Lucid & Maverick' ]("http://ubuntuforums.org/showthread.php?p=10213575")
[/B]```
xsetwacom set "Wacom Intuos3 6x8 pad" Button 1 "key r"  # rectangular selections
xsetwacom set "Wacom Intuos3 6x8 pad" Button 2 "key ctrl shift a"  # select none
xsetwacom set "Wacom Intuos3 6x8 pad" Button 3 "key p"  # paintbrush
xsetwacom set "Wacom Intuos3 6x8 pad" Button 8 "key ctrl z"  # undo
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown "key minus"  # zoom out
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp "key shift plus"  # zoom in

xsetwacom set "Wacom Intuos3 6x8 pad" StripRightDown "key alt down"  # brush radius (must be mapped in GIMP)
xsetwacom set "Wacom Intuos3 6x8 pad" StripRightUp "key alt up"
xsetwacom set "Wacom Intuos3 6x8 pad" Button 9 "key alt 0"  # brush default - map in gimp
xsetwacom set "Wacom Intuos3 6x8 pad" Button 10 "key ctrl x"
xsetwacom set "Wacom Intuos3 6x8 pad" Button 11 "key shift ctrl n"  # new layer in gimp
xsetwacom set "Wacom Intuos3 6x8 pad" Button 12 "key ctrl v"  
```

I'm pretty sure I've got the most up to date driver, I cloned the xf86-input-wacom git repository today (but for some reason synaptic says I'm still using 0.10.8 version of xf86-input-wacom). My kernel is 2.6.35-28-generic and I'm running Ubuntu 10.10

Any help would be apreciated, can't find any info on a problem like this on the forums. Thanks in advance for any help.:D

T

---

### Post by Favux on 2011-04-08
Hi squiregrand,

Welcome to Ubuntu forums!

Everything looks correct, nice job.  I'm wondering if it's a hardware problem or bug.  To rule out hardware problems do all the express keys work in Windows?

Because you compiled xf86-input-wacom it's not registered in the package manager.  So to get the version number enter in a terminal:
```
xsetwacom -V
or
xsetwacom --version
```
It should be 0.10.99.2.  It should also be in your Xorg.0.log in /var/log.

If it's a bug your timing is good.  They are doing bug squashing for the next week or two prior to bringing out 0.11.

A sample Intuous3 script is attached to the bottom of the #2 post on the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also see the linux wacom project's mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

Try entering *set* and *get* commands seperately for each non-responding button in a terminal and see if you get a descriptive error message.

---

### Post by Favux on 2011-04-10
Hi squiregrand,

I'm pretty sure they just fixed your issue with the *Fix higher button events* commit that was just added to the xf86-input-wacom git repository.

---

### Post by squiregrand on 2011-04-23
Hi Favux, Thanks.

The terminal says I'm running 0.10.99 of xsetwacom. Having cloned the git repository, how do I upgrade/access advances? Does it happen automatically or is there something I have to do?

I tried to find info on the difference between repositories and Git's but came out blank.

my right hand stip has started working, but still not the buttons, could that be because of the change you mentioned?

Thanks again for the help. Hope you're having success marcchristopher.

Sincerely,
T






__

---

### Post by Favux on 2011-04-23
> Having cloned the git repository, how do I upgrade/access advances? Does it happen automatically or is there something I have to do?
Version 0.11.0 just came out the other day.  A couple of commits have been added since to support the use of input tool serial numbers so cloning the git again will give you 0.11.0+.  If you still have the xf86-input-wacom folder you change directory into it and then run:
```
git pull
```
That will update xf86-input-wacom to the latest version of the git repository.  To get 0.11.0 you need to download the release tar:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)
> my right hand stip has started working, but still not the buttons, could that be because of the change you mentioned?

Not sure what's wrong with the buttons.  As far as I know they should be working if you get the button mapping correct.  You know if Button 4 is being seen as Button 8 etc.  I think they are planning on addressing that problem (scroll gestures having buttons 4 to 7 reserved) soon.

---

