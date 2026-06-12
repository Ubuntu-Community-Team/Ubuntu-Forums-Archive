---
title: "AMD HD 6470M incompatible with Ubuntu!"
date: 2011-10-05
forum: Hardware
---

### Post by yazanki on 2011-10-05
Hello, i have a Dell Inspiron 14R-3060 with AMD Radeon HD 6470M, but is incompatible with Ubuntu and variants. Someone have a solution?

---

### Post by Redblade20XX on 2011-10-05
What do you mean incompatible?? Does the os loads the default open source ati drivers? A little bit more details needed! :P

-Red

---

### Post by begumgenc on 2011-10-06
hi, i have the same problem. i activated the graphics driver from additional drivers. however when i tried to run glxgears i got segmentation fault error. then i learned that there is no support for the card i am using, which is amd 6470m. there is also an integrated card in my laptop. 
Can anyone help me about installing the amd driver properly or using the integrated card instead of 6470m, please?

---

### Post by SeijiSensei on 2011-10-06
Does this computer have both an Intel and the ATI card?  A quick glance at Dell's page for the Inspiron 14R-3060 suggests it has both.  On an HP laptop I recently configured, I could upgrade the BIOS and force the ATI card on.  Then the Additional Drivers applet saw the card and installed the proprietary driver.

I suggest you start by reading this: [http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by begumgenc on 2011-10-06
i did all the steps in a and after i run the command lspci -vnnn | grep VGA 
i got:

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760] (rev ff) (prog-if ff)

and i still do not see a driver for intel in additional drivers. am i missing something?

---

