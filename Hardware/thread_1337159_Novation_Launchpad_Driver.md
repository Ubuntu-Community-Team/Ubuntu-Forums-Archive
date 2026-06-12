---
title: "Novation Launchpad Driver"
date: 2009-11-25
forum: Hardware
---

### Post by mrtof on 2009-11-25
Hi,

I bought the Novation Launchpad ( [http://www.novationmusic.com/products/midi_controller/launchpad](http://www.novationmusic.com/products/midi_controller/launchpad) ) thinking the device would be a typical usb midi device. But it turns out they decided to require the use of custom drivers (for no real apparent reason as the device acts as a standard MIDI device in XP or OS X).

I sent an email to Novation as follows:

> Do you expect to support Linux(Ubuntu) with the Launchpad? Or is there a way the Launchpad can be used in Linux as a standard usb MIDI device?

This is their answer:

> At the moment there is no MIDI driver for Launchpad, so it will not work on Linux. However, we will happily help anyone who wants to write their own driver and there is a possibility that we may release our own driver for Linux although I can not confirm this at present.

So. *This seems like an open invitation*!
Any Linux Driver Writer up to task of writing a Linux Driver for the Novation Launchpad? :P The device is currently being recognized by Ubuntu as a Open Host Controller Interface.

---

### Post by clam2000 on 2009-12-26
So in an evening of reading through the USB device drivers I was able to modify a skeleton driver into one that talks to my launchpad.

It works enough to register key presses and releases, and with a bit of luck I'll be able to figure out the format for sending messages to it as well.

Did you send your email to anyone in particular at Novation? I'm planning on pinging them soon to see if I can get a data sheet about the communication protocol, and whoever you reached seemed to be the right person.

Once I've got the hardware side figured out I'll look into the procedure for making this a midi driver, but that will also be a learning experience :)

---

### Post by mrtof on 2009-12-26
This is all I have from  : [email]launchpad@novationmusic.com[/email]

> Hi Thomas,

Thanks for your mail,

At the moment there is no MIDI driver for Launchpad, so it will not work on Linux. However, we will happily help anyone who wants to write their own driver and there is a possibility that we may release our own driver for Linux although I can not confirm this at present.

Hope this helps!

Best regards,

Neil Marron
Focusrite/Novation Tech Support

[www.focusrite.com](www.focusrite.com)

---

### Post by clam2000 on 2009-12-26
Cool.  I fired off another email to them, and I'll take a look at seeing what I can do on the input side today as well.

> 
Dear Novation,

I am looking into setting up a linux driver for the Novation
Launchpad.  I found online that when previously asked about this, you
guys offered to answer questions if someone wanted to take initiative.
[1]  I am already able to receive button presses and releases without
problem, but before I spend a bunch of time I was wondering if you can
help with the format that is used for setting LED colors on the
device.

Thanks,
--Will

[1] [http://ubuntuforums.org/showthread.php?t=1337159](http://ubuntuforums.org/showthread.php?t=1337159)


---

### Post by clam2000 on 2009-12-26
I dug around a bit more, and it turns out that Novation has released a programming reference for the launchpad.

[http://nezoomie.wordpress.com/2009/10/28/novation-released-launchpad-programming-guide-and-protocol/](http://nezoomie.wordpress.com/2009/10/28/novation-released-launchpad-programming-guide-and-protocol/)

I still haven't been able to turn on it's lights, but now I know what I should be sending it.

---

### Post by clam2000 on 2009-12-26
Okay, so I have what I believe to be a working kernel module for the launchpad.  

I've attached a zip file with the c file, and a makefile.  extract it to a directory and type make to build the kernel module, then as root you would run 
```

insmod launchpad.ko

```

Then, when you plug in the launchpad it will show up as a file at /dev/launchpad0.

The following perl script will turn on all of it's lights:
```

my $code = chr(0xb0).chr(0x00).chr(0x7F);
open FILE, ">/dev/launchpad0" or die $!;
print FILE $code;
close FILE;

```

The next step is probably to write a daemon that acts as an alsa midi endpoint and translates between the alsa midi messages and the launchpad syntax.  I'll try to take a crack at that next.

---

