---
title: "acpi force on 10.04"
date: 2010-03-11
forum: Hardware
---

### Post by ratdude747 on 2010-03-11
i have an older machine running 10.04 

By old, i mean athlon classic old.

the board is acpi capable, but ubuntu does not detect that.

i remember that grub had some place to add "acpi force", but times change and we are in grub 2.

how would i force acpi upon boot?

---

### Post by plucky on 2010-03-11
> **ratdude747 said:**
> i have an older machine running 10.04 

By old, i mean athlon classic old.

the board is acpi capable, but ubuntu does not detect that.

i remember that grub had some place to add "acpi force", but times change and we are in grub 2.

how would i force acpi upon boot?

```
gksudo gedit /etc/default/grub
```

Add the line shown in red

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="05"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="[color=red]acpi=force[/color]"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Then run ```
sudo update-grub
``` to include the command into the grub.cfg file.

Good Luck

---

### Post by sandrogiava on 2010-11-15
Thanks, 
I had the same problem and it worked fine for my Asus K7m mb + Athlon slot A 650 Mhz cpu.
:smile::smile::smile:

---

