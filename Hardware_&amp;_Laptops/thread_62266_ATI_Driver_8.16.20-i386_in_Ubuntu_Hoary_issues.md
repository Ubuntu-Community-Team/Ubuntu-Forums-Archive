---
title: "ATI Driver 8.16.20-i386 in Ubuntu Hoary issues"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by thawkth on 2005-09-04
Hello all, I've downloaded the ATI installer from the ati website and installed as root the drivers. I clicked through the simple dialogues, and then ran fglrxconfig. I get the ATI config program put in my menu, as well as being told that the driver is being used.

My only problem is this: it's still trying to use mesa for opengl! Everything else seems to be listed correctly.

Fglrx is listed when I do an lsmod, and as far as I can tell, I did fglrx correctly.

I've been attempting to use cedega's point2play, and I get a very slow score on glxgears and fail the 3d acceleration portion entirely. 

Have I forgotten something somewhere? Has anyone seen a problem like this?

Oh, and I can't remember the command, but I read in other forums that I should use a particular command to see if direct render was set to yes or no - all I know is it replied with No. I don't know how to change this or if I should.

Thank you very much for your help!

Todd

P.S. - I had previously attempted installing the drivers via apt-get, but of course I can't remember the exact files I downloaded (I believe it was an older version of fglrx and the ati control panel)...I know this may be part of the issue.

---

### Post by bjweeks on 2005-09-04
Most people dont recommend the ATI drivers. You should check the ATI driver How to s in the how to forum section.

---

### Post by ry_ry on 2005-09-04
I used this "How to" to install the ATI drivers using the ATI installer. You might want to check it out.

[http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10&highlight=ati+fglrx+8.14.13](http://www.ubuntuforums.org/showthread.php?t=32495&page=17&pp=10&highlight=ati+fglrx+8.14.13)

Scroll down and follow Epskampie posted How to., except insert driver version 8.16.20 in place of 8.14.13 version.

Hope this helps.  :)

---

