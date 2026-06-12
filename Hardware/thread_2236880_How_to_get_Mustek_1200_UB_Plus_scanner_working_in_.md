---
title: "How to get Mustek 1200 UB Plus scanner working in Ubuntu 14.04"
date: 2014-07-29
forum: Hardware
---

### Post by Eleanor_Ellis on 2014-07-29
I struggled to get my scanner working using the instructions from [williamts99]("http://ubuntuforums.org/member.php?u=69004") at [http://ubuntuforums.org/showthread.php?t=154429](http://ubuntuforums.org/showthread.php?t=154429) and I discovered it left out the step of adding your username to the scanner group. So here is my complete howto, based on the work of [williamts99]("http://ubuntuforums.org/member.php?u=69004").

Where I show code like this ```
do some instruction here
``` it means you should type or copy this into a terminal. 
To open a terminal, 
[LIST]
[*]search for "Terminal" in Unity,
[*]select |Accessories|Terminal from your Ubuntu menu,
[*]or press [Ctrl] [Alt] [T].
[/LIST]

If you haven't already, install **sane** and **xsane**. I prefer xsane as a GUI for sane but you can use some other application if you prefer.

```
sudo apt-get install sane xsane
```

Create and navigate to driver firmware directory
```
sudo mkdir /usr/share/sane/gt68xxcd 
cd /usr/share/sane/gt68xx
```

Download driver firmware file **sbfw.usb**
```
sudo wget http://www.meier-geinitz.de/sane/gt68xx-backend/firmware/sbfw.usb

```

Set up **/etc/sane.d/gt68xx.conf** file
```
cd /etc/sane.d/
sudo sed -i.backup -e 's/^#override "mustek-scanexpress-1200-ub-plus"/override "mustek-scanexpress-1200-ub-plus"/' gt68xx.conf

```

You could also do this by editing the **gt68xx.conf** file in gedit or your text editor of choice and remove the **#** from the start of the line that looks like [B]#override "mustek-scanexpress-1200-ub-plus"
[/B]```
sudo gedit /etc/sane.d/gt68xx.conf
```

Add your user name to the "scanner" group
```
sudo adduser <username> scanner
```

Alternatively you can do this with the Gnome **Users and Groups** management tool
```

sudo apt-get install gnome-system-tools

```

Then run "Users and Groups" from |System Tools|Administration (if you are using a menu based desktop environment like Gnome Fallback or Xfce)


or search for “Users and Groups” in Unity

Click "Manage Groups"
Click on the "scanner" group and select "Properties"
Tick any users who should be able to use the scanner.


If you still have problems you may (or may not) find the following links helpful
[https://wiki.ubuntu.com/HardwareSupportComponentsScannersMustek1200UB](https://wiki.ubuntu.com/HardwareSupportComponentsScannersMustek1200UB)
[http://www.sane-project.org/](http://www.sane-project.org/)
[http://www.sane-project.org/sane-mfgs.html#Z-MUSTEK](http://www.sane-project.org/sane-mfgs.html#Z-MUSTEK)
[http://www.sane-project.org/man/sane-gt68xx.5.html](http://www.sane-project.org/man/sane-gt68xx.5.html)

Good luck!
Eleanor

---

