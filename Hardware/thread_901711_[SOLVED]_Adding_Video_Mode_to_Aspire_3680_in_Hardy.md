---
title: "[SOLVED] Adding Video Mode to Aspire 3680 in Hardy Heron"
date: 2008-08-26
forum: Hardware
---

### Post by N00bB00b on 2008-08-26
I see from previous versions that somebody used 915resolution to add a 1280x800 resolution for this laptop.  However that isn't available with HH, so how would I add 24-bit 1280x800 for this bugger?  1024x768 looks really stupid, especially in FF on this box.

TIA

---

### Post by N00bB00b on 2008-08-27
After continuing to search (a day of that before finding the solution), here's the answer:

[http://ubuntuforums.org/showthread.php?t=636252&highlight=aspire+3680+resolution](http://ubuntuforums.org/showthread.php?t=636252&highlight=aspire+3680+resolution)

there is a great wiki-page about resolutions here [https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)

if you want a quick fix though, then write this down (don't do it, write it and then do it as the first command will take the X away from you )

1. ctrl+alt+F2
2. log in using your user name and password (the password will be invisible, just type it and hit enter)
3. type: "sudo /etc/init.d/gdm stop" +enter, it will ask for password... insert it and enter
4. type: "sudo dpkg-reconfigure xserver-xorg" enter
5. follow the questions, choose the default answers when not sure (use tab and arrow keys to move around, space to select many objects etc)
6. the important part is when the screen resolution is asked, choose the ones you want to use, use space key to select them
7. after all is finished type "sudo /etc/init.d/gdm start" +enter

---

