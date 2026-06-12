---
title: "Problems with NVIDIA drivers in Ubuntu 18.04"
date: 2018-08-27
forum: Hardware
---

### Post by romanessp on 2018-08-27
I recently purchased a Lenovo ThinkSystem SR630 Rack Server with a NVIDIA Quadro P600 graphic card.

I wanted to install Ubuntu 18.04. I inserted the installation live DVD and everything seems to work ok (I'm referring to the graphic interface), so I did install the OS successfully. Then I tried to log in (log in screen shows up correctly), and the graphic interface then goes all wrong and I can only see red horizontal lines, as it if were codified. If I try to log in with Wayland (a new concept for me), it does work, but it is sooooo slow while moving the mouse cursor or even while typing on the console. I can also log in at the console mode.

At this point, I assumed (and maybe I am wrong assuming this) that the Intel default graphic card was being used for the Wayland session (and that's why it is so slow), and that NVIDIA card with nouveau drivers were being used in the default sessions (and they don't work, and that's why it looks like that).

My next step was installing NVIDIA propietary drivers. I installed recommended version 390. They are successfully installed, but both session types are behaving the same (default no graphics, wayland slow). I checked with "nvidia-settings query" command that the nvidia card is set as the graphic card in use (but that not what is stated if I go to Settings -> Details -> About; Here, llvmpipe library is shown). Also, if I enter command "glxinfo | grep OpenGL" I also get llvmpipe library, as shown here:

OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLM 6.0, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.0.5

After reading other people's problems with nvidia390 drivers in Ubuntu 18.04, I decided to go with an older drivers version currently suporting my graphic card: 375 and 38 
package nvidia-384, which is restricted, but it is not found using apt-get command. I checked my current repositorioes (default, as I have not added nor removed any repositories since I installed the system), and restricted is supposed to be enabled.

Running out of options, I installed Ubuntu 18.04 server, installed nvidia-390 drivers, and then installed gnome dektop packages [as detailed in this web]("https://linuxconfig.org/how-to-install-gnome-on-ubuntu-18-04-bionic-beaver-linux"). Nevertheless, after rebooting I get to log in at console mode again, but the GUI log in is never shown. Also, I tried installing them manually from the .run file provided by NVIDIA, but the compilation failed and I got zero assistance from NVIDIA, so I finally installed the ones in ubuntu repositories.

Then I tried with Ubuntu 16.04 desktop, and the installation DVD states that there is not enouogh space for installation: 0 Mb available. It seems that no hard disk is detected with Ubuntu 16 installer, which is weird.

At this point, I could try manually installing nvidia-396 drivers, but they aren't available for Quadro P6000 in Nvidia web for Linux 64bit. I could also try installing Ubuntu 17.04 and crossing my fingers and pray for everything to work nicely from the beginning. Final attempt will be changing to a different Linux distro, which I rather not.

I could live with a different dektop from gnome too, but I don't think that's the problem. If so, please tell me so I can try lubuntu/kubuntu.

Can you please provide any help on this?

BTW: How is it possible that graphics work correctly on live cd, but after installation they don't work at all?

---

### Post by pqwoerituytrueiwoq on 2018-08-27
On the live session you are using the open source drivers
purge the nvidia drivers to use them
[FONT=courier new]sudo apt-get purge nvidia-*
rm /etc/X11/xorg.conf[/FONT]

If you would like to use the nvidia drivers can you tell us what gpu you have?
l[FONT=Courier New]spci|grep -i vga[/FONT] will give us that info (edit: quadro p6000)

---

### Post by romanessp on 2018-08-27
> **pqwoerituytrueiwoq said:**
> On the live session you are using the open source drivers
purge the nvidia drivers to use them
[FONT=courier new]sudo apt-get purge nvidia-*
rm /etc/X11/xorg.conf[/FONT]

If you would like to use the nvidia drivers can you tell us what gpu you have?
l[FONT=Courier New]spci|grep -i vga[/FONT] will give us that info (edit: quadro p6000)

The problem is that open source drivers (nouveau) are also loaded when the installation is over. I cannot run the Gnome session with them as I described in OP, and wayland works with very bad performances (in fact I just learned that Wayland is no compatible with Nvidia propietary drivers, so I suppose it doesn't matter as I'll have to stick to the gnome session).

Therefore, removing propietary drivers will leave me in the first step of my journey again, which wasn't working.

On the other hand, my last attempt has been disabling wayland by uncommenting the line "waylandEnable=false" in /etc/gdm3/custom.conf. When the OS boots, it gets stuck at a blank screen which just states: "/dev/sda2: clean 170956/3055616 files, 1502907/12207024 blocks". By the way, this was where I ended after installing gnome desktop packages in the ubuntu server attempt.

Any other idea?

---

### Post by pqwoerituytrueiwoq on 2018-08-27
have you tried booting with the nomodeset kernel parameter?

---

### Post by oldfred on 2018-08-27
Someone posted this:
       17.10 defaults to wayland where nvidia's driver don't work 
    
And 18.04 changed to not use wayland by default because of several issues.

---

### Post by chidley156 on 2019-04-11
Last night I installed Ubuntu 18.04 Bionic Beaver Linux on my desktop PC by completely whipping out Windows 7 OS. So after proper Linux installation the first problem I faced was low resolution display which was totally annoying me given that I have a NVIDIA Geforce GTX 750 TI graphics card installed in the machine [[COLOR=#000000]UPSers[/COLOR]]("https://www.upsers.online/").

---

### Post by oldfred on 2019-04-11
You just need to install the correct nVidia driver from Ubuntu repository.

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by Autodave on 2019-04-11
418 is the newest driver, but I have heard reports that there are still some bugs in that.  I would go with either the 410 or 415 driver.

---

### Post by hgkrug1 on 2019-05-23
I have the same problem on Ubuntu 19.04. 415 driver did not work for my case - gave error upon installation. I found at least a method to restore the Ubuntu Desktop - see entry #17 of [https://ubuntuforums.org/showthread.php?t=2411777&page=2](https://ubuntuforums.org/showthread.php?t=2411777&page=2) 

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

### Post by hgkrug1 on 2019-05-23
I have a NVIDIA Corporation GP107 [GeForce GTX 1050]and run Ubuntu 19.04.  According to Nvidia ([https://www.geforce.com/drivers/results/147582](https://www.geforce.com/drivers/results/147582)), the correct driver for it is the 430.14 version. I suspect that is the default one that is downloaded when you use "sudo apt install nvidia-driver-430", which give me the same problem.

---

### Post by hgkrug1 on 2019-05-23
I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread....nvidia+drivers]("https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers"), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

---

