---
title: "Breezy: Logout/ctrl+alt+backspace broken"
date: 2005-11-08
forum: General Help
---

### Post by Curlydave on 2005-11-08
I did a clean install of Breezy when it came out. I have been having this problem since then, but havn't posted about it. Log out and ctrl+alt+backspace no longer function properly in Breezy. They kick me to a black screen with no hope of return or safe reboot. All I get is black. This did not happen with my dist-upgraded Breezy, but it does with my clean-install one. Surely I can't be the only one who has this bug. How do I fix it? Thanks!

---

### Post by joris.brus on 2005-11-08
Happens to me to.. 
hit ctr + alt + f1
login and type startx to restart x

Or login as root and type 'telinit 0' to shutdown

---

### Post by dariomanno on 2005-11-09
I lost all hope when that happened to me! An ex-windows user panicked! :) And I just typed "reboot" on that black screens prompt... and it did exactly that! Ha ha ha, talk about an old-habit solution to the problem :p

---

### Post by Pablo_Escobar on 2005-11-09
Try to add 
> Option "UseInternalAGPGART" "no"

To Your /etc/xorg.conf 
Device section.

I had the same problem after ATI driver installation.

---

