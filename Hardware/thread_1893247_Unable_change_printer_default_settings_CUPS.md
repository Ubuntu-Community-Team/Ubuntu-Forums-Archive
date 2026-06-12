---
title: "Unable change printer default settings CUPS"
date: 2011-12-09
forum: Hardware
---

### Post by Alistair George on 2011-12-09
Hi I have GTKLP installed and set some settings which I used to be able to change. Now, no matter whether I use GTKLP or system printer settings the default printer parameters cannot be changed.
Any ideas? Please see the forms below. Settings stay fixed as *Photo and Other Photo Paper*.

---

### Post by bluexrider on 2011-12-09
usually have to be a member of the "lp group" to make changes that "stick". have your permissions changed or security updated?

did you try running your program via terminal to note any issues?

is your machine up to date?

did you look here for you help 

[http://localhost:631/sum.html#STANDARD_OPTIONS](http://localhost:631/sum.html#STANDARD_OPTIONS)

---

### Post by Alistair George on 2011-12-09
> **bluexrider said:**
> usually have to be a member of the "lp group" to make changes that "stick". have your permissions changed or security updated?

did you try running your program via terminal to note any issues?

is your machine up to date?

did you look here for you help 

[http://localhost:631/sum.html#STANDARD_OPTIONS](http://localhost:631/sum.html#STANDARD_OPTIONS)

Hi I am an administrator with printer privileges.
Fixed by deleting .cups/lpoptions
Assume though that was not the real cause; suspect admin did not have write privileges for lpoptions (I dont really know)
Thanks vm.
Alistair.

---

### Post by Alistair George on 2011-12-09
Im also wondering if the default File Print dialog can be made consistent between LibreOffice and eg print from Thunderbird. Both have different dialog one shows all printers available, and the other does not?

---

### Post by bluexrider on 2011-12-09
glad you got it going. don't have a answer for the File Print dialog

---

