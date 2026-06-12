---
title: "How to Force Boot with UEFI instead of BIOS?"
date: 2022-05-19
forum: Hardware
---

### Post by geeky-1 on 2022-05-19
I have a UEFI Windows system where I added a UEFI Ubuntu disk from another computer, but it always defaults to loading Windows and I want it to default to loading Ubuntu.
I read that I should deactivate Windows Boot Manager, which I did.
Then I should boot into Ubuntu and run efibootmgr. However, when I run efibootmgr, I get > EFI variables are not supported on this system., which indicates that it booted with BIOS instead of UEFI. So how do I force it to boot Ubuntu using UEFI?

---

### Post by oldfred on 2022-05-19
How you boot install media or repair media UEFI or BIOS is then how it installs or repairs.
Be sure to boot live installer in UEFI boot mode.

If still issues, to give more info:
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by guiverc on 2022-05-19
I agree with what @oldfred has already said.

I perform QA-testing (*Quality Assurance*) testing of Lubuntu, where we need to confirm Lubuntu (*and Ubuntu & other flavors*) installs in

- BIOS/CSM/*legacy* mode,
- uEFI mode, & 
- Secure-uEFI mode..

I set those modes according to the machine firmware , then boot the Lubuntu installation media (*no change is made in Lubuntu boot/media; the box & it's setup controls the boot mode*)

I control the mode the box boots the media in via the boxes own firmware/settings. The Lubuntu installation media will boot (*if written correctly & not modified*) in all of BIOS/*legacy*, uEFI or Secure-uEFI modes - with the user controlling which is used before the boot starts.

I am aware that it's possible to write Ubuntu ISO's to thumb-drives that can *force* Lubuntu installation to occur in specific modes; but if correctly written to media it'll install using the mode in which it's booted, or as set by the installer  (it's shown upper left in `calamares` during installation; on this [pic here the word BIOS tells you it's legacy/BIOS/CSM]("https://manual.lubuntu.me/stable/_images/partitioning.png"))

I do have certain hardware that cannot operate all modes; eg. some QA-hardware I use is 15+ years old, thus well before uEFI/Secure-uEFI existed, a few devices will only boot uEFI/Secure-uEFI so I don't use them to test BIOS/*legacy* booting.. but the hardware, or user controlling settings really dictates how Lubuntu is installed.

Your error message indicates your box is in *legacy/*BIOS/*csm *mode, as my current box is; for my existing box I manually forced it to be in this mode prior to install; and both my installs were made in BIOS mode.

---

