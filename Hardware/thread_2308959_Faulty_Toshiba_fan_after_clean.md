---
title: "Faulty Toshiba fan after clean"
date: 2016-01-06
forum: Hardware
---

### Post by ThanasisKant on 2016-01-06
[COLOR=#111111][FONT=Ubuntu]Today my friend brought me the laptop of his dad for dust clean and format.(installed Lubuntu 15). 
The laptop was a Toshiba Satellite L300-2C4 2Gb ram and Pentium Dual-Core T4200 at 2.00 GHz!
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After the cleaning i assembly it and push the power key to start! All good BUT the fan **starts**spinning and **stop** after 10 sec! I change ram slot ( one 2 gb dimm),now the fan **spins**, but i have**no screen signal**. Completly black! Change again, i have screen but, fan stop after 10 sec.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I clean-install ubuntu 14.04 thinking it might be a software problem but the same exaclty problem.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any help guys? Any suggestion? What i must do?

PLUS
1)Also something i found out. If i open it and the fan does not start at first boot, after i restart the fan starts... 
2)Also at first boot, if i go to bios reset to defaults save and exit, the fan starts operating ... Could it be a bios mulfuction[/FONT][/COLOR]

---

### Post by weatherman2 on 2016-01-06
If the fan spins at all when you first turn it on, I suspect it is working normally.

Believe it or not, the CPU fan may not spin constantly when the heat sink is clean.  The T4200 is not a hot CPU.  The fan should come on only when it needs to to cool the CPU, and the CPU will get warmer when it is doing heavy tasks.

Try putting the CPU under load.  Boot up Lubuntu, open Firefox and watch something on YouTube for a few minutes - that should do it.  See if the fan spins then.

If the heat sink was dirty before you cleaned it, the fan may have been on constantly because it was not able to cool effectively.  It's amazing how much cooler a laptop can run after you clean it out!

---

### Post by sammiev on 2016-01-06
My Toshiba laptop has been running over 5 mins now and the fan has yet to start.

It does spin on startup before any OS starts.

---

### Post by ThanasisKant on 2016-01-06
Oh i see i will check it out then.
 Also if what you say is true( which i hope :D) why after the restart the fan starts spinning from the beginning non-stop?

---

### Post by sammiev on 2016-01-06
I have a L650 and these are are normals for this unit.

I can here my fan start somewhere between 52c and 55c.

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +50.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +52.0°C  (high = +95.0°C, crit = +105.0°C)

---

### Post by ThanasisKant on 2016-01-06
Guys i just opened 5 streaming tabs so the temp can rise.It went up to 80 degrees celcius BUT  the fan didnt start. I got scared and i restarted it and the fan started. 

Is there a way to make it manual start? use parameters like the fan start at 20 celcius, so it can start from the beggining? I am going to die cause the laptop is not mine and it's my friends dad. HELP! :p

---

### Post by sammiev on 2016-01-06
It really sounds like you have issues.

Have you checked for a firmware update for the BIOS?

Edit: Is the battery still good on the cmos?

---

### Post by ThanasisKant on 2016-01-06
I will install windows xp... and make the updates. Yes the battery is still good its still soldered

---

### Post by weatherman2 on 2016-01-06
Unless you are installing it only to update your BIOS, Windows XP is a terrible choice - it is insecure as Microsoft stopped supporting it a few years ago.  Many web browsers are already no longer supported in XP.  Using XP on the web especially is inviting malware infections.

Your initial post suggested that cleaning the laptop fan had caused a problem, but to be clear it seems to be an inconsistency in how the fan is supported in Ubuntu.  Fan issues in Ubuntu are fairly common with laptops.  I suggest doing some web research and look for possible solutions to control the fan consistently at each boot and restart.  Yes, a BIOS update, if one is available from Toshiba, might be a good place to start.

---

