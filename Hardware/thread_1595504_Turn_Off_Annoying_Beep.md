---
title: "Turn Off Annoying Beep?"
date: 2010-10-13
forum: Hardware
---

### Post by csharpplus on 2010-10-13
How can I turn off the annoying system beep that comes up every few minutes? It drives me crazy.
 
I tried to edit:   gedit /etc/modprobe.d/blacklist
 
by adding the lines:
 
#silly speaker beep
blacklist pcspkr
 
and then restarting. It did not help. How can I fix this? (I am using Ubuntu 10.04)

---

### Post by CharlesA on 2010-10-13
You'd have to be more specific as to which beep you are talking about.

I've not run into that sort of thing on my Lucid install.

---

### Post by csharpplus on 2010-10-13
I did not either (on my other machine), but on this one, I did. It beeps informing of 'battery discharging' etc.
 
How can I turn off all beep, whatever the reason is?

---

### Post by CharlesA on 2010-10-13
Check the sound applet. I doubt it's the "pc speaker" making the beep.

---

### Post by csharpplus on 2010-10-13
I think I found the problem, and also the solution:
 
[http://ubuntuforums.org/showthread.php?t=457501](http://ubuntuforums.org/showthread.php?t=457501)
 
However, I do not understand what exactly I should do to solve this. Can any of the expert guys take a look and 'translate' the solution?
 
thanks so much!

---

### Post by csharpplus on 2010-10-13
Anybody?

---

### Post by CharlesA on 2010-10-13
I don't think Ubuntu uses HAL now, but I could be wrong. So it happens when it's on battery, or when it's plugged in?

---

### Post by csharpplus on 2010-10-13
When it's plugged in, every once in a while a message shows up: 'discharging bettery' and 3-4 annoying beeps follow. it happens say every 5-10min.

---

### Post by CharlesA on 2010-10-13
Is the battery already fully charged?

---

### Post by csharpplus on 2010-10-13
yes. I referred to a link I found describing the same problem. the guys there suggested a solution yet I am not fluent enough to understand what I shall do.
 
Any chance you can look at it and suggest how to solve it?  alternatively, any other ideas?
 
thank you for your time & help.

---

### Post by CharlesA on 2010-10-14
It might help to file a bug report on launchpad. That other thread is from 2007 and there have been quite a few releases since then.

---

### Post by csharpplus on 2010-10-14
How do I do that?

---

### Post by CharlesA on 2010-10-14
> **csharpplus said:**
> How do I do that?

Check [here]("https://help.ubuntu.com/community/ReportingBugs").

---

