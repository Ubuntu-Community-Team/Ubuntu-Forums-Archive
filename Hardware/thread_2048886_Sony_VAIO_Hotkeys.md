---
title: "Sony VAIO Hotkeys"
date: 2012-08-27
forum: Hardware
---

### Post by thesimsone on 2012-08-27
Hello everyone,
I need some help in order to make my Sony VGN-A617B laptop's Hotkeys working. There are 3 useful keys (mute, volume up, volume down) that I would like to use but they don't seem to be recognized. They seem to be an ACPI device but when I do acpi_listen, only the mute button  appears. Problem 1: do you know why the other keys don't seem to be recognized? What can I do to fix that? 
The mute button events are caught by the kernel but when I do xev, there is nothing when I press the mute button. So I tried to manually trigger an event with acpid through acpi_fakekey (my script executes acpi_fakekey 113). The problem now is that the mute function works but after that I press a second key (whatever) on my keyboard after the mute button, which is not comfortable... Problem 2: do you know how to fix that?
Thank you!

---

