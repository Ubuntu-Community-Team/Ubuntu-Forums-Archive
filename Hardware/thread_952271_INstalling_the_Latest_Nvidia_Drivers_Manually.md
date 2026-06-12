---
title: "INstalling the Latest Nvidia Drivers Manually"
date: 2008-10-19
forum: Hardware
---

### Post by jasonbrisbane on 2008-10-19
Hi,

After much frustration I have finally managed to update my Ubuntu 8.04 with the latest drivers from the Nvidia website and thought I'd post my success here.


Firstly download the NVIDIA drivers file from [http://www.nvidia.com](http://www.nvidia.com).

Next open synaptic package manager and  remove all nvidia drivers (excluding nvidia-kernal-common, which has to remain).

Next Press CTRL-ALT-F1 to get to a text console.
Log in.
Run:

> sudo killall gdm

then do a:
>  ps -ax | pg

and find what the process number of X is (if one is still running - mine was).

If you see X running then:

> sudo kill -9 xxxx
(where xxxx is the process number).

No cd to the directory where you downloaded the  Nvidia driver to and :

> sudo sh NVIDIA<tab>
(hitting tab will autocomplete the filename).

The install program will run and allow it to do whatever it wants.

Once it finishes, type:
> sudo gdm

and wait for the gdm login screen to start.
You should see an Nvidia logo splash on the screen,. if you do, the you know that your away!

The only issue I have is that /etc/X11/xorg.conf is overwritten each time I reboot, so I've modified the gdm startup program to auto copy the correct file to xorg.conf like so:

> # overwrite the current xorg.conf with the correct one for my Laptop
if [ -e /etc/X11/xorg.conf.darkeen ]; then
	echo "your_root_pwd" | sudo | cp /etc/X11/xorg.conf.myvalidconf /etc/X11/xorg.conf
fi



Yes, inserting the root password isnt good but I'm not a coding genius and dont know Linux enough to know how to get the system to auto-remember the xorg.conf.

If anyone knows why the xorg gets overwritten then I'd be grateful if you post the answer here.

Also, The latest driver appears to make the fan start and stop all the time (temperature sensitive maybe?)

Thanks.

---

