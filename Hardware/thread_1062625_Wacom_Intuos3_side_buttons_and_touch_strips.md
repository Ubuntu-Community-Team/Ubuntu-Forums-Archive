---
title: "Wacom Intuos3 side buttons and touch strips?"
date: 2009-02-07
forum: Hardware
---

### Post by miggols99 on 2009-02-07
I have got the tablet working with the touch sensitivity and the buttons on the pen (top does right click, the bottom does middle click) but the touch strips and side buttons do absolutely nothing. How can I set them up to work?

---

### Post by miggols99 on 2009-02-19
*bump*

---

### Post by woodybrando on 2009-03-22
I've got this same question. Wondering how to assign functions to the side buttons and side strips. Anyone know how to do this? thanks, jayson

---

### Post by mcduck on 2009-03-22
Here's a good guide for configuring Wacom tables on Ubuntu: [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom").

Worked fine for me with my Intuos3. :)

---

### Post by Favux on 2009-03-22
Hi everybody,

You also might want to check on the Wacom ExpressKeys site:

[http://freshmeat.net/projects/wacomexpresskeys/]("http://freshmeat.net/projects/wacomexpresskeys/")

---

### Post by miggols99 on 2009-03-23
None of these seem to do anything. Using the expresskeys program gives me

```
expresskeys ERROR: Tablet not attached, OR (in case of Cintiq 21UX, Intuos3
and Graphire4) the 'pad' device has not been specified in xorg.conf, OR is
lacking on the command line when using "named devices".
```

Even though I have the 'pad' device in my xorg.conf, and yes, it is actually connected ;)

---

### Post by duffman.c.d on 2010-06-19
I am having the same problem. (Has anyone found a solution). It seems that the pad is being treated as a pointing device. When any on the keys or the touch strips are pressed the caret (pointer) moves to the top left hand corner of the screen (0,0 maybe?). The buttons seem to be treated as mouse buttons with the layout below. ('scuse bad ASCII art)

2 _| 1_
_2 | 3_
_  1    _
on the left

1 _| 1_
_1 | 1_
_  1    _
on the right


1 is LMB, 2 is RMB and 3 is MMB if that's not clear.
Any help would be appreciated.

---

### Post by Favux on 2010-06-19
Hi duffman.c.d,

Which model of Inuos3?  What release of Ubuntu?

---

### Post by duffman.c.d on 2010-06-19
Sorry,
I've got 10.04 and a wired USB Intuos 3.
If thats what you mean.

---

### Post by Favux on 2010-06-19
OK, good.  So Lucid.

How are you attempting to configure the buttons? Are you using an xsetwacom script?  Do you still have an old copy of your .xinitrc from wacomcpl?  Also are you using the default Lucid 0.10.5 xf86-input-wacom?

---

### Post by duffman.c.d on 2010-06-27
Sorry for the late response, it's been a busy week.
Turns out this is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/560180]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/560180")
The solution seems to be > Upgrading to xf86-input-wacom 0.10.6 should also solve this issue. I haven't tried it yet as the process seems to be complicated (See comment #12 in bug report), I think I'll just wait for the repository to have the updated driver.

Thanks for the help.
CD

---

### Post by Favux on 2010-06-27
Hi duffman.c.d,

Actually it's pretty easy.  Follow II. in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by duffman.c.d on 2010-06-27
Thanks for the help Favux.
That did the trick.
The buttons are by default just the mouse buttons 1-8 so I set up an xsetwacom shell script like the one in the tutorial. Each line was (on my machine pad wasn't recognised so I had to use the full name):
```
xsetwacom set "Wacom Intuos3 6x8 pad" Button1 "key alt"
```
with the button number changing and alt replaced by the needed key(s) like ctrl or ctrl shift F2

Once the script was added to the "System>Preferences>Startup Applications" everything worked. The arrangements of keys on the Intuos3 were (again 'scuse ASCII art, this is for the Button1, Button2 etc above):
```
|---|---|       |---|---|
|   | 1 |       | 5 |   |
| 3 |---|       |---| 7 |
|   | 2 |       | 6 |   |
|---|---|       |---|---|
|   4   |       |   8   |
|-------|       |-------|
```
Thanks again for your help, hope this will be useful for someone else.

---

### Post by Favux on 2010-06-27
Hi duffman.c.d,

Excellent!

Let's get a xsetwacom script together for the Intuous3.  What are you using currently?

It has a stylus, two stylus buttons, eraser, two "pads" (two clusters of  4 buttons), does each cluster have a slider?  Does it also have a Wacom mouse?

---

### Post by duffman.c.d on 2010-06-27
I don't have a mouse but I believe one is available.
There is a slider on each side (StripLUp/Dn and StripRUp/Dn)
There are four buttons on each side Button1-Button8.
I've only recently got the pad and haven't used it much so I'm not entirely sure what buttons I want, for the moment I'm using the default of ctrl, alt, and shift on both sides and just using the strips to scroll.

I'm sure there are better layouts but I'm not sure what they are.
(when using Gimp for example I'll change the left strip to [ and ] to resize the brush)

---

### Post by Favux on 2010-06-27
Great.  Let's not worry about layout, because everyone will end up with their own.  We just want a default example.

It looks like they can have a mouse, so we'll have to put that in:
[http://www.dpreview.com/news/0409/04091002wacomintuos3.asp](http://www.dpreview.com/news/0409/04091002wacomintuos3.asp)
[http://www.google.com/products/catalog?hl=en&q=wacom+intuos3&cid=4602732989362373809&sa=title#p](http://www.google.com/products/catalog?hl=en&q=wacom+intuos3&cid=4602732989362373809&sa=title#p)

Can you post your?:
```
xinput --list
```
I can probably guess the rest from what you posted, but better to be sure.

[IMG]http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/expresss-keys.png[/IMG]

---

### Post by duffman.c.d on 2010-06-27
Attached is the result from xinput -list (yes I have two keyboards a mouse and a wacom attached to the one computer!)

I don't know if Wacom Intuos3 6x8 cursor is the (optional) mouse or if it is different.

[ATTACH]161705[/ATTACH]

---

### Post by Favux on 2010-06-27
You're right, cursor is what linuxwacom calls the Wacom mouse.  OK, well the mouse section won't be the best until we get a cursor to test with.  But at least we'll make it clear there is suppose to be a cursor section.

---

### Post by Favux on 2010-06-27
Hi duffman.c.d,

Alright, here's a first try.  I used a bunch of different stuff in pad so we can see what works.

---

### Post by duffman.c.d on 2010-06-28
Faux,
Most of the script works. There are a few changes needed (at least on my PC):
the tab needs a capital T
pageup and pagedown don't work, using xev I got Prior and Next (with capitals) for pageUp and pageDown when I inserted them into the script it worked.
NumPlus and NumMinus don't work I got KP_Add and KP_Subtract with xev
' doesn't work, I got apostrophe with xev (no caps)
I'm not sure if this is just my computer, or Lucid (x64) or what but they worked for me.
Also, my ClickForce had a range of 1-2048 (the number of pressure steps for the Intuos3) not 1-21 and was shared between the eraser and the stylus. Whichever was set last became the ClickForce. E.g. set stylus ClickForce to 1, then eraser to 2048. if you checked the stylus ClickForce it returned 1 but you had to push really hard to register a click on either the pen or eraser.

Other than those few things everything works.

---

### Post by Favux on 2010-06-28
Hi duffman.c.d,

I made the changes you suggested and some others so let's see how the second effort is.

The only thing I didn't change is ClickForce, because I don't understand it.  I mean I understand what you are saying, but I don't think ClickForce is suppose to behave like that:
> ClickForce     integer (1 - 21)         sets tip/eraser pressure threshold with clickforce scale

from:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

You may have uncovered a bug in the code, at least for the Intuos3.

---

### Post by Favux on 2010-07-07
Hi duffman.c.d,

It looks like you did uncover a bug in the code. A patch to fix it has been submitted:  [https://sourceforge.net/tracker/?func=detail&aid=3024929&group_id=69596&atid=525126](https://sourceforge.net/tracker/?func=detail&aid=3024929&group_id=69596&atid=525126)  It's been tested and works:  [https://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTilGRYYhRy-M0IFTchQvvhRZMIJZ7PgyxVKoHK3i%40mail.gmail.com&forum_name=linuxwacom-devel](https://sourceforge.net/mailarchive/forum.php?thread_name=AANLkTilGRYYhRy-M0IFTchQvvhRZMIJZ7PgyxVKoHK3i%40mail.gmail.com&forum_name=linuxwacom-devel)

You can either apply it or wait until it has been comitted to xf86-input-wacom and then clone the git.

---

### Post by ebotts on 2011-01-17
Hi. I'm relatively new to Ubuntu, so maybe I should have left well enough alone. But I didn't. I'm using a Wacom Intuos3 in Ubuntu 10.10. At first, everything was working okay--I could use the mouse and the pen--but I could not use the extra buttons on the mouse (side buttons and middle click). This looked like the right thread, so I used the [HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") recommended above. The pen works fine, but now when I  use the mouse, my cursor goes to the left side of the screen and won't move. Any help would be greatly appreciated.

---

### Post by Favux on 2011-01-17
Hi ebotts,

Welcome to Ubuntu forums!

You're a victim of bad timing.  That's exactly what happens to touch on the new Bamboos.  They (the LWP) manage to break relative devices (touch on a Bamboo P&T & Wacom mouse) a couple of weeks ago.  They are in the process of fixing it and it looks like the last patches have been submitted.  Hopefully they will be committed in a day or two or so.  Then you'll just reclone the git repository (part II.) and you should be good.

---

### Post by Favux on 2011-01-18
Hi ebotts,

The commits to the xf86-input-wacom git repository last night look to have fixed touch.  So they'll probably fix your Wacom mouse.  Just re-clone the git repository (part II.) and hopefully it will work for you again.

---

### Post by rylleman on 2011-02-10
Thank you *duffman.c.d* and *Favux*!
Thank's to you I now for the first time in linux (been using linux+wacom for 4+ years) have working pad buttons! Never had them before. Also my pen is mapped properly now with right click on lower and middle click on higher button. Always had them switched and couldnt get them right...

BUT, I can't get touch strips to work at all. Nothing happens when I map keys to them. Broken tablet or something else?

Also I still cannot hotplug my tablet, but that is a completely different matter. Left mouse button is always pressed, have to restart X to get it working again.

Intous 3 on Linux Mint 10, gnome.

---

### Post by Favux on 2011-02-10
Hi rylleman,

> BUT, I can't get touch strips to work at all. Nothing happens when I map keys to them. Broken tablet or something else?

I think touch strips should be working.  I believe a commit to fix them was added to the xf86-input-wacom git repository a few weeks ago.
> Also I still cannot hotplug my tablet, but that is a completely different matter. Left mouse button is always pressed, have to restart X to get it working again.

Mint 10 is the equivalent of Ubuntu Lucid?  Hot plugging should be working.  You don't have any tablet entries in the xorg.conf do you?

---

### Post by efflux on 2011-04-23
Hi. I have a Cintiq 21UX.

I can map all the buttons via xsetwacom but I can't get the touch strips to do anything except scroll which is what they do as default.

I've got a fresh install of Ubuntu 10.10.

---

### Post by Favux on 2011-04-23
Hi efflux,

Maverick's default xf86-input-wacom version is 0.10.8.  The touch strips weren't fixed until a later version.  So if you want to modify them your best bet is to compile a newer version by downloading the 0.11.0 tar or cloning the git repository.  See part II. on the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by efflux on 2011-04-24
Thanks a lot for that.

Strips are now working.

I just need to sort out a script.

This is awesome. I just got a second hand Cintiq a few days ago. Before that I was using a small TC1100 (old but great HP slate PC) for sketches. It's a testament to Linux and Mypaint that the TC1100 was even usable. Cintiq on desktop now takes things to a whole new level.

---

### Post by efflux on 2011-04-24
OK. I spoke too soon.

The 0.11.0 version was a serious regression from the 0.10.8. I had to drop back again.

The strips worked but the buttons didn't. I also lost the ability to hover over the screen and activate such things as colour history etc (in Mypaint) with the pen buttons (which do work) where I can't make contact with the screen or I actually draw. I tried changing this with TabletPCButton parameter but as with all the other buttons nothing works.

Just to add, I have checked the change in xsetwacom parameter names so that wasn't the issue.

---

### Post by Favux on 2011-04-24
Couple of things I should have warned you about.  A lot of parameter names changed starting with 0.10.11.  See *man xsetwacom* in that version or 0.11.0.  Also see the linux wacom project mediawiki:
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
If you enter a xsetwacom get or set command individually in a terminal it should also tell what the parameter name changed to.  I got them to put that into the code.  ;)

By the way if you find any mistakes in the mediawiki let me know so I can fix them.  I don't have a Cintig for example so those are just my best guesses.

Also there might be a problem with button mapping for you.  Button 4 may actually map as Button 8 for you right now, Button 5 as Button 9, and so on. That's because right now Buttons 4 to 7 are reserved for scroll.  I'm pretty sure they're planning on fixing that shortly.

Also a sample xsetwacom script for the Cintiq is attached to post #2 on the Bamboo P&T HOW TO I linked you to above.

---

### Post by efflux on 2011-04-24
Ok. Thanks for your reply.

I went back to 0.11.0 to make comparisons. There seems to be a bunch of problems so I can't specify things yet but I did find that button 4 maps to button 8.

I've got the parameter names correct. I've looked at that.

I'll get back here if I find anything else out.

I need the hover function. This is very useful but I can't get that. It told me my device doesn't have that function yet it works in 0.10.8.

One thing is certain, the Cintiq 21UX running on Linux with Mypaint has to be the ultimate painting system. I know Mypaint is quite simple and lacks some features but the ease of use of the app, the efficiency and all the procedural brush parameters make it superb for basic painting.

---

### Post by Favux on 2011-04-24
> I did find that button 4 maps to button 8.
Good.

I agree, MyPaint is nice.

TPCButton was changed to TabletPCButton and fixed with version 0.10.9?  But Jason recently discovered it was being conflated with the tablet PC default because the Cintiq has an LCD too.  It should be "off" by the default, i.e. hover mode, for the Cintiq.  But it was being treated as a tablet PC and turned "on" by mistake.  I'm not sure they fixed that yet, let me check.  So you're saying using *xsetwacom set "device name" TabletPCButton off* isn't giving you hover mode?

---

### Post by efflux on 2011-04-24
Buttons appear to be mapping exactly as you say but I only initially found it with 8 because I only have 8 buttons.

The hover problem whether I try to turn on or off:

```
ryan@Ubuntu:~$ xsetwacom set "Wacom Cintiq 21UX pad" TabletPCButton "off"
Property 'Wacom Hover Click' does not exist on device.

```

---

### Post by efflux on 2011-04-24
Oh wait!

Wrong device. It should be Wacom Cintiq 21UX Stylus.

Now it works.

I'll just go through everything to confirm. I think all is working now.

---

### Post by Favux on 2011-04-24
Ah, I see the problem.  By the way the patch to fix it was committed 10 days ago about 5 days before 0.11.0 came out.  I didn't understand the "fix".  It was a change to the macro checking mask in the defines which to me seemed unrelated to Jason's original post and proposed fix.  Developer magic I guess.  But maybe not working?  Or else I misunderstood and that was the first part of a fix?

Anyway the TabletPCButton parameter only applies to the stylus so it needs to be:
```
xsetwacom set "Wacom Cintiq 21UX stylus" TabletPCButton "off"
```
Make sure I got the "device name" correct.

Edit:  lol you beat me to it while I was going through the commits.  Good work.  :)

---

### Post by efflux on 2011-04-24
Hi.

I have a habit of editing my posts straight after I originally post them. I should stop doing that. Not sure if you noticed though.

Thanks for the info. The original info about the problem in 0.10.8 is really important to know. Without that you have a non fully functioning Cintiq and those strips are extremely useful.

Having strips and buttons working greatly improves your work because you use them. If it is not so ergonomic and you have to look at a keyboard you are less likely to use those changes and your strokes are much less organic because they will all look the same.

I have everything functioning now. I can't find any problems. I just need to decide the button assignments. Primarily I will use Mypaint so that bit is quite simple but I suppose you could make several scripts.

---

### Post by efflux on 2011-04-24
This is off topic a bit but does anyone who how to set your mouse for left handed while you also have a tablet? The trouble is that the pen button's right and left click get reversed when you set the mouse to left handed. I've tried to reverse the pen buttons in xsetwacom to compensate but get a pen that doesn't work quite right for some functions.

This is a constant pain for left handers.

---

### Post by Favux on 2011-04-24
Not sure.

But assuming it is a 3 button mouse and the current mapping is:
```
xinput set-button-map "WALTOP International Corp. Slim Tablet" 1 2 3
```
maybe
```
xinput set-button-map "WALTOP International Corp. Slim Tablet" 3 2 1
```
Using the mouse's "device name" *xinput list* returns for the mouse.  You could probably check the current mapping with:
```
xinput list-props "device name"
```

---

### Post by efflux on 2011-04-24
OK. Thanks for that. I will try it.

To get back to the touch strips. They appear to be upside down.

StripRightUp is in fact down etc. Not that this is vitally important.

---

### Post by efflux on 2011-05-05
Ubuntu 11.04 causes a total crash if you use xsetwacom to assign strips then use them (this is with a Cintiq). You end up back at login.

---

### Post by Favux on 2011-05-05
Hi efflux,

It sounds like the crash is reproducible.  Are you seeing anything in Xorg.0.log or Xorg.0.old (in /var/log) related to it?

You can use the *xsetwacom set "device name"* debug Parameters (set both to 12):  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Debugging](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Debugging)  See if the output in Xorg.0.log says anything.  Then you can report to linuxwacom-discuss.

---

### Post by efflux on 2011-05-07
Hi Favux.

OK. Thanks.

I expect the crash will probably happen on all systems. It says segmentation fault in Xorg0.log.old and enabling debugging in xsetwacom does not cause anything to appear in Oxorg log files.

I think I'll go back to Ubuntu 10.10. To be honest there are lots of issues with 11.04 due to all the drastic desktop changes. Total pain to simply get the Nvidia driver working and hence the Cintiq because it doesn't work at all without the Nvidia driver. Then you can't go near any of that Unity stuff with the NVidia driver or at least I can't but I'm not the only one.

---

### Post by Favux on 2011-05-10
Hi efflux,

I just found out what you meant because I installed Natty on my tablet PC that has Nvidia.  Sure enough with the default Nouveau driver the system booted to a blank screen.  Had to add 'nomodeset' to the kernel line for it to boot into X.  Luckily the Nvidia proprietary driver worked for my chipset in Natty.  I had to hook up to an ethernet cable to download the driver to work around the wi-fi problem.  But once I got the downloads I was able to fix that too and boot into Natty's 3-D without the 'nomodeset' option.

So I got lucky and my Nvidia chipset works on Natty with the proprietary drivers.

---

### Post by efflux on 2011-05-15
I have actually got a new system now. Quad core i7 2600. Painting performance with Gimp on this is fantastic.

However, I've moved this system to Debian testing 64 bit although I still have another Ubuntu system (tablet PC). Everything appears to be working as it was on Ubuntu when I had it working there with the same versions of everything. I find Debian to be better than Natty because Canonical have actually complicated rather than simplify things with 11.04, at least in my opinion. This version of Ubuntu seriously turned me off. I think making Unity the default was a mistake.

The segmentation fault killed Natty for me because none of the strips or buttons worked. Has anyone else had this issue? Total crash if you set the strips from xsetwacom.

---

### Post by Favux on 2011-05-15
Are you seeing the segmentation fault with just the strips or the Buttons too?  Because I have a Bamboo reporting the tablet Buttons become unresponsive after a few minutes and the only way to fix it is to hot plug the Bamboo.  That may his equivalent if the Buttons aren't causing as bad a crash as the strips.

As far as Unity goes I think it helps to consider it a Beta 1.  The Maverick netbook version of Unity would have been an alpha.  So the next Ubuntu release will probably show significant improvement and at least get it to a Beta 2.

---

### Post by efflux on 2011-05-16
The segmentation fault was actually occurring on all the buttons.

I have upgraded the wacom driver on Debian testing (Wheezy) the same way I did on Ubuntu 10.10 and it works. Driver 0.11.0.

Natty and Wheezy have the same version xserver as far as I am aware.

Not sure what is wrong but I saw a few bug reports of the exact same problem in Natty.

---

### Post by efflux on 2011-05-16
As for this latest Ubuntu version. It's veering too much towards fancy desktop concentration and treating users like idiots. Often I use LXDE on Debian. Nice and simple.

There are a lot of problems with the latest Debian testing which I have fixed but then it's called "testing". The extra complexity of problems in Ubuntu has put me off. I just want a simple desktop. I don't even use any of the effects even although I'm now on a quad core.

---

### Post by Favux on 2011-05-16
Thanks efflux,

I'd guess these are the Launchpad bug reports you mentioned:
[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/769477](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/769477)
[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/782756](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/782756)

Since the segmentation fault isn't present in Debian testing (Wheezy) it seems unlikely it is a xf86-input-wacom problem.  Since it is limited to using xsetwacom to set button and strip options maybe they've made some sort of change to Xinput's button mapping that is not anticipated by the Wacom X driver?

Don't get me wrong, I agree with most of what you are saying.  I have been happy with the Gnome top panel and Cairo dock as my bottom panel for several releases now.  But to be fair it is early days.  And I'm impressed by how quickly they changed strategy and executed it.  They've actually beaten Apple's Lion to the punch.  HP is planing on doing the same thing with Web OS.  It should be available on HP Desktops in around 6 months.   And Microsoft is too with Win 8.  And they're now a distant fourth.  So this is definitely the trend or fad.  We'll just have to see what the mature versions offer.

---

### Post by odd on 2011-05-22
Hi everyone

I finally managed to get Intuos3 pad buttons/strips to work on Lucid (64bit). They were causing cursor jumps to top-left corner on input-wacom 0.10.5 (default on Lucid repo), and 0.10.7 (from some PPA, can't recall) caused another problems (after first stylus "click" on the tablet surface, it stopped "tracking" cursor while I was moving pen hovered over the tablet until I "click" again with the stylus tip).

Anyway, I've compiled git version of input-wacom driver and it finaly worked ok, but xsetwacom script given by Favux on post#21 of this thread is not compatible with git version of input-wacom I guess.
First of all, PressCurve, ClickForce, TPCButton and "Button#" were replaced with (respectively) PressureCurve, Threshold, TabletPCButton and {"Button" "#" "command"}. But what concerns me most is that "Strip*" definition is not used anymore and I think touch-strips are now described as Button # like other buttons on the pad. So here's my question: does anyone have current layout of these pad buttons?
Till the moment, I recognized every button as fallows:
```

#|---|---|       |---|---|
#|   | 1 |       | 9 |   |
#| 3 |---|       |---|11 |
#|   | 2 |       |10 |   |
#|---|---|       |---|---|
#|   8   |       |  12   |
#|-------|       |-------|
# Strips: 4-7 - not sure yet, 
# strips doesn't seems to 
# handle "key tab" on which 
# I've tested all the buttons.

```

Kinda weird layout, but can someone confirm it/or complete it (strips section)?

EDIT: ok, didn't found [this]("http://ubuntuforums.org/showthread.php?t=1704369") earlier, so for strips we have:
```

StripLeftUp   StripRightUp
StripLeftDown StripRightDown

```

---

### Post by odd on 2011-05-23
Ok, few hours of testing, and I think that something is wrong with Button 11 and 12 (last two on the right), while every other works nice on MyPaint, Gimp, Blender, these two last buttons act similar to the bug with "top-left-corner-jump" issue + /see note below:)/.
Note: while running xev command, every button acts as expected: pressing and holding button triggers KeyPress event, releasing button triggers KeyRelease event. But when I press Button11 or 12, xev reports immediately KeyPress and KeyRelease at once (exactly the same time according to xev).

Note2: setting "key d" or "key f" (the simple ones:)) to button 11 and 12 seems to work, but "key [" or "key ]" (or "key bracketleft"/"key bracketright") don't.

Any ideas?


EDIT: ok, clarification: setting "key bracketleft" / "key bracketright" to Button 11/12 reports "8" / "9" keypress (in terminal/text-editor).
Setting "key [" / "key ]" gives nothing, so I think has something to do with right Alt key, [ key and ] key bindings themself rather than buttons on the tablet pad. Could this be missing stuff in wacom driver code? (AFAIR Tab key had this issue in some previous versions, right?)

---

### Post by Favux on 2011-05-23
Hi odd,

Nice work.

> Tab key had this issue in some previous versions, right?
Correct, it wasn't yet supported in xsetwacom.c in the tools directory of the xf86-input-wacom source folder.

The reason there is the tranposition of Button 4 to Button 8 is that 4,5,6, and 7 are reserved for scroll.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Pad_Physical_Button_to_X_Button_Transpositions](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Pad_Physical_Button_to_X_Button_Transpositions)
For general help see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

For alt in xsetwacom.c I see:
```
	{"alt", "Alt_L"},
	{"lalt", "Alt_L"},
	{"ralt", "Alt_R"},
```
I don't see an indication that the symbols [ or ] are supported so you'd want to use whatever *sudo dumpkeys* is calling them.

And if you see problems with the Linux Wacom Project's mediawiki or want to update or correct something let me know.

---

### Post by odd on 2011-05-23
Hi Favux

Thanks for an answer.
Further investigation revealed that my right Alt key is being reported as "ISO_Level3_Shift" in xev, which appears to be normal in Poland(Polish) keyboard layout.
So I've tested that a little bit:
```
xdotool key ISO_Level3_Shift+9
``` outputs expected "]" sign, but setting it on wacom:
```
xsetwacom set (...) "key ISO_Level3_Shift 9"
``` (while giving no error) outputs just "9" on Button press.

Oh, and it looks like I can't make right Alt report as Alt_R without breaking the polish keyboard layout (tried that by commenting out respective line in /usr/share/X11/xkb/symbols/pl/, which resulted in Alt_R on xev but no polish characters nor "]" symbols on Alt_R+9 etc.) :/.

EDIT: I can see that xmodmap may come to help, but neither I know how to use it;) nor it solves the problem.

---

### Post by duffman.c.d on 2011-06-06
I've just upgraded to Natty, and am having similar problems.

Odd,
did you have to do anything after upgrading to the latest git. I am still getting the upper-left-hand-corner problem, and xsetwacom won't let me set pad to relative (how I fixed it previously) it says:
```
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Mode id in failed request: 0x17
  Serial number of failed request:  15
  Current serial number in output stream:  15
```

Favux,
I agree with Odd's button numbers and the strips are Strip[Left/Right][Up/Down] but they are backwards (up is down and down is up). Also, if you set StripLeftUp it sets button 1 to the same thing and also SLD->2 SRU->3. (SRD goes to the unmapped button 4). Strangely this doesn't happen in reverse: Setting button 1 doesn't change SLU.

Any hints on how to set pad to relative (or stop it moving the cursor at all)?
duffman.c.d

---

### Post by Favux on 2011-06-06
Hi duffman.c.d,

It looks like there is a new bug affecting the Intuos.  There was an old launchpad bug about the cursor jumping with a button press that is active again:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/560180](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/560180)

Sanette has posted a "fix" that works for him on his Intuos4:  [http://sourceforge.net/mailarchive/forum.php?thread_name=201106052218.11514.san.vu-ngoc%40laposte.net&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=201106052218.11514.san.vu-ngoc%40laposte.net&forum_name=linuxwacom-discuss)

I'm wondering if this isn't actually a kernel side problem.  In other words they changed the xf86-input-wacom code but didn't change the wacom.ko code to match those changes.  That happened with the Graphire, resulting in a pad button freeze due to an absolute/relative issue.  They fixed it with the graphire.diff patch in this thread to wacom_wac.c:  [http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTikO9Fr-A%3De5z0xa_yPQtTzvhc18xQ%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTikO9Fr-A%3De5z0xa_yPQtTzvhc18xQ%40mail.gmail.com&forum_name=linuxwacom-discuss)  This bug is also on launchpad.

With the button assignment issues I don't know what to say.  They did make changes to some of the kernel button defaults (wacom_wac.c) starting around 2.6.37(?).  I don't understand them and can't really trace them in wacom_wac.c.  Too confusing for me.  I don't even know why they felt the need to do that.

With luck some of it is due to the bug and once that's fixed it may shake out a little.

---

### Post by duffman.c.d on 2011-06-06
Thanks Favux,
Sannette's fix worked for me. The important part was:
```
+               // SAN: I comment this out
+               /* xf86PostMotionEventP(pInfo->dev, TRUE, first_val, num_vals, */
+               /*                   VCOPY(valuators, num_vals)); */
```

Relative/Absolute don't seem to have any affect on the pad at all now. (I first tried without the above comment, and changing modes to Relative didn't fix the problem).
I can live with the strip problem as I just have to remember they're backwards, and make sure I set them before the buttons. Here's hoping it's all worked out in the bug fix you mention. And for anyone with similar issues, Sannette's fix worked for me on my Intuos 3.

duffman.c.d

---

### Post by Favux on 2011-06-06
Good.

I posted your positive results on San's linuxwacom-discuss thread so he has a tested-by and also to alert them that the Intuos3 is affected too.  Hope you don't mind.

---

### Post by sanette on 2011-06-07
hi duffman.c.d

for reverting StripLeft and StripRight to the correct Up/Down orientation
you might want to try this simple patch: (change value > 0 to value < 0).
It works for my cintiq which has the same issue as your intuos

diff --git a/src/wcmCommon.c b/src/wcmCommon.c
index bd47c51..c8d29b6 100644
--- a/src/wcmCommon.c
+++ b/src/wcmCommon.c
@@ -366,8 +366,8 @@ static int getWheelButton(InputInfoPtr pInfo, const WacomDeviceState* ds,
        {
                value = ds->stripx - priv->oldStripX;
 
-               fakeButton = (value > 0) ? priv->striplup : priv->stripldn;
-               *fakeKey = (value > 0) ? priv->strip_keys[0+1] : priv->strip_keys[1+1];
+               fakeButton = (value < 0) ? priv->striplup : priv->stripldn;
+               *fakeKey = (value < 0) ? priv->strip_keys[0+1] : priv->strip_keys[1+1];
        }
 
        /* emulate events for right strip */
@@ -375,8 +375,8 @@ static int getWheelButton(InputInfoPtr pInfo, const WacomDeviceState* ds,
        {
                value = ds->stripy - priv->oldStripY;
 
-               fakeButton = (value > 0) ? priv->striprup : priv->striprdn;
-               *fakeKey = (value > 0) ? priv->strip_keys[2+1] : priv->strip_keys[3+1];
+               fakeButton = (value < 0) ? priv->striprup : priv->striprdn;
+               *fakeKey = (value < 0) ? priv->strip_keys[2+1] : priv->strip_keys[3+1];
        }
 
        DBG(10, priv, "send fakeButton %x with value = %d \n",

---

### Post by sanette on 2011-06-07
> **duffman.c.d said:**
> 
Also, if you set StripLeftUp it sets button 1 to the same thing and also SLD->2 SRU->3. (SRD goes to the unmapped button 4). Strangely this doesn't happen in reverse: Setting button 1 doesn't change SLU.


this seems to be a bug in xsetwacom
1 2 3 4 is the internal code for SLU SLD SRU SRD
somehow this code is mixed up with buttons

---

### Post by duffman.c.d on 2011-06-07
Thanks Sanette,
Your up/down fix worked well, and I can get around the strip issues by setting them first.

---

### Post by MaxVK on 2011-06-26
Hey guys, I wonder if anyone can give me a pointer here:

I suffer with terrible RSI and Iv been using a Wacom Inutos3 on Jaunty for ages now and it makes a lot of difference, however, now that I am running Lucid (10.04) I'm having trouble with the touch sliders.

I use a script with these types of commands and it works fine:

xsetwacom set "Wacom Intuos3 6x8 pad" Button1 "core key ctrl x"

however, on jaunty the sliders could be used to scroll up and down a page (such as a web page or a document) and this seemed to be the default because I didn't have to edit anything, but this does not work on Lucid and touching the strips sends the pointer to the top left of the screen and scrolls through the tabs in a browser window rather than scroll the page up and down.

Iv tried to use:

xsetwacom set "Wacom Intuos3 6x8 pad" StripLDn "key down"

but this seems to fail and the sliders still scroll through tabs rather than up and down in the document.

Does anyone have any ideas how to get the touch strips to scroll the page up and down?

Cheers

Max

.

---

### Post by duffman.c.d on 2011-06-26
Hi Max,
I'd suggest [this post]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") by Favux. I'm not sure if you'll also need the patches I've pointed out on page 6 of this topic (post #57 and #59), they might be a Natty thing.
So I'd try steps I through IV of Favux's guide, then try setting the strips (StripLeftUp StripRightDown etc.) to 4 and 5. 4 and 5 are the button codes for mouse wheel up and down.
```
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftUp 4
xsetwacom set "Wacom Intuos3 6x8 pad" StripLeftDown 5
```
in your xsetwacom script.

Let us know how it goes.
duffman.c.d

---

### Post by MaxVK on 2011-06-26
I updated using the links from the page you suggest and I just rebooted and the tablet works after a fashion now, but none of the buttons work at all and the stylus, while moving the cursor, locks in place if I click with it. I'm now using a mouse and it already hurts!

Help!

If I type "xsetwacom --list devices" I get nothing at all so nothing can be set! 

Any ideas whats happening? I'm already on the verge of scrapping Lucid entirely and going back to jaunty, out of date or not, just so I don't have to use a mouse!

Sorry if I'm being dense but I'm rather lost!

[EDIT (again)]

So, Iv got the tablet working again (sort of) by editing the "/usr/lib/X11/xorg.conf.d/10-wacom.conf", but the buttons do not seem to work still, and amazingly the sliders now scroll pages again! Its kind of the reverse of the problem I started with, so now I just need to work out how to set the buttons!

Thanks for your help

Max

---

### Post by MaxVK on 2011-06-26
Okay an update:

Things are working okay for now - The button mapping had changed rather dramatically from my first script but that has been sorted now, and the touch sliders now scroll pages as I wanted them to, although the directions are backward - Setting them via xsetwacom just logs me out - I think I saw a patch for this but I'm loath to mess things up again so Ill just get used to the new orientation!

Thanks for your help. I'm now able to carry on without being in pain!

BTW: I don't really use the tablet for drawing anymore, just for general input as a guard against RSI.

regards

Max

---

### Post by duffman.c.d on 2011-06-26
Glad to hear you've got things working.
The patch is easy enough to apply if you want to fix the backwards scrolling.
Simply go to the folder you downloaded xf86-input-wacom to, then go to src and open wcmCommon.c. Find this bit:
```
/* emulate events for left strip */
if ( ds->stripx != priv->oldStripX )
{
	value = ds->stripx - priv->oldStripX;

	fakeButton = (value > 0) ? priv->striplup : priv->stripldn;
	*fakeKey = (value > 0) ? priv->strip_keys[0+1] : priv->strip_keys[1+1];
}
```
and replace both ">" symbols with "<". Again, just below:
```
/* emulate events for right strip */
if ( ds->stripy != priv->oldStripY )
{
	value = ds->stripy - priv->oldStripY;

	fakeButton = (value > 0) ? priv->striprup : priv->striprdn;
	*fakeKey = (value > 0) ? priv->strip_keys[2+1] : priv->strip_keys[3+1];
}
```
replace both ">" with "<". Then rebuild the xf86-input-wacom (Steps II(b) or II(c) of Favux's guide).
That _should_ fix you're problem. It worked for me on Natty at least!

duffman.c.d

---

### Post by MaxVK on 2011-06-27
Thanks duffman, but I downloaded from the PPA ([https://launchpad.net/~doctormo/+archive/wacom-plus](https://launchpad.net/~doctormo/+archive/wacom-plus)) because I was in a tearing hurry to get things done - I had some work to catch up on and needed the tablet working asap.

Cheers anyway

regards

Max

---

### Post by lionbeast on 2011-07-15
hello,i just upgraded to natty, and i read everything here. 

so in order to fix the bug that my cursor is jumping to the top left i have to apply a patch...

but i don't understand where. where do i have to change this to take effect, and where do i find it in ubuntu.

---

### Post by Favux on 2011-07-15
Hi lionbeast,

Sanette's patch is to the xf86-input-wacom source code.  The instructions in part II b) of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") show you how to download it.  Then you patch the source code before compiling it.

Each little hunk in the patch tells you which file to change, for example:
> --- a/src/wcmCommon.c
+++ b/src/wcmCommon.c

means you are working on the wcmCommon.c file in the /src folder/directory in the unpacked xf86-input-wacom folder.  The + in front of a line means you add it and the - means you subtract it.  From what duffman.c.d says in post #57 maybe only the 3 lines in wcmCommon.c need to be changed.  It helps if you turn on the line # preference in gedit.

Of course the other way is to apply the patch rather than edit manually.  So you could copy the patch into the xf86-input-wacom folder and enter:
```
patch -p1 < 0001-Intuos4-Natty-cursor-jump.patch

```
Where you've stuck the contents of the patch into a file you've named *0001-Intuos4-Natty-cursor-jump.patch*.

---

### Post by lionbeast on 2011-07-15
ok well i did compile like you told me, and before that changed the file. but i did something wrong because it still doesn't work, the pointer still jumps up. here is the section how i changed it...can you tell me if something is missing?

	
		sendCommonEvents(pInfo, ds, first_val, num_vals, valuators);

		/* xf86PostMotionEvent is only needed to post the valuators
		 * It should NOT move the cursor.
		 */
		// SAN: I comment this out
             /* xf86PostMotionEventP(pInfo->dev, TRUE, first_val, num_vals, 
*/
            /*                   VCOPY(valuators, num_vals)); */
	}
	else
	{
		if (priv->oldButtons)
			wcmSendButtons(pInfo, ds->buttons, 



and an other issue i'm having is that since i compiled it, i can't reassing the buttons.

when i put this:
xsetwacom set "12" Button 2 "key b" in therminal 
i get:
Property 'Wacom Button Actions' does not exist on device.

but i worked before i compiled


and before i forget, i remeber that last time i had a problem it was already you who helped me out, so thank you very much.

---

### Post by Favux on 2011-07-15
You're welcome.

Hopefully we can figure this out or sanette or duffman.c.d will help us out.

OK, maybe I misunderstood duffman.c.d and you do need all the changes.  I'm assuming you are preserving the code indentations, they are important.  It's just the indentations are not being preserved by the forum in your post because you are not placing the code in code tags (#).

Rather than use the ID # it's usually better to use the "device name" from *xinput list* because the ID # can change.

---

### Post by lionbeast on 2011-07-15
just a quick question. when modifing the code. do i add the + - before the sentence or do i just write it without it?

for the button mapping, you're right the id did change so this works again. i didn't know that the id could change.

---

### Post by Favux on 2011-07-15
Correct, no + or - when manually modifying.  The + and - are for the patch program.  They tell patch what to do i.e. add or subtract a line.

Good that you've got the buttons working!

---

### Post by lionbeast on 2011-07-15
ok so maybe it's just not compiling right. this is what i get while compiling...do you thing it worked or not.

because i must admit, it's my first time compiling anything..and i don't understand much of it.

```
vince@vince-AMILO-Xi-2528:~$ cd /home/vince/xf86-input-wacom-0.11.1
vince@vince-AMILO-Xi-2528:~/xf86-input-wacom-0.11.1$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... yes
checking whether the linker supports -wrap... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating conf/Makefile
config.status: creating doc/Makefile
config.status: creating doc/doxygen.conf
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating include/Makefile
config.status: creating tools/Makefile
config.status: creating test/Makefile
config.status: creating xorg-wacom.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
vince@vince-AMILO-Xi-2528:~/xf86-input-wacom-0.11.1$ make
make  all-recursive
make[1]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1 »
Making all in conf
make[2]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/conf »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/conf »
Making all in doc
make[2]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/doc »
make[2]: Rien à faire pour « all ».
make[2]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/doc »
Making all in src
make[2]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/src »
  CC     wcmCommon.lo
../src/wcmCommon.c: In function 'wcmSendPadEvents':
../src/wcmCommon.c:548:17: error: invalid preprocessing directive #xf86PostMotionEventP
../src/wcmCommon.c:549:37: error: invalid preprocessing directive #VCOPY
make[2]: *** [wcmCommon.lo] Erreur 1
make[2]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1 »
make: *** [all] Erreur 2
vince@vince-AMILO-Xi-2528:~/xf86-input-wacom-0.11.1$ sudo make install
[sudo] password for vince: 
Making install in conf
make[1]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/conf »
make[2]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/conf »
make[2]: Rien à faire pour « install-exec-am ».
test -z "/usr/share/X11/xorg.conf.d" || /bin/mkdir -p "/usr/share/X11/xorg.conf.d"
 /usr/bin/install -c -m 644 50-wacom.conf '/usr/share/X11/xorg.conf.d'
test -z "" || /bin/mkdir -p ""
make[2]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/conf »
make[1]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/conf »
Making install in doc
make[1]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/doc »
make[2]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/doc »
make[2]: Rien à faire pour « install-exec-am ».
make[2]: Rien à faire pour « install-data-am ».
make[2]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/doc »
make[1]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/doc »
Making install in src
make[1]: entrant dans le répertoire « /home/vince/xf86-input-wacom-0.11.1/src »
  CC     wcmCommon.lo
../src/wcmCommon.c: In function 'wcmSendPadEvents':
../src/wcmCommon.c:548:17: error: invalid preprocessing directive #xf86PostMotionEventP
../src/wcmCommon.c:549:37: error: invalid preprocessing directive #VCOPY
make[1]: *** [wcmCommon.lo] Erreur 1
make[1]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/src »
make: *** [install-recursive] Erreur 1
vince@vince-AMILO-Xi-2528:~/xf86-input-wacom-0.11.1$ 

```

---

### Post by Favux on 2011-07-15
Well it's complaining about the the first hunk or the change to wcmCommon.c:
>   CC     wcmCommon.lo
../src/wcmCommon.c: In function 'wcmSendPadEvents':
../src/wcmCommon.c:548:17: error: invalid preprocessing directive #xf86PostMotionEventP
../src/wcmCommon.c:549:37: error: invalid preprocessing directive #VCOPY
make[1]: *** [wcmCommon.lo] Erreur 1
make[1]: quittant le répertoire « /home/vince/xf86-input-wacom-0.11.1/src »
make: *** [install-recursive] Erreur 1

From what I see from the patch that should end up looking like:
```
                /* xf86PostMotionEvent is only needed to post the valuators
                 * It should NOT move the cursor.
                 */
                // SAN: I comment this out
                /* xf86PostMotionEventP(pInfo->dev, TRUE, first_val, num_vals, 
*/
                /*                   VCOPY(valuators, num_vals)); */
        }
        else
        {
```
Which is what I think you've got, correct?

---

### Post by lionbeast on 2011-07-15
thank you so much.
 

instead of erasing the code that wasn't good, i just commented it out with # before them. but that was obviously not the right way to do it. since you told me that the code was incorrect i erased it in all files and know it seems to work.


i can't tell you how thankfull i am. i know you're helping people since a long time with this mathers and i like to tell you that it's very much apreciated. you are really helping clueless poeple like me enjoy linux. thank you

---

### Post by Favux on 2011-07-15
Thank you for the kind words.

I hope the your Intuos4 is now working well for you.  :)

---

### Post by lionbeast on 2011-07-15
haha it's actually a cintiq, but really it's i who has to thank you.

---

### Post by efflux on 2011-07-20
This is a good thread to keep up with these issues. I'm not even using Ubuntu but Debian. I'm still installing Ubuntu for other people though.

Off topic here but it was mentioned in this thread. Favux supplied solution so I'm just confirming that it works.

A problem with Wacoms occurs if you are left handed because standard left handed mouse setting means left handed pen = no good.

I have a Logitech mouse. Solution was:

```
xinput set-button-map "Logitech USB-PS/2 Optical Mouse" 3 2 1
```

---

### Post by efflux on 2011-11-11
> **Favux said:**
> Thanks efflux,

I'd guess these are the Launchpad bug reports you mentioned:
[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/769477](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/769477)
[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/782756](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/782756)

Since the segmentation fault isn't present in Debian testing (Wheezy) it seems unlikely it is a xf86-input-wacom problem.  Since it is limited to using xsetwacom to set button and strip options maybe they've made some sort of change to Xinput's button mapping that is not anticipated by the Wacom X driver?

Don't get me wrong, I agree with most of what you are saying.  I have been happy with the Gnome top panel and Cairo dock as my bottom panel for several releases now.  But to be fair it is early days.  And I'm impressed by how quickly they changed strategy and executed it.  They've actually beaten Apple's Lion to the punch.  HP is planing on doing the same thing with Web OS.  It should be available on HP Desktops in around 6 months.   And Microsoft is too with Win 8.  And they're now a distant fourth.  So this is definitely the trend or fad.  We'll just have to see what the mature versions offer.

Back to this problem across the board. Wacom touch strips are useless. I've been using Debian Wheezy but I also use Ubuntu. I ditched Ubuntu on my main system due to this problem. I still have it on a slate PC with Wacom screen. I just upgraded Debian. Now I have Gnome 3. Not sure what else upgraded when this problem arose but it was mainly Gnome 3. More desktop eye candy but so many other things broken - Linux dying death here.

xf86-input-wacom is 0.10.10

I have tried various input-wacom versions. All segfault when buttons used. I've tried different kernel versions. No difference.

---

### Post by efflux on 2011-11-11
xf86-input-wacom-0.11.99.1 appears to solve the problem.

---

### Post by Favux on 2011-11-11
Hi efflux,

Ha, I was just about to tell you xf86-input-wacom-0.10.10 was likely the problem.  Luckily I saw your next post before I started.  0.10.10 was an emergency release because 0.10.9 had a pad bug.  Actually 0.10.10 didn't completely fix it.  It was finally fixed a few commits into the 0.10.10 tree.

---

### Post by efflux on 2011-11-11
Hi Favux.

There is another problem now. I'm on Debian but it relates the same to Ubuntu anyway.

the left strip is replicated on buttons 1 and 2. I seem to remember something like this before but can't remember or find if there is a solution.

The 0.10.10 is in Debian Wheezy and Sid. Has been for ages. Only one person reported a bug. I've added to that bug report to say that 0.10.10 is no good and this package needs upgraded.

By the way, I can't seen to create an account for launchpad to enable me to report anything about bugs in Ubuntu. I get no code sent via mail.

Also, Gnome 3 is actually quite nice. I moaned about Ubuntu Unity on here and then was confronted with more eye candy in Gnome 3 but now I like Gnome 3.

This stuff drives me crazy though because often I'm doing other things for a while then I decide to do some artwork. I upgrade the system and things break.

---

