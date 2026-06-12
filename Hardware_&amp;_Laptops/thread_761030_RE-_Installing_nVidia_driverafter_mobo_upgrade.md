---
title: "RE- Installing nVidia driverafter mobo upgrade"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by Aghosh993 on 2008-04-20
Hi,
I recently installed a new mobo; a Biostar TF7025-M2, with onboard nVidia 7025 GPU, and an AMD Athlon 4000+ CPU. When I boot into ubuntu, it fails to start Xserver, understandably. Then, I booted into recovery mode, and tried :
sudo dpkg-reconfigure xserver-xorg, to try enable basic vesa drivers. However, it return something like this:
sudo: dpkg-reconfigure not a valid command.

if I take out the sudo, it says: permission denied

Ideas?
Thx,
Aghosh993

---

### Post by overdrank on 2008-04-20
> **Aghosh993 said:**
> Hi,
I recently installed a new mobo; a Biostar TF7025-M2, with onboard nVidia 7025 GPU, and an AMD Athlon 4000+ CPU. When I boot into ubuntu, it fails to start Xserver, understandably. Then, I booted into recovery mode, and tried :
sudo dpkg-reconfigure xserver-xorg, to try enable basic vesa drivers. However, it return something like this:
sudo: dpkg-reconfigure not a valid command.

if I take out the sudo, it says: permission denied

Ideas?
Thx,
Aghosh993

HI and did you login with user name and password  before using that command ?

---

### Post by Aghosh993 on 2008-04-20
well, I selected recovery mode from the boot menu, and it started the usual list of boot scripts... then it just flashed a blinking cursor. I pressed enter, and it then gave me the root@ubuntu prompt. 
Thx,
Aghosh993

---

### Post by redoscar3 on 2008-04-20
On my Acer laptop running Edgy Eft, I tested the command recommended at the top of the /etc/X11/xorg.conf file which is specified as follows:

# sudo dpkg-reconfigure -phigh xserver-xorg

That script asked me to select a driver (vesa default) and a resolution.

I think most recent versions are doing something similar so I'm not sure why you might be having issues (other than the lack of the -phigh option.  Maybe give that a try.

Red

---

### Post by Aghosh993 on 2008-04-20
hmm, I'll try that next time I get to do that (probably tomorrow), thanks.
Aghosh993

---

### Post by redoscar3 on 2008-04-20
Also, I believe that dpkg-reconfigure is part of the debconf package and should be found in the /usr/sbin directory.

Red

---

### Post by Aghosh993 on 2008-04-20
Ok, I just tried it (the -phigh option) now, same effect.
for some reason, it doesn't recognize the command. I then tried to get the nvidia glx-new (sudo apt-get install nvidia-glx-new) drivers, but it pointed out some file name, and said there was extra 'junk' at the end of the file. (I'll have to reboot later and check the exact message, sorry). 
It's funny how this isn't working, given that it is one of the most common fixes mentioned in most forums. Damn frustrating, if you ask me...
Anyway, thanks.
Aghosh993

---

### Post by overdrank on 2008-04-20
> **Aghosh993 said:**
> Ok, I just tried it (the -phigh option) now, same effect.
for some reason, it doesn't recognize the command. I then tried to get the nvidia glx-new (sudo apt-get install nvidia-glx-new) drivers, but it pointed out some file name, and said there was extra 'junk' at the end of the file. (I'll have to reboot later and check the exact message, sorry). 
It's funny how this isn't working, given that it is one of the most common fixes mentioned in most forums. Damn frustrating, if you ask me...
Anyway, thanks.
Aghosh993

Ok then try it from the regular boot of ubuntu. When you receive the xorg blue screen just keep clicking ok then you will reach the command line and login and then the command.

---

### Post by redoscar3 on 2008-04-21
If you can't get the script to run, it is either that dpkg-reconfigure has been deleted, it is no longer executable, or that /usr/sbin is no longer in the path of the user.  You can check the existence of the file and its attributes pretty easily.

Drill down to /usr/sbin and see if the file still exists and if it can be executed.   If it's a path problem, you can fix that, or from the /usr/sbin directory enter something like:

> # sudo ./dpkg-reconfigure -phigh xserver-xorg

If the file is missing, try reinstalling the debconf package.  But I agree with you, this should not be this hard.  All this stuff should have just worked.  Good luck.

Red

---

### Post by Aghosh993 on 2008-04-21
Ok, I'll try that next time I boot into Ubuntu.
BTW, if I were to install from the Alternate CD, would it automatically install the vesa drivers and at least give me some kind of GUI?

---

### Post by redoscar3 on 2008-04-22
To be honest, I have never done an install using the Alternate CD.  I would expect it to install the vesa driver if indeed it installs the xserver.

---

### Post by thisismalhotra on 2008-04-22
> **Aghosh993 said:**
> Hi,
I recently installed a new mobo; a Biostar TF7025-M2, with onboard nVidia 7025 GPU, and an AMD Athlon 4000+ CPU. When I boot into ubuntu, it fails to start Xserver, understandably. Then, I booted into recovery mode, and tried :
sudo dpkg-reconfigure xserver-xorg, to try enable basic vesa drivers. However, it return something like this:
sudo: dpkg-reconfigure not a valid command.

if I take out the sudo, it says: permission denied

Ideas?
Thx,
Aghosh993

Dont quote me on this but I am almost sure what happens is when you log in a recovery mode, ubuntu only load the bare minimum modules and the kernel modules in your system. Anyother command/script have to be run manually.

What you need to do is log in as a regular command and let the xserver fail. Then hit Ctrl + Alt + F1 to get in command line mode and login woth your user name and password. At this moment you have your regular system but without the GUI.

Now run

```

sudo apt-get update
sudo apt-get upgrade
```

What I would do is install ENVY on the system and than run envy in text mode to install nvidia driver. ENVY as per my expeirnce does a much better job than anybody else out there (LOL even the nvidia offcial installer .. dont say I said this). If you can't get ENVY than run

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

and start as vesa to get the GUI up and than install envy and run it.

GL:KS

---

