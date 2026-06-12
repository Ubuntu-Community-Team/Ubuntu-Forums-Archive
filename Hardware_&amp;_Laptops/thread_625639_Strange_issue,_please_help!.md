---
title: "Strange issue, please help!"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by K4P741N KRUNCH on 2007-11-28
Hi, I'm new to the forums, but I've been using Ubuntu for a while now.

I have a Dv6000 and let me tell you, it was a hell of a struggle to get linux working correctly on it, but finally I did.  Wireless works, audio (including touch sensitive media controls) works, bluetooth works.  It all just seems to WORK (except the webcam)

Well recently on November 26th I turned on my Ubuntu box and got the latest batch of updates.  It was a rather large update and it took about 45 minutes to fully complete.  Then I went into add/remove programs and removed some games I didn't use to free up some space.

Thats all I did, I shut down normally afterwards and I thought everything was good, but now when I go to load Ubuntu, it freezes at a weird part in the startup process.

It gets past all the initial scripts, it then goes to a blinking cursor, finally the blinking cursor stops, it looks as though X is about to start, theres one final blink on my hard drive activity, then nothing.

I've left it there for an hour, nothing.
Before, the Nvidia fullscreen logo used to appear right there, but now nothing.

Luckilly for me I kept an old kernel in my menu.lst so I booted that and it worked just fine, only thing is it said my Nvidia driver was proprietary and I had to download the new one.

I would like to get the new kernel working again, because it seems alot of things aren't the same with the old one.  The new kernel was 2.6.22.14 and the old one I'm using is 2.6.20.16

Any help would be greatly appreciated, if you need more information, I can provide.
Thanks

---

### Post by PmDematagoda on 2007-11-28
You will have to reinstall the Nvidia driver when you upgrade the kernel.

1)Get the Nvidia driver for Linux from the Nvidia website.

2) Get the source files for your new kernel using:-
```

sudo apt-get install linux-source-2.6.22
```

3) Install the Nvidia driver again(As given in the Nvidia website).

4) Reconfigure the X-server using:-
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

5) Do:-

```
startx
```
to see if your GUI now works properly.

Note:- You may do the steps given either in the normal mode or Recovery Mode, and remember that the steps from step 3 **must** be done in the new kernel, otherwise it may not work, it is recommended that you do the full procedure in the new kernel to reduce the chances of problems.

---

### Post by K4P741N KRUNCH on 2007-11-28
Thats the thing though, I already have the new kernel installed and I just installed the nvidia-glx-new package for it, but since then I can't get it to boot!

---

### Post by PmDematagoda on 2007-11-28
Could you be more specific, what do you mean by "I can't get it to boot!"?

---

### Post by K4P741N KRUNCH on 2007-11-28
Here, I know its probably hard to see but it was in the initial post

It gets past all the initial scripts, it then goes to a blinking cursor, finally the blinking cursor stops, it looks as though X is about to start, theres one final blink on my hard drive activity, then nothing.

---

### Post by PmDematagoda on 2007-11-28
Remove the nvidia-glx-new package and install the Nvidia driver manually as I suggested in my first post.

---

### Post by K4P741N KRUNCH on 2007-11-29
Yeah, I was trying to do that for a while, but I still couldn't load linux with the new kernel, it wouldn't even get me to a terminal screen.

What I did was edit the command line in grub and removed 'splash vga=792'
And then it loaded fine and I used Envy to uninstall the old driver and when I started the desktop it automatically asked me to get the new driver from Nvidia, so I did, and now I'm fine!

Thanks for your help!

---

### Post by PmDematagoda on 2007-11-29
Nice to hear you solved the problem yourself, good job=D>.

---

