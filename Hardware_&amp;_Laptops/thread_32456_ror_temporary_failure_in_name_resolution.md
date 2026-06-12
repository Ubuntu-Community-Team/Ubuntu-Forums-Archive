---
title: "ror: temporary failure in name resolution"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by triskele on 2005-05-07
Well as you might guess I'm having an issue. I've installed Ubuntu just fine, but if I restart my computer I get the following error message in the boot dialogue:

"ror: temporary failure in name resolution"

It's obviously something to do with X because when X starts I get a black screen. I can log in via gdm blind but the desktop is useless if I can't see it. I've tried booting in rescue mode or whtever it is to boot to a command line, and type "vga=771" and then "gdm", but that doesn't work either. I really need help here because I really like Ubuntu and I'd hate to have to abandon it. I've installed twice now and I really don't want to have to do it again, although I'm almost positive that'll get me back where I am now. Thanks.

---

### Post by dave9191 on 2005-05-07
Thats an error to do with networking. I get it all the time cause my network doesnt get configured at boot time and ubunut tries to sync the clock online. And it cant look up the hostname of the clock server in nameserver because its not been configured. Im guessing thats the same reason on your computer, no network configured, cant sync clock online. 

As for the screen being blank.. maybe its a driver issue or something. Im not sure that I can help with that tho.

---

### Post by triskele on 2005-05-07
Ok, well if it's a driver issue then why does Ubuntu boot up just fine the first time after then install and then boot to a blank screen after that?

---

### Post by dave9191 on 2005-05-07
Maybe it uses a different driver during the install? Or maybe its just something in the X config files. Did you download any updates after you installed it?

---

### Post by triskele on 2005-05-07
I just installed a 3rd time, and immediately upon booting into the desktop I restarted. SAME BLACK SCREEN!!! I'd really like to know what's wrong here and how I can fix it. Someone please help me.

---

### Post by triskele on 2005-05-08
I found something that might be of use in the wiki page. I'll give it a try tonight and let you all know how it goes.

---

### Post by dave9191 on 2005-05-08
I dont think that installing it over and over is going to make any difference. And I am a little confused, do you ever get into the desktop after the install or has it always been blank, or is it blank after you restart after the install? 

Because if you have never been able to see anything once the X server started it could well be a driver issue or a bad X config. 

Have you ever updated the install? If not try updating it. 

Dave

---

### Post by blueplazma on 2005-05-08
The problem you're probably experiencing is that the loopback (lo) interface isn't being brought up when your network fails to come up. The next time you have this problem, try logging into the console and execute ```
sudo ifconfig lo up 127.0.0.1
sudo /etc/init.d/gdm restart
```
X should start up and you should be ready to go, albeit, you will lack external network connections.

---

### Post by triskele on 2005-05-08
To clear up any confusion here's what happens. I install Ubuntu, it ejects the CD, I restart my computer, finish the instalation, now if I restart my computer after this the screen is black. I'm gonna try this loopback thing and one other thing I found on the wiki page and see if that works.

---

### Post by triskele on 2005-05-08
Well I tried the loopback thing and reconfiguring X via "dpkg-reconfigure xserver-xorg" and that didn't work. I had it auto configure everything and left it all as is. I don't know the exact parameters for my monitor (14" dell laptop display) so I'm staying away from the advanced setup. If someone can tell me exactly what to do I'll try it, but until then I dunno waht to do.

---

### Post by fragmented_user on 2005-07-06
Re: Boots to black screen!!!!

[QUOTE=triskele]Well as you might guess I'm having an issue. I've installed Ubuntu just fine, but if I restart my computer I get the following error message in the boot dialogue:

"ror: temporary failure in name resolution"

It's obviously something to do with X because when X starts I get a black screen. I can log in via gdm blind but the desktop is useless if I can't see it. I've tried booting in rescue mode or whtever it is to boot to a command line,. I really need help here because I really like Ubuntu and I'd hate to have to abandon it....[/QUOTE]

Not Only that but I also receive an erorr when booting "... ACPI: Unable to locate RSDP " which I'm being told, means that I don't have ACPI but rather APM or something like that.

I would greatly appreciate if someone would asisst me to resolve both issues 
1(name resolution-error message) 2 (unable to locate RSDP-error message)

Thanks in Advance
Y.H. :)

---

### Post by varunus on 2005-07-06
triskele:

Try booting Ubuntu in recovery mode, opening up your /etc/X11/xorg.conf file with nano, and changing your graphics driver to "vesa".  It will be in the device section, it'll look something like:

Driver  "something"

change to

Driver  "vesa"

Then try to reboot.  Does this bring up the graphical login?

Also, try changing the DefaultDepth line to 16 instead of 24 (some cards can't support 24-bit color)

the ror error, don't worry about it.  I get it all the time if my ethernet isn't plugged in when I boot.

fragmented:
Don't worry about either error.  Ubuntu tries to load both ACPI and APM, and if only one is successful, the other outputs an error.  I get APM errors every time I boot up, but my computer still works with ACPI.

---

