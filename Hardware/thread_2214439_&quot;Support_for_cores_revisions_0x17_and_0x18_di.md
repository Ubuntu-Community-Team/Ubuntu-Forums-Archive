---
title: "&quot;Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. T"
date: 2014-04-01
forum: Hardware
---

### Post by dsobrinho on 2014-04-01
Hello,

I have noticed a problem during my boot system with ubuntu 13.10. 

Does anybody knows somethign about that? how to fixe it may be?

[FONT=arial]"Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1"

Best regards,
Daniel[/FONT]

---

### Post by Saurevv on 2014-05-30
It seems that support for that particular chip or firmware version is still not very stable.

  The message is telling you to [pass an option to the b43 kernel module]("https://wiki.archlinux.org/index.php/Kernel_modules#Setting_module_options") to activate support for your chip version. This **may improve things or not**. To do so, create a file /etc/modprobe.d/local-b43.conf containing the lines

  # Activate experimental support for some hardware revisions
options b43 allhwsupport=1
  To make the settings come into effect, turn off networking and unload then reload the module with the commands

  rmmod b43
modprobe b43
  Run these commands as root, i.e. with su or sudo.

(text copied from [http://unix.stackexchange.com/questions/93738/b43-wireless-driver-error](http://unix.stackexchange.com/questions/93738/b43-wireless-driver-error))

---

### Post by darkus2 on 2014-12-23
[http://ubuntuforums.org/showthread.php?t=2214110&](http://ubuntuforums.org/showthread.php?t=2214110&)      
Worked for me.

---

