---
title: "proble with WLAN button"
date: 2008-09-23
forum: Hardware
---

### Post by shazy on 2008-09-23
hi, i used to use windows vista on my laptop (compaq presario). 2 or 3 weeks i uninstalled windows vista and installed Ubuntu in my laptop. now since i have installed Ubuntu, the WLAN button does not work. when i used to use vista the button used to work very well, the blue light used to switch on whenever i pressed the WLAN button but now no matter how much i press the button there is no blue light nor is there any internet connection detected. please help. all the help will be very much appreciated. i am soooo worried!! thanking you...

---

### Post by Vakman on 2008-09-25
What wireless card do you have in it. And do not expect the button to work. You can still have wireless though, do not worry. Since it is a Compaq, I am going to assume that you have Atheros. 
[http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)
That is a link, in that link is a single post, scroll down to the direct download section and download a .deb package that suits your laptop. Then once it is installed, go into etc/modules and add a line that says 
> ath9k
Now only do this assuming you have an Atheros wireless card. When you are back online you can tell me what you have.

---

