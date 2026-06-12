---
title: "laptop does not restart"
date: 2011-08-12
forum: Hardware
---

### Post by paulwillems on 2011-08-12
Dear all,

I am having an ironing problem with a Asus laptop (X50N).
This problem however exist for a long period which means several releases.
I am trying to locate the problem in the kernel however without success so far.
I have used the site [http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt) to see which parameter can be a possible cause.

Right now the 11.04 have been installed. In the terminal the last message is "Restarting system" and then it hangs.

Does anyone have a suggestion for what I can try as a kernel parameter to see if the problem can be fixed?

Thanks in advance,

Paul Willems

---

### Post by Toz on 2011-08-12
Welcome to the forums.

There is a long running bug report specific to this notebook and rebooting. See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199687]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199687").

As for kernel parameters, there is a reboot=? parameter that you could try. The source indicates that you could specify **reboot=b** to force the reboot through the bios. I've also come across another bug report (see: [https://bugzilla.kernel.org/show_bug.cgi?id=11533]("https://bugzilla.kernel.org/show_bug.cgi?id=11533") that shows that **reboot=p** will also work.

---

### Post by paulwillems on 2011-08-12
Hi Toz,

Thanks for your quick response.
I've tried the parameter **"reboot=b" **already but it didn't work. However I didn't knew the parameter **"reboot=p" **and I've tried this one and **YES** **IT WORKS!!!!!** :popcorn:

Lets see how to make this parameter permanent in the kernel.

Btw: How does a new kernel reacts when a new kernel update is available for download? Does it mean that you have to set this parameter again?

---

### Post by Toz on 2011-08-12
To make it permanent, edit the file **/etc/default/grub**
```
gksudo gedit /etc/default/grub
```
...and edit the line starting **GRUB_CMDLINE_LINUX_DEFAULT** to include (inside the quotes) this new parameter. Something like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=p"
```

Save the file then run:
```
sudo update-grub
```

As for new kernels, if the new kernel still supports this parameter, it will be used if you employed the above procedure to permanently set it.

Please make this tread as solved using the "Thread Tools" link above. Thanks.

---

