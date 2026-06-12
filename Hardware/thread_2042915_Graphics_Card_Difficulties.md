---
title: "Graphics Card Difficulties"
date: 2012-08-15
forum: Hardware
---

### Post by Herakleios on 2012-08-15
Hello Ubuntu community. Now I'm not normally one for asking for help, but I've recently encountered a problem that many hours of messing around and internet searches have been unable to fix, so I now come too you.

I own a Dell Dimension E310 desktop computer that I've had for years. Recently it was beginning to slow down, so in order to try and fix the problem I installed Ubuntu and invested in a number of hardware upgrades.

First I must say that installing Ubuntu on this computer was the best thing I've ever done. It runs far more smoothly now, in fact I'd even venture to say that it operates faster now than it did when I first got it 6 or 7 years ago. I didn't have any issues with the initial install, nor did I have problems with the new memory I added, the new SATA hard drives, or the new disk drive.

However, I was not so lucky with the graphics card. As many of you may know, the Dimension series is not very customizable. There are only a very small number of graphics cards that function with the motherboard, and the one I ultimately selected was the Jaton VIDEO-338PCI-DVI GeForce 6200 256MB (256 MB) PCI Graphics Card.

Now immediately after inserting the graphics card into a PCI slot and hooking the monitor up to it, the computer failed to boot. After failing it automatically rebooted and gave me the option to boot Ubuntu in safe mode. I did so, and it went through the recovery process before asking if I wanted to resume a normal boot. I did so, and the computer booted without fail.

I immediately accessed the additional drivers menu and installed the recommended nVIDIA graphics driver, after which I was prompted to reboot my machine. However, after doing so the computer once again failed to boot and prompted me to boot in safe mode. This time, however, when I tried to boot it in this mode, after accepting the prompt to resume normal boot, my computer freezes on a blank image of my desktop. The wallpaper is visible, and there is a darkened area along the top where the task bar should be, but the GUI is not fully loaded and I cannot use any of it.

At the moment I am using the computer, but I modified the BIOS not to recognize the graphics card and to use the dedicated 8mb of graphics memory on the CPU to allow me to actually use the computer.

It is not a big deal to me, although I spent a bit of money on the graphics card it wasn't a requirement--merely a luxury. All the same, I would love to be able to resolve this problem and actually use the card.

If you require any additional system specs that I did not list, please you need only ask and I will provide them. As I've said, I spent numerous hours searching the web for a solution, but found none that worked (or at least none that I was able to successfully implement), so any help would be greatly appreciated.

Thank you,
Herakleios

---

### Post by NcScZ on 2012-08-15
I had a similar problem in adding a 2nd monitor. I was able to get a working solution by:

When the system gets to the point that you can see the wallpaper, use the CTRL/ALT/F1 combination to get to a command line login. 

Login and use the "nvidia-xconfig" command line tools to get a low resolution setting that would allow the system to boot. It took several experiments to work through all the options. After I got a working desktop I was able to the use the "nvidia X server settings" program.

---

### Post by Claus7 on 2012-08-15
Hello,

I think that the problem can be resolved by creating a xorg.conf file which will give to your graphics card all the info it needs in order for your system to boot normally. 

You can check this thread:
[http://ubuntuforums.org/showthread.php?t=1685186&highlight=6200+nvidia](http://ubuntuforums.org/showthread.php?t=1685186&highlight=6200+nvidia)

in which it seems that there is a similar card to your own and a xorg.conf file which actually works.

You might have to make some modifications since the monitor and some other things are not the same as yours. Check especially the section under "screen".
edit: This took place in a desktop computer, I hope that this will do the work for you as well.

Hope that this helps,
Regards!

---

### Post by Herakleios on 2012-08-15
Thank you both so much for the help, I've finally gotten the card working properly.

As it turns out, the issue was in my driver selection. I installed the current version of the driver from the additional drivers utility at the start of all of this. Thanks to NcScZ's information on booting to the command line (a feature I was completely ignorant of) I was able to just jockey-text to change the driver to the older version (173 I think) as an experiment. And it magically worked when I rebooted my system (though I still need to boot in recovery mode initially, fixing that is my next step I guess).

Once again thank you both, you've really helped me figure out how to fix this problem. I am a bit interested as to why the newer version of the driver didn't work though, could it simply be because my graphics card is so old?

---

### Post by Claus7 on 2012-08-23
Hello,

> **Herakleios said:**
> Thank you both so much for the help, I've finally gotten the card working properly.

As it turns out, the issue was in my driver selection. I installed the current version of the driver from the additional drivers utility at the start of all of this. Thanks to NcScZ's information on booting to the command line (a feature I was completely ignorant of) I was able to just jockey-text to change the driver to the older version (173 I think) as an experiment. And it magically worked when I rebooted my system (though I still need to boot in recovery mode initially, fixing that is my next step I guess).

Once again thank you both, you've really helped me figure out how to fix this problem. I am a bit interested as to why the newer version of the driver didn't work though, could it simply be because my graphics card is so old?

glad you were able to solve your problem. If I understand correctly your question about "old" and "new" drivers this is my response:

in the repositories you will be able to find a selection of drivers about nvidia graphics cards. Some characteristic numbers are 96, 173, 185.

All these correspond to different groups of cards. Some older cards use the 96 version of drivers, which does not necessarily mean that the drivers themselves are old. It is a necessity to pick up the right number which will support your specific gpu.

One way to find out is going to synaptic, choosing nvidia-xx, where xx stands for the number 96 and the like and see if this number includes your card. 

Sometimes, from update to update (of the driver) it might be that is buggy so either you have to stick with what you had or to wait for a new update.

Good ubuntu-ing,
Regards!

---

