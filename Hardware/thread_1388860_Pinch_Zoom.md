---
title: "Pinch Zoom"
date: 2010-01-23
forum: Hardware
---

### Post by nishant.singh28 on 2010-01-23
I have a Dell Studio 1555 with a Synaptics touchpad. It supports Pinch Zoom and Circular Scroll in Windows. I was able to get Circular Scroll to work nicely for vertical scrolling but how do I enable Pinch Zoom and Circular Scroll for horizontal scrolling?

---

### Post by nishant.singh28 on 2010-01-25
Bump!!!

---

### Post by thefluxster on 2010-01-25
I'm also interested in this.  Running on an Acer 1810T.

---

### Post by nishant.singh28 on 2010-01-29
Another shameless bump!!!

---

### Post by nishant.singh28 on 2010-02-03
BuuuuuummmmmmmmmmmmmmPPPPpppppPPppPPPP!!!!!!!!!!!!!!

---

### Post by nishant.singh28 on 2010-02-08
Bump!!

---

### Post by Tiede on 2010-02-11
I've been looking online, and it seems this is a wild goose chase...
I've heard some say they have it on Ubuntu Netbook Remix, others say they don't, and most people say they've gotten eveything else but that... so... I am not sure what to think...

Sorry.


(hidden shameless bump...)

---

### Post by saif_held on 2010-02-11
Did you check Dell's support forum here in Ubuntu forums?

---

### Post by nishant.singh28 on 2010-02-11
Yup, no mentions. It's a pretty new feature actually.

---

### Post by saif_held on 2010-02-11
Then probably might take some time to be ready. Good luck mate.

---

### Post by Abu_Dayya on 2010-04-17
I know this is an old thread, but I'm searching for the same thing.

I'm on kubuntu 9.10 with kde 4.4.2, installed on a Lenovo T60 laptop. I have tow finger vertical scrolling, two finger tap to open a new tab, three finger tap to get right-click menu. All these worked out of the box, I didn't change anything.

[This]("http://techdigger.wordpress.com/2009/04/02/multitouch-on-synaptics-trackpad-on-linux/") link shows how to edit xorg.cong to get some extra multitouch features (no pinch zoom though). Hope this helps

---

### Post by n.l.o on 2010-05-04
Just out... see
[http://www.synaptics.com/solutions/technology/gestures/touchpad-linux](http://www.synaptics.com/solutions/technology/gestures/touchpad-linux) for details.
only released for OEM (?) ie linux pre-installed pc. which is odd..

anyway, it will be here soon, without "xinput" ([http://ubuntuforums.org/showthread.php?t=1441300](http://ubuntuforums.org/showthread.php?t=1441300) ) or synclient (SHMConfig thing, eg [http://www.ibm.com/developerworks/opensource/library/os-touchpad/](http://www.ibm.com/developerworks/opensource/library/os-touchpad/) ) 

For me (on my brand new ThinkPad T410) it did not work out of the box, although in the Live USB it worked. So after trying alot of other things I managed to get it working with xinput, but not pinch zoom. 

So I am also waiting for a good solution to this...

---

### Post by farmfield on 2010-10-11
As there's no posted solution I'll make a contribution.

The xorg.*.*.synaptics-packages in Lucid and Maverick both support multitouch since may 1010 and the main thing to get it going is enabling SMH Config.

It's all in the Ubuntu helt-pages... :)

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

And if you're touchpad supports multitouch it's all there, from two finger scrolling, three finger swipe and not the least, pinch zoom...

*[COLOR="Silver"]It's like an iPhone, just 20 times the size of the screen and 1/20 the size touchsurface... ;)[/COLOR]*

---

### Post by Gary_inNYC on 2010-11-15
I've searched everywhere for this feature as well, and based on my results, there is currently no way to get pinch-zoom done in Ubuntu.  Save yourself the trouble of looking further.

Please correct me if I'm wrong by showing actual steps to get pinch zoom working, and not generalized wiki pages that doesn't apply to this specific functionality.  

It's better to assume one has read the wiki, than to link something that you yourself have not read.  Very often, linking blindly is the precursor to wild-goose chases.  

For real-world info on the status of "pinch zoom" feature in Ubuntu, check out this link regarding "Synaptics Gesture Suite (SGS-L)":

[http://www.synaptics.com/solutions/technology/gestures/touchpad-linux](http://www.synaptics.com/solutions/technology/gestures/touchpad-linux)

Clearly, it's planned for OEM machines running Ubuntu, and nothing was stated regarding when, if at all such functionality will be applicable to systems that aren't pre-built, which is a lot of us considering how people install linux in laptops initially packaged with Windows.

- Gary_inNYC

---

### Post by Burfee on 2010-12-07
looked everywhere and no pinch to zoom. found this link in another topic  and it seems to have all the settings you could use:  [http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html)

i created a file which runs on start-up containing the following commands:```
#!/bin/sh
xinput set-prop "SynPS/2 Synaptics TouchPad" --type=int "Synaptics Circular Scrolling" 1
xinput set-prop "SynPS/2 Synaptics TouchPad" --type=int "Synaptics Circular Scrolling Trigger" 3
xinput set-prop "SynPS/2 Synaptics TouchPad" --type=atom "Synaptics Two-Finger Scrolling" 1

```

hope it helps someone save a lot of time searching.

---

### Post by solu61 on 2011-01-03
nothing bluhhdy working in this regard! bummer!!!

---

### Post by raid517 on 2011-08-16
Still no pinch zoom? I want to be able to pinch zoom web pages, both on my touch screen and my trackpad.

---

### Post by SGAShepp on 2011-08-16
I'm interested in this as well!:o

---

### Post by nishant.singh28 on 2011-10-12
Well. The new drivers in Oneiric did surprise me with the three finger window drag thing. It is very cool and very, very useful. But I still can't see any hints of....guess what-Pinch Zoom!!!. Come on...someone?

---

### Post by Chaz46 on 2011-12-11
I have pinch zoom working on my Asus in document viewer, but it seems to cause more problems than it solves. When scrolling with two fingers it sometimes jumps out to 50%. Any idea how to make it a little less sensitive?

---

