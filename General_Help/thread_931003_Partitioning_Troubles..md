---
title: "Partitioning Troubles."
date: 2008-09-26
forum: General Help
---

### Post by AdamMPkins on 2008-09-26
I installed ubuntu via Wubi the other day with the intention to switching it to its own partition soon after. Once it was installed, i then decided to partition my hard drive with a 10 gb partition for Ubuntu.

I ran gparted on a live cd and it worked successfully. I then tried to boot to the windows partition and ran chkdsk. After rebooting, I attempted to boot to ubuntu so i could run the LVPM but instead recieved this error:
file:\ubuntu\winboot\wubildr.mbr
Status: 0x000000e
Selected entry could not be located because the application is missing or corrupt

I should note that Vista also gave me a similar error when i initially tried to boot but i put the OS cd in and used the "repair my os" option and booted in fine after the chkdsk.

What have i done wrong? Can I rectify this without uninstalling my wubi partition and reinstalling?

---

### Post by AdamMPkins on 2008-09-27
any help?

---

### Post by AdamMPkins on 2008-09-27
any help at all?

---

### Post by Gondee on 2008-09-27
Im not sure how to fix that one. But you could just use the Ubuntu installer. It seems to work much better

---

### Post by AdamMPkins on 2008-09-29
> **Gondee said:**
> Im not sure how to fix that one. But you could just use the Ubuntu installer. It seems to work much better

this doesn't help. I have settings saved in the wubi setup that id like to keep.

---

### Post by AdamMPkins on 2008-10-08
> **AdamMPkins said:**
> this doesn't help. I have settings saved in the wubi setup that id like to keep.

bumping this back up to get an answer.

---

### Post by Nxion on 2008-10-08
I have had this problem as well. And the issue was what Vista did to the partition. I did the same thing you did and it was gone. My suggestion is to uninstall Wubi from Programs and Features in Vista and reload. I think that might be the only way to fix the issue at hand. But who know I have been wrong in the past and there might be anbother way to solve this.

---

### Post by AdamMPkins on 2008-10-15
Can anyone offer any assistance?

---

