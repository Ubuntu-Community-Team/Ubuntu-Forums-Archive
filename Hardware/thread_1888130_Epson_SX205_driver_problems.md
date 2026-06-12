---
title: "Epson SX205 driver problems"
date: 2011-11-28
forum: Hardware
---

### Post by maxamos on 2011-11-28
Hello 

Since upgrading to 11.10 I've been having problems with printing colours, greyscale printing is fine but colours are being printed separately slightly unaligned. 

Any ideas very much appreciated.

Max

---

### Post by crazy bird on 2011-11-28
Did you try to align the printer itself? Since grayscale/black is okay but the color prints are misaligned.

---

### Post by maxamos on 2011-12-01
Yes have tried doing that and the printer prints fine using my Windows 7 laptop (which is annoying).

Have searched online and noticed one other person with same issue but he had posted in the launchpad forum and so got no help.

---

### Post by willivonh on 2012-01-16
Hello,

I had the same problem and I have just managed to solve it. I am using Ubuntu 11.10, and my printer is a multifunction epson stylus sx205.  After lots of attempts, I found this old solution to a similar problem:

[http://ubuntuforums.org/showthread.php?t=932547&highlight=epson+stylus+sx205]("http://ubuntuforums.org/showthread.php?t=932547&highlight=epson+stylus+sx205")

and after changing the driver model from "epson stylus sx205" to the "epson stylus dx4800" I can now print both in grayscale and color perfectly. 

I actually made this change using the CUPS web-interface, but I suppose that by simply changing on ->System Settings -> Printers -> Proprieties it should also work.   

This is my first time around, I hope this helps someone.

Willi

---

### Post by maxamos on 2012-02-27
Slightly belated thanks works, like a charm.

had forgotten all about it and was relying on Windows for colour printing and Ubuntu for greyscale but all's back to normal in the world again.

Cheers

Max

---

### Post by peer30 on 2012-03-13
Does this changing from SX205 to DX4800 not mean that the original scanner drivers will have a conflict? Or do I need other scanner drivers as well then?

Please advise.

---

### Post by peer30 on 2012-03-15
After having changed everything my Epson SX205 is not working at all any longer.
Then I changed it back to the original setting, but still my printer is not working and refuses to work.
I deleted the printer and I re-installed the printer again, but without result, it does not work at all.
What could have happened and what can I do to get the printer back?

Please advise.

---

### Post by peer30 on 2012-03-18
Well, last but not least, the solution suggested in this thread did not work at all here.
So I had to remove the printer, all drivers en reboot the desktop, have the printer configured again (localhost:631), just with the so called SX200 drivers.
In the meantime printing remains the same: black/white documents starting from 1-2 mm from the top, coloured documents "echoing" and the velocity: like a real snail in both cases. Copying and scanning are perfect: quality, fast.
I have tested this printer on older Ubuntu versions and then printing is perfect and fast, just up to version 11:04.
On another website I read that Oneiric effectively has problems with the Epson SX205, it is not Epson and the drives, but this time Oneiric "is to blame".

Well, I am sure my Epson SX205 is still working perfectly (I have tested the printer), I still have the original Windows-CD with its drivers, so this printer is interesting to Windows-users and Linux-users, and as far as Ubuntu goes up to version 11.04.

In the meantime I bought a Canon Pixma, and this one is working perfectly. I saw this printer with a friend with Oneiric, easily configuring, fast printing, perfect quality.

---

### Post by s_g_robertson on 2012-12-30
There is an issue in the gutenprint drivers relating to the sx200 that affected me in 12.04.  It is fixed in the version packaged for quantal onwards.  I installed that version and the colour alignment problem was solved.  Might help you?

---

