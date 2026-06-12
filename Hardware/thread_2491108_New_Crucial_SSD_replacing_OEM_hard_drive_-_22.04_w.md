---
title: "New Crucial SSD replacing OEM hard drive - 22.04 won't install"
date: 2023-09-26
forum: Hardware
---

### Post by uacnt83982803 on 2023-09-26
My Acer Aspire E5-576's original HDD started failing, so I ordered a replacement (Crucial MX500).

I installed the drive and inserted a bootable 22.04 LTS usb stick.  It detected the drive correctly (correct size, etc.) and started the install.  I enabled the LVM filesystem and encryption.  Once I got to the point where it started copying the system files to the new SSD, I got this error:

```

Error fsycing/closing/dev/sda1: Input/output error

Retry |  Ignore

```

I exited and went to a live USB environment.  It sees the drive correctly, however when I try to do a manual format (the original install attempt did partition the drive properly) I get the same error.

I then restarted the installation, this time not encrypting the disk and so far it seems to be copying stuff over ok.

What did I do wrong and how do I go about fixing it so I can install this with the SSD encrypted?

-OR- do I even need to worry about this (encryption) since the Crucial controller includes hardware encryption (though I don't understand how that really helps, since someone could just remove the SSD and plug it into another laptop)?

Thanks.

---

### Post by oldfred on 2023-09-26
Do you have latest firmware?
Acer often needs UEFI update and if SSD, firmware update to SSD.

You may need control-S in UEFI to open more settings.
If you set "trust", be sure not to lose password, or reset back to blank or you may brick system.

---

### Post by uacnt83982803 on 2023-09-27
So, I should have read up on these (SSD) drive beforehand.  What I found out after reading is that Crucial drives are self-encrypting.  

In the end, I installed Ubuntu without trying to encrypt the disk using LUKS.  What I then did was go into the BIOS and enable hardware encryption and set a strong key.  Now, when the PC boots, the BIOS pops up a small window where I enter that key, which unlocks the drive so the system can boot and run normally.

I find this a much better solution, as the PC's processors no longer have to incur the overhead of processing the encryption/decryption.  Also, of course the SSD is lightning-fast so the overall experience is tremendously improved.

Marking this thread Solved but leaving it here in case someone else can benefit.

---

