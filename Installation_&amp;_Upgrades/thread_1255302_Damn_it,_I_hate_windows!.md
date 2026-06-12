---
title: "Damn it, I hate windows!"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by bukueOner on 2009-09-01
I tried to install win xp after i installed ubuntu so i could play games like gta. Unfortunately i didn't know about the grub back then. So know all i get when i start up my pc is a message saying "error loading operating system". All i want to do is retrieve all the data from the the original ubuntu, but every time i do it says i don't have the right permissions. Does anyone know how to remove or change the permissions so i can copy the data from the original ubuntu using the live cd? Thanks.

---

### Post by DonaldJ on 2009-09-01
I hate windows too.. maybe More than you...

If I had your problem, and didn't get a response to my question in the forum, I'd run RemasterSys to make a copy of the hd, then open files in RS, and transfer them to CD or Flash-D...

Me thinks that when you fail to make a perfect backup before you starts foolin-around with installing OS's over OS's is just asking for troubles...
As a last resort, make a full backup that you can play with later...

---

### Post by bukueOner on 2009-09-01
*sigh*...19 views and no help. thank you ubuntu community, very helpful...

---

### Post by Bear Knuckle on 2009-09-01
> **bukueOner said:**
> *sigh*...19 views and no help. thank you ubuntu community, very helpful...

If no one answers, it's hardly because they don't want to, it's mostly because, the just can't.

I can't either, so is this helping you in any way?

But maybe this can help you: [http://www.lmgtfy.com/?q=permission+ubuntu+live+cd](http://www.lmgtfy.com/?q=permission+ubuntu+live+cd)

---

### Post by bedhead75 on 2009-09-01
From what I understand, if you installed XP after installing Ubuntu, then Grub will have been overwritten by XP and you'll have to reinstall it from the live CD.  It's actually a very simple thing to do, but I just can't remember exactly what to do off the top of my head.  Just google how to dual-boot Ubuntu and XP and you'll find plenty of online tutorials on how to do it, whether you install Ubuntu first and then XP, or vice versa.

---

### Post by denver on 2009-09-01
Assuming you did not clober your ubuntu and/or boot partition, you might find the posts in this thread usefull:

[http://ubuntuforums.org/showthread.php?t=1252251](http://ubuntuforums.org/showthread.php?t=1252251)

Good luck!

---

### Post by bukueOner on 2009-09-02
Ok, this is the 5th time i've tried to get help with this problem, so hopefully someone will respond with a descent answer this time and not just some vague description on how to fix the grub. 

The problem is that i installed win xp after i installed ubuntu. At the time i wasn't aware of the grub list, so you can guess what happened next. Now all i get when i start up my pc is a message saying "error loading operating system". 

All i want to do is retrieve all the data i copied onto ubuntu. It includes over 200 movies, 15,000 songs and a <snip> load of images, so losing this data would be a major piss off.

I'm using the live cd right now and everytime i try to copy the data to my external hard drive it comes up with some message saying i dont have the permissions to copy this data. Also there is a little "X" next to each folder, if that helps.

Now all I want to do is copy the data and reinstall ubuntu. 
I DO NOT WANT TO FIX THE GRUB!

Thanks in advance.

---

### Post by bukueOner on 2009-09-02
> **bedhead75 said:**
> From what I understand, if you installed XP after installing Ubuntu, then Grub will have been overwritten by XP and you'll have to reinstall it from the live CD.  It's actually a very simple thing to do, but I just can't remember exactly what to do off the top of my head.  Just google how to dual-boot Ubuntu and XP and you'll find plenty of online tutorials on how to do it, whether you install Ubuntu first and then XP, or vice versa.

Yeah, except that i said i needed to copy all my data. re-installing would loose my whole library of videos, pics and music. thanks anyway...

---

### Post by Soley on 2009-09-02
Load up a live disc. Mount both your ntfs (windows) and ext* (ubuntu) partitions.

You should be able to drag & drop your files from the Ubuntu partition to the Windows partition no problem.

Edit: Actually, your partitions may mount automatically. At least they did when I just tried a 9.04 disc on my wife's computer.

---

### Post by Grenage on 2009-09-02
This will sort you out, if you installed XP to a different partition then your ubuntu install will be ok:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by kerry_s on 2009-09-02
use the live cd to copy all your stuff off the drive, do you have anything big enough to hold it? how much videos, pics and music ya talking here?

---

### Post by megamania on 2009-09-02
> **bukueOner said:**
> 
I'm using the live cd right now and everytime i try to copy the data to my external hard drive it comes up with some message saying i dont have the permissions to copy this data. Also there is a little "X" next to each folder, if that helps.

From the live cd, try opening the terminal, then enter
```
gksudo nautilus

```
Check if you can copy from that window.

---

### Post by Soley on 2009-09-02
> **megamania said:**
> From the live cd, try opening the terminal, then enter
```
gksudo nautilus

```
Check if you can copy from that window.

Huh...don't know how I completely missed that line...

---

### Post by overdrank on 2009-09-02
Threads merged.

---

### Post by bukueOner on 2009-09-02
> **Grenage said:**
> This will sort you out, if you installed XP to a different partition then your ubuntu install will be ok:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)


OMFG! Finally someone gave me a good answer/link that finally fixed my problem. Thankyou grenage, ur a legend man.

---

### Post by Grenage on 2009-09-02
Glad it worked! :)

---

### Post by Bear Knuckle on 2009-09-03
Glad to see your problems solved.

Now that you're in such a good mood, maybe you wanna read this, as an introduction to the topic:

[http://support.microsoft.com/kb/555375/en-us/](http://support.microsoft.com/kb/555375/en-us/) (From our friends at Microsoft.)

and afterwards this:

[http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html) (Don't you miss the part about the subject headers!)

It will help you a lot in the future and saves you from frustration and anger!

---

### Post by presence1960 on 2009-09-03
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

