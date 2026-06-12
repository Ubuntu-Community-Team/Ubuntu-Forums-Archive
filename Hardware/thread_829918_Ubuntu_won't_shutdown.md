---
title: "Ubuntu won't shutdown"
date: 2008-06-15
forum: Hardware
---

### Post by sandman2600 on 2008-06-15
Just installed Ubuntu 8.04.  I'm new to linux.  It is installed on a laptop with a pentium II processor and 192 MB RAM.  Everything is fine except for when I shut down the computer.  From the desktop, I click on the "shutdown" button to start the shutdown sequence and instead of shuting down completely, it hangs up at the Ubuntu Logo similar to the logo that appears when you cold boot the computer...

The dvd I used to install Ubuntu had an error in one of the files.  I know this because I used the disk "integrity" checker available while installing Ubuntu.  My initial guess is that the bad file contains code that is part of the shutdown sequence of Ubuntu, which is why Ubuntu won't shutdown...I tried downloading from a location closer to me, and using different ISO burner software, but I always end up with an error in at least one file, when I run the "integrity" checker available at the installation interface...CDs are worse, When I burn CDs the "integrity" checker finds error in at least 20 to 30 files...DVDs seem to work the best...   

On the other hand, the error in that one file (dvd) may not have anything to do with the laptop not shuting down properly.......either way any suggestions would be appreciated for troubleshooting

---

### Post by Arthur Archnix on 2008-06-15
The most likely answer is that Ubuntu isn't communicating with your system's bios or hardware. Usually it means an acpi problem. Try adding kernel options like "irqpoll" or "noacpi" to your next few boots, and see if any of these solve your problem. 

Here's the page with all the options:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Scroll down the section on kernel options.

As a temporary workaround, you can try running from a terminal
```
sudo shutdown -h now
```

---

