---
title: "Macbook external keyboard woes"
date: 2009-03-06
forum: Hardware
---

### Post by corydodt on 2009-03-06
I had a perfectly-working keyboard setup on my macbook pro 3.1 and now I have several issues when I plug in an external keyboard after upgrading Hardy->Intrepid.

**1)** "Pointer can be controlled using the keypad" turns itself off when unplugging.  This setting is found in System>Preferences>Keyboard>Mouse Keys.  It *must* be turned on for my setup to work - the macbook only has one mouse button, so I have mapped two keyboard keys, right option and lower enter to middle click and right click, respectively.  I did this with xmodmap (below).  They stop working when I unplug the external USB keyboard, because this checkbox toggles itself off every time I do that.

When I navigate there and turn it back on, they work again.


**2)** Super key on the external does not work, even though keysyms are correct.  It works on the builtin keyboard. . . *unless* I mess with anything in layout or xmodmap, in which case it stops working and won't turn back on again.  This is usually accompanied by an XKB error message like the one [here]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/67188").


_Debugging_

The laptop's builtin keyboard displays this when I run xev and press left option (I have win keys mapped to Super).

KeyPress event, serial 30, synthetic NO, window 0x5200001,
    root 0x13b, subw 0x0, time 344569374, (347,802), root:(479,825),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

The external keyboard also displays EXACTLY the same thing when I press the left option key there.

I have the layout set to "Macbook/Macbook Pro", with the layout list containing "USA Macbook" and the default circle is NOT filled in (some people seem to think this matters, but I can't see why).   "Super is mapped to the win keys", and this xmodmap:

clear lock
keycode 104 = Pointer_Button3
keycode 133 = Super_L
keycode 134 = Pointer_Button2

"lshw" reports this for the external keyboard:
              *-usb
                   description: Keyboard
                   product: Bluetooth HCI MacBookPro (HID mode)
                   vendor: Apple, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 19.65
                   capabilities: usb-2.00
                   configuration: driver=usbhid speed=12.0MB/s


Happy to provide any other debugging info you gurus might need.

---

