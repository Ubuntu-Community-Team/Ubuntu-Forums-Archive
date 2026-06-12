---
title: "Some Cairo-dock applets not working"
date: 2008-11-13
forum: General Help
---

### Post by s3kt0r on 2008-11-13
Hey everyone, been having a problem with Cairo-dock version 1.6.2.3 and some of its applets. 
The power manager applet doesn't refresh in the time gap specified (5 secs, in my case), I have to open the cairo-config or the applet-config dialog and close it again, for it to display the correct charge the battery has. 
Also, the systray applet, behaves strangely (besides not looking the best way it could be); When I click it once to view what's on systray, I can't make it go away with another click, as it should be. I have to restart cairo-dock.
Tried searching using google and forums, but it seems no one has reported this. Anybody is having the same problem, or knows of any tips to get this working ?
It's not like there isn't an alternative option to check the battery charge and system tray, but would like to get rid of the last panel I have.

Thanks in advance,

---

### Post by fabounet on 2008-11-14
middle click to make the systray dialog disappear, or you can also detach it from the dock.
for powermanager, could you please tell me what happens in the console with "cairo-dock -l debug" (just the part concerning the battery, on more than 5 seconds)

---

### Post by s3kt0r on 2008-11-14
fabounet, thanks for trying to help. I hope this is what you needed to see:


It showed

```

PowerManager : On Battery:1 ; iCapacity:4752mWh ; iRemainingCapacity:1331mWh ; iPresentRate:0mW ; iPresentVoltage:10800mV

```

like 5 or 6 times, and then switched to

```

PowerManager : On Battery:1 ; iCapacity:4752mWh ; iRemainingCapacity:1284mWh ; iPresentRate:0mW ; iPresentVoltage:10800mV

```

and as before, repeated the same 5 or 6 times, can't be sure about how many.

Is the update_icon part also important? 

Sorry for late response, wasn't online all day.

---

