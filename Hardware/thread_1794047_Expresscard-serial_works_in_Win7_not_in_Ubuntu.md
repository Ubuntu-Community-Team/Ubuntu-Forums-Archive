---
title: "Expresscard-serial works in Win7 not in Ubuntu"
date: 2011-06-30
forum: Hardware
---

### Post by Yepi on 2011-06-30
Hi, I have bought a Startech 1 port native expresscard-serial adapter, it works fine in win7 installed drivers no issues and got it to work with my plotter. 

I thought that as virtually al laptops come with an expresscard/pcm... something slot that it should be plug and play, unfortunately Startech do not have linux drivers.

when I type   setserial -g /dev/ttyS[0123] I get 

```

/dev/ttyS0, UART: unknown, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

```

I also went to the add printer wizard and the first time a serial port showed up /dev/ttyS4 ( I thought it only goes to 3) so I selected the serial port option and installed but it did not work.

I also got a LSR safety check error when I use dmesg | grep tty 

```
ubuntu@ubuntu-AH530:~$ dmesg | grep tty 
[    0.000000] console [tty0] enabled
[    1.119217] tty tty21: hash matches
[   25.097765] ttyS4: LSR safety check engaged!
[   25.098838] ttyS4: LSR safety check engaged!
[  189.850744] ttyS4: LSR safety check engaged!
[  218.507622] ttyS4: LSR safety check engaged!
[  677.298475] ttyS4: LSR safety check engaged!
[  693.325455] ttyS4: LSR safety check engaged!
[  712.327517] ttyS4: LSR safety check engaged!
[  720.103525] ttyS4: LSR safety check engaged!
```

Also I tried cutecom and gtkterm to, with gtkterm I get an endless repeat of input/output error in terminal and with cutecom when I open device I get 
[/CODE]
tcgetattr() 2 failed
tcgetattr() 3 failed
tcsetattr() 1 failed
tcgetattr() 4 failed
tcsetattr() 2 failed[/CODE]

Any help would be great,
Thanks in advance

---

