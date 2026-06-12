---
title: "Samsung clp-315 karmic printer problems"
date: 2009-11-04
forum: Hardware
---

### Post by ubiubi on 2009-11-04
Hello all

I installed karmic koala beta a few months ago (erasing my jaunty version in the process but not my home partition!) and my printer
continued to work flawlessly!(I suppose it took the jaunty settings and applied them to the new system, like my old modem details etc...).

The problems arose when I updated to the final version of karmic last week. I also erased my home directory as part of my spring cleaning.

The printer was recognised as Samsung cpl-310 (not 315) and all it printed was error messages. I followed a thread to download the latest unified samsung driver but the installation programme refuses to recognise that the printer is attached (I have unplugged and replugged it several times) and so the installation is not complete.

I also followed threads for a programme which was supposed to solve colour issues.
The result is that I now have a printer which will print in black and white but not colour!

Any suggestions?

Cheers):P

---

### Post by josvanr on 2009-11-14
I can confirm your problem with this printer on the latest karmic version, mine also stopped working .... Any solutions yet?

---

### Post by josvanr on 2009-11-14
hi all, I just found a solution/fix/workaroud (what ever) for this on this page: [http://www.xappsoftware.com/wordpress/2009/11/11/clp315karmic/](http://www.xappsoftware.com/wordpress/2009/11/11/clp315karmic/)
I'll include the text below, just in case the article there is removed.
The fix works: after following the steps described, the samsung prints
it's old dark brown coffee stain-colors again! Happy!


josvanr

-----------------------------------

This color laser printer is automatically detected but it doesn't work.

Ubuntu 9.10 detects this printer as a Samsung-CLP-310-Series printer, this is the problem.

And here is the solution:

Go to System->Administration->Printing

a printer configuration window will appear,  

double click on the Samsung-CLP-310-Series icon, a printer properties window will appear:

click on the Change Button for Make and Model, from the list select Samsung and click on the forward button then from the Models list select the CLP-315 and then click on the Forward Button.

Select "Use the new PPD" and then click on the "Apply" button

Select Printer Options and configure the printer then click on the apply button.

This method does not use the Samsung CD so you can apply this procedure also on your netbook, I didn't try this procedure on my AspireOne but it should work fine.

---

### Post by gg1 on 2009-11-15
> **josvanr said:**
> 
I'll include the text below, just in case the article there is removed.
The fix works: after following the steps described, the samsung prints it's old dark brown coffee stain-colors again! Happy!


josvanr


Josvanr I think that this article will stay on my blog for a lot of time :), however thank you for adding this link. I hope this can help some users.

Gg1

---

### Post by torracollons on 2009-11-24
> **gg1 said:**
> Josvanr I think that this article will stay on my blog for a lot of time :), however thank you for adding this link. I hope this can help some users.

Gg1
Thanks Thanks and a lot of Thanks.. my printer is working ok:popcorn:

---

### Post by Saito Chikara on 2009-11-28
I don't see any "Administration" under "System". Where do I need to look?

---

### Post by BuffaloX on 2009-12-03
> **Saito Chikara said:**
> I don't see any "Administration" under "System". Where do I need to look?

System->Administration->Printing
Is for Ubuntu, you are using Kubuntu, so you have to look for the Kubuntu equivalent.

I'm sorry I don't use KDE, so I can't tell you where it is, hope you found it already.

---

### Post by gg1 on 2010-02-07
> **BuffaloX said:**
> System->Administration->Printing
Is for Ubuntu, you are using Kubuntu, so you have to look for the Kubuntu equivalent.

I'm sorry I don't use KDE, so I can't tell you where it is, hope you found it already.

You should go to "Kickoff Application Launcher"->"System Settings" then, in Computer Administration" you should select "Printer Configuration".

This should work.
Let me know your results! So I will add a comment to the Blog Post.

GG1

---

### Post by josvanr on 2011-01-30
bump

any progress on te too dark colors from someone? 


.. I was just pondering: what's with this 'print preview' 
funtion in gimp and other programs. In the 20 years I've 
been using linux (and other os'es) I've never once seen 
a 'print preview' that looks like the printed result (not in color
or margins), also not on my now calibrated monitor.

josvanr

---

