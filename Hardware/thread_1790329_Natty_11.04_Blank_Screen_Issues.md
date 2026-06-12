---
title: "Natty 11.04 Blank Screen Issues"
date: 2011-06-24
forum: Hardware
---

### Post by kmajor on 2011-06-24
I upgraded to Natty and was immediately terrified when I got the black/blank screen at bootup. After countless hours scouring the web on another machine I finally used the 
```
setpci -s 00:02.0 F4.B=0
``` command that I found in a few forums.  Sweet, that worked but I needed it to that on boot, so I added that code to the bottom of my /etc/rc.local file, just above the exit 0 line.  
Nice, so now my laptop boots and I can see my monitor, life's good...... wait..... it's blank when it comes back from suspend, #%&*!!!!  More hours of research and no dice.  I give up, weeks go by, but today it's just driving me crazy and I'm realizing how much time it costs me to shut it down everytime I change locations.  So I spend another hour today and I finally came up with a solution.  Just run a script that runs the setpci command on wakeup... easy... yes yes it is.  
So.... just create a bash script like 
```

#!/bin/sh
setpci -s 00:02.0 F4.B=0

```and put it in /etc/pm/conf.d and like magic it should come back from suspend like a champ. 
Good luck....

---

