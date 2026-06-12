---
title: "Where are the config files for stock kernel?"
date: 2008-07-27
forum: General Help
---

### Post by Neo_The_User on 2008-07-27
Hello! I am going to compile the 2.6.26 kernel from kernel.org but I would like to use the config file for the 2.6.24-19-generic kernel that way when I compile the kernel and do make-xconfig, I can load an existing kernel config file that I can optimize for my hardware and turn off debugging (etc.) I am sure that this question has been asked far too many times but I cannot find a thread that relates to this thread and I did several searches all over google and could not find the directory for the stock kernel's config file. I have the 2.6.24-19 source and headers with all required packages. I know how to compile, run, and install the kernels on kernel.org but I am not highly experienced with computers do understand every single function in the make-xconfig nor do I have days to learn each and every option inside and out so if you can find the directory and file that xubuntu uses for a stock kernel config file, that would be great.

Sincerely,

Neo_The_User

---

### Post by Neo_The_User on 2008-07-27
Does Ubuntu / Xubuntu even have a config file that I can mess with?

...bump

---

### Post by braddcadd on 2008-07-27
I just compiled an Ubuntu kernel with KernelCheck.  It was insanely easy.  The config options appear in a dialog (not sure if the dialog would work in xubuntu).  KernelCheck is definitely worth the try.

---

### Post by Neo_The_User on 2008-07-27
> **braddcadd said:**
> I just compiled an Ubuntu kernel with KernelCheck.  It was insanely easy.  The config options appear in a dialog (not sure if the dialog would work in xubuntu).  KernelCheck is definitely worth the try.

And KernelCheck loads the stock config file right into xconfig? I am confused. If it doesn't work in xubuntu, I'll go install Ubuntu 8.04.1 and I already have it burned. Oh and I am trying to compile a non-ubuntu kernel. KernelCheck is not in the repository.

---

### Post by Taxman415a on 2008-07-27
I don't have the full sources installed, but I do have the headers and my kernel config files are in /boot.

Incidentally a good general method for finding stuff like this if google and searching the forums fails is to go to the [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) Ubuntu community documentation ([https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)). Typing in kernel in the search box got links to some pages you probably want to read thoroughly:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

---

### Post by Neo_The_User on 2008-07-27
OK Now I am stuck. Are the stock ubuntu kernel configs in boot or debian/config/ARCH/ because the guide said something else.

---

### Post by braddcadd on 2008-07-27
> **Neo_The_User said:**
> 
And KernelCheck loads the stock config file right into xconfig? I am confused. If it doesn't work in xubuntu, I'll go install Ubuntu 8.04.1 and I already have it burned. Oh and I am trying to compile a non-ubuntu kernel. KernelCheck is not in the repository.


I think kernel check reads your current kernel config and feeds it to a dialog where you can edit the options.  I am 99% sure it will work in xubuntu fine, but I haven't tried it myself.

KernelCheck definately gets the latest kernel from kernel.org.  That is the purpose of the application, to keep you on the latest kernel.  

No Kernel check isn't in the repository.  You must download and install it on your system manually.  See the link below:
[http://kcheck.sourceforge.net/download.html](http://kcheck.sourceforge.net/download.html)

Hope that helps.

---

### Post by Taxman415a on 2008-07-27
Try an ls in /boot and you'll know. :) The guide actually gives you both of those locations. You may be more interested in KernelCheck [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) as braddcadd mentioned or the Master Kernel Thread manual method that thread links to.

---

