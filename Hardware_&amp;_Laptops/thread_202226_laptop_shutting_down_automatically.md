---
title: "laptop shutting down automatically"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by Bytewalker on 2006-06-23
hello, i just installed kubuntu yesterday but i am getting a seriously annoying problem:

it keeps shutting down in the middle of me doing stuff (even just sitting there), one time i noticed a message on the console saying "cpu reached critical temperature" before it started the shutdown sequence. so how can i disable this?

---

### Post by x64Jimbo on 2006-06-23
You're probably experiencing a failure of ACPI to properly detect your CPU's cooling system. I'd google your laptop's model number with "Linux ACPI" to see if anyone has set it up to work properly.

---

### Post by Bytewalker on 2006-06-23
hmm ok i tried modprobe -r thermal
seems to be working so far. is this gonna have any other consequences tho?

---

