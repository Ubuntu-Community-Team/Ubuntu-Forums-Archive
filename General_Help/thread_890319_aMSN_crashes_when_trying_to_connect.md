---
title: "aMSN crashes when trying to connect"
date: 2008-08-14
forum: General Help
---

### Post by TurboFreak on 2008-08-14
Hello,
i recently installed aMSN but everytime i try to login to my msn account it just crashes. It also crashes when i click the link for checking for a newer version.
When i start aMSN through a terminal it says "Segmentation fault" when it crashes.
Today i recieved an update for aMSN but it is still the same.
I got that problem on both, my laptop and my desktop pc, running hardy i386 on the laptop and hardy for amd64 cpus on the desktop pc.

Does anyone have a suggestion what i can do about that?
Many thanks in advance!

---

### Post by jualin on 2008-08-14
Go to the terminal and run aMSN through there. And then copy all the outputs to the forums to see if aMSN tells us a clue of where the problem lies. Good luck!

---

### Post by jualin on 2008-08-14
Disregard my last post since I didn't read the part in your post where it said that you already tried it. :lolflag:

---

### Post by tuxxy on 2008-08-14
MSN updated their protocol, you need to update your aMSN to the new 0.97.2 version to access the network, download the 32/64bit update package here; [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)

---

### Post by jualin on 2008-08-14
Did you install aMsn using Synaptic or did you download the program and install it manually?

---

### Post by TurboFreak on 2008-08-14
> **jualin said:**
> Did you install aMsn using Synaptic or did you download the program and install it manually?

I installed it via Synaptic.

---

### Post by TurboFreak on 2008-08-14
> **tuxxy said:**
> MSN updated their protocol, you need to update your aMSN to the new 0.97.2 version to access the network, download the 32/64bit update package here; [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)

OK, i downloaded amsn_0.97.2-1~getdeb1_i386.deb and installed it on my laptop.
aMSN now identifies itself like this: "aMSN 0.97.2 (07/25/2008)"
But it still keeps crashing. :(

---

### Post by jualin on 2008-08-14
You need to uninstall the aMSN you installed via Synaptic first and then install the package that tuxxy suggested.

---

### Post by tuxxy on 2008-08-14
When is it crashing? I thought it was when you clicked update and it seg faulted? 

If you installed that .deb then it shouldnt prompt you to update as you are running the current version.

---

### Post by TurboFreak on 2008-08-14
> **jualin said:**
> You need to uninstall the aMSN you installed via Synaptic first and then install the package that tuxxy suggested.

I have now uninstalled aMSN again using Synaptic, then reinstalled it using amsn_0.97.2-1~getdeb1_i386.deb.
But it's still all the same.

---

### Post by TurboFreak on 2008-08-14
> **tuxxy said:**
> When is it crashing? I thought it was when you clicked update and it seg faulted? 

If you installed that .deb then it shouldnt prompt you to update as you are running the current version.

It does not promt me to update.
There is just some link thing in the aMSN main window saying: "Auf neue Version prüfen" (german)
In english it means: "check for newer version"

It crashes when i click that link but more important is, that it also crashes when i try to login to my msn account.
In both cases the terminal output is the same, just: "Segmentation fault"

---

### Post by Leechpool on 2008-08-16
I am seeing exactly the same behavior. I installed 0.97+final-0ubuntu5.1 on Hardy from synaptic. When I run it in a login window appears. It all appears OK except that the moment I hit login or check for updates the window disappears and nothing replaces it. If I run in terminal "Segmentation fault" is all that appears in the terminal when it crashes.
Not sure what this means but in synaptic, the following tcl packages are installed:
tcl
tcl8.3
tcl8.4
tcl8.5
tcltls

I hope someone can suggest something.....

---

### Post by jualin on 2008-08-16
How about using Kopete instead of aMSN?

---

### Post by Leechpool on 2008-08-17
I tried Kopete- it doesn't seem to support voice calls .... otherwise it seems OK.

---

### Post by jualin on 2008-08-17
How about Pidgin for Voice calls and Kopete for webcam.

---

### Post by TurboFreak on 2008-08-17
I tried Kopete now, too.
But it doesn't seem to support handwritten messages either.

Also, i now recieved an update for aMSN on my desktop, dedicated to fix an "login issue" on debian systems. But it still keeps crashing when i try to login. :(

---

### Post by donpedrodos on 2008-08-21
I faced the same problem yesterday by getting the "Segmentation fault".

It took me until now to find the solution on the internet.

[Debugging aMSN via gdb]("http://ubuntuforums.org/showthread.php?t=823848").

There became clear that the problem after clicking to login was caused by:
> Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb796c6b0 (LWP 7749)]
0xb68fd835 in _nss_wins_gethostbyname_r () from /lib/libnss_wins.so.2

Further seaching forums i found one item [here in bugs.launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/tk8.5/+bug/200397").

> Removing wins from nsswitch.conf removes the problem.
This was for me the solution.
This file was edited a few day ago, so why it became a problem so suddenly i do not know.
After restoring the backupfile, this was without the wins, the login with aMSN was normal again.

A pitty is that i cleaned the whole system with respect to aMSN more or less for only one stupid word in a config file .... wins .... the loser :-(

---

### Post by TurboFreak on 2008-08-23
Thanks, donpedrodos!
That did it!

It's also a bit of a pitty because i added "wins" to nsswitch.conf myself on purpose.
Cause according to this thread you need it to be able to mount by the netbios name: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by fermulator on 2008-09-06
Confirmed this fix on HARDY 8.04.

I've posted a bug report in the amsn forums: [http://www.amsn-project.net/forums/viewtopic.php?p=33431#33431](http://www.amsn-project.net/forums/viewtopic.php?p=33431#33431)

---

### Post by ddog800 on 2008-11-09
Yep, looks like 'wins' added to /etc/nsswitch.conf was my problem as well. This started suddenly a week or 2 ago, and that was about the same time I'd modified it so I could access my windows file server easier. I just removed 'wins' from the file, and aMsn now connects with no problems. 

I hope this bug gets corrected soon.

-Daniel

---

### Post by bigtooth on 2009-05-05
I'm using Ununtu 8.04 and removing wins from /etc/nsswitch.conf also resolved my segmentation fault problems with aMSN. I have never touched this file in my life so don't know why it suddenly started to give me troubles. Many thanks for proving me this solution!

---

### Post by Strange_Movement on 2009-06-04
I also had the segfault problem due to having added winbind to my system so I could refer to my PCs on the network by name rather than ever changing DHCP'd IP address. I didn't want to lose this ability so I took a guess at name resolution being tried in order of method listed in */etc/nsswitch.conf*

....and it appears to have worked !

So try this; change the order of name resolution methods on the line you had as:

*hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4*

to:

*hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins*

Notice how *wins* is now the last method to be used rather than the second. Hopefully this means that aMSN will get its name resolution completed by *dns* first and never get to *wins*. This way if you're looking for name resolution for PCs on your network hopefully all the preceding methods will fail until *wins* is tried at the end.

Hope this is helpful to everyone.

---

### Post by ProsperB on 2009-07-26
Thanks for this post. It was most helpful !
I say thanks to donpedrodos also because removing wins already made it work again.
In an afterthougt I read the rest of this thread and found Strange_Movement's consideration about resolving PC-names on the home network. Adding wins again but at the end of the line didn't make it break again...

---

