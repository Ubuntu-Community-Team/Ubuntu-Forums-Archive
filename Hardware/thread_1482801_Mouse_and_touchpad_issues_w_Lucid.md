---
title: "Mouse and touchpad issues w/ Lucid"
date: 2010-05-14
forum: Hardware
---

### Post by npattillo on 2010-05-14
I have an ACER Aspire 5740 laptop. I have Lucid edition of Ubuntu installed on a dual boot w/ windows 7. I had no issues with the touch pad not working since I installed it and I could transition between using the touch pad and a small USB mouse easily. Now, at login, the touchpad works as it should. As soon as Ubuntu is loaded under my user name, it ceases to function and I have to use the USB mouse. Please instruct me on what I need to do. Please keep in mind with your replies that I am new to the Ubuntu community. Thanks so much for your help.

---

### Post by kommi on 2010-05-17
I have the same issue like you discribed on my Acer 5740g. Running lucid. The touchpad works on the login-screen. After loging in it stops working. Unfortunately I can`t help you. Searching for a solution, too.

---

### Post by kommi on 2010-05-17
I found a fix for this on [http://ubuntuforums.org/showthread.php?t=1465426](http://ubuntuforums.org/showthread.php?t=1465426)

Maybe this helps you, too.

Open a terminal and then the gconf-editor

```
gconf-editor
```Then look into /desktop/gnome/peripherals/touchpad if touchpad_enabled is set to true. If  not set it to true. 

Your touchpad should now work and you should be able to enable/disable it by the touchpad-key besides the touchpad.
At my notebook this change is permanent. It works even after reboot.

---

### Post by npattillo on 2010-06-10
Thanks. This works like a champ.:popcorn:

---

