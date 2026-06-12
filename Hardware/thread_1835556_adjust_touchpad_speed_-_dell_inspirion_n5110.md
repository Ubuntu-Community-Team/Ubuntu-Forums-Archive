---
title: "adjust touchpad speed - dell inspirion n5110"
date: 2011-08-29
forum: Hardware
---

### Post by Darngood on 2011-08-29
Hello. I have a Dell Inspirion N5110 and I want to adjust the touchpad speed because it's too slow.

Changing settings under mouse preferences didn't help.
I have also installed gpointing-device-settings but it doesn't help me since the touchpad is seen as a mouse.

Thank you in advance,
Dan

uname -a output:
Linux InspironN5110 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ajgreeny on 2011-08-29
Try the command line ```
synclient -l
``` to list current settings and then you can change, partly by trial and error the setting you have at the moment.

I think the ones you need are MinSpeed, MaxSpeed and AccelFactor.

You change the settings with command such as ```
synclient MaxSpeed=1.75
```but it will be trial and error to get it right, I think.

---

### Post by Darngood on 2011-08-30
> **ajgreeny said:**
> Try the command line ```
synclient -l
``` to list current settings and then you can change, partly by trial and error the setting you have at the moment.

I think the ones you need are MinSpeed, MaxSpeed and AccelFactor.

You change the settings with command such as ```
synclient MaxSpeed=1.75
```but it will be trial and error to get it right, I think.

I get this message after trying the command:
```
synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
```
It was a bit expected since it's seen as a mouse, not a touchpad.

---

### Post by ajgreeny on 2011-08-30
In that case, I have no idea where you can go for any more help;  sorry.

---

### Post by tryten on 2011-09-11
I come with bad news. The new Alps touchpads in Dell computers have limited support for linux. It seems like the company (Alps) refuses to release information/drivers so that the problem can be fixed.
But some progression is being made anyway. Pray to God (or to Torvalds) and a solution may appear!
Further reading:
[http://pj.freefaculty.org/blog/alps-touchpad-linux-final-statement-now](http://pj.freefaculty.org/blog/alps-touchpad-linux-final-statement-now)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/678103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/678103)

Regards
/Simon

---

### Post by tryten on 2011-09-30
A fix is available är [http://people.canonical.com/~sforshee/alps-touchpad/]("http://people.canonical.com/%7Esforshee/alps-touchpad/"). 
Look for the latest psmouse-alps deb package and install. Restart your computer and you can then configure the touch pad.
For more info see the bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625).
I guess it will be implemented in a future kernel. 
Regards
/Simon
Ps. The Thread should be marked as solved. Ds.

---

### Post by quarara on 2011-10-23
Hi!
I've just installed Ubuntu on my Dell Inspiron 15r n5110.
Even though I've installed the psmouse deb suggested by tryten, my touchpad is not recognized as such.
Can you help me please?
Regards,
Luigi

---

### Post by quarara on 2011-10-24
Up.

---

### Post by quarara on 2011-10-26
Up? :(

---

### Post by broxen on 2011-11-21
This was EXACTLY what I was looking for. Thank you!

---

### Post by Vacross on 2011-12-17
> **tryten said:**
> A fix is available är [http://people.canonical.com/~sforshee/alps-touchpad/]("http://people.canonical.com/%7Esforshee/alps-touchpad/"). 
Look for the latest psmouse-alps deb package and install. Restart your computer and you can then configure the touch pad.
For more info see the bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625).
I guess it will be implemented in a future kernel. 
Regards
/Simon
Ps. The Thread should be marked as solved. Ds.

thanks so much, worked like magic!

---

