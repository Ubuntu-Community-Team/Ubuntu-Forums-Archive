---
title: "HP Chromebook 14 -- Two Beeps"
date: 2016-06-04
forum: Hardware
---

### Post by teejay17 on 2016-06-04
Hello,
I've recently installed Ubuntu on an Acer Chromebook C720P successfully, following the directives quoted below. Everything works, including the touchscreen. When I try to install on a different Chromebook, an HP Chromebook 14, following the same directives, I get two beeps when I press the final CTRL - L. For some reason I can't boot into SeaBios. Instead I get two audible beeps.
Would anyone know of a solution or work-around? 

The method I followed: 
> [U][B]1. Put the Chromebook into developer mode by holding down "ESC" and "Refresh" while powering on.

2. Press Ctrl+D and then press Enter. If you see a message about OS verification being off press CTRL + D again

3. Boot into ChromeOS (You will need to press Ctrl + D at the boot screen)

4. Press Ctrl + Alt + T to bring up a chrosh
[/B][/U]
_**5. Enter the Shell**_
shell [U][B]
6. Elevate privileges with sudo[/B][/U]
sudo bash 
_**7. Configure the system to boot from USB devices.**_
crossystem dev_boot_usb=1 dev_boot_legacy=1 [U][B]

8. Reboot the computer


9. Insert the USB installer media and turn the computer on

[/B][/U][U][B]
10. Press Ctrl + L to boot SeaBios[/B][/U]

---

