---
title: "Dell Inspiron 17R not detecting lid close event"
date: 2014-01-23
forum: Hardware
---

### Post by adam33 on 2014-01-23
Hey all,
I am pretty new to Linux in general, but I wanted to set up a Linux development environment on my new laptop.

Running Ubuntu 13.10.

I just bought a Dell Inspiron 17r 5737, and first tried Mint on it.  I ran into issues with the back light not adjusting, and lid close not being detected.  I installed Ubuntu looking for a fix, and ran into the same issues.  The back light was easy enough to fix, but i've been trying to fix the lid close not triggering any acpi event for a while now without any real luck.

I can run acpi_listen, close the lid, and nothing is logged.  There is never a lid close event triggered no matter what I do (plug / unplug power while lid is closed).

Hoping it could be an issue with the BIOS, I just did an update to the latest version.  That didn't effect it at all though.

I am at a standstill, because I haven't seen a single case where someone reported this issue, and it was actually resolved.
Any help would be greatly appreciated.

---

### Post by Toz on 2014-01-23
Hello and welcome to the forums.

Is your lid recognized by the system? What does the following return?
```
dmesg | grep -i lid
```

Can you also run the following command:
```
while true; do sleep 1; cat /proc/acpi/button/lid/LID/state ; done
```
...then close your lid, wait 5 seconds and open again and post back the results of that command through that process. Lets see if the lid state is being recognized by the system but not by acpi.

And finally, and maybe a real long shot, but try changing:
> #HandleLidSwitch=suspend
...in **/etc/systemd/logind.conf** to:
```
HandleLidSwitch=ignore
```
...and reboot to test.

---

### Post by adam33 on 2014-01-23
Running:
```
dmesg | grep -i lid
```
I get:
```
[    1.190148] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0D:00/input/input0
[    1.190179] ACPI: Lid Switch [LID0]
[    1.394740] [Firmware Bug]: battery: (dis)charge rate invalid.
[    4.480461] realtek: No valid SSID, checking pincfg 0x40e00001 for NID 0x1d
[    4.484054] hda_codec: invalid CONNECT_LIST verb 5[1]:0
[    4.484121] hda_codec: invalid CONNECT_LIST verb 6[1]:0
[    4.484185] hda_codec: invalid CONNECT_LIST verb 7[1]:0

```

Running: 
```
while true; do sleep 1; cat /proc/acpi/button/lid/LID/state ; done
```
it says open no matter how long I keep the lid shut (I already tried it).

Trying to set #HandleLidSwitch=ignore now, will update post after I see if it worked or not.
Edit: didn't seem to have an effect.  Still says open when running the loop.

---

### Post by Toz on 2014-01-23
Are you using any extra kernel boot parameters?
```
cat /proc/cmdline
```

If not, you might want to try **acpi_osi="!Windows 2012"**. See if you get better acpi support.

---

### Post by adam33 on 2014-01-23
> **Toz said:**
> Are you using any extra kernel boot parameters?
```
cat /proc/cmdline
```

If not, you might want to try **acpi_osi="!Windows 2012"**. See if you get better acpi support.

I am not quite sure how to do that...

this is what that command reads:
```
adam@adam-Inspiron-5737:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.11.0-15-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
```

---

### Post by Toz on 2014-01-23
> **adam33 said:**
> I am not quite sure how to do that...

this is what that command reads:
```
adam@adam-Inspiron-5737:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.11.0-15-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
```

Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions at the [Kernel Boot Parameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki. See if it makes a difference. 

When you boot with that parameter, post back:
```
cat /proc/cmdline
```
...to ensure it worked and do the lid tests again.

---

### Post by adam33 on 2014-01-23
Done. Didn't seem to have any effect.
```
adam@adam-Inspiron-5737:~$ while true; do cat /proc/acpi/button/lid/LID0/state; sleep 1; done
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
^C
adam@adam-Inspiron-5737:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.11.0-15-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7

```

---

### Post by Toz on 2014-01-23
What does:
```
cat /proc/cmdline
```
...say?

---

### Post by adam33 on 2014-01-23
It's at the bottom of the code window in my last response =).

---

### Post by Toz on 2014-01-23
Sorry, didn't see that. Did you try it with the acpi_osi="!Windows 2012" kernel parameter? Its not showing in that result.

---

### Post by adam33 on 2014-01-23
Yes, I edited my /etc/default/grub file so it now looks like:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

acpi_osi="!Windows 2012"

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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

Then I ran sudo update-grub, and rebooted.

EDIT: Well I feel dumb... fixed the grub file, didn't realize how I needed to add that parameter.
```
adam@adam-Inspiron-5737:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.11.0-15-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7
adam@adam-Inspiron-5737:~$ while true; do cat /proc/acpi/button/lid/LID0/state; sleep 1; done
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open
state:      open

```

Still doesn't register the close event.

---

### Post by Toz on 2014-01-23
Sorry, but that's incorrect. It is best if you test it first temporarily in case something goes wrong (just need to restart to get the system back to the way it currently is). If it works, we can add it permanently by putting it in the GRUB_CMDLINE_LINUX="" line (thought the formatting will be different).

1. During boot, hold down the shift key to bring up the grub screen.
2. Press 'e' to edit the entry.
3. Use the arrow keys to go down to the line that starts with "linux".
4. Press the 'end' key to go to the end of the line and enter a **<space>**
5. Type in **acpi_osi="!Windows 2012"**
6. Press Ctrl+X to boot the system.

---

### Post by adam33 on 2014-01-23
Yeah, I had realized the error of my ways.  I was trying to do it the temporary way, but holding shift did nothing, just got brought to the Ubuntu login screen (tried about 10 different time). So I just did the permanent way.

But I edited my post above after I realized what I did wrong, and it is now showing up when I type: [COLOR=#000000][FONT=Ubuntu Mono]cat /proc/cmdline[/FONT][/COLOR] but it didn't seem to effect the event being triggered.

---

### Post by Toz on 2014-01-23
If you are adding the parameter permanently, you need to use a different format (you need to escape the quotes). Try:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by adam33 on 2014-01-23
Using that exact line, I get:
```
adam@adam-Inspiron-5737:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.11.0-15-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7
```

It still does not register close events.

---

### Post by Toz on 2014-01-23
Perhaps you should create an official [bug report]("https://help.ubuntu.com/community/ReportingBugs") for this issue.

---

