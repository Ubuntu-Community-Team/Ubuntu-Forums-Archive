---
title: "Installing nVidea Drivers"
date: 2014-12-12
forum: Hardware
---

### Post by emayayess on 2014-12-12
I believe my current ubuntuy installation is running with default drivers since even scrolling a page flickers. So i need help installing nVidea drivers. 

I ran following command and here is the result of this command

```

lspci -v | grep -i VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310] (rev a2) (prog-if 00 [VGA controller])

```

Based on this, I went to on to NVIDIA and downloaded 300 series drivers for linux 64 bit which had a .run extension. But when i tried executing it, it never ran. 

So now i don't know what to do. Am i installing the right driver ? if yes then how to install it properly. 

Thanks

---

### Post by ajgreeny on 2014-12-12
Try **Additional Drivers** utility from the menus first rather than going direct to nvidia.

---

### Post by oldfred on 2014-12-12
+1 on ajgreeny's suggestion.

If it did install anything, you must purge before installing from Ubuntu repository. 
They create conflicts and cause all sorts of issues. 

And if you install the nVidia driver from nVidia you have to reconfigure it on every kernel update as it is not registered. Always better to use repository unless you have an extremely new card/chip and driver in repository does not support it.

sudo lshw -c display
Under configuration it still should say this if nVidia not installed:
configuration: driver=nouveau

---

### Post by pqwoerituytrueiwoq on 2014-12-12
for a card that old i would suggest probably the legacy 304 driver

---

### Post by deadflowr on 2014-12-12
For what it's worth, and for the record I agree with the above posts about using the Additional Drivers method, I think you needed to mark the .run file for execution before trying to run it.
As well as you need to run the file without Ubuntu's desktop running.
Simple method would be
Press ctrl+alt+F1
Enter your username and password in the full screen terminal window that you should now see.
Kill X, the display server that runs the graphical desktop.
```
sudo stop lightdm
```
Make sure the file is executable
```
chmod +x /path/to/file.run
```
Run the file
When it finishes running and is installed, I would reboot from here
```
sudo reboot
```
since any changes won't happen for it until you reboot the system. Ne need to restart the display server if all you are going to do is load the old driver.

As stated, though, much easier to use the Ubuntu driver installer...

---

### Post by Yellow Pasque on 2014-12-12
TL;DR version: use the 340.xx driver from this PPA: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

@deadflowr, I wouldn't recommend anyone to install the nvidia driver not using a .deb package (and if I did, I would make sure they had the **dkms** package installed first ;) ). I guess there might be exceptions, like if someone wants to try a super-new beta that hasn't been packaged yet, but overall, it seems like a bad idea to me.

> for a card that old i would suggest probably the legacy 304 driver 
It's not THAT old. I have an 8400GS and run the 340.xx series, which is the legacy driver for 8000-GT300 cards. That's what I'd suggest to the OP.

> Try Additional Drivers utility from the menus first rather than going direct to nvidia. 
Normally, that's best. The only reason I recommend using this PPA instead is because Ubuntu is way behind on keeping the Nvidia driver up-to-date. [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by deadflowr on 2014-12-12
> **Temüjin said:**
> 
@deadflowr, I wouldn't recommend anyone to install the nvidia driver not using a .deb package (and if I did, I would make sure they had the **dkms** package installed first ;) ). I guess there might be exceptions, like if someone wants to try a super-new beta that hasn't been packaged yet, but overall, it seems like a bad idea to me.


Yeah, I'm not recommending anyone do it that way either, just how you would do it.
And needing to install additional packages like dkms, just adds to the reasons why not to do it that way.

---

