---
title: "How to remove GRUB and get it back later again"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by kamlesh30rao on 2009-03-03
Here's my current setup:

- Installed XP
- Installed Windows 7 Beta
(Multi-boot menu appears to choose Win7 or XP
- Installed Ubuntu 8.10 and added GRUB
(Multi-boot menu starts from Unbuntu)

Now, I need to remove Ubuntu GRUB, go back to Windows Boot Menu.
Then, replace Windows 7 with Windows 2003 Server.

And later again bring back Ubuntu GRUB menu without reinstalling it.

Not sure if this will work?  Any suggestions?

My new multi boot should have the existing Ubuntu with XP and Win 2003.

---

### Post by cariboo on 2009-03-03
You don't have to remove grub to install another operating system, although I have to ask why install a server version on a triple boot system. Just install the OS like you normally would, then restore grub using this [howto]("http://ubuntuforums.org/showthread.php?t=224351").

You will have to remove Windows 7 from C:\boot.ini

Jim

---

### Post by kamlesh30rao on 2009-03-07
Jim, thanks for your inputs it worked.  Somehow, it automatically replaced Windows 7 and I didn't had to manually edit the boot.ini file.

For the benefit of others, I used the below steps:

1) Booted my PC into XP and ran Windows 2003 setup.  During the setup, choosed the Windows 7 partition(D: drive).  Choosed the quick format option.
2) After Win 2003 setup, my GRUB got lost and I started directly getting the Windows Multi-boot menu (XP and 2003).
3) Followed the steps in the [thread]("http://ubuntuforums.org/showthread.php?t=224351") shared b Jim.

My GRUB returned back.  Now I am able to boot Ubuntu, WinXP and Win 2003.

Once again Thanks to Jim.

---

