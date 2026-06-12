---
title: "Logitech Quickcam for Notebooks Pro"
date: 2010-03-24
forum: Hardware
---

### Post by chandler220 on 2010-03-24
I am using ASUS Eee PC 901 with Ubuntu 9.10 Netbook Remix.
I am a rookie of Ubuntu and Linux.
I used Ubuntu since last November, I found it very cool and fast and stable.
But lately I am facing a problem of my Eee PC 901 internal webcam,
it goes black and white once day and the color never come back.

Before I take my EeePC to fix, I would like to try my existing Webcam which I used to use on WinXP, Logitech Quickcam for Notebooks Pro
[http://www.amazon.com/Logitech-Quickcam-for-Notebooks-Pro/dp/B000BBYH8O/ref=dp_cp_ob_e_title_2]("http://www.amazon.com/Logitech-Quickcam-for-Notebooks-Pro/dp/B000BBYH8O/ref=dp_cp_ob_e_title_2")

Can anyone tell me can I use this Qucikcam on my Eeepc? And if yes can someone teach me how to install the driver so that I can use it in my Ubuntu 9.10 Netbook Remix environment.

Since I am a rookie of Linux, if someone can teach me how to do this with step by step it will be very grateful.

---

### Post by byStanderone on 2010-03-24
...go thru this thread, deals a lot about webcam, good luck:
[http://ubuntuforums.org/showthread.php?t=1436708](http://ubuntuforums.org/showthread.php?t=1436708)

---

### Post by chandler220 on 2010-03-24
Thank you byStanderone, but I really hope someone can teach me Step by Step, actually I read that thread before but I really don't understand what they are talking about.

---

### Post by byStanderone on 2010-03-24
...you can start by plugging your cam into the usb port, and post a feedback.

---

### Post by chandler220 on 2010-03-25
I am sorry, I am really a rookie, I did plugin to the usb port, but nothing happened. And the Cheese and Skype still only identify the internal camera, it didn't recognize my Logitech Quickcam for Notebook Pro.

---

### Post by byStanderone on 2010-03-25
...you got to have a webcam application so as to handle your webcam, try installing cheese.

---

### Post by byStanderone on 2010-03-25
...someone with a 9.10 netbook remix webcam experience?

---

### Post by mrpaulin on 2010-06-01
Plug the camera. In a terminal type "sudo rmmod uvcvideo" (without the quotes;you need to type your password); this will remove the driver of your camera. Now type "sudo modprobe uvcvideo" (whithout the ";type again your password); this will reload the driver and your camera should work fine. If this works for you try to figure out how to make this happen each time you start ubuntu.

---

