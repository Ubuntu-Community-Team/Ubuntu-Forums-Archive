---
title: "USB keypad &quot;driver&quot; - error while loading shared libraries: libusb-0.1.so.4"
date: 2014-05-18
forum: Hardware
---

### Post by themainliner2 on 2014-05-18
I have an [Ergodex DX1]("http://www.ergodex.com/mainpage.htm") keypad. I've been using it happily for many year with the open source driver from [HydraProductions]("http://ergodex.hydraproductions.com/wiki/downloads"). This driver is really simple: you start it up with .csv file: "/path to/ergo /path to/%key defs%.csv"  which it uses to program all the keys. Having looked at the makefile
```
build: ergo

ergo: ergo.c ergo.h
    ${CC} -o ergo -lusb ergo.c

clean:
    rm -f ergo
```
 (no really) - the thing looks beyond simple (but not being a programmer what do I know).

In fact the truth is I compiled the driver forever ago and have simply copied it to ever distro I've used since. It's current working a treat on the Debian Testing based antiX Core M13.1 and I hoped there would be no issues using in Ubuntu (where I probably compiled it originally).

Obviously I wasn't lucky (or I wouldn't be posting this :D ). My first thought was "Just recompile on Ubuntu 14:04 64-bit - problem solved."

Here is the output from trying to make the binary:
```
themainliner2@ubuntu:~/Desktop/Ergodex$ make
cc -o ergo -lusb ergo.c
/tmp/ccyBDFlO.o: In function `write_req':
ergo.c:(.text+0x3ab): undefined reference to `usb_interrupt_write'
/tmp/ccyBDFlO.o: In function `read_resp':
ergo.c:(.text+0x436): undefined reference to `usb_interrupt_read'
/tmp/ccyBDFlO.o: In function `pad_open':
ergo.c:(.text+0x4ad): undefined reference to `usb_open'
ergo.c:(.text+0x4e4): undefined reference to `usb_claim_interface'
ergo.c:(.text+0x512): undefined reference to `usb_close'
/tmp/ccyBDFlO.o: In function `pad_close':
ergo.c:(.text+0x53c): undefined reference to `usb_release_interface'
ergo.c:(.text+0x56a): undefined reference to `usb_close'
/tmp/ccyBDFlO.o: In function `pad_query_device':
ergo.c:(.text+0x732): undefined reference to `usb_device'
/tmp/ccyBDFlO.o: In function `cmd_reset':
ergo.c:(.text+0x9cd): undefined reference to `usb_open'
ergo.c:(.text+0x9e4): undefined reference to `usb_reset'
/tmp/ccyBDFlO.o: In function `main':
ergo.c:(.text+0x10c4): undefined reference to `usb_init'
ergo.c:(.text+0x10c9): undefined reference to `usb_find_busses'
ergo.c:(.text+0x10ce): undefined reference to `usb_find_devices'
ergo.c:(.text+0x10d3): undefined reference to `usb_get_busses'
collect2: error: ld returned 1 exit status
make: *** [ergo] Error 1
```

I tried to run the pre-compiled binary (from a network drive) this is the result (illuminating?):
```
themainliner2@ubuntu:~/Desktop/Ergodex$ 
'/mnt/server/New Linux Build/.ergo/ergo' /mnt/server/New Linux Build/.ergo/ergo: error while loading shared libraries: libusb-0.1.so.4: cannot open shared object file: No such file or directory
```

Naturally I tried: sudo apt-get install libusb and tabbed a couple of times ;):
libusb-0.1-4           libusbip-dev           libusbprog0
libusb++-0.1-4c2       libusb-java            libusbprog-dev
libusb-1.0-0           libusb-java-dbg        libusbredirhost1
libusb-1.0-0-dbg       libusb-java-doc        libusbredirhost-dev
libusb-1.0-0-dev       libusb-java-lib        libusbredirparser1
libusb-1.0-doc         libusbmuxd2            libusbredirparser-dev
libusb-dev             libusbmuxd2-dbg        libusbtc08-1
libusb++-dev           libusbmuxd-dev         libusbtc08-dev
libusbhid-common       libusb-ocaml           
libusbip0              libusb-ocaml-dev

So I tried installing libusb-0.1-4 and libusb-dev. Then I tried libusb++-dev and libusb++-0.1-4c2. Then all -dev packages for a laugh. :rolleyes:

No joy. Clues, suggestions, advice? All welcome!

---

### Post by themainliner2 on 2014-05-24
My research leads me to suspect that a change made with the release of 13.04 Raring Ringtail his stopped the driver compiling / the pre-compiled binary working.

---

### Post by themainliner2 on 2014-07-07
After weeks of retrying, Internet searches and investigation I have concluded that this is probably a failure with multiarch support, which appears to be particularly problematic in Debian-based distros. The Ergodex 'driver' is a 32bit app, so I suspect the issue of not locating **usb.h** may be one of "simple" symbolic linking. Can *anyone* suggest how I might symlink to **usb.h** in the correct location, and of course *what that location might be* for a 32bit app?

Thanks for looking over this update.

---

### Post by steeldriver on 2014-07-07
The 'make' errors that you posted are from the link phase, not the compile phase (so likely nothing to do with header files) - most probably, you need to correct the link order (i.e. put the usb lib AFTER the .c file that depends on it) in your makefile 

```

build: ergo

ergo: ergo.c ergo.h
    ${CC} -o ergo [COLOR=#0000ff]**ergo.c -lusb**[/COLOR]

clean:
    rm -f ergo

```

---

### Post by themainliner2 on 2014-07-07
THANK YOU SO MUCH!

Honestly, this reflects a upstream change in Debian, so I was worried about how I would use the Ergodex, in Linux, going forward. You just made all those problems go away. Honestly I wish I could "buy you a beer" or "flattr" you that is so valuable to me. If we're ever in the same bar... :p

---

### Post by steeldriver on 2014-07-07
Happy to help - sorry I didn't spot your thread earlier, I'm on here most days

Cheers

---

