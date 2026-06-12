---
title: "USB not working on Compaq Presario F572US after ndiswrapper"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by raseel on 2007-09-26
Hi,
  I got the wireless on my Compaq Presario F572US working by following the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Its working perfectly fine.

But now, only 1 out of the 3 USB ports works and even that one doesn't work perfectly. 
Here's the output from "lsusb" :
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

But if I unplug the mouse and plug it in again, I get :
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
and I'm forced to use the TouchPad.

This is for  just 1 of the USB ports. The other two ports, don't  even show any "dmesg"  output when plugged.

This has started only AFTER I followed the above link for getting Wifi to work.

Also, I'm sure that the other 2 USB ports were working perfectly fine, so I know its NOT a issue with the hardware ports.

---

### Post by Jonnothin on 2007-09-26
Hey I've got the same problem, my ports only work on the restart and I can't even get my wireless to work even with Ndiswrapper. anyways after the restart they work perfectly if there plugged in while it's starting up, but after a few seconds of setting it stops and if I unplug it and wait for more than about a minute then it doesn't work again and I have to restart.

Is this your problem? Cause this is the problem I have with the same model.

I do appreciate the link though it is exactly what I'm looking for for my wireless card to work

---

### Post by raseel on 2007-09-26
Well, my problem is not EXACTLY the same, but the bottom line is that the USB is not working.
In my case, 2 out of the 3 ports are not working AT ALL. Not even if there are devices plugged into them before booting.

---

### Post by Jonnothin on 2007-09-26
Did they work before Ndiswrapper or did they all work before? Maybe my problem is hardware.

---

### Post by raseel on 2007-09-26
Well, the laptop came with Windos Vista pre-installed and all the ports were working fine then.
After I installed Ubuntu on it, the first thing I did was to get the wireless card working using the ndiswrapper method. 
Never been able to use those USB ports then on.
Maybe I'll revert back to the default configuration by removing ndiswrapper and the other wireless settings.
You don't have ndiswrapper installed yet , right ? So what exactly is the behavious with your USB  ports again ?

---

### Post by Jonnothin on 2007-09-27
I have to reboot with the mouse, flash drive, etc. . . in whatever port, but if I don't then none of them work at all until I reboot again. Plus, if I unplug them then they'll stop running after a minute or so. But your's works all the time right, I mean the only one that works, works all the time.

---

### Post by Ayuthia on 2007-09-27
Are any of you running noapic in your kernel parameters?  If so, that could be the cause of your problem.  You might enter dmesg in a terminal and see if any messages pop up about any interrupts.

Various HP/Compaq laptops have USB problems when running with noapic and the solution varies by model.  For me, I can use noapic noirqdebug and it solves my laptop from locking up during startup and allows me to use my USB ports.  There is also another solution that is escaping my mind right now.

---

### Post by Jonnothin on 2007-10-03
Yes I am running noapic thanks for the tip, I'll check it out. Will it cause any problems or can I just use this command in the terminal without it messing things up?

I don't know about raseel though.

---

### Post by Ayuthia on 2007-10-03
> **Jonnothin said:**
> Yes I am running noapic thanks for the tip, I'll check it out. Will it cause any problems or can I just use this command in the terminal without it messing things up?

I don't know about raseel though.

You will need to update your kernel parameters in /boot/grub/menu.lst file.  You will need to have root access (sudo/gdesu) to change the file.  Just look for noapic and add noirqdebug beside it and that should fix it upon reboot.  Some people have used irqpoll also so you might try that if noirqdebug does not work.

---

### Post by Jonnothin on 2007-10-03
So in a terminal type in /boot/grub/menu.lst file. After that, find noapic and replace it with noirqdebug, then reboot, correct?

---

### Post by Ayuthia on 2007-10-03
> **Jonnothin said:**
> So in a terminal type in /boot/grub/menu.lst file. After that, find noapic and replace it with noirqdebug, then reboot, correct?
You actually want both.  The noapic will help your Compaq to boot and the noirqdebug will handle the USB interrupt issue.

---

### Post by Macyoshary on 2007-10-03
I have a similar problem on a Power Mac G4 I got a couple of days ago. It boots up with yaboot and I press l for linux and enter to boot. When Ubuntu loads though, neither the mouse nor the keyboard works. Sometimes they do work and it seems to increase the likelihood of working if I open the case and stick a huge fan next to it.

---

### Post by Macyoshary on 2007-10-03
Hmm.. when I boot up and it starts loading, once it gets to the 3rd division it stops. If it continues after about 30 seconds the usbs will work, if it waits 5 min before continuing they wont.

---

### Post by Jonnothin on 2007-10-04
IT WORKS! ! ! MY USB PORTS WORK! ! ! raseel you have to try this. You have to do two searches for noapic. After the second search type a space and type the thing in, then reboot like the guy says.

Thanks for your help Ayuthia:guitar:

---

### Post by midknight51 on 2007-10-25
> **Ayuthia said:**
> You will need to update your kernel parameters in /boot/grub/menu.lst file.  You will need to have root access (sudo/gdesu) to change the file.  Just look for noapic and add noirqdebug beside it and that should fix it upon reboot.  Some people have used irqpoll also so you might try that if noirqdebug does not work.

That worked perfectly for my f572us. Thank you for the help! Thumbdrives, mice, and keyboards all work.

---

### Post by southernbase on 2008-02-05
Hi, 

Just as an FYI I'm runnning my super duper $400 laptop... a Compaq Presario C500 with a Broadcom 4311 wireless NIC in it.  I also installed ndiswrapper to get better range from my card and lost my 2 USB ports on the left hand side as a result, but this little gem with the noapic noirqdebug got me back up and running.  Thumbs up, good work and thank you.

---

