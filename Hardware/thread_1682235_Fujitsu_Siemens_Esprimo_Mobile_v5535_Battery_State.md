---
title: "Fujitsu Siemens Esprimo Mobile v5535 Battery State"
date: 2011-02-05
forum: Hardware
---

### Post by Sneo on 2011-02-05
Hi all,

I'm currently on the latest version of Ubuntu [10.10] and I'm having issues with the GNOME power applet, basically it shows when its plugged and how long till charge however when the laptop isn't plugged into the AC adaptor I get no notification of how much battery is left, causing the computer to just shut down once it hits "critical" battery level.. Clicking the battery all I get told is "The battery is charged" and the battery icon itself still has the "charge" icon.. 

Any help would be really appreciated,

Cheers!

---

### Post by debiant on 2012-01-12
Was there ever a solution to this problem?  Just got one of these handed down having bought a new iPad for someone else :P

[http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29](http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29)

Re Page above-

   ```
 * sudo add-apt-repository ppa:iaz/battery-status && sudo apt-get update
    * sudo apt-get install battery-status
```


I then found and added the applet to the panel, however it says this command is needed for Ubuntu-

```
/usr/lib/battery-status/battery-status --indicator
```

This command doesn't seem to me to be complete-the terminal doesn't think so either and is sitting there waiting for the rest of it!

Any suggestions welcome.

:(

---

