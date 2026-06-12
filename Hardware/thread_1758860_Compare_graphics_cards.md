---
title: "Compare graphics cards?"
date: 2011-05-15
forum: Hardware
---

### Post by meddyuk on 2011-05-15
Hiya i've got a NOVATECH GFFORCE 6200 256MB AGP card lying around. I wondered if it will make any difference if i put in the new PC which currently has a intel r g965 express chipset? Which is the better one?

---

### Post by BlouBlou on 2011-05-15
Intel graphic cards are the worst in my opinion, and NVidia are the best ones, so, stay with it :)

Keep in mind that NVidia is a linux-friend and makes its own driver, and community has its own driver too, called Nouveau.

I would stay with GeForce.

---

### Post by meddyuk on 2011-05-15
thats what i thought, but i didnt want to put the AGP card in the new PC, if the onboard graphics was a lot better. I bought the AGP card in 2008.

---

### Post by coffeecat on 2011-05-15
> **BlouBlou said:**
> Keep in mind that NVidia is a linux-friend and makes its own driver, and community has its own driver too, called Nouveau.

@BlouBlou, this is a very strange statement. Nvidia make their own proprietary driver for Linux, it is true, but provide no information for the open source nouveau team, which has to do all its development itself. Intel, on the other hand, work with the FOSS community and the driver for Intel graphics cards is open source. Also compare nvidia's stance with ATI/AMD. ATI provide a proprietary driver for Linux, but they also work with the FOSS community to develop the open-source ati driver for ATI cards. Which is why the ati driver is generally more developed than the nouveau one. How then is nvidia more of a friend to Linux than ATI/AMD or Intel?

> **meddyuk said:**
> thats what i thought, but i didnt want to put the AGP card in the new PC, if the onboard graphics was a lot better. I bought the AGP card in 2008.

@meddyuk, that nvidia chipset is elderly. It dates back to well before 2008. Have you tried Ubuntu with the onboard Intel graphics? Although you will have a separate GPU with the nvidia, you might find that the Intel graphics is quite enough for your needs. It will certainly support 3d-compiz for Unity.

---

### Post by MartyBuntu on 2011-05-15
> **meddyuk said:**
> ...but i didnt want to put the AGP card in the new PC,


Your new computer has an AGP slot?

:confused:

---

### Post by meddyuk on 2011-05-19
I open up appearances on this new pc and i do not get the option for desktop effects with the intel chipset. is it worth installing the old nvidia card which i know allows desktop effects. I wan the awn dock

---

### Post by coffeecat on 2011-05-20
> **meddyuk said:**
> I open up appearances on this new pc and i do not get the option for desktop effects with the intel chipset.

I see you are  running 11.04/Natty. That option has been removed from the appearances window but that doesn't mean that you are not getting desktop effects. You get desktop effects with Intel graphics but with Natty there are different ways of going about it.

There's an easy way to check if you are getting desktop effects. Open a terminal and move it over another window or a desktop icon. Is it semi-transparent? If yes, you have the ability to have desktop effects. In fact, terminal transparency is a desktop effect.

Second question. Are you getting the Unity desktop? If yes, you are getting desktop effects because Unity is a compiz plugin. If you want more effects install the package compizconfig-settings-manager but do not try to enable the desktop cube. You will break your desktop in Natty if you do. Or, rather, if you want to enable the desktop cube, post back and I'll give you a link.

---

### Post by meddyuk on 2011-05-20
i want the awn dock with the elegant glass theme. i do get the icons down the left on unity so should be alright.

---

### Post by meddyuk on 2011-05-20
Got it sorted went in and changed from Gnome to Compiz and i've got it how i want it.

---

