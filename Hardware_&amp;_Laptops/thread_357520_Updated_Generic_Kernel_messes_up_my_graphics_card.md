---
title: "Updated Generic Kernel messes up my graphics card"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by ZeldaFan on 2007-02-09
When I automatically updated the generic kernel to version 2.6.17-11 on laptop, my Nvidia go 7600 GPU with 512 MB dedicated video RAM doesn't work anymore. However on 2.6.17-10, the 3d acceleration drivers work fine, so what is the problem when I updated the kernel?

---

### Post by Trsnrtr on 2007-02-09
I've got the same problem and am currently searching for the solution.  I tried running sudo envy to update the driver, but the checksum on the new driver fails.  I'm still hunting for a solution.

Dennis

---

### Post by Trsnrtr on 2007-02-09
OK, just go to Nvidia and download the latest driver and run it.  Everything should be fine.

I downloaded the new driver and placed it in my home directory and then rebooted using the new kernel which of course failed to start the xserver.  Then, at the command line, I ran sudo sh <driver> and let it have its way with my machine.  Then sudo reboot and everything is fine.

Dennis

---

### Post by ZeldaFan on 2007-02-09
I went to the Nvidia website and downloaded the file. I am just a beginner to linux in general, so I am not really sure what to do next. I tried installing it, but apparently I cannot while X is running and I do not know how to disable it.

---

### Post by Trsnrtr on 2007-02-10
> **ZeldaFan said:**
> I went to the Nvidia website and downloaded the file. I am just a beginner to linux in general, so I am not really sure what to do next. I tried installing it, but apparently I cannot while X is running and I do not know how to disable it.

The easiest way, is to put the driver in your home directory where you can easily get to it.  Then reboot and choose the new kernel, which will fail to start the xserver which is ok.  Eventually, it should give you a login.  Or, you can probably choose the new kernel in safe/recovery mode.  Go ahead and login.

Now, just type sudo sh <the name of the driver> and accept all of the recommendations that it offers you.  After it is done, reboot.  Should work fine.

BTW, if Ubunto is like other distros, you'll have to do this with every kernel upgrade.

Dennis

---

