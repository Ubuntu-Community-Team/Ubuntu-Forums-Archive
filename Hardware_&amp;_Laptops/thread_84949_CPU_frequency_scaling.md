---
title: "CPU frequency scaling"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by bealud on 2005-11-01
hello everybody.

I have a laptop based on the AMD Turion MT32 and I installed ubuntu breezy on it. 
I have some problem with the cpu frequency, the processor is all the time at 1,8Ghz :(
however powernowd is running !! I hadn't this problem with hoary.

What can I do to solve this problem???

thanx to everyboby.

ludo 
(sorry for my english :razz: )

---

### Post by 23meg on 2005-11-01
Can you please send the output you get from the "modprobe -l" command?

---

### Post by bealud on 2005-11-01
I can't send that, the text is too long.
What are the interessant lines ?

---

### Post by bealud on 2005-11-02
Here is the output of the command "modprobe -l" : 
[http://bealud.free.fr/mod.txt]("http://bealud.free.fr/mod.txt")

---

### Post by bealud on 2005-11-03
nobody to help me ???:confused: 
Please:KS

---

### Post by Delvien on 2005-11-03
install Emifreq from either the web or synaptic, then move the monitor into the task bar  via "Add to panel " Then scale the cpu down

---

### Post by munk on 2005-11-08
Might be relevant: my IBM Thinkpad refuses to run at anywhere above 1.8Ghz unless it is plugged into the mains power when it first turned on (then it's 3.33).

- Andrew

---

### Post by 23meg on 2005-11-08
Did you try running powernowd in an alternative mode? Take a look at its manpage where you'll find info on doing so; try it and tell us if it helps.

---

### Post by bealud on 2005-11-25
I have tried other modes, but it doesn't work better :(
What can I do now ?

---

### Post by frabcus on 2005-11-27
If it's any consolation, I have a similar problem! I'm running the Gnome Frequency Scaling Applet. When I boot up (with power not connected) the applet warns me that frequency scaling isn't supported, and it shows the CPU speed as being full. If I kill the applet and reload it everything now works fine.

So, bealud, when you say scaling isn't working, how are you telling this? From an applet, or looking at /proc/cpuinfo?

---

### Post by bealud on 2005-11-27
The applet works fine, I have checked it with /proc/cpuinfo...

---

### Post by Raoul Duke on 2005-11-29
I fixed this by rebuilding the kernel with the folowwing option changes:

Default CPUfreq governor=userspace
build all 4 governors into kernel (not as loadable)

---

### Post by bealud on 2005-11-30
what a good new !
Can you explain me how to rebuild the kernel, please ?
Also, if you know how to apply a patch "patch.diff"? (it's for my sound card)

Thank you very much ! :cool:

---

### Post by Raoul Duke on 2005-11-30
Kernel building HOWTO is here...
[http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")
 have fun :-)

---

