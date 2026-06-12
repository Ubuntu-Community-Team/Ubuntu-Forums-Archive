---
title: "Startup and wireless problem on Lenovo t61"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by gbgard on 2007-07-06
I have Lenovo T61 laptop with Feisty 64bit installed and mostly working.  There are a couple of strange problems (maybe related) I would like some advice on.  After some effort I managed to get the wireless networking working with NDIS (gave up on the Intel linux driver...)  However, it doesn't come up on every boot, and I can't get it to start if it doesn't start on boot.  There are also a couple of problems with bootup.  First, I have added piix to /etc/initramfs-tools/modules and run update-initramfs.  This in fact generates a new ramdisk file as indicated by the time stamps in /boot.  However I still get the "can't access tty; job control turned off" error.  I type modprobe piix and exit and the bootup continues for a while and then hangs.  Here's the strange part:  if I type ctrl-alt-del the boot process continues and fairly soon gets to the logon screen and the desktop then loads ok.  So something is stopping the boot process, but ctrl-alt-del allows the boot to complete.  I removed 'guiet' from the grub menu.lst file in an attempt to see where it stops.  But while this worked until the piix halt, after I type exit the screen just goes black until I get to the logon screen.

I'm sorry this post is a little long, but it's a strange problem or problem and I want to explain it as well as possible.

Any suggestions will be greatly appreciated.

Bernie

---

### Post by gbgard on 2007-07-06
A little more information:

1) I Don't think the piix startup problem is related to the ndis problem
2) I find that if I remove ndiswrapper (make uninstall), I still get the 'can't access tty..' erro
    but after the modprobe/exit the system boots normally;
3) If I then reinstall ndiswrapper and the appropriate drive, the next time I boot the system
    hangs as before, but now the wireless card works.  The wireless light comes on before
    the hang, I hit ctrl-alt-del, the system boots and I have wireless.
4) The next time I reboot, the wireless does not work.

I'm not sure what to do next!

Bernie

---

