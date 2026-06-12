---
title: "[SOLVED] Server installer only opens a dialog box with &amp;quot;Ok&amp;quot;"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by marmida on 2009-01-06
I am trying to install 8.10 server.  After it boots from the disc and I select a language, I am prompted with the main menu.  For any of the options I choose (excluding "Boot from local disk"), I get a dialog box in the center of the screen, containing only one word (e.g. 'install' or 'memtest'), and only one button labeled "Ok."  Selecting "ok" closes the dialog box.  The installer proceeds no further than this.

I've tried burning the disc at different speeds and using different programs, and have verified that the iso has the correct md5.

Is there a way to get more information about what the installer is doing or other next diagnostic steps?

---

### Post by marmida on 2009-01-09
Here's a photo of what the installer does when you select the "install" option.  It's a bit huge, sorry.

[http://dl.getdropbox.com/u/476602/boot.jpg](http://dl.getdropbox.com/u/476602/boot.jpg)

---

### Post by marmida on 2009-01-12
Figured this one out by chance:

[LIST]
[*]The box in question has a cheeseball Promise RAID controller.  Both drives were connected to this.
[*]Under the 8.04 version, the installer would start but then hit a kernel panic while trying to load Linux, because ACPI complained about the controller.
[*]Under the 8.10 version, the installer stops with the weirdness in the  aforementioned photo.
[*]Once the drives were moved to a different controller, both the 8.04 and 8.10 installers worked fine.[/LIST]

I will try to file this as a bug under the latest version of the installer.

---

