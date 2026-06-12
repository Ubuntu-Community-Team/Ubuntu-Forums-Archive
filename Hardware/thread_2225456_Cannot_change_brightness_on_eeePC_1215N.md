---
title: "Cannot change brightness on eeePC 1215N"
date: 2014-05-21
forum: Hardware
---

### Post by Einenlum on 2014-05-21
Hi there.

If on Xubuntu, changing brightness works out of the box, I can’t make it work on Lubuntu.
The fn keys seem to work, because when I press fn+F5 or fn+F6, the brightness applet shows the brightness bar moving. But the screen's brightness isn’t changing at all.
Then I saw on the net that changing GRUB entry could fix it.

Here was my original GRUB entry:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Here I tried to change the **GRUB_CMDLINE_LINUX_DEFAULT** value to "**apci_osi=Linux**", but no change. I also tried to replace it by "**acpi_backlight=vendor**": not only it did not fix it but then the applet is not called anymore.
If I put both options ( "apci_osi=Linux acpi_backlight=vendor" ), same thing. No fix, and no reaction from the brightness applet (Of course, I updated GRUB after every change).

Do you have any idea ? My eyes start bleeding…

Thanks in advance :wink:

**EDIT: PROBLEM SOLVED**
Thanks to this how to ( [http://ubuntuforums.org/showthread.php?t=2186919](http://ubuntuforums.org/showthread.php?t=2186919) ) I solved the prob (I assigned the Alt+F5 and Alt+F6) to these actions. :)

---

### Post by jeremy31 on 2014-05-21
> **Einenlum said:**
> Hi there.

If on Xubuntu, changing brightness works out of the box, I can’t make it work on Lubuntu.
The fn keys seem to work, because when I press fn+F5 or fn+F6, the brightness applet shows the brightness bar moving. But the screen's brightness isn’t changing at all.
Then I saw on the net that changing GRUB entry could fix it.

Here was my original GRUB entry:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Here I tried to change the **GRUB_CMDLINE_LINUX_DEFAULT** value to "**apci_osi=Linux**", but no change. I also tried to replace it by "**acpi_backlight=vendor**": not only it did not fix it but then the applet is not called anymore.
If I put both options ( "apci_osi=Linux acpi_backlight=vendor" ), same thing. No fix, and no reaction from the brightness applet (Of course, I updated GRUB after every change).

Do you have any idea ? My eyes start bleeding…

Thanks in advance :wink:

**EDIT: PROBLEM SOLVED**
Thanks to this how to ( [http://ubuntuforums.org/showthread.php?t=2186919](http://ubuntuforums.org/showthread.php?t=2186919) ) I solved the prob (I assigned the Alt+F5 and Alt+F6) to these actions. :)

So did you make the scripts and make them executable and bind them to the key presses?

---

### Post by Einenlum on 2014-05-22
Absolutely. I just had to make xbindkeys launch automatically at startup (which was not precised in the howto).
I assigned Alt+F5 and Alt+F6 to decrease and increase brightness (instead of the fn+F5 and fn+F6 combinations initially) because like the author of the howto I didn&#8217;t find how to assign *fn* keys.
;)

---

### Post by roger_1960 on 2014-09-03
I had the same issue as the original post on my eeepc 1011px and found this solution which works and seems a more simple solution
[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

Roger

---

