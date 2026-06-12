---
title: "cannot resume from suspend"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by mikecicc on 2008-01-14
I just recently installed Ubuntu 7.10 on my Gateway 4540GZ. The laptop is about ~3 years and it runs very well.

After redoing my system with linux, i had to do a little work to get my WiFi card & sound working, but it was pretty simple. However i am having much trouble getting my computer to resume from standby. The system will suspend on command, using the hotkey or through the OS's quit menu. The problem is when i attempt to recover from suspend, the computer is halted at a blackscreen. At first i was under the impression it was just a problem with the onboard video card/ generic drivers and such. so after some research i came up that this is a common problem with installing ubunutu on certain notebooks, and the resolution involved tweaking settings within the '/etc/default/acpi-support' file

no after trying almost every different combination of settings in this file, suspend still does not work, at this point my computer is completed halted, I've tried to ping the machine while its halted at the blackscreen, i get no response, i also tried to use the caps lock key to see if the computers LED will light up, but it doesn't. So now I'm under the impression the entire Suspend to RAM does not work on my system. I am going to revert my acpi-support file back to its default settings and attempt to recover from suspend, while preforming the same ping and caps lock tests (in attempt to pinpoint the problem is with my system recovering or the video being redisplayed)

I've also tried to disable the ACPI power management, enabling the older APM power management which apparently will give you much better functionality and works with older machines (which was a desperation move, i feel my system's hardware should support ACPI power management, is there any way I can confirm this ?). Here's step by step on how I did it.

1) Added 'noacpi acpi=off apm=on nolapic' to my kernel options in /boot/grub/menu.lst
i.e. Code:
Searched for the line that looks like 'kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash'
added 'noacpi acpi=off apm=on nolapic' (i've also tried noapic in replace of nolapic) to the end of that line.
Saved.

2) Added 'apm' to /etc/modules
i.e. Code:
sudo gedit /etc/modules
Added 'apm' (no quotes)
Save.

3) Created a file in /etc/modprobe.d (/etc/modprobe.d/power) and added the following:
'options apm power_off=1 realmode_power_off=1' (no quotes)
Saved.

4) Rebooted the system

Now my system just fails to suspend, so this method apparently doesn't work. Does anyone have any suggestions/solutions ? I can provide any hardware spec's or anything we need to get this working, I'm fairly new to linux and am liking/would like to keep ubuntu very much, But I definately require a suspend in my system.

Thanks in advance !!!

P.S. I've read forums where this issue has been resolved with the latest Kernal update, I'm assuming my kernal is updated automatically, how can i confirm that i am using the most up to date kernal, and how i can update this through a GUI or command prompt, apparently YUM doesnt work in Ubuntu.

---

### Post by balak on 2008-03-22
Are you using any restricted modules? (graphics/network card drivers).

Can you try the method given in here:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

to figure out which module may be the culprit

then you can search for a solution in the forums or google.

---

