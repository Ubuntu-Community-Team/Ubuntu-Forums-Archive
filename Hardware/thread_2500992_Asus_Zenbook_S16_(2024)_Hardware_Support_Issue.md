---
title: "Asus Zenbook S16 (2024): Hardware Support Issue"
date: 2024-09-19
forum: Hardware
---

### Post by abmmhasan on 2024-09-19
I've set up the Ubuntu 24.04 in the new Asus Zenbook S16 (2024).
Product Link: [https://www.asus.com/laptops/for-home/zenbook/asus-zenbook-s-16-um5606/techspec/](https://www.asus.com/laptops/for-home/zenbook/asus-zenbook-s-16-um5606/techspec/)

Issues faced on installation:
1. The boot media should be UEFI + GPT (any other combo simply fails; though it is not a problem)
2. After selecting Setup (1st option in boot menu) it takes too long to prepare the whole thing (just looooooooooooooong black screen, feels like a life time)
3. Needed to provide persistent cache partition (I have provided 2GB) to properly run (at least that is what I encountered)
4. On live desktop the installation dialog took too long to prepare.
5. After the setup finish, once reboot, the OS just stuck in blank screen again (which I resolved though; process given below)

Issues during OS run:
1. To resolve the startup blank screen issue (after selecting Ubuntu as stated above)
- Press E in boot menu; added **nomodeset** in place of **quiet splash **& **Ctrl+x**
- Now I was able to get in
- Still it was too slow to enter the login screen
2. I believe It failed with several drivers (specifically GPU; the laptop model uses Radeon 890M)
- Display was OK though (I think was coping with old AMD driver)
- I had to permanently add **nomodeset** in Grub default otherwise the same problem returns.
3. I didn't check any other thing yet, but there could be others
4. In addition to these, Ubuntu is performing slow enough. Cause the Windows 11 (I use duel boot) even performs faster (And for this, I think the hardware driver/firmware need to updated).
5. Sound also doesn't work

---

### Post by shaggyone2 on 2024-12-07
Good day, just bought the laptop.

1. At first I used to add `nomodeset`, but installing radeon drivers from amd page: [https://www.amd.com/en/support/download/linux-drivers.html](https://www.amd.com/en/support/download/linux-drivers.html) helped
2. There was an annoying keyboard backlit blinking. I tried to boot windows (didn't plan to use it at first) and blinking stopped. I used asus utils under windows to turn off smart backlit.

There are still issues
1. With bluetooth, it seems that there is a solution , but I didn't try it [https://github.com/BNieuwenhuizen/zenbook-s16](https://github.com/BNieuwenhuizen/zenbook-s16) 
2. No screen brightness control. I tried several approaches, none of them helped.

---

