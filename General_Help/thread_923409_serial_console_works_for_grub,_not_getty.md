---
title: "serial console works for grub, not getty"
date: 2008-09-18
forum: General Help
---

### Post by mechsoph on 2008-09-18
I am trying to enable the serial console for this ubuntu machine.  I followed the instructions on the [Ubuntu SerialConsoleHowto]("http://https://help.ubuntu.com/community/SerialConsoleHowto").  

Currently, grub works fine and I can choose which kernel to boot over the serial line.  The kernel starts to boot fine and prints messages on both tty0 and ttyS0; however, when it gets to the point where it begins to start services (apache, ssh, etc.) it stops printing output on ttyS0 and getty does not seem to run on ttyS0.  I see nothing more on ttyS0 until I reboot the system (via ssh) at which point it prints "Restarting System."

I'm not sure what else I need to do to make getty work properly on ttyS0.

The relevant section of my menu.lst file is
```

serial --unit=0 --speed=115200 --word=8 --parity=no --stop=1
terminal --timeout=15 serial console

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro console=ttyS0,115200n8 console=tty0
initrd          /boot/initrd.img-2.6.24-16-generic

```

My /etc/event.d/ttyS0 file is
```

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty  115200 ttyS0

```

setserial -g shows:
```

root@sparky:~# setserial -g /dev/ttyS*   
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: 16550A, Port: 0x03e8, IRQ: 10
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 5

```


Also, ttyS0 is in /etc/securetty.

---

### Post by liggyman on 2009-05-18
Were you ever able to find a resolution to this problem?

Thanks.

---

