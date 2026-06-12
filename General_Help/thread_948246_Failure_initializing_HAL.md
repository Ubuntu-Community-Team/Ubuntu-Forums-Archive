---
title: "Failure initializing HAL"
date: 2008-10-15
forum: General Help
---

### Post by henrik_daver on 2008-10-15
Just an hour ago, I took the time to install the latest upgrades that the update manager recommended. Among them were the dbus and the dbus-x11 upgrade, from 1.1.20-1ubuntu2 to 1.1.20-1ubuntu3.1. After rebooting, I keep getting an error message:

Internal error
failed to initialize HAL!

and I can't access any networks or USB drives, nor access the network settings.

I've searched the forum, and tried the fixes at, among others,
[http://ubuntuforums.org/showthread.php?t=28805](http://ubuntuforums.org/showthread.php?t=28805)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/archive/index.php/t-21887.html](http://ubuntuforums.org/archive/index.php/t-21887.html)

yet nothing have managed to do the trick, I still end up with the error message at boot.

I guess this must have to do with the dbus upgrade. If the hardware specs might be of any use, I'm running a Clevo M760 T, specs available at [http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=88](http://www.clevo.com.tw/en/products/prodinfo_2.asp?productid=88).

Grateful for help,
Henrik

---

### Post by PsychoCemia on 2008-10-15
I fixed this.

There's a bug in the '/etc/init.d/dbus' script.

I found this when I updated to the latest DBUS about 30 minutes ago, and got the HAL initialization error.

I ran 'sudo /etc/init.d/dbus start' and got several syntax errors.

FIX:

1.```

sudo nano /etc/init.d/dbus

```

2. Scroll down to line 75, and where you see
```

  elif [ -fc/rc${runlevel.conf ] ; then # file-rc

```
add a '}' (without quotes) right after 'runlevel.conf' so it looks like this:

```

  elif [ -fc/rc${runlevel.conf} ] ; then # file-rc

```

3. Scroll down to line 78, and where you see 
```

      grep -E "^[[:digit:]]{2}[[:space:]]+([0-9,S]+|[-])[[:space:]]+.*$r.*[[:space:]]+$i$"c/rc${runlevel.conf

```
add a '}' (again without quotes) right after 'runlevel.conf' so it looks like this:
```

      grep -E "^[[:digit:]]{2}[[:space:]]+([0-9,S]+|[-])[[:space:]]+.*$r.*[[:space:]]+$i$"c/rc${runlevel.conf}

```

4. Save the file (CTRL-X,YES), then perform a GDM restart (CTRL+ALT+BKSP)

5. Profit :)

So what did we learn? Fix your code before you release a critical update! o.0

---

### Post by henrik_daver on 2008-10-15
Thanks for your help, unfortunately it didn't do it for me. In fact, my /etc/init.d/dbus file looks different at the actual rows. Line 75 reads

```
elif [ - f /etc/runlevel.conf ] ; then # file-rc
```

and line 78 reads

```
grep -E "^[[:digit:]]{2}[[:space:]]+([0-9,S]+|[-])[[:space:]]+.*$r.*[[:space:]]+$i$" /etc/runlevel.conf
```

I tried changing it all to your code, yet the computer won't start appropriately.

Any other ideas?

---

### Post by henrik_daver on 2008-10-16
If it may be of any help, I just eyed through the log files, and found

```
Out of memory: kill process 5292 (dbus-daemon) score 5330 or a child
Killed process 5292 (dbus-daemon)
```

and

```
Out of memory: kill process 5822 (hald-addon-acpi) score 4168 or a child
Killed process 5822 (hald-addon-acpi)
```

This is strange, since I've got 2 GB of RAM which should be more than enough :)

If i try to restart dbus, the computer freezes, so I don't get to see any error messages that could lead me somewhere.

---

### Post by henrik_daver on 2008-10-16
Well, I rebooted and chose the previous kernel in GRUB, and this way it all works fine. So I guess it has something to do with the kernel upgrade rather than dbus?

---

