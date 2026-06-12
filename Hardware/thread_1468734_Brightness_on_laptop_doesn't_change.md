---
title: "Brightness on laptop doesn't change"
date: 2010-05-01
forum: Hardware
---

### Post by GhostToast on 2010-05-01
Hi all,

I recently installed Ubuntu 10.04 LTS on my ASUS UL20A-A1 laptop through Wubi.  I am loving it so far but there is one really annoying issue.  Whenever I try to adjust my screen brightness by pressing Fn>F5/F6, the brightness meter on the top flashes, and the brightness doesn't change, not even when I plug in my laptop.  And after I try adjusting the brightness once, the brightness meter keeps popping up randomly without my pressing of the button, and there is no way to stop it popping up.  This is really irritating and I really want to use Ubuntu but this is a serious problem for me.  Does anybody know how to fix this?

Thanks!

-GhostToast

---

### Post by KlavKalashj on 2010-05-01
> **GhostToast said:**
> Hi all,

I recently installed Ubuntu 10.04 LTS on my ASUS UL20A-A1 laptop through Wubi.  I am loving it so far but there is one really annoying issue.  Whenever I try to adjust my screen brightness by pressing Fn>F5/F6, the brightness meter on the top flashes, and the brightness doesn't change, not even when I plug in my laptop.  And after I try adjusting the brightness once, the brightness meter keeps popping up randomly without my pressing of the button, and there is no way to stop it popping up.  This is really irritating and I really want to use Ubuntu but this is a serious problem for me.  Does anybody know how to fix this?

Thanks!

-GhostToast

This is a known bug, and it also affects me on my UL30A. You can find progress info here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543294](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543294)

Please write there if you have anything to add.

---

### Post by KlavKalashj on 2010-05-02
Dude, you are lucky! I just checked the bug report again, and someone posted a workaround which worked perfectly! Do it like this:

1. Open a terminal (Program - Accessories - Terminal)
2. Type in "sudo gedit /etc/default/grub" (without the "")
3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"
4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"
5. Save and exit
6. Run the command "sudo update-grub" (again without quotes of course)
7. Reboot and enjoy!

It's very easy and on my ul30a it worked like a charm!

---

### Post by kjurkic on 2010-07-28
Thank you very much KlavKalashj

I used this fix for Asus EEEPC 1005PE and it worked. 

I have years of experience with various linux distros, but would have taken a long time to figure that one out....its little problems like this that make Ubuntu or linux in general a hard-sell to newbies, who don't really car about OS's, they just want it to work without having to trouble-shoot.

regards
Ken

---

### Post by Donalt2010 on 2010-07-28
This actually didnt work for me for some reason, done exactly as it says and its made no difference:(

---

### Post by rs87424 on 2010-07-29
I have an Acer Aspire 4810 and I also didn't see any change in this modification... are you able to use the "Fn" key to adjust your brightness?

---

### Post by D4v1dw1r7h on 2010-09-03
> **KlavKalashj said:**
> Dude, you are lucky! I just checked the bug report again, and someone posted a workaround which worked perfectly! Do it like this:

1. Open a terminal (Program - Accessories - Terminal)
2. Type in "sudo gedit /etc/default/grub" (without the "")
3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"
4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"
5. Save and exit
6. Run the command "sudo update-grub" (again without quotes of course)
7. Reboot and enjoy!

It's very easy and on my ul30a it worked like a charm!


This worked perfectly on my ul20a too!!

---

### Post by burrhead1 on 2010-09-29
Yee Haw Pa, it worked! There was a difference in line 4 of the instructions and the line in the directory that appeared after running the line 3 command; the word DEFAULT was between LINUX and the = sign. Ran the line 4 command with out DEFAULT in it and it didn't work. Ran line 4 again with DEFAULT in the command and it worked like a charm. Now I won't have to wear sun shades at night when  using Linux.
This is the best O/S forum I've ever been on. Thanks to all who contributed to solving my problem.

---

### Post by travissparks1307 on 2010-12-17
I just booted up my Acer Aspire 5734Z and the screen was way too dark. Brightness controls were doing nothing. I did what the workaround said, rebooted, and BAM! Oh so beautiful. Thank you so very very much.

Running Ubuntu 10.10

---

### Post by ikiini on 2010-12-17
I  have a t410 with a dedicated nvidia quadro nvs 3100m card. This fix is not working for me. the brightness is set only if I set it, and restart the machine. it restart with the brightness level i set before restarting. I tried a lot of things, but no luck. Any other solutions I an attempt? or somewhere I can check logs?

I am running 10.10

---

### Post by legend_gibby on 2011-02-23
ok so ive done this and still no joy!!! i have an acer aspire one a0751h!!

this is what is in my grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap pci=nocrs mem=896mb"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1366x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_CMDLINE_LINUX="mem=896mb"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"

can ya help!!!

thanks

---

### Post by KingLewy on 2011-03-20
Score. Fixed my girlfriend's Samsung R519. Thanks :p

But not when running on battery :( any ideas? Cheers.

---

### Post by metalmine on 2011-09-21
i can't edit the grub file and I also can't access root...

---

