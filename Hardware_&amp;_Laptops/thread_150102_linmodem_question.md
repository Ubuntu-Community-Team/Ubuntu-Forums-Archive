---
title: "linmodem question"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by Raoul Duke on 2006-03-25
I finally  got my (ugh) linmodem working after my pcmcia modem broke...however...

With the old modem I was able to program it to report the connection (modem to modem) speed rather than the DTE speed upon connection. This is important where I live (Ecuador) due to flaky phone lines especially when it rains. If the connection was flaky (as indicated by modem speed) I knew not to undertake certain things such as downloading  or Skype. However my Linmodem does not support the same AT commands that I used to use to do this (don't remember them offhand). So the question is this...Does anyone know how to do this? Or where I can look for the AT command set for my linmodem?

My computer is Toshiba Satellite 2450
Modem Chipset is: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97

Any help will be apreciated

---

### Post by towsonu2003 on 2006-04-14
After 2 weeks of no answer, I'll assume this is not known? I use conky to monitor my modem speed (refresh speed per 3 seconds, give graphic). I am not sure if this would work. Tips and Tricks has a post for conky. Once you take a look at that, here is the part I use (for .conkyrc, the configuration file of conky) to monitor modem speed:
```

$color$stippled_hr
${color lightgrey}Networking:
${color lightgrey}$color PPP0:  ${color lightgrey} downloaded $color ${totaldown ppp0}${color lightgrey}; uploaded $color ${totalup ppp0}
$color$stippled_hr

```

---

