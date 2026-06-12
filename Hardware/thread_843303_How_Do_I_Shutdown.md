---
title: "How Do I Shutdown?"
date: 2008-06-28
forum: Hardware
---

### Post by Jonathan Harford on 2008-06-28
I have Kubuntu 8.04/KDE4.1b2 on a Thinkpad X41, and the typical methods for turning of the machine don't seem to work!

Power button has no effect (though it turns the computer on when it's off, so it's not that the button is disconnected). It's worth mentioning that I couldn't power off via this method when Windows was installed either.

The shutdown tab of the K menu? Also no effect.

Ctrl-Alt-Del used to pop up a menu in the middle of the screen for shutting down that worked. Now that I've upgraded to KDE 4.1, Ctrl-Alt-Del just logs me out. Selecting "Shutdown" from there works, but this seems a roundabout way to get there.

Any advice?

---

### Post by be1952 on 2008-06-28
i had a similar problem on my T40 and corrected it by turning off the power management in the bios.

---

### Post by prshah on 2008-06-28
> **Jonathan Harford said:**
> 
Ctrl-Alt-Del just logs me out. Selecting "Shutdown" from there works, but this seems a roundabout way to get there.


No workaround/solution to why the power button refuses to co-operate, but does ```
sudo shutdown -P now
``` not work?

---

### Post by Jonathan Harford on 2008-07-02
> **be1952 said:**
> i had a similar problem on my T40 and corrected it by turning off the power management in the bios.

Can you be specific? There are loads of power management option and (as I do like to maximize battery life) I'd like to disable as few as possible.

Also, to the other poster: that shutdown command does, indeed, work.

---

### Post by _sphinx_ on 2008-07-02
Quoting from [http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)
> 

   1. Hold down the Alt and SysRq (Print Screen) keys.
   2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB
   3. Watch your computer reboot magically.


---

### Post by kevmitch on 2008-07-02
[erased duplicate]

---

### Post by kevmitch on 2008-07-02
You can likely get the power button to work. Let's see if the power button is generating an acpi event. First we'll temporarily stop acpid if it's running

```
sudo /etc/init.d/acpid stop
```

Now let's watch for events 

```
sudo cat /proc/acpi/events
```

Now hit the power button, you might have to hold it for a second, but not too long, or you'll get a BIOS poweroff. Does anything show up?

If not, do you have the "button" module loaded?

```
lsmod | grep button
```

If not, try loading it 

```
modprobe button
```

Does the power button generate an event now?

If that still doesn't work, see if you've got thinkpad_acpi loaded

```
lsmod | grep thinkpad_acpi
```

if not, load it and check to see if an event is generated

```
sudo modprobe thikpad_acpi
```

Once you manage to get an event see if acpid will respond to it by shutting down.

```
sudo /etc/init.d/acpid start
```

To get thinkpad_acpi to load on boot 

```
sudo echo thikpad_acpi >> /etc/modules
```

Acpid should be loading "button" on boot. If it is not, your /etc/default/acpid should look something like this

```

OPTIONS="-d -c /etc/acpi/events"
# Specify modules to load on acpid's startup
# MODULES may be uncommented to load "none", contain the string "all"
# to load all acpi related modules or simply a space seperated list
# of modules to be probed.
MODULES="battery ac processor button fan thermal video"
# using all allows us to drop extra modules in drivers/acpi and have them
# be autoloaded.
#MODULES="all"

```

---

### Post by Jonathan Harford on 2008-07-02
Wow, what a thorough reply! Thank you!

Unfortunately, though lsmod reveals that thinkpad_acpi and button are loaded, my two power buttons (one above the kb, the other under the screen) are the only "special" buttons that do not seem to trigger events!

---

### Post by kevmitch on 2008-07-03
Darn, I guess they've improved the ACPI standards compliance for the T60's. Are you sure you're pressing the power button for long enough? The one way to be sure is to press it until it does actually give a BIOS poweroff which you very well may already have tried. If not, such a brutal experiment might necessitate shutting down as many services as possible, including the xserver. You could then login via the console. 

On the other hand, the fact that it doesn't work with the officially supported OS is not encouraging.

---

