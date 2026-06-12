---
title: "Adding Scripts to Laptop-Mode?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by davebed on 2006-11-02
Can anyone tell me how to add the command
**aticonfig --set-powerstate 1**
to my Laptop-mode configuration?

I have it set that laptop-mode kicks in when running on battery, but I want the ATI x1400 card to switch to low powerstate automatically.

Currently I have to run the command manually.

Any thoughts?

Thanks!

---

### Post by ShinjiLeery on 2006-11-02
write the line in the System --> Sessions if you have Gnome

With KDE i don't know ;)

---

### Post by davebed on 2006-11-02
> **ShinjiLeery said:**
> write the line in the System --> Sessions if you have Gnome

With KDE i don't know ;)

But I only want the command to run when laptop-mode runs - ie. not on AC Power, only on battery....

Adding the line where you suggest would enable it at bootup every time, if i'm not mistaken. 

Thanks anyways.

---

### Post by Seq on 2006-11-02
Have a look in /etc/laptop-mode/

I'm not sure what if the power states are correct as I do not have an ati graphics card...

```
echo -e '#!/bin/bash\n\naticonfig --set-powerstate 1' > /etc/laptop-mode/batt-start/ati-powersave-start
echo -e '#!/bin/bash\n\naticonfig --set-powerstate 0' > /etc/laptop-mode/batt-stop/ati-powersave-stop
chmod +x /etc/laptop-mode/batt-start/ati-powersave-start /etc/laptop-mode/batt-stop/ati-powersave-stop
```

---

### Post by zasf on 2006-11-03
> **davebed said:**
> But I only want the command to run when laptop-mode runs - ie. not on AC Power, only on battery....

Adding the line where you suggest would enable it at bootup every time, if i'm not mistaken. 

Thanks anyways.

I put scripts in /etc/acpi/ac.d/ or /etc/acpi/battery.d/ and it works fine

---

### Post by davebed on 2006-11-04
Thank you Seq for the code. Forgive me, but I'm *very* new to Linux.
Could you please tell me how to make use of this code - i've tried adding it to the end of my laptop-mode.conf file, but that didn't work...

Thanks

---

### Post by Seq on 2006-11-05
> **davebed said:**
> Thank you Seq for the code. Forgive me, but I'm *very* new to Linux.
Could you please tell me how to make use of this code - i've tried adding it to the end of my laptop-mode.conf file, but that didn't work...

Thanks

Nope, just run it in the terminal:

Applications > Accessories > Terminal

Although you may wish to change the file paths to the ones zasf provided.

---

### Post by davebed on 2006-11-05
> **zasf said:**
> I put scripts in /etc/acpi/ac.d/ or /etc/acpi/battery.d/ and it works fine

I now have a script in both of the abovementioned locations. The scripts function when manually excecuted, but do not automatically run when the power is removed/restored.

Have I missed a step?

Thank you for you help.

---

### Post by GStubbs43 on 2006-11-05
Try making a text file with ```
aticonfig --set-powerstate 1
``` in it and save it as script.sh in the /etc/acpi/battery.d/ That should set it to run the script when it is on battery power. /etc/acpi/ac.d/ runs scripts on AC.

---

### Post by davebed on 2006-11-05
> **GStubbs43 said:**
> Try making a text file with ```
aticonfig --set-powerstate 1
``` in it and save it as script.sh in the /etc/acpi/battery.d/ That should set it to run the script when it is on battery power. /etc/acpi/ac.d/ runs scripts on AC.

Thank you GStubbs43 and thank you all for your input.

I beleive there must be some sort of problem, as if my /etc/acpi/ac.d and battery.d are not being called at the appropriate times. Like i said above, whether i follow the above quoted format for my files or those mentioned earlier, neither effects the desired effect automatically - though they do work when manually executed. 

What could it be that prevents the contents of /etc/acpi/ac.d and battery.d from being called?

Thanks again all.

---

### Post by pvegdahl on 2006-11-07
> **davebed said:**
> What could it be that prevents the contents of /etc/acpi/ac.d and battery.d from being called?

I am having the same problem, but it isn't an issue of the scripts not being called, it seems to be a permissions issue.

I modified the line to dump output to a file:

```
aticonfig --set-powerstate=1 &> /home/username/AtiDebug.txt
```

I get the following in that file:

Error: Unable to open display `'.

I'm not sure how to fix that yet, but I will let you know if/when I solve that problem.

---

### Post by pvegdahl on 2006-11-08
Okay, I figured it out. You need to tell the script which display you're dealing with. The following works for me.

```
DISPLAY=:0 /usr/bin/aticonfig --set-powerstate=1
```

Does that work for you?

---

### Post by davebed on 2006-11-09
Well, I've figured it out, for my situation anyhow. It seems that I still had the Mesa drivers installed for my ATI x1400 card and that was causing hibernation and other ACPI trouble, including *this*.

Many thanks to you _all_ for your help - I've used some of what each of you have written and it now works as it should :)

---

