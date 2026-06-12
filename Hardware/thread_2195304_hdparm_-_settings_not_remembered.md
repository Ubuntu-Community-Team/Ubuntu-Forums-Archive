---
title: "hdparm - settings not remembered"
date: 2013-12-23
forum: Hardware
---

### Post by Ub28 on 2013-12-23
Hi, I'm using Ubuntu 13.04 (64-bit).

I can make my Western Digital drive go faster by using hdparm and setting the "multcount" to 16.  But the drive forgets this setting after rebooting or shutting down the PC.  I've tried editing *hdparm.conf* - but **no luck**!

Any ideas?

BTW I have a Western Digital WD1002FAEX.

---

### Post by mikewhatever on 2013-12-23
...and what did you put into hdparm.conf?

---

### Post by Ub28 on 2013-12-23
I've tried various edits to the **hdparm.conf** file such as removing the hash "#" from this line in the file - and putting 16 as the value: 

[I]# -m sector count for multiple sector I/O
#mult_sect_io = 16[/I]


I've tried the same with: 

[I]#/dev/hda {
#    mult_sect_io = 16
#}
[/I]

and I've also tried adding this to the bottom of the file:


 [I]/dev/sda {
mult_sect_io = 16
}[/I]


After saving the file and rebooting, I see the setting has not been remembered.  In the Terminal, after rebooting, I type:


[I]sudo hdparm -m /dev/sda
[/I]
and see this returned:

*/dev/sda:*
* multcount     =  0 (off)*

The setting is not being remembered. :(

---

### Post by mikewhatever on 2013-12-24
OK, and how do you edit the file? Do you open it as admin - **gksu gedit /etc/hdparm.conf**? Files outside your home directory are owned by root, and regular users can't edit them.

---

### Post by Ub28 on 2013-12-24
> **mikewhatever said:**
> OK, and how do you edit the file? Do you open it as admin - **gksu gedit /etc/hdparm.conf**? Files outside your home directory are owned by root, and regular users can't edit them.
 
Yes I did and I remembered to save the changes to the file.

---

