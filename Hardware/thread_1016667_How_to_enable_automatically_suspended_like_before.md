---
title: "How to enable automatically suspended like before?"
date: 2008-12-20
forum: Hardware
---

### Post by jay li on 2008-12-20
I remember when I've got my fresh ubuntu 8.10, the suspend worked automatically. 
After the first time the system made an updates this option gone. 
I don't know why and I would like to bring it back.

Specs:

eee pc 701
sd card
Ubuntu 8.10
jfs format
no swap

---

### Post by iponeverything on 2008-12-20
Go to:

System -> Preferences -> Power Management 

and check your settings.

---

### Post by jay li on 2008-12-20
Thanks iponeverything, but I did that already and nothing change as you can see in the attachment below.

PS ignore the "blank screen" selection

---

### Post by iponeverything on 2008-12-20
Does it obey on AC?

is acpi running?

```
ps uaxwww|grep acpi 
```

---

### Post by jay li on 2008-12-20
I run the code you gave but didn't understand anything from it. 

Output:
 
[COLOR="Blue"]baryoni@baryoni-desktop:~$ ps uaxwww|grep acpi
root        50  0.0  0.0      0     0 ?        S<   21:45   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   21:45   0:00 [kacpi_notify]
111       4588  0.0  0.1   2296   960 ?        S    21:45   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4816  0.0  0.3   2840  1796 ?        Ss   21:45   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
baryoni   6204  0.0  0.1   3240   812 pts/0    S+   22:19   0:00 grep acpi[/COLOR]

If can explain me what is that mean, I'll appreciate that. 

Thanks.

---

### Post by dserodio on 2008-12-20
> **jay li said:**
> I run the code you gave but didn't understand anything from it. 

Output:
 
[COLOR="Blue"]baryoni@baryoni-desktop:~$ ps uaxwww|grep acpi
root        50  0.0  0.0      0     0 ?        S<   21:45   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   21:45   0:00 [kacpi_notify]
111       4588  0.0  0.1   2296   960 ?        S    21:45   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4816  0.0  0.3   2840  1796 ?        Ss   21:45   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
baryoni   6204  0.0  0.1   3240   812 pts/0    S+   22:19   0:00 grep acpi[/COLOR]

If can explain me what is that mean, I'll appreciate that. 

Thanks.

The first line means that **kacpid** (**k**ernel **ACPI** **d**aemon) is running.

---

### Post by jay li on 2008-12-20
And...?
Can I get it work or not?
If the answer is yes, then how please.

---

