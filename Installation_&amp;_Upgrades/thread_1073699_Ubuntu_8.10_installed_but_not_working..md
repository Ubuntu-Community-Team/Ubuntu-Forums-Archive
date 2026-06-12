---
title: "Ubuntu 8.10 installed but not working."
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by sthrnpagan on 2009-02-18
well, I have Ubuntu installed but last night when i tried to boot into it after it did the whole check installation and all, it went to a black screen and nothing came up, then this morning as i tried to boot Ubuntu I am getting command line stuff. I think that something is wrong. Anyone know how to fix?  Thanks

---

### Post by jrandolph on 2009-02-18
bump for this guy because i cant help

---

### Post by avtolle on 2009-02-18
How did you install? The "check installation" thing makes me think you did an install "inside Windows" using Wubi.

EDIT: If you indeed installed with Wubi, one thought; uninstall, then defragment the drive, and then try to reinstall. If you instead installed Ubuntu to a dedicated partition, then disregard.

---

### Post by avtolle on 2009-02-18
One more thought; what graphics card do you have for the computer?

---

### Post by sthrnpagan on 2009-02-18
> **avtolle said:**
> How did you install? The "check installation" thing makes me think you did an install "inside Windows" using Wubi.

EDIT: If you indeed installed with Wubi, one thought; uninstall, then defragment the drive, and then try to reinstall. If you instead installed Ubuntu to a dedicated partition, then disregard.

i did use wubi, i used it because Unetbootin did not work. HOw would i uninstall Ubuntu?

---

### Post by sthrnpagan on 2009-02-18
i really want to use Ubuntu, but I am coming to the realization that I may have to settle for another distro like Fedora. If this is the case any recommendadtions?

---

### Post by sthrnpagan on 2009-02-18
> **avtolle said:**
> One more thought; what graphics card do you have for the computer?

how would I find this information?

---

### Post by sthrnpagan on 2009-02-18
I installed Ubuntu 8.10 and the installation with Wubi went fine. When the Ubuntu login page comes up, I enter my username and password for the first time and then it goes to a black screen with my cursor sitting in the middle of the screen. I stayed like that for more than an hour before I just restarted back  into windows. I would like to get rid of windows permanently and use Ubuntu, I have been trying for 2 days to get this to work. Can someone please help me:(

---

### Post by Therion on 2009-02-18
I'm not a big fan of Wubi, personally.  I'd suggest you download a LiveCD or DVD and boot to that for a test-drive.  If all goes well and you want to install Ubuntu you can do so using the LiveCD or DVD.  If you want to dual-boot Ubuntu alongside your Windows install, you can do that too, but post back here first so you can get some direction on how to do that.

---

### Post by sthrnpagan on 2009-02-18
> **Therion said:**
> I'm not a big fan of Wubi, personally.  I'd suggest you download a LiveCD or DVD and boot to that for a test-drive.  If all goes well and you want to install Ubuntu you can do so using the LiveCD or DVD.  If you want to dual-boot Ubuntu alongside your Windows install, you can do that too, but post back here first so you can get some direction on how to do that.

i would use a live CD or DVD but i do not have a Cd reader on my computer. Have heard of others successfully attepmting to install without CD like I am. I am at my wits end here.

---

### Post by halitech on 2009-02-18
open a terminal and post the output of
```
lspci
```and ```
lshw -C video
```

---

### Post by Therion on 2009-02-18
> **sthrnpagan said:**
> i would use a live CD or DVD but i do not have a Cd reader on my computer. Have heard of others successfully attepmting to install without CD like I am. I am at my wits end here.
S'allright... We'll see if we can't get you through this.  No CD drive, eh?  
What about a USB thumb-drive or flash-drive or jump-drive... Whatever kids are calling them today.  Got one of those?

---

### Post by insineratehymn on 2009-02-18
I bet the problem is with compiz. Leave it as it is, press cntrl+alt+f1 once you get to the login screen (do not log in there). That will bring you to a terminal. Log in with your user name and password and then type: > sudo apt-get remove compiz compiz-core
Then press cntrl+alt+f7, that will bring you back to the gui login screen. Press cntrl+alt+backspace to restart the xserver. Try logging in then.

---

### Post by cariboo on 2009-02-18
When you get a black screen after login, there are two possibles causes, your monitor is not being detected properly, or updates weren't completed. Since this is a new installation the update problem shouldn't count.

Start in recovery mode and at the menu screen select xfix from the menu. Once xfix is finished select resume and continue on to the desktop. Once at the desktop install all the updates, as there is a fix for your problem in the updates.

Once you have completed the upgrades you will be asked to rebot, after the reboot, go to System-->ADministration-->Hardware Drivers and activate the restricted video drivers.

Jim

---

### Post by sthrnpagan on 2009-02-18
> **insineratehymn said:**
> I bet the problem is with compiz. Leave it as it is, press cntrl+alt+f1 once you get to the login screen (do not log in there). That will bring you to a terminal. Log in with your user name and password and then type: 
Then press cntrl+alt+f7, that will bring you back to the gui login screen. Press cntrl+alt+backspace to restart the xserver. Try logging in then.

I will try that. Thanks, I'll let you know how it goes.

---

### Post by sydbat on 2009-02-18
This is off the top of my head for XP, as I no longer have Windows on my computers. However...

To uninstall a wubi installation, boot into Windows, go toStart > Control Panel > Add/remove programs and uninstall it from there.

Also, while in Windows, you can check what your video card is by right clicking on the desktop and choosing properties. This should bring up a window that has the configuration stuff (like setting desktop background, etc). There should be a tab that allows you to change desktop/monitor resolution. Also in that tab is an Advanced button...this should bring up another window that will tell you what your card is.

If I missed anything, can someone fill in the blanks? Otherwise, it is pretty self explanatory once you start clicking things...

---

### Post by sthrnpagan on 2009-02-18
> **cariboo907 said:**
> When you get a black screen after login, there are two possibles causes, your monitor is not being detected properly, or updates weren't completed. Since this is a new installation the update problem shouldn't count.

Start in recovery mode and at the menu screen select xfix from the menu. Once xfix is finished select resume and continue on to the desktop. Once at the desktop install all the updates, as there is a fix for your problem in the updates.

Once you have completed the upgrades you will be asked to rebot, after the reboot, go to System-->ADministration-->Hardware Drivers and activate the restricted video drivers.

Jim


I will try this also, will either of these two options completely remove XP from this machine?

---

### Post by insineratehymn on 2009-02-18
Neither will.

---

### Post by sthrnpagan on 2009-02-18
> **insineratehymn said:**
> Neither will.

what do i have to do to wipe out windows?

---

### Post by insineratehymn on 2009-02-18
Reinstall after a clear format. Or use a tool like gParted to wipe out a certain partition and reallocate/reformat. But since you are using a fresh version of Ubuntu anyway I would just reinstall. Select the "guided, use entire disk" option in the partitioner (assuming that you have no other OSs/partitions installed that you want to keep).

---

### Post by Therion on 2009-02-18
You have to install on OS on top of it.  Part of the install process of Ubuntu will, if you decide you want to do it that way, completely over-write your Windows installation. I thought that's what you wanted to do from the beginning, which is why I directed you to using a USB thumb-drive and Unetbootin in my previous post.

---

### Post by sthrnpagan on 2009-02-18
> **Therion said:**
> You have to install on OS on top of it... I thought that's what you wanted to do.  Which is why I directed you to using a USB thumb-drive and Unetbootin.

Unetbootin did not work and i do not have a flash drive available.

---

### Post by insineratehymn on 2009-02-18
> **Therion said:**
> You have to install on OS on top of it... I thought that's what you wanted to do.  Which is why I directed you to using a USB thumb-drive and Unetbootin.

You ever have any luck with Unetbootin?

---

### Post by sthrnpagan on 2009-02-18
> **insineratehymn said:**
> You ever have any luck with Unetbootin?

nope

---

### Post by insineratehymn on 2009-02-18
> **sthrnpagan said:**
> nope

Me neither.

---

### Post by sthrnpagan on 2009-02-18
> **insineratehymn said:**
> Me neither.

how did you get it working>?

---

### Post by Therion on 2009-02-18
> **insineratehymn said:**
> You ever have any luck with Unetbootin?
It's what got Ubuntu installed on my Asus eee-pc.  

No USB thumb drive, no optical drive = no install as far as I'm concerned.  Other methods have never shown me to be reliable.

---

### Post by insineratehymn on 2009-02-18
Yeah, I agree completely. What ever happened to an FTP install for ubuntu? Get a small client on a 3.5" or something... I dunno.

---

### Post by Therion on 2009-02-18
> **insineratehymn said:**
> Yeah, I agree completely. What ever happened to an FTP install for ubuntu? Get a small client on a 3.5" or something... I dunno.
Well I guess you have to draw a line somewhere.  I mean we can't install Ubuntu on our cell phones either, can we?

---

### Post by insineratehymn on 2009-02-18
> **Therion said:**
> Well I guess you have to draw a line somewhere.  I mean we can't install Ubuntu on our cell phones either, can we?

[Hmmm...]("http://linuxdevices.com/news/NS8030785497.html") [I wouldn't say that...]("http://www.linuxdevices.com/articles/AT9423084269.html") ;)

---

### Post by argux on 2009-02-18
I used to follow the instructions on this page when I didn't want to burn a CD rom just to try a distro. It's been a while since I last did it, but it should work if you're not afraid of performing the steps.


[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")

---

### Post by Therion on 2009-02-18
> **insineratehymn said:**
> [Hmmm...]("http://linuxdevices.com/news/NS8030785497.html") [I wouldn't say that...]("http://www.linuxdevices.com/articles/AT9423084269.html") ;)
Damn you! I **knew** I should have gone with "We can't install Ubuntu on a granola bar, either, can we?" but nooooo....



/I double-dog DARE you...
//;)

---

### Post by insineratehymn on 2009-02-18
> **Therion said:**
> Damn you! I **knew** I should have gone with "We can't install Ubuntu on a granola bar, either, can we?" but nooooo....



/I double-dog DARE you...
//;)

[I can do this all day.]("http://picasaweb.google.com/chris.a.terry/RandomStuff#5304235682261727090")

---

### Post by sthrnpagan on 2009-02-18
Well, I dont know how i did it but Ubuntu is installed. I am now glad to report that this reply is being made from within Ubuntu. Thank you all for your help

---

### Post by Therion on 2009-02-18
> **insineratehymn said:**
> [i can do this all day.]("http://picasaweb.google.com/chris.a.terry/randomstuff#5304235682261727090")
[B]
*** Head Asplosion ***[/B]

---

### Post by brian_hayward on 2009-02-18
> **sthrnpagan said:**
> what do i have to do to wipe out windows?

When you install Ubuntu, you will come to a partioning window, which looks like the one in the attached photo (hopefully i attached it correctly...if i didn't here is the address [http://www.linuxdynasty.org/images/stories/distros/ubuntu/install4.png](http://www.linuxdynasty.org/images/stories/distros/ubuntu/install4.png)).  click the radio button next to the Guided - use entire disk option, continue through the rest of the installation windows and as Ubuntu is being installed it formats the drive to a file system it can understand which will wipe EVERYTHING including windows. 

Also, i don't mean to insult your intelligence, i'm sure you have thought about this already and taken the necessary steps but for those who may read this in the future who may not have thought of this, when you install Ubuntu on to your computer you are FORMATTING the drive to another file system, which erases everything currently on the drive, so all of your files (music, videos, pictures, ect) will be gone forever.  so make sure you go through your computer with a very fine toothed comb and save all the important stuff to a CD, DVD, or some other storage medium.

---

### Post by sthrnpagan on 2009-02-18
> **brian_hayward said:**
> When you install Ubuntu, you will come to a partioning window, which looks like the one in the attached photo (hopefully i attached it correctly...if i didn't here is the address [http://www.linuxdynasty.org/images/stories/distros/ubuntu/install4.png](http://www.linuxdynasty.org/images/stories/distros/ubuntu/install4.png)).  click the radio button next to the Guided - use entire disk option, continue through the rest of the installation windows and as Ubuntu is being installed it formats the drive to a file system it can understand which will wipe EVERYTHING including windows. 

Also, i don't mean to insult your intelligence, i'm sure you have thought about this already and taken the necessary steps but for those who may read this in the future who may not have thought of this, when you install Ubuntu on to your computer you are FORMATTING the drive to another file system, which erases everything currently on the drive, so all of your files (music, videos, pictures, ect) will be gone forever.  so make sure you go through your computer with a very fine toothed comb and save all the important stuff to a CD, DVD, or some other storage medium.



thank you. but i realized that since i used Wubi to install it wsas the the type of install to wipe windows. I now have a flash drive and am trying to figure out how to use that to install ubuntu and wipe windows.

---

### Post by insineratehymn on 2009-02-19
> **sthrnpagan said:**
> Well, I dont know how i did it but Ubuntu is installed. I am now glad to report that this reply is being made from within Ubuntu. Thank you all for your help

Great! Now... go and teach what you have learned!

---

