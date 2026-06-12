---
title: "battery problem"
date: 2008-11-09
forum: Hardware
---

### Post by Cysten on 2008-11-09
Hello. I'm really new to Linux. I know some basic terminal commands and that's about it.

I just bought a Compaq Presario 1700 laptop to tinker around with linux with. 

The first problem I had was that it wouldn't shut down. After doing a dmesg|less I was able to see that it was an ACPI problem. So I found a thread that told me to attach ACPI=force at the end of my kernel in menu.lst

Well, this worked great. Mow It shows me the battery icon in the upper left. It says:

Computer is running on battery power
Laptop battery discharging (0.0%)
Battery discharge time is currently unknown

I think it is the ACPI thing because the battery icon was not there before. Also there are some ACPI error messages in my dmesg thing, which I have copied over to a file and attached. Let me know if you can help me with this. If you see any other problems you can help me with let me know!

---

### Post by hikewithmike on 2008-12-13
I have the same issue.  If I am able to find some sort of resolution I'll post it.

---

### Post by hikewithmike on 2008-12-19
a post-reply on another thread mentioned removing the battery when the computer/laptop is powered off.  I did this, and it in essence resest my battery reading, which is now correct, both though the OS and kpowersave.  It's like removing the car battery.

---

