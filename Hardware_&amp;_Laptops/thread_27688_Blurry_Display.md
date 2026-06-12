---
title: "Blurry Display"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by Linkable on 2005-04-17
I am a total Linux newbie so maybe I'm just doing something wrong but there's a weird blur on my screen. I can read everything okay but it's not as sharp as I'd like it to be (and like I'm used to with Windows).
I have a nividia geforce 4 4600 on a Samsung SyncMaster 710n TFT screen @ 1280x1024. I have installed the nividia drivers following the BinaryHowTo guide. I'm getting somewhere in the 4000's FPS when I run glxgears in terminal. 
Does anyone have a suggestion on how to fix this?

---

### Post by andvaranaut on 2005-04-17
[QUOTE=Linkable]I am a total Linux newbie so maybe I'm just doing something wrong but there's a weird blur on my screen. I can read everything okay but it's not as sharp as I'd like it to be (and like I'm used to with Windows).
I have a nividia geforce 4 4600 on a Samsung SyncMaster 710n TFT screen @ 1280x1024. I have installed the nividia drivers following the BinaryHowTo guide. I'm getting somewhere in the 4000's FPS when I run glxgears in terminal. 
Does anyone have a suggestion on how to fix this?[/QUOTE]
 The only thing I can think of is that you are not using a 1280x1024 resolution, but something smaller (say 1024x768 ). Since the TFT screen resolution is fixed at 1280x1024, the TFT will scale the 1024x768 image to its native resolution, giving a rather blurry image.

Look in System > Preferences > Screen resolution (or similar names ;)) and check that you indeed have 1280x1024 selected.

Hope this helps

---

### Post by Linkable on 2005-04-18
Thank you for your reply.

My TFT screen can display any resolution up to 1280x1024 and I'm quite sure that I've put it in 1280x1024 via System > Preferences > Screen resolution. So I don't think that caused the problem.

---

### Post by andvaranaut on 2005-04-18
Hi linkable

I mostly have no clue, then ;)
However, there are still two things to try. First, most TFT's displays have a button which adjusts the TFT's settings to get the best picture. This auto-adjustment is automatically triggered when you change resolution. However, if you don't change resolution but change the refresh frequency, it might not be. Maybe you have slightly different optimum settings for Windows and Linux and your TFT is stuck with the Windows ones. Try autoset and see whether it works...
And second, if your problem is exclusively with the way fonts are displayed, [http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456) is highly recomendable with hi-res TFT displays.

Good luck, andvaranaut

---

