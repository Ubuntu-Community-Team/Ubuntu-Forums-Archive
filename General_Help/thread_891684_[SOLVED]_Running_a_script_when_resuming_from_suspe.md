---
title: "[SOLVED] Running a script when resuming from suspend"
date: 2008-08-16
forum: General Help
---

### Post by Steve1961 on 2008-08-16
I currently run Hardy on my eeepc 1000H and it works very well on the whole.  The only slight problem I have is that network-manager has trouble connecting to my wireless network when resuming from suspend.  I'm using ndiswrapper at the moment and I found a simple fix was to unload and reload ndiswrapper and then restart networking.  I also found this script that does just that, and works well:

```
#!/bin/sh

# Stop NetworkManager
/etc/dbus-1/event.d/25NetworkManager stop

# Unload ndiswrapper
/sbin/modprobe -r -f ndiswrapper

# Reload ndiswrapper
/sbin/modprobe ndiswrapper

# Restart NetworkManager
/etc/dbus-1/event.d/25NetworkManager restart
```

I've called this 99-reload-wireless.sh and dropped it into /etc/pm/sleep.d/ - which is where I believe Hardy now reads all scripts for suspend and resume.  But whilst it works well, at the moment it's run when suspending and again when I resume.  Not a huge problem I know, but it only really needs to run when resuming.  As I know nothing about scripting I wondered if there was any way to just have the script run when resuming?

---

### Post by olejorgen on 2008-08-16
I think /etc/acpi/resume.d and suspend.d are read too

If you use the /etc/pm/sleep.d (or /usr/lib/pm-utils/sleep.d( you nned to use the following format:```

case "$1" in
	hibernate|suspend)
		# your command
		;;
	thaw|resume) 
		# cour command
		;;
	*)
		;;
esac

```

---

### Post by Steve1961 on 2008-08-16
> **olejorgen said:**
> I think /etc/acpi/resume.d and suspend.d are read too

If you use the /etc/pm/sleep.d (or /usr/lib/pm-utils/sleep.d( you nned to use the following format:```

case "$1" in
	hibernate|suspend)
		# your command
		;;
	thaw|resume) 
		# cour command
		;;
	*)
		;;
esac

```


Thanks for this.  I tried first putting it in /etc/acpi/resume.d but it didn't run, and I've read somewhere that Hardy now defaults to /etc/pm/sleep.d exclusively.  Anyway, just to clarify, as I don't want any commands to run when suspending, should I just leave that section commented?

---

### Post by olejorgen on 2008-08-16
Yes, that should work

EDIT: you have to use ndiswrapper with a eepc? Isn't that a windows driver wrapper, sort of?

---

### Post by Steve1961 on 2008-08-16
> **olejorgen said:**
> Yes, that should work

EDIT: you have to use ndiswrapper with a eepc? Isn't that a windows driver wrapper, sort of?


OK, that seemed to work fine, although the system runs the scripts from the highest number first when resuming (the opposite when suspending), so it gets run almost immediately, despite the network manager script seeming to do much the same thing shortly afterwards.  However, if I remove this script network manager still doesn't connect automatically, so it obviously does something extra that the system needs.  Many thanks for this.

As for using ndiswrapper, it's just a matter of which works best.  The 1000H uses the ralink rt2860 chipset, and the native driver isn't included in Hardy.  That said, I'm using a custom kernel built by one of the eeeuser forum members that has the native module built in.  Unfortunately I've found it to be less reliable than ndiswrapper, especially when switching from network to network using network-manager.  And as I use this laptop for work (mobile IT tech), and that involves connecting to lots of different networks, I've just opted for the option that seems to work flawlessly.

---

