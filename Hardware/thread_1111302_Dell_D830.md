---
title: "Dell D830"
date: 2009-03-30
forum: Hardware
---

### Post by u.2 on 2009-03-30
Hi,
I am making the big switch and I am not entirely new to linux but never used it day in/out on my primary machine and haven't done a ton.

I have a few issues and I Haven't gotten any replies in the other forums on how to fix them entirely. SO here goes.

I have a Dell D830 laptop - 4gb ram - should I use the 32 or 64bit version of Ubuntu? I am using 32 now but plan to host VM systems on it using vmworkstation or virtual box.

SO far my main issues are:
1. NIC Settings don't stay - I setup a static IP config and it stays there but every reboot I get a new connection for "auto" and it defaults to that. Then the original DHCP connection it makes also is there even though I deleted that. "Done all this via the gui" in the panel tray.

2. Dual monitors - the resolution on my laptop even without dual is not right, it should be in the 1400's but it is at 1024x768 and I can't pick bigger?
Then my dual monitor settings, once I dock my laptop in the morning and power it up, I can't login because my primary screen goes to my main monitor but nothing shows up, and I end up hard powering off. I found the fix is to shut off the external monitor but there must be an easier way then shutting that off each time I dock it?

3. RDP client - HELP - I have to manage windows servers. I am using the built in Terminal Server Client on ubuntu and if I don't immediately "Grab" the window when it goes to open to a server and move it to the middle of the screen then I can't use my mouse on either screen and the keyboard stays locked in the RDP screen, so I tab around to log out and then try to catch the window and move it somewhere else on the screen once it starts opening.

4. How to run these gui apps as sudo? Is that my problem?

5. How come ubuntu doesn't prompt for root permissions like the other linux distro's I have tried and how do I get my settings to stay and ensure I get the right file permissions when I creat files?

6. How do I run the gui apps for system settings to that my settings save to the right place?

7. Should I try version 9.0.4 since it is supposed to fix some bugs?

8. How do I rescan or update my video card driver?

---

### Post by kgr132 on 2009-05-16
Not that I have any specific answers to your questions, but I installed Ubuntu 9.04, 64-bit version a couple of weeks ago and it works flawlessly on my D830. The only thing I had to do was go into System...Administration...Hardware Drivers and enable the Nvidia (ver. 180) and the Broadcom Wireless drivers. No other workarounds, patches, etc like with previous versions of Ubuntu. Amazingly, it all just worked. Even my Sprint wireless USB card is handled by Network Manager. Also, the D830 has no problem booting from and external USB drive. So if you want to take Ubuntu for a test drive, I recommend installing it on an external drive. It works almost as if it's on the internal drive, just a hair slower with drive intensive operations. Good Luck.

---

