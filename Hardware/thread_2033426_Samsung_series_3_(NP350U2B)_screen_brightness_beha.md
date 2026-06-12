---
title: "Samsung series 3 (NP350U2B) screen brightness behaves strangely"
date: 2012-07-26
forum: Hardware
---

### Post by buildingsteam on 2012-07-26
I have a Samsung series 3 (NP350U2B) which was working fine with Ubuntu 64 bit 12.10.
 
That was until a software update a couple of days ago. Before the update the brightness could be set at a range of values, using both the builtin keyboard function keys, and the settings control. After the update the brightness can only be at minimum or maximum values (keyboard function keys and settings control) and the brightness control display stutters when trying to select anything inbetween.
 
Anyone experience anything similar ? I dont really know where to start in order to determine what part of the update is causing the problem.
 
Any advice much appreciated.

---

### Post by Toz on 2012-07-26
Hello and welcome to the forums.

Its quite possible that the update a couple of days ago was a kernel update. What kernel are you currently using (from a terminal window, type in the following command and post back the results)?
```
uname -r
```

You could try booting the previous kernel and see if the brightness works. If it does, we may have a kernel regression and a bug report may be necessary. To boot the previous kernel, hold down the shift key while booting to get to the grub screen, select "Previous Linux Version" and select the topmost entry.

Please also note the kernel version that works using the command above.

---

### Post by buildingsteam on 2012-07-26
Thanks for your help.
 
The kernel is 3.2.0-27 generic.
 
When I revert to the previous one (3.2.0-26) the brightness works correctly.

---

### Post by Toz on 2012-07-26
I would suggest creating a bug report on launchpad against the kernel (package=linux) specifying a kernel regression against brightness on your laptop. 

To get the process started, try:
```
apport-bug linux
```

---

### Post by dsakuma on 2012-07-28
I have exactly the same problem.

---

### Post by dsakuma on 2012-07-28
I found a solution [here]("http://askubuntu.com/questions/167832/ubuntu-12-04-brightness-problem")


Add the **"Linux On My Samsung"** repository to the sources list:
```
sudo add-apt-repository ppa:voria/ppa
```

Update the programs list:
```
sudo apt-get update
```

Install samsung-backlight:
```
sudo apt-get install samsung-backlight
```

Restart the system and check if backlight control works


More info [here]("http://www.voria.org/forum/viewtopic.php?f=3&t=1091")

---

### Post by buildingsteam on 2012-07-29
The steps above worked, thanks for your help, hopefully it'll be sorted out in the next version of the kernel.

---

### Post by JanuaryJones on 2012-07-31
It worked for me also!

---

### Post by flaviod on 2012-08-26
Great. Thank you, dsakuma.

---

