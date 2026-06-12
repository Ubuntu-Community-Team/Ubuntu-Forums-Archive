---
title: "Ubuntu 16.04 on Asus Vivobook S15"
date: 2017-10-24
forum: Hardware
---

### Post by karen-menezes on 2017-10-24
Am looking to replace my current Dell laptop. Was looking at a lightweight, core i7 (preferably 7th Gen or later) machine that can run Ubuntu 16.04 (or later version).
This is the machine I'm looking at.
[https://www.asus.com/us/Laptops/ASUS-VivoBook-S15-S510UQ/](https://www.asus.com/us/Laptops/ASUS-VivoBook-S15-S510UQ/)

Haven't found any information online for Ubuntu compatibility with it. If anyone's used it and has feedback, I would be grateful if you could share.

---

### Post by tebugst on 2017-11-19
Hay, did you find out ? I am also looking to buy same model. Please update if you able to run ubuntu on asus vivobook s15

---

### Post by Vradi_dm on 2017-11-30
Hy guys! I'm running ubuntu 16.04 on this machine right now. The only problems I experienced are: the function keys and the key lights not functioning.

---

### Post by tebugst on 2017-12-02
cool. did you check this link - [https://askubuntu.com/questions/644410/cannot-turn-on-keyboard-backlight](https://askubuntu.com/questions/644410/cannot-turn-on-keyboard-backlight) ? 
May be try linux-mint 18. It comes with good pre-configuration imo

also try - [https://askubuntu.com/questions/866437/function-keys-do-not-work-brightness-sound-ubuntu-16-04](https://askubuntu.com/questions/866437/function-keys-do-not-work-brightness-sound-ubuntu-16-04)

bdw how's d machine ?

---

### Post by Vradi_dm on 2017-12-09
> **tebugst said:**
> cool. did you check this link - [https://askubuntu.com/questions/644410/cannot-turn-on-keyboard-backlight](https://askubuntu.com/questions/644410/cannot-turn-on-keyboard-backlight) ? 
May be try linux-mint 18. It comes with good pre-configuration imo

also try - [https://askubuntu.com/questions/866437/function-keys-do-not-work-brightness-sound-ubuntu-16-04](https://askubuntu.com/questions/866437/function-keys-do-not-work-brightness-sound-ubuntu-16-04)

bdw how's d machine ?

Thank you very mutch for your help! The solution for they keyboard lights problem worked fine!

I don't understand clearly your question (probalbly because I'm new on ubuntu forums)but if You wanted to ask how this machine performs with Ubuntu 16.04, the answer is:I mainly use this machine for raw picture processing with darktable and I'm pleased with the performance of it. 
If You have concrete questions about this feel free to ask theme here and I will try to answer You :)

---

### Post by tebugst on 2017-12-09
ok thanks. can you please tell me how you fixed keyboard light issue ?

---

### Post by tebugst on 2017-12-10
Also you might need to fix graphics card drivers. Are you able to run propitiatory nvidia drivers or opensource nouveau drivers? Graphics might drain battery as both will start on boot ( external and internal ). May be best option for now is disable external grahpics for linux unless you not using. IDK.

---

### Post by JD82 on 2017-12-24
Just installed Ubuntu 16.04 on an S15 X510UQR (i5-8250U), after the installation the VGA and Wifi were not working. I manually installed the latest kernel (4.14.8) from the mainstream ppa and the Intel [kbl-guc and bxt-guc]("https://01.org/linuxgraphics/downloads/firmware") since I got a [working for missing firmware]("https://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings") and both started working fine. I've also installed the nvidia driver for the 940mx from the ppa graphic drivers.

The only thing that is not working is the fingerprint reader. And I found zero information on how to get it to work on linux. I don't even find it in lspci or lsusb.

---

### Post by staroldur on 2018-01-29
Sorry for a bit of a necro.
I'm interested in buying this model specifically for Ubuntu, and wanted to ask how many hours of battery life are owners of this model getting on Ubuntu?
Reviewers claim that this model has a so-so battery life, and since Ubuntu already depletes the battery faster than Windows (afaiu), I'm a bit worried, it'll be too short.
Thanks in advance :)

---

### Post by juanccorrea on 2018-03-03
I recently bought an Asus VivoBook s14 and wifi doesn't work. I need help....

---

### Post by oldfred on 2018-03-03
@juanccorrea
Best to start your own thread in the Wireless sub-forum.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)
And run the script suggested in the thread sticky.
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Then those that know wireless issues can help.

---

