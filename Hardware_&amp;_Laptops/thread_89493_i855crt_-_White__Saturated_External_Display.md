---
title: "i855crt - White / Saturated External Display"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by mintcoffee on 2005-11-12
I'm having a really strange problem with the i855crt and i810switch utilities. If i use the following:

```
i855crt rawpipe on
```

The display works fine at the same resolution as my laptop monitor ( which is 1280x768 ) but that is not what I want.

Running the following:

```
i855crt on 1280x1024@60
```

or any variant in mode would result in a VERY saturated (almost white all over) display on my LCD monitor.

Any clues to why this might be happening, and a possible solution? As far as I've read... i855crt should 'just work' with this model. The LCD works fine at 1280x1024 on my Desktop install of Ubuntu.

I am running Ubuntu 5.10 Breezy Badger on a Sony Vaio TR3 with 855resolution. I don't think there is anything else that might have affected the display.

---

### Post by jamesshuang on 2005-11-29
I'm having the same problem right now. When I was running gentoo, I tried the same program on the same laptop, and I got it working correctly - however, now it does not. Any progress on this?

---

### Post by penvzila on 2006-03-14
I am getting this to work fine, except for one slightly disturbing thing.  When I run i855crt, it has a segfault, but turns on the CRT and displays moslty fine, but with a weird looking black patter in the upper left hand corner of the crt.  I can't figure out how to make it go away.  I used the online generator to add a modeline for my crt.

---

### Post by cyrus7580 on 2006-03-23
I'm having the same issue here: Here's a short history of my struggle with it:

- Worked almost immediately with Fedora core 3
- Somewhere along the way, it stopped working. I got the "washed out" white screen as you described.
(- a very weird occurrence is that immediately after an upgrade to FC4, it worked again ONCE, then went back to the white crap. For the life of me, I can't figure out why it would have worked once and then quit.)
- Badly needed external CRT/LCD to work, so I wiped the laptop (dell 700m) and installed Ubuntu Hoary Hedgehog 5.04 to give it a try.
- At resolution of 1024x768, the source packages of i855-crt worked pretty well at giving me a useable image on my external LCD.
- Then I wanted 1280x800 on my laptop LCD. I had to upgrade to Breezy 5.10 to have access to the 855resolution package.
- Finally got 1280x800 working on my laptop LCD, but using the ubuntu-packaged i855crt command, the external LCD does not work (white saturation). 
- rawpipe doesn't work for me. The colors are OK, but the external LCD screen is violently wavy. 

If anybody has any information on this phenomenon, we'd all appreciate it. Thanks.

---

### Post by cyrus7580 on 2006-04-04
I wiped my laptop and made a dual boot Ubuntu/Windows XP. I thought I'd share how Windows handles the CRT out stuff on my Dell 700m, because it shocked me at what happened.

I have an external 1280x1024 LCD. My laptop's native resolution is 1280x800. When I hook the external LCD up to the laptop's "CRT" out port under Windows, it's stretched vertically at first and the picture on the laptop is as the same as it always is. BUT... when I hit the Fn+F8 combo (labeled CRT/LCD in blue) the laptop screen cuts out and the screen on the external LCD goes to 

(drum roll)

FULL SCREEN 1280x1024!!!! Full aspect!

I had always wondered if the graphics chip in my laptop was capable of the different aspect ratio out of the CRT port. Even when I had the CRTout working under linux, It would only show 1280x800 with a blank strip across the bottom of the LCD. I thought full aspect would be complete wishful thinking. Apparently it's not.

The question now is, how the hell do i get Ubuntu to do that? How do I get ubuntu to output 1280x1024 from the CRT-out port? Especially considering this crazy white-saturation we're getting just attempting 1280x800. 

Seriously... if anybody has any insight into this stuff, please fill us in.

---

### Post by ruffneck on 2006-04-21
I'm in the same boat with my Dell 700m. The best I can get is the CRT on with the violent wavy thing using i855crt rawpipe on.

---

### Post by godlesscommie on 2006-05-31
Anyone have any recent luck getting this to work?

---

### Post by cyrus7580 on 2006-06-02
Just wanted to report some more (not good) info.

I had hoped that the final version of Dapper might fix the problem. It didn't. So I then tried this new Xgl/compiz stuff that everybody's talking about. I thought that X running under a different graphics library might fix the external monitor issue. It didn't. 

Has anybody filed a bug report on this? Where would I go to file such a report?

---

### Post by godlesscommie on 2006-06-02
That's too bad.

I'm thinking of switching to the Xgl/compiz environment with my 700m. Can you tell me a bit more about how you went about it?

---

### Post by Peacepunk on 2006-09-26
Sorry to break in: thanks to wieman01 and 

[http://ubuntuforums.org/showthread.php?t=221908&highlight=Problem%3A+Sony+Vaio+VGN-250+external+projector+i855crt](http://ubuntuforums.org/showthread.php?t=221908&highlight=Problem%3A+Sony+Vaio+VGN-250+external+projector+i855crt)

&

[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

I sorted the problem on my 855GM intel integrated graphic card on a Sony Vaio VGN-T17GP.

When I say "sorted", it's not completely true: it enabled XINERAMA, unleashing DualHead capability (factory-locked under windows for this model !), but it has some drawbacks:

[http://ubuntuforums.org/showpost.php?p=1542684&postcount=12](http://ubuntuforums.org/showpost.php?p=1542684&postcount=12)

A matter of choice, but a definite answer to those that cannot live without their VGA port (or with a resident XP system for that purpose)

Now, this 2304x768 resolution of mine looks great for GIMP, thumbnails browsing and Xine among others. OOo2 Presentation untested as of now.

---

### Post by McLogic on 2006-10-23
One of my only disappointments with the 700m (1280x800, Pentium M, Intel 855 graphics, VGA out, TV-out) has been the inability to get video/CRT out working. The 1394 and SD reader also never worked. On the upside the 700m really has 5 hours of battery life and weight about 5 lb.

I was thinking of the D620, but it has no TV output. Then I realized that I just boot into windows when I need out because the i855 has not worked on Linux. It made me wonder if we will ever be able to support common hardware.

Do the nVidia laptop cards do better at switching?

---

