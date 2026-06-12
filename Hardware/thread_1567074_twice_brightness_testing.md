---
title: "twice brightness testing"
date: 2010-09-03
forum: Hardware
---

### Post by pavolzetor on 2010-09-03
Hallo, I have Thinkpad T500 and my brightness is changed by twice steps (setting by hotkey)

Please, I need your help, because
[https://bugzilla.gnome.org/show_bug.cgi?id=579224](https://bugzilla.gnome.org/show_bug.cgi?id=579224)
[https://bugs.launchpad.net/gnome-power/+bug/257827](https://bugs.launchpad.net/gnome-power/+bug/257827)

[COLOR="Red"]You need working FN keys for brightness (if you have problem with them, please describe it)[/COLOR]

So, if you have laptop with running Ubuntu and GNOME, you can provide me output of these commands and some additional information (please, no SPAM, if you have problem with one of steps, please, ask me, I try help):

At first, run script in attachment (who is not registred, please, sent output to [email]pavol@klacansky.com[/email] and I will post it, skript is here [http://disk.jabbim.cz/pk@jabbim.sk/brightness.sh](http://disk.jabbim.cz/pk@jabbim.sk/brightness.sh)) by command ```
bash brightness.sh
```


Count (gpm running): count of steps (from min. to max.), when you use hotkeys; gnome-power-manager running

Count (gpm killed): count of steps (from min. to max.), when you use hotkeys; gnome-power-manager killed by command ```
killall gnome-power-manager
```

and then you can start it by press ALT+F2 and run "gnome-power-manager"


Example output:

System: 
OS: Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic

Notebook:
LENOVO
208253G
ThinkPad T500
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Brightness:
ACPI: acpi_video0
Max: 15
Count (gpm running): 8
Count (gpm killed): 15

Thanks for making Ubuntu better

---

### Post by pavolzetor on 2010-09-03
My sister's laptop

System:
OS: Ubuntu 9.10
Kernel: 2.6.31-22-generic

Notebook:
FUJITSU SIEMENS
ESPRIMO Mobile V5505           
20
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)	

Brightness:
ACPI: acpi_video0
Max: 15
Count (gpm running): 8
Count (gpm killed): 15

---

### Post by coudy on 2010-09-03
System:
OS:Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic


Notebook:
ASUSTeK Computer Inc.        
A5E       
1.0     

Brightness:
ACPI: asus_laptop
Max: 15
Count (gpm running): 15
Count (gpm killed): 15

---

### Post by mirek on 2010-09-03
System:
OS: Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic

Notebook:
Dell Inc.
Vostro 1400  
Not Specified                   
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

Brightness:
Max: 7
Count (gpm running): 7
Count (gpm killed): 7

I had only problem with OSD indicator during counting of brightness steps - sometimes the indicator doesn't show each step, but skips one step.

---

### Post by RuneLacroix on 2010-09-03
System:
OS: Ubuntu 10.04.1 LTS
2.6.32-24-generic


Notebook:
ASUSTeK Computer INC.
1008P
x.x
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

Brightness:
ACPI: eeepc
Max: 15
Count (gpm running): 8
Count (gpm killed): 15

---

### Post by pavolzetor on 2010-09-04
Peter (don't have account)

System:
OS: Ubuntu maverick (development branch)
Kernel: 2.6.35-muj

Notebook:
Hewlett-Packard
HP ProBook 4510s
F.0A

Brightness:
ACPI: acpi_video0
Max: 24
Count (gpm running): 24
Count (gpm killed): not works

---

### Post by JohnyN on 2010-09-04
System:
OS: Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic

Notebook:
FUJITSU SIEMENS
ESPRIMO Mobile M9400
1.0

Brightness:
ACPI: acpi_video0
Max: 7

---

### Post by pavolzetor on 2010-09-04
my teacher's laptop (Linux Mint is based on Ubuntu IMHO)

System:
OS: Linux Mint 9 Isadora
Kernel: 2.6.32-23-generic

Notebook:
Hewlett-Packard
HP Compaq 6730b (FG243EC#AKR)
F.0E
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Brightness:
ACPI: acpi_video0
Max: 24
Count (gpm running): 24
Count (gpm killed): not works

---

### Post by pavolzetor on 2010-09-05
Simon (don't have account)

System:
OS: Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic

Hewlett-Packard
HP ProBook 4510s
F.14
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Brightness:
ACPI: acpi_video0
Max: 24
Count (gpm running): 24
Count (gpm killed): not works

---

### Post by fict10n on 2010-09-05
System:
OS: Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic

Notebook:
LENOVO
17024EU
ThinkPad X60s
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

Brightness:
ACPI: acpi_video0
Max: 7
Count (gpm running): 4
Count (gpm killed): 7
Count on tty1: 7

---

### Post by fict10n on 2010-09-07
System:
OS: Ubuntu 10.04.1 LTS
Kernel: 2.6.32-24-generic

Notebook:
LENOVO
2714AAG
ThinkPad R500
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Brightness:
ACPI: acpi_video0
Max: 15
Count (gpm running): 8
Count (gpm killed): 15
Count on tty1: always 15
-------------------------------------------------------

System:
OS: Ubuntu 10.04 LTS
Kernel: 2.6.32-21-generic

Notebook:
LENOVO
647814G
ThinkPad X300
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Brightness:
ACPI: acpi_video0
Max: 15
Count (gpm running): 8
Count (gpm killed): 15
Count on tty1: always 15

---

### Post by lpc921 on 2012-01-06
System:
OS: Ubuntu 11.10
Kernel: 3.0.0-14-generic

Notebook:
LENOVO
4239CTO
ThinkPad T520
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

Brightness:
ACPI: acpi_video0 intel_backlight
Max: cat: /sys/class/backlight/acpi_video0: Is a directory
cat: intel_backlight/max_brightness: No such file or directory

Count: 6
gnome-power-manager: command not found
Count (gpm running): Unknown

---

### Post by mohammad110 on 2012-01-06
System:
OS: Ubuntu 11.10
Kernel: 3.0.0-12-generic

Notebook:
LENOVO                          
IdeaPad Y450                    
Rev 1.0                 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Brightness:
ACPI: acpi_video0
Max: 10

---

