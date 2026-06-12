---
title: "Lubuntu Laptop - Suspend via terminal = no issue. Suspend via closed lit = issue"
date: 2019-12-08
forum: Hardware
---

### Post by crayoneater2 on 2019-12-08
Hardware: Compaq Presario M2000 (Service tag M2105US p/n: EC214UA#ABA)
(Manual: [https://data2.manualslib.com/pdf2/28/2733/273281-hp/compaq_presariopresario_m2000.pdf?36fcc7fca143f41296d4817c58f23449](https://data2.manualslib.com/pdf2/28/2733/273281-hp/compaq_presariopresario_m2000.pdf?36fcc7fca143f41296d4817c58f23449) )

Symptom:
```
[COLOR=#242729][FONT=Arial]sudo systemctl suspend[/FONT][/COLOR]
``` works as intended. System suspends (fans off / display off. Keystroke wakes system - login prompted)

Close lid - system suspends(?) Open Lid/Keystroke - Fans Spin, Display is back lit, but no image, and no known key prompts display text on screen.

Issue has only existed since changing from xubuntu to Lubuntu.

```

[LIST]
[*][COLOR=#333333]x@x:~$ lsusb[/COLOR]

[*][COLOR=#333333]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]

[*][COLOR=#333333]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

[*][COLOR=#333333]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]

[*][COLOR=#333333]x@x:~$ lsb_release -d[/COLOR]

[*][COLOR=#333333]Description:    Ubuntu 18.04.3 LTS[/COLOR]
[/LIST]

```

As always, thank you all for your help! Any and all suggestions/requests, just let me know!

 :mrgreen: <-Me...Green as Green can be when it comes to Linux!

---

### Post by gnusci on 2019-12-08
This post may help:

[https://ubuntuforums.org/showthread.php?t=2432626&p=13914343#post13914343](https://ubuntuforums.org/showthread.php?t=2432626&p=13914343#post13914343)

---

### Post by guiverc on 2019-12-08
What release of Lubuntu are you currently using?
What release of Xubuntu were you using?  (or did you just add `lubuntu-desktop` to your existing xubuntu system?; but which release?)
What kernel are you using (I can guess from release you didn't provide; though LTS releases could be using two kernels; normal or HWE)

---

### Post by crayoneater2 on 2019-12-08
[COLOR=#333333].[/COLOR]

---

### Post by crayoneater2 on 2019-12-08
> **guiverc said:**
> What release of Lubuntu are you currently using?
What release of Xubuntu were you using?  (or did you just add `lubuntu-desktop` to your existing xubuntu system?; but which release?)
What kernel are you using (I can guess from release you didn't provide; though LTS releases could be using two kernels; normal or HWE)
[COLOR=#000000]The latest Lubuntu - [/COLOR][COLOR=#333333]Description: Ubuntu 18.04.3 LTS (If there's a command to tell which release of Lubuntu is currently being used, do educate me what command that would be!)


As for xUbuntu - no clue - it was done by a college friend of mine.

Nada - I formatted the system and installed lubuntu 32x via boot CD

Tell me how to identify what kernel is being used and I'll gladly report on it!

Thanks for taking time to look into this![/COLOR]

---

### Post by him610 on 2019-12-09
Run this from a terminal then show the results between the code tags.
```

uname -a && lsb_release -a 

```

---

