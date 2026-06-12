---
title: "ACPI (or maybe gnome-power-manager) problem"
date: 2008-08-24
forum: Hardware
---

### Post by SpazTheCat on 2008-08-24
Hi,

I have a Motion LS800 tablet that is running Ubuntu 8.04. Everything is working great with the exception of Suspend to ram and I need a little help troubleshooting.

When I look at the acpid log, it appears that the intial power button press is properly recognized. I can see that the /etc/acpi/powerbtn.sh is getting executed and the gnome-power-manager dialogue box comes with the options of suspend, shutdown, etc....

If I chose to suspend at this point, it looks like it sleeps appropriately. The screen powers off and just the power light is blinking. The problem occurs when I try to wake it back up.

I have to use the power button to wake it (none of the other tablet buttons have any effect). When I do this, the computer reboots. Meaning, the first thing I see is the bios bootsplash and then grub.

I thought if I commented out the last line in /etc/acpi/powerbtn.sh that forces a shutdown if it fails to pass things off to gnome-power-manager would fix this but it does not. Actually, removing the entire powerbtn.sh script has no effect either. The machine behaves in exactly the same manner. Also, when I look the acpid logs, I don't see the power button event to wake the computer. I only see the initial press that put the computer to sleep. The next entries are the ones you see when acpid first starts up.

So, is this an acpi issue? gnome-power-manager issue? Or, since the power button press to wake the computer isn't getting recognized by acpid am I just out of luck?

Thanks,

Andy

---

