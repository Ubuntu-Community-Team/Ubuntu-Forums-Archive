---
title: "can't install my network driver"
date: 2009-02-25
forum: Hardware
---

### Post by mongoose_za on 2009-02-25
Hi there,

Just installed Ubuntu 8.04 Hardy Heron and there is no network connectivity. I don't think my network card is installed.
So I've downloaded the drivers from [asus]("http://za.asus.com/")

From the README 
"[I]After the driver installation package is unpacked, type the following
   commands to start the sk98lin driver build process:

   # cd DriverInstall
   # ./install.sh[/I]"

So figured I needed to type in terminal
"[I]mongi@mongi-ubuntu:~$ /home/mongi/Desktop/DriverInstall/install.sh
/home/mongi/Desktop/DriverInstall/install.sh[/I]"

But I get this error
"[I][COLOR="Red"]mongi@mongi-ubuntu:~$ /home/mongi/Desktop/DriverInstall/install.sh
/home/mongi/Desktop/DriverInstall/install.sh: 71: Syntax error: "(" unexpected[/COLOR][/I]"

I also went into Sudo Nautilus and tried to run the install.sh file but nothing happened.

What am I doing wrong? 
Network card is: _Marvell Yukon Gigabit Ethernet Adapter_

Thanks,

---

### Post by ddrichardson on 2009-02-26
There's an error in the script at line 71, an extra (

Post the script, it might be an easy fix.

---

### Post by ProNux on 2009-02-28
> **mongoose_za said:**
> Hi there,

Just installed Ubuntu 8.04 Hardy Heron and there is no network connectivity. I don't think my network card is installed.
So I've downloaded the drivers from [asus]("http://za.asus.com/")

From the README 
"[I]After the driver installation package is unpacked, type the following
   commands to start the sk98lin driver build process:

   # cd DriverInstall
   # ./install.sh[/I]"

So figured I needed to type in terminal
"[I]mongi@mongi-ubuntu:~$ /home/mongi/Desktop/DriverInstall/install.sh
/home/mongi/Desktop/DriverInstall/install.sh[/I]"

But I get this error
"[I][COLOR="Red"]mongi@mongi-ubuntu:~$ /home/mongi/Desktop/DriverInstall/install.sh
/home/mongi/Desktop/DriverInstall/install.sh: 71: Syntax error: "(" unexpected[/COLOR][/I]"

I also went into Sudo Nautilus and tried to run the install.sh file but nothing happened.

What am I doing wrong? 
Network card is: _Marvell Yukon Gigabit Ethernet Adapter_

Thanks,

I think you missed something.  The instruction says

```
./install.sh
```

I think, you missed the DOT (.) before the ./install.sh

---

### Post by ddrichardson on 2009-02-28
The ./ before a command tells the shell to look in the current folder, typing the full qualified path (which he did) does the same thing.  The problem is an extra character (a "(") at line 71!

---

### Post by ddrichardson on 2009-02-28
You need to point us to the file or paste it here because I had a quick look on Asus site and all I can find are kernel packages for _old_ kernels. There's an old thread about the sk98lin module [here]("http://ubuntuforums.org/showthread.php?t=176096") but that was Dapper nearly five years ago. I thought it was now using the sky2 module.

What is the output from the terminal for:
```
ifconfig
```

---

### Post by ProNux on 2009-02-28
> **ddrichardson said:**
> The ./ before a command tells the shell to look in the current folder, typing the full qualified path (which he did) does the same thing.  The problem is an extra character (a "(") at line 71!

Thanks for the info bro....

---

### Post by mongoose_za on 2009-03-01
Hey ddrichardson, thanks for the reply. Ok I'll post the scriopt. But is it the install.sh that u want me to open and look on line 71 or is it another file?
I'll post the ipconfig with the other stuff now. Oh and i looked at the date seems these drivers off the asus stie are from 2006 -__-

---

### Post by mongoose_za on 2009-03-01
Ok so I went to line 71 but seems like that is the method posting the error. I've attached the install-8_41.tar. The install.sh is where the error is I think -_-

Hopefully this will work otherwise I'm going to have to try that How to that you posted earlier which doesn't look easy :-(

---

### Post by ddrichardson on 2009-03-01
Are you _sure_ the network interface isn't loaded or that something else is preventing it from functioning? That module should not need building.

I'll check over the script tonight when I'm on a Linux box and not this forsaken Windows XP machine at work.

---

### Post by mongoose_za on 2009-03-01
Hmm okay so it's working. I checked my Device manager in Windows and got the name of the Network Adaptor which was Atheros 8121 or something like that. 

I then went to [Atheros Communications]("http://partner.atheros.com/Drivers.aspx") and downloaded "AR81Family-linux-v1.0.1.0.tar.gz" because I didnt' trust the ones I got from ASUS. 

I followed the instruction until the "Make Install" which worked but after that I didn't actually understand what I was supposed to do so I just rebooted, and wow, the network is online and I'm posting from within Ubuntu. Yay!

Thanks for your replies and your help.

---

### Post by ddrichardson on 2009-03-02
Good to hear you fixed it!

---

