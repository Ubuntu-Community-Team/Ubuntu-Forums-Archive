---
title: "cd rom"
date: 2008-05-03
forum: Hardware
---

### Post by eletrixmike on 2008-05-03
any help my cd rom drive is not being recgonized by ubuntu

---

### Post by Aearenda on 2008-05-03
Perhaps a little more information would help get a useful reply....
Have you installed Ubuntu, or is this when you try to boot off the CD?
If the latter, what do you see on the screen? Any error messages? 
Does the CD drive start (does it make a noise)?
Does the CD drive work on other operating systems such as Windows?

---

### Post by dcroeser on 2008-05-03
I'm getting this problem as well. DVD drive is just absent. I installed Hardy from the very same drive so it seems strange that it would now not be able to recognise it.

---

### Post by Aearenda on 2008-05-04
[http://ubuntuforums.org/showthread.php?t=676909](http://ubuntuforums.org/showthread.php?t=676909) seems relevant, and gives a possible workaround, but it isn't very satisfactory really. To verify whether it applies, reboot with acpi=off added to the kernel line in Grub.

Here's how to add that option to GRUB for one boot only, at boot time:

When you see the 'Press ESC to enter menu' message, press ESC.
At the Grub menu, press 'e'.
Use the cursor keys to move the highlighting down to the 'kernel' line shown, and press 'e' again.
Move to the end of the line, add a space if necessary, then add 'acpi=off' (without the quotes).
Press <ENTER> to complete the edit, and then press 'b' to boot.

The system will then start up, and you should be able to see the extra drive. This isn't a good permanent solution for modern PCs, however.

---

