---
title: "Wireless connection drops"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by doc_holiday on 2005-03-20
Just installed ubuntu 5.04 previeuw. Now when I start my wireless connection after about a minute it stops working. When I deactivate and reactivate it everything is ok again for a minute or so. 
Anybody having the same problem? Somebody know how to fix this?

greets

---

### Post by jsgotangco on 2005-03-20
I did experience this a few days ago, but after having the latest update yesterday, everything went well again.

---

### Post by ozorba on 2005-03-20
The problem has not been resloved with Centino wireless, IPW2200. If you try to re-connect with Network utility you may loose GNOME menus. toolbar etc.

---

### Post by hcf on 2005-03-20
I also have problems with reconnecting my ipw2200. If I use System --> Administration --> Networking and deactivate - active, immediatly after boot, it works fine. To me it seems like there is a problem with acpi. It's only a problem if I leave my computer inactive for a while. If the screensaver has kicked in I'm not able to activate mye wirelss connection again, and have to restart Gnome to be able to reboot.

I run Hoary with the latest updates.

---

### Post by robdaemon on 2005-03-22
[QUOTE=ozorba]The problem has not been resloved with Centino wireless, IPW2200. If you try to re-connect with Network utility you may loose GNOME menus. toolbar etc.[/QUOTE]

I have the same card in my laptop, and when the card disconnects, it shuts its radio off also.  The only means of recovery for me is to reboot.  It seems to happen when ACPI kicks in and the card goes to sleep.

I'm used to my laptop (Dell Inspiron 4150) not recovering correctly from sleep modes and such  ;)

---

### Post by knappen on 2005-03-23
The same happened to me using kubuntu.

---

### Post by doc_holiday on 2005-03-24
It looks stable now

---

### Post by knappen on 2005-03-24
What did you do?

I stay connected if I have Kopete running but drops otherwise.

---

### Post by doc_holiday on 2005-03-24
Just did the latest updates

---

### Post by knappen on 2005-03-25
Ok, I will see if it makes any difference.

---

### Post by knappen on 2005-03-25
No, it still drops out after about 5 - 10 minutes. However it does not drop out if I run Kopete.

---

### Post by knappen on 2005-03-25
By the way, what type of card do you have?

---

### Post by snop on 2005-03-25
Hi,

I've had this problem for a long time (this didn't happen with Warthy).  Looking at bugzilla ([see this](https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=ipw2200&field0-0-1=component&type0-0-1=substring&value0-0-1=ipw2200&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=ipw2200&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=ipw2200) ) this seems to be a common problem with ipw2200 drivers but Ubuntu developers refuse to upgrade to new drivers because they are in a freeze process for Hoary and they fear to introduce new bugs.

I can understand this "freeze" thing but after a release, at least, Ubuntu should update some packages that are "save" to upgrade (for instance: it would have been great if you could just upgrade firefox in warthy without the need of backports project).

Anyway, my warkaround is to have a file called "workaround_wireless" with this three lines:

rmmod ipw2200
modprobe ipw2200
/etc/init.d/networking restart

Then I made a launcher on my desktop that executes:

gksudo "/home/snop/workaround_wireless"

Whenever I lose connection I just double click to my launcher and my wireless connection comes back. Interestingly once I reload ipw2200 module it doesn't fail anymore (until a new system restart).

Bye

SnOp

---

### Post by knappen on 2005-03-25
I am going to have Kopete running until there is a new upgrade.

---

### Post by mglukhovsky on 2005-03-27
I have a laptop with the IPW2200, and my solution since the beginning has been to open the root terminal, and type:

rmmod ipw2200
modprobe ipw2200
dhclient eth1

eth1 being the network interface for my card. This cleared up ALL of my networking issues and reset the interface entirely. With recent updates this rarely happens, but just in case I made a shell script (chmod'ed it to executable) and now when it goes down I just type "./resetWifi.sh" and voila!

Interestingly enough, this NEVER happened in Warty. But frankly, I'm just so damn happy that Ubuntu got its act together to provide support for this card out-of-the-box that it doesn't concern me too much.
-Mike Glukhovsky

---

### Post by nehalem on 2005-03-27
Glad I ran accross this. I have the same wirelesss device (2200) and mine will randomly get disconnected too.  I've also noticed that the battle of wesnoth game kills them too.  I have no idea why.  They really need to upgrade if there is this serious of a bug in the current version.

Glad it's not just my hardware however...

---

### Post by mglukhovsky on 2005-03-28
I was thinking of trying to write a small script or application that would ping google every few minutes (adjustable and with the capability to turn on/off in areas w/o a net connection) that would automatically execute the three commands and revive the dead net connection if the ping request failed. If it's not fixed by April when Hoary rolls out final, I may just do that. It'd be neat if it were integrated into a signal strength-type applet on the panel... or even just as a service or startup app.

---

### Post by lerrup on 2005-03-31
how do I find out which module  that I need to kill/restart?

I've a centrino based laptop and this behaviour is not good :evil:

BTW, it seems worse in Gnome than KDE for some reason.

---

### Post by snop on 2005-03-31
[QUOTE=lerrup]how do I find out which module  that I need to kill/restart?

I've a centrino based laptop and this behaviour is not good :evil:

BTW, it seems worse in Gnome than KDE for some reason.[/QUOTE]

Hi,

The module is called ipw2200 (try "lsmod | grep ipw2200" to see if this module is loaded).

> rmmod ipw2200
modprobe ipw2200
/etc/init.d/networking restart


This lines are the ones I use to bring my connection back again when a drop occurs.

> 
I was thinking of trying to write a small script or application that would ping google every few minutes (adjustable and with the capability to turn on/off in areas w/o a net connection)

When I read this I thought this was a better idea than manually bring my connection back. So I wrote this small script:

```

#!/usr/bin/env python

from time import sleep
from os import system

#Check for your wireless device typing iwconfig in a terminal and assign
#your device here (it can be eth0, eth1, etc...)
MYWIRELESSDEVICE = 'eth1'

while (1):
	#Wait for 15s
	sleep(15)
	
	#Reload the module when the connections drops	
	if system('iwconfig ' + MYWIRELESSDEVICE + ' | grep 00:00:00:00:00:00 > /dev/null') == 0:
		#Wait for 5 seconds more, just in case our connection comes back (we may be just 
		#moving our laptop from one place to another)
		sleep(5)
		if system('iwconfig ' + MYWIRELESSDEVICE + ' | grep 00:00:00:00:00:00 > /dev/null') == 0:		
			system('/sbin/rmmod ipw2200')
			system('/sbin/modprobe ipw2200')
			system('/etc/init.d/networking restart')

```

It's really simple. It does really check few things...

Edit: Don't forget to change MYWIRELESSDEVICE if yours is other than eth1 (check it issuing iwconfig from a command prompt). 

In order to use this script you should follow this steps:

1. Copy/paste the script into a file name "wireless-wa.py" (or the name you prefer).

2. Save this files wherever you want (I saved mine to /usr/local/bin)

3. Give execution permisson to the file:
chmod +x /usr/local/bin/wireless.py

4. Put is as the first line at /etc/init.d/local such as this:
/usr/local/bin/wireless-wa.py &

Don't forget the & if you have more than 1 line on your /etc/init.d/local !

Hope this may help someone.

SnOp

PD: wireless-wa stands for wireless workaround.

PD2: I have just finished writting this script. I'll test it deeply next time I restart my computer since my connection just drops once per session (and it already dropped now...)

Edited: Added /dev/null to the script in order to prevent screen garbage...
Edited 4-19-2005: 
New script that avoids screen garbage and doesn't need to ping for google.

---

### Post by lerrup on 2005-03-31
Thanks, it is there.

Now, I'll have to wait to see if I have a cure...

---

### Post by snop on 2005-04-01
> PD2: I have just wrote this script. I'll test it deeply next time I restart my computer since my connection just drops once per session (and it already dropped now...)

I've been trying my script for some time and my connection does not seem to drop (and, if it does, the script should bring it up again). So it's working fine so far.

Bye

---

### Post by dbott67 on 2005-04-03
Snop,

Thanks for the nice solution! :)

I was also having problems with the wireless nic in my laptop (Toshiba Tecra 8000 with D-Link DWL-650+).  Before accidently stumbling across Ubuntu, I had tried a few other distros (Suse & a couple of Live CDs) but could never get the wi-fi working.  Apparently, D-Link does not have Linux drivers for the DWL-650+, but I found a number of references the the Texas Instruments acx_100 chipset, and for whatever reason, I couldn't get the wifi going under SuSe.

Also, I had always found that KDE was not that intuitive to me, so I decided to look for a different distro that used Gnome.  One Google search later and I found Ubuntu.  I couldn't get the Live CD to run on the laptop, but I decided to install the "Warty" distro and the wifi worked right away.  I had already figured out how to fix the sound card issues under SuSe, so it wasn't to difficult to get the sound working under Warty.

Like some of the others here, my wifi kept dropping out.  Sometimes it would last for hours or even days, other times only a few minutes.  After reading through some of the solutions here, I was able to locate the wireless module (**acx_pci**) and made some minor changes to your 3 line script.

For those that have even less experience in linux than me, here's what I did:

1.  I knew from some previous frustration in trying to get my wifi working under Suse that the drivers were called 'acx_100'.
2.  I read the troubles that others experienced in this thread about the 'ipw2200' drivers and ran the following command:** lsmod | grep ipw2200** just to make sure that I wasn't using these drivers.  grep found nothing... but I was pretty sure that it wouldn't.
3. I ran **lsmod | grep acx_100 **and again found nothing.  I ran **lsmod** by itself and found a module called "acx_pci" which looked promising.
4. I opened another terminal session and ran the following command: **sudo rmmod acx_pci** and POOF! network was gone.  Then I ran **modprobe acx_pci**, followed by** /etc/init.d/networking restart** and BINGO! everything was working!

After finally finding the key to resetting my networking interfaces without rebooting, I went upstairs to tuck the kids in bed (ifdown / ifup didn't work, restarting Gnome didn't work, only a reboot cured it).  When I came back down, my wifi was down, I ran the script & here I am --- back online and happy as a pig in dirt (a Warthog, no less).  :)

Thanks again!

-Dave

---

### Post by Beernut on 2005-04-17
Hi All

I am having the same problem I am probably going to use the python script to keep the connection working.  I have one question this might be stupid but I was just wondering.  Why use the rmod and modprobe command?  Isn't it OK to just restart the network connection.  Just trying to understand the commands.  For the record my network card is a Netgear MA401 so I don't think it is  a driver issue I think it's a power management issue.

---

### Post by snop on 2005-04-18
[QUOTE=Beernut]Hi All

Why use the rmod and modprobe command?  Isn't it OK to just restart the network connection.  [/QUOTE]

Hi,

There's a bug in ipw2200 that was already discussed in ipw2200 mailing lists. It seems that it's already fixed in the current version (1.0.3) but hoary still uses v0.19 (note that 0.19 is not that old: they jumped from 0.22 to 1.0). The only way to reassociate my wireless network was to unload/reload the driver.

So, since I didn't want to compile the driver myself I just fixed the issue with a small python script.

There's a minor improve I'm planning to do on my script: there's no need to ping for a certain web site, just need to check if my access point mac address is 00:00:00:00:00 (now the unload-reload process happens on certain unneedec occasions). Also a bash script instead of python probably but consume less memory.

Bye

SnOp

---

### Post by snop on 2005-04-19
Hi,

Ok, I've modified slightly the script (not made in bash, yet).

The new script just checks if my wireless card has dissasociated and reloads ipw2200 when this happens. This is a better way than ping for google because it's more reliable (specially under heavy load) and prevents google from telling me that some kind of virus is spamming google from my computer... ;)

So, follow the instructions found at [http://ubuntuforums.org/showpost.php?p=111723&postcount=19](http://ubuntuforums.org/showpost.php?p=111723&postcount=19)
It's an early post that I've just updated.

Bye

PD: I have'nt tested deeply this new script but being so simple I guess it should work... ;) We will see next time I reboot...

---

### Post by beowulf62381 on 2005-04-22
hello i had been having the same problem on my m6ne notebook
using the out of the box ipw2200 drivers
a upgrade to the 1.0.0 drivers fixed this problem for me 
arg had to compile source ( linux user 4 days now free of M$ free at last )

---

### Post by jotagood on 2005-05-01
Hi... I'm having the same problem with Mepis. It is weird but in Ubuntu it works ok (I have the 2 distros on a triple boot with Win). The python script works ok (THANK YOU), BUT: it doesn't work automatically. When my connection drops, I go to a Terminal and try to execute it from my user shell and I receive an error... Permissions denied... It only works when I do su root, and then as root I execute it. So it works ok. Could you help me configure that? I'm kinda newbie, would appreciate every advice.

Thanks a lot

---

### Post by snop on 2005-05-01
Hi,

My Python script is a really ugly hack. It may not work that fine if you plan to move your laptop from network to network. It works for me, though.

> it doesn't work automatically. When my connection drops, I go to a Terminal and try to execute it from my user shell and I receive an error... Permissions denied...


That's true: in order to insert/remove a module from kernel  you need root permission. If you followed the instructions provided at [http://ubuntuforums.org/showpost.php?p=111723&postcount=19](http://ubuntuforums.org/showpost.php?p=111723&postcount=19) you should have done this:

```
4. Put is as the first line at /etc/init.d/local such as this:
/usr/local/bin/wireless-wa.py &

Don't forget the & if you have more than 1 line on your /etc/init.d/local !
```

If you did this correctly the script should automatically load at startup and have enough permissions to do its job. Check that the path to your wireless-wa.py (or whatever you called it) is right (i.e. you may have put the file in a path other than /usr/local/bin).

> a upgrade to the 1.0.0 drivers fixed this problem for me 

Updating is, probably, the best solution but it's hard for a newbie to compile a driver. I've just been too lazy to do this. Coming from Slackware I'm used to compile my own packages and I got tired of it. I only want to be developer of my own applications not hacking my whole system all the time... linux MUST be easier for everyone to succeed and I guess Ubuntu is going the right way... Well, enough ranting... I guess we won't have this problem when using breeze.

Bye

---

### Post by jotagood on 2005-05-02
Hi, actually I did have to create the local file because it wasn't there. But I think the script is not running at startup because I still lose my connection from time to time. Is there a way for me to check this out? (If the script is really running?)

Thank you

---

### Post by snop on 2005-05-02
> Is there a way for me to check this out? (If the script is really running?) 

I guess (and it't only a guess!)  that it may be the only python app running at startup. So you may open a console and type:

```
ps -A | grep python
```

If you don't get any output the application isn't running.

Please post here the contents of your /etc/init.d/local and I'll check if its right.

Bye

SnOp

---

### Post by Hieronymus on 2005-05-02
I have had the same problem in gentoo, I don't know any "nice" solution but setting boot options to "acpi=off" or "noapic". Both apic and acpi are known to cause hardware problems on some systems so turning them off can help, it did for me.

Good luck, Hieronymus

---

### Post by Psquared on 2005-05-05
I had to create the "local" file too. The only entry is:

4. Put is as the first line at /etc/init.d/local such as this:
/**usr/local/bin/wireless-wa.py &**

Is that right? How does it work? Does it check the state of the wireless connection and then reset it? How often? Does it detect if the wireless goes off and automatically restart it?

Thanks for your work.

---

### Post by snop on 2005-05-06
Hi,

[QUOTE=Psquared]I had to create the "local" file too. The only entry is:

4. Put is as the first line at /etc/init.d/local such as this:
/**usr/local/bin/wireless-wa.py &**

Is that right? How does it work? Does it check the state of the wireless connection and then reset it? How often? Does it detect if the wireless goes off and automatically restart it?

Thanks for your work.[/QUOTE]

I don't know if I get the point correctly here. If I'm not wrong you didn't read what's on [http://ubuntuforums.org/showpost.php?p=111723&postcount=19](http://ubuntuforums.org/showpost.php?p=111723&postcount=19)

Keep in mind that this is an ugly (really ugly in fact) hack. It probably won't work if you switch from network to network but I must say it works really well for me (I just use my own wireless network 99% of the time and has had no connection drops since I begun using this script).

Feel free to ask any questions.

SnOp

---

### Post by Psquared on 2005-05-06
[QUOTE=snop]Hi,



I don't know if I get the point correctly here. If I'm not wrong you didn't read what's on [http://ubuntuforums.org/showpost.php?p=111723&postcount=19](http://ubuntuforums.org/showpost.php?p=111723&postcount=19)

Keep in mind that this is an ugly (really ugly in fact) hack. It probably won't work if you switch from network to network but I must say it works really well for me (I just use my own wireless network 99% of the time and has had no connection drops since I begun using this script).

Feel free to ask any questions.

SnOp[/QUOTE]

SnOp, I'll go back and read it again. I'm sure I did something wrong because it killed my wifi. I deleted all the files and scripts and rebooted and it came back on. This morning it was on and I left my laptop on all night.

I'm using Xfce - that wouldn't make any difference would it?

In the meantime, I read where Jdong is looking into backporting the new drivers for ipw2200 so maybe it will get taken care of.

Frankly, I am thinking about compiling the new driver myself. Luca_linux has a "how-to" but it looks like a daunting task.

---

### Post by snop on 2005-05-06
Hi,

I've finally compiled ipw2200 v.1.0.3.

I've been using it for a while and it seems that the connection doesn't drop anymore.

I've put all the needed files in a tgz file found at [http://www.geocities.com/reflash8435/ipw2200-compiled-for-2.6.10-5-686-and-firmware.tgz](http://www.geocities.com/reflash8435/ipw2200-compiled-for-2.6.10-5-686-and-firmware.tgz)

The firmware is already included (I don't know if it is legal or not but... I don't really care much about that...).

In order to install this driver you'll have to do those steps:

1. Make ABSOLUTELY SURE that you are using kernel 2.6.10-5-686 (in a console type "uname -r" to know what kernel are you running at the moment).

I'll repeat: be absolutely sure that you are running the right kernel (pay attention: this is for the 686 kernel, not 386). If you are using the 386 kernel you can install the 686 version through Synaptic (look for linux-image packages).

2. Download the file mentioned above.

3. Uncompress the file:

```
cd /
sudo tar xvzf /path_where_you_put_the_file_downloaded/ipw2200-compiled-for-2.6.10-5-686-and-firmware.tgz

```
4. Restart your system.
  Note: this step may be replaced by som rmmod / modprobe but I encountered problems because I didn't know exactly what modules needed to be unloaded. A restart did the trick.

5. Check that you are using the new driver:

```
dmesg | grep ipw
```

You should see this:
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

I think that should be all. Notice that this is a risky process. I've included the old version of ipw2200 in case you need it. It's located at /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2200.ko.bak

In order to use the old version again you should rename this file to ipw2200.ko

That's all, I think. I haven't tried this process exactly (I went trough a "make install" process) so it may not work. If you try this report your result (specially if something goes wrong).

This is also a "hack" (because I haven't packaged all of this) but not as ugly as the python script...

SnOp

PD: I made this file just to save people from compiling the driver. It may work or not. I can't guarantee anything. Don't blame me if it doesn't work for you or your system get screwed up.

Also it's a good idea to keep a sane, trusted kernel handy just in case... (2.6.10-5-386 for instance).

PD2: If followed the tutorial by luca_linux found at [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Edit
ATTENTION: I've looked carefully to this process and I believe it probably won't work. I'm trying to package the driver.

---

### Post by Psquared on 2005-05-06
Snop - that looks "dicey"

I am using the 386 kernel. What's the advantage of udating to 686? What package(s) do I need?

---

### Post by snop on 2005-05-06
[QUOTE=Psquared]Snop - that looks "dicey"

I am using the 386 kernel. What's the advantage of udating to 686? What package(s) do I need?[/QUOTE]

It's compiled for better performance when using an i686 (I think this means from pentium 2 to 4).

I must say that I didn't noticed any performance boost. There might be other differnces as well (which I'm not aware of).

To install the 686 kernel just use synaptic to install the package named linux-image-2.6.10-5-686 (perhaps this is not exactly the right name because I'm just typing this from memory),

SnOp

PD: You can try to compile the driver by yourself but you'll need additional packages too. At least kernel headers and build essentials.

---

### Post by Psquared on 2005-05-06
So, the i686 is OK for a 1.5 Pent M laptop with 512 mb of RAM?

---

### Post by RaoulVolfoni on 2005-05-07
I have the same problem with an ACER TravelMate 4500.

The only way to restore the network link is to reboot the machine.

I can't find any log about this problem ...

My Ubuntu installation seems to be up to date ...

---

### Post by snop on 2005-05-07
[QUOTE=Psquared]So, the i686 is OK for a 1.5 Pent M laptop with 512 mb of RAM?[/QUOTE]

Yes, that's right. I guess all ipw2200 users are using a Centrino Dothan (that is a Pentium M 715 IIRC).

SnOp

---

### Post by Psquared on 2005-05-07
OK, I upgraded to the i686 kernel and all seems well. I kept the i386 just in case.

When I rebooted to the i686 kernel my wifi was gone. I had to re-activate it (probably normal) but I've not had the problem with the dropped connection so far.

I am sure it will crop back up and when it does I will try compiling the ipw2200 vers 1.03 package.

Thanks for your help.

---

### Post by gotmonkey on 2005-05-09
[QUOTE=snop]Hi,

I've finally compiled ipw2200 v.1.0.3.

I've been using it for a while and it seems that the connection doesn't drop anymore.

I've put all the needed files in a tgz file found at [http://www.geocities.com/reflash8435/ipw2200-compiled-for-2.6.10-5-686-and-firmware.tgz](http://www.geocities.com/reflash8435/ipw2200-compiled-for-2.6.10-5-686-and-firmware.tgz)

The firmware is already included (I don't know if it is legal or not but... I don't really care much about that...).

In order to install this driver you'll have to do those steps:

1. Make ABSOLUTELY SURE that you are using kernel 2.6.10-5-686 (in a console type "uname -r" to know what kernel are you running at the moment).

I'll repeat: be absolutely sure that you are running the right kernel (pay attention: this is for the 686 kernel, not 386). If you are using the 386 kernel you can install the 686 version through Synaptic (look for linux-image packages).

2. Download the file mentioned above.

3. Uncompress the file:

```
cd /
sudo tar xvzf /path_where_you_put_the_file_downloaded/ipw2200-compiled-for-2.6.10-5-686-and-firmware.tgz

```
4. Restart your system.
  Note: this step may be replaced by som rmmod / modprobe but I encountered problems because I didn't know exactly what modules needed to be unloaded. A restart did the trick.

5. Check that you are using the new driver:

```
dmesg | grep ipw
```

You should see this:
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

I think that should be all. Notice that this is a risky process. I've included the old version of ipw2200 in case you need it. It's located at /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ipw2200.ko.bak

In order to use the old version again you should rename this file to ipw2200.ko

That's all, I think. I haven't tried this process exactly (I went trough a "make install" process) so it may not work. If you try this report your result (specially if something goes wrong).

This is also a "hack" (because I haven't packaged all of this) but not as ugly as the python script...

SnOp

PD: I made this file just to save people from compiling the driver. It may work or not. I can't guarantee anything. Don't blame me if it doesn't work for you or your system get screwed up.

Also it's a good idea to keep a sane, trusted kernel handy just in case... (2.6.10-5-386 for instance).

PD2: If followed the tutorial by luca_linux found at [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]

Hi Snop,
I followed the your instructions to update to the newer driver. I restarted the system, and ran dmesg

ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x00000100, Config: 00000142
ipw2200: Start IPW Event Log Dump:
usbcore: registered new driver ipwtty
drivers/usb/serial/ipw.c: IPWireless tty driver v0.3
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x00000100, Config: 00000142
ipw2200: Start IPW Event Log Dump:

Any suggestions?

---

### Post by snop on 2005-05-09
Hi,

I'm gonna try to package the newest ipw2200 driver (I have some preliminar packages but I want to make a couple of test). 

Since ipw2200 driver is supplied with the kernel package it will require some "--force-overwrite" options (which is ugly). Perhaps I should try to package a new kernel...

I'll report news here. Stay tuned.

Bye

---

### Post by gotmonkey on 2005-05-09
[QUOTE=snop]Hi,

I'm gonna try to package the newest ipw2200 driver (I have some preliminar packages but I want to make a couple of test). 

Since ipw2200 driver is supplied with the kernel package it will require some "--force-overwrite" options (which is ugly). Perhaps I should try to package a new kernel...

I'll report news here. Stay tuned.

Bye[/QUOTE]

Great! Thank you very much. I look forward to hearing what you come up with.

---

### Post by evil-nick on 2005-05-09
I just started having a similar problem, and I haven't fixed it yet...  I have a netgear MA401, on a Sotec 3120X laptop.  4 days ago it just started dropping the connection a few minutes after boot.  This was weird because it's worked fine for a month.  Tonight, I tried ejecting the card, got an error msg, logged out of gnome, and when I logged back in half of my panel didn't come up (battery monitor, wireless monitor, clock) but the wireless worked... Any connection, or a fluke?

---

### Post by snop on 2005-05-11
Here are the packages for ipw2200 1.0.3 for Hoary, as promised.

Keep in mind that this is just another "quick hack" (but this time let's hope this one works better).

Here's the how-to:

1. Download this file:
[http://www.geocities.com/reflash8435/ipw2200-packages.zip](http://www.geocities.com/reflash8435/ipw2200-packages.zip)

2. Download the firmware (version 2.2) from here:
[http://ipw2200.sourceforge.net/firmware.php?fid=4](http://ipw2200.sourceforge.net/firmware.php?fid=4)
Note: You must press "I agree" at the bottom of the page to begin downloading the file.

3. Install the firmware:
```
cd /usr/lib/hotplug/firmware/
sudo tar xvzf /path/to/firmware/ipw2200-fw-2.2.tgz
```
Note: You don't have to type /path/to/firmware but the real path where you downloaded the file.

4. Check the kernel version you are currently using issuing this command on a console:
```
uname -r
```

IF YOU USE A KERNEL OTHER THAN 2.6.10-5-686 OR 2.6.10-5-386 THEN THIS WON'T WORK.

5. Now that you identified your kernel version unzip and install one of the files you'll find at ipw2200-packages.zip (you can use "file-roller" to unpack the file you need):

For 2.6.10-5-386:
```
Unzip ipw2200_1.0.3-386_i386.deb
Install the package issuing this command from a terminal:
sudo dpkg -i --force-overwrite ipw2200_1.0.3-386_i386.deb
```

For 2.6.10-5-686:
```
Unzip ipw2200_1.0.3-686_i386.deb
Install the package issuing this command from a terminal:
sudo dpkg -i --force-overwrite ipw2200_1.0.3-686_i386.deb
```

Note: As I said before this is a "quick hack" for many reasons. One of them is that this packages overwrite some files from your kernel. Don't blame me if nothing works after doing all this things...

6. Update modules:
```
sudo depmod -a
```

7. (Optional and risky step since led code is yet experimental)
I've been able to make my wireless led work issuing this commands:
```
sudo touch /etc/modprobe.d/ipw2200
sudo echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200

```

8. Restart your system.

That's all, I think. There are a lot of notes I could have done for almost every step but I don't want you to get bored...

Feel free to ask any questions and/or report success/failures.

SnOp

Edit: New packages upload. Hopefully should fix the problems found because of old modules being kept.

---

### Post by xbx on 2005-05-11
just tried to follow your instructions...
(I didn't do the last led bit)
went smoothly, expect after the reboot:

```
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
```

and I do have the correct kernel:
uname -r
2.6.10-5-686

I'm going to investigate a bit more.

[edit]

I downloaded the source and recompiled, and it works when following carefully the instructions (about removing previously installed files, notably ieee80211 modules).

I don't know anything about how .debs, but it looks to me the problem is that your installation doesn't remove the old files. (and the default install from the sources is very different from the default ubuntu kernel).

otherwise, i don't know how to find more clues of what went wrong. (the compiled ipw2200.ko is indeed different from the one you provide, but there are exactly the same size - and I don't know how I can see in what they differ)
On an other note, I noticed the firware is exactly the same as the one in ubuntu default install. (except the file names are different)

sorry I can't help anymore.

---

### Post by snop on 2005-05-11
[QUOTE=xbx]
I don't know anything about how .debs, but it looks to me the problem is that your installation doesn't remove the old files. (and the default install from the sources is very different from the default ubuntu kernel).[/QUOTE]

I think you're right. Since I made some many "make install" / "dpgk -i ... " and moved files I don't really know what's needed (hey, it works for me). I'm trying now to reinstall 2.6.10-386 kernel in order to have a "virgin" kernel to test my own packages and try to find out what's going on.

This is my first deb package and I'm still trying to figure out how everything works. I know that I can put a post-install script into the package to execute some commands . I planned to do the "sudo depmod -a" using a post install script but it was hard to add this script using checkinstall because, I think, of a bug in checkinstall ([http://asic-linux.com.mx/~izto/checkinstall/docs/Changelog](http://asic-linux.com.mx/~izto/checkinstall/docs/Changelog) look at PINST_EXISTS bug). Since I was short on time I decided to add it to the how-to. I think I'll have to package the deb "by hand".

All in all I'll try to get the right package. Any help would be appreciated. Ipw2200 1.0.3 is working really fine for me but I want everyone to easily install the new driver. 

Bye

SnOp

---

### Post by luca_linux on 2005-05-12
Yes, as has been already said, the old modules are getting loaded instead of the newer ones: copy them as said in this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623).
To make sure you got rid of the old ones, completely delete them (ipw2200.ko and ieee80211*.ko) before installing the new driver.

---

### Post by snop on 2005-05-12
[QUOTE=luca_linux]Yes, as has been already said, the old modules are getting loaded instead of the newer ones: copy them as said in this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623).
To make sure you got rid of the old ones, completely delete them (ipw2200.ko and ieee80211*.ko) before installing the new driver.[/QUOTE]

I believe that luca_linux is pointing into the right direction. ieee80211*.ko drivers are the ones that "hurt" here. ipw2200.ko is being already overwritten by the package.

---

### Post by gotmonkey on 2005-05-12
[QUOTE=luca_linux]Yes, as has been already said, the old modules are getting loaded instead of the newer ones: copy them as said in this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623).
To make sure you got rid of the old ones, completely delete them (ipw2200.ko and ieee80211*.ko) before installing the new driver.[/QUOTE]

It took a couple of tries, but I compiled the driver from your post and it works. I am running the latest driver. I had to go back and do it  a second time, because, I didn't delete the files you listed above.

Thanks Luca and Snop. I appreciate the help.

---

### Post by snop on 2005-05-13
Hi,

I updated the packages. The new ones should, hopefully, overwrite all modules.

I've tried to reinstall my kernel and apply my own packages. They work for me.

Remeber that the how-to on how to use this packages is found at [http://ubuntuforums.org/showpost.php?p=167782&postcount=46](http://ubuntuforums.org/showpost.php?p=167782&postcount=46)

SnOp

---

### Post by seti@tquadrado.com on 2005-05-14
Hi,

try this: kill the applet for signal strenght of the wireless.

---

### Post by phen on 2005-06-17
thank you snop, my wireless is now working - awesome! 

even the nice blue led works! I am having an

HP nc6120 laptop with intel centrino and ipw2200 wlan,

using kernel package:

linux-image-2.6.10-5-386,   installed version is 2.6.10-34.2  (reported by synaptic)


thanks for your work!

---

