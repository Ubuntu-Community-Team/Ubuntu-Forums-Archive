---
title: "Possible to blacklist lp module? Causing 3 minute boot delay!"
date: 2009-04-26
forum: Hardware
---

### Post by Beastie Boy on 2009-04-26
I have a fresh install of Ubuntu 9.04 on an Acer Aspire 9110 laptop. Previous versions of Ubuntu (& derivatives) have been fine, but this one takes forever to boot. Here is an excerpt from dmesg:
```

[ 11.110893] EIP: [<f7fa52c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ES
P 0068:f619bc54
[ 11.110906] ---[ end trace 9bd66193deb28a9c ]---
[ 11.500080] Clocksource tsc unstable (delta = -341257333 ns)
[ 11.588074] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 11.759586] usb 4-2: configuration #1 chosen from 1 choice
[ 11.790916] Bluetooth: Generic Bluetooth USB driver ver 0.3
[ 11.791032] usbcore: registered new interface driver btusb
[ 189.996709] lp: driver loaded but no devices found
[ 190.062114] Adding 506008k swap on /dev/sda5. Priority:-1 extents:1 across:5
06008k
```

As you can see, there is a 3 minute wait whilst the lp module searches for devices. I believe that lp is associated with parallel ports, but I don't have any.
I have created a file called 'blacklist-parallel.conf' and placed it in /etc/modprobe.d. The file contains 3 lines:
```

blacklist lp
blacklist parport
blacklist ppdev
```

but lsmod shows that all 3 modules are loaded.
How can I prevent this 3 minute search at boot? If I am going about it the wrong way, then please advise. Is this a kernel bug perhaps?

Many thanks in advance.

Cheers, Beastie.

---

### Post by oOarthurOo on 2009-04-28
After creating a blacklist file, such as blacklist.local in /etc/modprobe.d/ you need to update the boot image.
```

sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by charliemouse on 2009-05-07
Hi, did this fix work for you?

I'm having the exact same problem with 9.04 and have also tried creating a blacklist file under /etc/modprobe.d/blacklist.conf, where I'm blacklisting lp, ppdev and parport.

I've tried running

sudo dpkg-reconfigure linux-image-$(uname -r)
and have also tried removing them before rebooting (using rmmod) but each time the delay still occurs and when I type lsmod it shows all three have been started.

Can anyone think of anything else I need to try?

Thanks

---

### Post by oOarthurOo on 2009-05-07
Blacklisting only prevents the modules from being loaded at boot time, however, modules may still be loaded via other processes, like HAL if you should plug a device in.

Check to ensure that you have blacklisted the modules correctly. The form is:

```
blacklist pcspkr
```

Then update the initramfs file. A warning message occurs if you do not end the file name in .conf

pcspkr is a good one to test with. Try the following sequence:
```
lsmod | grep pcspkr
```
You should see it pop up in the terminal. Now do:
```
gksudo gedit /etc/modprobe.d/blacklist_custom.conf
```
Then cut and paste this in there:
```
blacklist pcspkr
```
Then update the initramfs by doing:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
Now reboot, the in a terminal do:
```
lsmod | grep pcspkr
```
You shouldn't see anything. However, you can still load it by doing:
```
sudo modprobe pcspkr
```
Now again do:
```
lsmod | grep pcspkr
```
And you should see it once more. However, when you reboot it will not be loaded automatically. 

If you have done this experiment to prove to yourself that this method works, and you are still having problems with blacklisting the modules you desire, then what is likely happening is that the modules are not being loaded by the kernel at boot, but are being loaded by some other process later in the startup, perhaps by HAL or printing or some such.

---

### Post by Beastie Boy on 2009-05-08
To cure the problem, I took the rather drastic step of compiling a new kernel with all modules relating to parallel ports disabled. This has worked for me and I now have no boot delay.
Compiling and installing a custom kernel was much easier than I expected. It can even be automated for the most part. Do a search for KernelChecker.

Hope you cure your problem.

Cheers, Beastie.

---

### Post by oOarthurOo on 2009-05-19
I have the following entries in my blacklist.conf file"
> 
blacklist joydev
blacklist e100
blacklist mii
blacklist serio_raw
blacklist pcspkr
blacklist psmouse
blacklist lp
blacklist parport
After updating my boot image and restarting, only lp and parport are loaded. Something else is loading them during the startup process, likely the printing configuration.

---

### Post by tekstr1der on 2009-06-27
Not nearly as bad as the OP's issue, but ppdev is causing a 7 second delay in my karmic boot. Other than by compiling a custom kernel without lp, ppdev and parport, has anyone had any success in blacklisting them by any other method?

---

### Post by Ayuthia on 2009-06-27
Have you tried blacklisting them and then running:
```
sudo update-initramfs -u
```It will update the boot information so that it knows that it needs to blacklist those items also.

I am not for sure what ppdev does though so I am not for sure what will happen when it is blacklisted.

---

### Post by kerry_s on 2009-06-27
> **tekstr1der said:**
> Not nearly as bad as the OP's issue, but ppdev is causing a 7 second delay in my karmic boot. Other than by compiling a custom kernel without lp, ppdev and parport, has anyone had any success in blacklisting them by any other method?

make sure you don't have cups installed.

---

### Post by lunatico on 2009-07-20
> **kerry_s said:**
> make sure you don't have cups installed.

but if i do this will i still be able to configure/use my network printers?

---

### Post by lunatico on 2009-07-20
> **Ayuthia said:**
> Have you tried blacklisting them and then running:
```
sudo update-initramfs -u
```It will update the boot information so that it knows that it needs to blacklist those items also.

I am not for sure what ppdev does though so I am not for sure what will happen when it is blacklisted.

this didn't work for me... still loading the modules...
is there another way without having to recompile a custom kernel?

---

### Post by pmanski on 2009-11-01
Blacklisting modules lp,ppdev,parport is not enough.
You must also disable loading lp module in default configuration of cups in /etc/default/cups.

```
# blacklist modules
sudo su -c "echo blacklist lp" >> /etc/modprobe.d/blacklist-custom.conf
sudo su -c "echo blacklist ppdev" >> /etc/modprobe.d/blacklist-custom.conf
sudo su -c "echo blacklist parport" >> /etc/modprobe.d/blacklist-custom.conf
sudo dpkg-reconfigure linux-image-$(uname -r)
# disable loading lp module in cups
sudo perl -pi -e 's/LOAD_LP_MODULE=yes/LOAD_LP_MODULE=no/' /etc/default/cups

```

---

### Post by landeel on 2011-04-05
@pmanski

Works!!!

---

