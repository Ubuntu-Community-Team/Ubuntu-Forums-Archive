---
title: "Using s2disk on Battery Critical Level"
date: 2011-10-17
forum: Hardware
---

### Post by tony1grendel on 2011-10-17
[SIZE=2]Hey, guys

I am using Ubuntu 10.04 and have had hibernate problems for a while on my [/SIZE] [SIZE=2]
Dell Latitude D620
[B]
I installed uswsusp and tested out s2disk from the command line and it worked!
I edited some config files and now [/B][/SIZE][SIZE=2]**when I select Hibernate from the menu**[/SIZE]** it works**
[SIZE=2]**but I can't get it to use s2disk when the battery is critically low**[/SIZE]

[SIZE=2]Here's a summary of the files I edited and in their order

I edited the file /etc/pm/config.d/*00_sleep_module*[/SIZE]
[SIZE=2] and added the line:[/SIZE]

[SIZE=2]SLEEP_MODULE="uswsusp"

I backed up hal-system-power-hibernate-linux[/SIZE]  [SIZE=2]

mv /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux   [/SIZE] [SIZE=2]
    /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak

and crated a new hal-system-power-hibernate-linux to read[/SIZE] [SIZE=2]
#!/bin/sh
/usr/sbin/s2disk

and I edited /etc/acpi/hibernate.sh to read[/SIZE] [SIZE=2]
#!/bin/bash
/usr/sbin/s2disk

I also did chmod 755 hibernate.sh[/SIZE] [SIZE=2]

[B]***So now, when I select Hibernate from the menu. It uses s2disk and that's GREAT****

but I can't get it to use s2disk when the battery is critically low!!!![/B][/SIZE]  [SIZE=2]  

I've gone to System -> Preferences -> Power Management
Gone to the "On Battery Power" tab
and changed "When Battery Power is Critically Low" to "Hibernate"

I also went into gconf-editor[/SIZE] [SIZE=2]
to 
/apps/gnome-power-manager/
and edited "action_battery_critical" to the value "hibernate"

/apps/gnome-power-manager/actions[/SIZE] [SIZE=2]
 and edited "critical-battery"  to the value "hibernate"

/apps/gnome-power-manager/general[/SIZE] [SIZE=2]
and unchecked "use_time_for_policy"

BUUUUT[/SIZE] [SIZE=2]
When my battery hits low power I get a message box saying:
"Laptop battery is critically low."
"Computer will hibernate very soon unless it is plugged in"

But when the power gets too low. My laptop just dies. It doesn't hibernate  or doesn't use s2disk

**Does anyone know how I can get s2disk to run when battery level is critically low?????**[/SIZE]

---

### Post by tony1grendel on 2011-10-17
[SIZE=2]NEVERMIND! I Got it work

the file [/SIZE][SIZE=2]/etc/pm/config.d/00_sleep_module

should actually be 

[/SIZE][SIZE=2] edited the file /etc/pm/config.d/00sleep_module

with only one underscore[/SIZE]

---

