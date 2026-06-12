---
title: "hibernating on a server without X"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by dninja on 2007-05-18
I have a server which won't be running X and I want to set it up to hibernate at night and come back on in the morning. I was planning to use wake on lan called from another machine which has to run 24/7  to wake it up and a cron job to hibernate it.

Is there a better way?

Can anyone point me at a howto for hibernation which involves no X stuff? The wiki article assumes you are running gnome.

---

### Post by kidders on 2007-05-19
Hi there,

There's nothing much more to hibernation than invoking a small script, so not having a graphical environment doesn't really make a difference. Hibernating a _server_ though is something that most people assume will never be done ... are you sure simply shutting down & restarting the machine wouldn't be wiser (in terms of security & stability)?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by dninja on 2007-05-19
It is a home server which is why I want it off overnight and I just figured that once it is up and running if I use hibernate then I can leave things like screen sessions running on it. I can also get the wake on lan to make sure that it is up and running just before I get up so that it has pulled down all my mail and done the other housekeeping before I need it.

---

### Post by kidders on 2007-05-19
Yep. :-) The decision is yours ... I just wanted to be certain you'd considered the potential for weirdness.

I'd probably do it the way you described, although one minor variation could be to use your CMOS clock to wake the machine up again (assuming your BIOS supports that). Needless to say, I've never even *considered* doing this before (hehe) so I'm not completely sure, but the place to start is probably **apt-get install hibernate**. Then, if you're not familar with it, take a look at how /etc/crontab works.

I would strongly recommend taking some precautionary measures before actually performing a scheduled hibernation though, such as shutting down Postfix, for instance. Corrupted email would be nasty!

---

### Post by dninja on 2007-05-19
I'm going to try running the machine in parallel with my current server before putting it live, see what does get killed. At least I'm not running X so don't have to worry about video drivers and stuff like that!

Off the top of my head the BIOS supports a single wake up at given time but not repeated but I will have a check.

---

### Post by kidders on 2007-05-19
> **dninja said:**
> At least I'm not running X so don't have to worry about video drivers and stuff like that!That's certainly a plus! :-) When it comes to servers though, the real worry is what might happen if the hibernate recovery were ever to fail for some reason. Databases in the middle of being manipulated, mail in the process of delivery, etc. might get garbaged. That's what motivated my idea about taking a few basic precautions ... nothing too fancy though.

> **dninja said:**
> Off the top of my head the BIOS supports a single wake up at given time but not repeated but I will have a check.Personally, I like your wake on LAN idea better (mostly because it's more configurable), but I thought I'd mention that as another possibility.

---

### Post by dninja on 2007-05-20
The advantage I have is that as I'm the only one using the server I can pretty much guarantee that it shouldn't be too active when it shuts down, if I was still working I'd override the shutdown. I think the only demons doing anything may be qmail/postfix (haven't decided yet) and fetchmail. I'll probably look at killing both in the hibernate script. I can leave mysql and apache running as they will be idle, if they do have problems I can shut them down as well.

Another option with the wake on lan was to setup some kind of port knocking on my router to do the wake up just in case I'm away from home and need access to the server.

---

