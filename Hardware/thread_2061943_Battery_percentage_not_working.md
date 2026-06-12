---
title: "Battery percentage not working"
date: 2012-09-23
forum: Hardware
---

### Post by whatbeup on 2012-09-23
For some reason, the battery in the notification bar thing at the top shows a percentage, but always gets stuck at around 70%. i charged my laptop over night, but it still won't go past the 70% when i know it should be higher if not full. is there a way i can either fix this or download something that can show me my percentage correctly?:confused:

---

### Post by newb85 on 2012-09-24
Hello, and welcome to the forums!

Please provide the output of

sudo lshw -C power

^^^
That's a terminal command.  Open the terminal (Ctrl+Alt+T) and paste that command at the prompt (indicated by a $) using Ctrl+Shift+V and hit enter.  It will ask for your user password, and will not give you any feedback as you enter it.  Once the command has finished running it will give another prompt.  Copy everything between the command and the second prompt using Ctrl+Shift+C and paste it into a new post on this thread.  Before hitting "Submit Reply", surround the output with quote tags, like this.

> Here's the output

[noparse][QUOTE]Paste
The
Output
Here[/noparse][/quote]

---

### Post by whatbeup on 2012-09-24
Here's the output

>  *-power UNCLAIMED       
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

---

