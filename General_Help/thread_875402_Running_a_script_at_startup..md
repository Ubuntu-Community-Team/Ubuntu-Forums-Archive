---
title: "Running a script at startup."
date: 2008-07-30
forum: General Help
---

### Post by iamsobored0056 on 2008-07-30
In order to reduce my thinkpad's fan noise, I've been using the tp-fancontrol script from [thinkwiki]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Comprehensive_bash_script_with_fine_control_over_fan_speed").  Unfortunately, I can't get the script to run during startup.
I've saved the tp-fancontrol script in /usr/bin, and the tp-fancontrol init script in /etc/init.d.  I then ran chmod +x on both of them, and "sudo update-rc.d tp-fancontrol" defaults to add it to startup.

Does anyone know why it isn't running?

---

### Post by tuxxy on 2008-07-30
Can you not add it to your sessions

---

### Post by Diabolis on 2008-07-30
Yeah its easier to add it to your session.

System / preferences / session

In that way you can keep the script in your home folder, so it won't be deleted if you make a reinstall of ubuntu. Assuming that you have your home folder in a separate partition.

---

### Post by iamsobored0056 on 2008-07-30
> **Diabolis said:**
> Yeah its easier to add it to your session.

System / preferences / session

In that way you can keep the script in your home folder, so it won't be deleted if you make a reinstall of ubuntu. Assuming that you have your home folder in a separate partition.

I added the script to my sessions, but it still wont startup.

The script is kind of weird though.  When I run it normally, it says permission denied:
> jason@jason-laptop:~$ ./tp-fancontrol
renice: 6782: setpriority: Permission denied
> Activating watchdog with delay 9 sec
./tp-fancontrol: line 293: /proc/acpi/ibm/fan: Permission denied
> Shutting down, switching to automatic fan control
./tp-fancontrol: line 256: /proc/acpi/ibm/fan: Permission denied
When I run it using sudo:
> jason@jason-laptop:~$ sudo ./tp-fancontrol
[sudo] password for jason: 
./tp-fancontrol: 32: Syntax error: "(" unexpected
It seems to only work when i run it in the root terminal.  Could this be the reason why it wont startup?

---

### Post by Diabolis on 2008-07-30
Yes, permissions are the problem, but you don't have to run it in a root terminal. You'll hardly need a root terminal. Probably you'll never need it.

Add a line to the beginning of the script. This line:
```
sudo *"your password"*
```

So it can be executed as root when you log in.

---

### Post by Diabolis on 2008-07-30
I think that modifying its ownership should work too.

```
chown root:root *"script name"*
```

---

### Post by iamsobored0056 on 2008-07-30
> **Diabolis said:**
> I think that modifying its ownership should work too.

```
chown root:root *"script name"*
```

Thanks!  I think that did the trick,

---

