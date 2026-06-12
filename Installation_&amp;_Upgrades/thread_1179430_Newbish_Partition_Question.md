---
title: "Newbish Partition Question"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by r-t on 2009-06-05
Just yesterday I reinstalled Windows, and finally got round to updating drivers, etc. I've halved the size of the NTFS windows XP partition, so there's quite a big space left for an Ubuntu Installation. I did this through Partition Magic. The half that is waiting for Ubuntu is not formatted, it's unallocated.

I have a live disk of 8.10 which i'd like to use. 

So, when I get to the partition menu, what's my best option?


[LIST]
[*]If I choose install on longest span of free space, will this find the 70GB unallocated space? If so, That'd be good right? It's just, when I select this, on the preview bar it comes up with "Ubuntu 100%", which is kinda... strange.
[*]What about manual partition, would this be better? I'm not confident about making swap, and now I'm really confused. Someone told me I need one partition for installation, and one for swap. And another tells me I need one for root, one for home, and one for swap. eh?
[/LIST]
Guided resize seems to want to partition the already existing Windows sect, and Guided full disk isn't an option.

Oh yes, Wubi has never worked for me. 
Side question: Anyone know how to remove the boot up option it has made? now that I've unistalled the Ubuntu it created. Would it be bad to leave it there and install an actual ubuntu?

Perhaps 9.04 has updated, but I'd like to stick with my 8.10 for now :)
Thanks for any help :D

---

### Post by marshall.robert on 2009-06-05
> **r-t said:**
> I'm not confident about making swap, and now I'm really confused. Someone told me I need one partition for installation, and one for swap.

This sounds about right, but if you have over 2GB of RAM then you can get away without using it.

> **r-t said:**
> And another tells me I need one for root, one for home, and one for swap. eh?
 
This is just too complicated. It is only useful if you intend to run different Linux distros side by side or reinstall a lot.


I would recommend opening the Partition Editor in System -> Administration and setting up swap and an ext3 (or ext4 if that is an option) partition using that. Make swap about the same size as your RAM. Some people say that you should have 1.5 times the amount but personal experience tells me that you don't need that on modern systems any more. When I had 2GB the swap was barely touched, now I have 4GB it is only used for hybernation.

Then when you go to install choose manual and select the ext3/ext4 partition and ticking format and selecting "/" from the drop down. The swap will be selected automatically so you need not worry about that. Just keep going with the installation after that.

Good luck, and hope this helped :D

---

### Post by r-t on 2009-06-05
One more tiny question ;)
Should the linux Ext3 be Logical or Primary, I'm assuming logical.

Thanks for your help, google was prooving kinda indecisive.

---

### Post by marshall.robert on 2009-06-05
Primary. You can have up to 4 primary or extended partitions on 1 hard drive. Logical partitions sit in extended partitions.

---

### Post by r-t on 2009-06-05
Will attempt an install now, thanks for your help :)

---

### Post by marshall.robert on 2009-06-05
No problem :D Good luck!

---

### Post by r-t on 2009-06-05
ugh... I had massive fail :(

Installation, fine. Everything done and dusted. I guess it then tried to load up Ubuntu... but GNOME failed, or something like that.

> *starting system tools                                                              [ O K ]
*starting deferred execution scheduler                                      [ O K ]
*starting periodic command scheduler atd                                 [ O K ]
*enabling additional executable binary formats binfmt-support    [ O K ]
*checking battery                                                                    [ O K ]
 
then it would flash different shades of black, the Linux X would appear, then disappear - and then it would just stop and return the the code above. Nothing else. 

I hope this is a common problem, and not something just my idiotic laptop is cooking up :P
I'm not sure how to boot back into the failed install of Ubuntu ^^"

---

