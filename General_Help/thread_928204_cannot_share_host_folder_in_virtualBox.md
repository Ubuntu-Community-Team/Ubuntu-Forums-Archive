---
title: "cannot share host folder in virtualBox"
date: 2008-09-23
forum: General Help
---

### Post by dhap on 2008-09-23
I am using windowsXP as a virtualBox host on my Ubuntu 8.04. Wanted to get some of the host folders available in my guest windows. I went to device->shared folders in VB and added the necessary folders. But couldn't see them in my guest OS. I remember I had to run some other command from command line within windows, but couldn't recall what. can someone help me out.

---

### Post by jimmy the saint on 2008-09-23
xp is the guest or the host?  if you boot up into Ubuntu then start VBox to run XP, it is the guest.  If this is the case, you need to map the folder that you enabled to share as a network drive.  Essentially, the guest and host are two different machines that can only communicate via an imaginary network.

---

### Post by dhap on 2008-09-23
Thanks Jimmy, sorry for the typo...XP is the guest and Ubuntu the host. I was able to see a host folder in XP by adding it to the shared folder in VBox and then running "net use x: \\vboxsvr\share". I could copy files from Ubuntu to XP. However if I tried to copy files from XP to Ubuntu the XP guest crashed. I didn't check the 'read only' mode in VBox either. What could go wrong?

---

