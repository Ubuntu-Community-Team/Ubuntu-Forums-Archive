---
title: "Suggestion: add &quot;rescue&quot; option to Wubi GRUB"
date: 2008-08-11
forum: General Help
---

### Post by spike.robinson on 2008-08-11
Can I make a suggestion for the next release of Wubi? It's quite minor but it might be helpful. 

Please add a "rescue" option on the menu.lst for GRUB. That is, add a line that has the kernel option "single" and also verbose output (no splash, no quiet). 

The reason for this is I needed to make kernel changes in order to get Ubuntu working on my machine. However all the online instructions for doing this wanted me to use the "rescue" option. I did not have the "rescue" option so I had to figure out what that was, and how to make my own by editing the kernel options in GRUB. Some people probably would've given up rather than doing this research and experimentation. 

I think it would make Wubi consistent with other installations of Wubi, if there was a "rescue" option in the GRUB boot menu. Or is "rescue" just obsolete now, for Ubuntu in general?

---

### Post by ago on 2008-08-11
It's already there, just press ESC after selecting "Ubuntu" at boot

---

### Post by spike.robinson on 2008-08-11
Sure, I can get to the GRUB menu.lst with Esc, but I do not see any "Rescue" option. I have to manually edit one of the existing menu options to add "single" and remove "quiet splash". Am I missing something?

Edit: Wubi version R506, Ubuntu 8.04.1

---

### Post by ago on 2008-08-11
> **spike.robinson said:**
> Sure, I can get to the GRUB menu.lst with Esc, but I do not see any "Rescue" option. I have to manually edit one of the existing menu options to add "single" and remove "quiet splash". Am I missing something?

Edit: Wubi version R506, Ubuntu 8.04.1

On first reboot you should see other options such as "safe graphic mode" and "verbose mode". After linux-side installation you should see the same options that you get in a normal installation

---

### Post by spike.robinson on 2008-08-11
Exactly. My GRUB options are:

Start installer in normal mode
Start installer in safe graphics mode
Start installer with ACPI workarounds
Start installer in verbose mode
Read-only Demo

This is where I would like to also have a "rescue" option. For my PC, I need to get in and do script edits before the installer will work.

---

### Post by spike.robinson on 2008-08-12
So, can we have a rescue / recovery / command-line option in GRUB, on the first reboot, **before** the linux-side installation has completed? Please? :)

---

### Post by ago on 2008-08-13
not sure why you would need to recover something that has not been installed yet...

The options you see are +/- the same you would get when you put in the live CD...

---

### Post by spike.robinson on 2008-08-13
> **ago said:**
> not sure why you would need to recover something that has not been installed yet...

The options you see are +/- the same you would get when you put in the live CD...

I need to use the recovery console to continue the installation, as it fails part way through. I have to edit the xorg.conf files from a console in order to complete the installation. To be honest though I'm not sure what GRUB menu I am using at that stage. It has the menu listing I copied in a post above. 

I'm about to repeat the whole install process from scratch so I can document it properly. I'll see if I can be more clear about what (if anything) is needed. 

Oh and just for laughs, I can't use the Live CD for installation. That's why I'm using Wubi! :)

---

