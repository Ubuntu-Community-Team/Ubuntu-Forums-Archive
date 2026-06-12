---
title: "Printer Does Not Print"
date: 2008-11-07
forum: General Help
---

### Post by Ciwan on 2008-11-07
Hi Guys

I have a HP LaserJet P1006 and I want to print a document that I created in OpenOffice.

When I first connected the Printer, A little balloon came up saying that the printer was installed and it was ready for use !!!

Now that I am pressing the [ Print ] button, it is not printing :(

Someone **Please** help :(

Thanks

---

### Post by Ciwan on 2008-11-07
someone please help :( I have some Uni work that needs printing :(

---

### Post by mdurham on 2008-11-07
Try, System->Administration->Printing right-click on printer icon and make sure it's enabled.

---

### Post by Ciwan on 2008-11-09
Hi Mdurham

I tried that, the printer is Enabled and set to be the Defaul **BUT** still it is not printing :(

**Please** Help.

---

### Post by mdurham on 2008-11-09
Have you installed 'hplip', this might help, give it a try.

---

### Post by Ciwan on 2008-11-12
How do I install hplip ??

[EDIT]

OK I just used { sudo aptitude install hplip } to install it, but still I can't print anything :(

Please Help :(

---

### Post by Scunnered on 2008-11-12
You may find some assistance by looking at Linux Printing.  I had no end of problems with a printer and on checking there found that it was a paperweight in their opinion.  Has a look at yours and it is shown as mostly working.

I have to rush out shortly so did not take matters further. Perhaps you will find an answer there.

Hope this assists

---

### Post by Newtothegame on 2008-11-12
Hey, 

I have messed with printers at work which are also hp and they required me to mess with the cups driver stuff. Mine are currently not working but i did have them working for about 3 mo. I am attaching some links that explain how to get it on a pharos system. But they also touch a bit on messing with the drivers. 

[http://dacc.wordpress.com/2007/02/06/uw-pharos-printing-from-your-laptop-linux-or-mac/](http://dacc.wordpress.com/2007/02/06/uw-pharos-printing-from-your-laptop-linux-or-mac/)

[http://www.byui.edu/wireless/linuxprint.htm](http://www.byui.edu/wireless/linuxprint.htm)

Hope this is not leading you in the wrong direction. 

Best of luck.

---

### Post by mdurham on 2008-11-12
> OK I just used { sudo aptitude install hplip } to install it, but still I can't print anythingDid you run the program after installing it?

---

### Post by KrazyPenguin on 2008-11-12
Something happened to my hp as well using IBex.  It won't print and it is a HP 5740.

Booted into Hardy, and it works.  This was tester on the same file to make sure there wasn't something wrong with the oo file.

My Ibex is also starting to lock up and hard freeze a lot.

Never used to do that.

Since this new kernal update my computer is on drugs.

I'm going back to Hardy until the kernel is updated again.

:guitar:

---

### Post by KrazyPenguin on 2008-11-13
After doing an upgrade today, my printer on ibex now works!!!

SOLVED

:guitar:

---

### Post by xyzt on 2008-11-15
Thank Zeus for small things. I had Ubuntu 8.04 installed and my HP Laserjet 1006 working after some fiddling I completely forgot about by now, and went to foolishly try Ubuntu 8.10. The printer accepted jobs (as by [http://localhost:631]("http://localhost:631")), went back to idle and didn't even make a single working sound nor, obviously, printed a test page.

So, I rolled back to 8.04. Of course I have been trying to get the printer to work since rollback... until I read the *"But did you run the program?*" and remembered to run (console) _hp-setup_ (not hp-lip). Which installed the plugin and firmware, something it *refused to do* in 8.10. The printer is now working.

Woof. Thanks. It's solved regarding my own situation.

---

