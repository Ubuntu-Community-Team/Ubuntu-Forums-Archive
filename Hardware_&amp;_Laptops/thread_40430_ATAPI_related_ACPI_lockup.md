---
title: "ATAPI related ACPI lockup"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by NRios on 2005-06-09
Hi there!

I've got a no-name Centrino laptop running Hoary and works fine for a few hours, then locks up totally. The lockup is total, and there is no further response to keyboard or network; it wont respond to ssh or ping back; it will not shut down with a short push of the power bottom.

With "acpi=off noapic" the system does not crash, but it runs hot, and it exhausts through the battery really fast, without feedback as to its state. Maybe there's an intermediate solution: after all, it DOES run with ACPI for hours at a time before it crashes, and then it always crashes with the same messages: see.

With the system recently booted, the last lines in /var/log/kern.log say;
[INDENT][COLOR=Blue]
Jun 7 22:24:48 localhost kernel: speedstep-centrino: invalid ACPI data
Jun 7 22:24:51 localhost kernel: eth0: no IPv6 routers present
[/COLOR][/INDENT]
After the system has locked up and then restarted, you can see these lines have been added right before the crash:
[INDENT][COLOR=Blue]
Jun 8 00:02:11 localhost kernel: hdd: irq timeout: status=0xd0 { Busy }
Jun 8 00:02:11 localhost kernel: hdd: irq timeout: error=0x00
Jun 8 00:02:41 localhost kernel: hdd: ATAPI reset timed-out, status=0x80
Jun 8 00:02:46 localhost kernel: ide1: reset: master: error (0x00?)
Jun 8 00:02:46 localhost kernel: hdd: status timeout: status=0x80 { Busy }
Jun 8 00:02:46 localhost kernel: hdd: status timeout: error=0x01IllegalLengthIndication
Jun 8 00:02:46 localhost kernel: hdd: drive not ready for command
Jun 8 00:03:16 localhost kernel: hdd: ATAPI reset timed-out, status=0x80
[/COLOR][/INDENT]
And then a new set of messages is appended on reboot, starting with
[INDENT][COLOR=Blue]
Jun 8 00:45:54 localhost kernel: Inspecting /boot/System.map-2.6.10-5-686
Jun 8 00:45:54 localhost kernel: Loaded 26806 symbols from /boot/System.map-2.6.10-5-686.
Jun 8 00:45:54 localhost kernel: Symbols match kernel version 2.6.10.
[/COLOR][/INDENT]
This has happenned time after time, with different time spans between boot and crash. While working, the system seems to run fine, including the ATAPI DVD/CDR combo which reads and writes OK.

I have to add that I have tried Ubuntu's 2.6.11 kernel, and though it boots to gdm, and almost starts gnome, it locks before it paints a single icon on screen (right after it's drawn empty top and bottom panels)

Any idea what is this?

Thanx,

-Nacho-

---

### Post by NRios on 2005-06-15
Due to the seemingly random length of time until the system crashes, I thought it might have something to do with the screensavers (which are chosen randomly), maybe OpenGL.

I tried to deactivate the screensaver, but no chance: the computer froze after 2hr 20min with the same messages about ATAPI.

Anybody out there also having trouble with ACPI and ATAPI?

Thanks, 

-Nacho-

---

### Post by NRios on 2005-06-18
Hello again!

A nasty trend of being the only one who responds to my own messages seems to be developing!  But maybe there's life out there, and someone's reading, so I'll continue my tale, to keep the thread alive ;-)

So, out of frustration that nobody answers my pleas for help, I blasted the whole Ubuntu out of my portable and installed the shiny new Fedora Core 6. After all, at more than two months old, Ubuntu was starting to feel obsolescent. And I really hoped that kernel 2.6.11 would help. The experience has showed that:

* Anaconda looks nice, but really does nothing in a better way, or more easily than Ubuntu's installer

* In fact, Fedora decided that the Centrino wireless network adapter was in fact a wired ethernet adapter, and I couldn't figure how to make it work as WiFi, so I had no way to configure the ESSID or the WEP key.

* Fedora's package manager does not let you search for a package, nor does it present a simple sorted list, which makes it tremendously inconvenient, especially when you have to laboriously scan every software cathegory trying to find something that is actually not there.

* ¡FEDORA CORE 6 FREEZES ON MY LAPTOP JUST LIKE UBUNTU!

So, Ubuntu is back, and I am none the happier.

I'm going to download Knoppix to see how I fare.

-Nacho-

---

