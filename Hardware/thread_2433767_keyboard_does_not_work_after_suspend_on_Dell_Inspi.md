---
title: "keyboard does not work after suspend on Dell Inspiron 15 7000 series"
date: 2019-12-25
forum: Hardware
---

### Post by k1rtqmfki on 2019-12-25
Hi Guys, 

I  have successfully escaped from windows chains and been using ubuntu for quite some time now fairly successfully on my PC. I got a the laptop from the header as a present from a relative. It is all 2 in 1 laptop with touch screen and stuff like that. It comes with win10 out of the box, but of course I wanted to use linux. Ubuntu works fine, but when I suspend the laptop with closing the lid it goes to sleep. When I open it it wakes up, but keyboard is not responding, therefore I cannot enter password with keyboard. I can log in with the touch screen without any problems, but I need to reboot in order to use the keyboard, which is annoying. 

I have tried the most common solutions from the net, but without any success. 

This annoying situation forces me to use the disgusting win 10 whenever I want to use the laptop. 


Please let me know what info I need to post so you, educated fellas, can provide some help. I really, really want to delete the windows. :)

Ubuntu 18.04.3 LTS

---

### Post by CelticWarrior on 2019-12-25
If it's one of those with a detachable screen you may try detaching and reattaching. Please note that even if this works it's nothing more than a lazy workaround. The root cause is some power saving setting that affects some devices when waking up from suspension. That can and should be corrected but I'm not the person to show you how.

---

### Post by k1rtqmfki on 2019-12-25
The laptop is not detachable. It just has touch screen, which btw is supposed to work on win 10 and does not have drivers for my preferred 7 (back then when I used it), but UBUNTU works out of the box. :D 

I kinda found a workaround. It still is an annoying one, but less  annoying than restarting. Here is how it goes. There are 2 options.

option 1 : instead of closing the lid directly, i set the power button  to act as SUSPEND, so I hit it first and then close the lid. Keyboard  works just fine. 

option 2: if I closed the lid by accident, the keyboard would not work  on reopening. Therefore I need to close the lid and open it immediately.  Then keyboard works.

Both of these sound a bit stupid, especially the second one, but I do  not have the knowledge to investigate it further... unfortunately.

---

### Post by CelticWarrior on 2019-12-25
Even if it works as expected in Windows 10, I would check for and update UEFI if available.

Off-topic PS - No modern hardware works with Windows 7 and that Windows is as good as dead with just a few days of support left. It shouldn't be used under no circumstance past January 2020.

---

