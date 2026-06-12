---
title: "What's this mean?"
date: 2010-02-01
forum: Hardware
---

### Post by Moozillaaa on 2010-02-01
What's the command mean that's in this post?
[http://ubuntuforums.org/showpost.php?p=2350483&postcount=6](http://ubuntuforums.org/showpost.php?p=2350483&postcount=6)

My scanner is detected, but I get:
failed to start scanner: error during device I/O

The above command worked for someone else... what's it mean?

I have my scanner (and mouse antennae, and printer) plugged into a 4x USB outlet, that's in turn plugged into the laptop USB port.......

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=145580&d=1265005746

---

### Post by IcarusR on 2010-02-01
```
sudo chmod a+rw /proc/bus/usb/*/*
```

Just like the next post says 

> make sure that permission to use your scanner is given to the scanner group

It gives all users read write permissions on everything below /proc/bus/usb/

See manual page for chmod.

```
man chmad
```

Most commands have a man page accessed as above

---

