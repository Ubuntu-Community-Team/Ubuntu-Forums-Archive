---
title: "video unreadable"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by wolfcub on 2009-03-11
I tried to install ubuntu but after a few questions my screen went

unreadable,It wes suggested that the problem might be my video card

I have a NVDIA GeForce 7300GS.

If it is the problem what do I need to do so I can use ubuntu.

                                                  Thank You:

                                                    wolfcub

---

### Post by ajgreeny on 2009-03-11
When you boot to the CD use F6 (I think) and choose **low graphics mode** or some similar description and you may be in luck when you try to install.

---

### Post by martrn on 2009-03-11
Installing Ubuntu 8.04 involves editing xorg.conf files Installing Ubuntu 8.10 doesn't work that way as its no-long reads xorg.conf files.

Install from an alternative CD ---

At first boot :
select root shell prompt then :

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo reboot
```

Sometimes that works.

---

