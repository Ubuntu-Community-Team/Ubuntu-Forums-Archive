---
title: "XSane stops working"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by BobSongs on 2006-08-03
With a fresh installation of Dapper XSane works just fine with the Brother drivers. No problem.

Then I'll call up XSane after several updates to Dapper. The splash screen appears and vanishes. Nothing follows. Normally all the different boxes appear and I can begin scanning.

But something then goes awry. I remove the Brother scanner drivers (sudo apt-get remove brscan2) and then I remove the XSane software (sudo apt-get --purge remove xsane) and I install from scratch. It still won't work.

Anyone else encountering problems with XSane?

I don't want to be flipping back to XP to get the scanner going.

---

### Post by zxee on 2006-08-04
If it was working prior to the updates perhaps something changed that borked xsane.
The way to get more info on this is to open xsane from a terminal so that even if it crashes-segfaults-whatever the terminal will usually provide you with some output.

---

### Post by BobSongs on 2006-08-04
Thanks, **zxee**. I failed to mention that problem.

When an application goes south I open the Terminal and check out any sign of death: something to tell me what's wrong.

In the case of XSane nothing is reported to the terminal.

Is there some way to see what an application does when it's fired up? Some kind of debugger? The benefits would be immense to see what an app does in its short lifespan.

---

### Post by zxee on 2006-08-04
> **BobSongs said:**
> Thanks, **zxee**. I failed to mention that problem.

When an application goes south I open the Terminal and check out any sign of death: something to tell me what's wrong.

In the case of XSane nothing is reported to the terminal.

Is there some way to see what an application does when it's fired up? Some kind of debugger? The benefits would be immense to see what an app does in its short lifespan.

Just to be clear here opening up a terminal after an app has vanished or failed to open is not the same as opening that app from the terminal. If you open from the terminal i.e > xsane you will normally get some output if things go wrong. You can check /var/log for messages pertaining to xsane.
Hope that helps.

---

### Post by BobSongs on 2006-08-04
Sorry: that's what I meant.

Applications > Accessories > Terminal > xsane

Well. I tried to capture the image. Can't. Still, the answer is: I did try it at the command promt. That's what I meant in my previous post.

Now to find a debugger.

Note: there may have been an update since the drivers for xsane were installed. The current system is Dapper Drake and XSane works just fine.

---

