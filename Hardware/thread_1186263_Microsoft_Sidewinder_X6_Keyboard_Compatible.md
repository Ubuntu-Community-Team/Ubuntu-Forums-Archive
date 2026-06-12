---
title: "Microsoft Sidewinder X6 Keyboard Compatible?"
date: 2009-06-13
forum: Hardware
---

### Post by wanged on 2009-06-13
I should be getting a MS Sidewinder X6 Keyboard tomorrow, and I was wondering if it was compatible with Linux because there is no official support for it. Also if anyone has gotten theirs to work, and whether or not you were able to use all the special shiny function/macro keys.

 Thanks.

---

### Post by mikau on 2009-06-25
I got mine yesterday, and the keyboard itself does work, but I can't get the macro-keys to work at all. However most of the pre-programmed keys (calculator, sound control etc) works fine.

I might also add that I've got the Sidewinder X8 mouse, and it works wonders. Same thing there thou, I can't get the macro-key to work :)

---

### Post by Lexicus on 2009-08-18
Picked this keyboard up about a week ago and yes I was very happy to see the audio controls working.  Rhythmbox likes it.  

lsusb:
"Bus 001 Device 006: ID 045e:074b Microsoft Corp."

Are the macro key assignments software only or does it store them on the hardware like the Logitech G15s?

---

### Post by sackbj on 2009-08-26
I have a Logitech G11 at work and an X6 at home.  I am installing Ubuntu today and I am thinking about switching them out and having the X6 at work and the G11 at home.

After googling for a bit, it seems like getting the Logitech function keys to work isn't too big of a deal.

---

### Post by simplyw00x on 2011-05-07
Keyboard still on sale (May 2011) and still no support for any of the macro keys / macro recording. The name of the underlying software stack is "Intellitype" but some searching doesn't reveal any reverse engineering of its protocol.

Boo.

---

### Post by Wattos on 2011-11-05
For anyone still interested:

I created a user space linux driver for this keyboard so that you can use the keyboard with macros:

[https://github.com/Wattos/LinuxSidewinderX6](https://github.com/Wattos/LinuxSidewinderX6)

---

### Post by cmavr8 on 2011-12-05
IT WORKS!!!
Thanks so much!

---

### Post by RaphaelBaer on 2012-06-04
This is what I was missing such a long time now.. 

Unfortunately it doesn't compile. When I enter the make command I am getting

```
gcc  -O3 -g -Wall -Wwrite-strings  -Wno-unused-result sidewinder.o -lusb-1.0  -o sidewinder-x6-macro-keys 
/usr/bin/ld: i386 architecture of input file `sidewinder.o' is incompatible with i386:x86-64 output
collect2: ld gab 1 als Ende-Status zurück
make: *** [sidewinder-x6-macro-keys] Fehler 1

```

(running Ubuntu 12.04 64Bit)

It seems there is a problem with 32Bit/64Bit, but since on Wattos page he states its tested on 64Bit Systems, the problem should be something with the compiler. But with what little knowledge I have, I am lost from that point on. Any ideas what I could do?

Thanks to everyone in advance for help.

---

### Post by cmavr8 on 2012-06-05
> **RaphaelBaer said:**
> This is what I was missing such a long time now.. 

Unfortunately it doesn't compile. When I enter the make command I am getting

```
gcc  -O3 -g -Wall -Wwrite-strings  -Wno-unused-result sidewinder.o -lusb-1.0  -o sidewinder-x6-macro-keys 
/usr/bin/ld: i386 architecture of input file `sidewinder.o' is incompatible with i386:x86-64 output
collect2: ld gab 1 als Ende-Status zurück
make: *** [sidewinder-x6-macro-keys] Fehler 1

```

(running Ubuntu 12.04 64Bit)

It seems there is a problem with 32Bit/64Bit, but since on Wattos page he states its tested on 64Bit Systems, the problem should be something with the compiler. But with what little knowledge I have, I am lost from that point on. Any ideas what I could do?

Thanks to everyone in advance for help.

Hi Raphael, can you try:
$ make clean
$ make

and report back?
Thanks

---

### Post by RaphaelBaer on 2012-06-05
Thank you for the fast reply cmarv8. make clean gives:
```
rm -f *.o sidewinder-x6-macro-keys

``` doesn't look interesting..

and make:
```
gcc  -O3 -g -Wall -Wwrite-strings  -Wno-unused-result -c sidewinder.c  -o sidewinder.o
gcc  -O3 -g -Wall -Wwrite-strings  -Wno-unused-result sidewinder.o -lusb-1.0  -o sidewinder-x6-macro-keys 

```

---

### Post by cmavr8 on 2012-06-05
Ok, so it was successful!!
Run it with 
> $ sudo ./sidewinder-x6-macro-keys
;)

---

### Post by RaphaelBaer on 2012-06-06
Ah, yes, right!  Thank you very much cmavr8 for your help.  And thank you Wattos for this driver, I couldn't get my work done without these macro keys.

---

### Post by cmavr8 on 2012-06-06
Glad you got it working :)

I'm experiencing a bug, 99% CPU usage after a few hours of running sidewinder-x6-macro-keys.

[More info]("https://github.com/Wattos/LinuxSidewinderX6/issues/5")
If anyone else is affected please comment there.

Thanks

---

### Post by hurinth on 2012-06-14
cmavr8. Raphael, can any of you (or any other owner of this kb and ubuntu user) tell me if you are so kind, if the macro keys are recognized by the system as regular command keys? 

My point is, I don't really use macros, however programming each key with a command like for example:

gnome-volume-control -o hardware

to open the volume applet is very much what Im looking for.

All I would ask of this keyboard+ubuntu is to be able to program different functions like open  folders locations or run a script, and if the button to choose from the 3 macro lists works in differenciating the macro keys even more. So my questions are:

Do you get the ability to program each key for separate commands?
Do you get 18 different keystrokes from the macro keys?

Thanks in advance!

---

### Post by cmavr8 on 2012-07-01
> **hurinth said:**
> cmavr8. Raphael, can any of you (or any other owner of this kb and ubuntu user) tell me if you are so kind, if the macro keys are recognized by the system as regular command keys? 

My point is, I don't really use macros, however programming each key with a command like for example:

gnome-volume-control -o hardware

to open the volume applet is very much what Im looking for.

All I would ask of this keyboard+ubuntu is to be able to program different functions like open  folders locations or run a script, and if the button to choose from the 3 macro lists works in differenciating the macro keys even more. So my questions are:

Do you get the ability to program each key for separate commands?
Do you get 18 different keystrokes from the macro keys?

Thanks in advance!

Sorry it took me so long to answer..

I can't assign commands via the ubuntu "keyboard shortcuts" procedure, but I can assign scripts using the custom software.

It allows us to configure the S1-S12 buttons for profiles 1,2,3, so in theory you get 12*3 = 36 button assignments!

I'm only using S1, S2, S3 and S12 at the moment... All of my scripts are just like that:

> #!/bin/bash
google-chrome

---

