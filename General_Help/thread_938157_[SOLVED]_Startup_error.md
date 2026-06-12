---
title: "[SOLVED] Startup error"
date: 2008-10-04
forum: General Help
---

### Post by Chamillionaire2 on 2008-10-04
Hello,

ok after installed ubuntu and had it working for a month and being very pleased with it over windows. however on a restart i got this ubuntu logo screen with loading bar for 2 -3 secs then a balck screen with the wrting of

Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) Built in shell (ash) Enter 'help' for a list of built-commands

(initramfs) [   94.818732] sd 6:0:0:0: [sdf] Assuming drive cache: write through [   94.818732] sd 6:0:0:0: [sdf] Assuming drive cache: write through
___________________________________________________________________

anyone know what todo?

---

### Post by jmszr on 2008-10-04
The first one has worked for me though I didn't have the part of your message after (initramfs). Worth a try though.

This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

---

### Post by Chamillionaire2 on 2008-10-05
> **jmszr said:**
> The first one has worked for me though I didn't have the part of your message after (initramfs). Worth a try though.

This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

Thanks alot :) i used the first option and now its back to its working self.

Thanks alot jmszr

---

### Post by Dalston on 2008-10-05
Thanks that helped alot,  although like the person said above I didnt need to do step 2.

---

