---
title: "USB Missile Launcher + ubuntu feisty 7.04"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by samsunix on 2007-08-05
Hi!

I bought these... well... toy
[img]http://www.thinkgeek.com/images/products/front/usb_rocket_launcher2.jpg[/img]
[http://www.thinkgeek.com/geektoys/warfare/8a0f/](http://www.thinkgeek.com/geektoys/warfare/8a0f/)

Idea is get it work as in windows with original drivers and software by a keyboard.
when it works I planned to change it to web use. (control by a web site where is control buttons and web cam image).

I wound one howto site:
[http://scott.weston.id.au/software/pymissile-20060126/](http://scott.weston.id.au/software/pymissile-20060126/) (with these should work also these model)

I tryed to install it like these:
```
- sudo apt-get install python gcc python-dev libusb-dev
- sudo apt-get install python-urwid #(0.9.8.1)
cd urwid-folder
- wget http://scott.weston.id.au/software/pymissile/missile.py
```

print:
```
samsunix@nuxlappis:~/urwid-0.9.8.1$ ./missile.py
Traceback (most recent call last):
  File "./missile.py", line 82, in <module>
    import usb
ImportError: No module named usb
samsunix@nuxlappis:~/urwid-0.9.8.1$ 

```

it seems that OS doesn't regonice it ???

also installed python-hid and python-usrp but it didn't work out. Any ideas anyone?

---

### Post by lolcats on 2007-08-05
I have these and they are alot of fun.

The thing you're missing is this:
```
 su -
(password)    #you cant sudo it.
apt-get install pyusb
apt-get install libusb
exit
```

thats about as simple as it gets. you didnt install pyusb so you cant use it :lolflag:

---

### Post by samsunix on 2007-08-05
> thnx for making me feel a noob again... however I keep failing:
```
samsunix@nuxlappis:~/libusb-0.1.12$ sudo ./configure
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```

config.log part I think it fails:
```
configure:2952: $? = 0
configure:2955: test -s conftest.o
configure:2958: $? = 0
configure:2976: result: none needed
configure:2994: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'm$
configure:3000: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me

```

why it isn't just "sudo apt-get install libusb"

Ok I make it out ... just reguired g++ installed 
```
sudo apt-get install g++
``` all should be fine now BUT:
```
samsunix@nuxlappis:/usr/share/python-support/python-urwid/urwid$ ./missile.py
No WMDs found.
samsunix@nuxlappis:/usr/share/python-support/python-urwid/urwid$ 

```

What's that now?

Found that WMD part in missile.py:
```
if opts:
    for o, a in opts:
      if o in ("-h", "--help"):
        usage()
      elif o in ("-v", "--version"):
        version()
      elif o in ("-n", "--network"):
        try:
          MissileNetwork().main()
        except NoMissilesError, e:
          print "No WMDs found."
          return
      else:
        try:
          MissileDisplay().main()
        except NoMissilesError, e:
          print "No WMDs found."
          return
  else:
    try:
      MissileDisplay().main()
    except NoMissilesError, e:
      print "No WMDs found."
      return
```

But I don't have idea what that means...

---

### Post by samsunix on 2007-08-06
it seems that Linux doesn't still regonice  my usb missile launcher.  device information: "Unknown (0x8021)" :confused:

I didn't get eny errors so I really am confused.

---

### Post by bonkey on 2007-09-24
any update on this? I have the same issue...No WMDs found.

---

### Post by bonkey on 2007-09-24
I found the vendor id and product id of the USB connection and updated the code.

self.dev=UsbDevice(0x1941, 0x8021, battery)

but no luck

$ sudo ./missile.py
Traceback (most recent call last):
  File "./missile.py", line 412, in <module>
    main(sys.argv[1:])
  File "./missile.py", line 406, in main
    MissileDisplay().main()
  File "./missile.py", line 201, in main
    self.ui.run_wrapper(self.run)
  File "/var/lib/python-support/python2.5/urwid/curses_display.py", line 179, in run_wrapper
    return fn()
  File "./missile.py", line 207, in run
    md.append(MissileDevice(missiles))
  File "./missile.py", line 120, in __init__
    self.dev.open()
  File "./missile.py", line 158, in open
    self.handle.detachKernelDriver(1)
usb.USBError: could not detach kernel driver from interface 1: Invalid argument

---

### Post by bonkey on 2007-09-24
update: commented out the line:

#self.handle.detachKernelDriver(1)

The app runs now.... BUT

Traceback (most recent call last):
  File "./missile.py", line 412, in <module>
    main(sys.argv[1:])
  File "./missile.py", line 406, in main
    MissileDisplay().main()
  File "./missile.py", line 201, in main
    self.ui.run_wrapper(self.run)
  File "/var/lib/python-support/python2.5/urwid/curses_display.py", line 179, in run_wrapper
    return fn()
  File "./missile.py", line 224, in run
    m.move(MissileDevice.UP)
  File "./missile.py", line 126, in move
    self.dev.handle.controlMsg(0x21, 0x09, self.INITA, 0x02, 0x01)
usb.USBError: error sending control message: No such file or directory


I think the issue is the codes used to move this model are a little different will update with the right codes if I get it to work.

---

### Post by unholy1 on 2007-12-31
hey bonkey,

I've just followed the exact same trail as you. I too would like to figure out what the correct codes are, but I've no idea how. Have you made any progress?

---

### Post by unholy1 on 2008-01-14
The latest version of [Andreas Henriksson’s ahmissile software]("http://www.fatal.se/fulhack/ahmissile/") (v0.5) works with the latest Dream Cheeky USB Rocket launcher (product ID: 0×0A81 vendor ID: 0×0701)! woohoo!

---

### Post by FlyingV on 2008-02-05
I'm having a bit of problem getting this device to work.

I've tried compiling the latest ahmissile code (v0.5), but I get this error message when running './configure':

```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.0.0 libusb) were not met:

No package 'gtk+-2.0' found
```

Any idea what I should do to fix this?

---

### Post by Rhubarb on 2008-02-05
Make sure you've got **libgtk2.0-dev libusb-dev** you can get these in the ubuntu repositories.

---

### Post by FlyingV on 2008-02-05
Never mind, figured it out.

I was missing the libgtk2.0-dev package.

---

### Post by FlyingV on 2008-02-05
I got it working, but the response of the device seems less accurate than when using the windows application.

Has anyone tried the other Linux applications and seen a better performance?

---

