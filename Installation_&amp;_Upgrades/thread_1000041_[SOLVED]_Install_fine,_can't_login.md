---
title: "[SOLVED] Install fine, can't login"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by vegetablestu on 2008-12-02
right i have used ubuntu in college (i tried asking my teacher he couldn't help lol)and i loved it. My teacher burnt off a disc (version 8.04)i tried installing it on my pc because i thought it would be perfect as windows is so annoying on it. 

i deleted windows and installed ubuntu, everything was fine i installed it to the hard drive, created a username and password, then rebooted (this is where the problem comes in). The ubuntu logo comes up, then i get the login screen, i type the username and password in, the login part goes away i just get the orange screen, then the login comes back without a error message. The username and password is correct but i just get this loop.
the pc spec:
motherboard msi - MS-7184
chipset - ATI Radeon XPress 200
AMD processor Sempron 3000+ 1.8 GHz
DDRI 512mb ram
80 gb hard drive

any advice will be great

---

### Post by lemming465 on 2008-12-03
Use Ctrl-Alt-F1 to switch to a text console, and try a command line login.  If you get in, do *less /var/log/Xorg.0.log* and *less /var/log/messages* and see if you have any complaints about something.

If you don't get in, the password is probably wrong.  At the grub boot prompt type "e" for edit, arrow down to the kernel line, type "e" again, append "single" as an argument, press enter to exit edit mode, type "b" to boot.  The system should come up single user running a bash shell on tty1 without prompting for a password.  Use a command of the form *passwd YourUserName* to reset your user account password.  Press Ctrl-D or type "exit" to resume the multiuser boot.

Or just reinstall.

---

### Post by vegetablestu on 2008-12-04
ok i set the session for failsafe_GNOME and i logged in, but i still can't login normally by typing the username and password(comfirmed and correct). I really want this to work so any more advice would be great.
 
thanks lemmings for your reply, time and effort

---

### Post by rokytnji on 2008-12-04
I had this problem once after a install. I found that the user default name was     admin       and I forget whether I used admin or the word root for password, and then it would log me in.

---

### Post by rokytnji on 2008-12-04
If you can log in here are the commands used in terminal for changing password and group.

[http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal](http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal)

---

### Post by vegetablestu on 2008-12-05
thanks rokytnji for your responce, but the username and login are correct as i had to put my username and password to load into te 'failsafe_gnome'. But thanks to your link i decided to add a username, but that wouldn't login.

When i put my username and password in, it does look like its going to load because the login screen disappears and i get the orange screen but it goes back to the login screen. i even changed the resolution in the 'failsafe_gnome', now when i login normally resolution changes at the orange screen before it goes back to the login screen.

---

### Post by littlebat on 2008-12-05
Try login with rescue mode and select the item like "fix xorg-xserver".

Try login with rescue mode (single), you will login with root account, then type "startx" to see if you can login into a graphic desktop.

Try google your display card to see if it need special driver.

---

### Post by littlebat on 2008-12-05
Hi, I just found a link may be helpful for you:
ATI Radeon Xpress 200
[https://answers.launchpad.net/ubuntu/+question/26538](https://answers.launchpad.net/ubuntu/+question/26538)

---

### Post by vegetablestu on 2008-12-05
i am very sorry but i don't think i know what to do, i have read everything in that link but i am unsure on what to do and choose.
i think that this could be the problem that i am having. but i don't know how to install the drivers.

---

### Post by littlebat on 2008-12-05
Try open source driver:
login with rescue mode, under command line, type "nano /etc/X11/xorg.conf",
Check "Device" section in "/etc/X11/xorg.conf", try change the Driver to "radeon" or "ati". save the file then type "startx" to verify if it works.

Try closed-source driver, two ways ( [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ), but, I read that " 
The 'fglrx' driver does not support cards earlier than the 9500", I don't know if xpress 200 is earlier than the 9500. So, I first recommend you to download the driver from offical web site, the page is: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html), for your 64bit cpu, it is "Linux x86_64 -> Integrated/Motherborad -> Radeon Xpress 200". 

Post your "/etc/X11/xorg.conf" and "/var/log/Xorg.0.log" here. And post the output of "lspci -nn | grep VGA"

Here is a link you can read: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by vegetablestu on 2008-12-05
ok everything is working, after i put a 8800GT 1GB ram graphics card in it, lmao haha. well the graphics through the onboard card were awful, unforunatly the graphics card will be put back into my other computer. But i would like to thank all the responces as they led me to success!

---

### Post by vegetablestu on 2008-12-06
> **vegetablestu said:**
> right i have used ubuntu in college (i tried asking my teacher he couldn't help lol)and i loved it. My teacher burnt off a disc (version 8.04)i tried installing it on my pc because i thought it would be perfect as windows is so annoying on it. 

i deleted windows and installed ubuntu, everything was fine i installed it to the hard drive, created a username and password, then rebooted (this is where the problem comes in). The ubuntu logo comes up, then i get the login screen, i type the username and password in, the login part goes away i just get the orange screen, then the login comes back without a error message. The username and password is correct but i just get this loop.
the pc spec:
motherboard msi - MS-7184
chipset - ATI Radeon XPress 200
AMD processor Sempron 3000+ 1.8 GHz
DDRI 512mb ram
80 gb hard drive

any advice will be great
anyone with this problem i recommend you get a basic cheap graphics card like i have, you can get a basic one in the uk for £10-15 on ebay

---

