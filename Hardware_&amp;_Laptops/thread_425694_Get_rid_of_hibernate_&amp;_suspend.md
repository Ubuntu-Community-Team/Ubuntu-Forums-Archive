---
title: "Get rid of hibernate &amp; suspend"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by zenkaon on 2007-04-27
Hello all,

Is there a way to get rid of the options to put my laptop into hibernation / suspend? 
It would be great if they worked, but unfortunately they don't, they just kill my laptop.

I want to remove the option from kde, I simply don't want 2 rouge "crash my laptop" buttons hanging around.

I am running kubuntu feisty fawn 7.04 on a Toshiba Tecra M3, 2.1Ghz Intel, 1gb RAM, 80gb HD.

---

### Post by DagMan on 2007-04-27
They bind to files in /etc/acpi/events which in turn call on scripts in /etc/acpi
You would want to edit the enty in /etc/acpi/events and comment them out however the one that has your laptop name in it is not always the one that is used.  If you really want, you could just move all the files from /etc/acpi/events that look like they might apply to another location.

It's quite possible that suspend and hibernate will work but something in the scripts called needs to be commented out.

---

### Post by calgarystevens on 2007-04-28
One thing that I did was: go to /etc/acpi as sudo (sudo nautilus) then make copies of hibernate.sh, sleep.sh and lid.sh Then open each of them and edit them with only this line: /sbin/shutdown -h now "Power button pressed"

This will mean that pressing the suspend or hibernate (or closing lid on laptop) will shutdown the computer. Then you can still use power management, but instead of sleep it will shutdown, so it won't have to run all day if you don't want it to.

---

