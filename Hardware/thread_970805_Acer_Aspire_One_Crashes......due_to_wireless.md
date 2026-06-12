---
title: "Acer Aspire One Crashes......due to wireless?"
date: 2008-11-04
forum: Hardware
---

### Post by Trafalger61 on 2008-11-04
I just installed Ubuntu 8.04 on my Acer Aspire One (AAO). Whenever I try to do anything on the internet, the AAO locks up and I have to reboot.  Even messing with the wireless settings crashes it.  The screen, keyboard, and mouse lock up, and the Caps Lock light slowly flashes. Any ideas?  I've also noticed that the Wireless LED blinks rather frantically, while as in XP it's a much slower flashing.  I'm using NDiswrapper, and not sure of the driver, I'll post it if you think you'll need it.

            thanks in advance!
                          -trafalger

---

### Post by nixscripter on 2008-11-04
The caps lock light flashing is a sign of a kernel panic.

Either it's a buggy driver, or there might be something else at work. Try a workaround to see if it's a power management problem:

1. Reboot. When it says "GRUB Loading stage 2...1...0" Hit escape.
2. At the menu, make sure the first line is selected, hit 'e' to edit.
3. Select the long line that says "kernel", hit 'e' to edit.
4. Scroll to the end of that line, and add **acpi=off** after a space.
5. Hit enter to save, and 'b' to boot.

Now try messing with settings again. Does it lock up?

---

