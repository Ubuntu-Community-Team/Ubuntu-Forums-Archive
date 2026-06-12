---
title: "GRUB doesn't boot the default entry (Ubuntu) automatically, keyboard sends ^[[[E"
date: 2018-12-05
forum: Hardware
---

### Post by kashinath26 on 2018-12-05
I'm using Ubuntu 18.04.1 dual booted with Windows 10 on Lenovo E41-15 laptop. Some keys of my laptop weren't working since past two months. But overnight, some miracle happened and all of the keys are working, not sparing a single one. The problem is, GRUB no longer boots the default entry automatically, and no countdown is shown. ( I had set grub_timeout to 3 sec). I have to select the OS manually every time. Also, the Ubuntu "Quiet Splash" page flickers when booting. (This wasn't the case earlier). Moreover, when the boot details are being shown, there are multiple occurrences of [FONT=arial black]^[[[E[FONT=verdana] (see attachments)[/FONT][FONT=arial][FONT=verdana]. I suspect a keystroke being sent repeatedly, which is causing all the problem. I tried checking the same with[/FONT] [FONT=arial black]xinput test 11 [FONT=arial][FONT=verdana]command, but there are no such keystrokes. It seems the problem persists only during boot. ( Not very sure about this).
Please help me out.
Thanks in advance.[/FONT]

[/FONT][/FONT][/FONT][/FONT]Here is my [FONT=georgia]/etc/default/grub[/FONT] file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Added to enable grub hiding
#GRUB_DISABLE_OS_PROBER="true"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

