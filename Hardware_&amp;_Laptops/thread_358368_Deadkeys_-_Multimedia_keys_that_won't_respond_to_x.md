---
title: "Deadkeys - Multimedia keys that won't respond to xev or the kernel"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by h6w on 2007-02-10
Hello people,

I finally got myself a shiny new Fujitsu P1510 laptop convertible tablet PC.  I've already got the tablet working, the only thing left are 5 keys that sit underneath the screen.   These keys are important because they are the only keys accessible when the laptop is converted to tablet mode (flip the screen so the keyboard is covered).

I have followed this tutorial:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

I have tried xev  but nothing is reported when I press the keys.

I have also looked at dmesg as it suggests, but the kernel doesn't report anything when the keys are pressed either.

What do I do now?  

Is it possible that the keys need to be "activated" or maybe that they use some special part of memory to report their status?

Alternatively, are there keyboard drivers?  Maybe I need to install a special module for my keyboard.  (Maybe called tablet_keys or some such)

Should I start talking to the kernel developers? It's strange that **nothing** is reported.  When nothing is reported I don't even know where to start. :-(

Cheers,
Tudor.

---

### Post by teaker1s on 2007-02-10
problem you have got is if the kernel doesn't respond then you can't map the key -annoying as it is- I've a keyboard and mouse with no output on some keys:(

---

### Post by h6w on 2007-02-11
Yes that's true.  I was surprised that there's **nothing**, not even a raw keycode.

However, that gives me an idea.  One of the keys is a Fn key, which I think is a hardware modifier.    e.g. Fn+F6 increases the brightness of the display.  It never sends a signal to the OS.  What if all these keys are hardware-controlled?  That could mean that we could have to poke somewhere to receive an event.  Or else listen in somewhere other than the normal place for keyboard events.

For example, mouse movements are treated this way.  What if the keys were somehow hooked into the tablet input controller?

I'll go have a look at the module I'm using to drive the tablet HID.

Cheers,
Tudor.

---

### Post by teaker1s on 2007-02-11
while I'm very much keen to find an answer, unless you get a different output from the function key and a dead key together, compared to just the function key. Then nothing will happen:(

---

### Post by RandomJoe on 2007-02-11
Can't help solve the problem, but Dell laptops have a similar issue.  All the "extra" keys (volume up/down, so forth) are accessible from Linux, but they have to use the "i8k" module since they are reported through Dell's custom BIOS.  The same module also handles the cooling fans.

The README has all the nifty details, found here:
[http://people.debian.org/~dz/i8k/00-README](http://people.debian.org/~dz/i8k/00-README)
I'm sure it won't work on a Fujitsu but perhaps it can give someone an idea what to look for...

---

