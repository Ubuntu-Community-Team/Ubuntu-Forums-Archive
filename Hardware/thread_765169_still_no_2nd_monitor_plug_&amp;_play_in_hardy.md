---
title: "still no 2nd monitor plug &amp; play in hardy"
date: 2008-04-24
forum: Hardware
---

### Post by mephisto56 on 2008-04-24
I see they have worked to improve this aspect. You can determine the resolution in the screen resolution application. But still no plug and play. Before I plug off my laptop from my big screen on my desk I have to boot into ubuntu and manually tell it that next time I boot on the train I'll use my laptops display. If I forget to do this, I'll just get a blanc screen.

Or does anyone have a solution?

---

### Post by prshah on 2008-04-24
> **mephisto56 said:**
> Before I plug off my laptop from my big screen on my desk I have to boot into ubuntu and manually tell it that next time I boot on the train I'll use my laptops display. If I forget to do this, I'll just get a blanc screen.
Or does anyone have a solution?

Isn't there a key combo to cycle displays (on my laptop it's Fn+F10). Does that work out for you?

---

### Post by mephisto56 on 2008-04-25
Doesn't work for me. The stupid thing is I have to unplug my monitor from my laptop before I restart of boot up. Else I get a black login screen. So I have to unplug it, log in, plug monitor in, adjust resolutions and then I can use my plugged in monitor. Not really plug & play to me.

---

### Post by mephisto56 on 2008-04-26
Going to bump this once more because it's so annoying and would like to have a solution.
I've also noticed that when nvidia drivers are enabled the screen resolution tool doesn't list my 2nd monitor anymore.

Actually for me it's a step back from gutsy.

---

### Post by narnian99 on 2008-04-26
Have you tried "sudo dpkg-reconfigure xserver-xorg"?

There may be some crud in your old xorg.conf that you want to get rid of.

That allowed me to enable the TV output

---

### Post by mephisto56 on 2008-04-26
Thanks for the suggestion. Unfortunately it changes nothing. I've seen similar posts as mine so if more people have the same problems they might work on this.

---

### Post by siulca on 2008-04-27
I have the same problem, my external monitor is no longer detected (among other problems). 

Has anyone found a solution for this yet?

---

### Post by syarost on 2008-05-03
I have tried using the command "sudo displayconfig-gtk" to bring up the display tool. I can get video sent to the external monitor, but have been unable to get the resolution correct. Perhaps this will solve your problem.

When I messed up my video beyond repair, I used "sudo dpkg-reconfigure xserver-xorg" to regain the video on my laptop screen.

---

### Post by syarost on 2008-06-03
A work around to allow use of an external monitor if you have an NVIDIA video card is to load EnvyNG, then use the NVIDIA Settings tools that is loaded when you run EnvyNG.

---

