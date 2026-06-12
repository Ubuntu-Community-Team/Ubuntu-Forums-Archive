---
title: "how do i monitor battery life in kde?"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by fuscia on 2006-07-18
if i can do it through the konsole, that would be best (it's a desktop aesthetics issue).

---

### Post by briguy on 2006-07-18
From konsole, type in:

```
cat /proc/acpi/battery/BAT1/state
```

---

### Post by fuscia on 2006-07-18
> **briguy said:**
> From konsole, type in:

```
cat /proc/acpi/battery/BAT1/state
```

i got the following for a response...

*present: no*

i'm guessing i need to install something?

nice wig, btw.

---

### Post by briguy on 2006-07-18
It sounds like ACPI or APM are not properly configured.  Some laptop batteries don't work well with Linux, although Ubuntu has fixed that to a large degree.  Have you gone through the Settings -> Power Control -> Laptop Battery and done the ACPI config?  This can also be found under the Control Panel.

Here are a few good links on the subject:

[http://acpi.sourceforge.net/](http://acpi.sourceforge.net/)
[http://www.linuxforum.com/linux-acpi/aboutacpi.html](http://www.linuxforum.com/linux-acpi/aboutacpi.html)

I like your wig too.

---

### Post by christhemonkey on 2006-07-18
```
sudo acpi -V 
```
Will list the state off all acpi devices (such as the battery, fan etc..)

---

### Post by fuscia on 2006-07-18
i solved my weird problem. i was using a minimal setup for kde with just the konsole icon on the desk. as i have right-click menu setup, i added kbfx to the panel and just used the konsole icon for it instead. thanks for the responses. oh yeah... i can find 'laptop' from there.

---

