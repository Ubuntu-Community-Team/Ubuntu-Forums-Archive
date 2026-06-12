---
title: "Running commands while booting + rc.local"
date: 2008-08-07
forum: General Help
---

### Post by Nepherte on 2008-08-07
To fix the brightness fn keys, I have to run the following two commands every time I've started my laptop (cfr. [https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/173652))
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
sudo /etc/init.d/acpid restart
```

Unfortunately, I don't really know how to run these commands on booting up my system. I was thinking of rc.local, but I'm not sure how.

---

### Post by mdsharp24 on 2008-08-07
#!/bin/bash
xrandr --output LVDS --set BACKLIGHT_CONTROL native && /etc/init.d/acpid restart

name it "keys", make it owned by root and executable, put it in /etc/init.d
and then link it to /etc/rc2.d/S91keys

ln -s /etc/init.d/keys /etc/rc2.d/S91keys

---

### Post by Nepherte on 2008-08-07
That doesn't seem to work. The script itself should be correct, since running it after I've logged in makes the brightness keys work.

---

### Post by Vivaldi Gloria on 2008-08-07
> **Nepherte said:**
> That doesn't seem to work. The script itself should be correct, since running it after I've logged in makes the brightness keys work.

Try this:

Save your script somewhere, make it executable, and add it to /etc/rc.local:

```
/path_to_your_script/script
exit 0
```

---

### Post by Nepherte on 2008-08-07
Doesn't work either.

The script:
```
cat /etc/init.d/brightnesskeys 
#!/bin/bash
xrandr --output LVDS --set BACKLIGHT_CONTROL native && /etc/init.d/acpid restart
```

My rc.local:
```
cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/etc/init.d/brightnesskeys
exit 0
```

Both files are executable and owned by root:
```
ls -l /etc/init.d/brightnesskeys 
-rwxr-xr-x 1 root root 93 2008-08-07 11:01 /etc/init.d/brightnesskeys
```
```
ls -l /etc/rc.local
-rwxr-xr-x 1 root root 332 2008-08-07 11:52 /etc/rc.local
```

---

### Post by louieb on 2008-08-07
Perhaps this will help.

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

You may have to link it with Init.

---

### Post by Vivaldi Gloria on 2008-08-07
If /etc/rc.local is not running then try commands of the sort

```
sudo update-rc.d rc.local defaults 
sudo update-rc.d rc.local multiuser 
```

See

```
man update-rc.d 
```

for more info. First use with the flag

```
-n     Don’t do anything, just show what we would do.
```

---

### Post by Nepherte on 2008-08-07
None of these things actually worked.

---

### Post by Vivaldi Gloria on 2008-08-07
> **Nepherte said:**
> None of these things actually worked.

Why don't you try a simple script to check if /etc/rc.local is working. How about you change rc.local to a simple one like

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "rclocal executed successfully" > /home/<your_username>/rclocal_executed 
exit 0
```

With this rc.local do you get a rclocal_executed file in your home folder when you boot up?

---

### Post by Nepherte on 2008-08-07
That works. So that leaves us two options:
[LIST]
[*]The script doesn't work:
```
#!/bin/bash
xrandr --output LVDS --set BACKLIGHT_CONTROL native && /etc/init.d/acpid restart
```
[*]The rc.local statement is wrong:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/init.d/brightnesskeys
exit 0
```
But that doesn't seem wrong to me. To restart acpid, it needs sudo privileges though. But it runs on booting so that should be alright no?
[/LIST]

---

### Post by Vivaldi Gloria on 2008-08-07
> **Nepherte said:**
> To restart acpid, it needs sudo privileges though. But it runs on booting so that should be alright no?


Yes, rc.local runs with root privileges. No problems there.

How about trying the following rc.local:

```

#!/bin/sh -e
#
# By default this script does nothing.

/usr/bin/xrandr --output LVDS --set BACKLIGHT_CONTROL native &
/etc/init.d/acpid restart
exit 0
```

---

