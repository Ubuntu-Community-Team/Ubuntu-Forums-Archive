---
title: "Aspire One A0751H + UNR Runs Slow"
date: 2009-08-20
forum: Hardware
---

### Post by trentscott4 on 2009-08-20
Has anyone experienced extremely slow loading times (i.e. when you click to open a program) with your Acer Aspire One Netbook and UNR?  I have an A0751H.  Does anyone know a way to fix this?

---

### Post by DarKnyht on 2009-08-21
Yes, I also had this issue, but thankfully I found [this]("https://help.ubuntu.com/community/AspireOne") reference guide.  You are much better off running the full 9.04 version of Ubuntu on the Aspire One A0751H.

Since following the instructions listed [there]("https://help.ubuntu.com/community/AspireOne"), I have full video working, sound, webcam, and microphone.  But be sure to copy down the instructions to reset the graphics because they will break when you update the kernel.

Now if Adobe would clean up their terrible Flash code I would be a happy man.

---

### Post by hmmmm on 2009-09-05
Hey I thought the same thing about adobe! But there the ones that are going to help here.
If you want to fix your choppy flash player remove swfdec with synaptic After you remove it go to [www.adobe.com]("http://www.adobe.com/") and get the deb package for flash works much better, youtube and all your flash sites will now work.

---

### Post by DarKnyht on 2009-09-06
I have and still ran into issues unfortunately, especially with full screen video.  To be honest, the same issue exists in Vista Basic that is on it too.

All that said, I ended up sticking with Vista (as much as I dislike it) as the primary OS on this netbook since it appears that the GMA 500 is not going to be supported in 9.10.  Until the support is there it just doesn't make sense for me to use it on a daily basis on here.  So for now Ubuntu is reduced to secondary status.

Perhaps once I hear news that 9.10 has resolved the graphics card issues, I will make a transition.  I really do prefer Ubuntu, but it is silly to intentionally cripple my user experience for it.

---

### Post by Druke on 2009-11-08
Does full Ubuntu-Desktop work notably better than UNR?

---

### Post by whitefort on 2009-11-09
> **Druke said:**
> Does full Ubuntu-Desktop work notably better than UNR?

On mine, it REALLY does.  UNR was so slow that it was totally unusable.  I'm running the normal install now, and apart from not being able to get good screen resolution (and generally poor graphics performs), it's at least basically functional.

---

### Post by Druke on 2009-11-09
> **whitefort said:**
> On mine, it REALLY does.  UNR was so slow that it was totally unusable.  I'm running the normal install now, and apart from not being able to get good screen resolution (and generally poor graphics performs), it's at least basically functional.

All of this after the patches?

---

### Post by whitefort on 2009-11-09
> **Druke said:**
> All of this after the patches?


Yeah, unfortunately.

I found I could click on something, then slowly count to about 10 or 20 before anything started to happen.  And the fade-in and fade-out on the NBR interface took 
f o r e v e r.

I'm getting better graphics performance on my 751 (normal Ubuntu) since I figured out how to make [COLOR=Blue][all this]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")[/COLOR] work.  Perhaps this would help with the Netbook remix too, I dunno...

The 751 is a nice looking machine, but it really does seem to have a rubbish graphic card.

---

### Post by Druke on 2009-11-10
well from what I've read it's that they combined it with the cpu to make a more efficient machine. That idea is really good, we just have to wait for a linux driver to be perfected.

My friend is running vista on it, and it's giving him tons of trouble. He himself is asking for ubuntu, but I'm very conflicted in recommending it. Notably his vista install is rather borked and we're not sure why.

---

### Post by whitefort on 2009-11-10
I was given mine for free for review purposes  (which was nice!).

It came with XP installed, but even then, brand-new, it felt very slow and clunky.  My little EEEPC 901 has WAY lower specs, but anyone comparing the two would think it was by far the more powerful machine.

I presume XP had the necessary drivers, but even so the machine was a bit of a dog, and really struggled even playing video.  I tried my best to give it a good review, but honestly couldn't do it.

When I installed Jaunty, the Acer's performance improved a bit, but I'm not totally convinced that it's ever going to be a good machine for graphics.

On the other hand, the cheap & cheerful EEEPC zooms along, with Compiz, rotating cubes and all the other eye candy.

Like I say, I was given my Acer for free, but in all honesty if I'd actually purchased it I would have been cursing myself by now and very disappointed.

---

### Post by Druke on 2009-11-10
Well he is mainly looking for a machine to take to class and take notes on. During D&D he may open a pdf or google spreadsheet for his character sheet. He doesn't plan to use it for anything powerful at all.

---

### Post by jchammons on 2009-12-24
I can say that after today on the full Karmic install using an a0751h:

 - Getting Flash directly from Adobe (I can't wait until that beast is put to rest), and...
 - Following the new method here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

... Made this machine perform better than any Microsoft Windows operating system I've tried on this hardware. Mind you, this machine won't play many 3d games well or Hulu without skipping (that's the only video site I've had issues with), but now the overall performance is very good and one could be quite productive with this machine.

---

### Post by P235 on 2010-05-20
Hello, I am wondering if anyone tried installing the new 10.04 release and what your experience of it is?

---

### Post by P235 on 2010-06-01
An update from my previous post last week:

I installed UNR 10.04 on my Acer and experienced the same problem from 9.10.  However, this time the computer was functional despite the graphics issue.  I found an [install script]("http://code.google.com/p/gma500/wiki/InstallScript") for the Poulsbo driver that solved the resolution and graphics issue.

At the time of writing, there are few posts concerning A0751h Acer and the graphics problem in relation to 10.04.  I hope this post proves useful.

Also, I learned of suspend and hibernation issues that are not yet resolved:

[http://ubuntuforums.org/showthread.php?t=1469340](http://ubuntuforums.org/showthread.php?t=1469340)

---

