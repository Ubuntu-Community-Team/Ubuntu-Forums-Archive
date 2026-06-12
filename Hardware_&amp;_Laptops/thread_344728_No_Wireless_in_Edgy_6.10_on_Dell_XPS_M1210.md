---
title: "No Wireless in Edgy 6.10 on Dell XPS M1210?"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by Yerknutz on 2007-01-23
I own a Dell XPS M1210 laptop. I have been running Dapper 6.06 for a while now and most everything worked fine. After alot of reading etc I decided the Edgy 6.10 upgrade was the next step. I did the built in Ubuntu upgrade and everything upgraded/installed fine, so it seemed.  After cleanup and rebooting into the new version I noticed that my wireless card LEDs no longer blink, looking for a network, Checking the network settings I see that the OS does not activate the wireless radio so there isn't even an eth1 for me to configure.  I tryed Network Manager, lwconfig etc and it just tells me there is no wireless card.  The Intel Pro Wireless 3945abg does however show up in the Ubuntu Device Manager.  

The wireless radio would activate fine in Dapper 6.06 and I always had a eth1 I could configure.  On a whim I even downloaded Kubuntu Feisty Fawn beta 2, and the wireless worked fine in that as well. So, what's missing in Edgy 6.10 that is in the other versions of Ubuntu that is not activating my wireless radio?  Is there a way for me to get Edgy to use this wireless card correctly or am I doomed to a life of 6.06 or waiting until Feisty is at a more final stage?  I'd really like to use Edgy if possible. Any help will be largely appreciated.

---

### Post by mikewhatever on 2007-01-23
This card works with Edgy, but strangely enough, kernel restricted modules need to be installed first. I'll look fore more specific info...
I'll find it in a minute or two. Meanwhile, try this thread [http://ubuntuforums.org/showthread.php?t=331038&highlight=Wireless+3945](http://ubuntuforums.org/showthread.php?t=331038&highlight=Wireless+3945)
just to make sure the card is detected.
Here it is [http://ubuntuforums.org/showthread.php?t=321045&highlight=Wireless+3945](http://ubuntuforums.org/showthread.php?t=321045&highlight=Wireless+3945)

---

### Post by Yerknutz on 2007-01-23
Thanks Mike. I had read the thread you linked, but the restricted modules got me thinking.  I found the restricted modules packages in Synaptic and got them installed and would you look at that, my wireless radio was active after reboot looking for a connection.  Eth1 shows up in the Networking section etc.

Unfortunately, the restricted modules install forced me to install nvidia-kernel-common and now my 1.0-9746 Nvidia driver is borked.  Any time I try to start the machine in Ubuntu I get the bluecreen crash that that X could not be started blah blah and the only way I can get back to X is if I change my xorg.conf back to "nv" from "nvidia" in the display section.  I have yet to find a way to have restricted modules installed without installing the nvidia-kernel-common.

I am going to keep cranking at it. Would be nice to have updated video drivers running and also have wireless.

---

### Post by mikewhatever on 2007-01-23
Your X must be reconfigured. Try this [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
I really hope it doesn't break something else. :D Did you make sure you've got the right restricted modules installed?
I've just googled for Dell XPS M1210. We have the same graphic card Gefoce 7400 go, so I don't understand why it shouldn't work for you.

---

### Post by Yerknutz on 2007-01-23
Thanks again for the tips Mike. What I realized I was running into was when installing the right restricted pack it was forcing me to install an old version of nvidia-kernel-common along with the madwifi package which I think is what was making my wireless radio finally be active.  Upon doing so, the old nvidia kernel that I was being forced to install was conflicting with the newer driver I had installed and in turn was crashing X.

Try as I might to find madwifi as a seperate install so I could avoid the nvidia-kernel-common install, no luck.  Instead, I removed everything nvidia and then installed nvidia-glx and it's interdependencies from Synaptic.  When I run the nvidia X server settings applet it looks like it is using the newest available driver. So far so good.

---

### Post by Yerknutz on 2007-01-23
Yeah, I spoke too soon. Reboot after I posted my last response and *crash* X server won't load.  It seems the only way I can get to a graphical desktop is if I load "nv" and not "nvidia" but without "nvidia" loaded, I get no 3d accelleration....

Looks like I am either stuck with working video drivers and no wireless, or with working wireless but not so working video drivers.  At this point I think I should probably go back to 6.06 and be happy with it or give up for a bit, It's getting irritating.

---

### Post by mikewhatever on 2007-01-23
I am really sorry you have those problems. If it helps, I got direct rendering with this ```
sudo apt-get install nvidia-glx
``` and no special driver installation

---

### Post by ArCeSiNo on 2007-05-08
Hey...

There's another way to activate the wireless in edgy eft... I have the same situation like you, I don't like to install the restricted-modules package because I had a conflict with the nvidia driver... after of ask to **god**ogle I found this solution...

First be sure that you have loaded the ipw3945 module.. try this command **lsmod | grep ipw3945** you must see something like this:

ipw3945               118816  1
ieee80211              34760  1 ipw3945

If you see this in the terminal means that the kernel loads the ipw3945 module but the problem is that the ipw3945 daemon is missing... you can be sure looking for it in /sbin is a file named ipw3945dXXX (XXX depends of your kernel version).

To get the ipw3945dXXX daemon the easier way is installing the restricted-modules package and copy the daemon installed in /sbin to other place and then uninstall the restricted-modules package. After uninstall the restricted-modules package copy the ipw3945 daemon to /sbin   then reload the module **sudo rmmod ipw3945 && sudo modprobe ipw3945** and check your wireless.

If the wireless still does not work, is because the module don't run the daemon yet... to solve this edit the file /etc/modprobe.d/ipw3945 whit root privileges course... whe you open the file you'll see something like this:

install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; sleep 0.5 ; \
        **/sbin/ipw3945d-$(uname -r)** --quiet
remove  ipw3945 **/sbin/ipw3945d-$(uname -r)** --kill ; \
        /sbin/modprobe -r --ignore-remove ipw3945

check the words in bold? yeah is the daemon... edit it like the daemons filename and then reload the module **sudo rmmod ipw3945 && sudo modprobe ipw3945** finally check your wireless again... Is it working?

This works for me in my xps m1210 laptop... I hope that works for you too... good luck!!!

... sorry for the bad english...

---

