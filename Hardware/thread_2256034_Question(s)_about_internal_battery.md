---
title: "Question(s) about internal battery"
date: 2014-12-09
forum: Hardware
---

### Post by michael-piziak on 2014-12-09
I've had internal batteries die in the past and had to replace them, but not using Ubuntu.  I'm curious how one knows with Ubuntu when their internal battery is getting low or has died.

I guess what got me thinking of this is sometimes on boot up it says "checking battery state" then far to the right it says [ok]"

---

### Post by TheFu on 2014-12-09
The CMOS battery?  Don't really worry about that until the BIOS gets confused or time keeping is way off.

For a laptop, there are battery monitoring tools. I use ```
acpi -V
``` from a shell to keep track.
An example:
> Battery 0: Full, 100%
Battery 0: design capacity 4030 mAh, last full capacity 4026 mAh = 99%


---

### Post by michael-piziak on 2014-12-09
Thanks.  I wonder if there is any way to check the battery in a desktop.

---

### Post by TheFu on 2014-12-09
You could open a terminal and run that same command. That works. 
 I've heard that other people like to use conky for stuff like this.

---

### Post by michael-piziak on 2014-12-09
Previously you said, "[COLOR=#000000]Don't really worry about that until the BIOS gets confused or time keeping is way off."

How does one know when the BIOS gets confused ?

[/COLOR]

---

### Post by TheFu on 2014-12-10
> **michael-piziak said:**
> How does one know when the BIOS gets confused ?

Things don't act normal, especially at boot.  There is no exact answer, but if a HDD disappears (and is still working in other machines), that is a hint.  Does that make sense?

In the last 10 yrs or so, I haven't had to deal with this at all.

---

