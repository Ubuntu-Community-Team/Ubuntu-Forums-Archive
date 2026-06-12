---
title: "Problems with the Ubuntu installation after restart? Read here."
date: 2005-11-11
forum: General Help
---

### Post by ShepMode on 2005-11-11
I spent 3 days trying to install Ubuntu. This is the problem I encountered:

I booted from CD, and setup my partitions. The installer then installed all files needed for the OS. I was then instructed to restart.

On restart, Ubuntu would start to load and then I would be dumped to the console, with the following error message (or something similar, I can't quite remember it):

"ALERT: Could not mount /dev/mypartition. Dumping to console."

After a lot of investigation and help from people in #ubuntu, it turned out that the problem was with my hardware setup. It could have been one of 2 problems: 

- My hard drive was plugged into my motherboard with a 40 pin IDE lead. I changed the lead to an 80 pin IDE.

and / or

- My hard drive was set to Cable Select. I changed it to Master.

I hope this helps someone.

---

