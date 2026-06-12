---
title: "Suddenly no video, no boot, fans run"
date: 2018-11-20
forum: Hardware
---

### Post by Odyssey1942 on 2018-11-20
Dell XPS 8700 Desktop i7-4790 16GB RAM dual boot Win 10 home on HDD / Ubuntu MATE 18.04.1 on SSD

Well, I managed to pull the pin on a grenade. I was trying to sort out an ethernet connectivity failure, following this forum post  [https://en.opensuse.org/SDB:Realtek_8169_driver_problem]("https://en.opensuse.org/SDB:Realtek_8169_driver_problem") and had started with step 2, then restarted. The power turned on (fans spun), but no video output. Dang!

This confounds me as I would not expect the change I made (enabled wake on LAN in BIOS) to brick the mobo, and hopefully there is some way to restore. 

Following this revolting experience, I am reluctant to experiment.

Anyone know how to recover? Thanks.

---

### Post by TheFu on 2018-11-20
Well, it is possible that THIS issue has been the root cause for the ethernet issue.

Power issues could be a bad PSU, bad power cabling inside the machine, fried GPU, or a short circuit somewhere on the motherboard.  The cheapest component to replace is the PSU, assuming you can't get a computer shop to test it for you.  Next would be the GPU (probably).

There's no way that compiling and installing a NIC driver would cause this.

---

### Post by Dennis N on 2018-11-20
Many if not all Dell Desktops have beep codes (and possibly diagnostic LEDs on the board) to diagnose the nature of startup problems:

These links might help:

[No Post, No Power, and/or No Video]("https://www.dell.com/support/article/us/en/04/sln153751/no-post-no-power-no-video-on-a-dell-desktop-computer?lang=en")
[Understanding Beep Codes]("https://www.dell.com/support/article/us/en/04/sln293445/understanding-beep-codes-on-a-dell-desktop-pc?lang=en")

---

### Post by Odyssey1942 on 2018-11-20
The Fu, Seems that if I had eth connectivity in a Windows boot up every time, but never in Ubuntu, it would be highly co-incidental. But maybe this is the underlying issue. I do have a PSU tester and will check this.

Dennis, thanks for those links. Will work on those when I get back here early  afternoon. BTW, I do not see any lights near the eth cable on back of computer, nor hear any beeps, without or with headphones. Also no video on monitor, no matter what I try.

---

### Post by Dennis N on 2018-11-20
The speaker is a tiny one plugged into the motherboard. It doesn't play through your regular speakers or headphones. On Dell, I get one beep (not loud) when I start up the Dell desktop machine, right after pressing power ON button. If you never previously heard any beeps on startup, you may not have a PC speaker, so look for LEDs. Check your computer's owner manual to see what diagnostic LEDs might be present on the board.

Ethernet sockets may have little LEDs to show connection status. All my computers have these. Attached is picture showing where they might be seen. Judging by the state of your wired connection in your other thread, I imagine yours may just be off.

---

### Post by Odyssey1942 on 2018-11-20
This just keeps careening around. Decided to try a SVGA cable and it works fine. Gets video to monitor, so looks like either the video card DVI circuit, the DVI cable, or the DVI port/circuit in the monitor has gone toes up. Will buy another DVI cable tomorrow and see if that is it. In the meantime, will continue with the SVGA.

That's the good(?) news. The bad is that it has stopped dual booting and will only boot into Windows. So either,

the previously unused, but 2 year old SSD has crashed (it does not show up in Windows file explorer), or

the bootloader isn't facilitating a dual boot.

The former seems the less likely (plus I am unsure how to test a SSD), so I suspect the bootloader?
--------------------------------
EDIT: UPDATE: By pressing F12 during the boot process that now results in a Windows boot, a screen comes up:

    Boot mode is set to UEFI with Legacy OPROM, secure boot off
    -----
    UEFI:

        Windows Boot Mgr  (if selected, boots into Windows)

        Ubuntu (if selected boots into Grub Screen and I select  Ubuntu, it boots into UM18.04).

The good news is that (1) the SSD seems to be OK and (2) the grub screen is still there, bad news is that the computer does not boot into the Grub screen.

The other good news is that it narrows down what needs to be fixed, i.e., booting directly into the grub screen. How can I do this?

---

### Post by Dennis N on 2018-11-20
You may just need to change the boot order in the UEFI so that Ubuntu goes first. That's a job for **efibootmgr** command. To see if I might be right, boot into your 18.04 install and then use the terminal to run the command below, and post the output:

```
sudo efibootmgr -v
```

(this doesn't change anything - just reports on the current status of boot order).

---

### Post by Odyssey1942 on 2018-11-20
```
sudo efibootmgr -v
[sudo] password for 
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0002,0006,0000,0001
Boot0000* P3: TOSHIBA Q300              	BBS(17,,0x0)
Boot0001* P1: TSSTcorp DVD+/-RW SH-216DB	BBS(19,,0x0)
Boot0002* Windows Boot Manager	HD(2,GPT,7b05b782-ee1e-47f0-b800-b772c1bbdc12,0xfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0006* ubuntu	HD(2,GPT,7b05b782-ee1e-47f0-b800-b772c1bbdc12,0xfa000,0x32000)/File(\EFI\Ubuntu\grubx64.efi)

```

---

### Post by Dennis N on 2018-11-21
Look at BootOrder - UEFI is set to boot Windows first.
```
BootOrder: 0002,0006,0000,0001
```
0002 (refers to Boot0002 in the list) is Windows.
Do this terminal command to change order and make Ubuntu boot first:
```
sudo efibootmgr -o 0006,0002
```
changes order of first and second entries in boot order list.
Reboot, and computer will start with Ubuntu grub menu.

---

### Post by Odyssey1942 on 2018-11-21
Dennis, Big thank you. Again you have nailed it. 

And thanks for all the previous input from Dennis and TheFu

Back to where I was on Monday morning. Marking this solved and now returning to the thread:

[HTML]https://ubuntuforums.org/showthread.php?t=2406098&page=5[/HTML]

---

