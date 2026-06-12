---
title: "gnome-power-manager and acpi"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by fangorious on 2006-01-29
I have an HP NW8240 laptop, and after installing the Ati proprietary drivers, suspend and hibernate both work quite well. From a terminal, I can run /etc/acpi/sleep.sh (or sudo pmi action suspend) or /etc/acpi/hibernate.sh (or sudo pmi action hibernate) and everything works as expected.

I have /etc/acpi/events/lidbtn set to run /etc/acpi/sleep.sh. When I close the lid, the laptop suspends as expected. But When I resume, I'm caught in a loop where it will go right back in to suspend once the resume is complete. I have to power down the machine holding the power button to break the cycle. This seems to be due to gnome-power-manager 0.8.2.1 from the backports repo. Uninstalling it (probably just not running it would have been good enough) seems to correct the problem, but I'd like to use gnome-power-manager 0.8.2.1 because it gives me individual status for both batteries.

I have /etc/acpi/events/sleepbtn (Fn+F3 seems, works right under Windows) set to run /etc/acpi/hibernate.sh. Instead it goes into suspend. It has been suggested that this laptop doesn't technically have a sleep button. But hitting Fn+F3 is most definitely a handled event, as the laptop suspends. I just can't figure out how to change the action.

---

### Post by ranf on 2006-01-30
Did you have a look at 
System -> Settings -> keys 
(something like that. I'm translating back from german) 

The question is, who is actually handling the Fn+F3? acpid or X (and then Gnome).

---

### Post by fangorious on 2006-01-31
gnome-keybinding-properties didn't have that keystroke (I'm not even sure what the Fn key would register as) doesn't have anything with F3 listed, nore does the gconf configureation for metacity. I tried running xev in a terminal to see what the Fn key registers as, doesn't seem to register, I guess that means it's already being caught and handled by something.

---

### Post by ranf on 2006-02-01
[QUOTE=fangorious]I tried running xev in a terminal to see what the Fn key registers as, doesn't seem to register, I guess that means it's already being caught and handled by something.[/QUOTE]
That something is the acpi daemon (most likely).
Have a look at its log file, then press the Fn+F3 key combination.
```
sudo tail -n 0 -f /var/log/acpid
```

---

### Post by mjg59 on 2006-02-02
[QUOTE=fangorious]I It has been suggested that this laptop doesn't technically have a sleep button. [/QUOTE]

It doesn't have an ACPI sleep button - the key generates a scancode. In Breezy, that's caught by gnome-settings-daemon and can be configured in system/preferences/keyboard shortcuts. However, there's no way to set it to do anything other than suspend to RAM. In Dapper the situation will be better, though it's currently waiting for a patch to HAL.

---

### Post by fangorious on 2006-02-10
Ah, ok. I have fixed it now. Using gnome-keybinding-properties I disabled the sleep keybinding. Then I went into gconf->apps->gnome_settings_daemon->keybindings and set hibernate to what dleep was. Now it puts my laptop into hibernate when I hit Fn+F3. Thanks for the extra clarification Matt. I look forward to the upgraded gnome-power-manager in dapper, hopefully it won't cause suspending by closing the lid to endlessly suspend-on-resume.

---

