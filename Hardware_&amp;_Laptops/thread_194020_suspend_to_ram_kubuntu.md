---
title: "suspend to ram: kubuntu"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by woodsworth on 2006-06-10
How do you suspend-to-ram in Kubuntu Dapper? Is there supposed to be a button in the logout dialog, like in Ubuntu Dapper? Without gconf-editor, how do you even enable suspend-to-ram?

Ubuntu's not working for me. giFToxic crashes at start, and I can't get GNUsTicker to run at all. Time to go back to KDE—but will I be in for another supend-hibernate wrangle?

---

### Post by woodsworth on 2006-06-11
Is there no way to suspend in KDE?

---

### Post by chuvisco on 2006-06-11
If you right-click on the power monitor icon in the system tray, you have options to suspend to disk or to RAM.  Both worked out-of-the-box for me with Dapper.

---

### Post by vespo on 2006-06-12
[QUOTE=woodsworth]Is there no way to suspend in KDE?[/QUOTE]

Hi
Do you have kpowersave installed and showing up in system tray?
If you don't you'll have to use command line acpi, so first check if kpowersave (and the demon it uses, powersaved) are there.

I don't have kde installed right now but I recall kpowersave working out-of-the-box in other distros (unless you install proprietary ati drivers, but this is another story).

vespo

---

### Post by Josh Kurtz on 2006-06-12
Right click on your battery monitor and select 'Configure KLaptop'.  In the upper right of the window, keep clicking the right arrow until the 'ACPI Config' tab is showing.  Open that tab and select 'Enable Suspend'.  

Log out of KDE and then log back in.  Right click on the battery monitor and 'Suspend...' should be an option.  Click that and your computer will suspend to ram.

If you go back to 'Configure KLaptop' you can click on the 'Button Actions' tab that's to the left of 'ACPI Config'.  In 'Button Actions', you can set your laptop to Suspend when you close the lid switch.  On mine, I close the lid to suspend and hit the power button to wake it back up.  

Hope this helps!  :)

---

