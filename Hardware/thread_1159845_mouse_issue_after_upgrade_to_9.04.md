---
title: "mouse issue after upgrade to 9.04"
date: 2009-05-15
forum: Hardware
---

### Post by bishman on 2009-05-15
hi all

I have just upgraded my old compaq evo n610c to jaunty.

all seems well untill the mouse click will stop working in various places on the screen - the scenario is different everytime it happens. Currently only clicking in text boxes on this page works, but sometimes i am only able to click launchers ib the panel - i can't move windows around or anything else.

The keyboard works - except for the fact that i can't alt-tab to switch windows, which goes along with the mouse click issue (hopefully, this is a key point as to what the problem is).

The only way out to stop it is to alt-ctrl-backspace or reboot, or wait for the issue to randomly correct itself - which it does somtimes.

Does anyone know anything that could help? Need more info - let me know

---

### Post by mmorgan27 on 2009-05-16
I have no solution I just wanted to let everyone know I'm seeing the exact same thing.  It's a difficult issue to describe but basically:
[LIST=1]
[*]clicking on MOST (sometimes all) windows/buttons does nothing (you can't raise other windows)
[*]you can still move the mouse pointer
[*]restarting the XServer does not necessarily fix the problem
[*]the issue spontaneously fixes itself (randomly?)
[*]the mouse pointer does not change shape when you mouse-over a link
[*]does not seem to be related to any application
[*]killing the focused application fixes the problem
[*]problem occurs once 2 windows are open (I opened 2 gnome-terminal windows and it happened.)
[*]the problem is not exhibited in gnome safe mode
[/LIST]

The config files and logs are attached.

---

### Post by mmorgan27 on 2009-05-16
After going into Gnome safe mode and/or removing the $HOME/.gconfd/saved_state file the problem has disappeared.

---

### Post by bishman on 2009-05-16
hi mmorgan

Thats good news! i'll give that a go. I was looking at your files trying find similarities with mine that might be a problem but I don't really know enough to notice anything.

I will try your solution (hoopefully your cause is the same is mine), and if it's still a problem will post a log...

What does the saved_state file do? Is it something residual from before the upgrade?? It is in my /home partition after all..

---

### Post by mmorgan27 on 2009-05-16
I could only guess that saved_state is some sort of text-file database of the state of the gnome window manager (what apps were running, position of windows, etc.).  There seems to be other discussions on the Ubuntu forums regarding this file becomming corrupted and causing a wide range of quirky behavior.

Deleting it seems to have no adverse effects.  I've done it several times so far.

---

### Post by radioraheem on 2009-05-29
I am having the same issue after upgrading to 9.04.  So far I've tried several different methods of removing the $HOME/.gconfd/saved_state file and so far have had no luck.  

The only difference is I did see this happen in the gnome safe mode as well.  

I would really like to avoid doing a clean format if at all possible.  Help!!!  My system is completely unusable right now as a result of this problem.

:(

---

### Post by Maxplayer14 on 2009-05-30
I am having the same issue to and it's getting really frustrating.

It gets to the point where I can't switch tabs in FF or ATL Tab to anything.  Most of the time if I am in FF I can hit ALT+F and ESC and then can move between tabs or click, but I have to do that like 1000 times to get around.

I can't find any fix to this issue and it happened right after my upgrade to 9.04.

---

### Post by UrbenLegend on 2009-05-30
I am kind of shooting in the dark here, but maybe a compiz issue?

---

### Post by bishman on 2009-05-31
So far I have had no luck with deleting saved_state. I've also tried other things like restarting HAL while it is happening.

I can confirm the problem happens with visual effects disabled in the appearance settings... Does this mean it is not compiz causing it?

So it could be the video driver?? I have an ATI Mobility Radeon 7500 in a compaq evo laptop. What does everyone else have?

Or it could be an input device problem. evdev maybe?

I have tried many solutions relating to these in the forums but no luck.

I am almost at the point of reverting back to 8.10 or 8.04, but would prefer to sort this out... :)

---

### Post by bishman on 2009-05-31
ok... so I just found out for sure that the ati radeon 7500 is not support by the radeon driver anymore... Even though my screen works :)

But it could be a related issue... Anyone have any ideas as to how to get this going?

---

### Post by kiwi-pete on 2009-05-31
The problem I have with my mouse after upgrading to Ubuntu 9.04 Jaunty Jackalope 64 bit is that when the pointer is placed at the extreme bottom of the screen, it sticks there. I have to rapidly move the mouse to unstick the pointer. It make no difference what portion of the bottom screen the pointer is on nor what surface the mouse is on either.

---

### Post by UrbenLegend on 2009-06-01
> **bishman said:**
> ok... so I just found out for sure that the ati radeon 7500 is not support by the radeon driver anymore... Even though my screen works :)

But it could be a related issue... Anyone have any ideas as to how to get this going?

Uhm, where did you get this info? Seems strange how they would do such a thing. According to [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), it is supported

---

### Post by UrbenLegend on 2009-06-01
I don't think its a video driver issue since its displaying fine. Maybe your input devices are configured wrong in xorg.conf. Can you post it?

---

### Post by srb715 on 2009-06-03
I'd like to add that I too am having the issues described by the OP. The only things I have installed are the latest patches and the ms fonts.

To reiterate the issue:

* Clicking with the mouse (both the USB mouse and touchpad on my laptop) stops working reliably shortly after logging in. By the time I open Firefox and the NetworkManager applet pops up its alert, the mouse is broken.

* To remedy the issue temporarily and unreliably, I try any series of keyboard shortcuts such as CTRL+ALT+D and ALT+F2. Normally showing the desktop allows me to click on the Ubuntu menu or another window for a while, but that isn't guaranteed.

* Scrolling with the middle wheel stopped working halfway through this post. :\

* ALT+TAB works sometimes, but it rarely restores clicking functionality. 

The inability to click may actually be the result of a different issue. I say this because when I hover over a text field in FF or the Back and Forward arrows, the cursor doesn't change to the I and the buttons don't highlight like they usually do.

Another interesting issue is that when the mouse stops responding and I show the desktop, clicking and dragging indicates that I am attempting to drag one of the windows I just minimized. This is in contrast to the expected behavior of drawing a selection rectangle on the desktop.

I'm using a Dell XPS 1530 with an MX 1000 mouse.

On a semi-related note, I was having trouble with my mouse in 8.10 too. The solution there was to add i8042.nomux=1 when booting. I tried that fix for 9.04, but it didn't fix the issue. (Surprising, no?)

edit: I have attached my xorg.conf file. I see nothing exciting there.

---

### Post by Maxplayer14 on 2009-06-06
Yeah this is getting so annoying.  Sometimes I can use the computer for hours upon hours with an issue.  Sometimes it happens a few minutes after I boot into Unbuntu and open a browser to do something.

I can find no rhyme or reason behind the problem.  It's so random.

---

### Post by radioraheem on 2009-06-06
Mine isn't really random, and have never worked for longer than a few minutes.

---

### Post by Maxplayer14 on 2009-06-09
I can't believe there has been no resolution for this issue.  It's really really really starting to bug me.

---

### Post by abhinav302 on 2009-06-11
hey all,
i installed jaunty on my compaq nc8230 using wubi and facing the same kind of mouse problems
the mouse after some time stops working properly. The right click functionality is totally lost and the left click is highly limited. even update manager says that it can't grab the mouse click. 
Its pretty frustating as u ve to do everything using keyboard. Basically i have to restart the system to get the mouse back on.

---

### Post by bishman on 2009-06-18
still happening after the latest kernel update

I feel this is a new set of symptoms for an old problem. Back in 8.10, the context menu would randomly pop-up where the mouse pointer is while I am typing something.

This still happens, but when it does, I go into the limbo of this issue. I thought it would be something specific to my laptop hardware crapping out on me - but obviously not since others are experiencing it.

Sometimes the issue will stop when I shut the application down (usually firefox - but other times its kmymoney), other times it won't so I ctrl-alt-bckspace. BTW - does anyone else have the KDE libraries installed - could it be them?

I might give 9.04 another month like this...

---

### Post by bishman on 2009-06-29
Hi All

I have disabled my touchpad on my laptop and haven't had the issue for a few days now...

( however, I do not notice what isn't there :p )

Try it and see...

---

### Post by Maxplayer14 on 2009-06-30
> **bishman said:**
> still happening after the latest kernel update

I feel this is a new set of symptoms for an old problem. Back in 8.10, the context menu would randomly pop-up where the mouse pointer is while I am typing something.

This still happens, but when it does, I go into the limbo of this issue. I thought it would be something specific to my laptop hardware crapping out on me - but obviously not since others are experiencing it.

Sometimes the issue will stop when I shut the application down (usually firefox - but other times its kmymoney), other times it won't so I ctrl-alt-bckspace. BTW - does anyone else have the KDE libraries installed - could it be them?

I might give 9.04 another month like this...

Yeah this is exactly what it does.  I will be scrolling around, or typing, or clicking on emails in Thunderbird and the context menu will just pop up.  Then I know I am screwed.  Funny thing is I thought an update or something fixed it because it didn't happen for like 2 weeks straight to me.  Now the last 4 or 5 days it does it multiple times a day.  It's really getting annoying and even more annoying that nobody has an answer for the issue.

It is a laptop and touch-pad that I am using.  But this never happened to me prior to 9.04.

And I can't disable my touch-pad as that is what I use.

---

