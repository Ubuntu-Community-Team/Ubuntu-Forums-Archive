---
title: "PDF printing using cups-pdf"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by sct10 on 2006-10-03
I just bought the "Ubuntu Hacks" book by Oxer, Rankin, and Childers.  In it they state that one can install pdf printing (print to a pdf file instead of an actual printer) using the following:

sudo apt-get install cups-pdf

However, apt-get cannot find the cups-pdf file at all.  After searching the web I found a Debian distribution of it but when I tried to install it I got a error message "Error, dependency not identifiable:  libc6".  

Anyone know why cups-pdf cannot be found with "apt-get"?

Thanks,
Steve

---

### Post by sawjew on 2006-10-03
It's in the Universe repositories not the Main repositories.  You need to enable the Universe repositories.  

To do this open Synaptic (System>Administration>Synaptic Package Manager) then go to the Settings menu in Synaptic and select Repositories.  

On the window that comes up click the Edit button on the right.  

The resultant window has a heading of Channels at the top and another heading of Components lower down. 

Under the Component heading there are four check boxes, check each one of these. 

Repeat this for each item under the Channel heading (in the drop down list).  

After you have done this reload your repositories and then follow the instructions found here [http://www.ubuntuforums.org/showthread.php?t=188860&highlight=cups-pdf]("http://www.ubuntuforums.org/showthread.php?t=188860&highlight=cups-pdf")

---

