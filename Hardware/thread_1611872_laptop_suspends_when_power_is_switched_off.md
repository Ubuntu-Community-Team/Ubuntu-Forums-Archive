---
title: "laptop suspends when power is switched off"
date: 2010-11-02
forum: Hardware
---

### Post by pratikk on 2010-11-02
Hi, I'm running Lucid on a Compaq Presario V2000. Works great except that if the laptop is booted while on AC power and then the power is switched off, it suspends. Ubuntu's native power management is set never to put the machine to sleep. Jupiter 0.0.42 is also loaded, but it offers no sleep/suspend options, only those for controlling display and switching on/off peripherals. I'm not sure what's wrong. I hear that they work well together.

Thanks

Pratik

---

### Post by Quackers on 2010-11-02
That sounds like the battery may be faulty.

---

### Post by pratikk on 2010-11-02
> **Quackers said:**
> That sounds like the battery may be faulty.


Could be, but it looks like a power management issue. Unfortunately, I did the elementary elimination tests after posting. Booting on battery and then turning on AC power also suspends the machine, just like the reverse. Completely removing Jupiter did not help. And the machine runs fine for three hours on this battery. Also, this is a recent development which was not visible on the fresh install six weeks ago. 

I wonder if one can completely remove and then reinstall native power management?

---

### Post by wilee-nilee on 2010-11-02
Look in power settings.

Hit alt-f2 the type gconf-editor go to apps-gnome power manager-actions and see if something is amiss.

I'm going to take a wild guess here and say you probably changed something and don't remember or didn't know you were doing it.;)

---

### Post by pratikk on 2011-03-27
Wilee, sorry, just noticed your reply, so many months later. Your wild guess was spot on. The laptop's power options included responses to hibernate and suspend buttons, hardware which it does not have. I set those options to do 'nothing' and all's well. The funny part is that I'm sure I never edited those options. The default config includes them, but it doesn't cause problems on my other laptops. 

Thanks a lot.

> **wilee-nilee said:**
> Look in power settings.

Hit alt-f2 the type gconf-editor go to apps-gnome power manager-actions and see if something is amiss.

I'm going to take a wild guess here and say you probably changed something and don't remember or didn't know you were doing it.;)

Sorry, got to update that. The behaviour returned after four or five boots. No idea why.

---

