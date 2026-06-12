---
title: "cpu at 99%"
date: 2005-11-29
forum: General Help
---

### Post by Murgle on 2005-11-29
So this has been an ongoing problem that I have had, it seems at random times my cpu usage will shoot up to 99% and top reports that Xorg is using 80% or more cpu.  This makes no sense because when I have found that most of the time X-Chat has frozen and simply exiting out of X-Chat fixes the problem, which most of the time requires me to force quit.  Here is where the plot thickens though, Some times it is gaim that has frozen and it has also been Rhythmbox that freezes.  I'm not sure what the problem is because I don't have any special eye-candy turned on, although I did at one point.  It happens most frequently when Xscreensaver is activated but has happend when I was using the computer.  The programs that I have running almost all of the time are Opera, Rhythmbox, Nautilus windows, Gaim, X-chat, Gnome-term and btlaunchmanycurses.

Any help or suggestions would be wonderful

---

### Post by Robgould on 2005-11-29
I had the same issue.  I resolved it by changine Kernels.  I was using the 686 smp kernel.  I also had freezes with the 386.  I now use the 686 and have never had a freeze with it....for months.  The 686 is for pentium processors.  The 686 smp should work for hyperthreading processesors like mine, but it does not.....it freezes.  I hope this helps you.
 
To try the 686 kernel, search for "686" in apt.  Find linux image 686 (going off memory) and mark for installation.  After installation, reboot.  You should see the new kernel in your grub options.  Test the new kernel.  If you like it, you can safely remove the 386 kernel.  I would not remove it until you decide the 686 has you fixed.  Worked for me.

---

### Post by Murgle on 2005-11-29
you say that the 686 is for pentium processors, I have an amd will that still work just fine? Does anyone know exactly what the difference is between the 386 and the 686?

---

### Post by Robgould on 2005-11-29
you want the k7 kernel.  Look in Synaptic.  Search for amd or k-7.  Install the package named "linux-k7".  This will install the kernel for AMD Duron/Athlon processors.  Reboot and make sure you select the new kernel from grub.  I hope this works for you.

---

### Post by Murgle on 2005-11-29
I will do that is there any reason that the 386 kernel works almost flawlessly but not quite on my comp?  I had thought that the 386 was the right one...

---

### Post by Murgle on 2005-11-29
Well I tried the k-7 kernel, not the k-7-smp one and It gave me a kernel panic when it rebooted and all the parameters are the same beteween it and the 386 kernel so I'm not sure what the problem is.

---

### Post by Robgould on 2005-11-30
Sorry that did not help.  Maybe you can find some more hints here:
 
[http://www.ubuntuforums.org/showthread.php?t=76288]("http://www.ubuntuforums.org/showthread.php?t=76288")

---

### Post by teaker1s on 2005-11-30
you need howto [here]("http://ubuntuforums.org/showthread.php?t=85917")

---

### Post by Murgle on 2005-11-30
Thanks guys, I'm Looking into it and will report on my success of failure.  I think it is the RenderAccel bug and not a kernel issue as I had it stable for months before this started happening.

---

### Post by Murgle on 2005-11-30
I am trying what seemed like a solution that worked for at least some people, I have removed powernowd and am waiting.  Thanks for all your help guys

---

### Post by Robgould on 2005-12-01
I tried that...did not work for me...hope it does for you.  Powernowd actually works quite well on my Toshiba laptop.  You can add a CPU frequency applet to your menu bar where you can watch your frequency and see it scaling.  IMO using this for a little while and watching it respond to your system will erase doubts as to the effectiveness of this program. Powernowd is a program that I think is taking a bit of a bad rap.  It actually works well.

---

### Post by Murgle on 2005-12-04
Well it seems to be happening less often but it still happens, and I'm leaving it stopped since this is a desktop and so it does nothing for me.

---

### Post by Murgle on 2006-02-27
Well, I must admit I haven't been working too hard to solve this problem, but the problem still stands, Everyone and a while Xchat or Gaim will suddenly start using 99% of the cpu making it barely possible to see the text,  Everything returns to normal when I kill the problem app and then restart it... I still haven't a clue what is causing this and don't know how to figure it out.  Any help would be great.

---

### Post by bb002 on 2006-02-27
I have this problem occasionally too. Gnome's "System Monitor" would tell me the problem was X.org or whatever application I happened to be currently using. However if I open a terminal and run the "top" program, I was told the true culprit was "update-notifier". After having to do this several times i eventually added a bash script to my session start up that would sleep for 20 seconds then  killall update-notifier. I have yet to have this problem again.

Whatever goes wrong in "update-notifier" and makes "System Monitor" think it is a different program that is malfuctioning I don't know. I'm afraid I don't know enough to do any kind of tracing or figure out what causes it, so i can file a bug report.

[edit]
BTY, I have a AMD Athlon XP 3000+ running the 686 kernel. I originally tried the K7 kernel but it ran like crap.

---

### Post by Murgle on 2006-02-28
Well I'll try killing the update-manager, though why would the script need to sleep for 20s?  Also when update freezes for you do any other programs freeze up as well?

---

