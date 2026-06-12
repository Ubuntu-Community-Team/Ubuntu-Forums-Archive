---
title: "Problem with External Monitor on Laptop"
date: 2008-06-25
forum: Hardware
---

### Post by OscarG on 2008-06-25
I am a Ubuntu N00b, which has recently converted from a 10+ years of experience in Windoze-Pain and have found a couple of problems related to the use of external monitors on my laptop. 

1) I have a problem with the external screen which is use with my laptop. Sometimes, it comes up blank upon getting to the login-screen. It appears to be quite random; if I do a *hard-reboot* by hitting the power button - sometimes it works again, and sometimes it shows the login-in screen and works perfect on the first try.

2) Is there anyway to turn off the laptop screen automatically, so that it only displays on the external monitor when plugged-in?

Does anyone have any similar problems, and a fix which can make the laptop always recognize the external monitor as the primary, when plugged in?

My system is:
Ubuntu 8.04
Acer laptop with Intel Core2Duo T7300
14,1" Monitor and Samsung Syncmaster 940BW External monitor
2GB Ram
Intel X3100 Gfx

---

### Post by NilsE on 2008-06-25
I never noticed that as a problem for me since I either leave the lid closed when I want just the external.  If I need 2 displays I just leave the lid open and I get both.

I assume you have done some tinkering with 

System > Preferences > Screen resolution 

to make sure it is detecting both displays correctly.

---

### Post by OscarG on 2008-06-30
Thx for the reply NilsE!

I usually just close the lid on my laptop as well; the auto-shutdown feature does not work in Ubuntu! :-)

However, I still have the annoying problem with the system not always detecting my external monitor! I have messed a bit around with the screen resolution settings - so when the monitor is actually detected, it works quite nicely. The problem is, that during startup the monitor is not always detected, or it is - but just as the log-on menu appears the external screen just displays black - it does not turn off, but simply displays "nothing". The error is periodic, so I am a bit puzzled. 

Maybe someone has experienced similar problems?

---

### Post by pwcabach on 2008-07-16
Which video chip do you have? 

If you are using nVidia, there is a setting in the application "nvidia-settings" that allows you to make the external monitor your primary display for your X screen. If the external is detected at boot time, it should always come up.

&

---

### Post by OscarG on 2008-07-16
Hi and thx for your reply!

I am using the very standard Intel X3100 on-board - so unfortunately I do not have that option. :-(

---

