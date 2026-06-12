---
title: "4 noob questions for wubi/ubuntu/kubuntu..."
date: 2008-11-26
forum: General Help
---

### Post by kyleryner on 2008-11-26
Hi all, 

  a VERY satisfied newbie wubi (hey that rhymes! :)) ubuntu user here... I just have 4 simple noob questions about it, if you dont mind (and no need to answer all the questions) 

Q1: I installed the Gnome desktop with wubi. Now I want to try Kubuntu. Is this the same as installing KDE? Whats the best way to do this?

Q2: I allocated 6 Gigs for the wubi/ubuntu install.. now im loving it so much I think Ill need more space. btw, is it really this way with linux/ubuntu? EVERYDAY, they offer you updates and new software for FREE? :) Updates alone, by my observation is about 50-80mb a day so at this rate, wont you easily fill up even a 10 gig partition in a year? Not to mention the softwares..:)
Anyway, im thinking the 6 gig isnt enough.. is there a way to re-allocate bigger space (maybe even dedicate the whole 12 gig partition i placed wubi/ubunti in) or would it be easier to just uninstall wubi and start all over again (while Ive only been using it for a few days)

Q3: Im loving Ubuntu so much, im going to install it to an old Pentium II w/ windows98. Im downloading the i386 iso now. Is it correct i should get the Ubuntu 8.10 iso, and wubi will give me the option to install Kubuntu? Or do i download the Kubuntu iso? Will wubi recognize kubuntu iso? or is is the same as the ubuntu iso? Hopefully Ubuntu/Kubuntu will run smooth even on an old machine :)


Q4: (Optional Question :) )What happened to my Ubuntu 8.10 Desktop-AMD64 ISO? Originally, i downloaded the alternate-AMD64 ISO..which turned out to be the wrong ISO. I then downloaded the Desktop ISO, and ran Wubi w/in the download directory containing the 2 ISOs. Wubi keeps ignoring the desktop ver, so i placed wubi and desktop iso in a separate directory and ran wubi from there. Wubi worked beautifully then and installed ubuntu. But now i cant find the desktop ISO.. it seems it was unpacked by wubi. Just wanted to burn the cd for future use (oh well, no biggie.. i can always redownload later.. just find it weird that it disappeared, thats all :) )

thanks to everyone, this forum is great and im learning new and cool stuff from here all the time :KS

---

### Post by mikewhatever on 2008-11-26
Hi, and welcome.

A lot of your questions concerning wubi are answered in [WUBI FAQ]("http://ubuntuforums.org/showthread.php?t=716201").

> Q3: Im loving Ubuntu so much, im going to install it to an old Pentium II w/ windows98. Im downloading the i386 iso now. Is it correct i should get the Ubuntu 8.10 iso, and wubi will give me the option to install Kubuntu? Or do i download the Kubuntu iso? Will wubi recognize kubuntu iso? or is is the same as the ubuntu iso? Hopefully Ubuntu/Kubuntu will run smooth even on an old machine

My guess is, neither Ubuntu nor Kubuntu will run well on PentiumII. It wouldn't hurt trying, but check the minimal requirements and that PC's specs first.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Zaraphrax on 2008-11-26
> **kyleryner said:**
> Hi all, 

  a VERY satisfied newbie wubi (hey that rhymes! :)) ubuntu user here... I just have 4 simple noob questions about it, if you dont mind (and no need to answer all the questions) 

Q1: I installed the Gnome desktop with wubi. Now I want to try Kubuntu. Is this the same as installing KDE? Whats the best way to do this?

I'd do this:

```
sudo apt-get install ubuntu-desktop
```

> 

Q2: I allocated 6 Gigs for the wubi/ubuntu install.. now im loving it so much I think Ill need more space. btw, is it really this way with linux/ubuntu? EVERYDAY, they offer you updates and new software for FREE? :) Updates alone, by my observation is about 50-80mb a day so at this rate, wont you easily fill up even a 10 gig partition in a year? Not to mention the softwares..:)
Anyway, im thinking the 6 gig isnt enough.. is there a way to re-allocate bigger space (maybe even dedicate the whole 12 gig partition i placed wubi/ubunti in) or would it be easier to just uninstall wubi and start all over again (while Ive only been using it for a few days)

Lubi SHOULD do it ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)). I haven't tried it and I'm not too sure whether it's compatible with Intrepid yet.....

> 
Q3: Im loving Ubuntu so much, im going to install it to an old Pentium II w/ windows98. Im downloading the i386 iso now. Is it correct i should get the Ubuntu 8.10 iso, and wubi will give me the option to install Kubuntu? Or do i download the Kubuntu iso? Will wubi recognize kubuntu iso? or is is the same as the ubuntu iso? Hopefully Ubuntu/Kubuntu will run smooth even on an old machine :)

If you want to install Kubuntu in Wubi, you need to download the Kubuntu ISO. And I *really* doubt that it will run smoothly on that machine. I tried Ubuntu on a 200mhz machine with 128mb of RAM and it was terrible. Even Xubuntu wasn't that great, but you could try it. If you used a really light WM like Openbox or something and screwed around with the kernel you could probably get it running acceptably for internet browsing etc. Although, I wouldn't do that with a Wubi install.

> 
Q4: (Optional Question :) )What happened to my Ubuntu 8.10 Desktop-AMD64 ISO? Originally, i downloaded the alternate-AMD64 ISO..which turned out to be the wrong ISO. I then downloaded the Desktop ISO, and ran Wubi w/in the download directory containing the 2 ISOs. Wubi keeps ignoring the desktop ver, so i placed wubi and desktop iso in a separate directory and ran wubi from there. Wubi worked beautifully then and installed ubuntu. But now i cant find the desktop ISO.. it seems it was unpacked by wubi. Just wanted to burn the cd for future use (oh well, no biggie.. i can always redownload later.. just find it weird that it disappeared, thats all :) )



Hmm, that seems a bit odd. What exactly are you seeing to make you see that?

---

### Post by kyleryner on 2008-11-26
> **Zaraphrax said:**
>  

Hmm, that seems a bit odd. What exactly are you seeing to make you see that?

umm.. this is embarassing.. i did a search and found the iso file (blush)turned out i saved it in another directory and forgot abt it.. i was looking at a different wubi directory with a bunch of install files (probably bec i tried to install several times before i got it right). sorry about that false alarm :)

as for the rest... thanks for the tips guys.

its just that in the past, ive tried to install ubuntu and other distros with little or no success.. only this latest ver 8.10 did it for me so im excited to try it out with my other pcs.

ill try to experiment with it on the PII (Puppy and DSL ran fine there). But i have another extra PC.. a Duron 950mhz that i might be fast enough to run Kubuntu properly.

thanks again for the replies..

---

### Post by Zaraphrax on 2008-11-26
> **kyleryner said:**
> umm.. this is embarassing.. i did a search and found the iso file (blush)turned out i saved it in another directory and forgot abt it.. i was looking at a different wubi directory with a bunch of install files (probably bec i tried to install several times before i got it right). sorry about that false alarm :)

as for the rest... thanks for the tips guys.

its just that in the past, ive tried to install ubuntu and other distros with little or no success.. only this latest ver 8.10 did it for me so im excited to try it out with my other pcs.

ill try to experiment with it on the PII (Puppy and DSL ran fine there). But i have another extra PC.. a Duron 950mhz that i might be fast enough to run Kubuntu properly.

thanks again for the replies..

/facepalm :P

Oh well, at least you got it sorted!

---

