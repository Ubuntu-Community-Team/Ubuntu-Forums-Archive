---
title: "Booting resolution problem in 10.4"
date: 2010-04-09
forum: Hardware
---

### Post by gall on 2010-04-09
Just after installing Ubuntu 10.4 I had plymuth and console resolution set to my screen native resolution, like 1920x1200. After updates and Nvidia drivers installation i have only 80x30 console:
from kern.log:
```

Console: switching to colour frame buffer device 80x30
```
so splash screen looks ugly and console is useless for me. How can i set right resolution?

---

### Post by Phentis on 2010-04-09
**Step 1**


You must edit the /etc/default/grub file.

Open a terminal and paste this:

```
$ sudo gedit /etc/default/grub
```

On line #18, uncomment (uncomment = remove the “#” in front of the line “#GRUB_GFXMODE=640×480” and change the resolution to whatever you want (in my particular case, I changed it to 1680x1050). Here is how it should look:

```
GRUB_GFXMODE=1680x1050
```


**Step 2**


edit the /etc/grub.d/00_header file.

```
$ sudo gedit /etc/grub.d/00_header
```

And find the following line: “gfxmode=${GRUB_GFXMODE}” (it’s line 103 on my computer) and under it, paste this:

```
set gfxpayload=keep
```


**Step 3**


update Grub 2:

To update the GRUB, simply run the following command:

```
$ sudo update-grub
```

Once you complete the above steps, restart the computer and you should see the nice Plymouth screen.

---

### Post by endtroducing on 2010-04-18
Thank you!

---

### Post by Bodai on 2010-05-01
Many thanks Phentis =D>

---

### Post by yeleek on 2010-05-18
Thanks :)

---

### Post by untitled_o on 2010-05-18
hey, im new here and i have one question, when im trying do what u said  Phentis appears on my console onething like " [sudo] password for untitled : "
and after i cant do anything :\

any help?

---

### Post by josarn on 2010-05-20
Hi there everyone. I would like to comment the behavior of my computer when i applied the changes to the config files mentioned in this thread . When I rebooted I found that the splash screen had the correct resolution but it was not centered and when I checked the terminal with  Ctrl + Alt + F1 I found myself staring at black screen. I did some googling and found that setting the resoultion in the 00_header file was supposed to work too, so I tried that and it set things straight. So in my case the line to add to /etc/grub.d/00_header looks like this:

```
set gfxpayload=1680x1050
```

---

### Post by spraitas on 2010-05-30
Like in josarn case i had same problem, everything not being centered. The quick update to /etc/grub.d/00_header solved eveything. Thanks all.

---

### Post by Beckman on 2010-10-22
This was very helpful, thank you.

---

