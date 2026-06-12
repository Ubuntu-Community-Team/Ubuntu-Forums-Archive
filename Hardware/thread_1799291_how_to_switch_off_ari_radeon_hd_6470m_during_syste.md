---
title: "how to switch off ari radeon hd 6470m during system startup on ubuntu 11.04?"
date: 2011-07-07
forum: Hardware
---

### Post by ciesla.tomasz on 2011-07-07
hi, I can't find proper drivers for my hybrid graphic card. It casues that Ubuntu tends to startup with black screen (about 50% of startups) and laptop fan is always turned on during normal work (due to that amd card is always turned on, instead of intel 3000 one - bigger power consumption).
I've googled alot about finding the solution but each was based on vga switcheroo, but i think that it isn't installed on my laptop by default.
I've figured it out how to switch off radeon after system starts:
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
sudo apt-get install git
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
cd acpi_call
make
**sudo insmod acpi_call.ko**
**./test_off.sh**

bu i can't figure out how to switch if off automaticly during system startup...

---

### Post by Mrunalinee on 2013-04-20
is it necessary to do this every time after the startup?

---

### Post by Mrunalinee on 2013-04-20
And how to switch on, when it is needed to keep it on?

---

### Post by oldos2er on 2013-04-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

