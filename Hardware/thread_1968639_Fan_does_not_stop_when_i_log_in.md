---
title: "Fan does not stop when i log in"
date: 2012-04-29
forum: Hardware
---

### Post by aswhad on 2012-04-29
Hey,
i (used ubuntu 9.10 for some time but) did a clean install = 12.04
On previous linux & Ubuntu i had to silent the fan with;
echo 0 > /proc/acpi/fan/FN2/state ;
 echo 3 > /proc/acpi/fan/FN2/state ;
i get the error; "...does not exist"
But this doesn't work anymore on 12.04 since there is no /proc ...

System is an old Fujitsu Amilo M7440g

Thank you in advance :)

---

### Post by aswhad on 2012-04-30
anyone?

---

### Post by brainwash on 2012-04-30
Please run following commands and attach the output:
```
cat /proc/cmdline
ls -l  /proc/acpi/*
```

```
sudo apt-get install acpitool
acpitool -f
```

---

### Post by aswhad on 2012-04-30
So here it is;

cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=b84c361a-9b0b-4d23-9799-473b8a04d59d ro quiet splash vt.handoff=7 acpi_osi=linux
( acpi_osi=linux is what i gave in the grubconsole but to no avail )

ls -l  /proc/acpi/*
-r-------- 1 root root 0 apr 30 18:17 /proc/acpi/event
-rw-r--r-- 1 root root 0 apr 30 18:44 /proc/acpi/wakeup

/proc/acpi/ac_adapter:
totaal 0
dr-xr-xr-x 2 root root 0 apr 30 18:44 ACAD

/proc/acpi/battery:
totaal 0
dr-xr-xr-x 2 root root 0 apr 30 18:44 BAT0

/proc/acpi/button:
totaal 0
dr-xr-xr-x 3 root root 0 apr 30 18:44 lid

sudo apt-get install acpitool
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  acpitool
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
Er moeten 46,7 kB aan archieven opgehaald worden.
Door deze operatie zal er 155 kB extra schijfruimte gebruikt worden.
Ophalen:1 [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) precise/universe acpitool i386 0.5.1-3 [46,7 kB]
46,7 kB opgehaald in 0s (326 kB/s)
Selecting previously unselected package acpitool.
(Database inlezen ... 181579 files and directories currently installed.)
Uitpakken van acpitool (uit .../acpitool_0.5.1-3_i386.deb) ...
Processing triggers for man-db ...
Instellen van acpitool (0.5.1-3) ...

acpitool -f
  Fan            : <not available>

---

### Post by brainwash on 2012-04-30
I think the value of
```
acpi_osi=
```
is case-sensitive. So you would have to add it like this to the kernel boot parameter list:
```
acpi_osi=Linux
```

Well, no fan is recognized by your system. Moreover, your laptop is indeed pretty old, try to boot with *acpi*=*force *once and report back.

---

### Post by aswhad on 2012-04-30
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=b84c361a-9b0b-4d23-9799-473b8a04d59d ro quiet splash vt.handoff=7 acpi_osi=Linux


no result....

---

### Post by brainwash on 2012-04-30
Did you read my last sentence? :)

Try booting with:
```
acpi=force
```

This should activate the ACPI system and hopefully provide the missing functionality.

---

### Post by aswhad on 2012-04-30
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=b84c361a-9b0b-4d23-9799-473b8a04d59d ro quiet splash vt.handoff=7 acpi=force


again no result :-(

---

### Post by brainwash on 2012-04-30
It looks like /proc/acpi/fan has been removed by the kernel developers. Lets take a look at the new "location":
```
find /sys/class/thermal/cooling_device*/ -maxdepth 1 -type f | xargs grep ""
```

This command will list the available cooling devices including state information (key:value).

---

### Post by aswhad on 2012-05-01
find /sys/class/thermal/cooling_device*/ -maxdepth 1 -type f | xargs grep ""
/sys/class/thermal/cooling_device0/type:Fan
/sys/class/thermal/cooling_device0/max_state:1
/sys/class/thermal/cooling_device0/cur_state:0
/sys/class/thermal/cooling_device1/type:Fan
/sys/class/thermal/cooling_device1/max_state:1
/sys/class/thermal/cooling_device1/cur_state:0
/sys/class/thermal/cooling_device2/type:Processor
/sys/class/thermal/cooling_device2/max_state:10
/sys/class/thermal/cooling_device2/cur_state:0

getting somewhere i guess :)

---

### Post by brainwash on 2012-05-01
Now you should try to adjust the *cur_state* values. I'm not sure, if will stop the fan, because all values are already set to 0.
```
echo **N** | sudo tee /sys/class/thermal/cooling_device**X**/cur_state
```

Changing the values might even require root privileges.

---

### Post by aswhad on 2012-05-01
> **brainwash said:**
> Now you should try to adjust the *cur_state* values. I'm not sure, if will stop the fan, because all values are already set to 0.
```
echo **N** | sudo tee /sys/class/thermal/cooling_device**X**/cur_state
```

Changing the values might even require root privileges.


"/sys/class/thermal/cooling_device1/cur_state:1" is the one because it changes

echo 0 | sudo tee /sys/class/thermal/cooling_device1/cur_state 
0   
 echo 1 | sudo tee /sys/class/thermal/cooling_device1/cur_state 
1

works :-) 
you made me a happy person brainwash !!!

---

### Post by brainwash on 2012-05-01
That's great! :)

Please use the [COLOR=Red]Thread Tools[/COLOR] and mark this thread as solved.

---

### Post by lolbot on 2012-07-07
Great, it works also here! I had same problem as Aswhad with my Fujitsu-Siemens Amilo Pa 1538 and just found this thread. Thanks Brainwash!

---

