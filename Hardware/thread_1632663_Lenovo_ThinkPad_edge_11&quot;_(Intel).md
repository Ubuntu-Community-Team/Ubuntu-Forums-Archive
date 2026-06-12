---
title: "Lenovo ThinkPad edge 11&quot; (Intel)"
date: 2010-11-28
forum: Hardware
---

### Post by SpritBille on 2010-11-28
Hey.

I have just bought a Lenovo ThinkPad edge 11" with Intel processor. Works fine with Windows 7, but now i won't my old fried Ubuntu back on top!

After installing Ubuntu 10.10, I can conclude that there is a couple of problems:
1) mouse/keyboard  freezes for a couple of seconds with some minutes interval.. I have might found a workaround (still testing).
2) My programs doesn't show up at the program bar at the button of the screen.
3) Wireless Internet does not work! :(

Has anyone found some workarounds for this?

Kind regards
Bille

---

### Post by kolafa on 2010-11-28
> **SpritBille said:**
> 
3) Wireless Internet does not work! :(


Perhaps missing driver from Intel? On my Lenovo R500 this was iwlwifi-5000-ucode-8.24.2.12 (check this) The installer (Debian squeeze) told me about possibly missing drivers.

Jiri

---

### Post by Nailor on 2010-11-30
> **SpritBille said:**
> Hey.

I have just bought a Lenovo ThinkPad edge 11" with Intel processor. Works fine with Windows 7, but now i won't my old fried Ubuntu back on top!

After installing Ubuntu 10.10, I can conclude that there is a couple of problems:
1) mouse/keyboard  freezes for a couple of seconds with some minutes interval.. I have might found a workaround (still testing).


On my laptop the mouse is the only thing that freezes. Keyboard still works fine. Annoying problem. What are you trying as a solution to it?

> 
3) Wireless Internet does not work! :(


You need to compile Realtek drivers manually, they don't ship with the Ubuntu 10.10. Just Google for Realtek 8192se and Ubuntu and you should find a bunch of howtos on the topic.

---

### Post by rogst on 2011-01-04
On my Thinkpad edge 11 the only thing I notice is that the mouse sometimes freezes for 3-5 seconds.

Did your solution work ?

---

### Post by SpritBille on 2011-02-13
Now I have found solutions to both the freezing and the network.

For the wireless network just install Realtek rtl8192ce_linux_2.6.0005.1116.2010.tar.gz

Freezing have also been solved although I can't remember how :)

But the program bar problem is still unsolved.

---

