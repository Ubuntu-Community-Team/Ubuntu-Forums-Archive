---
title: "Brightness"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by rhgilman on 2007-11-14
Ubuntu Gutsy on a Lenovo X61s. Everything works pretty well except that on battery power the screen dims to the lowest level after one minute of inactivity and does not return when activity resumes. The same thing on AC power except that the screen goes to maximum brightness. A minor but problem but distracting.

1. Display Brightness is set to High in BIOS
2. Power management preferences are the same for battery and AC, namely Computer Sleep-Never, Display Sleep -Never, Brightness 100%, and Dim Display When Idle unchecked. 
3. The automatic brightness adjustments do not produce any entries in the acpid log.

Who is dimming my screen? Can I adjust the amount of dimming or the time until dimming occurs? Failing that can I just turn this feature off?

---

### Post by rhgilman on 2007-11-15
One more item. On battery power the brightness applet sets the screen to minimum brightness no matter where the slider is. On AC power the applet works fine.

---

### Post by Chriswaterguy on 2007-11-15
I'm also getting brightness control problems, on my Lenovo Thinkpad R60. 

When I plug in to AC, brightness goes to full, which is usually too bright  - I dim it, but it keeps resetting itself at seemingly random times. When I switch to battery, it goes *very* dim. 

I've now changed my power management settings to 90% brightness for both, so it should be better - but is there a way I can entirely turn off the power management's control over brightness? If I'm using it in a brighter or dimmer environment, I want to set the brightness myself and not have the random gremlin reset it.

----
EDIT: Nothing changed till I rebooted. Now I have partial success. It's staying at 90% while plugged in (less glare = good) but dropping even lower when unplugged (10% of the brightness bar, though clearly more than 10% of actual brightness). 

I now see the reason - the counter-intuitive settings dialog for power management has "Dim display brightness by:" under the battery setting - so the control looks the same as the AC setting, but it has a completely different meaning. That needs redesigning. I'd still like to just disable this.

---

### Post by addicted1 on 2007-11-16
This problem is  there with all laptops. I have a HCL laptop, when it is connected to AC, I decrease the brightness and increse the brightness when its not. If there is any other solution then please let me know.

---

### Post by rhgilman on 2007-11-18
> **Chriswaterguy said:**
> I'm also getting brightness control problems, on my Lenovo Thinkpad R60. 

....

I now see the reason - the counter-intuitive settings dialog for power management has "Dim display brightness by:" under the battery setting - so the control looks the same as the AC setting, but it has a completely different meaning. That needs redesigning. I'd still like to just disable this.

Thanks for the tip. I adjusted  "Dim display brightness" to 20%, and everything seems fine.

---

### Post by trjonescp on 2008-01-22
I want Ubuntu to manage the screen brightness for me, but I would like to adjust the time until the laptop becomes "idle". Right now it dims after just 20 seconds or so. I would like to increase that to like 3 minutes.

---

