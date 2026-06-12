---
title: "Inkcut/Inkscape does not pick up my (chinese) plotter"
date: 2017-04-18
forum: Hardware
---

### Post by 70+pixelsaint+70 on 2017-04-18
Hi guys. Couple of days new to Linux. I use my pc for graphic design and signage. Been tinkering with it for some days. Keep running into issues to cut vinyl from inkcut/inkscape. Not sure what the settings should be. 

```
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 283, in on_send_clicked
    dev.plot(os.path.join(appPath,'tmp','plot.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
TypeError: on_defaults_clicked() takes exactly 1 argument (2 given)
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
Traceback (most recent call last):
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/main.py", line 283, in on_send_clicked
    dev.plot(os.path.join(appPath,'tmp','plot.hpgl'))
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/pixelsaint/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
```

Would really appreciate all and any help. 

Oh PS Im running Ubuntu Studio 16.04 - Latest Inkscape and Inkcut -

---

### Post by ian-weisser on 2017-04-18
> **70+pixelsaint+70 said:**
> app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS27: [Errno 13] Permission denied: '/dev/ttyS27'
TypeError: on_defaults_clicked() takes exactly 1 argument (2 given)

Since you're treating the vinyl cutter like a printer, let's call it a printer.

Precisely what is the printer manufacturer and model?
How, exactly, did you install the printer on your Ubuntu system?
Was the installation successful?
Can you print from other graphics programs onto the same printer?

---

### Post by 70+pixelsaint+70 on 2017-04-19
Thank you for the response Ian, I have a FLYCUT CSFY-720 printer. Tried looking for a driver as i dont find my printer on inkscape/Inkcut support groups. Not sure if it is installed as i only have a win driver for it. I used to cut from Corel and Artcut. I tried to run Artcut from WINE but it doesnt run. No idea how to install my plotter/printer other than with the win driver. I have tried finding other design programs that will also cut, but found only inkcut and robocut links.

---

### Post by pdc on 2017-04-19
Tuxplot [http://securetech-ns.ca/tuxplot.html](http://securetech-ns.ca/tuxplot.html) came up in discussions on another forum [https://forums.linuxmint.com/viewtopic.php?f=51&t=240180&p=1282102&hilit=vinyl+cutter#p1282102](https://forums.linuxmint.com/viewtopic.php?f=51&t=240180&p=1282102&hilit=vinyl+cutter#p1282102) and works well with linux; I think what might be really helpful is one can interact with someone who understands your work well, and may well be able to offer support; he needs to put food on the table, but then, many do

---

### Post by 70+pixelsaint+70 on 2017-04-19
Much thanks PDC!!! Will look into it.:D

---

