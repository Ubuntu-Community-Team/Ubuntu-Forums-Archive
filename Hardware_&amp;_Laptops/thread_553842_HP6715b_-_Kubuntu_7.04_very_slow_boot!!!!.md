---
title: "HP6715b - Kubuntu 7.04 very slow boot!!!!"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by miro_braun on 2007-09-18
HI, as the title says i have HP 6715b laptop and i have installed on it Kubuntu 7.04. 

I had some problems during/after th installation with graphic card drivers...(X server didn't want to load..).. but I managed to solve this with help from this forum.. I used live cd..deleted quiet splash from boot menu and when installation stopped i jumped to terminal (just pressed enter...) and did this:

$sudo -s
$killall kdm
$apt-get install xorg-driver-fglrx
$depmod -a
$aticonfig --initial
$kdm start

After that, X started and i saw login screen - ales gut.. i run the installation, everything did well, rebooted and the same stuf happened.. i did everything the same and it worked..and laptop works now..(also there were problems with wireless but i soved it - help on this forum..)..

But..lets get to the main issue: it all works, it's all fine **_BUT_** time to boot up is ***very very very very long.***.. I run live cd on desktop computer and it booted up in less than a minute.. On my laptop it takes more than five minutes.. :'(:'(

Can anybody help me with this ????????? Please!!

---

### Post by EXCiD3 on 2007-09-18
Have you tried a fresh install? Another thing you could try is tweaking feisty. I found this page VERY helpful in tweaking Feisty: [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/)
Using that guide I am able to boot in 25 seconds.
 
I would think it has something to do with loading the ATI graphics driver that is causing the slowdown.

---

### Post by Linicks on 2007-09-18
I think the issue is here determining what is hanging out at boot - as you say it all works great once up.

Usually boot hangs like this are something trying to resolve an address via DNS of the like (sendmail used to be notorious for this), so we need to see what the boot process is doing, and where it gets stuck.

It could also be fsck doing something too (but why?) and checking disk[s] each boot for some reason.

So, in /boot/grub/menu.lst locate the'kernel' line, and remove the 'quiet, splash' options at the end.

Then your system will boot in text mode, and you will see (or hopefully see) what it hangs on (or what it is doing) as it boots.

Remember, you need to edit the file as root, and ensure you make a back-up/do it right, as you can hose the system easily.

Nick

---

### Post by miro_braun on 2007-09-19
As I recall, boot process halted for a while at line that says something about loading USB drivers... something like this: USB 3 -0 ... I'll look it up and paste it here.... 

But, it suprised me, because, i had Ubuntu 6.0 installed on my laptop, and worked ok (without wireless..)..  I didn't install graphic drivers in a same way.. I installed ubutu with alternate installation (wich btw took about 5h...), and run it.. when the X server didn't want to load, I went to terminal, mnounted CD with ati drivers, copyed drivers to /home/username ,  and installed drivers.. after that i rebooted my comp. It booted up normaly and everything was ok.. Boot proces took about 1 min.. 

That way of installing graphic drivers didn't work on version 7.04.. I don't know why.. 

And, when i dont't delete quiet splash int boot menu, the blue bar shows, make some progress nad then disappear and i see text massagess like :

Loading restricted drivers.                                              [OK]

Ubuntu 6.10 didn't do that.. the bar made all it's progress and the X server started... and it was all ok.. and took about a minute...

?????? - me confused.. I'll paste menu.lst in next post..

Cheers!!

---

### Post by miro_braun on 2007-09-19
Here's my bootchart.. so if anyone have any idea please tell..

---

