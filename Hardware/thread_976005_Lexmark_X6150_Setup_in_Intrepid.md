---
title: "Lexmark X6150 Setup in Intrepid"
date: 2008-11-08
forum: Hardware
---

### Post by pwebster25 on 2008-11-08
I have a Lexmark X6150 multi-function printer.  I just installed Intrepid on it (it was previously a Windows box.  I followed the guidelines in the tutorial at: [http://ubuntuforums.org/showthread.php?t=49714]("http://ubuntuforums.org/showthread.php?t=49714")

except that I used a z55 driver instead of the z600 driver through the whole process.  That is the driver that was recommended by the openprinting database.

I got to the end and ran a test page.  It ran a paper through (which was more than it had done up to that point with the default choices) but it threw the following error: "can't write page 1 header"

I thought I had just messed up all the code but I found in the following pre-release forum on Intrepid that several others had the same problem with their x1240 that had worked in all the previous releases of Ubuntu.
[http://ubuntuforums.org/showthread.php?p=6035120#post6035120]("http://ubuntuforums.org/showthread.php?p=6035120#post6035120")  

I wonder if there are any clues as to what I could do to resolve this.

Thanks

---

### Post by pwebster25 on 2008-11-29
I deleted the printer and followed the how to at [http://ubuntuforums.org/showthread.php?t=419661](http://ubuntuforums.org/showthread.php?t=419661) .  This how-to worked much better.  It finds the ppd driver (for z55) without a hitch when I connect the printer and run through the dialogs (I have an x6150 but z55 is recommended).

It won't do a test page.  It appears to progress but it doesn't do anything and then it just disappears from the queue.  Any suggestions?

---

### Post by pwebster25 on 2008-12-08
After no responses and no more attempts to make it work it miraculously works now.  Don't know why.  Maybe a CUPS update.

Go figure.

---

