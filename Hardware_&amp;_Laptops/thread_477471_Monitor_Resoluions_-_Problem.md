---
title: "Monitor Resoluions - Problem"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by pinguino99 on 2007-06-18
Hello everyone, 
I am new to this forum so please be kind with me !
I am moving from fedora to ubuntu, i find it easier to use.
My problem:
I installed feisty on my pc, videocard geforce 5600xt ultra with nvidia-glx-new drivers.
Monitor is crt 17", acer ac711.
In gnome, screen resolution, i can correctly choose resolutions 1280x1024 , 1024x768 and 800x600.
But i cannot chooese exact frequency. For example, monitor supports 1024x768 at 85 hz but in the gnome screen resolution application i only can choose 50-51-52-58-59 hz  (not exactly sure about numers but it is more or less exact).
Same thing (with different frequencies) for all resoluions, lower than the good ones.
This problem makes almost impossible to play opengl games : screen flickers, or black screen etc.
I tried almost everything in xorg.conf : 
specified correct horizontal and vert refresh rates
enabled/disabled  useedi 
enabled/disabled many parameters (composite, addrgbvisuals etc)
reconfigured xorg with dpkg-reconfigure -phigh xserver-xorg  or dpkg-reconfigure -phigh xserver-xorg
and even gnome gconf.
Nothing solved the problem !
Ah, of course i also have problems using compiz/bery, i suppose because wrong monitor frequency.

I accept any suggestion !!
Ah ... in windows everything is ok, so hardware works.
Motherboard is asus a7v8x-x

Thanks to everyone and greetings from Italia !

---

### Post by txgeek on 2007-06-18
I always just edit the conf file directly and restart X

1.  Open a terminal window
2.  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup1
3.  sudo nano -w /etc/X11/xorg.conf
4.  Press CTRL-W to search
5.  Enter Horizsync and press enter
6.  Enter the correct horizontal and vertical sync frequency
7.  Press CTRL-X to save
8.  type exit to exit terminal
9.  Press CTRL-Backspace to restart X

If X refuses to start do the following to put everything back the way it was
1.  Login if you aren't already logged in
2.  sudo cp /etc/X11/xorg.conf.backup1 /etc/X11/xorg.conf
3.  startx to restart X Windows or type reboot to reboot the system

---

### Post by pinguino99 on 2007-06-19
Thanks for the help, i already did those steps you suggested for editing xorg.conf
and for restarting X ...
thanks anyway

---

### Post by scannerdarkly on 2007-06-19
in terminal:

nvidia-settings

---

### Post by pinguino99 on 2007-06-19
i tried also nvidia-settings but the situation is similar, i can set 1024x758 at only 85 hz but 
800x600 max resolution is again 85 hz, and the problem is that when i use glx (mainly in games) after few seconds i get errors like "fnctl operation not permitted", or i cannot use other resolutions in games, or  games quit to ubuntu after some flickering , sometimes hangs the computer and so on. I tried also envy, same problem. I tried to install manually nvidia drivers, i tried to install nvidia-glx and nvidia-glx-new, i tried also after reinstalling ubuntu but problem persists. I suppose the main problem is that gnome is not capable to "see" correct resolutions. I should try other distros maybe, but i like ubuntu and it would be a pity !
Any other suggestion is good.
Thanks
Pinguino

---

### Post by scannerdarkly on 2007-06-20
i don't have any other ideas.  Ubuntu is great.  If you are interested in trying other distro's I suggest Fedora or OpenSuse.  I currently run Ubuntu, Fedora, and OpenSuse on my laptop.  So I would suggest taking a peek at any of those.

---

### Post by bergersau on 2007-06-20
I had a similar problem until I used an online modeline generator found at
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")
to generate a modeline for my monitor.
After I inserted it into my xorg.conf and resetared x all was good.

---

### Post by pinguino99 on 2007-06-21
> **bergersau said:**
> I had a similar problem until I used an online modeline generator found at
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")
to generate a modeline for my monitor.
After I inserted it into my xorg.conf and resetared x all was good.

Ok, thanks a lot i will give it a try.
Which problem you had ?? Wrong choices of frequency in gnome resolutions ??

can i use xtiming just knowing, for example, that i need 800x600 at 100hz or i need to know more infos
about my crt ??

thanks again
pinguino

---

### Post by pinguino99 on 2007-06-25
> **bergersau said:**
> I had a similar problem until I used an online modeline generator found at
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")
to generate a modeline for my monitor.
After I inserted it into my xorg.conf and resetared x all was good.

So ... i tried also the xtiming program for generating modelines.
Unluckily did not work.
I even tried to change monitor and use another similar, a 17" CRT .. same results !!
I even tried to boot the PC with a livecd with nvidia drivers installed (STUX) just for check frequencies and ..
the same !!
I suspect there is something in video card ...
I should try a different monitor (LCD maybe) and see what happens.
The main problems is that opengl / glx applications when try to set a resolution makes flickering monitor or hangs. I changed ATI to NVIDIA just for have good drivers but ...
At this point i suppose no more suggestion from ubuntu gurus ... or a last chance for me ??
Bey and thanks
Pinguino

---

