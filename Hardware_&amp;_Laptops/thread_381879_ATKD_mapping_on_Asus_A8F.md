---
title: "ATKD mapping on Asus A8F"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by thesoothsayer on 2007-03-11
Hi,

I have an Asus A8F and I'm wondering if anyone has got the brightness up/down function hotkeys to work?

The symbol on my keyboard shows F5 to be the key to increase the brightness, while F6 is supposed to decrease it. However, /etc/acpi/events does not have any events to turn on or off the brightness on an Asus laptop.

Also, when I used acpi_listen, Fn+F6 does not show any event being captured while Fn+F5 seems to change on certain conditions. At first, Fn+F5 gave an ATKD of 22. So, I created my own event and scripts and replaced Fn+F6 with Fn+F4 after removing the original Fn+F4(51/Internet) event.

Pressing Fn+F4 seemed to give a constant value of 51 but Fn+F5 suddenly changed to a mapping of 20 for the ATKD. So, I changed the mapping to 20 in the event handler. Fn+F5 then worked for the first keypress, after which, its mapping changed to 21 and stayed at 21.

So my questions are these:
1. Is there anyone who knows the behaviour of the Fn+F5 mapping and why it changes?
2. Is there anyone who knows how to get Fn+F6 to return an ATKD event?
3. Is there a way to create an event which captures a range of ATKD values (eg. "event=hotkey ATKD 00000020 - XXX")?

Thanks!

---

### Post by thesoothsayer on 2007-03-11
Figured out for Fn+F5 works. The last hexadecimal value reflects the current brightness value in /proc/acpi/asus/brn

Also, found out how to set the hotkeys for multiple events
event=hotkey ATKD 0000002.*

However, I would still appreciate it if someone could tell me how to get a ATKD reading from Fn+F6.

Thanks.

---

