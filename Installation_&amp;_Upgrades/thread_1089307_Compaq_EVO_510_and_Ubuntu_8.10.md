---
title: "Compaq EVO 510 and Ubuntu 8.10"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by ddvanrooy on 2009-03-07
Hi All

I have a funny trying to install Ubuntu 8.10 on a Compaq EVO 510. I think it might be a problem with graphics drivers. When running the live CD everything appears to be normal, and the installation also seems to go fine. However, when the machine restarts is when the fun starts. Initially it seems to boot ok and upon starting Ubuntu plays the little tune, but then the screen goes black with only the mouse pointer visible.

Does it uses a different graphics driver on the live CD than on the actual installation ? I tried also Ubuntu 8.04 and same thing. 

I also installed Windows XP SP 2 on the same machine and XP did not autodetect the graphics card, sound card and ethernet, all which I had to get the drivers from the Compaq website.

However I dont know how to do the same trick for Ubuntu.....

Any ideas welcome

Regards
D

---

### Post by ddvanrooy on 2009-03-07
tried it. is no good. I mean, it does boot, and I even get to login screen, but after login, it just goes to blank screen with only the mouse pointer......

any ideas ??

---

### Post by Dallywood on 2009-03-08
I had the same problem. 
When you boot from the ubuntu cd can you start ubuntu without installing it?
I have heard some various fixes for the problem such as trying to burn ubuntu on dvd instead of cd. 
I managed to get 8.04 to work on my compaq but I had to try out a few different brands of cds.
I have also heard that cds burned from and apple comp or a comp using am operating system other than windows seem to work better.

---

### Post by ddvanrooy on 2009-03-10
I have now managed to get these EVO 510's working using a package called "Super Ubuntu". It is supposed to be 8.10 with a few extras like Skype and Wine, but in theory it should be the same as the original 8.10.  What can I say ? It works.... I havent actually checked of the kernel versions are much different.

Anyway is not the end of the story: I got 2 of these EVO's for my kids to mess around with and wanted to load Edubuntu. I had everything nicely running on a EVO D300, using Ubuntu 8.10. But now on the D510's I first had this "graphic" problem, which was mysteriously fixed when I load "Super Ubuntu". However on this version , the complete Edubuntu desktop doesnt want to install - complaining about conflicting software - although I managed to get some bits and pieces working. It seems it never ends....

---

### Post by Neo_The_User on 2009-03-10
Boot up in safe graphics mode.

---

### Post by ddvanrooy on 2009-03-11
> **Dallywood said:**
> I had the same problem. 
When you boot from the ubuntu cd can you start ubuntu without installing it?
I have heard some various fixes for the problem such as trying to burn ubuntu on dvd instead of cd. 
I managed to get 8.04 to work on my compaq but I had to try out a few different brands of cds.
I have also heard that cds burned from and apple comp or a comp using am operating system other than windows seem to work better.

I must say that this sounds pretty much exactly what I had as well, and now that you mention it, I first thought is was a problem with the disks (CD's) themselves. The package which eventually worked was from a DVD disk....and it seemed as if the machine was having problem reading CD's, although the drive was DVD-Rom, and later it read CD's fine again.

---

### Post by ddvanrooy on 2009-03-11
> **Neo_The_User said:**
> Boot up in safe graphics mode.

How to do this ?? 

As I said earlier, I tried the "Alt-F1" and it boots in verbose mode;it then gets to the login screen - in graphics mode - and after login the screen dissapears, with only the mouse pointer left.

---

### Post by spook1980 on 2009-03-11
> **ddvanrooy said:**
> Hi All

I have a funny trying to install Ubuntu 8.10 on a Compaq EVO 510. I think it might be a problem with graphics drivers. When running the live CD everything appears to be normal, and the installation also seems to go fine. However, when the machine restarts is when the fun starts. Initially it seems to boot ok and upon starting Ubuntu plays the little tune, but then the screen goes black with only the mouse pointer visible.

Does it uses a different graphics driver on the live CD than on the actual installation ? I tried also Ubuntu 8.04 and same thing. 

I also installed Windows XP SP 2 on the same machine and XP did not autodetect the graphics card, sound card and ethernet, all which I had to get the drivers from the Compaq website.

However I dont know how to do the same trick for Ubuntu.....

Any ideas welcome

Regards
D

got the same computer when i had 8.10 running before going back to 8.04
i had to do a complete shutdown then restarted the computer and everything was fine.

the Compaq evo 510 comes factory with an Intel extreme 2 on-board graphics which is fully supported in the Linux kernel.

---

### Post by JF_Sly on 2009-03-26
I am having the same issue.  I did try rebooting and it just keeps going to the same thing.  Where id you get the Super Ubuntu  From (URL)?

At the moment, to get around the issue, I cloned the drive of another D510 that is running Ubuntu 7.10 and was going to do an online upgrade to 8.1  if possible.

---

### Post by ddvanrooy on 2009-04-05
Hi

Ok the Super Ubuntu you can get here; hacktolive.org/su
I had all sorts of funnies with this Super Ubuntu and have gone back to standard 8.04 again, which so far works the best for me.

I'm normally running now on a Thinkpad R51 (8.04) but I have 3 other Ubuntu machines, Compaq D300 (which is fine on 8.10) and then the two D510's who are misbehaving.

However, something else : I found in this forum a possible fix and I have posted in another thread in reply to someone with a similar problem. It explains a problem with compiz. Just do an advanced search with my name and you'll see . It was about 2 weeks ago I think. I havent been able to try it myself since my two Evo's are on the other side of the planet. I'm curious to know if someone else could try and confirm if it works.

Cheers
DD

---

