---
title: "Command to Suspend to RAM"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2006-01-13
Hello,

I have an HP DV1000. I heard that for this laptop, suspend to RAM works without problems. But, I don't want to set it up to sleep when I close the lid. I want to instead put an icon on the desktop that I can just click when I want my computer to sleep. Is there a console command that will send the laptop into suspend to RAM mode?

Thanks...

---

### Post by davinci on 2006-01-13
There is a shell script you can start:

/etc/acpi/sleep.sh

Also adapt /etc/default/acpi-support to your needs.

---

### Post by audax321 on 2006-01-13
Thanks, I'll give that a shot when I get home. :)

---

### Post by Michael Steinberg on 2006-01-13
/etc/acpi/sleep.sh has to be run by root; at least on mine that's the case....So my little beetle icon in my bottom panel launches gnome-sudo /etc/acpi/sleep.sh, and I have to enter my password to put the machine to sleep. A pain, but it's a minor one; so far I haven't bothered checking the logs to see what all requires root permissions to see if changing the permissions accordingly would let me run the script as me.

---

### Post by audax321 on 2006-01-13
Thanks that worked great. The only problem I have is that my wireless mouse which uses evdev doesn't work after coming out of sleep, but everything else is working so I'm happy. Also, I have to run the script as root as well... :)

---

### Post by davinci on 2006-01-14
You can specify which modules should be unloaded/reloaded in /etc/default/acpi-support. May be this helps with the mouse.

BTW why don't you just define a keyboad-shortcut  for sleeping. No precious workspace, fast, no password, .... just a thought.

---

### Post by Mausoleum on 2006-01-14
In order to avoid the password, you can just modify your sudo settings (sudo visudo) so that the sleep command can be run without password... (no mucking around with permissions...)

---

### Post by Michael Steinberg on 2006-01-16
[QUOTE=Mausoleum]In order to avoid the password, you can just modify your sudo settings (sudo visudo) so that the sleep command can be run without password... (no mucking around with permissions...)[/QUOTE]

I don't see how. It's not a case of permissions for the sleep.sh script. Anyone can run the shell script, but some of the processes that it turns can't be modified by anyone but root and they look to the permissions of whoever is executing the script. If I'm missing something and it really is simple I'd be happy to stand corrected!

---

### Post by jecos on 2006-01-16
Klaptop Daemon in Kubuntu is great for acpi functions like closing the lid..

---

### Post by Michael Steinberg on 2006-01-30
Only a sudoer can TELL the machine to sleep, but if you configure a keyboard shortcut (Alt-Win was mine) anyone can put the thing to sleep.

---

