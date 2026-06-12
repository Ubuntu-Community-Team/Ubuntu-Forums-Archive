---
title: "PC randomly reboots during graphic intensive usage"
date: 2011-11-14
forum: Hardware
---

### Post by fleggle on 2011-11-14
Hi, for sometime now my computer suddenly shuts down and reboots itself, without warning. There is no consistency to when this happens. Sometimes the computer will be on for 9 hours, sometimes for less then an hour.
Also as far as I can tell it isn't an issue with the OS as it occurs both in ubuntu and windows 7. 
The biggest culprits appear to be flash related content and heavy gaming (although the former seems to be a greater issue)>
I have no idea where to begin in diagnosing and hopefully solving the issue, so any help would be greatly appreciated. 

NB: the temperature for all components are at about the 30-50 range so well within healthy regions

---

### Post by northd_tech on 2011-11-14
> **fleggle said:**
> 
NB: the temperature for all components are at about the 30-50 range so well within healthy regions

I'd make sure you've got **lm-sensors** and **sensors-applet** packages (and/or Conky) installed and set up conveniently to keep a close eye on that temperature anyway (and the **sensors** and **sensors -f **commands are your friends at the terminal or outside the X environment).

If you're sure the temperature is within the 'normal' range, then I would IMMEDIATELY start to suspect your power supply is dropping the voltage to your CPU and/or GPU (that's actually how the old "RESET" button worked on the ancient 8088 XT and 80286 AT PC's back in the 80's if anyone else remembers those).

What you are describing is just what it was like to have a 0.5-2 year old nephew crawling/toddling around on the floor with one of those [COLOR=Red]**big bright RED "RESET"**[/COLOR] buttons on the front of your computer case- in fact, I often disconnected that button from the motherboard for that reason back in the ole' 'hand crank PC' days. ;)

Edit:  You probably also want to check in your BIOS to see if those voltage, temp, etc. settings might be causing you to reboot, suspend, shutdown, etc.  Anything to do with voltage, ACPI, temperature, fans, Power Management, etc. is suspect IMHO.

---

