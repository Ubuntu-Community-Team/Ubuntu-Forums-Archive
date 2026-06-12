---
title: "Unable to suspend on laptop lid close"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by fatejudger on 2007-06-11
I recently upgraded from Kubuntu Edgy to Ubuntu Feisty on my Inspiron 1100 and have had some issues with power management. For some reason, my laptop refuses to do much of anything when I close my lid or press my power button, even though I have both set to suspend. Manually suspending the machine through appears to work just fine. Any input would be appriciated.

---

### Post by superatrain on 2007-10-12
There are a few bugs with Ubuntu and the Inspiron 1100. I have experienced this myself, but until seeing this, I thought it was an isolated issue. Hopefully what I am posting will help out some inspiron owners...

I have confirmed that my lid switch is responding properly by trying the following: ```
sleep 2 && cat /proc/acpi/button/LID/state
``` That is the specific location acpi uses to confirm lid state by default. That script waits 2 seconds, then outputs the state of the lid, so run it while the laptop is open, and then run it and quickly close the lid, and makes sure it responds "open" and "closed" Also, make sure you have the right drivers for Xorg. (i810, not vesa.)

In my case, acpid was running, but it did not seem to respond to the event. I have not tried the power button though. My quick dirty fix for this is to make my own acpi event watcher. It doesn't respond to events directly, it just keeps checking the /proc file. Acpi should be fixed properly rather than using cheap scripts, but here is a temp. hack for now.

```
#!/bin/bash
while [1 = 1]; ## endless loop
do
cat /proc/acpi/button/LID/state | grep closed
if [ $? = 0 ]; then
xset dpms force off
fi
sleep 0.5 # to make it nicer on the cpu
done
```

replace the xset line with whatever command you want to run, and stick this somewhere where it will get started on boot. Also, if you like how the acpi defaults have set it up, you can alter it to just call lid.sh, which has its own lid state check built in. I did not show this as the default, because I do not know how efficient the lid.sh script is, and it might be less aggressive to use my method. Use any method you like.

```
#!/bin/bash
while [1 = 1];
do
/etc/acpi/lid.sh
sleep 0.5
done
```

Also, I've noticed if the lid is shut while booting, the screen, which turned off with dpms properly, never turns back on. (I think "vbetool dpms on" stuck in a startup script should help) Has anyone else experienced this?

NB: As I didn't have my laptop on me when I wrote this, there may be inaccuracies. I plan to go over this code when I get home and confirm.

If you have a inspiron 1100 that works correctly in these situations, I would also like to know.

---

