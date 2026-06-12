---
title: "Microsoft Wireless Mouse TOO SENSITIVE"
date: 2011-07-30
forum: Hardware
---

### Post by joshgura on 2011-07-30
wow the text is soooo small in this editor...

Ok, I have a MS wireless 3000 keyboard and mouse.  The mouse is way too sensitive even with the mouse settings on lowest and slowest.  1000 pixels per inch just about.

I have looked at other pages that describe how to add a deceleration factor.  The only problem is there is no syntax offered when i get Ubuntu's response to my command.

my command:
 xinput --set-prop "Microsoft Microsoft® 2.4GHz Transceiver v6.0" "Device Accel Constant Deceleration" 5

Ubuntu's response:
Warning: There are multiple devices matching 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'.  To ensure the correct one is selected, please use the device ID, or prefix the device name with 'pointer:' or 'keyboard:' as appropriate.

but look at this mess:

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0    id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® 2.4GHz Transceiver v6.0    id=8    [slave  keyboard (3)]

I am suffering from pain due to the mouse being overly sensitive.  please help.

what am i supposed to do now?  what can Ubuntu do to eliminate this sort of problem?

---

