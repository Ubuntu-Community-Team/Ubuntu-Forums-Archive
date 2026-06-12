---
title: "Please help me create a guide for laptops/notebooks and power management/battery life"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by Axx83 on 2007-11-06
Hello everyone, I own an Acer travelmate 3040 (specifically travelmate 3043wtmi) a wonderful piece of hardware but the battery life with ubuntu 7.10 sucks, in windows vista it's a little better but I don't want to use that disgusting piece of crap, I came too late for refunding unfortunately and now I have it preistalled.

Anyway, I read a couple of topics around here but I didn't understand much. In my case suspend (aka suspend 2 ram) does not work, hybernate (suspend 2 disk) works badly and I substituted that with s2disk which works fine but it's not what I wanted (I prefer suspend) my question is:

What are the tweaks available to better my battery power, better manage my laptop in battery mode etc etc ?

So far I installed laptop-mode and modified /etc/default/acpi-support to enable it...but nothing changes significatly. Any other options ?

I'd like to create a documentation in the main site so that people can tweak their comp more easily, without having to read 3000 non pertinent messages on the forum.

Thank you.

---

### Post by Axx83 on 2007-11-06
I forgot to say, I also own an Asus A1300F laptop, it's very old with a celeron 800mhz and 128 mb of ram, actually 100 since 16 are taken by the video card.

I installed xubuntu dapper the other day since xubuntu gusty was running too slow, dapper runs fine but it lacks many gnome power tweaks gutsy has, also laptop mode does not work properly.

Any tips on own to tweak this one also ? (less priority on this one tough)

---

### Post by Evagrios on 2007-11-06
Good initiative - I'm a complete newbie, so I'm not likely to have much to add. there is this issue, which I like to hear some informed opinions on.

[http://www.beranger.org/index.php?page=diary&2007/10/24/18/07/21-it-s-confirmed-gutsy-is-killing-]("http://www.beranger.org/index.php?page=diary&2007/10/24/18/07/21-it-s-confirmed-gutsy-is-killing-")

---

### Post by Axx83 on 2007-11-06
I read it, and I didn't understand a thing about that, besides a couple of people saying that ubuntu sucks get this distro instead, and another couple saying that is not true shut up.

Some linux power users are VERY immature, at least newbies are humble.

Anyway that didn't help, I took laptop mode off my comp because it actually did nothing useful, and now that I know there is a bug involved all the better.

---

### Post by Axx83 on 2007-11-06
Forgot to mention my father owns a Lenovo Thinkpad x60s that he wanted to ubuntize, well i found this WONDERFUL site with a lot of guides:

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

and a cool thing about cpu scaling:

[http://www.thinkwiki.org/wiki/Installing_Kubuntu_6.10_on_a_ThinkPad_X60s](http://www.thinkwiki.org/wiki/Installing_Kubuntu_6.10_on_a_ThinkPad_X60s)

interesting, I have the same cpu on my Acer, maybe I can try that out, has someone tried it before on a different computer ???

---

### Post by Axx83 on 2007-11-20
No one has any infos ?

---

### Post by linuxonbute on 2007-11-20
It's been said before but a good starting point is [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

Anyone can contribute to it by adding info about their own PC.

Not forgetting, of course, the 'sticky' threads on this forum.  :wink:

---

### Post by Axx83 on 2007-11-20
Yes that's a start but my notebook is very uncommon outside Europe, don't know why since it's a wonderful piece of hardware, and besides that the website only has very old guides, also non specifically focused on battery management...

---

### Post by linuxonbute on 2007-11-20
Well I can only ask a few questions which you may have already considered.

How old is the battery? 

If it's old then did it last longer in the past?

What do you do on the machine - a lot of cd/dvd burning, graphics, hard disc intensive stuff etc?

---

### Post by Axx83 on 2007-11-21
No the battery is totally new as the notebook, couple of months and it's NEVER been used inside my house, it's always unplugged; then when I use it outside I plug it in and it lasts the poor half hour I mentioned, maybe not even a full 30 minutes sometimes.

On windows with asus battery management etc etc it lasts at least 1 hour and 20 minutes. AND IT'S WINDOWS VISTA for god' sake.

There is a problem here. But it's not just for my pc, I want to write something easy and useful that every newbie can use on his computer.

---

### Post by Axx83 on 2007-11-21
And no I don't do cpu intensive stuff when I use the battery, only word processing and mp3 playing, the rest is always done with ac plugged and battery unplugged.

---

### Post by linuxonbute on 2007-11-21
> **Axx83 said:**
> And no I don't do cpu intensive stuff when I use the battery, only word processing and mp3 playing, the rest is always done with ac plugged and battery unplugged.

My gut feeling is that the battery is faulty.

Also why do you unplug the battery while running on A.C power?

If you run on A.C power with the battery still connected, which I really believe is the safer way to use it on A.C power, then the power supply should be capable of supplying enough power to do whatever you want AND charge the battery.

How do you ensure that the battery is fully charged when you do use it?

Do you shut down the computer, plug the battery in and then the charger to charge it up?

---

### Post by Axx83 on 2007-11-22
I unplug the battery when I'm home only because the less charge/discharge cycles the battery does the more it will last and since there are absolutely no disadvantages in working with no battery (besides having to unplug it), that is the best way.

I also can safely say that the battery has done enough charge/discharge cycles to be considered at full potential, manuals usually say at least 5 or 10 cycles, for every litium battery in the world is the same, so it can't be considered new, neither too old, it's perfectly ok.

With windows Vista the computer can work for at least 3 hours, the acer battery manager is set to default (britness goes down, cpu power also), with Ubuntu it's not even 2 hours, probably 1 and a half...

Now, I'm a new user but I've read a couple of guides and NO ONE says the same thing. I don't even know if laptop mode is safe for my hard drive, because 100 people say yes and 100 people say no...

That's why I want to gather a few useful tips for laptop users and make a document for everyone to read.

---

