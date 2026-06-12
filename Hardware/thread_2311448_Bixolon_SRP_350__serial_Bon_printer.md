---
title: "Bixolon SRP 350 : serial Bon printer"
date: 2016-01-27
forum: Hardware
---

### Post by franz4 on 2016-01-27
[COLOR=#000000][SIZE=1]Hi i installed the Bixolon srp350 like this instruction[/SIZE][FONT=arial black] [http://www.bixolon.com/upload/download/manual_linux%20cups%20driver%20install_en_v1.0.0.pdf](http://www.bixolon.com/upload/download/manual_linux%20cups%20driver%20install_en_v1.0.0.pdf) [/FONT][SIZE=1]then i go to CUPS and ad the Bixolon
[/SIZE][/COLOR][FONT=Liberation Mono][COLOR=#000000]but at Local Printer i can only ad serial no Bixolon then after two times continue i can ad the Bixolon 350 when i finished this and will make a test print it do nothing??[/COLOR][/FONT][FONT=Liberation Mono][COLOR=#000000]
i used a serial adapter 25 to 9
what do i wrong?

[/COLOR][/FONT][FONT=Liberation Mono][COLOR=#000000]```
ps -ef | grep tty
root      1069     1  0 17:51 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1071     1  0 17:51 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1077     1  0 17:51 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1084     1  0 17:51 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1095     1  0 17:51 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1475     1  0 17:51 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1526  1517  3 17:51 tty7     00:01:08 /usr/bin/X :0 -audit 0 -auth /var/lib/mdm/:0.Xauth -nolisten tcp vt7
pe1-pos   2819  2684  0 18:24 pts/1    00:00:00 grep --colour=auto tty
pe1-pos@pe1-pos ~ $ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    2.716934] 00:08: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
```[/COLOR][/FONT]

---

