---
title: "Solution sharing for Intel HD Graphics card no HDMI output"
date: 2014-03-02
forum: Hardware
---

### Post by Psycopatologic on 2014-03-02
More than a questin i'm here to share a recent solution about an issue with my brand new laptop Lenovo G400s, Intel Core i5 3230m, 4 Gb Ram DDR3, Intel HD Graphics integrated card. I hae a dual boot with Windows 7 and ubuntu 13.10 on it, and i was having issues with the HDMI output. I installed the Intel Linux driver via the official release ([https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)) but still Ubuntu does not recognize the HDMI output. Then doing some research i remembered the fact that i add an option to grub that was nomodeset=0, an i realized that it was forcing my Intel drivers not to load. I edited the grub loader file /boot/grub/grub.cfg and i deleted every entry for the option nomodeset, and after a reboot everything it's working great.

I'm hoping that anyone can use this info, cause' it took me two days to fiure uot this.

---

### Post by Bashing-om on 2014-03-03
Psycopatologic; Thanks for the sharing !

Where though did you make that initial "nomodeset" edit ? ,, -> /etc/default/grub ?
Yes ? Then, if that file has not been edited to remove the option, when grub is once more updated, all your changes to "/boot/grub/grub.cfg" will be over written.
Make your change to /etc/default/grub file and for the change to be propagated:
terminal code:
```

sudo update-grub

```

sure ->
[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

