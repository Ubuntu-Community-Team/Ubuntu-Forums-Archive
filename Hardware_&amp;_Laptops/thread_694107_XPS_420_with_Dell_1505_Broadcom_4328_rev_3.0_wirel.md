---
title: "XPS 420 with Dell 1505 Broadcom 4328 rev 3.0 wireless card and nvidia 8800 gt card"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by mobiusdim on 2008-02-11
Hi all,
          I installed Gutsy on a Dell XPS and wanted to let everyone know what worked for me. The system came with Vista loaded, It was partitioned into a 54 MB fat16 Dell diagnostic partition, a 15 GB recovery partition which has the factory image of the OS for recovery and the windows partition. I recommend leaving the diagnostic partition as it is for obvious reasons. If you want windows (just for the heck of it) but relegate it to a distant corner of the hard drive you might want to copy the dell factory image and use it to get back the windows installation but i didn't care about it. There are online guides for this sort of a thing you can check out. Besides, there is some amount of satisfaction to be gained in reinstalling windows in a much smaller partition in a much stunted state (without all the factory junk that is installed in it. note that dell includes all the drivers etc in a disc). 

        I promptly deleted the recovery and windows partition using gparted on Gutsy live cd and partitioned the hard disk into 10 gb logical ext3, 8 gb logical swap, another 10 gb logical ext3  and a 360 gb ext3, a 20 gb ntfs for windows and 60 gb free space for data recovery etc. In the second 10gb ext3 partition, i mounted the  / for gutsy, i used the 8 gb for swap ( i have 4gb RAM ) and the first 10 gb ext3 i will use to play around with other versions. I consciously juxtaposed both the ext3 partitions around the swap. 

** Important note : if you plan to use the same /home folder for the two versions, don't format the /home partition during the second version install. Technically speaking, if you are serious about having two versions it is better to mount something like /data in the large partition you are wanting to use between both distros instead of /home as different distros might have problems using preferences files (dot files) stored in /home. But you can always just mount this large partition using the generically produced names like sda3 for example without having to bother with these details. But separating the / and data (in my case /home) is a good idea since if and when  :)  you destroy your current install if will have a separate /home partition you can keep all your data on and your user preferences (if you are the only user on the computer, in the dot files in /home) and reinstall linux on the partition where / is mounted , just making sure that you don't format the home partition. I find this an invaluable tool since it is easy to mess up your OS installation even if you are not seriously playing with it. 

The first step for me after installation is always is to get the wireless  working so I will start with it. 

The system has a Broadcom 4328 card (Dell 1505) Rev 3.0. Most of the instructions I gathered from the forums worked. Briefly , the latest windows driver from Dell for the wireless card didn't work (a "unknown symbol" message appears in /var/log/syslog) but the older driver namely the R151517.EXE works. Download it ,

sudo apt-get update
sudo apt-get install build-essential
sudo echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

REBOOT
sudo ln -s /usr/src/linux-headers-2.6.22-14-generic/ /lib/modules/2.6.22-14-generic/build
sudo apt-get install ndiswrapper-utils-1.9 

sudo ln -s /usr/sbin/ndiswrapper-1.9  /usr/sbin/ndiswrapper
(if you get a "file already exists , good for you, but sometimes not doing this produces a fatal error, in any case this is a benign exception)

cd to folder with the driver 

unzip -a 'driver'
cd folder named 'DRIVER'
sudo ndiswrapper -i bcmwl5.inf

sudo ndiswrapper -l
to make sure the driver is installed

sudo ndiswrapper -m
to insert an alias wlan0 into module configuration file

sudo modprobe ndiswrapper

If everything went as planned, the blue led on your wireless antenna should have come up.

test wireless by 

iwlist scanning

if you get a complaint saying wlan0 device doesn't exist do  

sudo ifconfig wlan0 up

Now if it didn't work, and you would like to try it again, you have to uninstall everthing you just did. I am not going to post those instructions here but you can find it here

[http://ubuntuforums.org/showthread.php?t=297092&page=3](http://ubuntuforums.org/showthread.php?t=297092&page=3)

and redo everything again.

Next comes the videocard. Initially. I actually just manually installed the latest nvidia drivers the (169.09 version) and it worked perfectly well , detecting both my Dell 22'' widescreen and my Viewsonic 28'' widescreen and I could configure them layout using  

sudo nvidia-settings 

But everytime I rebooted, X-server would crash. After doing this for a couple of times I decided to use envy. I downloaded Envy from here 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and first uninstalled everything including the manually installed nvidia driver by doing a 

sudo envy --uninstall-all

and then letting envy install everything including my nvidia driver. 

This works perfectly well. 

Now for a little quirk. My video card has two DVI ports, but my viewsonic has a hdmi and vga ports . Sometime after all this , my dvi to hdmi cable died on me and  I had to use a dvi to vga adapter to connect the computer to the monitor using vga cable. If and let's hope not , you need to do this, you need to run nvida-settings again.  But the resulting resolution (even though nvidia claims it is 1920 X 1200 ) doesn't look that great. The only workaround I found was to  allow set the resolution to 'auto' which causes nvidia to use "metamodes" in the xorg.conf file's Mode option  which works perfectly well. My dell 22'' screen can rotate so I included a

Option "Rotate" "Left" 

in the monitor section right before the subsection "Display" of my xorg.conf which allows me to use my dell in portrait mode. I use the separate X screeen option in nvidia-setttings so I have two monitor sections and I think this also helps in getting the mouse to change its direction of motion in the rotated screen so it moves between the viewsonic in landscape mode and dell in portrait mode seamlessly..

Everything else on the system seems to work out of the box , especially the 19 in one card reader (atleast for SD cards, I didn't try other cards ). I am not sure if my Hauppauge TV tuner card works , I would appreciate any information on that. 

Hope this helps someone , enjoy !

go ubuntu

---

### Post by mobiusdim on 2008-02-11
oh btw..forgot to mention that the dell Bluetooth keyboard and mouse work out of the box with gutsy.

enjoy

---

