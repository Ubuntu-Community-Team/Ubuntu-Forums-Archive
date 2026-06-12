---
title: "blank/black screen on logon"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by gautamz on 2007-06-13
My system specification - P4 2.4GHz on a 845G intel mb with integrated graphics. I have 40GB hard disk and still using an old 14" monitor. I have WinXP and Ubuntu installed in dual boot mode. 
This is my first experiment with Linux.

I am using the Ubuntu 6.1 DVD. When I boot off the DVD I get a black screen. I can hear a sound play indicating Ubuntu has logged in to the desktop successfully. But my screen shows nothing.

I used the text based install option hoping the installed version would work. And it works - sort of.
Directly trying to get to the Ubuntu logon screen gets me a blank screen. Though I do hear sounds playing that indicate the screen should be up there fine.

I fiddled with reconfiguring the Xserver options. And that didn't help - till I discovered the following.
If instead of choosing the default Ubuntu option in Grub I chose the Ubuntu recovery mode option I would get a terminal. Doing nothing except typing "exit" gets me to the login screen and I can see Ubuntu in all its glory. I am then able to login and play around with it fine. I was even able to reconfigure Xserver to give me multiple resolution options against the initial default and only option of 640x480.

Being new to Linux and Ubuntu I am unable to figure out why the system is not able to directly show me the login screen and needs to go the terminal way.
Is there some boot options I can try out to bypass going into Ubuntu through the terminal?

---

