---
title: "ATI driver recovery. (ubuntu 10.04)"
date: 2011-07-08
forum: Hardware
---

### Post by linux83 on 2011-07-08
Hello Friends,

i'm new on linux, just install ubuntu 10.04 and seem every thing working fine compiz
and virtual desktop.
i was thinking that i can install NVIDIA graphic driver and follow this link:
[http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html](http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html)

finally all my compiz won't work and i'm unable to turn on the virtual desktop.

any help will be appreciated.

i try to install my drivers and follow many links. almost of 3G of my disk gone 
without any thing.

---

### Post by coffeecat on 2011-07-08
You say ATI in your thread title, but nvidia in your post. First thing is to determine what graphics chipset you are using.

Open a terminal (Applications -> Accessories) and post the output of:

```
lspci | grep -i vga
```

---

### Post by linux83 on 2011-07-08
Hello,
first thank you [coffeecat]("http://ubuntuforums.org/member.php?u=129087") for your reply, this is the output:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

just to help you to help me on clear way, my resolution is ok but only compiz is not working
i remove the compiz compleltly and reinstall it and still give me an error that unable to enable desktop effect.

thanks in advance for your help

---

### Post by coffeecat on 2011-07-08
> **linux83 said:**
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

You have an Intel video chipset, which is neither nvidia nor ATI. The link you found is quite irrelevant. You should be able to get compiz with that Intel card in 10.04 and it sounds as though you did at first and something in that link has prevented compiz from working.

By the way, I am unimpressed with that link. A general piece of advice: don't follow howtos on blogs you find on the internet unless recommended by someone you trust or someone on the forum who seems to know what they are talking about.

I'm not sure what is interfering with compiz. I'm going to ask you to run another terminal command and post the output. It is:

```
cat /etc/X11/xorg.conf
```

I suggest you copy and paste that into the terminal so as not to make any typos. You use ctrl+alt+v to paste in the terminal. When you get some output, you can highlight it with the mouse, right-click and choose copy to copy it to the clipboard. Then you can paste it into your post.

---

### Post by linux83 on 2011-07-08
hi,

this is the output:

med@workss:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory


thanks again for your help.

---

### Post by coffeecat on 2011-07-08
That's good. It means that the installation of the nvidia driver was incomplete. If you had installed the nvidia driver you would have had an /etc/X11/xorg.conf file.

I must admit I'm a little short of ideas here. I've not before come across a situation where someone has tried to install the nvidia driver on a machine with Intel graphics. Let's try two more commands. The first tells us which driver is in use with your video card. The second to see if the intel driver has been blacklisted (blocked).

```
sudo lshw -C video
cat /etc/modprobe.d/blacklist.conf
```

The first will prompt you for your password. Don't worry that it doesn't seem to be going in. It is. Just type it and press enter. The second will be fairly long and require some scrolling for you to copy it. Copy and paste into your post as before.

---

### Post by linux83 on 2011-07-08
please find the output:

med@workss:~$ sudo lshw -C video
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8400000-e847ffff ioport:6000(size=8) memory:d0000000-dfffffff(prefetchable) memory:e8480000-e84bffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8500000-e857ffff
----------------------------------------------------------------
med@workss:~$ cat /etc/modprobe.d/blacklist.conf
    # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd



# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
med@workss:~$

also i think i install the ATI driver i can see it under preference-->ATI catalyst

---

### Post by coffeecat on 2011-07-08
You seem to be running the correct driver for the intel graphics, and it is not blacklisted. However...

> **linux83 said:**
> also i think i install the ATI driver i can see it under preference-->ATI catalyst

ATI catalyst is the proprietary driver for ATI cards. You also tried to install the proprietary nvidia driver, but you have an Intel graphics card. What did you hope to achieve with the ATI and nvidia drivers? Whatever has been installed is interfering with the intel driver in unpredictable ways - I would guess.

I suggest you do one of two things:

Re-install Ubuntu 10.04 and enjoy the compiz effects you get with the default video driver and don't be tempted to install any others.

Or...

Hope to be able to fix your system, but I'm out of ideas. You might want to start a new thread because this one will not attract people experienced with Intel chipsets. You need a good title. I suggest "Compiz not working with Intel 945GM after installing nvidia and catalyst drivers".

---

### Post by linux83 on 2011-07-08
[coffeecat,]("http://ubuntuforums.org/member.php?u=129087")

i would like to thank you very much for your help and support,
my issue fixed by removing every thing from Synaptic manager related to ATI.

and rebooting.

thanks again for your effort.

Best Regards.

---

