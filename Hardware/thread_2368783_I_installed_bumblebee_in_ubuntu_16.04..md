---
title: "I installed bumblebee in ubuntu 16.04."
date: 2017-08-15
forum: Hardware
---

### Post by atim0000000 on 2017-08-15
I am a Linux starter. I always got help from people. But I still do not know Linux well. (I am now a C language student, so it is difficult to ask.) 

But I am a beginner and I succeeded in installing bumblebee. I want to help it and post it. (Of course I copied the article here and there.)

The source is at the bottom. But I brought them here and there, not all. please understand. (The following is a summary of my style.)

The laptop I use is gigabyte's P34Gv2. (GTX 860m) And the sentence is strange because it is translated into English. please understand. (I can not speak English.)

I've numbered it for you. You can follow it.


1. $ sudo add-apt-repository ppa:oibaf/graphics-drivers ---> Pre-installed due to error on opengl 4.1 on steam. ===> This area contains unwanted icons. I can not fix it.
    ===> $ sudo apt update
              $ sudo apt upgrade

2. $ sudo add-apt-repository ppa:graphics-drivers/ppa ---> To install the latest nvidia graphic driver.
    ===> $ sudo apt update
              $ sudo ubuntu-drivers list ---> Let's look at the list.
              nvidia-384
              nvidia-381
              nvidia-370
              intel-microcode
              nvidia-340
              nvidia-375
              nvidia-378
              $ sudo apt install intel-micocode
              $ sudo apt install nvidia-384 ---> I installed this.
              $ sudo apt prime-select intel

3. $ sudo add-apt-repository ppa:bumblebee/testing
    ===> $ sudo apt update
              $ sudo apt install bumblebee
              $ sudo apt install primus

Here is the installation. The following are the settings.

1. $ sudo vi /etc/modules ---> Add the following at the bottom
    i915
    bbswitch

2. $ sudo vi /etc/modprobe.d/bumblebee.conf
    -----------------------------------------------------------------------------------------------------
    # 384
    blacklist nvidia-384
    blacklist nvidia-384-updates
    blacklist nvidia-experimental-384       ---> You just need to check this part. If not, add it.
   -------------------------------------------------------------------------------------------------------

    ===> Add the following at the bottom.
    # nVIDIA 384 blacklist
    blacklist nvidia_384
    blacklist nvidia_384_drm
    blacklist nvidia_384_modeset
    blacklist nvidia_384_uvm
    blacklist nvidiafb

3. $ sudo vi /etc/bumblebee/bumblebee.conf ---> If you see the place marked with *, edit it if it is different.
    ...
    # The secondary Xorg server DISPLAY number
    VirtualDisplay=:8 ===> *
    # Should the unused Xorg server be kept running? Set this to true if waiting
    # for X to be ready is too long and don't need power management at all.
    KeepUnusedXServer=false ===> *
    # The name of the Bumbleblee server group name (GID name)
    ServerGroup=bumblebee ===> *
    # Card power state at exit. Set to false if the card shoud be ON when Bumblebee
    # server exits.
    TurnCardOffAtExit=true ===> *
    # The default behavior of '-f' option on optirun. If set to "true", '-f' will
    # be ignored.
    NoEcoModeOverride=false ===> *
    # The Driver used by Bumblebee server. If this value is not set (or empty),
    # auto-detection is performed. The available drivers are nvidia and nouveau
    # (See also the driver-specific sections below)
    Driver=nvidia ===> *
    # Directory with a dummy config file to pass as a -configdir to secondary X
    XorgConfDir=/etc/bumblebee/xorg.conf.d ===> *
    # Xorg binary to run
    XorgBinary=/usr/lib/xorg/Xorg
    ...
    # primus.
    Bridge=primus ===> *
    # The method used for VirtualGL to transport frames between X servers.
    # Possible values are proxy, jpeg, rgb, xv and yuv.
    VGLTransport=proxy ===> *
    # List of paths which are searched for the primus libGL.so.1 when using
    # the primus bridge
    PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus ===> *
    # Should the program run under optirun even if Bumblebee server or nvidia card
    # is not available?
    AllowFallbackToIGC=false ===> *
    ...
    [driver-nvidia]
    # Module name to load, defaults to Driver if empty or unset
    KernelDriver=nvidia-384 ===> *
    PMMethod=auto ===> *
    # colon-separated path to the nvidia libraries
    LibraryPath=/usr/lib/nvidia-384:/usr/lib32/nvidia-384 ===> *
    # comma-separated path of the directory containing nvidia_drv.so and the
    # default Xorg modules path
    XorgModulePath=/usr/lib/nvidia-384/xorg,/usr/lib/xorg/modules ===> *
    XorgConfFile=/etc/bumblebee/xorg.conf.nvidia ===> *

    ## Section with nouveau driver specific options, only parsed if Driver=nouveau
    [driver-nouveau]
    KernelDriver=nouveau ===> *
    PMMethod=auto ===> *
    XorgConfFile=/etc/bumblebee/xorg.conf.nouveau ===> *

4. $ sudo vi /etc/bumblebee/xorg.conf.nvidia 
Locate the "BusID" entry. If there is a "#" in front, remove it. Save and exit.

BusID "PCI:01:00:0" ---> This is my case.

Let's check if it is correct.

  $ lspci | egrep 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2) ---> It is the same. It is good.

Finishing also follows.

  $ sudo systemctl enable bumblebeed

5. I have never experienced OpenGL issues. I did it simply because it was in the original.
$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf ---> Select the file name that contains "mesa".

====================================================================================================
There are 3 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).

  Selection    Path                                                   Priority   Status
-----------------------------------------------------------------
   0            /usr/lib/nvidia-384/ld.so.conf                    8604      auto mode
   1            /usr/lib/nvidia-384-prime/ld.so.conf           8603      manual mode
   2            /usr/lib/nvidia-384/ld.so.conf                    8604      manual mode
* 3            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode

Press <enter> to keep the current choice
[*], or type selection number: 3
====================================================================================================

Do the same for the next two.

$ sudo update-alternatives --config i386-linux-gnu_gl_conf
 $ sudo update-alternatives --config x86_64-linux-gnu_egl_conf

It's all over. Restart the system.
 $ sudo reboot

Since then I have done one more thing.
 $ optirun -b none /usr/bin/nvidia-settings  -c :8 ---> "NVIDIA X Server Settings" The window pops up.
  Antialiasing Settings -> Override Application Settings -> "Enable FXAA" check

I remember working today. I forgot to run bumblebee. For example, to run steam or nexuiz
$ optirun steam
$ optirun nexuiz

When I do BioShock Infinite with steam, the cooling fan makes a lot of noise. However, Half-Life 1 is quiet. Bumblebee seems to be doing well.
By the way, glxgears will average 60 frames. Probably because of primus. Anyway, I am satisfied that the cooling fans do not make a lot of noise when I use Half Life 1.

Referenced site:
[https://www.pcsuggest.com/nvidia-optimus-ubuntu/](https://www.pcsuggest.com/nvidia-optimus-ubuntu/)
[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)
[https://xipherzero.com/ubuntu-optimus-configuration/](https://xipherzero.com/ubuntu-optimus-configuration/)

---

### Post by efflandt on 2017-08-15
You should not need to use bumblebee. The last time I used that was in Ubuntu 13.10, before nvidia-prime was in Ubuntu 14.04. Bumblebee funnels your nvidia graphics through the Intel graphics for output. The advantage of bumblebee is that you can use it on the fly to switch graphics (using optirun), but the disadvantage is that it makes either graphics slower than it would otherwise be and you have to use extra parameters for games beside launching either steam or the game with optirun, and figuring out what other parameters you might need might not be easy to find. I never could get primusrun to work in 13.10, but optirun worked. I cannot access those extra optirun parameters for Source games at the  moment because my gaming laptop died (will not turn on properly).

Current nvidia drivers come with nvidia-prime which can switch to either Intel or Nvidia graphics (faster for either) using **NVIDIA X Server Settings**, but when switching graphics you may have to either exit X and log back in (switching Nvidia to Intel), or possibly reboot (switching Intel to Nvidia). Besides being faster because either graphics is dedicated at the time, you do not need any extra parameters for games.

The 60 fps limit for glxgears is probably due to either having "Sync to vblank" (vsync) enabled in Nvidia settings, or because it is funneled through the Intel graphics limited to refresh rate of your display when using bumblebee.

---

### Post by atim0000000 on 2017-08-18
Hello.

Thank you for answer. It's amazing that someone reads my post. I still do not fully understand what you are giving. 
It is sad that Linux is not as controllable as Windows. Linux can not use either Intel or nvidia. T.T 
Although it is controlled by intel, it is good to be able to keep Half Life 1 quiet. 
Someday, like Windows, Bioshock Infinite will be quiet.

Have a nice day.

---

