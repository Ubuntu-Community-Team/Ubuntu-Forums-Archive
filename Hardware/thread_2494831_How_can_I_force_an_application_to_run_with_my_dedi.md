---
title: "How can I force an application to run with my dedicated Nvidia GPU using open source"
date: 2024-01-28
forum: Hardware
---

### Post by awilt on 2024-01-28
'm using the open source Nouveau drivers, and I'd like to be able to  run applications with my dedicated GPU, NVIDIA GeForce MX250 in X11. Proprietary drivers are out of the question for me as they prevent me  from logging in. I tried using prime-run but when i boot minecraft it  shows me that it uses integrated intel graphics, and when i run ```
prime-run glxinfo | grep OpenGL
```, It returns the following output:

 ```
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) UHD Graphics 620 (WHL GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 23.2.1-1ubuntu3.1
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 23.2.1-1ubuntu3.1
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:

``` I'm not sure what this means, but I'm sure its meant to output my dedicated GPU, which shows up no problem in neofetch.

 Sorry if a lot of this information is unnecessary, I don't want to miss anything out

---

### Post by MAFoElffen on 2024-01-28
Prime works with the NVidia driver not with Nouveau...

Why is Nvidia out for you? I have a working work-around for the  6.5.0 series kernels... Yours does work fine with nvidia-driver-535 after using the work around:
[https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

I turned in a Bug Report for them to push ggc-12 through as the default so that we won't have to use that. It is just time.
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457)

Please join that bug as "Also Affected."

---

### Post by awilt on 2024-01-28
Last time i switched to nvidia drivers it installed fine but when i rebooted my system it repeated something about it being a 16 bit system mapped to a 4gb device or something, and then when i finally get to the login screen, I enter my details and just get a black screen. I had to boot into recovery mode and switch the drivers.

I don't understand much on that page, so Are you sure that's the right solution for me? also, I joined the bug as affected

---

### Post by MAFoElffen on 2024-01-28
It depends. Your iGPU is Intel UHD Graphics 620 (WHL GT2) found on 8th Gen Intel CPU's with Integrated Graphics. About low to mid-range benchmarks.

Your NVidia MX250 (GP108) is over 3 times faster.

But you should also be able to run that laptop on the Nouveau driver. maybe via an xorg.conf file, telling the system to use that driver for the GPU.

If you are not confident in command line making changes, you could always follow that bug report and follow when it it resolved. So you can make all you changes through the updates and using the Additional Drivers utility.

Another thing to follow would be this thread I started in the Installations & Updates Section, to try to keep people aware of it's progress: [https://ubuntuforums.org/showthread.php?t=2494834](https://ubuntuforums.org/showthread.php?t=2494834)

---

### Post by Yellow Pasque on 2024-01-28
You should be able to use DRI_PRIME=1. See if this returns info from the Nvidia card:
```
DRI_PRIME=1 glxinfo -B
```

That said, even if DRI_PRIME works, the Nvidia card may be stuck on low clock speed with nouveau because Nvidia never released the power management firmware for your GPU (Pascal core). I know that's the case for desktop GPU's. I guess laptop GPU's will have the same issue. In other words, it wouldn't surprise me if the Intel GPU was faster than using the Nvidia with nouveau.

---

### Post by MAFoElffen on 2024-01-28
> **Yellow Pasque said:**
> In other words, it wouldn't surprise me if the Intel GPU was faster than using the Nvidia with nouveau.
Dang. I forgot about reading slow early benchmarks on NVidia 30XX & 40XX GPU's running Nouveau... About 25 FPS with the newer kernels.

That is just only a bit faster than what the UHD Graphics 620 (WHL GT2) benchmarks at, which I've seen highest at 16.6 FPS.

But an NVidia MX250 (GP108) only benchmarks at between 36 to 54 FPS with the NVidia drivers on a good day.

---

### Post by awilt on 2024-01-29
the output of that command is attatched.

Also, I attempted to create an xorg.conf file before, But whenever I run X -configure i get an error. output also attatched.

---

### Post by MAFoElffen on 2024-01-30
I've used XServer since Unix. I think it's getting that erro becaseu there are two GPU's, but only one Display to connect as a "Screen"...

I create the xorg.conf file from scratch, manually. Since the format, and where all the pieces of that were now divided up into smaller pieces now, the smaller pieces of what might be are located now in these folders
```

/etc/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d
/snap/<version>-core22/3/etc/X11/xorg.conf.d

```
Where the User override file is still created in folder /etc/X11. What you would create is just an xorg.cof fle with your nvidia gpu in the device... 

But to do it to the newer best practices guidelines... 

Remove your NVidia 3rd party drivers... 

Ensure you do
```

lsmod | grep -E 'nvidia|nouveau'

```
To ensure the nvidia modules are removed and the nouveau module is present...

If not there: Either ensure that you remove nouveau from the blacklists... You can use this to find each file where it might be blacklisted:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ for File in /etc/modprobe.d/*.conf /usr/lib/modprobe.d/*.conf /usr/lib/modprobe.d/*.conf ; do echo ""; echo $File; grep 'nouveau' $File; done

/etc/modprobe.d/alsa-base.conf

/etc/modprobe.d/amd64-microcode-blacklist.conf

/etc/modprobe.d/blacklist-ath_pci.conf

/etc/modprobe.d/blacklist.conf

/etc/modprobe.d/blacklist-firewire.conf

/etc/modprobe.d/blacklist-framebuffer.conf

/etc/modprobe.d/blacklist-modem.conf

/etc/modprobe.d/blacklist-oss.conf

/etc/modprobe.d/blacklist-rare-network.conf

/etc/modprobe.d/dkms.conf

/etc/modprobe.d/intel-microcode-blacklist.conf

/etc/modprobe.d/iwlwifi.conf

/etc/modprobe.d/mdadm.conf

/usr/lib/modprobe.d/aliases.conf

/usr/lib/modprobe.d/blacklist_linux_5.15.0-92-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.2_6.2.0-35-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.2_6.2.0-37-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.2_6.2.0-39-generic.conf

/usr/lib/modprobe.d/fbdev-blacklist.conf

/usr/lib/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off

/usr/lib/modprobe.d/systemd.conf

/usr/lib/modprobe.d/aliases.conf

/usr/lib/modprobe.d/blacklist_linux_5.15.0-92-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.2_6.2.0-35-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.2_6.2.0-37-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-6.2_6.2.0-39-generic.conf

/usr/lib/modprobe.d/fbdev-blacklist.conf

/usr/lib/modprobe.d/nvidia-graphics-drivers.conf
blacklist nouveau
blacklist lbm-nouveau
alias nouveau off
alias lbm-nouveau off

/usr/lib/modprobe.d/systemd.conf

```
Each file that is followed by a line starting with blacklist, would be where you need to edit and comment out that line...

Once you ensure the nouveau module is loaded, then you could also then create this as file /etc/X11/xorg.conf.d/20-nouveau.conf:
```

## Example Nouveau /etc/xorg.conf or /etc/X11/xorg.conf.d/20-nouveau.conf file
Section "Device"
    Identifier "Nvidia card"
    Driver "nouveau"
EndSection

```

---

### Post by awilt on 2024-02-03
the lsmod command didnt contain nvidia. I'm assuming thats the desired output.

nouveau doesnt seem to be blacklisted on my system, so ill try create that file and see if it helps anything.

Also, I have two monitors so there should be two displays to connect as a screen?

(The output of the command to see blacklists)
```
/etc/modprobe.d/alsa-base.conf

/etc/modprobe.d/amd64-microcode-blacklist.conf

/etc/modprobe.d/blacklist-ath_pci.conf

/etc/modprobe.d/blacklist.conf

/etc/modprobe.d/blacklist-firewire.conf

/etc/modprobe.d/blacklist-framebuffer.conf

/etc/modprobe.d/blacklist-modem.conf

/etc/modprobe.d/blacklist-oss.conf

/etc/modprobe.d/blacklist-rare-network.conf

/etc/modprobe.d/dkms.conf

/etc/modprobe.d/intel-microcode-blacklist.conf

/etc/modprobe.d/iwlwifi.conf

/usr/lib/modprobe.d/aliases.conf

/usr/lib/modprobe.d/blacklist_linux_6.5.0-14-generic.conf

/usr/lib/modprobe.d/blacklist_linux_6.5.0-15-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-5.19_5.19.0-50-generic.conf

/usr/lib/modprobe.d/fbdev-blacklist.conf

/usr/lib/modprobe.d/nvidia-kms.conf

/usr/lib/modprobe.d/systemd.conf

/usr/lib/modprobe.d/aliases.conf

/usr/lib/modprobe.d/blacklist_linux_6.5.0-14-generic.conf

/usr/lib/modprobe.d/blacklist_linux_6.5.0-15-generic.conf

/usr/lib/modprobe.d/blacklist_linux-hwe-5.19_5.19.0-50-generic.conf

/usr/lib/modprobe.d/fbdev-blacklist.conf

/usr/lib/modprobe.d/nvidia-kms.conf

/usr/lib/modprobe.d/systemd.conf
```

---

