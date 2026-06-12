---
title: "clean installed Ubuntu won't shutdown"
date: 2008-07-25
forum: General Help
---

### Post by sunshine12 on 2008-07-25
Clean Installed Ubuntu and it won't shutdown, screen hangs on at the final ubuntu logo screen, the progress bar decreases and ultimately disappears but It won't power off and I have to manually do it.

Dual boot with ubuntu and xp and Having same problem with win XP Pro.. in that it says "windows is shutting down" and mouse and screen hangs(stuck)

Please suggest some solution, it is affecting both ubuntu and xp in same manner.. 

Thanks

---

### Post by Krupski on 2008-07-25
> **sunshine12 said:**
> Clean Installed Ubuntu and it won't shutdown, screen hangs on at the final ubuntu logo screen, the progress bar decreases and ultimately disappears but It won't power off and I have to manually do it.

Dual boot with ubuntu and xp and Having same problem with win XP Pro.. in that it says "windows is shutting down" and mouse and screen hangs(stuck)

Please suggest some solution, it is affecting both ubuntu and xp in same manner.. 

Thanks

Try ctrl-alt-delete. If the OS is still running, that will send a shutdown signal to all the processes and shut off (or reboot) the computer.

**Of course, [COLOR="Red"]only do this as a _last resort_ if the shutdown sequence is stuck and you have no other choice.[/COLOR] Ctrl-alt-delete in the middle of a running session MAY mess up your OS.**

---

### Post by coffeecat on 2008-07-25
> **sunshine12 said:**
>  it is affecting both ubuntu and xp in same manner.. 

Then it must be a hardware issue. Has Windows only recently started doing this?

Check in your BIOS. There may be something there that needs changing.

---

### Post by jimv on 2008-07-25
It could be an ACPI issue.  My machine was doing the same thing recently until I repaired the DSDT file.

A way to check if ACPI is your problem is to add "ACPI=off" to the end of the kernel line in /boot/grub/menu.list.  That will boot the machine with ACPI disabled, then you can try shutting down to see if it actually powers off.

---

### Post by sunshine12 on 2008-07-25
Done that.. My computer has ACPI, no APM.. In BIOS in power option there are two thing 
APM
ACPI

in APM, 2 options either Enable/Disable
in ACPI, nothing like that, only enabled..

Tried enable/disable APM, but won't help

I didn't changed anything in BIOS, then why this problem arises now?? Using xp and ubuntu since long time.. this is quite new problem to me, gone through various forums and solutions still problem persists..

Thanks for the reply and please suggest some more solutions.. I really need to sort this out.. Restart is working fine..

Thanks

---

### Post by sunshine12 on 2008-07-26
Updated BIOS to latest version.. still **problem PERSISTS**

What damage it could do if I manually turn off the computer in this case?? please give some more suggestions.. 

Thanks

---

### Post by stevoo on 2008-07-26
try pressing and holding down
ctrl+sysRg
and press
R + S + E + I + U + S ( i think it is S, B will restart. We dont want that)
 
Also check the logs as well. IN System -> Administration ->  System Logs
and see if something is wrong during shutdown.

---

### Post by sunshine12 on 2008-07-28
Can't understand the first thing ctrl+sysRg.. when to press and what is R + S + E + I + U + S??

System log at the end is..

Jul 27 14:02:58 admin-desktop -- MARK --
Jul 27 14:13:54 admin-desktop kernel: [ 1975.168580] gdm[5094]: segfault at 6e61745f eip b76b8e66 esp bfdec118 error 4
Jul 27 14:13:56 admin-desktop kernel: [ 1976.645562] ^Idriver to use reclaim_buffers_idlelocked() instead.
Jul 27 14:13:56 admin-desktop kernel: [ 1976.645566] ^II will go on reclaiming the buffers anyway.
Jul 27 14:13:56 admin-desktop kernel: [ 1976.774117] [drm] DMA Cleanup
Jul 27 14:13:57 admin-desktop kernel: [ 1977.868812] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 27 14:13:59 admin-desktop exiting on signal 15

---

### Post by sunshine12 on 2008-07-29
Upgraded to Latest version of the BIOS, problem still persists..

My system info:

Intel Pentium III 933MHz
Desktop Board : D815EEA2
384 MB SD RAM
OSs: Windows XP Pro and Ubuntu 8.04
Samsung samtron 55v monitor 15"
Graphic card: Intel 82815 graphic controller
ACPI Power Controll
C-Media PCI CM8738 4 channel soundcard
Realtech Ethernet controller (Hanghaou silan microchip)
160GB Seagate HDD, on slave/master (I really don't know, but it is between the cable)

Everything was working fine, but don't know when the real problem started? Clean install didn't help.. other solutions like enable APM and other solutions from Device manager is not there in the options (there is only ACPI)
No Driver conflicts

Please let me know if any other information is required.

Thanks

---

### Post by CatKiller on 2008-07-29
> **sunshine12 said:**
> What damage it could do if I manually turn off the computer in this case?? please give some more suggestions.

Well, the computer has already shut down. It's just the automatic power control that doesn't work. So no, you won't cause any damage.

Did you try editing your GRUB options as jimv suggested?

---

### Post by sunshine12 on 2008-07-29
Edited Grub, Problem is still there!!!

---

### Post by Potatoj316 on 2008-07-29
try putting acpt=force at the end of your grub entry.

post your /bott/grub/menu.lst, I can assist

---

### Post by sunshine12 on 2008-08-04
It seems I can't solve this problem, whatever I tried.. don't know what to do?

Thanks for the help, I don't know what to do to solve this problem now..

---

### Post by /////// on 2008-08-04
Have you been bumping around with the inside of  your computer lately? Like maybe you opened it to clean the dust and maybe hit something on the motherboard?

---

### Post by sunshine12 on 2008-08-10
Problem still Persists..

When shutting down from ubuntu safe mode, the following message appears..


"Network Manager: <warn> nm_hal_definit():
libhal shutdown failed
did not received a reply
Possible causes include:
The remote app. did not send a reply
The message bus security policy blocked the reply
The reply timeout expired
or the network connection was broken
[751,408281] power down"

thanks

---

