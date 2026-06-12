---
title: "[SOLVED] Able to install Gutsy, but..."
date: 2008-07-15
forum: General Help
---

### Post by charlesbw on 2008-07-15
I was trying to install Hardy, but seen as it was not detecting my drives I tried to give Gutsy a tried (and then hopefully upgrade).  But after installing Gutsy (which detected my drives with absolutely no problems) I cannot seem to get the installed version of the OS to be visible.  After grub loads and i select Gutsy, the screen goes blank and my monitor stops receiving information from my video card (which is a Nvidia XFX 8800 GT).  Any suggestions on how to make gutsy show me my ubuntu desktop?

---

### Post by charlesbw on 2008-07-15
in a related thread someone suggested i try vga=775 and that worked, is there something like that to resolve the compatibility issue?

---

### Post by overdrank on 2008-07-15
> **charlesbw said:**
> in a related thread someone suggested i try vga=775 and that worked, is there something like that to resolve the compatibility issue?

Hi and yes you can try this but the method has changed a little since you have installed. When you see the grub loading then press the escape key and highlight the selection you want and press e to edit the kernel line. Then remove the quiet splash and add the vga=771 or 775 then press enter and then b for boot.

---

### Post by charlesbw on 2008-07-17
thanks again overdrank

---

