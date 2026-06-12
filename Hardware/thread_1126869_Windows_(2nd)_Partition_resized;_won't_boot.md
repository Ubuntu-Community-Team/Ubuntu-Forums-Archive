---
title: "Windows (2nd) Partition resized; won't boot"
date: 2009-04-15
forum: Hardware
---

### Post by PeregrinGo on 2009-04-15
Hello Ubuntu Pros,

I'm in a bind. I have UBUNTU installed on my first primary partition and Vista on another partition. I rarely use it, but occasionally one of my graduate courses will require some software that just won't work right on Ubuntu. Don't wanna run a Virtual Machine, and Wine has limited capabilities... so, Vista lives on in the recesses of my mind and my machine. Anyway, I didn't alot enough space on the Vista partition to install any of the aforementioned school-related programs, and I need to resize it. I followed all the directions from the following website to the letter of the law: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/#comment-70422](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/#comment-70422)

Everything worked fine except for that repair your Windows installation part. It hasn't worked and I'd hate to have to reinstall Windows. If I do, I may as well do EVERYTHING (maybe I can make a recovery CD that includes all my current data?) so that I can dual boot using the two sniffy buttons on my Dell XPS M1530. Anyway, I DON'T want to go to all the hassle. Anyway I can fix my Vista install without the mess???? I appreciate your help!

---

### Post by sowelie on 2009-04-15
What kind of problems are you running into?  Can you just not boot into windows any longer?  If you google Ubuntu Windows Grub, there are a ton of articles out there describing how to add Windows to grub and get it working again.

---

### Post by meierfra. on 2009-04-15
Try this:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)

---

### Post by PeregrinGo on 2009-04-16
> **meierfra. said:**
> Try this:

Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.
 (If it does not give you an option to "write", it means that the original and rebuild boot sector are identical, and  testdisk RebuildBS won't be able to solve your problem)
This worked perfectly. Thanks so much! (I'd officially give you thanks, but for some reason that option isn't appearing. Have they gotten rid of it in the forum?)

---

### Post by meierfra. on 2009-04-16
```
This worked perfectly.
```
Great.

> Have they gotten rid of it in the forum? 

Yes. A couple of months ago, the forums had serious problems with their data base. And the "thank you" button was one of the  things which caused the problems.

---

### Post by Herman on 2009-04-16
PeregrinGo,
Did you use a GParted LiveCD to partition your hard disk before you discovered this problem, or do you think the problem came from GParted in Ubuntu?
What version of GParted did you use?

Thanks for any information,
Regards, Herman :)

---

### Post by PeregrinGo on 2009-04-16
I used the GParted Live CD. Thankfully, the fix above solved my problem.

> **Herman said:**
> PeregrinGo,
Did you use a GParted LiveCD to partition your hard disk before you discovered this problem, or do you think the problem came from GParted in Ubuntu?
What version of GParted did you use?

Thanks for any information,
Regards, Herman :)

---

### Post by PeregrinGo on 2009-04-16
I see. Well, thanks anyway. I'm so glad I didn't have to start from 0. Once you get accustomed to working with a certain configuration, it's such a pain to try and recoup it without the aid on an .iso.

---

### Post by Herman on 2009-04-16
:D Thank you very much for your kind co-operation, that news is important to me and it's what I was hoping for.
Nearly all booting errors are easily fixed, thanks to people like meierfra who are such a great help here in Ubuntu Web Forums.
No-one wants to have to go to all the work of re-installing an operating system. It can take days to get everything all installed, restored and personalized and customized and tweaked the way the user likes it.

Your feedback will help me decide how to edit my website appropriately.

Thanks again,
Regards, Herman :)

---

