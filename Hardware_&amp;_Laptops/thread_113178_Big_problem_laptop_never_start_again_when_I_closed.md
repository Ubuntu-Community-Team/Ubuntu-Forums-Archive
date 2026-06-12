---
title: "Big problem: laptop never start again when I closed lid"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by guillem01 on 2006-01-05
Hi!
I have big problem, I can't start kubuntu on my laptop. I tried to configure in kde the lid behavior to suspend or sleep (I don't remember exactly) when I closed it. 

I closed the lid and the computer seems to be sleep or suspend but I can't "wake it up" any more. I rebooted serveral times the computer due to the lack laptop's response.

The kernel starts, and kde too, but when is put my login and password, at "loading devices" (I don't know exacty the english translation) the screen goes black, the "sleep" led lights and the fan stops. I press the power button in order to "wake it up" but, the screen dosen't change, but the fan starts to move.

I don't know to restore the original lid behavior or start again a kubuntu session.

**In really desperate, I need your help.**

Thanks in advance

Sorry for my english

---

### Post by cblanquer on 2006-01-06
Guillem,

Suspend and so on tools are a little weak on the distribution.
I am still facing some trouble when switching off mine and from suspend status it is sometimes not getting back alive (Thinkpad T21).
However with the behaviour you are describing I would recommend to reinstall the whole pack and try to avoid the parameterisation you did.
Also first check your BIOS settings before (when starting the laptop usually get them by pressing "esc" or "F8" at the very start). Disable any BIOS suspend and similar behaviour, to avoid  interferrence with the operating system.
Bona sort!

---

### Post by guillem01 on 2006-01-06
I have an Fujitsu Amilo M3438G, and my BIOS has really few options. I think I can switch it off in the BIOS. 
I haven't found on the web how to switch off the lid behavior. I tried sereval kernel which previously compiled and I have no success. 

Now I have no option, I must use windows on laptop.

---

### Post by Botond on 2006-01-06
I don't know what could went wrong but in such a situation I would 1st create another user account (see "adduser") and try to log in with that into KDE. There's a little chance that you haven't misconfigured a system-wide option with your original account and the fresh one will won't hang after logon.

---

### Post by guillem01 on 2006-01-06
Finally I solved.

1) In the grub menu, I pressed "e" for edit the boot configuration.
2) I added acpi=off on kernel line and press "b" for boot.
3) It started without ACPI, and I can login and work
4) I searched this folder: "/home/{user_name}/.kde/share/config"  (This folder contains text files with the configuration you have in kde)
5) I found "kcmlaptoprc" and I erased it (to edit this file maybe is a better way but didn't want to take risks)

Now your power management in kde have default options and you can reboot and your laptop will start without problems.

Thanks for the help

---

