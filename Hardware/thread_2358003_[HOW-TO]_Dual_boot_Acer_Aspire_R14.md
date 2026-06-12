---
title: "[HOW-TO] Dual boot Acer Aspire R14"
date: 2017-04-08
forum: Hardware
---

### Post by amp_man on 2017-04-08
This probably also applies to other Acer models using InsydeH2O BIOS. After much messing around, this is how I got dual boot working on my Acer Aspire R14-471T:

1) Update to the latest BIOS (I know, it's UEFI, but I'm going to call it a BIOS). My new laptop shipped with 1.07, 1.10 is the latest as of this posting.
2) Shut down, then while starting back up hit the F2 button many times until the BIOS Setup Utility loads.
3) In the "Main" menu, set the "F12 Boot Menu" option to "Enabled". Press F10 to Save and Exit, then once Windows loads shut down again.
4) Insert your USB flash drive with your 64-bit Ubuntu installer on it.
5) Power on and keep pressing F12 until the boot menu pops up. Select the flash drive, boot, and install Ubuntu.

This is where things get tricky:
6) After ubuntu reboots, it will boot back into Windows. Shut down again. Reboot and hit F2 to enter the BIOS again.
7) Under "Security", choose "Set Supervisor Password", and set one. You will need this password any time you go back into the BIOS. A bunch of options on the page should change from grey to blue.
8) The "Select an UEFI file as trusted for executing" should now be available. If it's not available, check that Secure Boot is still Enabled, if not, Enable it. Select it, and navigate to HDD0->EFI->ubuntu->grubx64.efi. The BIOS will ask you for a name for it, I called it Grub.
9) Hit F10 to save and exit, then immediately hit F2 again to re-enter the BIOS. 
10) Now go to "Boot", set "Secure Boot" to "Disabled", and arrow down to the bottom of the list to your new "Grub" entry. Hit F6 until it's the top of the list.
11) Hit F10 one last time. Your system should now reboot to the Grub boot loader!

---

### Post by RobGoss on 2017-04-08
Thanks so much for posting these tip for Acer users, they probably have the hardest time installing Ubuntu on these machines do to the fact of all the changes that are needed within the BIOS I'm sure this will come in handy

---

### Post by ardydo on 2017-04-10
Thank you! I was having trouble with being able to launch grub on my acer e1 572 6 br648 and oldfred directed me here and now my issue is solved.

A pretty straightforward tutorial for something kinda weird with those notebooks.

Thank you once again!

---

### Post by amp_man on 2017-04-13
Glad it helped! I sort of stumbled across how to do it, and figured others were also having trouble with the stupid BIOS.

---

### Post by DrAcid on 2017-07-09
Amazing instructions, thanks a lot for sharing! :)
Really helpful, didn't know where to even begin.

---

### Post by resnor on 2017-07-09
Saved my day , Aspire ES 15      , ES1-572-358K Thanks !!!!!

---

### Post by f16dude on 2017-11-28
That helped me a lot. I thought I would never get this to boot into Linux. Thanks.

---

### Post by ckrzen on 2018-05-19
Thanks!

Worked perfectly on my Acer Aspire E5-575 (E5-575_115F) bios v1.32

---

### Post by abccjack20 on 2018-05-26
In fact, I wasn't one of the members of this forum until I read this article. I signed up just to thank you for helping me solve this stupid problem struggling me for couple of days. Your instructions are extremely helpful. Thanks you very much. I mean it!

---

### Post by scarboro on 2018-09-26
I tried this with a new Acer Aspire ES 11.  The 'bunch of options' did not appear.  They weren't on the UEFI list.  On rebooting, my Acer now reports 'No Bootable Device'.  Perhaps someone has some wisdom for me.

---

### Post by oldfred on 2018-09-26
@scarboro
Have you updated UEFI from Acer to latest version for your system?

Some old threads had users downgrading to an older UEFI, but in last year or so updates to UEFI have fixed issues of not seeing settings. You do have to have Secure Boot on and set UEFI password.

---

### Post by milanke on 2018-11-24
Acer F5 - 572G works too by this. Thank you!

---

### Post by morphine1530 on 2019-06-07
> **amp_man said:**
> This probably also applies to other Acer models using InsydeH2O BIOS. After much messing around, this is how I got dual boot working on my Acer Aspire R14-471T:

1) Update to the latest BIOS (I know, it's UEFI, but I'm going to call it a BIOS). My new laptop shipped with 1.07, 1.10 is the latest as of this posting.
2) Shut down, then while starting back up hit the F2 button many times until the BIOS Setup Utility loads.
3) In the "Main" menu, set the "F12 Boot Menu" option to "Enabled". Press F10 to Save and Exit, then once Windows loads shut down again.
4) Insert your USB flash drive with your 64-bit Ubuntu installer on it.
5) Power on and keep pressing F12 until the boot menu pops up. Select the flash drive, boot, and install Ubuntu.

This is where things get tricky:
6) After ubuntu reboots, it will boot back into Windows. Shut down again. Reboot and hit F2 to enter the BIOS again.
7) Under "Security", choose "Set Supervisor Password", and set one. You will need this password any time you go back into the BIOS. A bunch of options on the page should change from grey to blue.
8) The "Select an UEFI file as trusted for executing" should now be available. If it's not available, check that Secure Boot is still Enabled, if not, Enable it. Select it, and navigate to HDD0->EFI->ubuntu->grubx64.efi. The BIOS will ask you for a name for it, I called it Grub.
9) Hit F10 to save and exit, then immediately hit F2 again to re-enter the BIOS. 
10) Now go to "Boot", set "Secure Boot" to "Disabled", and arrow down to the bottom of the list to your new "Grub" entry. Hit F6 until it's the top of the list.
11) Hit F10 one last time. Your system should now reboot to the Grub boot loader!



After i turn on my laptop. It shows GNI GRUB version 2.02

Minimal BASH-like line editing is supported.
I cant choose Windows or Ubuntu

---

### Post by oldfred on 2019-06-07
@morphine1530
Please start your own thread as you have started to boot, but something in not configured correctly.
Post you model and link to summary report. Be sure to boot in UEFI mode, if that is how you installed.
       Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

