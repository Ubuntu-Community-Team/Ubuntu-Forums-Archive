---
title: "Sony Memory Stick on 8.04"
date: 2008-07-17
forum: Hardware
---

### Post by pembo22 on 2008-07-17
I have a Sony Vaio laptop running ubuntu 8.04 and it does not seem to recognize my memory stick slot. It's an older laptop but I figured the new ubuntu would recognize it. Any help would be appreciated.

---

### Post by sergiom99 on 2008-07-18
Theres no linux support for MStick yet. they have to code the drivers for them.

Does the reader apear in the output of lspci ?
Post it here if you are not sure and will look at it.
Good luck.

---

### Post by pembo22 on 2008-07-18
No, the slot does not show on lspci. According to Windows the controller is Winbond and the only items that appear on lspci is the ATI graphics, USB controller and ethernet controller.

---

### Post by silkstone on 2008-07-18
This issue came up a while ago, and I'm afraid sergiom99's answer is correct - there is no support for Sony Memory Stick with **internal** card readers.

However, an external USB card reader will work perfectly with Sony MS!

Strange but true. :)

---

