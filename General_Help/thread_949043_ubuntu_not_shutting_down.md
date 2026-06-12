---
title: "ubuntu not shutting down"
date: 2008-10-15
forum: General Help
---

### Post by Stargazer989 on 2008-10-15
first i started up mIRC and i saw that it said "27 days left" ... this only happens on fresh installs. next i tried a restart. everything locked up. i had to go into CLI mode and shutdown from there. everything came back up after that. but then i tried a shutdown from System > Quit - Restart. **then** my machine shutdown but i was left at the splash screen with some fans in my machines still running. 

any ideas as to what's wrong ? i really need to get this thing to shutdown properly.

---

### Post by Mister.Vash on 2008-10-16
You might need to pass the kernel the reboot=b option, which tells the machine to use the bios to do the restart.  

See this thread for details on adding it.  [http://ubuntuforums.org/showthread.php?t=839511](http://ubuntuforums.org/showthread.php?t=839511)

---

### Post by Yellow Pasque on 2008-10-16
My suggestion (if the above doesn't work) would be to temporarily remove the splash screen so you can see what is causing the lockup. You can do this by removing the splash keyword from your kernel boot line
> 
1.Press Esc during Grub boot delay to access the boot menu.
2.Select your actual Ubuntu boot line and press "e" to edit it.
3.Select the "kernel" line and press "e" to edit it.
4.At the end of the line, remove "splash" and "quiet" and press "enter".
5.Type "b" to boot the custom boot line.
Quote source: [https://wiki.ubuntu.com/Bugs/Responses#Freeze%20during%20boot%20or%20shutdown%20screen](https://wiki.ubuntu.com/Bugs/Responses#Freeze%20during%20boot%20or%20shutdown%20screen)

---

