---
title: "xorg.conf / XServer  issues at Fujitsu Stylistic"
date: 2008-04-25
forum: Hardware
---

### Post by nise8181 on 2008-04-25
Yesterday I have updated from xubuntu 7.10 to 8.04 and I was hoping to fix some problems but oviously I am in trouble with my hardware or configuration. After one night and half a day I really don't know what I could do more.

First problem: After start or reboot of the machine or restart of Xserver (Alt+Control+BackSpace) there is nothing to see then the desktop with a few icons but no menu at the top.
  What log files acn indicate that particular gdm problem?
  Since I had problems with my network as well I found out that the menu appears when I stop /etc/init.d/gdm and restart /etc/init.d/networking afterwards. Sadly the system freezes totaly.

Second problem: (it seems to be related with the first one) is my Touchscreen and the necessary configurations of my xorg.conf file.
I followed [http://www.neurath.org/stylistic_lt_c500/](http://www.neurath.org/stylistic_lt_c500/) but right after pressing the screen a few times xserver reboots. I don't see a pointer.

xorg.conf:
```
Section "InputDevice"
  Identifier "Touchscreen"
  Driver "fpit"
  Option "Device" "/dev/ttyS1"
  Option "Baudrate" "9600"
  Option "MaximumXPosition" "4096"
  Option "MaximumYPosition" "4096"
  Option "MinimumXPosition" "0"
  Option "MinimumYPosition" "0"
EndSection

``` 

and in the section server flags I've added:
```
 InputDevice "Touchscreen" "SendCoreEvents"
```

finaly I've put two lines to /etc/rc.local in order to reconfigure the touchscreen interface:
```
/bin/setserial /dev/ttyS1 autoconfig
/bin/setserial /dev/ttyS1 uart 16450 irq 5 port 0xfd68
```


Any suggestions are welcome. Thanx in advance.

---

