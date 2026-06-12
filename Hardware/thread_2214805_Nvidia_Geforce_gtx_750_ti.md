---
title: "Nvidia Geforce gtx 750 ti"
date: 2014-04-03
forum: Hardware
---

### Post by the-duck2 on 2014-04-03
Hi, i'm new here:)
I have a problem with my graphics card, it's a brand new nvidia geforce gtx 750 ti, i know that the problem is its a new card. The nouveau driver can't read it at all, so i installed an nvidia driver but it didn't work.. Then I thought it might be the kernel which is too old. What i'd like to know is whether it's a kernel problem, and if i'll be able to use it with ubuntu 14.04. Or will i have to install an unstable kernel?

---

### Post by Yellow Pasque on 2014-04-03
What version of the nvidia driver did you try to install (and how did you try to install it)?

---

### Post by the-duck2 on 2014-04-03
I installed 334.21 through a ppa (as no older one supports it), but i think i ended up removing it as it didn't work. 
The thing is when i booted with the graphics card, the boot screen freezed and it showed messages from nouveau (the current driver). It didn't seem to be able to read it at all. I thought that nouveau driver would support any card.
I have kernel version 3.11, dunno if thats the problem.

---

### Post by sudodus on 2014-04-03
It is worth trying Trusty Tahr, but don't install it, try it live (booted from the DVD or USB install drive). That will show if it works with its new nouveau version.

---

### Post by Yellow Pasque on 2014-04-03
> **sudodus said:**
> It is worth trying Trusty Tahr, but don't install it, try it live (booted from the DVD or USB install drive). That will show if it works with its new nouveau version.

It won't because Trusty's kernel is too old. Basic Maxwell support is coming in kernel 3.15: [http://www.phoronix.com/scan.php?page=news_item&px=MTY0MzQ](http://www.phoronix.com/scan.php?page=news_item&px=MTY0MzQ)

---

### Post by Yellow Pasque on 2014-04-03
> **the-duck2 said:**
> The thing is when i booted with the graphics card, the boot screen freezed and it showed messages from nouveau (the current driver).

Are you saying that happened while you had the proprietary driver installed?

---

### Post by the-duck2 on 2014-04-03
> **Temüjin said:**
> Are you saying that happened while you had the proprietary driver installed?

When i had nouveau installed, nvidia driver didn't work either..

---

### Post by the-duck2 on 2014-04-03
Aaaah, ok... So I saw my graphics card is based on maxwell architecture, and you just said kernel 3.15 supports it. I suppose i'll have to upgrade my kernel and see if it works.
Is there a way to install kernel 3.15 on ubuntu?

---

### Post by the-duck2 on 2014-04-03
But do you think nvidia drivers can read a maxwell-based gpu directly, without the appropriate kernel?

If that's possible I'll try to reinstall the driver, but i don't expect too much, I might have not installed it correctly and nouveau was still the main driver..

---

### Post by the-duck2 on 2014-04-03
[http://ubuntuforums.org/showthread.php?t=2214794](http://ubuntuforums.org/showthread.php?t=2214794) it worked for him, in a strange way but it worked

---

### Post by Yellow Pasque on 2014-04-04
> **the-duck2 said:**
> When i had nouveau installed, nvidia driver didn't work either..

You're confusing me. Are you saying that nouveau was loaded and generating error messages while the proprietary driver was installed? Maybe you need to manually blacklist nouveau module.

---

### Post by Carlos_Eduardo_Gel on 2014-04-04
It seems like the nvidia 750 models are not working on Linux, I have a dell inspiron 14R 5437-A40 with hybrid cards an intel and a nvidia GT 750M and I wasn't able to make work, I follow instructions on bumblebee and without bumblebee (with nvidia card running all the time). (on Ubuntu 13.10)

After login I get a black screen without bumblebee. 

And with bumblebee using the command "optirun glxgears" I get a message saying "Cannot access secondary GPU" "No devices detected". The nvidia card show up in lspci.

If someone made an nvidia 750M work on Linux, please tell us!!!

---

### Post by pqwoerituytrueiwoq on 2014-04-04
I would suggest trusty beta using the xorg edgers ppa with the 3.14 kernel
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) [FONT=courier new]sudo apt-add-repository ppa:**xorg-edgers/ppa -y;sudo apt-get dist-upgrade[/FONT]
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme) - easy installer for mainline kernels
pop in a spare hdd to try it to be sure it works if there is anything important on your install
i have upgraded a 13.10 install to 14.04, if you do that do it from a tty

---

### Post by Yellow Pasque on 2014-04-04
> **Carlos_Eduardo_Gel said:**
> It seems like the nvidia 750 models are not working on Linux, I have a dell inspiron 14R 5437-A40 with hybrid cards an intel and a nvidia GT 750M

The 750M is based on an older Kepler chip and used in Optimus/hybrid configuration. Your hardware is very different than the OP's (other than the meaningless model number). Please start your own thread.

---

### Post by Carlos_Eduardo_Gel on 2014-04-04
> **Temüjin said:**
> The 750M is based on an older Kepler chip and used in Optimus/hybrid configuration. Your hardware is very different than the OP's (other than the meaningless model number). Please start your own thread.

Ok, but anyway, do you think that it would be a good idea to do what pqwoerituytrueiwoq said? Try trusty?

Thanks.

---

### Post by sudodus on 2014-04-05
It costs only yours time to download and test Ubuntu Trusty, so if you have the time, please try :-)

---

### Post by zob on 2014-05-11
I guess I should add that it works for me
This is my card:
```
 *-display               
       description: VGA compatible controller
       product: GM107 [GeForce GTX 750 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:46 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

```
```
~$ nvidia-smi
Mon May 12 02:05:39 2014       
+------------------------------------------------------+                       
| NVIDIA-SMI 337.19     Driver Version: 337.19         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 750 Ti  Off  | 0000:01:00.0     N/A |                  N/A |
| 33%   32C  N/A     N/A /  N/A |    615MiB /  2047MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+
```
My system:
```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
3.13.0-24-generic

```

Until a moment ago I was convinced that I had to add nomodeset to grub not to get a black screen at boot, but I just looked in /etc/default/grub and it's not there, so maybe that was only in 13.10 (where it also worked for me).
EDIT: I think you will need nomodeset to boot with the open source noveau drivers.
[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

Please note that I installed the most recent (and unstable) drivers from the xorg edgers ppa as someone mentioned earlier.

I'm not a native english speaker but there is some kind of tearing or flickering at times, I'm not sure of the excact word. But it's not too bad.

You might be interested in this article: [http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

### Post by sudodus on 2014-05-12
Thanks for sharing your results, *zob* :KS

---

### Post by jasmin-beauregard-c on 2014-07-21
Had the same problem. Couldn't login at initial 14.04 installation. I "Ctrl-Alt-F1" to get to the terminal and installed NVIDIA-331. It's one of the standard proprietary driver supplied with initial 14.04 installation. It's not fully compatible and it's the reason why it's not shown when you try to detect an available driver, but at least, I could log into Unity. Then, I downloaded the driver 337.25 from NVidia site and followed the installation instructions (stop lightdm, remove nvidia-331, execute the NVidia~337.25.run)

It solved my problem. Hope it may help some of you. By the time I'm writing this, NVidia is at 340.24. Going to try it as soon as I'm home. :)

---

### Post by sudodus on 2014-07-21
Welcome to the Ubuntu Forums *[COLOR=#000000]jasmin-beauregard-c[/COLOR]*,

and thanks for sharing your results :-)

---

### Post by oldrocker99 on 2014-08-23
According to Phoronix (yes, I know that you sometimes might want to consider that source, but...), the Nouveau driver does not yet support the architecture of the 750 and 750ti. The 334+ drivers from nVidia work great.

---

### Post by wayne20 on 2014-09-11
I have and eVGA 750Ti running 3 displays using Xinerama on Ubuntu 14.04.1 with the NVIDIA 340.32 driver and I only have a couple of issues :p.  Xrandr is broken, and occasionally the system will hang on boot.  I'm sure the latter is due to some video setting weirdness as a boot to recovery and resume works fine.  I tried "nomodeset" but that gave me several complains after login. I forgot what a problem new hardware could be.

It's AWESOME when it's working ;)!

---

### Post by anika200 on 2014-09-11
The Nouveau does not work with this card, you definitely need to set nomodeset in the grub boot menu and then eventually make it permanent.
You will need to use the proprietary drivers to get the full use of your card, openGL and other cool things like energy savings.

The install goes fine because it uses vesa mode driver but as soon as you reboot after install you will be at a blank screen without the nomodeset.
Then you will be without opengl and other things until you get the Nvidia drivers installed, even the graphic driver finder does not work to get you drivers.

I have PNY 750Ti for 6 months or so now and through several distro and kernel it is the same.

I have been running the current beta from Nvidia 343.13  and it is working well so far.

oh yeah I agree with wayne20 -- they are awesome :smile:
I am on Kubuntu 14.04 with updates and backports.

---

### Post by psignosis2 on 2014-09-29
I've been using Nvidia 343.22 and everything has been working nicely with the exception of Thunderbird and Firefox. There's a lot of flickering/fluttering/flashing going on in those two applications. I've tried disabling all addons, disabling layer acceleration, disabling hardware acceleration, disabling/enabling smooth scrolling, and playing with the OpenGL settings "Allow Flipping" on/off. Nothing has made a difference except that last one - there was some improvement in the erraticness/rapidity of the flashing or flickering, but it was still there and slower.

750ti with a 2560 display. Any suggestions would be very appreciated! Thunderbird in particular is infuriating with this. I'll go to those forums next - it does appear limited to just these two Mozilla items.

Edited to add: It appears to have been the 343.22 after all. Went back to the open source 340.46 and all is well.
Edit # 2: Nope, it was good for a few days and now the flickering has returned, only in these two apps though.
Edit # 3: Yikes, it's a bug (#1314367). Turning on "Force full screen redraws (buffer swap) on repaint" in Compiz Config Settings Manager (under "Workarounds") fixed it.

---

