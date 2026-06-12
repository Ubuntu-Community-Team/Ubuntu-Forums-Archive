---
title: "Closing lid not blanking screen"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by Polymira on 2005-03-22
Hey all, i've had this working on other distro's (from gentoo to a few others), and I'd really like to have it working now, as i'm moving to Ubuntu as my primary OS on my laptop. 

I have a dell inspiron 8600, has an ati radeon 9000 mobility. I like to have my laptop shut off the LCD when i close the lid, and nothing else. BUT, as it stands, it just goes to what looks like a console with a blinking cursur. Kinda crappy...

xset dpms force off      <--- works to turn it off manually...

Anyone have any ACPI config files or anything that would work for this:?

---

### Post by francesc on 2005-03-25
Had the same problem here. It has an easy solution.

Just edit /etc/acpi/lid.sh remove chvt 12 line, and add after chvt 'cat $LIDSTATE'  chvt 7. File should like like this:

```
#!/bin/sh

. /usr/share/acpi-support/power-funcs

getXuser;

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
        . /usr/share/acpi-support/screenblank
        echo `fgconsole` > $LIDSTATE
else
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
                su - $user -c "xscreensaver-command -unthrottle"
        fi
        chvt `cat $LIDSTATE`
        chvt 7
fi
```

Hope it helps.

---

### Post by wernst on 2005-03-25
Thanks for this tip. It solves the problem for me perfectly.

I'm going to make sure this is added to the bugzilla, so it is fixed for all (or at least looked at).

-Warr

---

