---
title: "Error mssg:  communicating to tpm chip, after upgarde to 22.04 lts"
date: 2022-05-03
forum: Hardware
---

### Post by jmichaels29 on 2022-05-03
After doing a clean installation to 22.04 lts, upon boot up each time, I get around a dozen error messages flash across the screen,

similar to "ima:  error communicating to tpm chip"

Just curious what this is  (?)

Addendum:  I believe I found the solution (at [https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot](https://askubuntu.com/questions/1178285/how-to-solve-ima-error-communicating-to-tpm-chip-messages-during-boot)), to simply turn on the tpm chip in bios..
I pressed F10 repeatedly and got into the BIOS.  Anyone that can point me to where, in the menus, to turn on the "tpm" chip, I would much appreciate it.
Right now, the following menu selections are at the top, "File - Storage - Security - Power - Advanced."

Any help please

---

### Post by jmichaels29 on 2022-05-03
I read that "tpm" is something often or only found in business computers/servers.  If this is correct, perhaps I just ignore the error message?

---

### Post by Yellow Pasque on 2022-05-06
If you don't know what TPM is, then it's probably best to ignore the message. The TPM setting will be somewhere under the Security menu if you want to try toggling the setting (it may be called 'security processor' or something else).
Note that some folks feel these TPM chips create more security risks than they solve. You can google and make that decision for yourself.

---

### Post by yancek on 2022-05-06
I also expect you will find it under Security but you would likely get more specific help if you indicated the manufacturer of the computer as there are a number of differences.  On my HP Pavilian, it is under Security and has 3 optiions,  TPM Devoce shows Available,j TPM state enabled/disabled and Clear TPM.

---

