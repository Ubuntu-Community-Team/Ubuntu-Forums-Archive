---
title: "I need help with my Wifi Card!!!"
date: 2008-08-06
forum: General Help
---

### Post by sendblink23 on 2008-08-06
It seems not to work even if I do use the "ndiswrapper"

heres a print screen:
[IMG]http://i29.photobucket.com/albums/c272/sendblink23/Screenshot.png[/IMG]

As you can see It does show my Driver is *PRESENT, so whats wrong it doesn't show up in my *Network to be able to access wireless connection ???

---

### Post by phidia on 2008-08-06
What happens when you click "Configure Network"?

---

### Post by sendblink23 on 2008-08-06
> **phidia said:**
> What happens when you click "Configure Network"?

THAT'S WHAT IT SHOWS WHEN YOU CLICK IT :P, thast why I "print Screened to show my Problem"

---

### Post by sendblink23 on 2008-08-06
can anybody help me out?

---

### Post by phidia on 2008-08-06
> **sendblink23 said:**
> THAT'S WHAT IT SHOWS WHEN YOU CLICK IT :P, thast why I "print Screened to show my Problem"

We are all trying to help one another here. I'm sorry this is frustrating and you did not specify what steps you took. 

You know what you have done but if you don't explain it clearly no one else will know.  And "shouting" in caps may get you attention but it may not be what you need.

There are Ubuntu wifi troubleshooting guides [here]("https://help.ubuntu.com/community/TroubleShootingGuide").
You can also open a terminal and enter "iwconfig" "lshw -C network" & "sudo mdiswrapper -l" to see more of what's going on.

---

### Post by Crafty Kisses on 2008-08-06
Post the following output of:
```
iwconfig
```

---

