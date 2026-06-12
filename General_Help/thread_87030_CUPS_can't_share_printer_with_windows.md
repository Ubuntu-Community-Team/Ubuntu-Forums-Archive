---
title: "CUPS can't share printer with windows"
date: 2005-11-07
forum: General Help
---

### Post by supermarchino on 2005-11-07
#1 breezy with working printer (Epson Stylus Color 760 named 'Stylus_Color_760') (10.0.0.1)

#2 dual boot breezy + winxp pro (10.0.0.10 for both OSs)

I've been able to make Epson printer on machine #1 CUPS server available for other pcs in my LAN, so that I can easily print from #2 breezy box with IPP; but #2 from winXP won't print. Althought I set in winXP network printer as 'http://10.0.0.1:631/printers/Stylus_Color_760', windows says can't find the printer... Tried with no firewall at all aswell.

---

### Post by giftnudel on 2005-11-07
Hi, 
I have had the same problem, too, however I could not solve it. Have you tried to access the printer as a different user with WinXP since that worked for me. Something must have been installed/set up with that user. Honestly, I was not able to track this problem down, I even stopped all services and so on, but no chance

giftnudel

---

### Post by Joe_lurker on 2005-11-07
You should watch the output of the cups error log as you send the job from the windows machine.  Run the command:
```
tail -f /var/log/cups/error_log
```
to monitor the log "live".  Use ctrl-c to exit the tail command.

Note any errors and post them here.

-Joe

---

### Post by Davor281 on 2005-11-08
Hi!

Maybe you should try -
"http://10.0.0.1:631/printers/Stylus Color 760"

in Win XP ???

ENjoY!

Davor.

---

