---
title: "nvidia graphics card problem with 18.04"
date: 2019-07-21
forum: Hardware
---

### Post by bee+new on 2019-07-21
Is anyone having problems with NVIDIA graphic cards and Ubuntu 18.04 - during or after install

---

### Post by Autodave on 2019-07-21
None here on the 4 different machines.  What kind of problems are you having?  Can you give us some info on your equipment?  What drivers, if any, have you installed/tried?

---

### Post by cruzer001 on 2019-07-21
> **bee+new said:**
> Is anyone having problems with NVIDIA graphic cards and Ubuntu 18.04 - during or after install
Yes!  I think it killed my cat.

How bout a model number?

All I use is some form of nvidia, really like the geforce brand. but others have work with little or no problems.

I do not run the latest models, thats usually where the trouble is.

---

### Post by rbmorse on 2019-07-21
I didn't have any problems with the 970 GTX. 


But, as cruzer1 noted, the new cards are a different story.  My "new" box has a 2080 RTX. Ubuntu 18.04 didn't recognize the card.  Nouveau just gave me a generic 1240 X 1080 display (with no options to resize) and there was nothing in repository that supported the 2080. The graphics-drivers ppa has the required 430 driver, and while I installed that I consider it a sub-optimal solution. 

19.04 (Dingo) recognized the card and will install the 430 driver during the installation if the proprietary drivers option is selected.

---

### Post by CatKiller on 2019-07-21
> **cruzer001 said:**
> Yes!  I think it killed my cat.

Sorry, I think that was me.

For the OP, "problems with nVidia graphics cards during install" is generally a result of not having nomodeset. If that doesn't fix it you're going to need to provide more details, as everyone else has said.

---

### Post by Autodave on 2019-07-22
RTX 2070 here (very new) with no problems after adding the ppa.

---

