---
title: "Weird biping after wakup from suspend"
date: 2008-05-18
forum: Hardware
---

### Post by brujoand on 2008-05-18
My system beeps for 3 to 4 seconds after waking up from suspend, seems to happen even if the sound is of, so I suspect its a system sound. It happens about 50% of the time. Really weird, but only happened after a clean install of 8.04, never before. Anyone seen this elsewere, or have a clue on how to fix? 

tnx

---

### Post by jcro001 on 2008-05-18
I get the same beeping sound. This only happens when the laptop fails to sleep. In bottom left corner I get an error message saying "Your laptop failed to sleep"

---

### Post by brujoand on 2008-05-18
Yeah, same thing with me, I forgot about the sleep failing, since i disabled the fail message. But it's kind of weird, since the sleep obviously succeeded,(the laptop was stone cold). 
So it definitely an error message beep thing then.

---

### Post by brujoand on 2008-05-19
Nobody knows anything about this?

---

### Post by brujoand on 2008-05-21
Last bump, please help. The biiping is killing me!

---

### Post by szf on 2008-05-21
Go to System -> Preferences -> Power Management 

Select tab 'General'

On Hardy the last option is 'Extras' -> 'Use sound to notify on event of error'

Unselect it

---

### Post by brujoand on 2008-05-21
Ahh.. tnx, a great hack :)

Works 4 me

---

### Post by brujoand on 2008-05-23
Holy crap, That didnt work either!

---

### Post by elysianfields44 on 2009-05-28
Well this is about 1 year late but in case anyone still checks this thread.

The system sound is due to an error during suspend. Here's a fix that worked for me.

Try the following:

sudo vi /etc/default/acpi-support

Change this line:

STOP_SERVICES=""

To:

STOP_SERVICES="networking"

Save and exit the file.

This makes sure that the networking services (e.g. wireless connection) are properly stopped before suspend and restarted after resume. This fixed the beeping problem on my laptop, and incidentally also makes the wireless re-connect automatically (which I previously had to manually re-connect). Hope that helps.

---

