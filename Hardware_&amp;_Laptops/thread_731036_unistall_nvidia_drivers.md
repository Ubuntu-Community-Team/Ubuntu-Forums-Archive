---
title: "unistall nvidia drivers"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by Ozonecy on 2008-03-21
for one reason i need to unistall nvidia latest drivers from console. i canot start x because i change my vga. i need to unistall nvidia and then install ati drivers.
thanks

---

### Post by Ozonecy on 2008-03-21
i found this:
from the nvidia website:

Uninstalling NVIDIA drivers
Did something in your installation go terribly, terrible wrong? No
problem! Start your box up in console-only mode, navigate to where you
have the nvidia driver installation file saved, and run it with the
--uninstall option. sh filename.run --uninstall, and it uninstalls
everything it put in. Then it's a simple matter of restoring your
XF86Config from the backup we made above.


so in your case:
sudo sh NVIDIA-Linux-x86-169.07-pkg1.run --uninstall

hope that helps.

--
i installed nvidia drivers withn Envy.
i need to know where is the package and what driver version i have.
then i will type....
so what commands?:)

---

