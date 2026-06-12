---
title: "Toshiba Satellite A100 Bluetooth"
date: 2009-03-22
forum: Hardware
---

### Post by Otacon87 on 2009-03-22
Hi to all,
yesterday i needed to use bluetooth on my Toshiba Satellite A100-117, but I thought that Ubuntu doesn't recognize it since latest versions of linux kernel...Last time it worked under ubuntu, i've updated _**UNDER WINDOWS**_ the *Toshiba Bluetooth Stack*, then I restarted and it worked well, but i've thought that it was only a coincidence!
Yesterday i've tried again to update under Windows XP my Toshiba Bluetooth Stack...AND magically it worked another time under these conditions:
[LIST]
[*]Bluetooth **MUST** *remain turned on* during Windows Shutdown
[*]Toshiba Bluetooth Stack version **MUST** be *> 6.30*
[/LIST]

Now, if someone can explain WHY it worked and HOW to help you developing some "ugly" drivers to ENABLE and DISABLE it under ubuntu...
I can program in C / C++ / Python / Java / C# (last one only a bit :) )

---

### Post by Tclarkie on 2011-04-19
""The **bluetooth** module on **Toshiba Satellite A300** laptop is not available by default via **lspci** and **lsusb** tools. This is because we need to make an **acpi** call to enable it. Follow these steps to get it working on Debian/Ubuntu linux:
 1. Add these repositories to your **/etc/apt/sources.list**:
 deb [http://packages.kirya.net/debian/](http://packages.kirya.net/debian/) sid main contrib non-free
deb-src [http://packages.kirya.net/debian/](http://packages.kirya.net/debian/) sid main contrib non-free
When run 
 sudo apt-get update
to synchronize package list.
2. Install package **omnibook-source**:
 sudo apt-get install omnibook-source
3. Build and setup the **omnibook** module:
 sudo m-a a-i omnibook-source
4. Create new file called **omnibook** in **/etc/modprobe.d/** folder and put the following content there:
 options omnibook ectype=14
5. For autoload this module you can add the line in your **/etc/modules**:
 omnibook
6. Now you can load it manually via command:
 sudo modprobe omnibook ectype=14
The **bluetooth** icon should be appear in the system tray.""
[http://www.alexxoid.com/blog/linux/how-to-enable-bluetooth-on-toshiba-satellite-a300-laptop.html](http://www.alexxoid.com/blog/linux/how-to-enable-bluetooth-on-toshiba-satellite-a300-laptop.html)

---

