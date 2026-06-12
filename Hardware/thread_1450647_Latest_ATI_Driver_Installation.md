---
title: "Latest ATI Driver Installation"
date: 2010-04-09
forum: Hardware
---

### Post by jsp21c on 2010-04-09
Hi, I'm currently running Mint Helena x64 and plan to install Ubuntu 10.04 when it is realeased, my main reason for seeking better video drivers was for viewing text in the Firefox browser. The Mint drivers left the text looking somehow coarse and it hurt my eyes after a while.
I'd Googled the subject of ATI driver installation and read several articles but nothing worked for me, I used the admin/harware drivers section and installed the suggested option from there but it left a watermark on the screen saying" ATI Unsupported Hardware". I tried to follow the instructions from the ATI site but couldn't get the installer to run.
Finally I found a method which worked for me, my main problem was that I'd got the drivers from ATI but couldn't get them to install until using the method below.
I decided to write it up to help others who may have the same problem.

&#65279;ATI Driver Installation.

1.Download linux drivers from ATI. The version currently for my ATI 5770 video card on a 64 bit system is "ati-driver-installer-10-3-x86.x86_64.run". You will need to select drivers appropriate for your system.

2.Right click driver installer file and select Permissions then click &#8220;Allow executing file as program.&#8221; Close tab.
3.Open terminal. Type sudo then drag the ATI installation file from the download folder and drop it into the terminal window.
4.Press Enter.
5.Installation should start.
6.Choose options
7.Reboot. In the menu/preferences you will see the Catalyst Control Centre

If the installer doesn't run, type sudo and manually copy the location of the installer file from the lines above. Dragging and Dropping the file into the terminal worked once for me but not a second time on a fresh install of Mint. The quote marks around the file are the problem but typing a new line manually without the quote marks solved it for me.

---

