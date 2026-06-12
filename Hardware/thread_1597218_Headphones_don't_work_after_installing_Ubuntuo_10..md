---
title: "Headphones don't work after installing Ubuntuo 10.10"
date: 2010-10-15
forum: Hardware
---

### Post by MrHuaRen on 2010-10-15
I have looked this up online, and all the explanations I have found so far are extremely confusing (and don't make any sense to me).

My problem is that after upgrading my ubuntu version my headphones stopped working. My speakers work, but turn off when my headphones are put in (as they should). However no sound can be heard at that time.

I have heard some vague ambiguous explanations talking about:
Alsa Mixer
Volume control (the same thing?)

but so far no solution.

What can I do? (please be clear and don't assume that I know everything that you do).

Thanks.

---

### Post by MrHuaRen on 2010-10-15
My computer is useless with out headphones, come on, please help.

---

### Post by WaroDaBeast on 2010-10-15
Hope this helps: [http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)

My €0.02.

**EDIT:** Sorry about that hasty answer. I meant to say that you have to look for your soundcard and add the line corresponding to your hardware at the end of alsa-base.conf as follows: ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```Save and reboot. Voilà, your headphones should be working now! (Just keep in mind that you need to switch between “analog output” and “analog headphones” in the sound settings manager depending on which one you wanna use.)

---

### Post by MrHuaRen on 2010-10-15
Could you provide more steps?

---

### Post by WaroDaBeast on 2010-10-17
Well, could you tell me what your soundcard is? (Alsamixer should provide that information.)

If it's an integrated sound chip, you might be able to have your headphones back by adding &#8220;options snd-hda-intel model=*****&#8221; or &#8220;options snd-hda-intel model=***** position_fix=*&#8221; (without the quotes) at the end of alsabase.conf file, just as I explained in my previous post. All you need to do is to merely copy-paste it after all the text in that .conf file.

If your computer is a laptop, the line should be provided in that list. By the way, I'm really sorry I gave you a link towards a page in French, but that page is the only place I've found such a list.

If your computer isn't a laptop, then, you should try &#8220;auto&#8221; for the model and &#8220;0,&#8221; &#8220;1&#8221; or &#8220;2&#8221; for the position.

Hope you got it working this time around. :)

---

### Post by MrHuaRen on 2010-10-19
A friend of mine fixed the problem by (he said), writing a new line connecting the headphones to the sound card.

Thanks for the help though!

---

### Post by pwabrahams on 2010-11-01
I encountered the same problem, although it did not manifest itself until a recent update to 10.10.  Before that, the headphones were working with 10.10.  Please see [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/669224](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/669224) for more information.

---

### Post by manco1911 on 2010-11-20
I have an Asus G50vt and had this same problem. Just followed WaroDaBeast steps and voila ! Solved !

Thanks WaroDaBeast, exelent solution. 

Here is my own [thread]("http://ubuntuforums.org/showthread.php?t=1624557") on this issue, with the steps i followed.. if you need more details just send a PM and will post on this and that thread.

---

