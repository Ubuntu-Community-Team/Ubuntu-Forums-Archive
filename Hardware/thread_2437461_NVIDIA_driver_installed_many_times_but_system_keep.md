---
title: "NVIDIA driver installed many times but system keeps reverting to llvmpipe"
date: 2020-02-24
forum: Hardware
---

### Post by mandac2 on 2020-02-24
First my system specs relevant to this problem:


Ubuntu version: 18.04.3LTS
GPU: GeForce GT 1030


I have lost count on how many times I have had to reinstall the driver for my GPU, following instructions on this page:


[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-10-cosmic-cuttlefish-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-10-cosmic-cuttlefish-linux)


Things will run smoothly for a while, then for no apparent reason, the system will revert to llvmpipe (LLVM 9.0, 128 bits) instead of using the NVIDIA driver. Why the hell does this keep happening?

---

### Post by CatKiller on 2020-02-24
There are three different methods detailed on that page. You haven't said what you actually did.

Venting isn't going to contribute to getting help. We're just other Ubuntu users here, like you.

---

### Post by mandac2 on 2020-02-24
The first thing I did was the simplest solution - install the driver from the standard Ubuntu repository (sudo ubuntu-drivers autoinstall). After several times of reverting to LLVM and repeating the process, that would no longer work, so I took the route of installing the proprietary NVIDIA driver. After several reboots, my system has again reverted to LLVM for no apparent reason. So I tried the simplest solution again, and this is what I got:

E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

---

### Post by Autodave on 2020-02-24
I am assuming that this is a desktop?  Did you do a clean install of 18.04 or did you update from a previous version?

---

### Post by Yellow Pasque on 2020-02-24
First off, watch your language. They're serious about that here. 

> **mandac2 said:**
> Things will run smoothly for a while, then for no apparent reason, the system will revert to llvmpipe (LLVM 9.0, 128 bits) instead of using the NVIDIA driver. Why does this keep happening?

Probably because the kernel updates and out of tree kernel modules break, especially if you try to combine multiple methods of installing the Nvidia driver.
What kernel are you running?
```
uname -a
```

---

### Post by mastablasta on 2020-02-27
> **mandac2 said:**
> So I tried the simplest solution again, and this is what I got:

E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

looks like something else is using dpkg. check the processes - 
top or htop (in console) 
or use system monitor 

make sure everything is turned off and try again. the simplest solution is the one that should be used. if something else is using dpkg (i don't know what you did to the OS), this would explain why driver update fails and things get reverted to let's call it "safe mode".

did you maybe use sudo with GUI application?

---

### Post by mandac2 on 2020-03-19
> **Autodave said:**
> I am assuming that this is a desktop?  Did you do a clean install of 18.04 or did you update from a previous version?

Yes, this is a desktop. It's not a clean install of 18.04. I've just been updating all the way since version 16.

Thanks, Autodave. :)

---

### Post by mandac2 on 2020-03-19
> **Yellow Pasque said:**
> 
Probably because the kernel updates and out of tree kernel modules break, especially if you try to combine multiple methods of installing the Nvidia driver.
What kernel are you running?


Here's the output of "uname -a":

```
Linux mandac 4.15.0-91-generic #92-Ubuntu SMP Fri Feb 28 11:09:48 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

Thank you, Yellow Pasque. :)

---

### Post by mandac2 on 2020-03-19
> **mastablasta said:**
> did you maybe use sudo with GUI application?

I use the GNOME Terminal. Should I stop the GUI service and exit to command line?

Thanks, mastablasta. :)

---

### Post by webaake on 2020-03-19
I've run Nvidia for years on Ubuntu and the fastest most up-to-date way, is using the Ubuntu drivers PPA (repo). Here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Do not install the drivers directly from Nvidia! (Nvidia-xxxx---xxx.run) And be sure to chose the correct driver for your 1030 card. I believe that driver version 440.xxx should be the one for 1030GT. 

And it sounds a bit like you're having problem with DKMS. DKMS is responsible for re-installing the same driver whenever there is a kernel update. Ensure that your DKMS install is working by running the command; ```
dkms status
``` on the command line (terminal).

---

### Post by mandac2 on 2020-03-19
> **webaake said:**
> I've run Nvidia for years on Ubuntu and the fastest most up-to-date way, is using the Ubuntu drivers PPA (repo). Here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Do not install the drivers directly from Nvidia! (Nvidia-xxxx---xxx.run) And be sure to chose the correct driver for your 1030 card. I believe that driver version 440.xxx should be the one for 1030GT. 

And it sounds a bit like you're having problem with DKMS. DKMS is responsible for re-installing the same driver whenever there is a kernel update. Ensure that your DKMS install is working by running the command; ```
dkms status
``` on the command line (terminal).

Thanks for the response, webaake. Running "dkms status" echoed:

```

[COLOR=#000000][FONT=&quot]anbox-modules-ashmem, 10.1~20180523.2.xenial.c36965f, 4.15.0-76-generic, x86_64: installedanbox-modules-ashmem, 10.1~20180523.2.xenial.c36965f, 4.15.0-88-generic, x86_64: installedError! Could not locate dkms.conf file.File:  does not exist.anbox-modules-ashmem, 10.1~20180523.2.xenial.c36965f, 4.15.0-91-generic, x86_64: installed

```

So my DKMS is missing its configuration file.
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]To fix the problem, I tried "dkms autoinstall" as suggested in another forum, but it failed because it needs dkms.conf, apparently.
[/FONT][/COLOR]I also tried "sudo apt-get install dkms", but the configuration file was still missing afterwards.
[COLOR=#000000][FONT=&quot]This has to be fixed before I even attempt to compile the driver from PPA, correct?

[/FONT][/COLOR]

---

### Post by webaake on 2020-03-19
You could try ```
sudo dpkg-reconfigure dkms
``` It should fix it.

---

### Post by oldfred on 2020-03-19
Installing a new driver, does not uninstall the old driver. And then you eventually get conflicts of some kind.
You must purge every time.
And if you used the nVidia .run file, you must use its process to uninstall it.

nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by webaake on 2020-03-19
Yes, uninstall the nvidia-xxx.run file.  And here are more hints about dkms (and Nvidia too): [https://askubuntu.com/questions/227258/error-could-not-locate-dkms-conf-file](https://askubuntu.com/questions/227258/error-could-not-locate-dkms-conf-file)

---

