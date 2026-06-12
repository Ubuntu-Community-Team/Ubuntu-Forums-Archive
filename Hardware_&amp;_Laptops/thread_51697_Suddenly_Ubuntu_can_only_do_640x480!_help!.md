---
title: "Suddenly Ubuntu can only do 640x480! help!"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by Kegwen on 2005-07-25
Alright, so I've been using Ubuntu for short while now and everything has been great besides the lack of 3d acceleration, but I've pretty much accepted that this is my fate due to my ATi card (The work required to get the drivers installed is rather intimidating) and moved on. Anyway, earlier today I noticed that there were some package updates, so I updated and went on with my business. A while after that I restarted to go into Windows, but I stepped away and forgot to choose the OS. It boots into Ubuntu, and the login screen is at this unholy resolution. I figured it was a fluke and rebooted in to Windows.

Here I am a few hours later. I was done with my business in Windows, so I rebooted. Lo and behold, I'm met with 640x480 again. I log in and go to Screen Resolution, and 640x480x60 is the only option. Arrrrgh.. I have no idea what happened or what to do about it. Please help :(

In case anyone needs to know, I'm running a Radeon 9800 Pro.

---

### Post by heimo on 2005-07-25
Hi!

Check [this]("http://www.ubuntuforums.org/showthread.php?t=21984&highlight=screen+resolution+howto") thread and this [message]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21"). What I'd do is run
 ```
sudo dpkg-reconfigure xserver-xorg

``` 
to make new Xorg.conf and watch the log file (see the posts in threads linked abowe) for errors during "startx" or when gdm starts.

Your xorg.conf file as attachment (please not inline) could help, and the log file for Xorg is very helpful too. Please post your findings and many people on this forum will be glad to help.

Cheers!

---

### Post by Kegwen on 2005-07-25
Running dpkg-reconfigure xserver-xorg re-enabled up to 1024x768, which was excellent. I perused the two topics you linked, and the second one had the answers I needed. All I had to do after the reconfigure was add the resolution to xorg.conf.

Thanks for the help. I appreciate it!

---

### Post by heimo on 2005-07-25
Great to hear it was solved easily. :) And by the way, welcome on this forum.

---

### Post by Kegwen on 2005-07-25
[QUOTE=heimo]Great to hear it was solved easily. :) And by the way, welcome on this forum.[/QUOTE]

Thanks! It seems like a great community.

---

