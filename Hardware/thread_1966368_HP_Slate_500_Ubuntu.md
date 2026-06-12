---
title: "HP Slate 500 Ubuntu"
date: 2012-04-27
forum: Hardware
---

### Post by Crucias on 2012-04-27
Hey all, I know I am Necro-ing this thread, however there isn't much point in making a new one since this is completely on topic.

[SIZE="4"]**Ubuntu 12.04 Installation**[/SIZE]

So I popped in the 32bit LiveUSB and too my surprise it ran first time (11.10 the graphics drivers were not on the liveCD) so I promptly navigated past the annoying half screen bug to hit "Try Ubuntu", which to my joy fixed the screen. This bug I mention is where only the top half of the screen is the display, but the whole screen works with the pen (and touch), this makes for some trippy navigation.

You'll have to fiddle with OnBoard (the keyboard) to make it appear automatically when you touch into a text field and use the pen to enlarge it (drag the edges).

**What Works Out The Box?**
[LIST]
[*]Touch - Single Point
[*]Pen - inc Pen button (for right click)
[*]Graphics - Kinda, see UPDATE 2
[*]Sound
[*]Wi-Fi - after activating propriety drivers
[*]Bluetooth
[/LIST]

It's installing right now, so when it's done I'll report back on more tweaking. I'm installing Tri-Boot with Windows 8 and Android x86 ICS

UPDATE 1: Android isn't in Grub
UPDATE 2: Black screen of death at login, working on it

---

### Post by lisati on 2012-04-27
Moved to own thread from [http://ubuntuforums.org/showthread.php?t=1603301](http://ubuntuforums.org/showthread.php?t=1603301)

---

### Post by Crucias on 2012-04-27
Attempting to fix UPDATE 2: Black screen of (login) Death

To fix this you need to do the following procedure (plug in a keyboard).

[LIST=1]
[*]Boot "Recovery Mode"
[*]Select option "failsafeX"
[*]Select option "Resume" when back in the same menu as before
[*]Open Terminal (Cont+Alt+T)
[*]Type "sudo gedit /etc/default/grub"
[*]Add the following under GRUB_CMDLINE_LINUX_DEFAULT=....
[LIST=1]
[*]GRUB_CMDLINE_LINUX="console=tty1"
[*]GRUB_CMDLINE_LINUX="mem=1920mb"
[/LIST]
[*]Now save and close it
[*]Type "sudo update-grub" in Terminal
[*]Now run Update Manager and update everything
[/LIST]

Still a WIP

---

