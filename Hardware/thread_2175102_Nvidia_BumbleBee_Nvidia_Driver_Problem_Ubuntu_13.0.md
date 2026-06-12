---
title: "Nvidia BumbleBee Nvidia Driver Problem Ubuntu 13.04 Desktop"
date: 2013-09-17
forum: Hardware
---

### Post by jonesyp on 2013-09-17
Hi,
I have a Dell laptop with Nvidia and Intel graphics cards.  I have followed the instructions below to install BumbleBee on a clean install of Ubuntu 13.04 32Bit

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) 

After I reboot I go to terminal and type 'optirun firefox'  

Firefox launches but I get this error in the terminal.

**(process:2370): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed**

Would anyone be able to help please?

Many thanks

Peter Jones

---

### Post by dankojoffrey on 2013-09-17
I assume you have nvidia optimus... If you have older PC you don't need bumblebee...

Try uninstalling your drivers and install version 319

```
sudo apt-add-repository ppa:xorg-edgers/ppa

sudo apt-get update


sudo apt-get remove bumblebee-nvidia nvidia-current nvidia-settings


sudo apt-get install bumblebee-nvidia nvidia-319 nvidia-settings-319

```

then edit bumblebee.conf

```
sudo gedit /etc/bumblebee/bumblebee.conf
```

and change the values so they look like this:

```
Driver=**nvidia**
KernelDriver=nvidia-**319**
LibraryPath=/usr/lib/nvidia-**319**:/usr/lib32/nvidia-**319**
XorgModulePath=/usr/lib/nvidia-**319**/xorg,/usr/lib/xorg/modules

```

reboot and run nvidia control panel
```
optirun nvidia-settings -c :8
```

hope it helps... if not post your nvidia card version...

---

### Post by jonesyp on 2013-09-17
Hi,

Many thanks for the quick reply.  The card is an 2GB Nvidia GeForce GT 650M on a recent Dell 17R.  I will give your guidance a go and let you know how I get on.

Are they reasons why the standard install did not work?

Best wishes

---

### Post by jonesyp on 2013-09-17
Hi Again,

Thanks for your help.  I changed the code to:

```
## Section with nouveau driver specific options, only parsed if Driver=nvidia
[driver-nouveau]
KernelDriver=nvidia-319
PMMethod=auto
XorgModulePath=/usr/lib/nvidia-319/xorg,/usr/lib/xorg/modules
```


Can I safely delete the 'CODE][driver-nouveau][/CODE] section from the above code?

Just one other question. When I go Nvidia Settings with:

```
optirun nvidia-settings -c :8
```

The screen shows the display is only 640 x 480 which it most certainly is not.  If I go to settings and displays it correct shows the display at 1920 x 1080 (16:9)

If I do a 'optirun firefox'

I get this error in the terminal still:
```

(process:3028): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
```

I have tried this browser test and I get the same score with and without the optirun command:

[http://ie.microsoft.com/testdrive/Performance/PsychedelicBrowsing/Default.html]("http://ie.microsoft.com/testdrive/Performance/PsychedelicBrowsing/Default.html")


I enclose screen shots of both 

Thanks again for your help.

Peter Jones

[ATTACH=CONFIG]246313[/ATTACH][ATTACH=CONFIG]246314[/ATTACH]

---

### Post by dankojoffrey on 2013-09-17
sorry, I wasn't specific... you edited the section &#8203;about nouveau driver options... that's not right...

so first you edit the section about what driver to choose and change value Driver=nvidia exactly like here:
[FONT=Ubuntu Mono][COLOR=#000000][HTML]# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia[/HTML]Make sure the driver used by bumblebee is nvidia!!! 
Lines with # doesn't matter... they are just comments... important are lines without #...

then at the end of the file there are two sections - section about nvidia driver and section about nouveau driver...

nvidia section looks like this:
[HTML]## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-319
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-319:/usr/lib32/nvidia-319
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-319/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia[/HTML]

then there is a section about nouveau driver... Please correct it and make it look like this:
[HTML]## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau[/HTML]

Make sure this sections of the are correct, then reboot the PC and try running optirun command...[/COLOR][/FONT]

---

### Post by jonesyp on 2013-09-18
Thanks for the detailed reply.  I have run glxgears and can see the difference when I use optirun

The only remaining issue is that Nvidia settings still says 640 x 480. Please see the image on the earlier post.

I have shared the bumblebee.conf file via UbuntuOne

[http://ubuntuone.com/0MKvULuLHt8z4fUdxokOnR](http://ubuntuone.com/0MKvULuLHt8z4fUdxokOnR)

I have to apologise as one of the issues I mentioned 

(process:2370): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed'

Seems to actually be a Firefox issue and nothing to do with this issue:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1160569](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1160569)

Kind regards

Peter

---

### Post by dankojoffrey on 2013-09-18
I looked at your file, the sections about the drivers seems to be fine, but you still haven't changed first section about which driver to select
[HTML]Driver=

change to

Drive=nvidia[/HTML]

see attached screenshot... this will make sure that when you use optirun it's gonna use nvidia driver...

The resolution in your nvidia control center screenshot is not an issue... that's not a resolution of your laptop screen... that setting is only important if you use external monitor...

---

### Post by jonesyp on 2013-09-18
Very many thanks,

Peter

---

### Post by dankojoffrey on 2013-09-18
You're welcome... Glad to help...

---

