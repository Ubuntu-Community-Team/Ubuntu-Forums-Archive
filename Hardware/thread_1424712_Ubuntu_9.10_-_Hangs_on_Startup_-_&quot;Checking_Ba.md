---
title: "Ubuntu 9.10 - Hangs on Startup - &quot;Checking Battery State... [Done]&quot;"
date: 2010-03-08
forum: Hardware
---

### Post by Skootle on 2010-03-08
Hello,

I have clean installed Ubuntu 9.10 from a Live USB stick and I sometimes get an error when starting it up. It reads "Checking Battery State... [Done]" and just hangs there, at which point I have to force it to shut down. If I try booting up again, I'll normally get the same message, or I'm thrown to a command line in which I can't write (because it freezes after typing 2 or 3 characters) with the title "Ubuntu 9.10 fabian-laptop tty1" (fabian-laptop is the name of my computer). After 4 or 5 tries, I normally manage to boot normally to the desktop.

I have read that it might have something to do with nVidia drivers not being correctly installed, but I have installed them from the Restricted Drivers manager without any problems (I've got Compiz Fusion working quite well). I have also locked the versions of linux-image-generic and linux-headers-generic so as not to update the kernel (before my current install, it updated and completely messed up my system, so I had to reinstall).

Any help would be greatly appreciated.

Thank you

*EDIT*

I forgot to mention that my laptop is a Dell Inspiron 1520 and I have an nVidia GeForce 6800GTM

---

### Post by newk8600 on 2010-09-27
I don't know if anybody has helped with this problem but I got the same thing after having an: 

"error: environment block too small" 

so I reinstalled grub2 and rm grubenv  and created it again. I can almost boot into the install but it hangs at start up after: 

"checking battery state...
             ...done        "

I can't get past there.

---

