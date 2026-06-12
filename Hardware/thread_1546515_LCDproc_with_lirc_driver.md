---
title: "LCDproc with lirc driver"
date: 2010-08-05
forum: Hardware
---

### Post by cajda on 2010-08-05
Hello,
I installed lcdproc with lirc driver and I spent hours but I cannot get it work. Work it ever to somebody?
Lirc and irexec works fine, but not with lcdproc.
I just want to control lcdproc menu (and switching screens) with lirc ...

LCDd.conf
```

Driver=hd44780
Driver=lirc

...

[lirc]
lircrc=/etc/lirc/lircrc
prog=lcdd

```
/etc/lirc/lircrc
```

begin
        prog    = lcdd
        buttuon = KEY_BACK
        config  = Escape
end

...

```
Can anyone help me with this?
Thank you
PS: Please, excuse my English

**EDIT:**
I add a lcdproc report:
```

spetr@subuntu:~$ sudo LCDd -c /etc/lcdproc/LCDd.conf -r 5 |grep lirc
[sudo] password for spetr: 
LCDd version 0.5.3 starting
Built on Aug  4 2010, protocol version 0.3, API version 0.5
Using Configuration File: /etc/lcdproc/LCDd.conf
Set report level to 5, output to stderr
Server forking to background
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="hd44780", filename="/usr/local/lib/lcdproc/hd44780.so")
HD44780: using ConnectionType: lcd2usb
hd44780: Using hd44780_default charmap
hd_init_lcd2usb: device with firmware version 1.08 found
driver_load(name="lirc", filename="/usr/local/lib/lcdproc/lirc.so")
**lirc**: Using lircrc: /etc/lirc/lircrc
**lirc**: Using prog: lcdd
**lirc**: init() done
Key "Escape" is now reserved exclusively by client [-1]
Key "Enter" is now reserved shared by client [-1]
Key "Up" is now reserved shared by client [-1]
Key "Down" is now reserved shared by client [-1]
screenlist_process()

```

---

### Post by cajda on 2010-08-07
Do have someone any idea how to solve this probles? Is there any hope ..? I don't know what can I do ..

---

