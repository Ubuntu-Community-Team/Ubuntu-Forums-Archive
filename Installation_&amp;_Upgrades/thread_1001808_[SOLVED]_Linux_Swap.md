---
title: "[SOLVED] Linux Swap"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by Hoom@n on 2008-12-04
Hello,
I have more than one Linux installed on my computer. Each has its own swap on the hard drive(e.g. my Ubuntu's swap is hda5 and my Kubuntu's swap in hda8 ). I wanted to know is it correct? Or all of them can work with only one swap?
Thanks,
Hooman.

---

### Post by snowpine on 2008-12-04
Hi Hooman,
Only one swap is necessary (though I think having multiple is harmless).

---

### Post by __Ryan__ on 2008-12-04
They can be setup to work with only one swap. Change the entry for swap in **/etc/fstab** to point to the same partition for each of your installations.

---

### Post by Hoom@n on 2008-12-04
Thanks for the answers. I thought the same, but Ubuntu installer did that!
First I formatted my hard drive to one ntfs drive and installed Windows. Then I installed Ubuntu and the installed divided the Windows' drive into one ntsf, one ext3 and a swap. Then I installed Kubuntu; Its Installer divided the Ubuntu's drive into two ext3 and one swap. So, now I have one ntfs, two ext3 & two swap! Why did the installer did so?! Can I report it to be fixed in next versions?
Thanks.

---

### Post by snowpine on 2008-12-04
Hi Hoom@n, a couple of things,

1) You probably chose "guided install" during the partitioning process. This default option automatically creates a swap partition, since that is what most users want. There is also a "manual install" option that you should choose if you want anything other than the default partition scheme.

2) You don't need to install Kubuntu and Ubuntu on separate partitions since they are basically the same except for the desktop environment. You can add Kubuntu to Ubuntu by using the terminal command:

```
sudo aptitude install kubuntu-desktop
```

Then, log out. From the login screen, choose Options->Sessions->KDE to switch to Kubuntu, or Options->Sessions->Gnome for Ubuntu.

Of course, some people prefer them on separate partitions for various reasons. If you want to keep them separate for whatever reason, and have enough hard drive space, please ignore my suggestion. :)

---

### Post by tarps87 on 2008-12-04
If you use one swap partition you will need to be careful. Say you hibernate Ubuntu it will save all the data on the RAM to the swap partition if you then run Kubuntu using the same swap partition it will want to right over this data which is where a problem will occur. If you don't plan to hibernate this will not be a problem.
Also I don't know if you know but you can install the KDE desktop (Kubuntu) on Ubuntu and swap between them at the login screen.

Edit: If you didn't know snowpine has already posted so I'm too slow anyway :)

---

### Post by Hoom@n on 2008-12-04
> **snowpine said:**
> Hi Hoom@n, a couple of things,

1) You probably chose "guided install" during the partitioning process. This default option automatically creates a swap partition, since that is what most users want. There is also a "manual install" option that you should choose if you want anything other than the default partition scheme.

2) You don't need to install Kubuntu and Ubuntu on separate partitions since they are basically the same except for the desktop environment. You can add Kubuntu to Ubuntu by using the terminal command:

```
sudo aptitude install kubuntu-desktop
```

Then, log out. From the login screen, choose Options->Sessions->KDE to switch to Kubuntu, or Options->Sessions->Gnome for Ubuntu.

Of course, some people prefer them on separate partitions for various reasons. If you want to keep them separate for whatever reason, and have enough hard drive space, please ignore my suggestion. :)

Yeah! I used the guided install for the first time! Every time before, I used manual install and I know how to use it.

Again yeah! I know that I can Install KDE desktop on my Ubuntu, but in that way I think in that way my computer gets crowded! For example then I have both kate and gedit, and it takes a long time to decide which to use and remove the other. So I prefer to have them in different partitions.

Thank you.

---

### Post by Hoom@n on 2008-12-04
> **tarps87 said:**
> If you use one swap partition you will need to be careful. Say you hibernate Ubuntu it will save all the data on the RAM to the swap partition if you then run Kubuntu using the same swap partition it will want to right over this data which is where a problem will occur. If you don't plan to hibernate this will not be a problem.
Also I don't know if you know but you can install the KDE desktop (Kubuntu) on Ubuntu and swap between them at the login screen.

Edit: If you didn't know snowpine has already posted so I'm too slow anyway :)

Well, the hibernate function does not work on my computer! (I had this problem from older versions and still have it on 8.10) So, I think there will be no problem to use one swap.

And, I know that I can Install KDE desktop on my Ubuntu, but in that way way my computer gets crowded! For example then I have both kate and gedit, and it takes a long time to decide which to use and remove the other. Then I'll have a lot programs with same function. So I prefer to have them in different partitions.

Thank you for your answers.

---

