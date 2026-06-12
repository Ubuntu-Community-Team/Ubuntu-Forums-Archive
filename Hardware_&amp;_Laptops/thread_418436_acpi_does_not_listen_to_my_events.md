---
title: "acpi does not listen to my events"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2007-04-22
acpi does recognize my events, but does not run the scripts its supposed to execute.

When i run acpi_listen i can see that it gets the signal from rotating my screen (its a tablet pc):

```
sascha@sascha-laptop:~$ acpi_listen 
ibm/hotkey HKEY 00000080 00005009
ibm/hotkey HKEY 00000080 0000500a

```

Now i have this in my /etc/acpi/events:

```
# /etc/acpi/events/x41t-swivel-down
# called when tablet head swivels down
event=ibm/hotkey HKEY 00000080 00005009
action=/etc/acpi/x41tsdown.sh
EOF

```

As you can see the HKEY matches.

Unfortunately though the x41tsdown.sh script is not executed.
If i execute it myself it will run properly.


Does anyone have an idea what could be wrong?

---

### Post by schmolch on 2007-04-29
bump

---

### Post by jharbert on 2007-05-15
Try using the script on this [howto]("http://ubuntuforums.org/showthread.php?t=371510").  It works with my Tablet.

---

