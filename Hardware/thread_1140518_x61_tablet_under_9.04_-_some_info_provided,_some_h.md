---
title: "x61 tablet under 9.04 - some info provided, some help requested"
date: 2009-04-27
forum: Hardware
---

### Post by Nir Friedman on 2009-04-27
Just installed 9.04 after full release. Thought that I'd write up my experiences afterwards for testimonials. First though need to get some things working. I will also post any answers that get my stuff working at ThinkWiki to help other people. Okay, so let's get to it?

Installation: Kubuntu 9.04, April 23rd release. I left the Vista and recovery partition that came with the laptop. I shrank them to a total of around 75 gigs. My hard drive is 160 gigs, so out of the 85 remaining I put 6 gigs into swap, the rest to Linux. I used the ext3 file system, and 64 bit architecture. My specs are 1.6 core 2 duo, 3 gigs ram, integrated video. Resolution is 1024x768, no multi-touch. 

Installation (including shrinking of Vista partition) went very fast, no problems. After I started running it, things were good. I had a couple weird error messages telling me that things had crashed, but I couldn't actually find anything that had crashed either time. Boot time is impressively fast as well. It runs very smoothly on my OS overall. I turned on effects to see them; they run well but not quite perfectly. There's the occasional hiccup, but my laptop has no video card so that's fair. There's also occasional hiccups in other things, sometimes kickoff for example isn't as smooth as it should be. All in all though almost unnoticed. Standout features are the new krunner, as well as the plasmoids. Only annoying thing: the new kpackage. Adept was much better. Still it gets the job done and you don't have to look at it too often anyhow. Now, down to the meat of it:

Working
- All basic functionality
- Internet
- USB etc
- the tablet pen, but no eraser
- some special buttons: the volume works, but no mute (there is a work around though), the thinkvantage button yes, almost all fn+fN keys don't work, media keys work, forward/back keys work, brightness works
- middle mouse button, works at some level but it zooms me in and out of okular instead of scrolling. probably easily fixable.
- keys on front of tablet mostly work (esc and arrow keys), but tablet rotate does nothing and the button beside who's purpose I never knew doesn't work either
- Any of the buttons that do nothing, when I try to assign them to a shortcut I get a mesage that Qt does not support that button. I take this to be a positive b/c the computer for sure knows I am pressing the button.
- The old Vista installation still works :-)

To summarize what needs to be fixed:
 - volume mute, not a problem with the button because when I assign a different shortcut it still doesn't work. However if you reassign the key from mute to master HDA intel mute (in keyboard shortcuts in system settings)  then it mutes although you don't get any feedback. (credit goes to Pascal R., see link [https://bugs.launchpad.net/ubuntu/+bug/358168]("https://bugs.launchpad.net/ubuntu/+bug/358168").
 - The eraser on the pen. Help wanted!
 - Screen rotation. Help wanted!
 - Function Keys. Help wanted!
 - Middle mouse key. This one's not so urgent because I haven't even started playing with it and I think I can fix it myself. 

The ones I want help with, esp the first two I'm afraid to mess around with right now b/c most pre-Jaunty solutions involved the xorg file, and apparently a lot of those modifications can crash Jaunty. The function keys, if someone can just get me started (I know that there are some things you can do step by step to map out those keys, I just don't know what they are) I could probably play around with it and come back with more info. 
Cheers All!

PS Any highly recommended tablet software would also be appreciated.

---

### Post by anhonestfellow on 2009-04-27
This might help with the special keys, but I have not tried it myself:
 
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Mapping_keys_with_setkeycodes](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Mapping_keys_with_setkeycodes)

---

### Post by Favux on 2009-04-27
Hi Nir Friedman,

Anhonestfellow is right, and I think that first link I gave (the non-tablet X61) also had a lot on setting up your keys.  Usually you type "xev" in a terminal and it's little gui pops up.  You press the key of interest and hope the keycode pops up.  In the output you'll see something like keycode=153 or whatever.

Then you either setup a Xmodmap or do a keybinding.  For example to get your rotation button to work you want to find it's keycode and then bind it to a rotation script.  For some rotation scripts and a how to do keybinding see:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  Method 1 or 3 would probably work for you.

The 10-wacom.fdi has an entry for serial tablets and also has eraser and touch.  If you have a stylus button we could add that to it.  Or you could calibrate and configure some things through wacomcpl.  Type "wacomcpl" in a terminal.  Eraser only works in programs like Gimp where you have configured the input devices.  In Xournal the eraser is the stylus button if set as a right or middle mouse click.

---

### Post by Nir Friedman on 2009-04-30
Hey Favux,
some of the stuff there was handy, but I am kind of wary because from what I understand these seem to be 8.04 style solutions which involve editing the Xorg file. I was under the impression that in 9.04 these things could be better handled through HAL and that was the correct way to do them? No?

---

### Post by Favux on 2009-04-30
Hi Nir Friedman,

You are correct, in Jaunty we are suppose to be using the HAL/.fdi file method.  But think of the 10-wacom.fdi file as being = to xorg.conf.  They are both for configuration.  See:  [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

Or you could map the stylus button with wacomcpl, see section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Wacomcpl generates a .xinitrc file that is applied after the 10-wacom.fdi file, and can add to or replace it.

---

### Post by Nir Friedman on 2009-05-03
Okay, new discovery, I have found that my pen's other button actually works but as a middle click rather than as a right click. Should I post my 10-wacom.fdi file? I'm reading through it but I can't find anything obvious on how to make the modification. Also: when I try to run wacomcpl it runs but then when it offers me to select the device there are no devices there. Thanks for all your help Favux.

---

### Post by Favux on 2009-05-03
Hi Nir Friedman,

Not a problem.  With wacomcpl it looks like you've discovered a bug with the Wacom setup in Jaunty.  HAL/D-BUS is returning names linuxwacom doesn't understand.  When you type in a terminal:
```
xsetwacom list
```
you should see linuxwacom names like stylus and eraser.  If it's blank you have the "bug".  To see what HAL is using instead of stylus and eraser type:
```
xinput --list
```
If things were working it would return stylus and eraser and some other things like keyboard.

We are waiting for a fix.  In the meantime there are a few work arounds.

You could either figure out what names are being used for stylus and eraser and rename everything or you could use rec's script to translate the HAL stuff back to linuxwacom names so that wacomcpl will work.  See Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  If you decide to use rec's script (called wacomtohal) that's all you need to do.  Just install the script.  You can ignore the other stuff which is for usb tablet pc's and yours is serial.

---

### Post by geedew on 2009-05-16
I seem to have most of your issues fixed, see my blog

[http://geedew.com/blog/x61-tablet-ubuntu/](http://geedew.com/blog/x61-tablet-ubuntu/)

---

