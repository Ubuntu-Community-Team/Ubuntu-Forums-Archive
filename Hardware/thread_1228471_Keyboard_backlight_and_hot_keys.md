---
title: "Keyboard backlight and hot keys??"
date: 2009-07-31
forum: Hardware
---

### Post by zrs on 2009-07-31
ASUS Laptop model UX50V

I just ripped vista off my new laptop and am using ubuntu, and am extremely happy with the kernel so far! 

Although, the only issue I'm having is the laptop came with a brilliant keyboard backlight that I want to use, and it has hot keys associated with; but ubuntu linux doesn't recognize it. Additionally, other hot keys are not functioning.

Any ideas on how to set it up so I can use the backlight?

Thanks everyone!

---

### Post by pleb989 on 2009-08-20
I have the same problem on Karmic.

Ideas anyone??

---

### Post by IcarusR on 2009-08-21
I googled "Hotkeys Ubuntu" & the third result was this [https://wiki.ubuntu.com/Hotkeys]("https://wiki.ubuntu.com/Hotkeys")
You could also search the forum, this has been asked before.

---

### Post by pleb989 on 2009-08-21
> **IcarusR said:**
> I googled &quot;Hotkeys Ubuntu&quot; & the third result was this [https://wiki.ubuntu.com/Hotkeys](https://wiki.ubuntu.com/Hotkeys)
You could also search the forum, this has been asked before.

  Ok i looked into it a bit further and i am getting acpi events on the key presses for the keyboard illumination keys when running 'cat /proc/acpi/event' but i don't get any key press events after running 'sudo /lib/udev/keymap -i input/event4'.   [https://wiki.ubuntu.com/Hotkeys/Architecture](https://wiki.ubuntu.com/Hotkeys/Architecture) says the following;  'If a key generates an ACPI event but not a keypress, then the kernel needs to implement a platform-specific kernel ACPI driver that translates these ACPI events to input events on a dedicated input device (e.g., thinkpad_acpi).'  Does this mean i'm unlikely to be able to fix this myself?

---

### Post by Nobody2989 on 2009-09-05
Hey zrs, I have the same model Asus, nuked Vista, and tried putting Jackelope on there. But I couldn't get the Nvidea video graphics card to work with the os. Whenever I tried to activate the card in place of the integrated one, it would **** a brick. Were you able to work around this problem? I also tried at first to disable the hybird SLI with the video card in IGP, and evidentatly Asus has nuetered the Bios. Any suggestions?

---

### Post by alduc1 on 2009-11-19
probably it could help you, see (in french sorry) : [http://forum.ubuntu-fr.org/viewtopic.php?id=340024]("http://forum.ubuntu-fr.org/viewtopic.php?id=340024")

---

### Post by PantsOnFire on 2009-12-14
> **Nobody2989 said:**
> Hey zrs, I have the same model Asus, nuked Vista, and tried putting Jackelope on there. But I couldn't get the Nvidea video graphics card to work with the os. Whenever I tried to activate the card in place of the integrated one, it would **** a brick. Were you able to work around this problem? I also tried at first to disable the hybird SLI with the video card in IGP, and evidentatly Asus has nuetered the Bios. Any suggestions?


I am having the same hell here trying to get the nvidia card to work. have tried everything I can find and it bricks everytime and I have to do a fresh install to fix it back to the integrated graphics. So frustrating that the nvidia card just sits there unused and dormant.

:(

---

### Post by FLOZz on 2010-10-28
Maybe this ?
[https://launchpad.net/asus-keyboard-backlight](https://launchpad.net/asus-keyboard-backlight)

---

