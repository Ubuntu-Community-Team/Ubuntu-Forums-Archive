---
title: "Lenovo Y510 + Ubunut 8.04 - Oh man =/"
date: 2008-05-02
forum: Hardware
---

### Post by arvast on 2008-05-02
I have several of problems. And I will start out with just listing them :/

**1.** [COLOR="Red"]My laptop doesn't log out, or turn off. It clears the screen so you only see the background image and then stops like that until you hit the power button. Then it will just turn off.[/COLOR]

**2.** [COLOR="Red"]After hibernation, sound doesn't work. Have to turn off and restart computer.[/COLOR]

**3.** [COLOR="Red"]The brightness buttons are inverted, fn + brightness up makes the screen darker and vice versa. Also when idling, instead of dimming the screen it brightens it. Not so good for power saving eh?[/COLOR]

**4.** [COLOR="Red"]Back to the sound issue, only the back speakers - the subwoofer - is giving out sound when playing media.[/COLOR]

I read some on this but haven't really found a solution, I would be very grateful for any help.

Thanks in advance,
arvast

---

### Post by roma2 on 2008-05-02
Try this site: [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

Great resource on Linux/Thinkpads

Hope it helps.

---

### Post by arvast on 2008-05-03
Theres nothing about IdeaPads there =/ Some of its similar but its hard to navigate D:

---

### Post by tlcrepairs on 2008-05-20
> **arvast said:**
> I have several of problems. And I will start out with just listing them :/

**1.** [COLOR="Red"]My laptop doesn't log out, or turn off. It clears the screen so you only see the background image and then stops like that until you hit the power button. Then it will just turn off.[/COLOR]

**2.** [COLOR="Red"]After hibernation, sound doesn't work. Have to turn off and restart computer.[/COLOR]

**3.** [COLOR="Red"]The brightness buttons are inverted, fn + brightness up makes the screen darker and vice versa. Also when idling, instead of dimming the screen it brightens it. Not so good for power saving eh?[/COLOR]

**4.** [COLOR="Red"]Back to the sound issue, only the back speakers - the subwoofer - is giving out sound when playing media.[/COLOR]

I read some on this but haven't really found a solution, I would be very grateful for any help.

Thanks in advance,
arvast
I have the same problem with sound, subwoofer doesnt work but other 4 speakers do but not very loud. brightness controls are inverted, sound quits after suspend until restart and return from hibernate gives white screen until hard reboot. shutdown and restart are ok and bluetooth is a bit unstable. web cam not i have not messed with yet.

Dumped vista, installed win xp pro and ubuntu 8.04.(ubuntu default)

---

### Post by polluxx on 2008-05-20
There's already an excellent thread by wyth on the Y510, see [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=687663&page=1").

That should cover the sound issue, at least re speakers not working and so on.

As for the dimness/brightness situation, wyth also offers a workaround on one of the last pages, to at least get the power management right. Apart from that, there is currently no other solution, afaik.

Hibernation + white screen seems to be a problem in combination with compiz.
There exists already a bug report on this, I followed the solution given [[COLOR="Blue"]here[/COLOR]]("http://bugs.launchpad.net/dell/+bug/160264/comments/69"), and that did the job. Mind you, hibernation/suspend generally seems to be a lot more unstable in combination with compiz than without.

---

### Post by Sapfeer on 2009-04-26
Hello there

Recently I've installed Ubuntu 8.10 on my Y510 and I faced with some issues: after login brightness is reset to minimal value and I have to increase it to comfort level and WiFi indicator always showing that WiFi is On even if it turned Off... Is there a way to solve such problems?..

---

