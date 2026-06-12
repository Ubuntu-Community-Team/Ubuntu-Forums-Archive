---
title: "general question about how drivers work"
date: 2017-03-08
forum: Hardware
---

### Post by jeff666 on 2017-03-08
Ok so i get how loadable modules work in Linux and the process of install a say a driver i wrote myself i would compile it then load the .ko file with insmode (or modeprobe for auto dependencies) then lsmod would show my driver.  (also that manufacturers and dkpg packages have scripts that pass arguments and configure the driver.) What i really don't get is how the os knows about devices, for example lshw why does it know i have wifi card, ethernet port, sound card, etc? On top of that it somehow knows which driver use for each device and loads it at start up?

thanks in advance this is really going to help me understand linux better and get my installs to work better.

---

### Post by TheFu on 2017-03-08
At boot, the OS looks for devices. It searches everywhere. If something is found, it tries to figure out which vender and model it is, then it looks for the most appropriate driver.

**lshw** just looks through the found hardware that the kernel already found. It looks in the pseudo-file systems under /proc/ and /sys/ for the information. [https://linux.die.net/man/1/lshw](https://linux.die.net/man/1/lshw) which is a manpage confirms this.

Not sure if that helps or not.

---

### Post by jeff666 on 2017-03-08
@TheFu ok so theres a hardware scanning program (in kernel) with a data base of info about hardware it compares it and store the data in the kernel, so programs can use it(and i guess so the kernel can use it). So is there a file that the kernel looks in to see what drivers are available then choices the best one based on relevancy. Thanks for the help, although a more detail responses would be great also, none the less appreciated!

---

