---
title: "can't install on asus p5gz-mx"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by uribank on 2009-04-01
Hello i gave this mother (fuc****) board
and i can't install ubuntu or any other linux
dis on it
i have nvidia geforce 8800 install in adition.

intel core 2 due E6400
asus p5gz-mx mother board

i want to install using wubi on my second H.D
even live CD won't work, i've tried many times

can anyone please help me ? 
and please in plain English even a new user like me can understand

thanks
Uri

---

### Post by dandnsmith on 2009-04-01
OK, so you cannot install some things.
Can you describe at least some of the errors - at the moment you just say it fails, stipulating no reason.

Typically, I will try several liveCDs of distros to see if some work on the hardware, and not others. If I find one which works, and looks OK, then I try that (for a start).

---

### Post by uribank on 2009-04-01
none of the distribution works
i can't tell the problem because i keep getting different errors
if working in non verbose mode the bar get stuck on the lower third and stays that way.
i read somewhere it has got something to do with dual graphic card
tell me if there is anyway i can upload the error report

thanks

---

### Post by uribank on 2009-04-01
[http://ubuntuforums.org/showthread.php?t=766219&highlight=asus+p5gz-mx](http://ubuntuforums.org/showthread.php?t=766219&highlight=asus+p5gz-mx)

can anyone explain if this got anything to do and how to solve the problem?
thanks

---

### Post by dandnsmith on 2009-04-03
If you too have an onboard graphics chipset as well as a graphics card, or 2 graphics cards, then you need to disable the on-board or one of the 2 to get things to work for the install.
Then, when the install has worked, you can operate on the xorg.conf, as indicated, to include the second graphics facility.

---

### Post by uribank on 2009-04-03
i've tried disabling the on-board it still did not install

---

### Post by slushpuppisan on 2009-08-05
I'm having a similar problem with the same motherboard and a GeForce 7300 video card. I managed to install Jaunty after physically removing the video card, as described in the posts linked to above. I'm a little antsy about reinstalling the video card, for two main reasons:

1. When I have tried to disable the onboard graphics in BIOS, it re-enables when the computer restarts (since it restarts when I save, I mean basically right away). Is there a way to really disable it? Is this really necessary or would blacklisting the intel drivers work just as well?

2. The driver information given in the posts that are linked to above is for previous versions. What's the best driver to use now? Do I need to download it ahead of time (I don't have an internet connection to that computer at the moment)? 

I'm thinking of trying to blacklist the Intel drivers and then just rebooting with the card installed and see if Ubuntu can figure out what drivers to use. I'll probably be posting again soon about how that didn't work.

---

### Post by slushpuppisan on 2009-08-05
Blacklisting the intel drivers worked! I probably still have the wrong settings for the video card but it is now at least functional. Problem postponed.

---

### Post by spoonyx on 2009-09-01
I have the same problem. I will try to blacklist the module... but... can anyone tell me the name of the module and if it's possible to blacklist a module at boot time, passing an argument to the kernel.

Thanks in advance :)

---

### Post by slushpuppisan on 2009-09-15
To blacklist, you want to open /etc/modprobe.d/blacklist and add the lines:

[FONT=Courier New]blacklist agpgart
     blacklist intel_agp

For more in-depth instructions, check out [http://ubuntuforums.org/showthread.php?t=406205](http://ubuntuforums.org/showthread.php?t=406205) (but note the typo: it's agpgart not agpart)

I'm a major newb to linux, so I generally don't tell the kernel what to do; if anything I think it would instruct me. From everything I read, and I did search, there doesn't seem to be anyway to blacklist the drivers at start-up, although I agree it would make life a lot easier.

Good luck! Oh, and heads up: When I first installed Jaunty I had a lot of problems with the system hanging at random times. Updates seem to have fixed this since then, with no intelligent intervention on my part.
[/FONT]

---

