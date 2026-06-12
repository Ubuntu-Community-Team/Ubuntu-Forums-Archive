---
title: "Automatically modprobe ndiswrapper"
date: 2008-09-21
forum: General Help
---

### Post by Inane_Asylum on 2008-09-21
I got my wifi working again on my new installation, but this time, I have to run "sudo modprobe ndiswrapper" after every reboot.

How would I go about making that command automatic at startup?

---

### Post by phidia on 2008-09-21
From the guide I used to install ndiswrapper:
> 7. Make sure ndiswrapper loads up every time we start Linux:
Code:

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
Hope that helps.

---

### Post by Inane_Asylum on 2008-09-21
Sweet, thanks...I'll try that when I get to my computer.

What guide did you use?  I was hunting down a good guide but ended up using bits and pieces from lots of guides. (I had a particularly difficult wifi card to support)

---

