---
title: "Compiz Problem in 8.10"
date: 2008-12-02
forum: General Help
---

### Post by dashingbadal on 2008-12-02
Sir 

I have intalled ubuntu 8.04 and compiz was working perfectly fine. After that I upgraded to 8.10 using update manager. But to my surprise compiz is not working now.

Please help me out.

My system configuration is :-
Pentium IV
512 MB ram

I don't have a graphic card.

---

### Post by wilbbe01 on 2008-12-02
You have to have a graphics card or you wouldn't have compiz working in the first place as you wouldn't be able to power anything.  You probably meant your graphics card is the one onboard (some shared memory thing attached to the motherboard).

Try going to System --> Hardware Drivers.

If you see something relating to graphics there try clicking it to activate it.  If it is already activated, try removing the check box or whatever is used, and reactivate it.

---

### Post by wilbbe01 on 2008-12-02
duplicate, stupid slow internet :(

---

### Post by cdtech on 2008-12-02
Mine didn't work after the upgrade. I had to use the "Compiz Fusion Icon" located under "other" (yours may differ). You may even need to install it.

---

### Post by prshah on 2008-12-02
> **dashingbadal said:**
> 
I have intalled ubuntu 8.04 and compiz was working perfectly fine. After that I upgraded to 8.10 using update manager. But to my surprise compiz is not working now.

If you have installed any custom extensions and configurations, (temporarily) remove them; open a terminal (Applications-Accessories-Terminal) and give the command```
cd
cp -p .compiz compiz_old && rm -rf .compiz
```

WARNING: Be _very careful_ with the second command. You can inadvertently wipe out your entire home directory (for example, if you put in a space inbetween the "." and "compiz"- DON'T DO THIS.). You perform this at entirely your own risk. 

Then, try running compiz from the terminal ```
compiz --replace
``` If it works, fine, otherwise paste back any output that you get from this command in the terminal.

---

### Post by Forlong on 2008-12-02
Your chip may be blacklisted on Intrepid, try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

