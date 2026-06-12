---
title: "Printer quit working after running out of paper"
date: 2008-05-10
forum: Hardware
---

### Post by umdmariachi on 2008-05-10
I just installed 8.04 using Wubi last week on my laptop, and everything was working great. My printer (HP p1006) installed and worked great, and I also installed a network printer (HP 6200). 
I was printing yesterday though, my printer ran out of paper, and I hit the cancel button on the printer instead of the continue button on the desktop. After that point, every time I try to print something it sends it to the printer and shows the job as complete.
I tried uninstalling and reinstalling the printer. A reboot did nothing to help either. Documents still print fine on my network printer. (Thank God, I had 3 10 page papers due yesterday)
Any help or a kick in the right direction would be much appreciated.

Thanks, 
Clint

---

### Post by umdmariachi on 2008-05-13
Ok, so I booted windows and printed some stuff, and now its working fine in ubuntu again. I dunno why it happened though.

---

### Post by xyphier on 2009-03-19
Had the same problem with the P1006 and finally figured out how to fix it. You will need the HPLIP plug-in to do this.

First make sure there are no print jobs in the queue as they will just jam up again as soon as you restart the queue.

Turn your printer off and take the paper out. Turn it back on and let it go through its boot up process.

Now put the paper back in and press the red "X" button.

Goto the HPLIP plug-in and refresh the printer (right click on your printer and select "Refresh Device")

Now click on the "Print Control" Tab and click "Start Printer"

At this point the printer should look like its ready to go with no errors.(do not start a print job at this time)

Restart Ubuntu with the printer ON

Start print job


Hope this does the trick, it works for me every time now. Before I figured this out I about drop kicked my printer through the window.

---

