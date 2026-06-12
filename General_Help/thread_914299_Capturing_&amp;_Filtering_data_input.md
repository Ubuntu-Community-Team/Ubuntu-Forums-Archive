---
title: "Capturing &amp; Filtering data input"
date: 2008-09-08
forum: General Help
---

### Post by Friqenstein on 2008-09-08
Hey all,

Was looking for a simple way to run **cat** on a USB device that has data streaming in, and the pipe it **|** to a simple command line to remove the **\n** (or carriage returns).
Is there a simple way to do this via command line?

---

### Post by unutbu on 2008-09-08
Perhaps try```

lsusb
awk '$1' RS="" ORS="  " /dev/usb1
```

The lsusb command will show you your usb devices.
Note the device number. Change the 1 in /dev/usb1 to the correct device number you find from the lsusb command.

---

### Post by Friqenstein on 2008-09-08
Thanks for the reply.

Well, what I was doing before was:```
cat /dev/ttyUSB0
```And that would basically show the incoming data on that USB device. It scrolls through the terminal window, but it has a space between each line. I was just trying to get it to remove the spaces between the lines (the carriage returns) so that the incoming data would be formatted a bit better.

I tried your **awk** suggestion, but nothing happened.```
cat /dev/ttyUSB0 | awk '$1' RS="" ORS="  " /dev/ttyUSB0
```There wasn't anything happening in the terminal after that, so I **^C** to kill it and tried a few variations of those two commands. Can't seem to get it to actually scroll the data using the **awk** script.

---

### Post by unutbu on 2008-09-09
awk reads the last argument /dev/ttyUSB0 as a file so there is no need to pipe in cat as well. So the command to try would have been
```

awk '$1' RS="" ORS="  " /dev/ttyUSB0
```

However, given that you saw no data from your other command there is probably some funniness going on with reading /dev/ttyUSB0 which is unlike reading from a regular file.

Perhaps try this instead:
Save this in a file named stream.py
```

#!/usr/bin/env python
import sys
fh=open(sys.argv[1],'r')
print "".join(line.strip() for line in fh)
fh.close()
```

Make it executable:```

chmod 755 stream.py
```

Run it like this:```

./stream.py /dev/ttyUSB0
```

---

