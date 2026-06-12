---
title: "how do i play .bundle programs?"
date: 2008-10-18
forum: General Help
---

### Post by reinaldistic on 2008-10-18
i am trying to install vmware and it comes as bundle, how do i use it?

---

### Post by darco on 2008-10-18
This is from the vmware install guide...you can find more help in the Ubuntu Virtualization forum...

    Install Workstation on a Linux Host Using a Bundle
          The bundle&#8208;based installer lets you install the product in one step. If the GUI&#8208;based 
          installer fails, run the installer file with the --console command in your terminal.
          NOTE   On Red Hat Enterprise Linux 5.1 hosts and possibly some other Linux 
          distributions, the bundle&#8208;based installer launches a command&#8208;line wizard rather than 
          a GUI wizard. 
          VMware-Workstation-<xxxx-xxxx>.<architecture>.bundle is the name of the 
          installer file. In the name, <xxxx-xxxx> is a series of numbers that represent the version 
          and build numbers, and <architecture> is i386 or .x86_64.
          To install Workstation on a Linux host using a bundle
          1    Log in to your Linux host with the user name you plan to use when running 
               Workstation.
          2    In a terminal window, become root to perform the initial installation steps:
               su
          3    If you are installing from the installation media instead of a downloaded file, 
               mount the Workstation installation media.
VMware, Inc.                                                                                       43
Workstation User&#8217;s Manual
           4    Change directories to the directory where the installer file is located and run the 
                installation file:
                sh VMware-Workstation-<xxxx-xxxx>.<architecture>.bundle
                If you are using the Workstation installation media, this file is in the Linux 
                directory.
           5    Accept the EULA to continue.
           6    (Optional) If you are using the --console option or running a host that does not 
                support the GUI installation do one of the following:
                     To scroll to the end of the VIX EULA, press spacebar.
                     To exit the EULA and go to the prompt Do you agree? [yes/no], press q.
           7    (Optional) Enter the directory path to the Integrated Virtual Debugger for Eclipse 
                if Eclipse is installed.
           8    Click Install.
           9    Open Workstation to launch the kernel module updater to install and configure the 
                kernel.
                See &#8220;Start Workstation on a Linux Host&#8221; on page 52.

good luck

darco

---

### Post by cariboo on 2008-10-18
THe first thing to do is to make sure your .bundle file is executable. I'm going to assume your .bundle file is located on your desktop. In an Applications-->Accressories-->Terminal type:

```
chmod +x ~/Desktop/*bundle
```

This makes the file executable. To install anything in Linux you have to be root, in the same terminal type:

```
sudo ~/Desktop/*bundle
```

This should install vmware if you have met all the dependancies.

Jim

---

