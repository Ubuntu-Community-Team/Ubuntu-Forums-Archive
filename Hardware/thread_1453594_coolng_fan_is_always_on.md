---
title: "coolng fan is always on"
date: 2010-04-13
forum: Hardware
---

### Post by confused_user on 2010-04-13
I have an advent 4213 netbook.  When on battery power the cooling fan stay's on all the time which drains the battery too fast. 

Ironically i get 30-45 more minutes from windows 7.

it's doing it right now with only about 30% cpu being utilised.

Any idea's how i stop the fan from running all the time, just when it's hot would be nice?

---

### Post by khelben1979 on 2010-04-13
[How to control fan speed]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed").

I'm not sure if it works with your exact model of your laptop, but you can try at your own risk.

Also, it's good to have control of what software the system is using to keep the cpu usage down thereby keeping the heat down inside. Fast video drivers prevents the cpu from "working itself to death".

---

### Post by confused_user on 2010-04-13
thanks, that looks a bit drastic though, shouldn't ubuntu already do auto fan control?

---

### Post by khelben1979 on 2010-04-14
> **confused_user said:**
> thanks, that looks a bit drastic though, shouldn't ubuntu already do auto fan control?

I'm not sure. What version of Ubuntu are you using?

---

### Post by confused_user on 2010-04-14
9.10 

2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

fan speed control appears to work as it slows and speeds up now and then but remains on all the time.

In windows 7 (i hate referring to this) the fan is not on all the time, it comes on with high cpu, when otherwise hot and switches off when cool.

---

### Post by khelben1979 on 2010-04-14
Maybe it gets more efficient with the next release once it's stable?

[HOWTO: Fancontrol]("http://ubuntuforums.org/showthread.php?t=42737") if you're interested.

---

### Post by psyopper on 2010-04-17
I've been researching fancontrol under 9.10 for about a week now trying to fogure out how to modify my cpu and system fan settings. The like you posted is from 2005 and is slightly depricated... :)

---

### Post by confused_user on 2010-04-17
yeah i forgot to post on that, the guide you mentioned, while appreciated is pretty old and a lot has changed since then.

My gut feeling is that implementing that on 9.10 would be a bad idea.

I did find today that switching from firefox to opera has helped.  It seems that while i have firefox open i get 100% fan, even when the cpu usage is low.

With opera running the fan just ticks over rather than blowing 100%.  not a solution but an interesting find.

the trouble with waiting for the next release is that 10.04 will bring it's own new problems and break other things that used to work.

With Ubuntu, waiting for the next release is not a viable idea.  You end up in a perpetual cycle of waiting for things to be fixed only to find things that used to work dont anymore.

---

### Post by Roly25 on 2010-06-17
I have exactly the same problem on my Advent 4213 Netbook running Ubuntu 10.04.  The fan control hotkey Fn F11 used to work under Windows XP/Vista and 7, but under Ubuntu 10.04 it has abserlutly no effect on the fan, as a result it is draining my batter fast.  under windows Icould use my netbook for hours on battery but under Ubuntu I can only use it for a few hours.  I turned it on this morning and the battery meeter was reporting 2hours15min of battery left at 7am and now it is reporting  1hour15mins of battery left only 45mins after I turned on my Notebook, it's getting really annoying as there doesn't seem to be a solution to this and I don't want to switch to another distro as all the hardware in the Advent works out of the box and I'm worried that switching distros will bring on new problems like hardware not working (especially the builtin 3G modem).

Roland

---

