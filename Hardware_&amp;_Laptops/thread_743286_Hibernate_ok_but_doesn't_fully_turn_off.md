---
title: "Hibernate ok but doesn't fully turn off"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by sistoviejo on 2008-04-02
I installed 8.04 Beta and hibernate and suspend work correctly! :)
The only problem is that the computer doesn't switch off after it has finished hibernating. I have to manually switch it off after it stops using the hard drive.
I know it hibernates OK because I can see all my open tasks after rebooting. The only thing that it doesn't do is switching off after it's done hibernating.

It does switch off correctly when I use "Shut down". The computer is an HP Laptop tx1215nr (tx1000 series).
Please don't suggest to go back to 7.10. Hibernate didn't work with it. Many other things didn't also work. I'm very happy with Hardy :)

---

### Post by sistoviejo on 2008-04-04
Bump! Anyone?

PS: Here's my bug report for this issue: [https://bugs.launchpad.net/ubuntu/+bug/211011](https://bugs.launchpad.net/ubuntu/+bug/211011)

---

### Post by antonkuijsten on 2008-04-28
I have exactly the same problem. bump!

---

### Post by sistoviejo on 2008-04-28
> **antonkuijsten said:**
> I have exactly the same problem. bump!

Please post your laptop's specs and model so people know them.

---

### Post by PenKnife on 2008-04-29
I have an ACER aspire 4710z, I set it to hibernate, the power light and the other indicator flash orange like they should, but I can still hear the HD spinning and thge fan running. Also, the power light continues to flash orange when the machine is re-opened.

---

### Post by sistoviejo on 2008-04-29
> **PenKnife said:**
> I have an ACER aspire 4710z, I set it to hibernate, the power light and the other indicator flash orange like they should, but I can still hear the HD spinning and thge fan running. Also, the power light continues to flash orange when the machine is re-opened.

That is the exact same problem I have.
I wonder why shutdown successfully turns off the computer but hibernate doesn't. :confused:

---

### Post by triathman on 2008-05-17
Same problem here, my machine is a Dell precision 690

Thanks

---

### Post by aquammles22f on 2008-05-19
Same problem here... HP s3100n

---

### Post by jefi on 2008-06-03
same problem for me :

Dell XPS M1710

---

### Post by drem on 2008-06-08
Sorry, but I'm not using Ubuntu right now, so I might not be very accurate.

1.try to install uswsusp (an 
```
sudo apt-get install uswsusp
```
should do it)

2.edit the file /etc/uswsups.conf
```
sudo gedit /etc/uswsusp.conf
```
and change the line (I think it's the last one):
```
shutdown method = platform
```
to
```
shutdown method = shutdown
```

try to suspend using
```
sudo s2disk
```

if it works, you might be able to link this to your normal suspend button following this guide (but I do not guarantee it works...):
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

---

### Post by kgen on 2008-06-11
Well, I had the same issue on my asus laptop running Ubuntu 8.04 when hibernating. For the fix was as follows...

* Edit the /etc/default/acpi-support (required root privilege).

* Change the value for HIBERNATE_MODE as
```
HIBERNATE_MODE=platform
```

* Save the file and retry hibernating.

Well, the only other thing I did was crossing my finger... (Just in case that's the real secret ;))

---

