---
title: "Video Card Driver stops my laptop from waking."
date: 2011-02-17
forum: Hardware
---

### Post by Zanderist on 2011-02-17
(HP   Pavilion dv6; Maverick Meerkat amd64)

From this post here, 

[http://ubuntuforums.org/showpost.php?p=10439458&postcount=6](http://ubuntuforums.org/showpost.php?p=10439458&postcount=6)

Turning on the,

'ATI/AMD proprietary FGLRX graphics driver'

stops my laptop's ability to wake it's self.

I know that this driver is the problem because I've removed it, and my laptop is able to wake it's self again.

---

### Post by trundlenut on 2011-02-17
It could be an issue with the kernel mode setting.

Try adding "nomodeset" to grub when booting (after "quiet splash") and see if that sorts the problem.

I have a similar issue caused by the radeon driver.

---

### Post by Zanderist on 2011-02-17
> **trundlenut said:**
> It could be an issue with the kernel mode setting.

Try adding "nomodeset" to grub when booting (after "quiet splash") and see if that sorts the problem.

I have a similar issue caused by the radeon driver.
Where do I find grub?

---

### Post by trundlenut on 2011-02-17
When the machine boots do you have a choice of what to boot (grub menu)?

If the grub menu doesn't pop up there should be a message along the lines of press x to enter grub menu.

If select the normal line, press "e" then add nomodeset on the next to last line and then ctrl-x to boot.

---

### Post by Zanderist on 2011-02-17
> **trundlenut said:**
> When the machine boots do you have a choice of what to boot (grub menu)?

If the grub menu doesn't pop up there should be a message along the lines of press x to enter grub menu.

If select the normal line, press "e" then add nomodeset on the next to last line and then ctrl-x to boot.
Oh I see what you mean,

reboot-> select ubuntu-> then the kernel

---

### Post by Zanderist on 2011-02-17
> **Zanderist said:**
> Oh I see what you mean,

reboot-> select ubuntu-> then the kernel

I did that and it returned.

unknown command: 'nomodeset'

---

### Post by trundlenut on 2011-02-17
Yep, I'm just trying to do too many things at once so that probably wasn't too clear.

---

### Post by Zanderist on 2011-02-23
I still haven't found any solutions.

Btw this is my uswsusp file.

What happens is, if I select suspend. The computer suspends, it's when I press the power button to wake it that all I get is a lit screen but with nothing going on and I'm forced to shut down .

```
#!/bin/sh

# disable processing of 90chvt and 99video.
# s2ram and s2disk handle all this stuff internally.
uswsusp_hooks()
{
    disablehook 99video "disabled by uswsusp"
}

# Since we disabled 99video, we need to take responsibility for proper
# quirk handling.  s2ram handles all common video quirks internally,
# so all we have to do is translate the HAL standard options to s2ram options.
uswsusp_get_quirks()
{
    OPTS=""
    ACPI_SLEEP=0
    for opt in $PM_CMDLINE; do
        case "${opt##--quirk-}" in # just quirks, please
            dpms-on)        ;; # no-op
            dpms-suspend)        ;; # no-op
            radeon-off)        OPTS="$OPTS --radeontool" ;;
            reset-brightness)  ;; # no-op
            s3-bios)        ACPI_SLEEP=$(($ACPI_SLEEP + 1)) ;;
            s3-mode)        ACPI_SLEEP=$(($ACPI_SLEEP + 2)) ;;
            vbe-post)        OPTS="$OPTS --vbe_post" ;;
            vbemode-restore)   OPTS="$OPTS --vbe_mode" ;;
            vbestate-restore)  OPTS="$OPTS --vbe_save" ;;
            vga-mode-3)        ;; # no-op
            save-pci)          OPTS="$OPTS --pci_save" ;;
            none)            QUIRK_NONE="true" ;;
            *) continue ;;
        esac
    done
    [ $ACPI_SLEEP -ne 0 ] && OPTS="$OPTS --acpi_sleep $ACPI_SLEEP"
    # if we were told to ignore quirks, do so.
    # This is arguably not the best way to do things, but...
    [ "$QUIRK_NONE" = "true" ] && OPTS=""
}

# Since we disabled 99video, we also need to handle displaying
# help info for the quirks we handle.
uswsusp_help()
{
    echo  # first echo makes it look nicer.
    echo "s2ram video quirk handler options:"
    echo
    echo "  --quirk-radeon-off"
    echo "  --quirk-s3-bios"
    echo "  --quirk-s3-mode"
    echo "  --quirk-vbe-post"
    echo "  --quirk-vbemode-restore"
    echo "  --quirk-vbestate-restore"
    echo "  --quirk-save-pci"
    echo "  --quirk-none"
}

# This idiom is used for all sleep methods.  Only declare the actual
# do_ method if:
# 1: some other sleep module has not already done so, and
# 2: this sleep method can actually work on this system.
#
# For suspend, if SUSPEND_MODULE is set then something else has already
# implemented do_suspend.  We could just check to see of do_suspend was
# already declared using command_exists, but using a dedicated environment
# variable makes it easier to debug when we have to know what sleep module
# ended up claiming ownership of a given sleep method.
if [ -z "$SUSPEND_MODULE" ] && command_exists s2ram && \
    ( grep -q mem /sys/power/state || \
        ( [ -c /dev/pmu ] && check_suspend_pmu; ); ); then
    SUSPEND_MODULE="uswsusp"
    do_suspend()
    {
        uswsusp_get_quirks
        s2ram --force $OPTS
    }
    if [ "$METHOD" = "suspend" ]; then
        add_before_hooks uswsusp_hooks
        add_module_help uswsusp_help
    fi
fi

if [ -z "$HIBERNATE_MODULE" ] && \
    [ -f /sys/power/disk ] && \
    grep -q disk /sys/power/state && \
    [ -c /dev/snapshot ] &&
    command_exists s2disk; then
    HIBERNATE_MODULE="uswsusp"
    do_hibernate()
    {
        s2disk
    }
fi

if [ -z "$SUSPEND_HYBRID_MODULE" ] && 
    grep -q mem /sys/power/state && \
    command_exists s2both && \
    check_hibernate; then
    SUSPEND_HYBRID_MODULE="uswsusp"
    do_suspend_hybrid()
    {
        uswsusp_get_quirks
        s2both --force $OPTS 
    }
    if [ "$METHOD" = "suspend_hybrid" ]; then
        add_before_hooks uswsusp_hooks
        add_module_help uswsusp_help
    fi
fi

```

---

### Post by trundlenut on 2011-02-24
I still think the problem relates to KMS, try "radeon.nomodeset=0" instead of "nomodeset" and make sure you didn't try "nomodset", I did this about half a dozen times and couldn't understand why it didn't work before I relaised I couldn't spell.

---

### Post by Zanderist on 2011-02-24
Okay I will give it a try and report back.

---

### Post by P4man on 2011-02-24
Even if you mistype a kernel parameter, I dont think it returns "unknown command", so I think you are doing it wrong. Please see the link in my signature for detailed step by step instruction to boot with nomodeset (and other kernel options).

---

### Post by Zanderist on 2011-02-24
Well I tested before. And it did boot, with the nomodeset added, but nothing changed.

---

### Post by Zanderist on 2011-02-24
> **trundlenut said:**
> I still think the problem relates to KMS, try "radeon.nomodeset=0" instead of "nomodeset" and make sure you didn't try "nomodset", I did this about half a dozen times and couldn't understand why it didn't work before I relaised I couldn't spell.
I tried this, nothing changed.

I still wasn't able to wake the computer from suspend. (i.e, I boot the computer, then click the suspend button. The computer goes to sleep and when I press the power button to wake it doesn't return.)

Hibernate mode reports something different, "not enough swap space".

---

### Post by P4man on 2011-02-24
> **Zanderist said:**
> I tried this, nothing changed.

I still wasn't able to wake the computer from suspend. (i.e, I boot the computer, then click the suspend button. The computer goes to sleep and when I press the power button to wake it doesn't return.)

Can you elaborate a bit? Does the screen remain black, does the backlight come on? Also, can you try pressing control+alt+F1 and see if you get a full screen terminal, then try control+alt+F7 (sometimes F8 ) to return to the GUI?

Lastly, if none of that helps, try some of the other options described in my link. Like "acpi_osi=Linux" and "noapic"

> Hibernate mode reports something different, "not enough swap space".

How big is your swap partition?

---

### Post by Zanderist on 2011-02-24
> **P4man said:**
> ** the screen remain black, does the backlight come on?** 
This is what happens.

This is happening because I activated my video card.

If I remove my video card (downgrade) this problem does not happen.

> How big is your swap partition?

How can I check this because I really can't see anything Disk Utility and Gparted, saying anything about swap space.

> **P4man said:**
> Also, can you try pressing  control+alt+F1 and see if you get a full screen terminal, then try  control+alt+F7 (sometimes F8 ) to return to the GUI?

Tried this, nothing happen. Just what I quoted you on first.

---

### Post by trundlenut on 2011-02-24
what does "sudo fdisk -l" output?

---

### Post by Zanderist on 2011-02-24
I did a wubi install.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85f81c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       58050   466076672    7  HPFS/NTFS
/dev/sda3           58050       60789    21997568    7  HPFS/NTFS

```If you want to know what the partition 1 not ending on the cylinder boundary is about (at least to me it sounds like a problem)

I had some trouble before that is completely unrelated to this and is documented in this following thread:

[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

---

### Post by trundlenut on 2011-02-24
> **Zanderist said:**
> I did a wubi install.



That, I suspect opens a whole new can of worms.

---

### Post by Zanderist on 2011-02-24
> **trundlenut said:**
> That, I suspect opens a whole new can of worms.

Not really cause all I have to do is downgrade the video driver and everything will be fine.

I just won't be able to have smoother graphics.

Remember the problem, has to do with the suspend/hibernate option.

I close the laptop and it fails to suspend,  if I click the button ( with the mouse) the screen goes black and never comes back.

This doesn't have to do with me booting it up, which works flawlessly. It's just that the laptop doesn't want to wake when I suspend or hibernate it.

---

### Post by P4man on 2011-02-24
Can you try booting with "nomodeset" and then provide the output of
```
cat /proc/cmdline
```
That way, we will be sure you are doing it correctly, as I have my doubts still. 

As for hibernating, I dont think its supported with wubi.

---

### Post by Zanderist on 2011-02-24
> **P4man said:**
> Can you try booting with "nomodeset" and then provide the output of
```
cat /proc/cmdline
```That way, we will be sure you are doing it correctly, as I have my doubts still. 


```
BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash nomodeset

```> As for hibernating, I dont think its supported with wubi.It was hibernating before I activated the video card, this all has to do with the video card it seems like.

---

