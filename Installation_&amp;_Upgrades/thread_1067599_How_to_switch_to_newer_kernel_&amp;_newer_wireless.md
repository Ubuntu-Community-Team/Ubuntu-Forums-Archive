---
title: "How to switch to newer kernel &amp; newer wireless driver?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by TimDaniels on 2009-02-12
`uname -r` tells me that kernel 2.6.24-19-generic is running.  And for some reason, the directory  /lib/modules contains the directories:
2.6.24-19-generic,  2.6.24-21-generic,  2.6.24-23-generic

Currently, the wireless driver doesn't seem to work because the Network Manager dropdown menu doesn't offer a checkbox to enable wireless networking, and the system doesn't see any surrounding wireless networks.  (The dual-booted Vista does wireless just fine, though.)  The Hardware Drivers app shows only the B43 chipset driver to be available, and it lists it as being enabled and in use.  There is also a supposedly better "STA" driver available from Broadcom that is for kernels more recent than 2.6.24-19-generic (see [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)).  I would like to run that STA driver instead of the B43 driver (which apparently has somehow gotten secretly disabled - contrary to what Hardware Drivers says), but to use it, the kernel must be more recent than the 2.6.24-19-generic kernel that is running.

So how should I go about dumping the B43 driver, switching from the 2.6.24-19-generic kernel to a more recent kernel, and then getting the Broadcom STA driver listed as a selection in Hardware Drivers?

*TimDaniels*

---

### Post by mpl34 on 2009-02-12
have you run
```
sudo apt-get update
sudo apt-get upgrade
```

For the STA driver i suggest doing it manually unless you can successfully activate it using your driver manager.

I assume it is the following driver that you will need for your chipset, you may want to make sure it is compatible the driver is given [here]("http://www.broadcom.com/support/802.11/linux_sta.php")

Step 1: Create a directory in your home directory to compile the source:

```
mkdir ~/hybrid
```
(For example)

Step 2: Copy the files you downloaded into the hybrid directory.

Step 3: Change to the hybrid directory to uncompress the file:

```
cd ~/hybrid
```

Step 4: Uncompress the file:

```
tar -xzf hybrid*.tar.gz 
```

Step 5: Just to make sure that the source has not been pre-compiled:

```
make  -C /lib/modules/`uname -r`/build M=`pwd` clean
```


Step 6: Compile the source:

```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

Step 8: Remove any current wireless modules:

```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
```

Step 9: Load the necessary modules:

```
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo modprobe b44
```

Step 10: Restart your network:

```
sudo /etc/init.d/networking restart
```

and you should find it installed and working hope this helps

---

### Post by TimDaniels on 2009-02-12
> **mpl34 said:**
> have you run
Step 5: Just to make sure that the source has not been pre-compiled:

```
make  -C /lib/modules/`uname -r`/build M=`pwd` clean
```


Step 6: Compile the source:

```
make -C /lib/modules/`uname -r`/build M=`pwd`
```


I did everything you listed, and then steps 5) and 6) both reported an error:
make: *** /lib/modules/2.6.24-19-generic/build: No such file or directory. Stop.

*TimDaniels*

---

