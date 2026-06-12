---
title: "Blueman Bluetooth Manager not working"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Buschbarber on 2009-09-14
I have a Logitech MX5000 Bluetooth Keyboard and Mouse. Some time ago, I came across the Blueman Bluetooth Manager and installed it. It has worked perfectly, for months, until the latest upgrade of Bluez came along. Now I get an error box indicating that "Bluez Daemon is not running and Blueman cannot continue".

I followed this thread, but it did not solve the problem.

[http://ubuntuforums.org/showthread.php?p=7380937](http://ubuntuforums.org/showthread.php?p=7380937)

I have Uninstalled and Reinstalled both Bluez and Blueman, but I still get the same error.

Any suggestions would be appreciated.

---

### Post by Buschbarber on 2009-09-14
I received the following error when I ran blueman-manager from Terminal


rich@UE23:~$ sudo blueman-manager
[sudo] password for rich: 
Loading configuration plugins
_________
on_bluez_name_owner_changed (/usr/bin/blueman-manager:99)
org.bluez owner changed to   
rich@UE23:~$

---

### Post by steveneddy on 2009-09-15
```
sudo /etc/init.d/bluetooth restart
```

Maybe that will work?

Add **blueman-applet** to your Sessions menu.

If no workie, try reinstalling Blueman.

---

### Post by steveneddy on 2009-09-17
Did you ever get this working?

How?

---

### Post by Buschbarber on 2009-09-17
> **steveneddy said:**
> Did you ever get this working?

How?

I started a thread on the Blueman forum. One admin had me run a series of commands and I sent him Screen Captures.

I uninstalled Blueman and Bluez. When I reinstalled Blueman, it also installs Bluez. I got the Bluetooth Manager to appear in the System/Preferences menu, but everything was greyed out except View and Help, in the Menu Bar. There was no Bluetooth Applet in the Top Panel.

Today, I received a prompt for Ubuntu Updates. Most of them were Bluetooth related. I installed them and suddenly, the Bluetooth Applet appeared and when I launched the Bluetooth Manager, my Keyboard and Mouse appeared and I was able to Connect them.

There is one Update, called libbluetooth3 that will not install. It says Failed to detect Distribution.

---

