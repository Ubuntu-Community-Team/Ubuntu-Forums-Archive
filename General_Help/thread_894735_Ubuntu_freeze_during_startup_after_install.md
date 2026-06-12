---
title: "Ubuntu freeze during startup after install"
date: 2008-08-19
forum: General Help
---

### Post by ecv on 2008-08-19
Hi,
For some time I have wanted to try to install linux. So yesterday I got hold of the 8.04 Ubuntu install cd and today i decided to go for it.

I went with the "Install inside windows" option, just to try out first. The installer ran and after it finished i rebooted and choice the "ubuntu" option from the startup menu.

Unfortunately the joy of the simplicity of the process ended there, since the startup process froze when the startup bar was filling at around 4/5 full.

Then i tried to restart ubuntu in both the graphic and acpi safe mode. In both cases the startup process ended with this message (more or less) on the screen:

... start_kernel + 0x31f/0x3b0
... unknown_boot option + 0x0/0x1e0
=======================
... Code ec 83 c8 .... < 3 lines of hexadecimals >
... kernel panic - not syncing: fatal exception in interrupt

I also tried to simply run it from the cdrom, but here it froze during startup as well.

Any help would be appreciated. Thanks in advance.

---

### Post by prince_niceguy on 2008-08-19
Can you do a check on the cd to see if the cd is corrupt copy or something?

---

### Post by ubguess on 2008-08-19
Experienced the same error, redownload and/or reburn the image - this will solve it.

---

