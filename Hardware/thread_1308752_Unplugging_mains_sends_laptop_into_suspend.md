---
title: "Unplugging mains sends laptop into suspend"
date: 2009-10-31
forum: Hardware
---

### Post by QwUo173Hy on 2009-10-31
The battery was 50% charged so I don't see a reason for this behaviour. I know this was an issue on a previous release, but with all the changes under the hood, I don't know which package to file a bug against.

Can anyone direct me a little?

---

### Post by BenRitchie on 2009-11-01
I'm seeing the same problem with an HP 2133 netbook - was fine with 9.04, now suspends when I remove mains power even with 100% battery

---

### Post by QwUo173Hy on 2009-11-01
Mark yourself as affected in the bug-report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421985](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421985)

If you want to circumvent the problem for now, you can run System->Preferences->Power Management and go to the On Battery Power tab.

The entry for 'When laptop lid is closed' is the behaviour that gets acted when you remove your AC cable. I've changed it to 'Blank Screen' for now, as I can live with that.

---

### Post by texla on 2010-06-25
> **jarlath said:**
> 
If you want to circumvent the problem for now, you can run System->Preferences->Power Management and go to the On Battery Power tab.

The entry for 'When laptop lid is closed' is the behaviour that gets acted when you remove your AC cable. I've changed it to 'Blank Screen' for now, as I can live with that.
Worked for me!  Old laptop with a touchy cord running Karmic was turning off non-stop because of a short in the cord.  Now it's just about plugging it back in - great tip.

---

### Post by Leonasha on 2010-07-27
I too have this problem and then some.

If I unplug the main power while using the computer, it suspends and will not wake up.

If I power up on battery power, all is well til I plug in the main power ... then it suspends and won't wake up.

If I purposefully suspend the computer using the top right corner button, it suspends and does not wake up unless I hold the power button for a few seconds, whereupon it asks for my password and resumes function, but without my wired internet connection. Wireless is still accessible, but as it's my neighbour's, I can't use it all the time ;)

I am running Lucid on an HP G61.

edit: I have changed the power management settings as suggested by Jarlath, but it didn't change the behaviour.

---

### Post by QwUo173Hy on 2010-07-29
If I were you Leonasha, I would disable all settings related to suspend in the Power Manager. I just doesn't seem to work well with your hardware.

If you followed my suggestion above for the "When laptop lid is closed" section, then just do the same for the other sections.

It's not ideal, but that's what I would do until I found better information :)

---

### Post by Leonasha on 2010-07-29
> **jarlath said:**
> If I were you Leonasha, I would disable all settings related to suspend in the Power Manager. I just doesn't seem to work well with your hardware.

If you followed my suggestion above for the "When laptop lid is closed" section, then just do the same for the other sections.

It's not ideal, but that's what I would do until I found better information :)

ok then. it just seems kinda silly to have a laptop you have to restart in order to run on battery power!

---

### Post by QwUo173Hy on 2010-07-31
Yes, it is. But it would be my favorite of all the options I know of :)

---

### Post by Leonasha on 2010-08-05
interestingly, this problem has now corrected itself. I don't remember installing updates ... not sure how this happened.

now if only I could get Ubuntu to recognize my webcam...

---

