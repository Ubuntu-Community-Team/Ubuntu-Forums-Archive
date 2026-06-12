---
title: "USB-&gt; Parallel port lead"
date: 2013-01-15
forum: Hardware
---

### Post by linuxonbute on 2013-01-15
I bought a usb to parallel lead which I would like to use to connect to an ADC circuit I want to build.
If this was a normal parallel port I know what the address of the data ,status and control ports would be.
As I will need to make the data pins input rather than output first I will need to write to the control port.
What I don't know is how I would do it with this lead.

I have collected this information:
-----------------------------------------------------------------------------------------------------------------------------------------------
On plugging the lead in I got from dmesg:

[125304.300134] usb 4-1: new full-speed USB device number 15 using ohci_hcd
[125304.505565] usblp0: USB Bidirectional printer dev 15 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584
-----------------------------------------------------------------------------------------------------------------------------------------------
I then did lsusb -v -d 0x1A86:0x7584 from which I got:

Bus 004 Device 015: ID 1a86:7584 QinHeng Electronics CH340S
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1a86 QinHeng Electronics
  idProduct          0x7584 CH340S
  bcdDevice            2.54
  iManufacturer           0 
  iProduct                2 USB2.0-Print 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               96mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

-----------------------------------------------------------------------------------------------------------------------------------------------
Then ls -alt /dev/u* gave:
crw------- 1 root root 252,   0 Jan 12 11:45 /dev/usbmon0
crw-r----- 1 root root  10, 223 Jan 12 11:45 /dev/uinput
crw-rw-rw- 1 root root   1,   9 Jan 12 11:45 /dev/urandom
.... etc

/dev/usb:
total 0
drwxr-xr-x 18 root root   4340 Jan 15 19:35 ..
crw-rw----  1 root lp   180, 0 Jan 15 19:26 lp0
drwxr-xr-x  2 root root     60 Jan 15 19:26 .
-----------------------------------------------------------------------------------------------------------------------------------------------
Could anyone advise me how I can do this please?
I will be writing the code in C++
Thanks

---

### Post by sanderj on 2013-01-15
So ... did you write and try any code? Or are you asking for code?

PS: Probably wise to run you executable as root.

---

### Post by linuxonbute on 2013-01-15
Well no, I have no idea where in the system this appears.
As I said if it was a standard port it would be at 0x3bc or 0x378 
but this doesn't seem to be.
If I plug it in and try some code it shows no errors but it is no different with it unplugged.

---

### Post by sanderj on 2013-01-15
My experience with writing to a parallel port is more than a decade old, but let's try it with python: higher level, so less thinking

```
sudo apt-get install python-parallel

```
then start python, and type:

```
import parallel
p = parallel.Parallel()     # open LPT1
p.setData(0x55)

```
does that work? Post the output here.

---

### Post by linuxonbute on 2013-01-15
I guess it didn't

sudo python
Python 2.7.3 (default, Aug  1 2012, 05:16:07) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import parallel
>>> p = parallel.Parallel()     # open LPT1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/parallel/parallelppdev.py", line 187, in __init__
    self._fd = os.open(self.device, os.O_RDWR)
OSError: [Errno 2] No such file or directory: '/dev/parport0'
>>> p.setData(0x55)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'p' is not defined
>>>

---

### Post by sanderj on 2013-01-15
Sorry, I have no further ideas.

---

### Post by linuxonbute on 2013-01-15
Had a look at python-parallel 
[http://pyserial.sourceforge.net/pyparallel.html](http://pyserial.sourceforge.net/pyparallel.html)
 found it said lp module shoud be unloaded
so did so and ran code again.
 sudo python
Python 2.7.3 (default, Aug  1 2012, 05:16:07) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import parallel
>>> p=parallel.Parallel
>>> p.SetData(0x55)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: class Parallel has no attribute 'SetData'
>>> 
So a different outcome but some progress.

---

### Post by linuxonbute on 2013-01-15
Had a look at what python-parallel provides and saw one was
setData  not SetData so tried again. My mistake!!

sudo python
Python 2.7.3 (default, Aug  1 2012, 05:16:07) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import parallel
>>> p=parallel.Parallel
>>> p.setData(0x55)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unbound method setData() must be called with Parallel instance as first argument (got int instance instead)
>>> 
So a different error again.
As I know nothing worthwhile about this i am still at a loss

---

