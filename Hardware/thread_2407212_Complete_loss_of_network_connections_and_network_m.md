---
title: "Complete loss of network connections and network manager in Ubuntu 18.04"
date: 2018-12-01
forum: Hardware
---

### Post by Keith Myers on 2018-12-01
I have experienced a complete loss of ethernet connectivity because I have lost the network manager software.  No connections showing nor any connectivity apps are available.

I had purged nvidia drivers and reverted to nouveau drivers.  I did an autoremove after that and rebooted.  Now the desktop comes up in nothing but 640 X 480 and windows are unable to be resized.  I use a wired ethernet connection.  No connectivity icon in the title bar. 
ip a produces the ethernet interface as down.  sudo netplan apply produces netplan not found. All the commands to restart the network-manager service fail.

So how to I restore network connectivity to the computer.  I assume I will have to download the software from another computer and the install it via command line from a USB stick.

---

### Post by freemedia2018 on 2018-12-01
Try this. It's old advice, it's what I've always done in this situation. It might not work but it wont hurt anything:

```
sudo dhclient
```

---

### Post by Keith Myers on 2018-12-01
Thanks you are a live saver.  Got ethernet connections back so I could put the nvidia drivers back in and get a proper sized desktop.  Now just have to figure out how to get the network manager icon and app back.

---

### Post by freemedia2018 on 2018-12-01
Oh, I'm glad that still works. Thanks for letting me know, cheers.

As for reinstalling, try 

```
sudo apt-get install network-manager
```

---

### Post by Keith Myers on 2018-12-01
Nah, nothing worked.  I tried for two hours trying to get any website to resolve. Finally threw in the towel and just reinstalled.  Should have done that in the beginning instead of fighting it. Saved my /home directory off disk but still had to spend another 4 hours trying to compile my SIO kernel mode driver and reinstall all the packages that my various applications need. Finally have a working system again to continue crunching.

No idea why something I have done a dozen times before blew up in my face this time.  Thanks for the assistance anyway.

---

