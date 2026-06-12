---
title: "Display brightness bug on intel 945gse msi u100 netbook"
date: 2013-10-24
forum: Hardware
---

### Post by venetin on 2013-10-24
I have made the biggest mistake by upgrading from the most stable ubuntu 13.04 to this unfinished and buggy 13.10.There is a lot of bugs but i will post here only about my backlight problems(because the section is called hardware).

My netbook is msi u100 with intel 945gse graphics.The driver used by the system is intel 915.
When i log into unity,xfce or other DE i can not control the display brightness.If i try to use the "fn" shortcuts the brightness starts going down and the slider indicator appears and indicates that i am constanly pushing fn+F4 for decreasing the brightness.The biggest issue is that the desktop becomes unresponsible since it thinks that the keys are constantly pressed.Only hardware reboot solves the issue thill the next try for increasing/decreasing the brightness.This also happens when i open the lock and brightness settings.On lightdm login screen brightness control is ok.

```
acpi_backlight=vendor
```

Solves the issue partialy.It makes fn keys unusable and disables any kind of brightness control and locks the brightness with the last settings.

---

### Post by Toz on 2013-10-24
Hello and welcome to the forums.

Can you provide some more detailed information:

1. Your current kernel boot parameter line:
```
cat /proc/cmdline
```

2. Your video card(s) and currently running drivers:
```
lspci -k | grep -iA3 VGA
```

3. Your current backlight interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

4. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by venetin on 2013-10-25
1.
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=c29e5b60-7559-49f8-9ddf-849e399c5ee7 ro splash quiet splash vt.handoff=7
```
2.
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Kernel driver in use: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```
3.
```
/sys/class/backlight/acpi_video0
8
8
8

```
4.
```
[http://paste.ubuntu.com/6300950/](http://paste.ubuntu.com/6300950/)
```

---

### Post by Toz on 2013-10-25
Can you put the **acpi_backlight=vendor** kernel parameter back and also do the following:

1. With root privileges, create the file /usr/share/X11/xorg.conf.d/20-intel.conf:
```

sudo -i gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```
...enter your password when prompted.

2. Copy/paste this into the new window:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

3. Save the file.

4. Log out and back in again and test.

5. Post back again the results from the commands in post #2.

---

### Post by venetin on 2013-10-25
1.
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=c29e5b60-7559-49f8-9ddf-849e399c5ee7 ro splash quiet splash acpi_backlight=vendor vt.handoff=7
```
2.
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Kernel driver in use: i915
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```
3.
```
/sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: &#1053;&#1103;&#1084;&#1072; &#1090;&#1072;&#1082;&#1098;&#1074; &#1092;&#1072;&#1081;&#1083; &#1080;&#1083;&#1080; &#1076;&#1080;&#1088;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080;&#1103;
cat: /sys/class/backlight/*/actual_brightness: &#1053;&#1103;&#1084;&#1072; &#1090;&#1072;&#1082;&#1098;&#1074; &#1092;&#1072;&#1081;&#1083; &#1080;&#1083;&#1080; &#1076;&#1080;&#1088;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080;&#1103;
cat: /sys/class/backlight/*/max_brightness: &#1053;&#1103;&#1084;&#1072; &#1090;&#1072;&#1082;&#1098;&#1074; &#1092;&#1072;&#1081;&#1083; &#1080;&#1083;&#1080; &#1076;&#1080;&#1088;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080;&#1103;
```
4.
```
[http://paste.ubuntu.com/6302484/](http://paste.ubuntu.com/6302484/)
```


PS. It still does not work.

---

### Post by Toz on 2013-10-25
Interesting. Might as well get rid of that parameter, it does nothing useful. And delete the file we created.

[Here]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/415023") is an old bug report about this laptop but the comments continue on. After a quick perusal, it looks like a bios update fixed the issue for a number of people. Do you have the latest bios?

---

### Post by venetin on 2013-10-25
I don't know which il the last version.But i will check the comments related to the bug report.Thank you for your time.I will write back if there is a change.

---

### Post by venetin on 2013-10-25
I made an upgrade of the BIOS from ver 10D to the lates available 10F.I think this fixed the problem.I can control the brightness from the system settings.With function keys i am only able to use four steps(maybe 25% intervals) but it is enough.The display looks a little bit darker,but this is maybe because i was on a maximum brightness for a week.
Thanks again for your help.

---

### Post by Toz on 2013-10-25
Thats good news about the bios upgrade. Does this command:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...return the same one backlight interface, or has the bios upgraded resulted in the creation of an intel_backlight interface?

---

### Post by venetin on 2013-10-26
It returns the same interface:

```
/sys/class/backlight/acpi_video0
5
5
8

```

Do i need to add the file?Or i can keep going like this?

---

### Post by Toz on 2013-10-26
I was thinking it might have created another interface, but it didn't. This may be the best it will get (4 steps instead of 8) - you don't need that file. If you want finer control, you should be able to manually manipulate the brightness using a command like:
```
echo XX | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...where XX is a value between 0 and 8.

---

### Post by venetin on 2013-10-27
They are 4 steps only when i use Fn key combinations.In the display settings the slider can be moved freely and i think that the steps here are more than four.Anyway.I think that the problem is solved.Thanks again.

---

