---
title: "help! upgrade to 9.10 killed Grub, can't boot"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by MalphasWats on 2009-10-30
Hi,

  I've just completed the (very slow) upgrade to 9.10, now when I reboot, I get the error:

```
error: unknown command 'initrd'
```

I tried the solution at
[https://wiki.ubuntu.com/Grub2#line-473]("https://wiki.ubuntu.com/Grub2#line-473")

but when I do that, I get the error:

```
error: You need to load the kernel first
```

The full content of the command in the grub menu is:

```

recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,6)
search --no-floppy -fs-uuid --set 8d6....longuuid...\

linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8d6...sameuuid...\
...restofit... ro    quiet splash
initrd /boot/initrd.img-2.6.31.14.generic

```

When I was installing the update, it asked me about GRUB-PC because I'd already installed it in 9.04 so I told it to leave the existing installation alone because it took me ages to get it working, after that, I just clicked >next for any options that came up, none of the things that came up were any help at all anyway, I didn't understand them - they had no explanations.

I think it was the last one that broke it, as it asked something like which device do you want to install to and I just clicked next without choosing (there was only 1 option anyway).

It's annoying that it clearly just went ahead and installed over the top even though it asked me if I wanted to keep the old one. I had it working fine before :(

Hope someone can get me up and running again, I don't know where to start with this.

Thanks
-Malphas

---

### Post by MalphasWats on 2009-10-30
I've managed to fix this now, after searching around and trying a few things.

When GRUB loads, I hit 'e' on the top option, then edited the command to look like this:

```
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=8d6...sameuuid...\
...restofit... ro    quiet splash
initrd /boot/initrd.img-2.6.31.14.generic
```

then hit ctrl+c to get a grub command line, typed:
```
insmod linux
```

hit escape and then ctrl+x to boot. That got me back into the system and I could then do a:
```
sudo grub-install /dev/sda
```

The biggest problem I hit after that was how to reboot!! The new UNR launcher thingy doesn't have a button for it anymore! Eventually I hit ctrl-alt-del and that brought up a menu with the reboot option etc on it. Rebooted and it worked.

-Malphas

---

