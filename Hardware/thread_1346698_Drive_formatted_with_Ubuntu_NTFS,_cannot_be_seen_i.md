---
title: "Drive formatted with Ubuntu NTFS, cannot be seen in XP"
date: 2009-12-05
forum: Hardware
---

### Post by Elvis99 on 2009-12-05
Hi everybody,

I'm using Ubuntu 9.04 on my Dell Mini 10v netbook and XP on my PC. I have an external 400 GB HHD, that I have formatted with NTFS while it was connected via USB to my Netbook. When I plug it in on my PC, it won't show up in explorer. I hear the "dingdong" of an USB device being attached, an strangely I can eject the drive with the "safely remove hardware" option, but it simply won't show up in XP. Can someone help me please?

thank you,

E

---

### Post by coffeecat on 2009-12-05
If the drive is sufficiently recognised by Windows that you can "safely remove" it, does the safely remove utility show a drive letter? E:, F:, G:, whatever? You say that it doesn't show up in Explorer. Does that include not showing up in "My Computer"?

If it has been allocated a drive letter, but doesn't appear in My Computer, have you tried from a command prompt? Sorry, my ms-dos skills are rusty and I'm posting from Ubuntu, but assuming the disk has been allocated the drive letter G:, try this at the command prompt:

```
G:
```Does the prompt change to a 'G' one? If so, try:

```
dir
```(If I'm remembering correctly.) Does this show the Windows equivalent of 'ls' and is there something there?

The only other thing I can suggest, and this will only work if it being allocated a drive letter, is to run chkdsk. You can do this from a command prompt if the GUI is not showing the drive. [Microsoft page on chkdsk in XP]("http://support.microsoft.com/kb/315265").

---

