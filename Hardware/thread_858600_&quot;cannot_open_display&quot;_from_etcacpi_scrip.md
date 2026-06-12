---
title: "&quot;cannot open display&quot; from /etc/acpi/ script"
date: 2008-07-13
forum: Hardware
---

### Post by timrichardson on 2008-07-13
I want to modify /etc/acpi/video_brightnessdown.sh to call xbacklight
I have used
xbacklight -display 0:0 -set 50 
but in /var/log/acpid I see an error message

No protocol specified. 
Cannot open display "0:0"




I know the syntax is correct. Why can acpid not run this?

---

### Post by timrichardson on 2008-07-14
By copying lid.sh I solved this.

The call to xbacklight needs to be su the logged in user (I tried to solve this with setuid but lid.sh has a much simpler solution)

Secondly, working out the display name is not so trivial, but once again, it is already done in existing scripts such as lid.sh

---

