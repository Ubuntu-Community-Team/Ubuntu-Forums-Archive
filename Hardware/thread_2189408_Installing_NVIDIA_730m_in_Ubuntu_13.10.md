---
title: "Installing NVIDIA 730m in Ubuntu 13.10"
date: 2013-11-22
forum: Hardware
---

### Post by renato3 on 2013-11-22
Hi, I have a Dell Ispiron 14R 5421 with a Nvidia 730m. I'm trying to install my video card using default Nvidia official driver (the *.run file for linux 64 bits). But when I do this, during installation it says automatic script failed and ask if I want to continue anyway. When I continue, it complains there is Nouveau module. It adds a line in /etc/modprobe.d blacklisting "nouveau" module. Then ok, when I finish installation, Ubuntu's login manager doesn't load. A gray screen appears, mouse cursor is an X and nothing happens anymore.

Could someone help me? What did I do wrong? Is there any official tutorial about how to install this driver in this Ubuntu release?

---

### Post by heir4c on 2013-11-22
Boot up in recovery mode from Grub-menu and when you see a little menu click just Enter.
Than when you see the Desktop go via Dash to "Software&Updates" and click on the Tab of the drivers. He will search for drivers.
What shows up?

---

### Post by renato3 on 2013-11-22
I suppose this procedure you're suggesting will install Nvidia open source driver, right? I need nvidia proprietary/official driver.

---

### Post by howefield on 2013-11-22
It will show you what drivers are available for your card, which should include proprietary nvidia, but possibly not as up to date as whatever you downloaded from a third party site.

---

### Post by renato3 on 2013-11-22
I went all throught this process again:

ctrl+alt+F1
added "blacklist nouveau" to a file in /etc/modprob.d
restart
```
# chmod +x NVIDIA-linux-x86_64-331.20.run
# service lightdm stop
# ./NVIDIA-linux-x86_64-331.20.run
# service lightdm start
```

And again, lighdm fails to start. I get stuck with a gray screen and an X as mouse cursor. Whenever I turn the computer on, this occurs and I have to reinstall the whole system to be able to use X again. Please, help... I need proprietary drivers :(

---

### Post by renato3 on 2013-11-22
> **heir4c said:**
> Boot up in recovery mode from Grub-menu and when you see a little menu click just Enter.
Than when you see the Desktop go via Dash to "Software&Updates" and click on the Tab of the drivers. He will search for drivers.
What shows up?

I don't think I have grub here. Maybe the installer didn't install it to my UEFI boot partition because I had no other OS here. Help, everything is so messed up :(

---

### Post by renato3 on 2013-11-22
> **renato3 said:**
> I don't think I have grub here. Maybe the installer didn't install it to my UEFI boot partition because I had no other OS here. Help, everything is so messed up :(

I checked using synaptic, the following packages are installed:

grub-common
grub-efi-amd64
grub-efi-amd64-bin
grub-efi-amd64-signed
grub2-common

So it seems grub2 is installed, buuuut it doesn't show up when I turn my computer on. It boots straight to Ubunt. Oh hell :(

---

### Post by grahammechanical on 2013-11-22
It is easy to get confused. Just step back a bit.

You say there is only Ubuntu on this machine. Yes? In that case you will do not see a Grub menu. We only get a Grub menu if we have more than one OS. So, try pressing Shift at the start of the boot process.

At the Grub menu select Advanced Options for Ubuntu. Once will move any key the boot countdown will stop. Inside Advanced options there will be another menu. From there we will get Recovery Mode. Select it and then select Resume that may get you to a desktop using a fallback version of the Nouveau open source video driver.

There is something else that I might suggest. When you install Ubuntu do not tick to install third party software. Doing that will install a proprietary video driver and if the usual Nvidia driver is not useful then it may be better to let Ubuntu install and activate the Nouveau video driver and change things afterwards.

Do not assume that the latest proprietary video drivers are the best. They are certainly untested by Ubuntu developers otherwise they would be available through Additional Drivers. It may be this Nvidia driver that is causing the problems. It may be buggy.

Regards.

---

### Post by renato3 on 2013-11-22
> **grahammechanical said:**
> It is easy to get confused. Just step back a bit.

You say there is only Ubuntu on this machine. Yes? In that case you will do not see a Grub menu. We only get a Grub menu if we have more than one OS. So, try pressing Shift at the start of the boot process.

At the Grub menu select Advanced Options for Ubuntu. Once will move any key the boot countdown will stop. Inside Advanced options there will be another menu. From there we will get Recovery Mode. Select it and then select Resume that may get you to a desktop using a fallback version of the Nouveau open source video driver.

There is something else that I might suggest. When you install Ubuntu do not tick to install third party software. Doing that will install a proprietary video driver and if the usual Nvidia driver is not useful then it may be better to let Ubuntu install and activate the Nouveau video driver and change things afterwards.

Do not assume that the latest proprietary video drivers are the best. They are certainly untested by Ubuntu developers otherwise they would be available through Additional Drivers. It may be this Nvidia driver that is causing the problems. It may be buggy.

Regards.

You're probably right, this new proprietary nvidia drive is buggy in windows too. But is my procedure wrong? Am I doing something wrong to install that *.run file?

---

### Post by heir4c on 2013-11-22
First see the Grub menu and recovery mode to start Ubuntu up.
Then look what Ubuntu recommend for your card via Software&Updates.

---

### Post by renato3 on 2013-11-22
I formated and reinstalled Ubuntu. Now I can access desktop again. But "Additional drivers" is empty and I have internet access,,, I don't know why it's happening.

---

### Post by Yellow Pasque on 2013-11-22
You have an Optimus machine with Intel/nvidia hybrid graphics, so you can't just install the nvidia driver like normal. See: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by renato3 on 2013-11-22
> **heir4c said:**
> Boot up in recovery mode from Grub-menu and when you see a little menu click just Enter.
Than when you see the Desktop go via Dash to "Software&Updates" and  click on the Tab of the drivers. He will search for drivers.
What shows up?

Although I have internet connection running, I get this screen:

[IMG]http://img546.imageshack.us/img546/6498/drad.png[/IMG]

---

### Post by renato3 on 2013-11-22
> **Temüjin said:**
> You have an Optimus machine with Intel/nvidia hybrid graphics, so you can't just install the nvidia driver like normal. See: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Why not?

(sorry if I sound like a noob, but I am a noob indeed... :( )

---

### Post by ChrisFromOz on 2013-11-22
Hi, I've just read this thread and the similar one started by the same member but now closed. I have an identical issue with an i7 Ivy Bridge processor controlling graphics. I have a 2GB Nvidia 720M under Ubuntu 13.10 on Asus F550C. I have read numerous posts on various pages over several weeks now. I have Bumblebee installed and latest Nvidia driver available through Synaptic. Xswat updates are enabled, yet still no 720M seen by Ubuntu. I've done a hardware search with System Profiler, it detects 720M, yet it doesn't appear to be being used by the system. Maybe this is not the case and it is being used under Nouveau, how can I check this if 720M is not shown by Ubuntu? I've checked, I have 3D hardware rendering, this too appears to be working, but as far as I know this can be handled by i7 processor so unsure how to proceed. I've generally been able to solve my own issues simply by reading other posts in the past, this one has me stumped. Hope you can help me as well with this issue? Thanks!

---

### Post by heir4c on 2013-11-22
> **renato3 said:**
> Although I have internet connection running, I get this screen:

[IMG]http://img546.imageshack.us/img546/6498/drad.png[/IMG]

So, there are no drivers for. Maybe with that Bumblebee but I have no experience with that. I use only ATI cards.

---

### Post by Yellow Pasque on 2013-11-23
> **renato3 said:**
> Why not?

Because it will bork the intel driver...
> A gray screen appears, mouse cursor is an X and nothing happens anymore.

---

### Post by Yellow Pasque on 2013-11-23
> **ChrisFromOz said:**
>  Maybe this is not the case and it is being used under Nouveau, how can I check this if 720M is not shown by Ubuntu?

With Bumblebee, the nvidia card will only be used if you specify that it should be used. Check:
```
sudo apt-get install mesa-utils
optirun glxinfo
```

---

### Post by renato3 on 2013-11-23
> **Temüjin said:**
> With Bumblebee, the nvidia card will only be used if you specify that it should be used. Check:
```
sudo apt-get install mesa-utils
optirun glxinfo
```

I installed mesa-utils, but:

```
$ optirun
optirun: command not found
```

---

### Post by Yellow Pasque on 2013-11-23
renato3, that comment was directed at ChrisFromOz. You need to install Bumblebee for optirun to work: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by renato3 on 2013-11-25
> **Temüjin said:**
> renato3, that comment was directed at ChrisFromOz. You need to install Bumblebee for optirun to work: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I didn't understand what's Bumbleblee for, but I'll try to install it.

---

