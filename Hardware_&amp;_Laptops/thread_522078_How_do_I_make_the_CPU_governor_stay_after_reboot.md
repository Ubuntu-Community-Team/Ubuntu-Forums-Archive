---
title: "How do I make the CPU governor stay after reboot?"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by bogoliubov on 2007-08-10
Hello. I've reconfigured the gnome-panel so that I can change the CPU scaling governor. But after reboot it goes back to "On demand". Can I make the changes stay after reboot somehow?

Since I'm using a laptop, I'd like the machine to switch governor if I unplug the power cable. Can this be done somehow? I guess it would be a nice feature!

---

### Post by bogoliubov on 2007-08-10
bump....

---

### Post by bogoliubov on 2007-08-13
bump!

---

### Post by matburton on 2007-08-13
Hey,

I had exactly the same problem. In the end I stopped the system swapping back to on-demand after every reboot by removing the on-demand module! There must be a better way though! I tried many tutorials and how-tos that simply didn't work! Hope someone answers this definitively!

On the swap when the power lead is removed front I fixed that relatively easily.
If you have a look in /etc/acpi you'll find a load of scripts and folders which relate to the actions that occur when certain power events occur.
In battery.d I made a file named 99-powersave.sh, made it executable and inserted the following:
```

#! /bin/sh

# Set the CPU governor to powersave mode
# Frequency will be set to minimum regardless of load
sudo cpufreq-selector -g powersave

```
And did a similar thing in ac.d

Hope that helps!
Mat

---

### Post by bogoliubov on 2007-08-13
> **matburton said:**
> Hey,

I had exactly the same problem. In the end I stopped the system swapping back to on-demand after every reboot by removing the on-demand module! There must be a better way though! I tried many tutorials and how-tos that simply didn't work! Hope someone answers this definitively!

On the swap when the power lead is removed front I fixed that relatively easily.
If you have a look in /etc/acpi you'll find a load of scripts and folders which relate to the actions that occur when certain power events occur.
In battery.d I made a file named 99-powersave.sh, made it executable and inserted the following:
```

#! /bin/sh

# Set the CPU governor to powersave mode
# Frequency will be set to minimum regardless of load
sudo cpufreq-selector -g powersave

```
And did a similar thing in ac.d

Hope that helps!
Mat

Hey, great idea! Though I do not know much about the ACPI stuff, I'll have a look at it.

---

### Post by bogoliubov on 2007-08-13
Hmm, how do I make it so that the scripts that I've added are run whenever an "event" takes place?

---

### Post by matburton on 2007-08-14
If ACPI is working properly they should just work.

Make sure that the file name is something like mine e.g. 99-powersave.sh because the number is used for the order of scripts.
Also make sure that the script is actually executable!

The script in the appropriate folder should be run when the event occurs e.g. all scripts in battery.d run when the ac is removed. It works on start-up for me as well.

Any help?
Mat

---

### Post by bogoliubov on 2007-08-14
> **matburton said:**
> If ACPI is working properly they should just work.

Make sure that the file name is something like mine e.g. 99-powersave.sh because the number is used for the order of scripts.
Also make sure that the script is actually executable!

The script in the appropriate folder should be run when the event occurs e.g. all scripts in battery.d run when the ac is removed. It works on start-up for me as well.

Any help?
Mat

I put the exact script you showed me into /etc/acpi/battery.d  :

$ ls
total 8,0K
-rwxr-xr-x 1 root root 168 2007-03-05 07:38 15-anacron.sh
-rwxr-xr-x 1 root root 142 2007-08-13 22:10 99-powersave.sh

So it should work then I guess. But it doesn't..., hmm...

---

### Post by matburton on 2007-08-14
That's odd...

If you have a look in /etc/acpi/events and then look in both ac and batter they both run the script /etc/acpi/power.sh which in turn will run every script in either /etc/acpi/ac.d or /etc/acpi/battery.d
```

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done

```

 *clutching at straws* Your laptop does show you batter power etc correctly right?
I'm out of my depth now, strange thing is it works great for me.
Sorry!

---

### Post by Calhil on 2007-08-14
You can change cpu frequency governor using gconfig
Just type:
gconf-editor
Then find:
/apps/gnome-power-manager/cpufreq_ac_policy
/apps/gnome-power-manager/cpufreq_battery_policy
and change them to whatever governor you want ;]

---

### Post by matburton on 2007-08-15
Ah that's a better way lol :)

---

### Post by bogoliubov on 2007-08-15
> **Calhil said:**
> You can change cpu frequency governor using gconfig
Just type:
gconf-editor
Then find:
/apps/gnome-power-manager/cpufreq_ac_policy
/apps/gnome-power-manager/cpufreq_battery_policy
and change them to whatever governor you want ;]

Oh, very nice! I was looking for something like this, but couldn't find it. Sometimes gconf-editor is not very easy to navigate.

Thanks!

---

