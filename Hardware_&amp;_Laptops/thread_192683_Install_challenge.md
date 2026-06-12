---
title: "Install challenge"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by pvangarde on 2006-06-09
Hello everyone. First, I want to congratulate the ubuntu team for making linux friendlier and easier, and something that just works. 

Now, to the good stuff: I'm converting my girlfriend to a ubuntu user but she is having problems installing the system. She has a laptop and it seems like the CD has a real hard time reading the installation CD. It reads it, but it does so really, really slowly. You wait for dialogs to pop up for 10 minutes. I'm pretty sure it is the CD reader thats the problem, since I burned a few CDs (from her own laptop and mine) and they all did the same. So, it is nearly impossible to carry out the installation in this state.  The CDR plays and records CDs fine in Windows which leads me to think that maybe Ubuntu has problems handling the device. 

Is there any way to fix the CD issue? I've thought about saving the image on a USB Drive and loading it up but I don't have a 1 gig drive, so that's out of the question. Maybe I can somehow the run the setup from my hdd? Or fix the CD issue (as for example copy all the necessary files on the hdd and continue for there?) Finally, how would you go about isntalling ubuntu on a computer which does *not* have a CD drive?

Thanks

---

### Post by aysiu on 2006-06-09
Are you running the **Desktop CD** or the **Alternate CD**?

---

### Post by tmahmood on 2006-06-09
How much RAM do you have? If you are low on memory(<256) then this might be the reason for slow down. In that case switch to Alternate CD. which runs the text mode installer. Its fairly easy too(I like it more then the GUI one).

---

### Post by Face1 on 2006-06-09
[QUOTE=aysiu]Are you running the **Desktop CD** or the **Alternate CD**?[/QUOTE]
I can't answer this for pvangarde (obviously), but I am having the same problem, using the desktop CD.  Should the Alternate CD be used for laptops?

---

### Post by aysiu on 2006-06-09
It's not for laptops but for systems with very little RAM.

---

### Post by Jason_25 on 2006-06-09
Run the disk integrity check.  If that passes, but the install is still slow, I would say it's a problem with the cd drive too.  Lots of laptops have problems with the optical drives because they're not meant to be moved/knocked around.

I second the alternate cd suggestion too.

---

### Post by NetMatrix on 2006-06-09
The desktop CD worked for me and I have a fujitsu lifebook with very different hardware than most laptops/desktops.  However after installing with the text installer I am unable to boot into the CLI.  I'm not quite sure why this is and for some reason my laptop will not run gnome.  It will freeze everytime.  So I am currently downloading the Kubuntu desktop CD.

What kind of laptop is it and how much RAM does it have?

---

### Post by pvangarde on 2006-06-09
It is a Gateway laptop. It has at least 256 MB of RAM, I suspect it is 512MB. It is not here with me right now to check, but the RAM is not a problem. It has a Pentium M processor and I think that maybe the reason for it being so slow. I ran the Desktop CD and I'll try the Alternate CD today to see if that works better. I'll let you know later today.

I'll run the disk integrity check to see how fast it completes. The reason for thinking it is the CD drive's fault is mainly because when it starts reading the CD the whole things starts vibrating like it's about to fly out of the case. I think the Alternate CD may fix the issue, if it is indeed a cpu thing.

---

### Post by NetMatrix on 2006-06-09
Perhaps you could do a network install.  You could set up a NFS mount to boot the laptop from.  Check this link.

[https://wiki.ubuntu.com/Installation/OnNFSDrive?highlight=%28install%29]("https://wiki.ubuntu.com/Installation/OnNFSDrive?highlight=%28install%29")

This may solve your problem.  Here is a whole list of install options:

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=installation&titlesearch=Titles]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=installation&titlesearch=Titles")

Hope this helps good luck. :D

---

### Post by pvangarde on 2006-06-10
Success! I was able to install Ubuntu using the Alternative CD. It was still slow but it worked. The laptop has 256 MB RAM, and Pentium Celeron Mobile 1.3GHz.

Do I need to maybe recompile the kernel so that the cpu runs faster? I think I should since it seems slow.

---

### Post by Jason_25 on 2006-06-10
Nothing that you do will make gnome run significantly faster with 256 MB of ram, sorry.

---

