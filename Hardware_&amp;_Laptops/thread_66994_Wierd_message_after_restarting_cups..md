---
title: "Wierd message after restarting cups."
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by Plank117 on 2005-09-19
I am trying to get my Lexmark z25 to work, but when I run 
```
/etc/rc2.d/S19cupsys restart
```
 I get the following message: 
```
cupsd: Child exited with status 13!
```
What does this mean? I was using this tutorial: [http://ubuntuforums.org/showthread....&highlight=z600](http://ubuntuforums.org/showthread....&highlight=z600)
Also, when I go to install a printer in gnome (under System->Admnistration), I cannot find the z600 in the wizard's list of lexmark printers, as in is described in the tutorial. Are these two things related, or should I switch to fedora? (god forbid...)

---

### Post by Xian on 2005-09-19
I'm not familiar with that particular service but any restart commands need to be done with admin priviledges.

# sudo /etc/rc2.d/S19cupsys restart

---

### Post by Plank117 on 2005-09-19
I did in fact sudo it when I tried it the first time, I'm just bewildered as to what that message means.

---

### Post by Xian on 2005-09-19
Listed below is my output.
Are you sure that sudo is working on your system?

```
$ sudo /etc/rc2.d/S19cupsys restart
 * Restarting Common Unix Printing System: cupsd
```

---

### Post by Plank117 on 2005-09-19
Okay, I tried it again. It works now, it sees the printer, but the printer is behaving strangely. When I try to print a test page, it moves the head maybe 3 inches, stops for about a minute and does the same thing. I'm using the z600 driver, which purportedly works on most lexmark inkjet printers.

---

