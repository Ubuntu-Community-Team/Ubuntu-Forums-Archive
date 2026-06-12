---
title: "MSI GS30 Gaming Dock support"
date: 2017-02-26
forum: Hardware
---

### Post by adrizein on 2017-02-26
Hello everyone !

I've had an MSI GS30 Laptop with a gaming dock equipped with an Nvidia GTX970 for several months now: [https://www.msi.com/Laptop/GS30-2M-Shadow.html#hero-specification](https://www.msi.com/Laptop/GS30-2M-Shadow.html#hero-specification) 
It has been running on Windows 10 pretty well until now, but I decided to install a dual boot Windows 10 - Ubuntu 16.10. 
I replaced the 2 128GB SSD in RAID0 by two 525GB SSD without RAID where one contains Windows, and the other Ubuntu. The CPU is an Intel i7 4720-HQ, and the laptop has 16GB of RAM.
Everything works fine when the laptop is disconnected from the dock, but I have some weird issues on Ubuntu when booting it from the dock.

To put things in context, here is how the dock is supposed to work:
 
[LIST]
[*]It contains a dedicated **desktop** GPU
[*]When the laptop is disconnected from the dock, booting the laptop launches grub (in my case), and the laptop screen uses the integrated GPU (Intel Iris 5200 Pro)
[*]When the laptop is connected to the dock, the laptop should be closed and booting should be done using the dedicated button on the dock.
[*]Once the laptop is booted in dock mode, it should load grub, launch the specified OS and **_only use the dedicated GPU_** (GTX970 in my case) to display on an **external** screen.
[*]Hot plugging and unplugging is not expected to work at all and is in fact strongly discouraged as it shutdowns whole system immediately
[*]The dock also provides USB, RJ45, and audio I/O ports, which I use to connect a mouse, a keyboard, to my local network and my headphones.
[/LIST]

All of these features work as expected on Windows 10 launched from grub.
To make these features work on Ubuntu 16.10 here is what I did:
[LIST=1]
[*]install the nvidia-367-dev package
[*]add the **nomodeset** boot option in /etc/default/grub
[*]run the update-grub command
[*]reboot the computer
[/LIST]

This got Ubuntu 16.10 to boot successfully up to the login screen. Now, [B]this is my current problem:
[/B]Once I finally get the the login screen, I can enter my credentials, **login successfully**, and use the computer for a few seconds until the systems goes back to the login screen on its own...
When I re-enter my credentials, I again log successfully, and can use the computer for a few seconds but at this point the computer either re-closes the session or stops sending the video signal to the external screen.
Also, when my headphones are disconnected, the integrated speakers in the dock do small "pop" sound which is followed by some white noise, but that's a minor issue.

For full disclosure I plan to use this gaming dock for gaming on Windows and for CUDA on Ubuntu.

Thanks a lot in advance for any help :)

---

### Post by adrizein on 2017-02-26
Ugh... I finally figured out what was happening... It's just that when the lid of the laptop is closed (even if it has been closed since the bootup) , the power saving option activates and puts the laptop into hibernating, which looks like shutting down from my perspective since I'm looking at the external screen.

So I simply set the following option in the power settings as presented here: 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=273903&d=1488131256[/IMG]

And then I unchecked the following box in the Security & Privaty settings:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=273904&d=1488131257[/IMG]

And this solved the problem, the active GPU is the nVidia GTX970 and the loaded driver is nvidia-367. I'll test intensive GPU load ASAP and return here if something bad happens.

Anyway, I hope this will help people with the same issues as me.

---

### Post by oldrocker99 on 2017-02-26
Welcome to the forums!

Since you solved your own problem, please use the Thread Tools to mark this thread as [SOLVED].

---

### Post by adrizein on 2017-03-05
Hello again,

Turns out my problem is still here, but now happens in laptop mode, so when the laptop is not on the dock and the integrated GPU is supposed to be active.
I think I figured out the problem, but I don't know how to solve it in practice.
When my laptop boots on Ubuntu I think that the Xorg conf is stuck with the nVidia driver and tries to use the dedicated GPU. 
When the laptop is on the dock, no problem, it works. But when the laptop is in laptop mode, I think that Xorg fails to find the driver of the integrated GPU or tries to use the nVidia driver.

So I think that I should write a custom Xorg conf to specify that my system should try to use the nVidia GPU with the nVidia driver and if it fails, it should fallback to the integrated GPU with the Intel driver.
I have no idea how to do that, or if it even makes sense, so I'd be extremely grateful if someone could help.

**Note**: I deleted to my xorg.conf in hope that it would reset the conf to something that works in laptop mode. I also tried to boot in failsafe mode multiple times but it didn't work.
Here is my xorg.conf.failsafe file.
```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection


Section "Monitor"
    Identifier    "Configured Monitor"
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

Here is the output of **lspci -nnk | grep VGA**:
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM204 [GeForce GTX 970] [10de:13c2] (rev a1)

```

Here is the output of **lshw -C video**:
```

  *-display                 
       description: VGA compatible controller
       product: GM204 [GeForce GTX 970]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:37 memory:a0000000-a0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:a1000000-a107ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a1400000-a17fffff memory:b0000000-bfffffff ioport:6000(size=64)

```

---

### Post by adrizein on 2017-03-05
Removing the nomodeset option in /etc/default/grub works without the dock, and activating works with the dock. I'll try to create two separate grub configs: one with nomodeset and one without so I can select the correct one at boot.

---

### Post by adrizein on 2017-03-05
So I think I finally cracked it!
Here is the first solution I found: I added the following custom grub entry in **/etc/grub.d/40_custom** (full file)[B]:
[/B]```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu NVIDIA" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-nvidia-6c8b96e6-401e-4187-a74a-fe21c32282bf' {
    recordfail
    load_video
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  6c8b96e6-401e-4187-a74a-fe21c32282bf
    else
      search --no-floppy --fs-uuid --set=root 6c8b96e6-401e-4187-a74a-fe21c32282bf
    fi
    linux    /boot/vmlinuz-4.8.0-39-generic.efi.signed root=UUID=6c8b96e6-401e-4187-a74a-fe21c32282bf ro  quiet splash nomodeset $vt_handoff
    initrd    /boot/initrd.img-4.8.0-39-generic
}

```
I basically copy/pasted the first menuentry of **/boot/grub/grub.cfg** which starts with the following line:
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6c8b96e6-401e-4187-a74a-fe21c32282bf' {
```
and I changed the title "Ubuntu" in "Ubuntu NVIDIA" and added this infamous nomodeset option. I also replaced the word "simple" by "nvidia" but I'm not sure this is necessary.
Finally, I did a **sudo update-grub.**
Now when I boot my laptop I have an extra grub entry called "Ubuntu NVIDIA" which works with the dock. When my laptop is not on the dock, I can use the default "Ubuntu" grub entry.

This works pretty well but it has the drawback of having to be maintained manually at every kernel update.

Instead I applied the following solution: I edited the **/etc/grub.d/10_linux **file, here is the diff against the original version:
```

115c115
<   if [ x$type != xsimple ] && [ x$type != xnvidia ]; then
---
>   if [ x$type != xsimple ] ; then
132,138c132,133
<       if [ $type = simple ]; then
<             title="$os"
<       else
<             title="$os NVIDIA"
<       fi
<       echo "menuentry '$(echo "$title" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-$type-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
<   fi
---
>       echo "menuentry '$(echo "$os" | grub_quote)' ${CLASS} \$menuentry_id_option 'gnulinux-simple-$boot_device_id' {" | sed "s/^/$submenu_indentation/"
>   fi      
336,338c331,332
<     linux_entry "${OS}" "${version}" nvidia "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_LINUX_DEFAULT} nomodeset"
< 
<     linux_entry "${OS}" "${version}" simple "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_LINUX_DEFAULT}"
---
>     linux_entry "${OS}" "${version}" simple \
>     "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_LINUX_DEFAULT}"

```

Now each time the **update-grub **command is called (by me or by a kernel-update) it will generate the "Ubuntu NVIDIA" entry **at the top of the menu.**

---

