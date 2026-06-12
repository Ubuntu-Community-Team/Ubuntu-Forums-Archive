---
title: "Sound comes out of speakers and headphones"
date: 2009-06-21
forum: Hardware
---

### Post by houms on 2009-06-21
Good day folks,
I have just installed Jaunty 9.04 on a vostro 1520 laptop. Everything is working great, except I have one issue with the sound. it works but when i plug in headphones, it comes out of the headphones and the speakers at the same time. I cannot get it to just play on the headphones only. Please does anyone have any suggestions on how to fix this? I believe this laptop uses snd-hda-intel. I appreciate any assistance.

---

### Post by yoblin on 2009-06-21
> **houms said:**
> Good day folks,
I have just installed Jaunty 9.04 on a vostro 1520 laptop. Everything is working great, except I have one issue with the sound. it works but when i plug in headphones, it comes out of the headphones and the speakers at the same time. I cannot get it to just play on the headphones only. Please does anyone have any suggestions on how to fix this? I believe this laptop uses snd-hda-intel. I appreciate any assistance.

Also having this problem... are you having any trouble with freezes? Half the time when I start the computer the mouse/keyboard don't work (helps to tap caps lock throughout the boot process) and I get lockups randomly every couple hours that need a hard reboot

---

### Post by houms on 2009-06-21
do you have a vostro 1520?

yes i experience that same symptom. I have to reboot it to get it going. I dualboot with sidux and it works fine. I have not seen the freezes with sidux and the new .30 kernel. And that new kernel works with the sound card flawlessly.  Its just a real other distros have these issues.

Oh i have not been able to find a fix for the freezing issue, and i really am not sure what causes it.


as far as the sound issue, i have tried adding the lines  

```
options snd-hda-intel model=laptop
```

and

```
options snd-hda-intel model=dell
```


to my alsa-base.conf, and neither solve my problem. Let me know if you have any suggestions.

---

### Post by yoblin on 2009-06-21
Yes, I have the Vostro 1520.

I just upgraded to the newest kernel in the jaunty repositories and it actually made things worse: wireless no longer works.

Fixing wireless isn't the big problem though, I can work on that.

What I really need is a way to stop these freezeups that are now happening every 30 minutes or less.

None of the logs have any info after a freeze, so I don't know where to start debugging...

---

### Post by yoblin on 2009-06-21
Tried upgrading to latest 2.6.30:

It fixes the headphone problems, and I haven't been getting the keyboard/mouse detection problems (in this kernel or the latest in jaunty repos.)

The broadcom wireless drivers need to be compiled from source ([http://ubuntuforums.org/showthread.php?p=7401742](http://ubuntuforums.org/showthread.php?p=7401742))

the freezes are NOT fixed... however there's a kernel panic at least now instead of just nothing. Logs still show nothing.

Ugh I don't want to have to go to windows for the first time in years.. Maybe I'll try to get OSX on this machine for a while.

---

### Post by houms on 2009-06-21
no need for the new kernel for me, although thanks for the suggestion. 

I just installed alsa 1.20 for source. It was very easy. and has finally solved my intel hda issues. if anyone needs those steps let me know.

---

### Post by yoblin on 2009-06-24
bad motherboard on the new laptop... there goes two weeks of useless kernel debugging ](*,)

---

### Post by houms on 2009-06-27
> **yoblin said:**
> bad motherboard on the new laptop... there goes two weeks of useless kernel debugging ](*,)


How did you find that out? what kind of laptop was that on?

---

### Post by yoblin on 2009-06-29
> **houms said:**
> How did you find that out? what kind of laptop was that on?

New Vostro 1520, freezes a lot when the power cable is plugged in. Thought it was a linux problem until I installed vista and it did it on that, too.

---

### Post by subfusca on 2009-08-05
Similar to Houms, I installed the latest alsa drivers (1.0.20), which worked perfectly! I tried everything else, but nothing worked until I stumbled upon instructions to install the alsa drivers ([http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)).

---

### Post by Xavier_To on 2009-08-25
Hi houms,

I have exactly the same problem as you did. Can you provide the steps to fix the problem ?

Thanks

---

