---
title: "screen turns on in standby (8.04 ibm t30)"
date: 2008-05-06
forum: Hardware
---

### Post by fuzzyworbles on 2008-05-06
I've searched high and low for a solution to this, but with no avail. When I put my IBM T30 into standby, everything seems to do well for the exception of the LCD (and alsa, but that problem is at least tolerable). 

The screen will turn off, then immediately turn back on.

The screen will then remain on while what seems to be standby mode. I never noticed this until it died due to the battery getting drained. I never had this problem with feisty or gutsy. Here are some things I've tried:

1. vbetool dpms off/standby both work just fine when called on their own
2. replacing the 'vbetool' line in /etc/acpi/suspend.d/90-framebuffer-stop.sh with 'radeontool light off' has no affect.
3. adding '"Option" "dpms" "true"' in xorg.conf has no affect.
4. uncommenting everything besides 'vbetool dpms off' in 90-framebuffer-stop.sh

I really think that it's more a problem of the screen getting turned back on after 'vbetool dpms off' is called rather than it not getting shut off correctly

.. and nothing really seems to jump out at me as a problem in /var/log/messages or /var/log/acpi .. 

can anybody offer an other suggests as to where i should look to solve this? an "unstandbyable" laptop is no laptop at all, man.

---

### Post by fprintf on 2008-05-15
I have exactly the same problem and would really appreciate the help. I activated swap after reading the problems with Hibernate (which is still broken for me) but during suspend the screen is still on.

It makes no sense that something that was working perfectly in prior editions of Ubuntu should get broken like this in Hardy!

Ta!

---

### Post by fuzzyworbles on 2008-05-15
Getting the idea from thinkwiki [here]("http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep#testing_radeonfb_without_changing_initrd") I modprobe'd radeonfb with the option force_sleep=1 and now it sleeps like a baby (this is specifically with my Radeon M7 mind you). Thinkwiki says to use radeontool light off if you use gnome, but that simply doesn't work. Yup, so "modprobe radeonfb force_sleep=1" is the pepper, as it doesn't seem to have any adverse affects running alongside the radeon xorg driver. just add it to /etc/modules.

What's this you say about no hibernation? It works fine for me.

---

### Post by fuzzyworbles on 2008-05-16
doh! don't load radeonfb. though it enables you to put your t30 to sleep, it keeps it from shutting down. before, i had discounted 'radeontool light off/on' sa a solution because the screen would still turn back on after administering the command in a terminal. finding that heron uses this new fandangled power manager (not the stuff under /etc/acpi), i found a script, edited it, and copied it into /etc/pm/sleep.d

the script looks like this:
> 
#!/bin/bash
case $1 in
    hibernate)
        /etc/init.d/alsa-utils stop
	/usr/sbin/radeontool light off
        ;;
    suspend)
        /etc/init.d/alsa-utils stop
	/usr/sbin/radeontool light off
        ;;
    thaw)
        /etc/init.d/alsa-utils start
	/usr/sbin/radeontool light on
        ;;
    resume)
        /etc/init.d/alsa-utils start
	/usr/sbin/radeontool light on
        ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac


it doesn't matter what you name your script. just make it an .sh and chmod +x. notice that i also have alsa-tools in there. now i don't have to manualy restart alsa-tools after resuming.

---

