---
title: "how to save last failed booting log?"
date: 2016-01-06
forum: Hardware
---

### Post by rla030gmail.com on 2016-01-06
hi, man

I bought the PICe TO SATA([COLOR=#404040][FONT=Roboto]asmedia 106x controller)[/FONT][/COLOR] because my machine(NAS) is lack of SATA port... just have 2 sata port

when i connect between mother and card and card and hdd using SATA cable,
I cannot boot.

i just see the words, "[COLOR=#404040][FONT=Roboto]acpi pcc probe failed" on the screen.

[/FONT][/COLOR]so i want to check the log in this situation and then i check the folder in /var/log
howhere, i can't see the log file saved log at this time...

someone know to me how can i see this one(last failed log file)?

thanks.

---

### Post by mastablasta on 2016-01-06
it should be in dmesg, however it might not get that far to be logged yet. does the grub show? 

in any case read more about logs here: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

