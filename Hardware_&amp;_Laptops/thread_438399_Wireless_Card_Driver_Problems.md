---
title: "Wireless Card Driver Problems"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by asonetuh on 2007-05-09
I'm new to Ubuntu, and have just installed version 7.04 on my Dell Inspiron 1150 laptop. I am unable to use the wireless card (Dell Wireless 1350 WLAN Mini-pc), however. I have tried using ndiswrapper, but have not been successful. When I attempt to install ndiswrapper using the packaged instructions, I receive error messages when using the commands 'make file' and 'make install'. 

Any help would be appreciated.
Many thanks,
Asonetuh

---

### Post by ghostboy on 2007-05-09
Check out this website [http://www.linux.com/article.pl?sid=06/09/05/2055232]("http://www.linux.com/article.pl?sid=06/09/05/2055232") they have a pretty good tutorial in how to make the wireless card work in Ubuntu.  If that doesnt work, I would search this site for any support regarding that specific wireless card.

---

### Post by Rescue9 on 2007-05-12
First don't build ndiswrapper, use the package.

Second, you may have to blacklist the bcm43xx driver from the kernel.

---

### Post by eprench on 2007-05-15
hey, im having the exact same problem, however, I have not even tried ndiswrapper, I have less experience than this dude. I have used ubuntu before on my old laptop and loved it though. Can someone put down some step by step -baby step instructions?

Thanks!

---

### Post by Rescue9 on 2007-05-15
Ok... I'm doing this from memory, so bear with me. Also, please note that the card I have is a Truemobile 1450, but I believe the procedure should be the same. Also, please note that a good majority of this information came from this page: [http://ubuntuforums.org/showthread.php?t=340689&highlight=ndiswrapper+4306]("http://ubuntuforums.org/showthread.php?t=340689&highlight=ndiswrapper+4306")

First, use synaptic package manager to get ndiswrapper-common and ndiswrapper-utils.

Then remove the bcm44xx module and blacklist it:
```
sudo modprobe -r bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

Now, for me, I had the Dell drivers on my windoze partition, so I just copied over the files. If you don't have the correct Truemobile drivers, you'll have to search them out for your card.

You will need the following files: bcm43xx.cat, bcmwl5.inf, and bcmwl5.sys. If your drivers are different, you will need the appropriate files, just make sure you have a .cat, .inf, and .sys file.

Now, we'll "install" the drivers into ndiswrapper.
```
sudo ndiswrapper -i bcmwl5.inf
```

After that we can load the ndiswrapper module and test it out:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

Then we'll add the ndiswrapper module to the modules dir to make sure it autostarts on boot. 
NOTE: The link above has instructions on renaming your interface to wlan instead of eth. This isn't necessary, but does help out a bit if you have multiple interfaces.

```
sudo nano /etc/modprobe.d/ndiswrapper
```

That should get the driver up and running. If you have problems, check the above link first. If that doesn't seem to help, repost.

---

