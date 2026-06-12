---
title: "No sound after suspend - resume"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by citronelu on 2006-06-05
I have an Acer Aspire 1362WLMi (Sempron 2800+, Nvidia FX Go 5200). I made a clean install of Ubuntu 6.06, and everything worked ok - except suspend and wireless.
Yesterday I found this page - [http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO) - and helped me make suspend-to-RAM and resume work. However, now I have a new problem: after resume, the sound doesn't work anymore.

The sound chipset is identified as VIA 8235 with VIA1612A. I search the forums, but it didn't help.

---

### Post by Flamekebab on 2006-06-08
I have the same laptop and I'm trying to get suspend and hibernate working.

I'm a bit of a n00b, however, so I'm struggling. A little help anyone?

---

### Post by ddumanis on 2006-06-09
Do

**sudo gedit /etc/default/acpi-support**

and change mode from "mem" to "standby" (in the 3rd item down).

Worked for me!

---

### Post by citronelu on 2006-06-09
This doesn't solve my problem - the sound card is not working after resume.

---

### Post by ddumanis on 2006-06-09
Time to file a bug!

---

### Post by Flamekebab on 2006-06-09
Is there a simple way of restarting the sound system?

That could possibly be a viable work-around..?

---

### Post by Flamekebab on 2006-06-10
It would seem, if you're running ALSA, the following would help:
```
/etc/init.d/alsa-utils restart
```
or
```
alsa-utils restart
```

---

### Post by l.tambiah on 2006-06-23
Hmmm, I have discovered that my sound has completeley gone dead after doing a hibernate. Not even a reboot gets my sound back. Before I did a hibernate my sound was perfect.

---

### Post by tebibyte on 2006-06-23
I have the same problem, though with a diffrent laptop. Wasn't their a major sound bug In previous releases? It could be related.

---

### Post by l.tambiah on 2006-06-23
I think the hibernate needs some love, I guess its hard to do with so many laptops around, I am avoiding hibernate now altogether, though I can use suspend with no issues after changing the sleep.sh code.

---

### Post by borris.morris on 2007-02-06
what change did you make to the sleep.sh code? also, i have a thinkpad 600x and same problem.

---

### Post by flossgeek on 2007-02-07
[http://www.ossgeeks.co.uk/?p=10](http://www.ossgeeks.co.uk/?p=10)

---

### Post by borris.morris on 2007-02-10
nope, no go.

---

### Post by rapmuzick on 2007-02-27
I've been having the same problem... I'm a noob too, but could you feasibly unload the sound module before standby and load it after waking up?

---

### Post by borris.morris on 2007-02-28
possible, don't know which one to unload or how. can't remember the code.

---

### Post by Grizzlitiger on 2007-09-02
Hi,

I've now finally managed to get my Thinkpad to suspend to ram too - but like you I have the problem that my sound is **completely dead and doesn't even work after a reboot.**

---

### Post by Grizzlitiger on 2007-09-02
nope mine could be solved simply by unmuting PCM and CD with alsa mixer and turning them up.

---

