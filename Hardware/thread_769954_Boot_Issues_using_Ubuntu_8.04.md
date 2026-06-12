---
title: "Boot Issues using Ubuntu 8.04"
date: 2008-04-27
forum: Hardware
---

### Post by tritonofg on 2008-04-27
Hello,
  I tried loading Ubuntu (8.04 64bit OS) using the live cd (did not load at all).  I then tried the alternate (text) cd which worked.  When I rebooted grub loaded...and Ubuntu began to load...went to the splash screen (Ubuntu logo which bars  under it)...followed by text (too fast to read).  The last thing I saw before the screen went black was "ELSA"

I am trying to run Ubuntu on a Sharp Actius AL 27 Laptop
With:  AMD 64 Processor 2700+ (CPU)
       15" XVGA Monitor (1024 X 768)
       1280 MB RAM (1 Gig + 256 MB)
       VIA / S3G Unichrome Pro IGP (Video)
 
Note:  Ubuntu Works great if I have an external Monitor and Moue Hooked up. (CD's are both good...worked on desktop)

thanks in advance.

---

### Post by jump_sk8r340 on 2008-04-27
If you are using a laptop try pressing f6 to go into boot edit and type in "vga=771" it helps with laptop display errors. Hope that helps :)

---

### Post by Dev'olution on 2008-04-27
I agree with Jump... looks like the issue is in the laptop screen res itself. 

Try what jump said :)

:popcorn:

---

### Post by tritonofg on 2008-04-27
> **jump_sk8r340 said:**
> If you are using a laptop try pressing f6 to go into boot edit and type in "vga=771" it helps with laptop display errors. Hope that helps :)

When do I do this?  Do I have to go into recovery terminal?  Or boot up attached to external screen and use terminal?

---

