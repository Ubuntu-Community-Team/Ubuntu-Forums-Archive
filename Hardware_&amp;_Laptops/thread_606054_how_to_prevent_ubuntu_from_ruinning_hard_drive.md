---
title: "how to prevent ubuntu from ruinning hard drive"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by Andrewie on 2007-11-07
I have a laptop, How do I make sure that Ubuntu over rides the bios settings?

---

### Post by creeco on 2007-11-07
> **Andrewie said:**
> I have a laptop, How do I make sure that Ubuntu over rides the bios settings?

Ubuntu doesn't override any of your bios settings.. It just creates a new MBR on "top" of your HD, at ("Sector 0") 
If you want a more technical explaination take a look at [http://en.wikipedia.org/wiki/Master_boot_record]("http://en.wikipedia.org/wiki/Master_boot_record")

So go ahead install ubuntu, theres nothing to be afraid of, except for the ugly brown color of the gibbon :P!

---

### Post by Whiffle on 2007-11-07
I'm pretty sure as long as you don't enable 'laptop-mode,' you should be fine.

---

### Post by Andrewie on 2007-11-07
that was the fastest response I've ever seen...How do you check if it's in laptop mode, and if it's enabled how do I turn it off?

---

### Post by Whiffle on 2007-11-07
Its not enabled by default, you have to edit  '/etc/default/acpi-support' to enable it.

---

### Post by Andrewie on 2007-11-07
thats good, thanks for all the help

---

### Post by creeco on 2007-11-07
> **Andrewie said:**
> thats good, thanks for all the help

You're welcome

---

