---
title: "battery percentage notification status"
date: 2010-11-30
forum: Hardware
---

### Post by t1m3 on 2010-11-30
solution:
- instead of the 'acpi=off', use the 'nolapic' or 'noapic' command.  I use 'nolapic'.
- acpi stands for advanced control, power interface. you need the acpi to see your battery.

my setup: asus f50sv (laptop)

try it:
- when the computer boots, select a kernel with 'e' to edit and right before it says 'quiet splash' type 'nolapic'.
- hit 'ctrl-x' to boot.
If it's a successful boot then you know this option will work for you.
If not try another one of these commands.

tweak:
Consider adding it to startup script so you don't need to type it every time.  That's fairly technical, ask someone with a lot of computer experience to help you. I don't really want to get into it but basically you need to edit your /ect/default/grub file (or do what I did and even though it tells you not to, carefully configure your boot/grub/grub.cfg file directly..).

this also resolved:
- I am now able to adjust my screens brightness.
- When i select shutdown off the panel, I no longer need to press the power button as well.

LINUX IS WORKING PERFECTLY NOW :DDD so stoked. i was a little leery to recommend this to people at first (although I was very impressed with how stable Linux had become), now with these issues cleared up I can knowing they'll be fine.  THIS SHOULD BE STICKIED.

---

