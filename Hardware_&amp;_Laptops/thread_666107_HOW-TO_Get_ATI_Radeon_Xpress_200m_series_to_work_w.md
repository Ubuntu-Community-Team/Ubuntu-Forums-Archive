---
title: "HOW-TO Get ATI Radeon Xpress 200m series to work with DRI and Desktop effects"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by cannedmonkey on 2008-01-13
Now some people might say that this is not really a fix for the problem but you decide. If you want Desktop effects and DRI to work on the same computer with this graphics card. This is what i did.

P.S Sry in advance is this is hard to follow because this is my first post.

Now for the whole time i have used linux i can not find a way to fix this so that desktop effects and DRI work AT THE SAME TIME, but i have found a way for it to work in defferent sessions.

First step-  (for 32bit comps)

Download the fglrx driver for your card and install it, i downloaded the proprietary driver from the ATI site and used their installer, this is the link [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run")
To install i navigated to the folder i downloaded in through the terminal, which in my case was the desktop so in terminal i did "cd Desktop". After that i used this to run the installer "sudo bash ati-driver-installer-8.443.1-x86.x86_64.run" (you might need to change this based on installer version and if you dont have a 32bit comp). Follow the installer then restart, (just as a side note you may want to edit your xorg by doing "sudo gedit /etc/X11/xorg.conf" and put this in if it is not in already, you may not need to do this) 

Section "Extensions"
        Option  "Composite" "Disable"
EndSection 




Second step-

After restarting you should boot up and if you have compiz (which is what i use) or beryl you should be haveing your desktop effects working. So congrats give yourself a pat on the back. But you may notice that if you put "glxinfo | grep rendering" (which is used to check if direct rendering is working) you will get a no. DO NOT WORRY this is what is supposed to happen. Now logout or use Ctrl+Alt+BACKSPACE. At the bottom left of your login screen you should see options so go ahead and click on that. Now click on change session and for this session you will want to use FAILSAFE GNOME. go ahead and login.

Third step-

After you login you may noice that ATI Catalyst Control Center now works when it hasent before in your regular login, and that if you put "glxinfo | grep rendering" in your console you get yes. But although you now have DRI and can play games like CSS (which you can and i do) you have the loss of Desktop effects for THIS session. But do not worry, if you want to showoff your cool desktop effects to your friends just Ctrl+Alt+Backspace out and do a regular login for your desktop effects.

SO REMEMBER

Desktop Effect= Normal session

DRI= Failsafe Gnome session 

Yes this is not really a fix for the problem i guess, but it does work so if you like this solution and it works then good im happy to help. i did not see this workaround anywhere else and i randomly stumbled upon this when i logged into failsafe the other day.

If you have any questions just comment them or email me ill try to check this topic regularly and for once check my email.

---

