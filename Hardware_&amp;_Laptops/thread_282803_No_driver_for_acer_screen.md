---
title: "No driver for acer screen?"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by ZombiekE on 2006-10-23
I just upgraded to Edgy and after the OS loads I get to a blue error message telling me that the driver for the screen couldn't be found. I wish I could post the log here, but I don't know how to access my ubuntu partition from Windows XP.

I am using a Laptop Extensa 2600 series (2603LMi). I hadn't had any problems with this before. What can I do? I can choose between yes or no in that error message, but I always get nowhere with that, can't even type commands.

Edit: I just opened Xorg.0.log (I think that was the name) in /var/log/ in the recovery mode and saw these lines with errors:

(EE) Failed to load module "i810" (module does not exist)

And then after Module synaptics... in the next section, I guess this is the driver thing

(EE) No drivers available
Fatal server error:
no screens found

Could the second error be caused by the first one? How fix that?

---

### Post by ZombiekE on 2006-10-24
Sorry for posting in my own topic, but I added some new information in the original message that could be useful to solve this.

---

