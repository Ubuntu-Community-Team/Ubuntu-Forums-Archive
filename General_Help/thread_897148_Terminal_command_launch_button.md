---
title: "Terminal command launch button"
date: 2008-08-21
forum: General Help
---

### Post by abross on 2008-08-21
I was wondering how I can put a button on the top bar on my screen so that when I click it, it will show me the end result of this:

```
abross@abross-laptop:~$ cd /proc/acpi/battery
abross@abross-laptop:/proc/acpi/battery$ cd CMB0
abross@abross-laptop:/proc/acpi/battery/CMB0$ cat state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            537 mW
remaining capacity:      3217 mWh
present voltage:         16766 mV

```

I want to be able to click on a button and see the cat state part.

Thanks.

---

### Post by jerome1232 on 2008-08-21
you could make a simple script open gedit, save it as batt-state (or whatever you want)
put this in it
```
#!/bin/bash
cat /proc/acpi/battery/CMB0/state | less
```


then make it executable and copy it to a place in your $PATH
```
chmod +x batt-state
sudo mv batt-stat /usr/bin
```

now make a launcher for it
right click your panel>>add to panel>>custom application launcher>>

name:batt-state
command:gnome-terminal -x batt-state
comment:blahblah

I think that should work

edit: I just noticed this is for xfce, I don't know if you use a different terminal emulator or not, also you can use whatever text editor you want.

---

### Post by abross on 2008-08-22
Thanks.  But there's a problem.  When I click on the icon to launch the program, it says, "Could not run "batt-state"
                  Failed to execute child process "gnome-terminal"
                         (No such file or directory)

---

### Post by jerome1232 on 2008-08-22
ok lets check a few things, 

a) Does it work from the command line (open a terminal and just type batt-state)

b) did you move the script into /usr/bin (that was important for our launcher to work)

c) lets check permissions on it (please paste the output)

```
sudo ls -l /usr/bin/batt-state
```

d) Can you paste the exact command of your launcher?

---

### Post by LateNiteTV on 2008-08-22
> **jerome1232 said:**
> you could make a simple script open gedit, save it as batt-state (or whatever you want)
put this in it
```
#!/bin/bash
cat /proc/acpi/battery/CMB0/state | less
```


then make it executable and copy it to a place in your $PATH
```
chmod +x batt-state
sudo mv batt-stat /usr/bin
```

now make a launcher for it
right click your panel>>add to panel>>custom application launcher>>

name:batt-state
command:gnome-terminal -x **/path/to/batt-state**
comment:blahblah

I think that should work

edit: I just noticed this is for xfce, I don't know if you use a different terminal emulator or not, also you can use whatever text editor you want.

or give the full path to the batt-state script.

---

### Post by abross on 2008-08-23
1. When I type in batt-state, I get this (which is what I want):

```
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            0 mW
remaining capacity:      3405 mWh
present voltage:         16719 mV
```

2. I don't get it.

3. When I pasted it in, I got this:

```
abross@abross-laptop:~$ sudo ls -l /usr/bin/batt-state
-rwxr-xr-x 1 abross abross 52 2008-08-22 17:59 /usr/bin/batt-state
abross@abross-laptop:~$ 

```

---

### Post by jerome1232 on 2008-08-23
OH duh, lol I wasn't paying attention, your error said faild to execute gnome-terminal, so xfce apparently doesn't have gnome-terminal installed by default. 

So I'm not sure what terminal emulator you are using, but if you want you could just install gnome-terminal.

```
sudo apt-get install gnome-terminal
```

also for good practice reasons go ahead and give ownership of your script to root.

```
sudo chown root:root /usr/bin/batt-state
```

---

### Post by kerry_s on 2008-08-23
mousepad ~/.battery
put:

```
#!/bin/sh
cat /proc/acpi/battery/CMB0/state > ~/.battery-state
xmessage -center -file ~/.battery-state
```

right click the file> properties> permissions, check exec

for the launcher command put: ~/.battery
or use the browse button and select it.

---

### Post by abross on 2008-08-23
Thank You.  It worked perfectly.  Now I just wish that the battery status thing worked on my comp so I wouldn't have to use batt-state.

---

### Post by kerry_s on 2008-08-23
> **abross said:**
> Thank You.  It worked perfectly.  Now I just wish that the battery status thing worked on my comp so I wouldn't have to use batt-state.

okay, what comp is it, no info, no guess what could be wrong.

---

### Post by abross on 2008-08-23
it's a Compaq Presario 1720US.  I just wanted to add something, I'm relatively new to linux.

---

### Post by kerry_s on 2008-08-24
> **abross said:**
> it's a Compaq Presario 1720US.  I just wanted to add something, I'm relatively new to linux.

hmm, from what i been reading it should work, there are a few threads about it not working only in ubuntu, but works in every other distro, which is strange.
have you tried other distro's? perhaps straight debian might be better suited.
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-xfce-CD-1.iso)

---

