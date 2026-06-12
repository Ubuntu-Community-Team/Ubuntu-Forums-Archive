---
title: "Intel 945 chipset horribly slow with Jaunty"
date: 2009-04-23
forum: Hardware
---

### Post by u'b'u'n't'u on 2009-04-23
I recently upgraded to jaunty from hardy and everything is sooooo sloooow 3d acceleration is so slow its hardly even there!:(:eek: is this a known bug that i can fix?

---

### Post by alcCapone on 2009-04-24
Me, too.

```
$ lspci | grep -i 945gm
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```I upgraded to Jaunty yesterday and my **glxgears**' score is now only one fifth of the approx. 1000 FPS I used to have.

```

$ glxgears 
get fences failed: -1
param: 6, val: 0
1058 frames in 5.0 seconds = 211.528 FPS
...

```If I remember correctly, **glxinfo** now says *Mesa* where it said *Intel* before. And what is this *get fences failed* stuff?

```

$ glxinfo | grep render
get fences failed: -1
param: 6, val: 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2

```By the way, where did all the stuff in **xorg.conf **go? Where can I say: Use an intel driver, or the vesa driver, or ...?

Greetings,
Christian.

---

### Post by MonsterDigital on 2009-04-24
Hi friends, excuse me for my english I speak spanish... 

But I have the same problem, and I found this 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

where says that we can reverting the driver of Xorg Intel, and in many cases solve the problems and the performance is better... 

I hope works for us, and I trying in a couple hours...

Luck... and greetings... :lolflag:

---

### Post by caro on 2009-04-24
I just tried this [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") and it worked great.  Compiz is smooth again.

---

### Post by 71CH on 2009-04-24
Can somebody tell this noob how to add the GPG keys using that tutorial?  Thanks.

---

### Post by Chemical Imbalance on 2009-04-24
> **71CH said:**
> Can somebody tell this noob how to add the GPG keys using that tutorial?  Thanks.

Make a new .txt file on your desktop and paste the lines in this link into it:[http://ppa.launchpad.net/siretart/ppa/ubuntu/dists/jaunty/Release.gpg](http://ppa.launchpad.net/siretart/ppa/ubuntu/dists/jaunty/Release.gpg)

Then just import it in the Authentication tab within System Sources.

---

### Post by 71CH on 2009-04-24
I'm sorry if these are stupid questions but I can't seem to get it to import into system sources.  I made the txt file and pasted the numbers.  I tried twice where the first time I pasted everything in that link you pasted and the second time I just pasted the letters and numbers in the middle.  Both times the system sources wouldn't import it.  Can you give a little more help?  Thanks.

---

### Post by Chemical Imbalance on 2009-04-24
> **71CH said:**
> I'm sorry if these are stupid questions but I can't seem to get it to import into system sources.  I made the txt file and pasted the numbers.  I tried twice where the first time I pasted everything in that link you pasted and the second time I just pasted the letters and numbers in the middle.  Both times the system sources wouldn't import it.  Can you give a little more help?  Thanks.

Make sure you copy everything exactly as it appears in that link, not just the numbers.  Otherwise it should work.




Try opening gedit and paste it into that first and save it to your desktop.

---

### Post by caro on 2009-04-24
> **71CH said:**
> Can somebody tell this noob how to add the GPG keys using that tutorial?  Thanks.

This is the first time I've done this, but following the directions from the wiki above do this (I've copied the key for you):

Copy the following:
```

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXOhUgEEALnFAL8QAwFpZZk1B6e2Ih46cZQGrhIjyA3p5BaJWs1fKMuXcIfRCKVbVY7s
zAPXiAZKfYCQTQar2nqat/ep5VbvqFphyiKldeGWa6HgWHAaeKUsZ9unPWOOIkxCcgJ3t5nn
fQgqUJ3lI+MJvLxe6yHPctbVCD+o3vxQQZ5Fpk9JABEBAAG0IkxhdW5jaHBhZCBQUEEgZm9y
IFJlaW5oYXJkIFRhcnRsZXKItgQTAQIAIAUCSXOhUgIbAwYLCQgHAwIEFQIIAwQWAgMBAh4B
AheAAAoJEM6Q2Jg+cx95JjIEALHLv+aU8zSsBFgKgdc6b+eL9+Ow1/SvxdgeNqLMjFH4Oe8y
c/CnSnW70BDaVpkK1Z5DDw7yZxTJy8sfyRurqOfuJYjf7bAtkIFO1fhWHKViFJ0s5y4o+BDD
/ZIDnsIESwT8GOy2bYqSn0g7qTxLEs3KHYAOPTMIqNyNlLS7jwMj
=+SQO
-----END PGP PUBLIC KEY BLOCK-----

```

Open up a terminal window and enter:
```
gedit
```

This will bring up a text editor.  Paste the code above in to the text editor and then save the file.

Open up System > Administration > Software Sources and click on Authentication tab.  The click on the Import Key File button and navigate to the file you just just saved and double click on it.

---

### Post by 71CH on 2009-04-24
Thanks for your help but it doesn't seem to be working.  I thought I wasn't as big of a noob as this.  :D  Do you think you can tell me how I can add this key through the command line?  Thanks.

---

### Post by 71CH on 2009-04-24
NVM I got it to import.  Thanks everyone for your help! :D

---

### Post by 71CH on 2009-04-24
So I just noticed that my fps got worse in glxgears after doing this.  Does this mean I should not use it?  I kinda hoped this would improve it...

---

### Post by caro on 2009-04-25
> **71CH said:**
> So I just noticed that my fps got worse in glxgears after doing this.  Does this mean I should not use it?  I kinda hoped this would improve it...

My fps didn't change much after I did made this change, but my compiz effects (like rotate cube) and my screen savers improved tremendously.  Check a few things before you decide it didn't work.

---

### Post by caraboy on 2009-04-25
On my HP530 with intel 945gm I have the same performance issues. :( I decided to wait some time before applying any trick, maybe ubuntu team will fix it.

---

### Post by alcCapone on 2009-04-26
> **caraboy said:**
> I decided to wait some time before applying any trick, maybe ubuntu team will fix it.

That's why I'm keeping the new driver, too. But at least I do what I can to improve this driver's performance.

The device section in my **xorg.conf **now looks like this:
```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "AccelMethod" "uxa"
    Option        "MigrationHeuristic" "greedy"
EndSection
```Now I'm back to 40% of my original performance - at least better than one fifth. It's measured with **glxgears** although one of the posted links suggested not to use this as a benchmark. But the general compiz performance also feels like approx. half the FPS I had in *Intrepid*.

BTW: Can someone recommend a simple non-game benchmark to measure your 3D performance?

---

### Post by Roanoke on 2009-05-02
Awesome. I had the same problem, the guide mentioned on page 1 solved it.

---

### Post by almikul on 2009-05-04
Can I suggest to run high-definition YouTube videos or any other flash ones in full screen mode as a benchmark? You will probably still get an awful performance no matter what you do in Jaunty.

When I reverted to Intrepid's driver (2.4) in Jaunty, the compiz effects improved and the DVD videos started playing much more smoothly, but the flash was still jerky and un-watchable and glxgears gave me ~250 fps instead of 800 fps in Intrepid. Also, when I set the virtual resolution to 2960x1050 to connect a second monitor, the whole video performance goes down the drain. 

I also tried to use UXA with native Jaunty driver, and it improved the compiz and DVD playback, but it does not allow to set virtual resolution to 2960x1050. Also, glxgears gave me ~350 fps. 

So, both 'workarounds' proved to be of little use to me. I hope one day the Ubuntu team could bring the performance to the Intrepid level which worked great for me.

---

### Post by alcCapone on 2009-05-06
After upgrading to [COLOR=DarkRed]**xserver-xorg-video-intel (2:2.6.3-0ubuntu9.2)**[/COLOR] I'm - according to **glxgears** - now back to approx. 50% of my *Intrepid* performance.

```

$ glxgears 
get fences failed: -1
param: 6, val: 0
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/57626 the monitor refresh rate.
2488 frames in 5.0 seconds = 497.523 FPS
2452 frames in 5.0 seconds = 490.358 FPS
2493 frames in 5.0 seconds = 498.499 FPS
2490 frames in 5.0 seconds = 497.964 FPS
2479 frames in 5.0 seconds = 495.672 FPS
2445 frames in 5.0 seconds = 488.672 FPS
2454 frames in 5.0 seconds = 490.515 FPS
2469 frames in 5.0 seconds = 493.770 FPS

```In games like **OpenArena** it feels like I'm having _way less_ than half of my original FPS value - although I don't have any exact reference value. The quality of *Youtube* videos watched in HQ in full screen mode is fair again - no black stripes appearing.

---

### Post by alcCapone on 2009-05-25
[CENTER][LEFT]I've made an interesting observation today. Since I upgraded to *Jaunty* I thought that the overall *compiz* performance is noticeable better when I use an attached monitor with my X60s laptop.

Today I pseudo-measured that with *glxgears* (yeah I know ... not a benchmark) and I have a plus of 10% (404 instead of 366) when I use the external monitor with a **higher** resolution of 1280x1024 instead of using the internal laptop LCD with 1024x768. But actually the performance boost working with the external monitor feels way bigger than just 10% - again *glxgears* is no benchmark.

When I switch the monitor to the laptop LCD native resolution ( 1024x768 ) then the performance loss is back.

So the question is: At what screen resolution do you experience your performance loss right now?


[/LEFT]
[/CENTER]
[U]
Christian.
[/U]

---

### Post by nutznboltz on 2009-07-19
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/342904]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/342904")

Says there's a new major version of the -intel driver is now available in Karmic.

Asks for volunteers to test Karmic Alpha:

[http://cdimages.ubuntu.com/releases/karmic/]("http://cdimages.ubuntu.com/releases/karmic/")

Download iso, boot into live mode, see if graphics improve.  Thanks.

---

### Post by piou13 on 2009-07-22
i tested with Karmic Alpha and i think that everything is back again
i boot with live cd and the video in full screen was ok .
also the mozila window was quick again when from minimized i bring it to front
im waiting for the stable release

---

