---
title: "Issues with Fujitsu Siemens AMILO Li 1718 laptop"
date: 2011-03-29
forum: Hardware
---

### Post by moma on 2011-03-29
Hello,

[COLOR="Red"]EDIT 30.mars.2012:[/COLOR] Solution for Ubuntu 12.04.
Please read: [http://ubuntuforums.org/showpost.php?p=11804328&postcount=9](http://ubuntuforums.org/showpost.php?p=11804328&postcount=9)
------------------------------------------------------------------------

I have an old (Fujitsu Siemens AMILO Li1718 ) laptop that runs Ubuntu 11.04 (Natty) with Unity-desktop.

It has couple of issues that bother me.

1) The wireless network does not start at boot. 
Sometimes this laptop simply forgets to switch the wifi on. Usually the wifi works after a reboot.  These commands helped me to find a solution.

$ [COLOR="DarkGreen"]iwlist scan[/COLOR] 
 lo        Interface doesn't support scanning.
 eth0      Interface doesn't support scanning.
 wlan0     Failed to read scan data : Network is down

$ [COLOR="DarkGreen"]sudo ifconfig wlan0 up[/COLOR]
 SIOCSIFFLAGS: Operation not possible due to RF-kill

$ [COLOR="DarkGreen"]rfkill list[/COLOR]
 0: acer-wireless: Wireless LAN
  	 Soft blocked: yes
 	 Hard blocked: no

 1: phy0: Wireless LAN
	 Soft blocked: yes
	 Hard blocked: no

$ [COLOR="DarkGreen"]rfkill unblock 0[/COLOR]
$ [COLOR="DarkGreen"]rfkill unblock 1[/COLOR]
$ [COLOR="DarkGreen"]sudo ifconfig wlan0 up[/COLOR]

I have now added these lines to the /etc/rc.local file (before the exit 0 line). 

[COLOR="DimGray"]rfkill unblock 0
rfkill unblock 1
ifconfig wlan0 up[/COLOR]

EDIT: Check also this [posting...]("http://www.amilo-forum.com/topic,929,105,-linux-on-amilo-li-1718.html")
EDIT: I had problems with compilation of the fsam7400.ko. Please read [this...]("http://ubuntuforums.org/showthread.php?p=10663457") posting.
-----------

2) This laptop gets kernel-panic and crashes randomly. It drops to a textual console and prints trace-log for the kernel. This may be a hardware failure. After all, this Fujitsu Siemens AMILO Li 1718 laptop is old.

Here are some pictures of the crash:
Crash 1[[img]http://bildr.no/thumb/852990.jpeg[/img]](http://bildr.no/view/852990)   2: [[img]http://bildr.no/thumb/852991.jpeg[/img]](http://bildr.no/view/852991) 3: [[img]http://bildr.no/thumb/852992.jpeg[/img]](http://bildr.no/view/852992) 4:[[img]http://bildr.no/thumb/853135.jpeg[/img]](http://bildr.no/view/853135)

I have tried various kernel options (boot-options) but no success so far.
Ref: [https://help.ubuntu.com/community/BootOptions#Common Boot Options]("https://help.ubuntu.com/community/BootOptions#Common Boot Options")

[Here...]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt") are more kernel parameters.
---

Both problems (wifi and the kernel-panic) occur/happen in Ubuntu 10.10 (Maverick) as well in 11.04 (Natty), with both ordinary GNOME 2.x and Unity Desktops.
---

EDIT: I just completed a [memtest86+]("http://www.memtest.org/") on this laptop.
It passed ok. No errors found.

EDIT: I have now upgraded BIOS in this laptop. You can get BIOS image from [this site...]("http://support.ts.fujitsu.com/COM/support/linkapplication.html?LNG=COM&ID=&IDNR=amilo") 
Burn it to a CD as image, then reboot. The upgrade procedure is very simple.

EDIT: Study also this [bug-report...]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/744777")

ps.[SIZE="1"]Save your Skype-calls and radio broadcasts with [audio-recorder...]("https://launchpad.net/audio-recorder")[/SIZE]

---

### Post by roadrash on 2011-05-02
The latest Ubuntu 11.04 Natty Narwhal has lost wifi connection on the LI1718. Its predessor Maverick meerkat was Ok.
Anyway the good folks over at Ubuntu Launchpad have aleady released a kernel to correct this.

Here is what to do.

Download this file to your home folder [http://people.canonical.com/~sforshee/lp710738/linux-image-2.6.38-8-generic_2.6.38-8.42~lp710738v201104200928_i386.deb](http://people.canonical.com/~sforshee/lp710738/linux-image-2.6.38-8-generic_2.6.38-8.42~lp710738v201104200928_i386.deb)

now open a terminal and type:

   >  sudo dpkg -i /lp710738/linux-image-2.6.38-8-generic_2.6.38-8.42~lp710738v201104200928_i386.deb



once finished restart PC and wireless should be working.

roadrash
     
    Posts: 6
    Joined: Thu Jan 24, 2008 13:40

Top

---

### Post by moma on 2011-05-14
Hello roadrash and many thanks for the fix. 
The wireless works very well now.

To the kernel crash:
I was adviced to remove the [modemmanager]("https://launchpad.net/modemmanager") package.
Please see:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/744777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/744777)

$ [COLOR="DarkGreen"]sudo apt-get remove modemmanager[/COLOR]

EDIT: It did not help. The laptop keeps crashing randomly. It's certainly a hardware failure. End of story. Period.

BTW: Some great clips from [icehockey 2011...]("http://www.youtube.com/watch?v=FOt8q-YagiI")

---

### Post by Wim Feijen on 2011-05-28
Hi, I'm also experiencing kernel crashes. I completely removed modemmanager as suggested. My computer seems to be running better now. 

In bug reports I saw people reporting the same problem. I am convinced it is not a hardware failure.

I only recently started experiencing such crashes, maybe because I updated to Ubuntu 11.04?

---

### Post by Wim Feijen on 2011-05-29
I'm sorry, but removing modemmanager seems like a bad idea now. My system crashed almost immediately when playing a particular movie. 

I reinstalled modemmanager and the system seems to be working better now.

When removing modemmanager, I selected: completely remove modemmanager, and at least one other file was removed as well. I do not remember which. I reinstalled modemmanager and my system doesn't crash at a specific point in the movie where it repeatedly crashed earlier.

EDIT: It still crashes spontaneously.

---

### Post by Wim Feijen on 2011-05-29
Roadrash thanks!

```
sudo dpkg -i linux-image-2.6.38-8-generic_2.6.38-8.42~lp710738v201104200928_i386.deb 

```
really solves it for me. 

Because it is a regression, you need to use this command from a terminal, it won't install by double clicking.

In addition, afterwards, I updated using the Update Manager, which stated that a new kernel version (linux-image-2.6.38-8-generic) was available.

I did not restart my computer when suggested to do so. Instead, I checked for additional updates and installed them as well.

This seems to solve the wireless problem.

---

### Post by Wim Feijen on 2011-05-30
Right now I am using a Fujitsu-Siemens Amilo Li 1718 and a Fujitsu-Siemens Amilo Pi 2530. 

The Pi 2530 is still experiencing (semi-)random crashes.

The Li 1718 lost it's wireless again.

This is a bit embarassing, but I thought of it only this night, that I just recently replaced the hard drive of my Li 1718 because I thought it was broken... because it crashed randomly as well.

I am sorry to say so, but the only conclusion which seems to fit is that Ubuntu breaks computers. :(

---

### Post by Wim Feijen on 2011-05-30
Ok, for the wireless, as far as I understand, it is being handled, see:
[https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/710738](https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/710738)

Apparently it has to do with a soft block, see message #15 in the above bug report.

sudo rfkill unblock wifi 

seems to solve it, for now. 

Probably a BIOS upgrade fixes this as well. Only I lost my BIOS password so I cannot check it.

---

### Post by moma on 2012-03-30
Hello,

**SOLUTION IN UBUNTU 12.04:**
The ATI-radeon video driver is cause of the crash. I have now tested my AMILO Li1718 laptop with Ubuntu 12.04 beta where I installed the "fglrx" video driver and the laptop works really well. It does not seq-fault anymore. Do this:

Step 0) First, install Ubuntu 12.04 from the Ubuntu daily iso. The final release is in 28th april.

Step 1) Replace the default  "xserver-xorg-video-radeon" video driver with "fglrx". Run 
[COLOR="DarkGreen"]sudo apt-get install fglrx[/COLOR]

Step 2) Reboot.
The laptop should now work flawlessly.

You may also try the "fbdev" driver. More about this in the link below.

Please read this bug-report for more details
[https://bugs.launchpad.net/linux/+bug/744777/comments/38](https://bugs.launchpad.net/linux/+bug/744777/comments/38)

Wireless network:
Wireless network works well in Ubuntu 12.04. No tweaks required. 
EDIT: Sometimes I have to reload the wifi-list. I simply:
$ sudo service network-manager restart

Or sometimes even these:
$ sudo modprobe -r ath5k 
$ sudo modprobe ath5k

---

