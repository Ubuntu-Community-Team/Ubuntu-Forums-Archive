---
title: "Run script on wake"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by zombie.daemon on 2007-02-12
I've been looking for awhile, but haven't been able to find an answer, maybe you fine folks can help.  i'm running Edgy on an IBM laptop and looking to run a script when the laptop comes out of sleep mode.  any ideas?

---

### Post by kidders on 2007-02-12
Hi there,

This is an interesting one! I *know* there must be a way to trap the ACPI wake event, and I've been looking around for suggestions, because I'd love to know how to do this.

In the meantime, I thought I would at least suggest a somewhat hacky solution to you. It's based on the presumption that time is seen to elapse while your PC is asleep, which I'm not so sure about. Could you test the following out for me?

```
#!/bin/bash

while [ 1 ]; do
	SECONDS=`/usr/bin/time --format "%e" --output=/dev/stdout sleep 10 | cut -d. -f1`
	if [ $SECONDS -gt 20 ]; then
		echo "Sleep detected (lasted around $SECONDS seconds)"
	fi
done
```

Essentially (and this is _terribly_ crude), I'm wondering if timing your PC while it does nothing for a while would work. See what happens when you...

[LIST=1]
[*]Run the script.
[*]Put your computer to sleep immediately for 30 seconds or so.
[*]Wake it up & wait about 10 seconds.
[/LIST]

With luck, my script will notice that "sleep 10" took a lot longer than expected to finish executing.

---

### Post by gradedcheese on 2007-02-13
Actually, acpi will happily run anything that is located in:

/etc/acpi/resume.d/

when it wakes up :)  Similarly there is a suspend.d, start.d and so on.  Take a look at the existing scripts there for examples.

---

### Post by kidders on 2007-02-13
Thanks for the info, gradedcheese. I suspected the right answer would be something relatively simple, but that's ridiculous!

(Sorry zombie.daemon)

---

### Post by zombie.daemon on 2007-02-13
Hey no problem kidders, your idea is a good hack without a proper point of control.  And thanks gradedcheese.

---

