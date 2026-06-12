---
title: "MSP430 on Linux"
date: 2010-02-18
forum: Hardware
---

### Post by kbaumen on 2010-02-18
Hi.

As weird as it may sound, I won in a lottery (seriously) an MSP430 microcontroller with a USB development tool eZ430-RF2500 from Texas Instruments. I've already used it a bit. At uni, we have a project in labs where we have to use this thing. We wrote a few simple C programs to make the LEDs flash etc. 

Now the lab computers have windoze on them. I'm curious if it's possible to connect this thing to Linux somehow. As in actually writing a C program for it. The official manual doesn't say anything about Linux support. Any help will be appreciated.

---

### Post by kbaumen on 2010-02-19
bump

---

### Post by cicciopapero on 2010-04-28
The latest thing I could find that allows you to use the USB-stick version
of the MSP430 development system is the following:

  robust.cs.utep.edu/arch1/msp430/doc/msp430.pdf

I don't know if the latest version of the USB stick uses the same
USB protocol as the earlier. But the above paper is certainly an excellent
starting point. Let me know what you can do with it.

Best,
                                 Tommaso Toffoli [email]tt@bu.edu[/email]

---

### Post by heyandy889 on 2011-02-10
Hi, everyone. :-D Just wanted to get in on this thread. That pdf looks very promising, looks like there is even gdb support (read: makes debugging a dream) for the msp430. I have the ez430-f2013 debugging utility; it is an msp430 chip on the end of a usb stick. Using Code Composer Studio in Windows allows you to step through microcontroller programs; sweet! Being a computer science major and an advocate of Ubuntu, I would love to get this microcontroller running with an open-source operating system. I have a semester project dealing w operating systems this semester, so maybe I can use the msp430 with my project (specs are pretty loose. we can do anything with hardware or systems programming)

---

### Post by snakerdlk on 2011-06-12
If find your lack of google disturbing...

[http://mylightswitch.com/2010/06/21/installing-mpsgcc4-and-mspdebug-on-kubuntu-1004/](http://mylightswitch.com/2010/06/21/installing-mpsgcc4-and-mspdebug-on-kubuntu-1004/)

---

### Post by kbaumen on 2011-08-30
> **cicciopapero said:**
> The latest thing I could find that allows you to use the USB-stick version
of the MSP430 development system is the following:
 
robust.cs.utep.edu/arch1/msp430/doc/msp430.pdf
 
I don't know if the latest version of the USB stick uses the same
USB protocol as the earlier. But the above paper is certainly an excellent
starting point. Let me know what you can do with it.
 
Best,
Tommaso Toffoli [EMAIL="tt@bu.edu"]tt@bu.edu[/EMAIL]
 
Woah, I had not looked at this thread in a while, so missed the late reply. And I had not really done anything with the MSP430 over the last year (uni, work and other nonsense got in the way). But that pdf does look very interesting. Am currently at work, but will give it a shot over the next few days.
 
Thanks a lot mate.

---

### Post by kbaumen on 2011-08-30
> **snakerdlk said:**
> If find your lack of google disturbing...
 
[http://mylightswitch.com/2010/06/21/installing-mpsgcc4-and-mspdebug-on-kubuntu-1004/](http://mylightswitch.com/2010/06/21/installing-mpsgcc4-and-mspdebug-on-kubuntu-1004/)
 
This (according to comments on the website) is for 32-bit systems but I am on 64. Anyway worth a shot, so thanks.
 
Btw, I do use google, but this tutorial was posted a few months after I started this thread.

---

### Post by kbaumen on 2011-10-06
Very old thread, but I thought I should mention it anyway that I solved the problem. I can now use my MSP430 with Ubuntu 10.04. I did a lot of stuff, but what I am eventually using is msp430-gcc to create the binaries and mspdebug to flush the binaries down to the controller.

When running mspdebug, the usual command that I saw in a few tutorials was
```
mspdebug uif -d /dev/ttyUSB0
```

Well, that didn't work for me. I instead of ttyUSB0 I have ttyACM0 which still didn't solve the problem. Eventually I did manage to get mspdebug to run with my rf2500 by using the command
```
sudo mspdebug rf2500
```
Note the sudo, it doesn't work without it.

After that, write your code according to the datasheet, compile it with msp430-gcc, and flush it to the controller by using the appropriate commands in mspdebug (its help command is very helpful in understanding how to use mspdebug).

---

### Post by heyandy889 on 2011-10-07
Cool. Way to go, dude!

---

### Post by stefaneb on 2011-11-17
TI has released Code Composer Studio 5.1 with support for Linux.  I am about to try and install it with hopes of getting my MSP430 kits to communicate with my Linux machines.  I will try to post an update soon.

Update:  I am apparently a total loser.  I installed CCS, but then had to get back to work, which didn't include any 430 stuff :(

---

