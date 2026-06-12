---
title: "Howto get rid of ubuntu-proposed updates?"
date: 2010-05-23
forum: Hardware
---

### Post by timosha on 2010-05-23
After a lot blood, sweat and tears I had a nice and stable Lucid working on my IBM Thinkpad R51. 

In my ignorance I klicked "proposed-updates" in Software Sources". One of those "updates" killed suspend on my old R51. Now I can only resume once from suspend, all other resume from suspend results in a complete freeze of my R51.

How can I get rid of these proposed-sources "updates" and get back to the release version of 10.04. If possible without a complete re-install then a re-install will fail because my oldie has an Intel 845/855GM video chip.

---

### Post by plucky on 2010-05-24
> **timosha said:**
> After a lot blood, sweat and tears I had a nice and stable Lucid working on my IBM Thinkpad R51. 

In my ignorance I klicked "proposed-updates" in Software Sources". One of those "updates" killed suspend on my old R51. Now I can only resume once from suspend, all other resume from suspend results in a complete freeze of my R51.

How can I get rid of these proposed-sources "updates" and get back to the release version of 10.04. If possible without a complete re-install then a re-install will fail because my oldie has an Intel 845/855GM video chip.

Open **Synaptic Package Manager** and open the **Origin** window and select the Proposed repository and see what was installed.It will have a green button.

You might have to re-install the older versions of anything the proposed repository installed using the normal repositories as they might have been removed when the newer versions were installed.

Good Luck

---

