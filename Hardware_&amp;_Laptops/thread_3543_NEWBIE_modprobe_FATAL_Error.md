---
title: "NEWBIE: modprobe FATAL: Error"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by Nikita on 2004-11-07
When my PC boots, I get an modprobe Error. Later on sound absolutely doesn't work. Soundcard is: Creative Soundblaster 16 Plug and  Play (WDM) for ISA-Port and it works properly under windows.

Another problem: I am mot able to work as aministrator. Tried sudo -s, but it asks for password, which I don't know. Have I forgot to write it down during configuration?

Can anybody help?

---

### Post by Andy Owen on 2004-11-07
I had a similar issue today. It was fixed using the bootloader. You need to edit the script it runs when it launches Ubuntu. On the line that begins with "kernel" add "pci=noacpi" to the very end of it. This will hopefully fix the sound.

As for sudo, when it asks for the password, this is the password you chose for yourself as user, not a separate administrator/root one. So, you just need to use the one you use to log in with.

---

