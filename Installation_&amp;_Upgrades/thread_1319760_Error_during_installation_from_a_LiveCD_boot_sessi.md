---
title: "Error during installation from a LiveCD boot session"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Mikko8 on 2009-11-08
I tried to install Ubuntu from a LiveCD but it produced an error during the installation process so now I am having 10.0GB less disk space. I assume I cannot see and access them because the error came during the installation process after booting from the LiveCD as it was not through Windows. 

In another boot from LiveCD I tried the disc checking which showed that I have error in one file (in that CD I assume).

So later I tried to recover those 10.0GB but I couldn't. I am also adding two pictures so you can see what I tried to do. 

In the first picture you can see the distribution of my HDD. 
[INDENT]sda1 - Windows XP
sda5 & sda6 - unfinished Ubuntu install
[/INDENT](In the first time of the installation (when I got the error) there were more options. I chose the one witch allowed with a slider to take some disk space from Windows XP to use for Ubuntu.)

I chose the second option (Specify partitions manually (advanced)). In the second picture you can see the situation after I deleted sda5 & sda6 contents with the option provided at bottom of the screen. That is why it tells 'free space'. Unfortunately I couldn't continue the installation because another error message popped up telling something that a root direction is not selected (and I couldn't find how to do that) nor I could save the free space settings. And of course I couldn't add the free space back to the space available to windows from witch I took it at the first installation. 

So what's bothering me is either how to put those 10.0GB back so I can use them again or how to install Ubuntu over those 10.0GB as I wanted in the first time. 


Regards
Mikus

---

### Post by Mikko8 on 2009-11-10
> **Mikko8 said:**
> I tried to install Ubuntu from a LiveCD but it produced an error during the installation process so now I am having 10.0GB less disk space. I assume I cannot see and access them because the error came during the installation process after booting from the LiveCD as it was not through Windows. 

In another boot from LiveCD I tried the disc checking which showed that I have error in one file (in that CD I assume).

So later I tried to recover those 10.0GB but I couldn't. I am also adding two pictures so you can see what I tried to do. 

In the first picture you can see the distribution of my HDD. [INDENT]sda1 - Windows XP
sda5 & sda6 - unfinished Ubuntu install
[/INDENT](In the first time of the installation (when I got the error) there were more options. I chose the one witch allowed with a slider to take some disk space from Windows XP to use for Ubuntu.)

I chose the second option (Specify partitions manually (advanced)). In the second picture you can see the situation after I deleted sda5 & sda6 contents with the option provided at bottom of the screen. That is why it tells 'free space'. Unfortunately I couldn't continue the installation because another error message popped up telling something that a root direction is not selected (and I couldn't find how to do that) nor I could save the free space settings. And of course I couldn't add the free space back to the space available to windows from witch I took it at the first installation. 

So what's bothering me is either how to put those 10.0GB back so I can use them again or how to install Ubuntu over those 10.0GB as I wanted in the first time. 


Regards
Mikus
I solved this with GParted application.

---

