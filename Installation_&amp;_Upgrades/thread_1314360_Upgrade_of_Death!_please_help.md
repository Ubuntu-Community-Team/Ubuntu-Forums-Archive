---
title: "Upgrade of Death! please help"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by bobdotexe on 2009-11-04
I was upgrading my tablet PC from xbuntu 9.04 to 9.10
it was taking forever, so I let it upgrade overnight (using full duplex {probably the problem})

any way, the next day someone unplugged it while I was at school;
and the battery ran dead, I figured it was fine (last nite it said 6hr till complete)

So I booted it up an I got an error:

```


Init: mountall main process (636) terminated with status 127


```
I tried all the recovery stuff from grub, but nothing works!
So I figured I would just reinstall or attempt a repair using the alternet install disk. (pc has no floppy drive/cd drive, and 1 usb port, 1 cf slot)

I tried a network install, but my pc would not connect, so I built a bootable CF card, in hopes of a direct boot,
but grub could not find it; so I tried USB and Grub did not see that ether.

My bios only allows booting from NET/HD/FD but I have no floppy drive, and I cant install another boot loader, because I have no bootable media, and I cant access the files on the HD...


dose anyone know how I can BootUp and maybe save my files???

---

### Post by cariboo on 2009-11-04
Have you tried starting in recovery mode and select drop to boot prompt with networking?

If you can do the above, at the prompt type:

```
sudo apt-get -f install
```

to see if the system will continue with the upgrade?

---

### Post by bobdotexe on 2009-11-04
can't get that far all that works is GRUB; 

I get the error while the OS is still loading...

---

