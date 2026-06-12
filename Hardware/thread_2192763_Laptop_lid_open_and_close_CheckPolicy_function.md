---
title: "Laptop lid open and close: CheckPolicy function"
date: 2013-12-09
forum: Hardware
---

### Post by landersohn-m on 2013-12-09
I had a problem that after closing and reopening the lid on my laptop it remained dark, no matter what I put in the power manager.
I solved the problem by editing /etc/acpi/lid.sh:
The is a check
if [ `CheckPolicy` = 0 ] then exit fi

Apparently the script never made it past this point so I simply uncommented this lione and everything works peachy.
CheckPolicy seems to be a bash function but I can't figure out what it does or what I would have to set to actually make it work.


Question: what does CheckPolicy do and how does it do it?

---

### Post by landersohn-m on 2013-12-09
Never mind, I found the script. Looks like if a power manager is running, the lid.sh script exits and lets the power manager do its thing. In my case, though, the power manager (xfce4-power-manager) does not turn the power to he screen back on. Looks like a probem with xfce4 power manager to me, sorry for the noise

---

### Post by Toz on 2013-12-09
Thanks for posting the solution. It might be helpful if you created a [bug report]("https://help.ubuntu.com/community/ReportingBugs") against xfce4-power-manager at launchpad.

---

### Post by landersohn-m on 2013-12-09
submitted a bug

---

