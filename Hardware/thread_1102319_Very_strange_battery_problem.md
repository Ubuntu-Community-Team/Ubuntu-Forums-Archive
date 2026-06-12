---
title: "Very strange battery problem"
date: 2009-03-21
forum: Hardware
---

### Post by BrendanM on 2009-03-21
Hey, all, I'm using Ubuntu on an eeePC 901. I've recently started seeing a very odd battery problem.

Basically, when charging, the battery seems to "hang" at certain points. Like, it'll charge to 27% and then not charge any higher. At first I thought this was just a problem with the software battery meter (which are notoriously inaccurate) but it seems to be quite accurate. For example, if I remove the AC power, it will run down from 27% to 0% and the laptop will die right around when it reaches 0%.

Now, even stranger, I have figured out a trick to charge the laptop. For example, if it hangs at 27%, and then I unplug it, right after it's unplugged, it will show 28%. I can then plug it back in, and it will continue charging until it hangs again. There seems to be no rhyme or reason to when it hangs, I've seen it get stuck at 19%, 27%, 33%, 48%, 78%, 80%, etc. and it's not always the same places.

Has anyone EVER seen something like this? Or heard of it? Does this 
suggest a problem with the battery itself, the charging circuit in the laptop, the software?

---

### Post by KermMartian on 2009-05-07
I just ran into this problem for the first time with my new eeePC 901; it hung on 46%.  Any idea what could be causing this? I tend to suspect Ubuntu over hardware (or that could be wishful thinking).

---

### Post by 1love on 2009-05-08
I'm having similar problem where battery time is reported incorrectly by acpi and gnome power manager: 

[https://bugs.launchpad.net/ubuntu/+bug/371981](https://bugs.launchpad.net/ubuntu/+bug/371981)

I have regular Toshiba Satellite laptop but there's this other bug which was reported by netbook user:

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/373081](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/373081)

---

### Post by mr.niceguy&lt; on 2009-05-08
I'm having similar problem it hang only in 57% when ever we charge its still and hang this is strange this is not a battery problem its the CPU sometimes

---

