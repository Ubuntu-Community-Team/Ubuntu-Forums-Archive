---
title: "Problems with wifi on vaio"
date: 2010-12-18
forum: Hardware
---

### Post by gr1ph00n on 2010-12-18
Hello, i am a new ubuntu user, i have installed the 10.04 lts release on my laptop, a sony vaio f vpcf12s1e. I have followed a guide which i have found on these forums in order to install nvidia and alsa drivers properly. Unfortunatelly i cannot get the wifi working, only the bluetooth works and of course the ethernet connection. 
The command ```
dmesg | grep wlan0
``` says "link is not ready" but i have not found a way to fix this. Could you help me, please?

EDIT: 

i have noticed that ```
iwlist scan
``` shows me the avaible wifi connections but i cannot see the icon on the top bar.

---

### Post by coffeecat on 2010-12-18
> **gr1ph00n said:**
> 
EDIT: 

i have noticed that ```
iwlist scan
``` shows me the avaible wifi connections but i cannot see the icon on the top bar.

Until it's connected, it's quite nondescript. It *should* be just to the left of the sound/volume icon. Try left-clicking in that vicinity until you get a drop-down menu showing all the wireless networks. Since you get an output from iwlist scan, then hopefully the device is working. If you get a drop-down showing the networks, click on yours and put in your passkey where prompted.

---

### Post by gr1ph00n on 2010-12-18
> **coffeecat said:**
> Until it's connected, it's quite nondescript. It *should* be just to the left of the sound/volume icon. Try left-clicking in that vicinity until you get a drop-down menu showing all the wireless networks. Since you get an output from iwlist scan, then hopefully the device is working. If you get a drop-down showing the networks, click on yours and put in your passkey where prompted.

Hi, first of all thanks for your reply, i have tried it but it does not appear, i can only see the bluetooth icon... Otherwise, is there a way to connect to a wifi net troughout console?

---

### Post by coffeecat on 2010-12-19
> **gr1ph00n said:**
> i have tried it but it does not appear, i can only see the bluetooth icon...

If the network manager icon is not appearing then there is something wrong with your installation and it would be better to fix this rather than mess around in the console. I was wrong about the disconnected network manager icon being nondescript - I was going from memory. It was nondescript in one version, but in 10.04 it tells you a lot. See my screenshots below - click on the thumbnails. These are from the 10.04-1 live CD running on a laptop with working wireless (a Sony Vaio), but not yet connected. The network manager is the one with the red exclamation mark - meaning, not yet connected. It's just to the left of the volume icon in the first (no bluetooth device connected) and to the left of the bluetooth icon in the second.

Do you have this icon? If not, look closely at the screenshots just to the left of the network manager icon. You can see three small horizontal lines. These are the notification area, a panel applet to which the network manager is tethered. If you have no notification area, then you will not be able to see network manager. Again, if you have no notification area, then something is wrong. Both notification area and network manager appear in a default install.

[ATTACH]178828[/ATTACH]

[ATTACH]178829[/ATTACH]

---

### Post by gr1ph00n on 2010-12-19
I don't see neither the 1st icon nor the 2nd one (the one with the exclamation mark).. i see only the volume icon, the bluetooth one, the date one, the mail one and so on.. What is strange is that after installing linux the 2 icons were here, then i installed updates with apt-get and then they disappeared... Now i am trying to install ubuntu 10.04 lts again and i ll see what will happen. I let you know what will happen.

---

### Post by coffeecat on 2010-12-19
Probably too late now if you are reinstalling, but all you might have needed to do is to right-click on the panel, select 'add' and select the notification area applet.

Whatever, let's see what a reinstall does. I've not seen any threads reporting loss of the notification area after a system update.

---

### Post by gr1ph00n on 2010-12-19
Nothing, i can still see only the ones you can see in the attached image. I have tried what you said too, but i do not see the option you mentioned. I mean i can add icons to the panel but the one you named is not present, moreover the nm-applet process is running.

---

### Post by coffeecat on 2010-12-19
> **gr1ph00n said:**
>  I mean i can add icons to the panel but the one you named is not present, moreover the nm-applet process is running.

Notification Area not listed? Let's be clear. You say that if you right-click on the panel and select 'Add to panel', then Notification Area is not in the list of panel applets? That's very odd. The only thing I can think of that could possibly cause the absence of the notification area in a default install and in the list of available panel applets is a corrupted installation CD.

Did you check the downloaded ISO md5sum? And did you burn the CD at a slow speed?

---

### Post by Quackers on 2010-12-19
Hi
Can you go into synaptic package manager and in the quick search box enter "network-manager"  without the quotes. You should see 2 entries. One called network-manager and another called gnome-network-manager. They should both have green boxes next to them, confirmning that they are installed.
If they are not installed try right-clicking on both of them and selecting Mark for installation, then click on the green tick mark in the toolbar to install them.
Let us know what you find :-)

---

### Post by gr1ph00n on 2010-12-19
> **coffeecat said:**
> Notification Area not listed? Let's be clear. You say that if you right-click on the panel and select 'Add to panel', then Notification Area is not in the list of panel applets? That's very odd. The only thing I can think of that could possibly cause the absence of the notification area in a default install and in the list of available panel applets is a corrupted installation CD.

Did you check the downloaded ISO md5sum? And did you burn the CD at a slow speed?

Ah nope I have confused it with another one, anyway i have added it and but i have noticed that such notfication area is already on the bar, it's the icon which you can see on the left of the battery (the 3 little horizontal lines) in the screen i posted before. By the way, i have installed the os with 2 different cds, burnt at a slow speed, and both passed successfully the md5 checksum and the integrity test.  

> **Quackers said:**
> Hi
Can you go into synaptic package manager and in the quick search box enter "network-manager"  without the quotes. You should see 2 entries. One called network-manager and another called gnome-network-manager. They should both have green boxes next to them, confirmning that they are installed.
If they are not installed try right-clicking on both of them and selecting Mark for installation, then click on the green tick mark in the toolbar to install them.
Let us know what you find :-)

Hi, i have checked them but they seems to be already installed.

---

### Post by coffeecat on 2010-12-19
> **gr1ph00n said:**
> it's the icon which you can see on the left of the battery (the 3 little horizontal lines) 

Yes, of course, I missed that. So you do have the notification area but not the NM applet. Next step:

Go to System > Preferences > Startup Applications > Startup Programs Tab. Check that Network Manager is ticked. If it's not in the list, click on the Add button and this is what you need:

Name: Network Manager
Command: nm-applet --sm-disable
Comment (optional): Control your network connections

If you need to tick the NM entry or add the entry, you may need to reboot.

---

### Post by gr1ph00n on 2010-12-19
As you can see in the attached image, it was already added and configure as you mentioned, but how is it possible that it does not appear on the bar?!.

---

### Post by Quackers on 2010-12-19
If you press Alt + F2 and enter in the run box nm-applet and hit enter, does it appear then?

---

### Post by Rubi1200 on 2010-12-20
Hi,
coffeecat asked me to jump in here with some suggestions (not that coffeecat and Quackers haven't already tried most of what I would have suggested already), so let's try something else.

Since this is a fresh install and you have probably not made too many customizations yet, try this (warning: this **will** remove any custom settings you may have had!):[FONT=monospace]

Go to Applications > Accessories > Terminal and run these commands:
[/FONT]```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Log out and back in to see the changes.

Let us know if this helps.

---

### Post by gr1ph00n on 2010-12-22
> **Rubi1200 said:**
> Hi,
coffeecat asked me to jump in here with some suggestions (not that coffeecat and Quackers haven't already tried most of what I would have suggested already), so let's try something else.

Since this is a fresh install and you have probably not made too many customizations yet, try this (warning: this **will** remove any custom settings you may have had!):[FONT=monospace]

Go to Applications > Accessories > Terminal and run these commands:
[/FONT]```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Log out and back in to see the changes.

Let us know if this helps.


Hi, first of all thank you for your reply, i have tried the commands you said, but after the restart of the gnome gui, the network manager didnt appear on the bar. Btw, i forgot to specify that i have a 64bit version of linux and the kernel version is the 2.6.32-27-generic. Ah another thing which may be useful is that i have noticed the network manager icon disappeared after installing the first updates and if in not mistaken, one of them was a network daemon, its name should be avdhcp or so... maybe this issue is due to one of these ones...
Another thing, in order to connect my laptop trought eth0 i have used the pppoeconf command but the icon disappeared before i used it...

---

### Post by coffeecat on 2010-12-23
I am very puzzled. I have never, ever had network manager disappear from the panel after a routine update. Not after any update for that matter. Since this has happened to you twice now, I wonder if you installed something that is causing the problem. You mention...

> **gr1ph00n said:**
> Ah another thing which may be useful is that i have noticed the network manager icon disappeared after installing the first updates and if in not mistaken, one of them was a network daemon, its name should be avdhcp or so... maybe this issue is due to one of these ones...

What is this 'avdhcp'? There is no package that corresponds to this. Have a look in System > Administration > Log File Viewer. Look for 'dpkg.log' in the left pane and click on the drop-down arrow. Now select the day for when 'avdhcp' was updated/installed. What is its correct name? With that we might be able to investigate and see if it is likely to be a problem.

Also have you, by chance, installed wicd or any other networking software?

---

### Post by gr1ph00n on 2010-12-24
> **coffeecat said:**
> I am very puzzled. I have never, ever had network manager disappear from the panel after a routine update. Not after any update for that matter. Since this has happened to you twice now, I wonder if you installed something that is causing the problem. You mention...



What is this 'avdhcp'? There is no package that corresponds to this. Have a look in System > Administration > Log File Viewer. Look for 'dpkg.log' in the left pane and click on the drop-down arrow. Now select the day for when 'avdhcp' was updated/installed. What is its correct name? With that we might be able to investigate and see if it is likely to be a problem.

Hi, the name of that pack was avahi or so, but after a rapid search on  google i do not think it could cause such issue. 

> **coffeecat said:**
> Also have you, by chance, installed wicd or any other networking software?

I did not install any networking software, and as i previously said the only thing i configured was the pppoe

---

### Post by gr1ph00n on 2011-01-02
I have an update: if the pc goes in standby mode and then i restart it, then the wifi icon appears and i can use it as usual :-D

---

### Post by gr1ph00n on 2011-01-21
problem solved with wicd network manager :)

---

### Post by kemtnbkr on 2011-02-19
I was having the same problem on my HP Pavilion dv6, but I found a (very ugly) way to get the WiFi to work in 10.10.  I just boot to Windows (i have a dual OS setup) b/c from Windows the Wifi on/off switch (hardware) works fine.  Then I reboot to Ubuntu, and it is working.  However, this is by no means a fix, but that's all I've been able to figure out thus far.

---

