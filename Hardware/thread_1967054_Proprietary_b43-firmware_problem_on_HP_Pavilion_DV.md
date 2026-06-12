---
title: "Proprietary b43-firmware problem on HP Pavilion DV5000"
date: 2012-04-27
forum: Hardware
---

### Post by Flame_Phoenix on 2012-04-27
Hello gentleman, I have a HP Pavilion DV5000 and unfortunately it is literally impossible for me to install or even run any sort of Ubuntu or LiveCD on this machine due to a proprietary firmware problem.

When running the livecd the loading simply freezes and so does everything else. To fix this I decided to run the livecd with "nomodeset" checked. After loading for a few minutes everything got frozen again, but now with the message:
"Didn't find b43-firmare, you must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and follow the instructions." (or something very similar to this).

So, like a good boy I decided to go to the website. However, in order to install the missing firmware I have to install Ubuntu first and to install Ubuntu I need the firmware... Seeing the problem? 
Furthermore, looks like I need an internet connection to install a freaking driver for a WIRELESS ADAPTER!! How can I download the installer, if my wireless adapter need the installer to download the installer!? Arrghhh I guess I am tired, there must be something wrong in this cycle, I am surely miss understanding something or missing something.

So after some frustrating searches I started concluding this version of Ubuntu was terrible, however this bug seems to be around since the dawn of time:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/220223](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/220223)

And many other people have tried to solve it, though not really reaching any decent conclusion:
[http://ubuntuforums.org/archive/index.php/t-859564.html](http://ubuntuforums.org/archive/index.php/t-859564.html)

I even tried finding a version of MiniUbuntu in a command line, but all links seem to be broken and so this search also lead to nowhere.

At this point I was pretty much sure that the task of installing Ubuntu on this machine was something forbidden by the Gods themselves, but then i found this:
[http://ubuntuforums.org/showpost.php?p=10829309&postcount=628](http://ubuntuforums.org/showpost.php?p=10829309&postcount=628)

Meaning that someone, somehow, in a very distant past, managed to install Ubuntu on a HP Pavilion DV5000 and had no problems at all. 

I then made a search and it seems that package firmware-b43-installer was removed from the livecd (source missing :'[).

So, at this point now I am pretty much frustrated and tired... and I have no idea on how to do this. Can someone give me a light on how to install this thing on that wooden machine?

Thanks in advance, Flame_Phoenix.

---

### Post by chili555 on 2012-04-27
You could transfer this on a USB key or similar and then drag and drop it to your desktop. Right-click it and select Extract Here. Then open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```You should be all set.

I hear your frustration and I could explain some subtleties for many paragraphs; however, I assume you simply want it to work. Post back if you need more help.

---

### Post by Flame_Phoenix on 2012-04-27
I totally appreciate your help but I don't understand what to do, mainly for 2 reasons:
1 - The livecd won't even boot, so I don't have a desktop (lol)
2 - The livecd won't boot, so I can't use "sudo".

I am currently running this old laptop on windows XP and it sure makes it heavy. Still Chrome runs and I can surf a little bit. I can download the zip and uncompress it on windows, but I am not sure on what to do next, nor if it will help =(

thanks anyway

---

### Post by chili555 on 2012-04-27
> When running the livecd the loading simply freezes and so does everything else. To fix this I decided to run the livecd with "nomodeset" checked. After loading for a few minutes everything got frozen again, but now with the message:
"Didn't find b43-firmare, you must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and follow the instructions." (or something very similar to this).I think the freezing is coincidental and not caused by b43 firmware. I suggest you check the integrity of the CD before you try to boot. [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The lack of firmware will prevent a Broadcom card from working *after* you've booted. Do you have a Broadcom card?

---

### Post by Flame_Phoenix on 2012-04-27
I tested the CD on two fairly recent computers and it worked like a charm. In this computer however, it just seems to freeze while loading, every single time.
> 
The lack of firmware will prevent a Broadcom card from working after you've booted. Do you have a Broadcom card?
yes I do:
wireless adapter broadcom 802.11b/g
Driver date: 25-08-2009
Version of driver: 5.60.18.9

This information was retrieved using my Windows XP. Really wish I could know what is happening. According to one of the forums the problem is graphical, but I already tried to run the CD with every extra option disabled and I still get the same problem).

---

### Post by westie457 on 2012-04-27
Hi, post #5 in this thread has a work-around for this issue.

[http://ubuntuforums.org/showthread.php?t=1966631](http://ubuntuforums.org/showthread.php?t=1966631)

---

### Post by Flame_Phoenix on 2012-04-27
So I have to access to the kernel command's line and blacklist the driver that I apparently need? Don't take me wrong, but this is seriously messed up...

[s]Anyway, i assume I have to press "Esc" while in the "Try Ubuntu" menu right? How do I get back to the menu after?
[/s]
I will test this right away! Thanks for your time guys! I'll post as soon as I have news.
//===================
How do I really access the kernel command line using a livecd and before loading the system?
I'm guessing I don't...
I'm starting to think I'd be better changing the ISO itself to contain that damn proprietary driver...

---

### Post by MorrisseyJ on 2012-04-28
See post #6 from the above link for a step-by-step solution

---

### Post by MorrisseyJ on 2012-05-01
Not sure if you have this working yet. For detailed instructions see here: [http://ubuntuforums.org/showthread.php?t=1966655](http://ubuntuforums.org/showthread.php?t=1966655)

Again its post #6 that has the detailed solution.

---

### Post by Flame_Phoenix on 2012-05-03
MorrisseyJ,thanks! Your post really helped me!
I was stuck after the shift thing, I didn't know I had to press "e". You are a life saver man!

---

### Post by MorrisseyJ on 2012-05-07
No problem, i had similar problems and am glad to hear that you got this working. 

It would be good if you could mark this thread as 'solved' (top of the page--> 'thread tools' --> 'mark this thread as solved')

---

### Post by Flame_Phoenix on 2012-05-08
Done! 
Once again, Thanks for being awesome and help me!

---

