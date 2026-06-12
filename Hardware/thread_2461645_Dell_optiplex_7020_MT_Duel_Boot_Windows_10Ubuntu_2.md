---
title: "Dell optiplex 7020 MT Duel Boot Windows 10/Ubuntu 20.o4 LTS won't power on"
date: 2021-05-04
forum: Hardware
---

### Post by chew3001 on 2021-05-04
I have a duel boot installed on a Dell Optiplex 7020 MT. up to date. The problem was that after I booted into Ubuntu and then shut it down the PC wouldn't start when I pushes the power button. I had to unplug the Power Supply Unit  wait then plug it back in. Didn't have the problem with Windows. So I did some troubleshoot and found that if I disable Deep Sleep in the BIOS, the problem was solved. Secure Boot=Enabled, UEFI mode=Enabled, TPM updated, BIOS updated. BIOS settings = default

---

