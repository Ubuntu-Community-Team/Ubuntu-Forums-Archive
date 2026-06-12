---
title: "battery discharging even in standby"
date: 2010-04-20
forum: Hardware
---

### Post by finite9 on 2010-04-20
Just bought a Thinkpad Edge Intel 13" and notice that the battery continues to discharge quite rapidly even when in standby mode.

Gnome Power Manager says 4hours, I put it in standby, leave it a few hours (cant remember how long) then open lid again log in and it says 2 hrs 15 min.

Anyone know what could cause this?

Im running 10.04 beta2 daily updates amd64

I get a message almost every time on boot saying thinkpad model not yet supported (tp_acpi).  Is this the reason?  That the ACPI is not supported on this laptop yet and everything to do with power management is screwed?

---

### Post by P4man on 2010-04-20
are you sure it actually goes in to sleep mode and its not just blanking the screen? Its normal that batteries discharge a bit in sleep mode (ram still needs to be powered) but not at that rate. It should last at least 24+hr in sleep mode.

Another thought is that your wifi radio is not powered down in sleep mode. Perhaps turn the radio off before suspending, see if that makes a difference?

---

### Post by finite9 on 2010-04-21
Yes it does go into standby: The Thinkpad light blinks on the outer casing to indicate this.

Thinkpad Edge doesn't have a physical kill switch but I read on lesswatts.org that you can basically do the same thing from the terminal using rf_kill, so 'll try that.

After I made this post yesterday, I realised that I have a BIOS feature for powering USB connected devices even when in standby/hibernation mode, and that this feature probably accounts for some of the battery drain during standby.  I disabled it in the BIOS but I was still seeing drain, but I could not quantify it and compare to what I saw earlier as I didn't have time.

I will try rf_kill tonight and see if I can standby for 2 hours without drain.

---

### Post by _0R10N on 2010-04-21
Feel the whole surface of your laptop, looking for any sign of overheating. That may indicate an electrical insulation problem causing the continous discharge of your battery.

If you want to run a simply test to prove whether the laptop is sleeping or not, leave a download in progress. When you wake up the laptop, you should notice some sign of connection loss.

Kind regards!

_0R10N >>

---

### Post by finite9 on 2010-04-26
uhh... I was wrong: the laptop does not go into standby when I close the lid despite having this set in the power manager preferences.  If I put the paltop in standby manually then it does not use battery during standby.  The laptop is supposed to beep when it goes into standby (and it does when  do it manually) but when I shut the lid: no beep, just blanks display.

I upgraded to the RC during the weekend and tested battery time and standby battery drainage and everything now seems fine: battery time according to power manager was very accurate and I got 4.5-5 hours out of it with light web surfing.

---

### Post by P4man on 2010-04-26
Good. And did they fix the lid/suspend button? If not, file a bug report (assuming you are certain you configured the actions  correctly for on ac power and on battery power)

---

### Post by orawax on 2012-03-06
> **finite9 said:**
> Just bought a Thinkpad Edge Intel 13" and notice that the battery continues to discharge quite rapidly even when in standby mode.

I have a similar problem with FS Lifebook P7120. Battery starts discharging as soon as it's fully loaded, while on AC power. It doesn't seem to discharge on suspend, though.

> **_0R10N said:**
> Feel the whole surface of your laptop, looking for any sign of overheating. That may indicate an electrical insulation problem causing the continous discharge of your battery.

This laptop is pretty hot on the bottom, but then again that may be quite normal for this model, since there's no ventilation. The problem has existed since I got this, so there's nothing I could compare to.

How would one determine whether this really is the case and how to locate the problem more precisely? Or is it even possible to fix this with reasonable effort?

---

