---
title: "Disabling touchpad when mouse is connected."
date: 2009-04-21
forum: Hardware
---

### Post by Diablosblizz on 2009-04-21
Hey, being a Linux newbie (but so happy to try it, perhaps leaving Windows in the dust). I am using a Toshiba laptop, and I constantly hit my touchpad when I am typing, causing it to either click off or scroll down. I always use a mouse with my laptop, a Microsoft 3000 series mouse (it was cheap) and I was wondering if I could disable the touchpad once the mouse is connected.

I have searched for this, and it results in stuff I don't understand. Something about putting a code somewhere. I'm a Windows nerd, so I do understand basic understanding of how this might work. The middle button also isn't functioning.

Does anybody have a tutorial that I could perhaps read from? Thank you very much!

---

### Post by xMarine73 on 2009-05-14
I've got a script that I wrote for this very problem.  It will require a single small change by you for your particular mouse but it works like a charm.  The change is documented in the script.

Basically what the script does, is polls the system every couple seconds to see if the state of the mouse has changed - either plugged in or unplugged.  When plugged in, the touchpad is disabled.  When unplugged, the touchpad is re-enabled.

The file should be attached.  Make it executable, add it to your list of apps to run at start-up, and you're good to go.

---

