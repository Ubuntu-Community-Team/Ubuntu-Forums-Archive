---
title: "Dell keyboard problem boot select problem"
date: 2011-12-25
forum: Hardware
---

### Post by bfromcolo on 2011-12-25
Hopefully this is the right spot to post this.

I replaced an ancient dell PS2 keyboard with a somewhat newer Dell SK-8135 USB keyboard. The keyboard works during boot up to access BIOS settings, and it works once Windows 7 is fully booted. But it does not work when the Windows screen to select what operating system to boot is presented. I dual boot Windows and Ubuntu (WUBI install) and can no longer select the Linux boot. Any ideas?

Thanks

---

### Post by BC59 on 2011-12-25
So it's working under Windows?

---

### Post by bfromcolo on 2011-12-25
Yes its fine in Windows, and it works in BIOS config screens, it just doesn't work in the Windows Boot Manager screen.

---

### Post by BC59 on 2011-12-25
Then it's a Windows, BIOS or hardware problem.
Look here if you can do something:
[http://answers.microsoft.com/en-us/windows/forum/windows_vista-windows_install/windows-boot-manager-frozen/8e3c3cad-75b8-4c4c-a70b-05b281b5f2f7](http://answers.microsoft.com/en-us/windows/forum/windows_vista-windows_install/windows-boot-manager-frozen/8e3c3cad-75b8-4c4c-a70b-05b281b5f2f7)

---

### Post by BC59 on 2011-12-25
I think is a USB keyboard problem. You have to enable the USB Legacy support on your motherboard. Search through your BIOS if you can do it.

---

### Post by bfromcolo on 2011-12-25
Turns out there is a BIOS setting to enable legacy DOS USB keyboard support.  I guess Windows 7 boot manager thinks is DOS.

Working now, thanks.

---

### Post by BC59 on 2011-12-25
Ok we posted the same moment. Good to know that you solved the problem.

---

