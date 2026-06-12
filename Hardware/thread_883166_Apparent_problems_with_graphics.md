---
title: "Apparent problems with graphics"
date: 2008-08-07
forum: Hardware
---

### Post by Melindrea on 2008-08-07
I've installed Xubuntu on my grandmother's laptop (an old one that my mother used to have), but I've found two big problems:

(right, mouse seems to have fixed itself with the latest upgrade... If I need help with it later, I'll post another question!)

2) After I've logged in, the graphics work. However, there seems to be a problem that right as I'm logging in, the graphics card can't be recognized, or somesuch. Basically, the colours are all screwed up where I type in the username and password.

I'm not sure exactly how to check what her graphics card is, since I don't know my way around Ubuntu like I do Windows.

Also, is there a setting to setup that so that it shows the password with stars? I thought it did on my Ubuntu, but it doesn't on the Xubuntu. I can live without seeing the password, but this is my computer illiterate grandmother we're talking about... =)

Thank you,
Melindrea

---

### Post by phidia on 2008-08-07
From the Ubuntu wiki [here]("https://help.ubuntu.com/community/Video") 
> lspci | grep VGA that will tell you what card is in the laptop.

Added: I should have said open a terminal from Applications > Accessories > Terminal and then copy and paste the command I quoted into the terminal.

Consult the link for more info on setting it up or post back here with questions.

---

### Post by Melindrea on 2008-08-08
I'm not :that: Linux illiterate, I do know how to use the terminal. 

The card is a Silicon Motion, Inc. SM720 Lynx3DM. 

What was it I should look at the wiki to find? The problem is right before logging in, once I've logged into Xubuntu there is no problem with the graphics. Right before I log in, the colours flimmer and are completelly screwed up.

---

### Post by phidia on 2008-08-08
Searching your video card produced a lot of [graphics problems]("http://www.google.com/custom?q=Silicon%20Motion,%20Inc.%20SM720%20Lynx3DM&client=pub-7828731768650352&forid=1&ie=utf-8&oe=utf-8") with linux.

You can try the terminal and entering this > sudo dpkg-reconfigure -phigh xserver-xorg If you can not login graphically at all you can open a commandline interface (CLI) by pressing the Ctrl+Alt+F1 (F2-F7 also).
If that doesn't work for you post your /etc/X11/xorg.conf .

---

