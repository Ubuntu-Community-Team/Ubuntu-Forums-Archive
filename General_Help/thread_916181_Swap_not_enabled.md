---
title: "Swap not enabled"
date: 2008-09-10
forum: General Help
---

### Post by fkabir on 2008-09-10
Hello

ubuntu has been using alot of memory, so i went out and bought anoth 256mb sdram card and maxed out the ram that the computer could handle, but it still uses alot of memory and i know ubuntu doesnt use all that. So it looks like the swap was disabled, so i need to enable it. Can some one help me out and guide me into resolving this?

If using the terminal please be very clear and detailed with your commands as i am a beginner.

attached is a screen shot of the system top screen.

thanks
faizan

---

### Post by WRDN on 2008-09-10
To turn the swap on, open the Terminal and type:

```
sudo swapon -a
```

Then, enter your password and it will be activated. You can easily tell whether it is on or not by opening System Monitor (System > Admistration > System Monitor) and clicking the Resources tab. If the swap usage is listed as "0 bytes (0.00%) of 0 bytes", then it is turned off.
To turn swap on at boot-up, you need to edit the fstab file.

First, find the UUID of the swap partition by typing:

```
sudo blkid
```

```
sudo gedit /etc/fstab
```

Add to the file, the line:

> UUID=**82e16643-e596-47e8-9bac-974019308ddc** none swap sw 0 0

Note that, you will need to change the UUID (seen in bold), using the output from the "sudo blkid" command.

Now, save the file and when you reboot, the swap should be turned on automatically.

EDIT: After looking at the attached image, other concerns have been raised. It appears you have already got swap turned on (else it would list 0k) under all "Swap:" entries. However, it is very odd that it is not being used at all. I would first try turning it off and on again:

To turn it off:

```
sudo swapoff -a
```

Then:

```
sudo swapon -a
```

---

### Post by fkabir on 2008-09-10
I did what us said and turned the swap on and off and i still have no response with the swap drive.

Was i suppose to get a reply form the terminal when i enter sudo swapon -a and off?

---

### Post by fkabir on 2008-09-10
im not sure if this matters but the total swap space is 1.9gb and my total memory on the computer is 768mb

---

### Post by WRDN on 2008-09-10
> **fkabir said:**
> I did what us said and turned the swap on and off and i still have no response with the swap drive.

Was i suppose to get a reply form the terminal when i enter sudo swapon -a and off?

When the swapon/swapoff commands are entered, there should be no output.

Please post the output of:

```
sysctl vm.swappiness
```

You may want to then raise the value that appears, by typing:

```
sudo sysctl vm.swappiness=70
```

Change "70" to a value between 0 (no swap) and 100 (high swap usage).

If you raise the swappiness and it is used, you can make this change permanent, by editing the sysctl.conf file:

```
sudo gedit /etc/sysctl.conf
```

Add the following line to the bottom of the file:

> vm.swappiness=70

As mentioned, you can replace 70 with a different number.

Now, save and reboot.

---

### Post by fkabir on 2008-09-10
1st code > vm.swappiness = 60i made it 100 and it still isnt being used

i attached a screenshot

---

### Post by xebian on 2008-09-10
> **fkabir said:**
> Hello

ubuntu has been using alot of memory, so i went out and bought anoth 256mb sdram card and maxed out the ram that the computer could handle, but it still uses alot of memory and i know ubuntu doesnt use all that. So it looks like the swap was disabled, so i need to enable it. Can some one help me out and guide me into resolving this?

If using the terminal please be very clear and detailed with your commands as i am a beginner.

attached is a screen shot of the system top screen.

thanks
faizan

From top, you have swap.  If you have none, then top will show '0'.  
There is nothing wrong if no swap is used because your system does not feel the need yet.

One way to find out memory usage/stats is execute on the terminal this command

```
 free -m 
```

Mine looks like this bec I don't have one

```
free -m
             total       used       free     shared    buffers     cached
Mem:          5947        666       5281          0         36        282
-/+ buffers/cache:        347       5599
Swap:            0          0          0


[COLOR="Red"]**Now with swap on**[/COLOR]

free -m
             total       used       free     shared    buffers     cached
Mem:          5947        670       5276          0         36        283
-/+ buffers/cache:        350       5596
Swap:         4808          0       4808



```

---

### Post by fkabir on 2008-09-10
right but the swap wasnt even being used when i had 3 or 4 programs open. i only had some 90mb of memory left out of 768mb. im assuming it should have used the available swap.

take a look at my first post with the attached photo.

---

### Post by fkabir on 2008-09-10
heres a recent top screen with multiple programs open and no swap usage. i made the swap usage to 100 like what WRDN said and i guess it still doesnt make a difference.

and thanks for helping out guys, i appreciate it.

---

### Post by xebian on 2008-09-10
> **fkabir said:**
> heres a recent top screen with multiple programs open and no swap usage. i made the swap usage to 100 like what WRDN said and i guess it still doesnt make a difference.

and thanks for helping out guys, i appreciate it.

Most of your open apps probably are not memory hog.  Why don't you open Firefox, open lots of tabs and open Youtube.  Or do some video editing, open some spreadsheets or play some games.

---

### Post by Habbit on 2008-09-10
> **fkabir said:**
> right but the swap wasnt even being used when i had 3 or 4 programs open. i only had some 90mb of memory left out of 768mb.

These are my "free" statistics: ```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1999         15          0         42       1173
-/+ buffers/cache:        783       1231
Swap:         4094          0       4094
``` At a first glance, it appears that I have used nearly all of my memory (15 MiB free??), but the real information is in the 2nd line: I am "only" using 783 MiB and have over 1.2 GiB free. Linux is very aggressive with caching and persists weak buffers for as long as there is no memory pressure, so it might appear all my memory is used up when in reality 1.1GiB of that "used memory" are cached files that can be discarded on the fly. In the default configuration, Linux only uses swap when it gets close to running out of memory.

---

### Post by fkabir on 2008-09-10
i sure did, i opened up epiphany a few times, open office word twice, and open office presentation, kontact. these were all open at one time and the screen shot in the post above yours shows the memory usage. there is only 35000kb free out of 775000kb

---

### Post by fkabir on 2008-09-10
o okay i see what your talking about. if thats the case thats fine, ut if free -m says my bnuffer i only have 526 free and 250 used is that okay?

---

