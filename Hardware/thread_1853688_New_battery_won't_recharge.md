---
title: "New battery won't recharge"
date: 2011-10-02
forum: Hardware
---

### Post by Flutter Finch on 2011-10-02
TIA for any help.

I had been getting an error message "Your battery may be broken" for months since installing Ubuntu.  Rightfully so, as it was somewhat older (5 or so years) and should probably be replaced.  I usually kept my laptop plugged in anyway, so a crapped out battery was never really an issue.

Cut to last week- My wonderful husband ordered me a new battery.  We put it in the HP-Pavilion dv2000 and left it turned off for the night.  I powered it up the next day, ran it using AC power for most of the morning, then unplugged to use battery power.  The battery was almost completely drained after a few hours (reasonable, I assume) and I plugged it back in.

Cut to now- The battery, even when plugged in, will not recharge.  Now when I unplug, my laptop shuts down immediately because the power is completely drained.  When I look at the status icon for my power, it says laptop battery is charged 100%.  But when I unplug, it says battery is discharging 0.0%

I'm at a loss.  Is it possible that the new battery isn't playing nicely with the machine and I have to rearrange some settings to get it to charge?  I am definitely a super-noob so use small words. :)

---

### Post by Redblade20XX on 2011-10-03
Is it an official battery or is it a third party battery? Sometimes people buy batteries from the internet for lower prices but they are usually low quality/poorly made ones.  Those batteries usually lose charge really quick and have an extremely limited amount of charge cycles.  Anyway back to your problem,

With the battery connected to the laptop, can you open a terminal and type in:

```
 sudo apt-get install acpi
```Press Y when it asks you to install and after it finishes installing type in the terminal:

```
acpi -b
```Please post this in your reply.

Also in the terminal, please type in:

```
acpi -i
```And also post this in your reply.

This will give us some information on your battery so that we can debug a bit. ;-)

- Red

---

### Post by Flutter Finch on 2011-10-03
Hmmm... This does not bode well.

sudo apt-get install acpi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acpi is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


 acpi -b
Battery 0: Unknown, 0%


acpi -i
Battery 0: Unknown, 0%
Battery 0: design capacity 4400 mAh, last full capacity 4529 mAh = 100%


But I definitely appreciate your quick reply to the orig post... I just got back and had an opportunity to do some more investigating.  I'll look forward to any additional directives. :)

---

### Post by mastablasta on 2011-10-04
what happens if you charge the battery when computer is shut down?
 
I have an old Compaq running 10.04 LTS and it seems something is wrong with Ubuntu batery monitor. It used to be workign fine when i installed the OS and then for over a year no issues. Now, though my baterry works as before. It also seems to never get fully charged or only sometimes this happens. However it lasts as long as before when it was new. one of the updates in Ubuntu made this change. i am sure of it.

---

### Post by Flutter Finch on 2011-10-04
Thanks for the suggestion... unfortunately, no dice.

---

### Post by Flutter Finch on 2011-10-04
Hey there... I have added the details per your instructions, but posted it as a separate reply as well.

---

### Post by BS_Kustomz on 2011-10-04
i had an issue similar to this with my compaq, try taking the battery out and reseating it while the laptop is still plugged in (i know i may get yelled at by people as to not take the battery out while it has power)
but this worked for me, wait for the icon to flash to the lightning bolt before reinserting the battery pack it then should flash back over to the fully charged battery icon then to the charging battery icon, try it a couple of time before giving up

---

### Post by Flutter Finch on 2011-10-05
Kustomz, that might have done it! I am not 100% sure but it DOES register as charging when I go to the status/info on the battery... Strange.

Either way, THANK YOU THANK YOU THANK YOU for sharing this trick! :)

To any other posters, I curious as to what insight you may have for the CAUSE of this.  It's still bewildering.

---

