---
title: "Grub failing after ubuntu install"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by karuzo on 2009-11-08
Hello all,
  I'm having this situation where although possibly common, I was unable to find a solution for.
On Thursday I reinstalled  windows on my work computer after installing a new hard drive. I decided to also install ubuntu in case I need it (I did need it before and used the live cd).
Windows is installed on primary hard drive and ubuntu on a slave drive. Problem is that even though I pointed it to install grub on first drive I get this error when booting:
'grub error: no disk found' and a grub-rescue prompt.
My main problem is that I cannot spend too much time figuring this out on my work computer as I am not supposed to, for non-work issues. If I cannot resolve it in 10 minutes I will have to reinstall windows, or use its recovery feature for that matter. Any suggestions on how to reinstall grub or fix the situation in a safe and sure way that will work? My main computer at home is running ubuntu and I'm familiar with the terminal and basic commands...
Thanks.

---

### Post by mechro on 2009-11-08
You can edit grub when it boots so you can look for the right "root" and partition to boot.

[http://members.iinet.net.au/~herman546/p15.html#Temporarily_Edit_the_GRUB_Menu](http://members.iinet.net.au/~herman546/p15.html#Temporarily_Edit_the_GRUB_Menu)

This isn't a permanent fix. You'll have to edit and maybe re-install grub.

Try the quick fix and see if it works.

---

### Post by mechro on 2009-11-08
A useful tip when editing grub on the fly is the tab key prompt e.g if you edit the root line to read **root(** then pressing the tab key will offer you the relevant options and you can guess which is the correct one and try it

---

### Post by mechro on 2009-11-08
By the way, is the Grub boot menu offering the option to boot into Windows? If it does then you haven't got much of a "work" problem. If you can boot Windows then you can sort out booting Ubuntu at leisure.

---

### Post by karuzo on 2009-11-08
> **mechro said:**
> By the way, is the Grub boot menu offering the option to boot into Windows? If it does then you haven't got much of a "work" problem. If you can boot Windows then you can sort out booting Ubuntu at leisure.
Mechro - thanks for the response. I looked into the link you provided. The machine does not get into any grub menu, only a command line "grub rescue". I managed to go to my office and bring that computer home and try to fix the problem. While researching more, I let it perform another ubuntu install with hopefully a proper chive of grub location install.
Thanks.

---

### Post by mechro on 2009-11-08
Oh dear, I keep forgetting that Grub2 is now the chosen path! ;)

Boot rescue is significantly different...

[https://help.ubuntu.com/community/Grub2#Editing](https://help.ubuntu.com/community/Grub2#Editing)

---

