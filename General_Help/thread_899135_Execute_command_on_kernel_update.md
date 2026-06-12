---
title: "Execute command on kernel update"
date: 2008-08-24
forum: General Help
---

### Post by niccholaspage on 2008-08-24
Hey Guys.Well I followed the guide here:[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

To setup my Wireless connection on this Toshiba Laptop instead of using ndisgtk.Now At the bottom of the page it says this:
> 
(Note: For users that experience kernel updates that result in broken wireless. This is a simple repair. I thought it needed to be added to the page simply due to the frequency that we seem to get them :~)
```

cd /wifi
sudo ./makedrv
sudo ./wlan0up

```


Instead of having to run that these commands every time (or most of the time) is there any way to some how automatically run them when the kernel upgrades?

---

### Post by bthoward on 2008-08-24
The only quick way I can think off off hand is to have a script that runs at boot time that writes your current kernel version to a file and in the event that the latest received kernel version does not match the last saved value run a set of commands.  This would require a reboot (but so does upgrading the kernel) :)

---

### Post by bthoward on 2008-08-24
I'd use the uname -r command and just save that away.

---

### Post by niccholaspage on 2008-08-24
That was what I was thinking of...But I cannot do any linux shell scripting...
EDIT:even after that useful command I cannot script...

---

### Post by bthoward on 2008-08-24
Well let me see if I can figure it out...  You going to be around for a bit?

---

### Post by bthoward on 2008-08-24
Well I see you finally got sick of waiting for me... I don't blame you I was a bit slow on this one...  Most of the code I write is in HDL languages so it took me a bit as I've not really ever written a bash script at all and had to figure it all out online for ya....

Anyway here is a good start.

```
#!/bin/bash
if [ ! -f ~/.kernelver ]; then
        uname -r > ~/.kernelver
fi
if grep -q `uname -r` ~/.kernelver;
then
        echo Kernel is unchanged
else
        cd /wifi
        sudo ./makedrv
        sudo ./wlan0up
fi

uname -r > ~/.kernelver

```



So anyway if you paste that into a file called newKern.sh and then run chmod +x ./newKern.sh then you can run that and it will do what you want.  Then you can add that to your rc.local so that its run at boot up.  

I think I may actually use this on my machine as if you're using virtualbox you have to recompile the virutalbox modules every time you install a new kernel.  Until now that happened so unregularly that I just did it by hand.  But heck now that I've put in the time I may as well use it.

Thanks for the fun project!

---

### Post by niccholaspage on 2008-08-24
Thank you and your welcome:P Oh and is this rc.local right?
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/wifi/wlan0up
ifconfig wlan0 up
dhclient wlan0
./newKern.sh

exit 0

```

---

### Post by bthoward on 2008-08-24
Yea that should work for you.  Easiest way to test it is to run newKern.sh and then go in and edit ~/.kernelver lower the number by 1 or something...  Then run newKern.sh and it should run your commands.

That was a fun one.  I decided to spend the night in the forum working on earning some thanks clicks and ended up having a bit fo fun on this one.

---

### Post by bthoward on 2008-08-24
Another thing you may add is if you're running virtual box to put /etc/init.d/vboxdrv start into your newKern.sh.  This will make the modules that Virtual box needs recompiled on a kernel change appear automatically after a new kernel.

---

