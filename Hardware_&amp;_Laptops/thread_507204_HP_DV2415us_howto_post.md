---
title: "HP DV2415us howto post"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by buntunub on 2007-07-22
HP DV2415us Howto

I'll be honest and admit I had a real bear of a time getting this thing up and running. Some of it my fault and the rest ill attribute to Vista and HP's hardware preconfiguration. At first I tried to install Ubuntu Fiesty via the livecd using Gparted. This failed due to some funky disk setup that HP preconfigured the thing with (ie kept getting fatal disk errors). So, I went into Vista and in the Disk Admin section, found a utility that allowed disk resizing. That done, I rebooted back into livecd and away we go! Install flawless (minus the bcm43xx errors on initial bootup) and then booted into the live system. Now enter my world of bugs! 
-Wireless wont work
-Webcam wont work (even with Ekiga)
-Scrollpad wont work
-Dual monitoring wont work
-Sound wont work at all.

Phew! What did work – Everything else. Very long story (and dozens of hours of troubleshooting), I get all but the webcam to work in the end utilizing various wiki's and howto's on these, and other sites (nope, no IRC crying for me!).  However, a misadventure with ssh and vnc somehow screwed up my /home partition and so it was that I reinstalled. Vista was irking me! Nothing about that OS appeals at all and it most certainly has nothing over modern day linux. In fact, I quickly discovered that there wasnt one single thing that a Home Premium edition of Vista has that Linux doesnt, and in most cases, does better. The 2007 Outlook is nice and is indeed better than Evolution, but hey, its how much $$ ? ALOT! No, it does not come free with home premium. Off we go. Fresh install went much, much smoother. I think Gparted worked like a charm this time because I told it to wipe out Vista, which it did, enthusiastically! Second time around:
-Webcam worked out of the box with Ekiga only
-Wireless still no work.
-Scrollpad worked
-Beryl+Multimedia worked flawlessly
-dual screens no work
-DVD playback works but is choppy sometimes
-DVD/CD Record seems to work OK

It being the second time around, I didnt have to spend too much time getting all the stuff to work that I did before, but this time, I got it ALL working flawlessly. Heres how I did it:

1)Wireless. The HP DV2415us comes with a Dell 1390 Broadcom Chipset. Use this guide [http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+wireless](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+wireless)
2)Webcam. Sonix Microdia chipset 0c45:62c0. Like I said, this works with Ekiga only on fresh install. Ekiga can take pictures and if you have an account, you can Video Conference with it. However, I needed something for more generic uses and luvcview came to the rescue here. Heres how to get that working:
		a.	On a fresh Fiesty install, your uvc and cam drivers should be good to go. All you need to do                                                                                                                     install luvcview's deps and your up and running. Install libsdl1.2-dev using Synaptic, then download and install luvcview as follows:
			-download luvcview-20070512.tar.gz from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)
			-Using either file roller or command line, untar it into the directory of your choice. 			I created a .drivers folder while following the above ndiswrapper guide, so I just used that one.
			-cd to the folder the untar created. for me it was ~/drivers/luvcview-20070512, and 			then $make, then sudo make install. You should not have gotten any errors on that process. If you did, you might need to reload your uvc drivers or webcam drivers. However, if your camera worked out of the box with Ekiga, then you probably just didnt do the compile correctly. Go back and try again.
			- Now via command line, $lucview -d /dev/video0 -f yuv -s 640x480. Thats it, you 			should now see the light come on and your smiling face in the luvcview window. You can change the above parameters as needed. For example, make sure your using the right video mount point and change screen size to desired (320x240, etc).
	3)  Scrollpad. Follow this guide 			[http://ubuntuforums.org/showthread.php?t=485289&highlight=scrollpad](http://ubuntuforums.org/showthread.php?t=485289&highlight=scrollpad)
	4)  WPA wifi security follow this guide 	[http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+howto](http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+howto)
	5)  Dual Monitoring. Use $nvidia-settings and setup Twinview. For ATI, cant help ya as I avoid 	that card like the plague. You can get it setup quite nicely there, but it does have the bad habit of 	making the secondary monitor the primary one and I haven't yet figured out how to fix that.
	6)  Networking guides which have been invaluable:
	[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
	[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
	[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)
	[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

	Other guides:
	[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

	Thats about it. All my hardware now works very will in Fiesty. It wasnt all that painful in the end, 	but it is a steep learning curve if your new to Linux but well worth it.

---

