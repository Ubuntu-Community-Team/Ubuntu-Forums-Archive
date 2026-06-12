---
title: "Loading Mac OS X 10.6.3 from Grub almost successful, HELP"
date: 2010-05-27
forum: Hardware
---

### Post by ngativ on 2010-05-27
Hi everyone

I have a macbook 2.1 with Snow Leopard 10.6.2 and Kubuntu 10.04 installed.

Now ... Grub2 is installed in my Linux root partition and refit in the efi master boot. Everything works fine with refit; i am able to boot Snow Leopard (SL) and the grub loader from  refit. But i think that it would be great to bypass the refit menu since grub(-efi64?) (in theory) can make that job already.

So here's the deal: The grub2 scripts detected my Kubuntu OS and also detected my SL, so it generated these entries in the grub menu:

[LIST=1]
[*]Ubuntu, with Linux 2.6.32-22-generic,
[*]Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
[*]Memory test (memtest86+)
[*]Memory test (memtest86+, serial console 115200)
[*]Mac OS X (32-bit) (on /dev/sda2)
[*]Mac OS X (64-bit) (on /dev/sda2)
[/LIST]

1) When i get into the the grub menu and i select Mac OS X (32-bit) to boot, i get the boot  messages from the darwin kernel booting, it look like it really boots but at the end, i just a white screen . Then i press power button, press enter  and my macbook shuts down. It seems to me that booting in 32bit mode works but i having video issues. 

2) If i select the 64bit mode Mac Os X kernel from the grub menu, the boot process stars too in verbose mode. Then, i  get into my Session. But the problem is that my the Video Intel (GMA 950)  kexts is not loaded , so i only get an 1024x728 screen resolution without acceleration support,neither  my Airport wireless and my HD Intel sound card, so they doesn't works.  Is that the grub's  xnu_mkext doesn't load all the kext from the System/Library/Extentesions? 

here it is an  excerpt for my Mac OS X entries  from the /boot/grub/grub.conf



```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8653880178bdcb79
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 8653880178bdcb79 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
	insmod hfsplus
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8653880178bdcb79
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 8653880178bdcb79 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

```

Maybe, loading those missing kexts, from  grub, would help?
From this source [http://grub.enbug.org/XNUSupport]("http://grub.enbug.org/XNUSupport")        i see that i could use the option to load a single kext using xnu_kext. I tried this option passing it to the grub.conf, when loading the Mac Os 64 kernel:
```
xnu_kxet /System/Library/Extensions/AppleIntelGMA950.kext
``` 
 but it doesn't works!

So... any suggestion? :confused:

---

### Post by OpenMinded on 2010-11-02
Hi,

I think this has something to do with the fact that you have to tell grub the EFI settings to detect the graphics card.
The setting is the boot.plist file for all I know.

The other thing that should fix this is use a devtree.
That page just is not clear about how to that:
[http://grub.enbug.org/XNUSupport](http://grub.enbug.org/XNUSupport)

If you have a clue on how to boot OS X with boot.efi like it says and find that grub command, please let me know :).

---

### Post by ngativ on 2010-11-02
> **OpenMinded said:**
> Hi,

I think this has something to do with the fact that you have to tell grub the EFI settings to detect the graphics card.
The setting is the boot.plist file for all I know.

The other thing that should fix this is use a devtree.
That page just is not clear about how to that:
[http://grub.enbug.org/XNUSupport](http://grub.enbug.org/XNUSupport)

If you have a clue on how to boot OS X with boot.efi like it says and find that grub command, please let me know :).

 Sadly my macbook died some time ago. But before that i fixed this problem by not using grub-pc . If you own a mac, then the best  thing that you can do is using grub-efi.
With grub-efi you can boot mac os, windows  and linux in (a lot) faster and natural way. This is even better than using rEFIt.

---

