---
title: "Installer fails at 99.9%"
date: 2008-07-14
forum: General Help
---

### Post by AADude on 2008-07-14
**Xubuntu-8.04.1**

Okay I downloaded **Xubuntu**, I burned the files to a CD. I tested it out and everything worked on the Xubuntu system. Now, I went back to Windows and pressed the "Install inside Windows" button. 

It gets to the "Creating Image" portion of the installation and reads off of the disk. It gets to 570.3mb of 570.6mb, and then suddenly fails and says it can't read off of the CD anymore.

Here's a screenshot:
[img]http://www.majhost.com/gallery/AADude/Random/xubuntu_fail.png[/img]

Any help please? Also, I'm new to Linux so if you don't think this is the best system to start out with can you recommend a different type of Linux (i.e. Knoppix, Ubuntu, Kubuntu, etc.). 

Thanks, Stephen.

---

### Post by AADude on 2008-07-14
Also, I don't really get what an "alternative cd" is. Does it just contain the installer you can start without a CD?

---

### Post by halitech on 2008-07-14
an alternative cd is just for use to install only as opposed to the normal cd which has the Live CD which allows you to test drive Ubuntu without installing it. 

Depending on your system specs will determine if Xubuntu is the best or not. I use it on my laptop but its an older machine. What kind of computer are you trying to install on?

as to the original issue, are you using WUBI to install? Might want to ask on the WUBI forum, they may have a better idea

---

### Post by laser_in_your_eye on 2008-07-14
Courtesy of the ubuntu home page:

"The alternative desktop CD...does not include the Live CD, instead it uses a text-based installer."

As for your other problem, did you try to check your install CD for errors?  There is normally an option to do that when you insert the CD with a standard installation, but I'm not sure with the "install in Windows" route.

---

### Post by AADude on 2008-07-14
Well there is wubi.exe, I just open up umenu.exe and do the installation that way. It only works on the CD though. My computer is a Dell Dimension E310 which I hate xD.

And laser, there is no option to do that on this installation.
EDIT: But when it installs it check sums the files first (as I recall).

---

### Post by ChameleonDave on 2008-07-14
99.9%?  That must be infuriating!  I hope we can solve your problem.

By the way, an admin should probably move this to the Wubi forum, where people have more specialised knowledge.

---

### Post by AADude on 2008-07-14
And uh whats the difference between "Guided - use the entire disK" and "Guided - use the largest continuous free space".

I want to not overwrite Windows, so which would be my choice? I don't want to screw up.

---

### Post by HotCupOfJava on 2008-07-14
"Guided - use largest continuous free space" - but that is not what I would expect to see if you were trying to install INSIDE Windows. Both of those options sound like a normal installation. Are you wanting a dual-boot system? There is a better way to do that......if you're interested.

---

### Post by AADude on 2008-07-14
Yes, I'm trying to have Linux and Windows on at the same time. Currently I can boot up them both at seperate times when I start up my computer, but that's if I have the LiveCD in. I want it to work without the CD.

EDIT: And I was originally trying to make a partition for Linux, but then I tried to install it inside of Windows... so what I **want** to do is have it inside of a partition.

---

### Post by HotCupOfJava on 2008-07-14
OK, then here is what I suggest you do:

First, run your Windows disk defragmenter SEVERAL times in a row (even if it says you don't need to). This will help reduce the risk of accidentally overwriting when you re-partition. Then load the live CD and pull up the utility called "Partition Editor" (this is GParted, and it works much better than the partitioner the install process runs). It should be under "Applications">"System"(if I remember correctly). Use this utility to resize the Windows partition. This will leave free (no filesystem) space on the hard disk for Xubuntu. Then restart with the Live CD, and choose "Install Xubuntu" during the boot-up process (don't wait for it to boot and try to install then). When it gets to the part where it asks if you want to use the entire disk or use the largest free space, choose "Guided-use the largest contiguous free space". Finish on out. When you restart, you should get a list of options on which OS you want to boot with. The first time you boot back into Windows, it will want to re-examine your filesystem for errors. Let it do it. Everything should be fine.

---

### Post by AADude on 2008-07-14
Thanks for the instructions/tips. One small problem though, recently today (a few hours ago) I tried disk defragmenting. It would literally take 10+ hours just to do it once.

---

### Post by HotCupOfJava on 2008-07-14
You for sure need to defrag first, then. It will save you alot of heartache (sorry its gonna take so long). After that first defrag the others will go MUCH faster, I promise.

---

### Post by AADude on 2008-07-14
Okay I guess I'll leave my computer on overnight and let it defrag. And do you know where Firefox downloads save to? -.- there is no options menu to view/change the folder location.

Thanks for your help D:

---

### Post by HotCupOfJava on 2008-07-14
They usually download to the desktop......

---

### Post by HotCupOfJava on 2008-07-14
And its my pleasure to help. Hope it all works out for you.

---

### Post by AADude on 2008-07-14
Ah okay I'm so used to Windows actually showing the icons - LOL. Thanks alot as I said before D:

---

### Post by p_quarles on 2008-07-15
Moved to the Wubi section.

---

### Post by ago on 2008-07-15
As explain in the guide and the FAQ this is a known bug due to a Windows issue with ISO extraction. For different reasons it was not possible to ship a workaround in 8.04.1. Although annoying, the solution is simple: do not use a physical CD at all. Simply run wubi.exe and let it download the ISO, if you already have an ISO you can place the ISO and wubi.exe (use rev 506 from the wubi website as the version on CD cannot use local ISOs) in the same folder and then run wubi.exe. Of course an installation to a dedicated partition is always a better long term solution.

---

### Post by AADude on 2008-07-15
Thanks everyone, I'm probably gunna go with the partition. Defragging now :)

---

