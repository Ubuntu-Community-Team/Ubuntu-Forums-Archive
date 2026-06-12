---
title: "PySerial AttributeError: 'module' object has no attribute 'Serial'"
date: 2008-10-14
forum: Hardware
---

### Post by the_person0 on 2008-10-14
I am trying to use PySerial to talk to a USB to serial adapter, a radio shack brand with a vendor=05ad and model=0fba.  The serial adapter works fine with minicom (opening /dev/ttyUSB0) and when I enter the following two lines into a python prompt, however when I put these two lines into a python script it will fail.

```

import serial
ser = serial.Serial('/dev/ttyUSB0', 38400)

```

The error created is

```

shawn@Loki:~/python$ python serial.py
Traceback (most recent call last):
  File "serial.py", line 1, in <module>
    import serial
  File "/home/shawn/mines/seniorDesign/BD950/serial.py", line 2, in <module>
    ser = serial.Serial('/dev/ttyUSB0', 38400)
AttributeError: 'module' object has no attribute 'Serial'
shawn@Loki:~/python$

```

Thank you for your help.

---

### Post by the_person0 on 2008-10-14
Turns out that it was importing serial.py that i had written rather than the module, changing the name of the script cleared up this problem.

---

### Post by lgvienna on 2008-10-15
> **the_person0 said:**
> Turns out that it was importing serial.py that i had written rather than the module, changing the name of the script cleared up this problem.

thank you very much for sharing this. i did the same thing and could not find the mistake until i found your post.

---

### Post by Bln on 2011-01-24
> **the_person0 said:**
> Turns out that it was importing serial.py that i had written rather than the module, changing the name of the script cleared up this problem.

Thank you very much mate. You saved my day!!!
You can easily waste hours trying to get rid of bugs like this one.

---

