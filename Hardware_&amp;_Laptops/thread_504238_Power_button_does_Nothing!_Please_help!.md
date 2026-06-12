---
title: "Power button does Nothing! Please help!"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by fd9_ on 2007-07-18
Well, after not being able to wake up from Suspend mode, and not being able to restart via the holding down the power button, I had to pull out my battery in order to restart the machine - which I hate doing. So before I attempt to do this again, I want to make sure that my power button actually works! According to my power management settings under Feisty, pressing the power button is supposed to ask me if I want to suspend, hibernate, or shutdown. But pressing the power button does nothing! I don't think it's even detecting that the power button is being pressed, which is what I had feared.

Here are the contents of  /etc/acpi/events/powerbtn:

```

# /etc/acpi/events/powerbtn
# This is called when the user presses the power button and calls
# /etc/acpi/powerbtn.sh for further processing.

# Optionally you can specify the placeholder %e. It will pass
# through the whole kernel event message to the program you've
# specified.

# We need to react on "button power.*" and "button/power.*" because
# of kernel changes.

event=button[ /]power
action=/etc/acpi/powerbtn.sh

```


And here are the contents of /etc/acpi/powerbtn.sh:

```

#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

# Skip if we just in the middle of resuming.
test -f /var/lock/acpisleep && exit 0

# If gnome-power-manager, kpowersave or klaptopdaemon are running, let
# them handle policy This is effectively the same as 'acpi-support's
# '/usr/share/acpi-support/policy-funcs' file.

if pidof gnome-power-manager kpowersave > /dev/null ||
  (pidof dcopserver > /dev/null && test -x /usr/bin/dcop && /usr/bin/dcop kded kded loadedModules | grep -q klaptopdaemon) ; then
    exit
fi

# Otherwise, if KDE is found, try to ask it to logout.
# If KDE is not found, just shutdown now.
if ps -Af | grep -q '[k]desktop' && pidof dcopserver > /dev/null && test -x /usr/bin/dcop ; then
    KDESES=`pidof dcopserver | wc -w`
    if [ $KDESES -eq 1 ] ; then
        # single KDE session -> ask user
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 1 2 0
        exit 0
    else
        # more than one KDE session - just send shutdown signal to all of them
        /usr/bin/dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
    fi
fi

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"

```

I own a Lenovo T61, if that's any help.

---

### Post by meierfra on 2007-07-18
I would assume that the power button works just find. I would guess that "suspend" crashed your laptop. If this happens again, pressing the powerbutton for a long time ( something like 5-10  seconds) should also shutdown your computer.

---

### Post by fd9_ on 2007-07-18
> **meierfra said:**
> I would assume that the power button works just find. I would guess that "suspend" crashed your laptop. If this happens again, pressing the powerbutton for a long time ( something like 5-10  seconds) should also shutdown your computer.

As I clearly stated in my first post, my computer does not recognize the power button at all. I held it down for a full minute and it didn't do a thing.

Also, I should be getting a menu that asks me "do you wish to suspend, shut down, etc.." but I do not.

---

### Post by fd9_ on 2007-07-19
Ok, so it is recognizing the power button under certain situations...for example, I tried switching users, got a frozen black screen, and holding down the power button actually was able to restart my computer! I was very pleased. :P

But it still won't work when I try it other times. Does anyone have an answer? Do you have to hold the power button to get to that shutdown menu, or should it work just by simply pressing it?

---

### Post by misfitpierce on 2007-07-19
You should be able to hold it regardless for 10 sec tops and kill power on any OS so this is very odd

---

