---
title: "HP P1006 laser printer not working on Sony Vaio laptop"
date: 2009-02-13
forum: Hardware
---

### Post by teachmeifyoucan on 2009-02-13
Hi,

I have a Sony Vaio laptop with Ubuntu 8.10 installed. I have just connected an HP P1006 printer, which is recognized by the system.

When I try to print a test page (or a Word document), the job appears in the printing queue, then disappears after a few seconds (as though it had successfully printed). However, no print is made.

I have installed "hplip" from sourceforge, to no avail.

So much of my external hardware does not work on Ubuntu, and this is the final straw. If this doesn't work out, I'm finally shelling out for a Mac... :-(

Cheers

r

---

### Post by cariboo on 2009-02-13
You may want to uninstall the version of hplip from sourceforge, as it is installed by default. Have you installed **hplip-gui**, it is available in the repositories.

Jim

---

### Post by teachmeifyoucan on 2009-02-13
> **cariboo907 said:**
> You may want to uninstall the version of hplip from sourceforge, as it is installed by default. Have you installed **hplip-gui**, it is available in the repositories.

Jim

How do I uninstall it? "sudo uninstall" does not work.

---

### Post by teachmeifyoucan on 2009-02-14
HELP! Please? Anyone?

I can print from any program in Ubuntu, including Wine. Everything works properly, except that the printer itself does not react. The job goes into the queue, is "printed" and then disappears from the queue after about a minute.

I've already tried everything I can. I urgently need to print some important letters and send them out on Monday...

Thanks in advance to anyone who has a solution.

---

### Post by teachmeifyoucan on 2009-02-18
I finally solved the problem. Now how can I delete this thread?

---

### Post by Axdrenalin on 2009-02-25
> **teachmeifyoucan said:**
> I finally solved the problem. Now how can I delete this thread?

I'd be interested in knowing what you did to solve this issue. I have a P1006 hooked up to my Q6600 setup and get the exact same issues that you're describing here. I've not had any luck at all getting it to work, and have been trying for about a week now.

If you've got any guidance you would be willing to share, It would be greatly appreciated.

Thanks,

Ax

---

### Post by teachmeifyoucan on 2009-02-26
Gladly, Ax.

Basically, I downloaded the software from this page, and followed the command line instructions specified.

[http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/)

It worked like a charm.

Occasionally, however, my laptop still doesn't recognize that the printer is plugged in. When this happens, I simply unplug the printer's USB cable from my laptop, then plug it back in. Then the printer is always recognized immediately, and any pending printing jobs start printing right away. Of course, the printer has to remain turned on when you unplug it from and replug it into the computer.

Good luck, and post again if something goes wrong.

---

### Post by Axdrenalin on 2009-02-26
I appreciate you posting a response so quickly with your suggestions and info. I've been down the foomatic road on numerous occasions, and have tried all sorts of other workarounds that I've found on the 'Net, but to no avail.

My problem isn't so much that I can't get the drivers installed, but in the fact that once I print that first page or document - even a test page - the print job doesn't get released and the printer status says "Processing" and I get a dialog box in the lower left area of the desktop that says "Printer Error - There is a problem with the printer."

This problem is replicated on both computers I've tried them on, my HP laptop as well as one of my many Q6600 Boxes at the house.

It all just hangs there, and unless I unplug the USB cable from the back of the printer to try to reset things it never clears up. Sometimes even doing that leaves the printer in a state of suspension, and it still doesn't work even after I plug it back in.

This has been the single frustation that I've encountered using Linux, and I've tried several different distros in hopes that one might handle the problem better than another. 

Any other ideas or suggestions that you (or anyone else) had concerning this particular SNAFU would be greatly appreciated. 

Ax

---

### Post by teachmeifyoucan on 2009-02-26
Well, from what you've written it looks as though your problem is different from mine (I never got error messages). I am a typical end user and know nothing at all about Linux save for what I can google. If nobody else can help you here, I suggest you seek out professional help. I ended up paying a professional Linux geek to get my laptop's jack for external speakers to work, because nobody could help me online either.

---

### Post by Georgesl on 2010-02-22
I'll chime in and say that I'm having similar issues with my HP3005n printer and Jaunty.  It is recognized but then it will not print a test page or anything else unless I unplug and replug the USB cable.  Every print job requires an unplug/replug, then it sits for about 15 seconds and then the printer works... for that job only.

Very frustrating.  I hope that someone gives me a hand with it soon, even if it means being whacked around a bit with a noob stick.

---

