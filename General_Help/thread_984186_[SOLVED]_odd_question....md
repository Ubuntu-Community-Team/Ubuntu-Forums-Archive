---
title: "[SOLVED] odd question..."
date: 2008-11-16
forum: General Help
---

### Post by 4sixes on 2008-11-16
hey, i'm currently dual booting ubuntu with xp. there seems to be a problem with my computer where it thinks the power button is being pressed repeatedly, i've tried all sorts of things to fix it but the only thing left is a new motherboard, which i can't affoard, so i'm having to make do... my question is does anyone know how to suppress the shutdown menu in ubuntu, i can do it in windows, but the menu in ubuntu for what to do when the power button is pressed doesn't have 'do nothing' as an option. would there be any other way of doing it? thanks if anyone can help...

---

### Post by CatKiller on 2008-11-16
There is a cable that goes from the power button to the motherboard that sends the signal. Has this become damaged? If so, fixing it might help. If not, disconnecting this cable from the motherboard will disable the button.

Also, there may be an option in your BIOS to control the power button behaviour.

---

### Post by 4sixes on 2008-11-16
i've replaced the cable and switch, i've tested without the power switch conected at all, and i've checked the connection for any debris/dust which may be causing a short. the options in the motherboard for controlling the power button allow for immeidiate or software shutdown. thats why i was wondering about a way to make ubuntu ignore it.

---

### Post by poo_22 on 2008-11-16
System > Preferences > Power Management > General Tab

There's an option for what to do when the power button is pressed...

---

### Post by 4sixes on 2008-11-16
> **4sixes said:**
>  but the menu in ubuntu for what to do when the power button is pressed doesn't have 'do nothing' as an option. would there be any other way of doing it? thanks if anyone can help...
 there isn't an option... i can only select shutdown or ask me... shutdown isn't usefull, and ask me brings up loads of dialogs, disrupting any thing else i'm doing...

---

### Post by CatKiller on 2008-11-16
> **4sixes said:**
> i've replaced the cable and switch, i've tested without the power switch conected at all, and i've checked the connection for any debris/dust which may be causing a short. the options in the motherboard for controlling the power button allow for immeidiate or software shutdown. thats why i was wondering about a way to make ubuntu ignore it.

The fact that it's doing it without the power button signal isn't too promising. Is there anything underneath the motherboard?

If you open gconf-editor, there's a key that's controlled by the power-management settings - /apps/gnome-power-manager/buttons/power - that should determine what gets done when the power button is pressed. "nothing" is supposed to be a valid option, but it doesn't seem to work for me when I try it; for some reason it brings up the logout dialogue rather than the shutdown dialogue. So possibly this key in combination with some currently-unknown other option will help you.

---

### Post by 4sixes on 2008-11-17
Thank You, that seems to have worked so far... about 40 mins without any problems now... thanks alot catkiller

---

### Post by KailasNarendran on 2011-02-13
Thanks for this solution!  I had a hard time finding this, but to index it, I was trying to run a eeepc900 in clamshell mode.

I changed the power setting for behavior when the lid is closed to "do nothing", but the system continued to shut down when closing the lid.  I closed the lid and opened it quickly to see a dialog like the power button dialog.  As such, I guessed that maybe they looked the same to the OS.

I tried editing /etc/acpi/powerbtn.sh and putting an "exit" at the top of the script, to no avail.  

Finally, this suggestion (using gconf-editor) worked.
:D

-k

---

