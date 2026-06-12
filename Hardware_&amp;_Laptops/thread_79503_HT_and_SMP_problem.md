---
title: "HT and SMP problem"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by alt236 on 2005-10-20
Hello!

I have a P4 with HyperThreading and I tried to install the 686-smp kernel.
The problem is that the system now is veeeerrrryyyy slow (taking 5-10 minutes to boot) instead of 30 seconds when using the 386 kernel.
Furthermore, when I finally login to Gnome a messagebox informs me that hal failed to initialise.

When I was using warty/hoary everything was working fine...
Is there a flag I need to pass to the kernel apart from ht=on?

Any ideas? Anyone else with the same problem?

Everything else works fine though! Keep up the good work people! 

This thread comes from this one: [http://www.ubuntuforums.org/showthread.php?p=424185&mode=linear]("http://www.ubuntuforums.org/showthread.php?p=424185&mode=linear")

---

### Post by alt236 on 2005-10-23
No one else with the same problem?

---

### Post by yacc45 on 2005-10-24
I had a similar problem. I tried to use the 2.6.12-9-686-smp kernel on my P4 HT system. The system always freezes after the login window is shown. Any idea?

---

### Post by prasys on 2005-10-24
I'm no linux expert here. Is it because you need the ubuntu extensions when you need to compile SMP-based kernels. Correct me if i'm wrong

---

### Post by duffydack on 2005-10-24
similar problem here.
linux/kde lags quite a bit with 686-smp 
and now i gone back to hoary my net lags with dns resolving......i cant win

---

### Post by Robgould on 2005-10-24
I have the sam prcoessor and the same issue.  When I ran the smp kernel I had massive system instability.  I have used smp kernels from Fedor before wih no issues.  I am not technical enough to troubleshoot so I went to the base 686 kernel.  This resolved my issues, but I'm still wondering if I should be using the other kernel somehow.  I don't think that I am taking advantage of the hyperthreading capability of my processor this way.

---

### Post by alt236 on 2005-10-24
[QUOTE=prasys]I'm no linux expert here. Is it because you need the ubuntu extensions when you need to compile SMP-based kernels. Correct me if i'm wrong[/QUOTE]

I didn't compile my kenrel, i apt-getted the one on the repositories... Thanks for the suggestion though.
I might try compiling one later on this week (including the Ubuntu extensions) just to make sure that its not something one the source tree/ kernel settings that affects it.

Has anyone filed a bug report till now, or should I do it?

---

### Post by alt236 on 2005-10-25
A bug report already exists apparently.
It is located here:  [http://bugzilla.ubuntu.com/show_bug.cgi?id=15591]("http://bugzilla.ubuntu.com/show_bug.cgi?id=15591")

---

### Post by alt236 on 2005-10-27
Out of curiosity, how much RAM do you guys have?
Both me and the person filing the bug have 768 MB.

---

### Post by charly4711 on 2005-12-05
Hi folks,
have the same symptoms and for me it is related to

[http://bugzilla.kernel.org/show_bug.cgi?id=5165](http://bugzilla.kernel.org/show_bug.cgi?id=5165)

the patches there won't really solve things for me (am pondering setting C1 the hard way) but the command 
```
echo 1 >| /sys/module/processor/parameters/max_cstate
```
(once I've booted) fixes my lag
HTH,

Karl.

---

### Post by charly4711 on 2005-12-05
phew ....
just before I was about to dive into patching my kernel myself I found [this]("http://www.thinkwiki.org/wiki/Talk:Problem_with_high_pitch_noises")

passing idle=halt as a bootup option fixes things for me.

Karl.

---

### Post by marwis on 2005-12-08
[QUOTE=charly4711]Hi folks,
have the same symptoms and for me it is related to

[http://bugzilla.kernel.org/show_bug.cgi?id=5165](http://bugzilla.kernel.org/show_bug.cgi?id=5165)

the patches there won't really solve things for me (am pondering setting C1 the hard way) but the command 
```
echo 1 >| /sys/module/processor/parameters/max_cstate
```
(once I've booted) fixes my lag
HTH,

Karl.[/QUOTE]

this works.  However, each time the system reboots, the value (1) is set back to 8 ... well, this might sound very dirty but
```
sudo chmod 444 /sys/module/processor/parameters/max_cstate
```
worked for me.

---

