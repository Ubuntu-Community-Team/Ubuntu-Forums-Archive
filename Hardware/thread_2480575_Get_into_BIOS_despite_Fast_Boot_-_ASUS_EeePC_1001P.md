---
title: "Get into BIOS despite Fast Boot - ASUS EeePC 1001PX"
date: 2022-11-02
forum: Hardware
---

### Post by John Nagle on 2022-11-02
I just bought an ASUS EeePC 1001PX off Ebay. I've bought these before and put XUbuntu on them with no trouble. But this machine was "upgraded". Someone put Windows 10 on it and enabled Fast Boot.

So I can't get into the BIOS. F2 during boot won't work. F2 pushed repeatedly won't work. F2 pushed and held during power on won't work. Pushing and holding the power button for 3 seconds won't work. ESC won't work. Pressing F10 won't work. The keyboard seems to totally ignored in this boot mode. 

The BIOS does come up, the usual messages (Press F2, Press ESC, etc.) appear and rapidly disappear. Then Windows 10 boots and I can't stop it. Windows seems to be fine; I just can't get out of it.

Tried ASUS advice: [https://www.asus.com/us/support/FAQ/1044641](https://www.asus.com/us/support/FAQ/1044641) No good.

Tried Intel advice: [https://www.intel.com/content/www/us/en/support/articles/000005847/intel-nuc.html](https://www.intel.com/content/www/us/en/support/articles/000005847/intel-nuc.html) No good.

Tried Microsoft advice: [https://answers.microsoft.com/en-us/windows/forum/all/cant-access-bios-settings-via-f2-key-in-windows-10/203c9b35-6905-45be-acdb-dfa865891d1e](https://answers.microsoft.com/en-us/windows/forum/all/cant-access-bios-settings-via-f2-key-in-windows-10/203c9b35-6905-45be-acdb-dfa865891d1e) Useless.

Any ideas?

---

### Post by John Nagle on 2022-11-02
Found a workaround. Apparently someone enabled Ultra Fast Boot. With that on, you have no options at boot unless boot fails. But once Windows is up, if you do a Windows Restart, you can get boot options. So now I have a Ubuntu USB stick running.

---

