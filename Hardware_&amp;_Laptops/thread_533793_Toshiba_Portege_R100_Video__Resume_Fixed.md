---
title: "Toshiba Portege R100 Video / Resume Fixed"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by cynfewl on 2007-08-24
Below are some observations on running Feisty on a Toshiba Portege R100.

**Video (Trident Microsystems CyberBlade XP4m32 using xorg trident driver)**
The video card in this unit appears to have a known issue with acpi state change (ac -> battery).  What happens is the video is resized so you only see a corner of the screen. You can fix this temporarily by switching to the first console and back (ctrl-alt F1, ctrl-alt F7). This appears to be a bug in the driver itself. A workaround for this issue is to append the kernel option vga=791 in your grub menu.lst file. My testing appeared to show that you can replicate the issue simply by trying to change the screen brightness.

Following are the options I enabled to get this workaround in place.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
defoptions=quiet splash vga=791
```

My theory was the above code would append this option to any new kernels. Of course, this won't affect the current kernel, so I modified that line too.

```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=4918ce99-94aa-4145-bb4f-b8783c0482c4 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

Reboot the machine so these settings go into effect. This should get you to a state where you can unplug the ac and the resolution will stay the same.

**Resume**
To get resume working on this laptop (suspend worked out of the box, as did hibernate), make the following changes to /etc/default/acpi-support. We need SAVE_VBE_STATE as otherwise our kernel options from above are lost when we cold boot the video driver (the POST_VIDEO=false option).

```

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false
```

I also modified /usr/share/acpi-support/TOSHIBA.config. I'm not sure if this modification did anything, but here is the contents of the new file just in case.

```

case "$model" in
        "libretto U100"*)
                ACPI_SLEEP=true
        ;;
        "P4000"*)
                ACPI_SLEEP=true
        ;;
        "PORTEGE A100"*)
                ACPI_SLEEP=true
        ;;
        "PORTEGE A200"*)
                ACPI_SLEEP=true
        ;;
        "PORTEGE M200"*)
                ACPI_SLEEP=true
        ;;
        "PORTEGE R100"*)
                ACPI_SLEEP=true
        ;;
        "PORTEGE R200"*)
                ACPI_SLEEP=true
        ;;
        "Satellite 1900"*)
                ACPI_SLEEP=true
        ;;
        "Satellite M70"*)
                ACPI_SLEEP=true
        ;;
        "TECRA A2"*)
                ACPI_SLEEP=true
        ;;
        "TECRA A5"*)
                ACPI_SLEEP=true
        ;;
        "TECRA M2"*)
                ACPI_SLEEP=true
        ;;
esac
```

With these modifications, this laptop is not only portable, but distinctly usable as well.

---

### Post by ddrichardson on 2007-08-25
This is some great information - have you considered entering it on the [wiki]("https://help.ubuntu.com/community/")?

---

### Post by Lokasvami on 2007-09-20
Great information, my R-100 is much happier now !

I have one last remaining problem with my Toshiba (I hope its the last), when I enable desktop effects, I get a white screen. I have not found any information relating this problem to the Toshiba R-100. Any help on how to overcome this problem would be greatly appreciated.

---

### Post by Quoll on 2007-10-18
Brilliant!

I had it sort of working, but resume was always a bit unstable. This has sorted it.

Thank you.

---

### Post by RedPillMode on 2007-11-05
Hello, this does not seem to work with 7.10. Any thoughts? Maybe I should start new topic.

---

### Post by uki on 2007-11-19
sadly these tips don't resolve the graphics problems my dear r100 is experiencing with kubuntu 7.10.

any ideas?

---

### Post by fsman on 2008-01-18
Doesn't work in Gutsy for me either. 
All is uk upto the GDM logon screen. 
However when it goes into the ubuntu desktop, my screen flickers (I assume a screen resolution reset) and then it falls into 800x600. A quick ctrl+alt F1 followed by ctrl+atl F7 corrects, but it is a pain in the butt and work get my wife and daugher to stop using windows XP.

Help me fix this and I can wide off windows...

---

### Post by cynfewl on 2008-03-26
The issues with Gutsy are related to the framebuffer module not being loaded by default.

This is dealt with in the following post:

[http://ubuntuforums.org/showthread.php?t=652038](http://ubuntuforums.org/showthread.php?t=652038)

If you enable the vesafb module (by commenting it out from /etc/modprobe.d/blacklist-framebuffer), the fix listed above should work.

One thing to be aware of in the original fix is that you don't need to uncomment the defoptions directive. You can simply add the "vga=791" option to the end and then run update-grub as root to get all listed kernels to inherit this option.

/etc/default/acpi-support in Gutsy also uses POST_VIDEO=true, which seems to work with the new version of xorg.

Now if only evolution worked properly I would never need Windows again...

---

