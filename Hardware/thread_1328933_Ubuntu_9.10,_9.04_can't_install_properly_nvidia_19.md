---
title: "Ubuntu 9.10, 9.04 can't install properly nvidia 190.xx driver"
date: 2009-11-16
forum: Hardware
---

### Post by blackened07 on 2009-11-16
hello guys, i'm having this little problem, I just bought this sony laptop
VPCCW17FX, thath comes with nvidia 210m chipset

I tried adding to the /etc/apt/sources.list and installing the driver from the terminal and everything seems to work fine, until y reboot and goes to my log in screen, the screen goes totally to black, like turned off, anyway I tried from system/administration/hardware drivers and enabling the 185, and the 190 driver will do the same thing.

I also tried downloading the driver from de nvidia webpage, and installed, but the same thing, the screen goes totally black, I can log on in my ubuntu, but I can't see a thing.

I'm running ubuntu 9.10 amd 64, ( I also tried in 9.04 i386 ) but the same thing, I don't know how to look for info, since I can't find too many on the net, Obviuously I'm missing sth, but don't have a clue what it is, any help, or tip would be really appreciated

Thanks in advance.

---

### Post by blackened07 on 2009-11-17
i also want to agree that I have tried with the 173 nvidia driver, and obviously didn't work, also de 185.18 that comes with envy, and the same story.

The nvidia card is Geforce g210m 

thanks in advance

---

### Post by jusce on 2009-12-04
i'm having the same problem...

that sucks

---

### Post by Loan_Refi on 2009-12-10
Same problem here;
Sony Vaio VPCCW17FX 
Ubuntu 9.10 64 
After I enabled Nvidia Driver reboot I get a dark screen as if the display was turned off.

Brightness Fn F5 keys do not work. I can't control the brightness setting even if I add the brightness applet.

Now that I have a dark screen is there any way to remove the driver via terminal to get my screen back?

Any help is appreciated

---

### Post by Loan_Refi on 2009-12-10
Okay I attached an external monitor and I got to see my desktop so loged in and disabled the Nvidia Driver, rebooted and now I'm able see my desktop and not connected to my external monitor.

I still can't use Brightness Fn F5 function control and obvious my graphics card drivers are missing.

Help anyone?

---

### Post by shooray on 2009-12-20
I bought SONY VIAO VPCCW100C laptop last week. It takes me more than 5 hours to keep windows 7 and ubuntu 9.10 coexist with each other. But when I install the nvidia driver for Gforce G210m graphic card, I get the same problem with blackened07. Ubuntu goes to black screen.
I visit nvidia official site and download the latest drivers for G200m series linux with x86 64 bits.
However, neither NVIDIA-Linux-x86_64-190.53-pkg2.run nor NVIDIA-Linux-x86_64-190.42-pkg2.run causes same black screen problem.
And as Loan_Refi said, Fn+F5,F6 brightness function key seem to be invalid.

Does anybody help us?...

---

### Post by shooray on 2009-12-20
I find the solution to the problem.
Please visit nV News forum:
[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

What [egghead3]("http://www.nvnews.net/vbulletin/member.php?u=95280") said is right.

---

### Post by shooray on 2009-12-27
Although I have installed nvidia driver for sony vaio VPCCW100C,  I couldn't adjust brightness on ubuntu 9.10.

I've searched related message underneath:
[http://vaioubuntu.wordpress.com/2009/01/07/new-sony-laptop-brightness-control/](http://vaioubuntu.wordpress.com/2009/01/07/new-sony-laptop-brightness-control/)
[http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/](http://vaioubuntu.wordpress.com/2008/12/04/finally-a-brightness-how-to-for-vaio-fw-series/)
[http://bugzilla.kernel.org/show_bug.cgi?id=11682#c1](http://bugzilla.kernel.org/show_bug.cgi?id=11682#c1)
[http://bugzilla.kernel.org/show_bug.cgi?id=10950](http://bugzilla.kernel.org/show_bug.cgi?id=10950)

Can anybody tell me how to resolved brightness control problem for vaio cw series? It' too hard for me.

---

### Post by blackened07 on 2010-02-11
> **shooray said:**
> I find the solution to the problem.
Please visit nV News forum:
[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

What [egghead3]("http://www.nvnews.net/vbulletin/member.php?u=95280") said is right.

Yes, that solves it, tested in ubuntu 9.10 amd64, and LinuxMint 8

---

