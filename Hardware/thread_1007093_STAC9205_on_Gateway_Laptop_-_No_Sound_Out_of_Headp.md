---
title: "STAC9205 on Gateway Laptop - No Sound Out of Headphone Jack"
date: 2008-12-10
forum: Hardware
---

### Post by Ecologger on 2008-12-10
I have been trying to remedy this situation since 8.10 came out. Sound came out of the headphone jack in 8.04 but now the speaker mutes but no sound comes out of the headphone in 8.10. I have tried just about everything and I even messed up my alsa package so badly I had to reinstall Intrepid. So, is there any help out there for the STAC9205 users who cannot put any of the suggested model names into the hda intel sound statement, i.e. del-m44 and such because none of the suggestions work.

Much appreciation.

---

### Post by Ecologger on 2008-12-10
To add, the headphones do work when the computer is restarted WITH the headphones plugged in. But when you remove them, the jack will not work again until you restart again.

---

### Post by ckennow on 2008-12-13
I too am having this same problem with my Gateway laptop. Any suggestions would be helpful. There is no switch in Alsa mixer for the headphones and I don't know what to modify in the configuration files.

---

### Post by bgilbert on 2008-12-14
I am having the exact same problem on my gateway laptop, headphones work when plugged in during initial boot, but do not once they've been unplugged. Also the hardware volume controls seem to alter the wrong OS sound controls. I changed my snd-hda-intel model to dell-m42 by adding the following line to /etc/modprobe.d/alsa-base per this [**[COLOR="Blue"]thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=616845"):

```
options snd-hda-intel model=dell-m42
```

This seemed to fix my problem on restart, however a day later I was having the same problem again......which is extremely odd if you ask me. I am not very familiar with alsa, especially since I've only recently moved over to Ubuntu. I can say that I experienced no such problems under 8.04. If anyone has any suggestions I'm all ears.

Thanks in advance.

---

### Post by Ecologger on 2008-12-16
In the meanwhile we have been using the Hardy kernal, which works with both the brightness and the headphone jack, but not everything works correctly. Follow [this]("http://ubuntuforums.org/showthread.php?t=881127&highlight=gateway+laptop&page=7") for direction.

---

### Post by psychoelf on 2009-01-16
Same issue here on a Gateway 6850fx.  Headphones/speakers work on initial boot if plugged in, but stop once unplugged.  I noticed that there is about a half second of sound when first plugging in, but then silence.  Tried the modprobe file and like a previous poster pointed out it worked once but not again.  I don't want to revert to 8.04 due to other issues.  :mad:

---

### Post by agibby5 on 2009-02-10
I'm having this same problem.  It's very annoying, to say the least.

---

### Post by tecknos11 on 2009-02-28
Same problem here. I think it's the same with all t-series gateway laptops. Plugging in the headphones mutes both speakers and headphones

---

### Post by JackKerr on 2009-02-28
Did you try right clicking the volume button -> volume control -> switches -> checking the headphone box?

I was confused by that before.

---

### Post by psychoelf on 2009-03-01
You have a headphone option on a gateway with STAC9205 (if so what model, might be useful)?  I think the problem we are all having is that it is not switching properly and the only thing under Switches is "Analog Loopback".  There is not a button we have missed (so far), but thank you for checking.

It supposedly has to do with the current version of Alsa in the kernel.  Don't know if anyone has tried compiling their own as most of us don't know how to do that.

---

### Post by JackKerr on 2009-03-01
[http://ubuntuforums.org/showthread.php?t=806620&highlight=sound+headphones](http://ubuntuforums.org/showthread.php?t=806620&highlight=sound+headphones)
This says 8.04, but it looks like it would work in 8.10 as well.

---

### Post by psychoelf on 2009-03-01
Yeah...I've tried that one.  The Gateway option does not work.  I even started trying the different models that had STAC9205 to no avail.

---

### Post by Alessa on 2009-03-15
Having this issue myself.  Would love to hear of a fix.  At first search I thought this was a solo problem, but it does appear this is affecting enough users that it should be looked into and/or solved somewhere.

---

### Post by kapchoi on 2009-03-18
Same problem here. Gateway laptop T-series. Would love to see a remedy for this issue.

---

### Post by Zamboniman on 2009-03-31
I was finally able to solve this problem on my Gateway T-1620 by compiling and installing the latest alsa snapshot.  It's nice to finally have this working.  There's a script in the forums here that can automate this for you at [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)  Use the -snap option.

---

### Post by psychoelf on 2009-03-31
No luck with the Alsa upgrade on my 6850FX.  :(

Whoops...didn't use the "-snap" option.  Trying again with that.  :)  ==>Update:  Still no headphones.  Poo.

---

### Post by bkanuka on 2009-04-07
I'm in the same position.

---

### Post by Kain000 on 2009-04-09
Bump, same problem, seems to be gateway specific, my dell works fine.  newest alsa driver release has no effect.

---

### Post by tomsa on 2009-04-22
I'm having the same problems also.  I tried upgrading my ALSA using the automated script and still no sound from the headphones.  The internal speakers work fine.  I'm on a Gateway T-1625 laptop and have the STAC9205 sound card as well.  I've been working on a solution here as well:

[http://ubuntuforums.org/showthread.php?p=7117161#post7117161](http://ubuntuforums.org/showthread.php?p=7117161#post7117161)

But I haven't gotten anywhere so far.  Maybe something in there will give one of you guys a bright idea that solves all of our problems!

---

### Post by Wootyeah on 2009-07-29
I fixed mine on this Gateway T 1628 Laptop by doing what this guy did from step 5 to the end.  It worked for me.  I can post some specific outputs if you like, but I'm really somewhat of a noob.

Anyway, here it is. Hope it helps.

[http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/](http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/)

---

### Post by freeztar on 2009-09-30
> **Wootyeah said:**
> I fixed mine on this Gateway T 1628 Laptop by doing what this guy did from step 5 to the end.  It worked for me.  I can post some specific outputs if you like, but I'm really somewhat of a noob.

Anyway, here it is. Hope it helps.

[http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/](http://blog.wessendorf.org/software/headphones-with-ubuntu-904-and-gateway-t-6345u/)

Thanks for that, it worked perfectly on my T-1620!

---

