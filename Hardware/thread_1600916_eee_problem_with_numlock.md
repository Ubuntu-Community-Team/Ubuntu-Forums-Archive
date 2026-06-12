---
title: "eee problem with numlock"
date: 2010-10-19
forum: Hardware
---

### Post by chaemil on 2010-10-19
hi. ive just applied this "patch" to my eee 900A with lucid lynx desktop edition...

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

and after restart i'm not able to type the numeric symbols with the FN plus numerickey...

so im not abble to type numbers, plus, start and soime other symbols.

PS im ussing the czech keyboard....

---

### Post by ThatBum on 2010-10-19
When I had Lucid on me Eee, I got all my hotkeys working by putting a kernel parameter in GRUB.

Go and edit /etc/default/grub with "sudo gedit /etc/default/grub".

Fine the line that starts with "GRUB_CMDLINE_LINUX_DEFAULT=" There should be something like "quiet splash" after it. Put "acpi_osi=Linux" anywhere in it, e.g. "acpi_osi=Linux quiet splash" and save it. This parameter tells the BIOS what OS is running.

Now run "sudo update-grub". This applies changes. Now reboot.

I didn't have any problem with my numlock, but it got all my other Fn keys working, like volume up/down/mute, wireless toggle, etc.

By the way, if this doesn't work, you can upgrade to Maverick. Maverick now has native support for Intel acceleration, because it has kernel 2.6.25, which is what you put on your Lucid through a PPA. So yeah.

---

### Post by chaemil on 2010-10-19
thanks i will try this but i already have maverick on my eee installed and it was so slow and buggy so i have decided to put back the lucid...

EDIT: it wont work... everything is in the same state...

---

### Post by ThatBum on 2010-10-20
Maverick is buggy, you say? It works fine on my Eee 1015PED...I'm typing to you on it now. I donno.

Anyway, let's try to see if it detects the numlock press on the low-level end, and if it's a higher-level GUI-related thing.

Get a terminal and run "xev". This will detect all input that you put in, provided the "Event Tester" window is in focus. So do just that, and hit the combination for numlock, Fn-Insert I'm guessing.

If it finds the keypress, the terminal should output something like this as it detects it being pressed and released:

```
KeyPress event, serial 36, synthetic NO, window 0x7400001,
    root 0xaa, subw 0x0, time 15976832, (84,-7), root:(134,291),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 36, synthetic NO, window 0x7400001,
    atom 0x19a (XKLAVIER_STATE), time 15976847, state PropertyNewValue

KeyRelease event, serial 36, synthetic NO, window 0x7400001,
    root 0xaa, subw 0x0, time 15977081, (84,-7), root:(134,291),
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```Does it?

If it doesn't, you might want to see if it still works with the old kernel, which I assume you still have. Shutdown the computer, and hold Shift while it's starting. This will show you GRUB's menu and your installed kernels. The one that says "2.6.35-xx" is the one that was installed to get acceleration support. Run any other previous version and try it. If it works with the older kernel, you may have to stay with that one if you want your numlock to work, but you won't have acceleration. Or you can try Maverick again.

If it does, then I don't really know what to do next, as UI monkeying isn't really my forte. Maybe someone else can pick up on it.

---

### Post by chaemil on 2010-10-21
yes i have some output but nothing when i press fn + "+" or fn + *, but when press fn + some number on numeric keyboard it will show some output i used to type numbers like this bcs czech keyboard have this symbols: " &#283;š&#269;&#345;žýáíé"  up from the "qwertyuiop" instead of numbers... 

and if i start older kernel it will print my this.:

udevadm trigger is not permitted while udev is unconfigured

i think i will stay with the hw acceleration support and find how to type "*" and "+" some other way :D anyway thanks i've learned something interesting...

---

### Post by ThatBum on 2010-10-21
No problem.

On my Eee 1015, I can type a * or a + with Shift+8 and Shift+=, respectively, and 8 being the one on the horizontal numbers above the letters, or wherever they are on your keyboard...the primary ones. I think all the Eee keyboards function the same, so try that. Oh and I forgot you can't run an old kernel without reconfiguring udev, which I don't know how to do. Meh. I think it keeps the old ones for compatibility, or to keep the headers, or some kind of emergency fall-back if the new one fails, which shouldn't even be on Lucid.

Something here, all my keys work, but Scroll Lock. It's kind of a useless, vestigial key, but still. Weird, because xev sees it. It's not toggling because lock-keys-applet says it isn't. Oh well.

---

