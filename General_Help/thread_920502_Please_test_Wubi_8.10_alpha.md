---
title: "Please test Wubi 8.10 alpha"
date: 2008-09-15
forum: General Help
---

### Post by ago on 2008-09-15
Wubi 8.10 alpha should be working now, please test it and report about your experience. It is recommended to let Wubi 8.10 download the ISO for you. 

[http://wubi-installer.org/devel/minefield/Wubi-8.10-rev507.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev507.exe)

If you already have 8.04 installed you can either uninstall it and try 8.10, or you can try to upgrade 8.04 to 8.10 (note that dist-upgrades cannot be reverted). In either case it is well possible to back up your previous installation by copying the ubuntu directory.

---

### Post by avanhel on 2008-09-16
I like the starter menu. But I must admit that I would like a bit more choice with the storage size menu. I get 4,5,6,7,8,9,10,15,30 Gb. I would like to see a smaller jump between 15 and 30 like 20 and 25. If that makes any sense. 
Also the fact that it chooses the language automatically is really good. :)
Keep up the good work

---

### Post by Orlsend on 2008-09-16
So how do i upgrade? using wubi? Ill be insterested to test wubi with II.

---

### Post by ago on 2008-09-16
[http://ubuntuforums.org/showthread.php?t=834808](http://ubuntuforums.org/showthread.php?t=834808)

even better:

press Alt+F2 and type in &#8220;update-manager -d&#8221;

---

### Post by sat_e_llite on 2008-09-16
> **avanhel said:**
> I like the starter menu. But I must admit that I would like a bit more choice with the storage size menu. I get 4,5,6,7,8,9,10,15,30 Gb. I would like to see a smaller jump between 15 and 30 like 20 and 25. If that makes any sense. 
Also the fact that it chooses the language automatically is really good. :)
Keep up the good work The new one has larger install sizes?

---

### Post by Orlsend on 2008-09-16
Anybody got the Ideas of how much the Update will take? with already HH installed?

like who many MB of download.

---

### Post by ago on 2008-09-16
it depends on how much software you installed, since all your apps will get updates. Normally it is north of 1G

---

### Post by Orlsend on 2008-09-16
Okay ill do this when I am in Finland, rigth now here in africa the internet is slow.

---

### Post by duksandfish on 2008-09-16
Well, I have used wubi 8.04, which worked perfectly, as did this, and the only problems being intrepid related, also the uninstall worked fine (STILL no wi-fi support for atheros 5007eg....)

---

### Post by sat_e_llite on 2008-09-16
I'll try it soon but I'm not so sure in using Alpha software.

---

### Post by ZjosH on 2008-09-17
I just tried to install wubi 8.10 alpha, and it installed without errors in windows. But then I needed to reboot my computer, and I got through grub, selected Ubuntu. It did the usual loading bar stuff. But then it gave me a busybox built in terminal, and I have no clue what to do when I get it. It didnt say anything about what to do eighter, the only thing I saw was the name of the user ( I suppose ) and it was (initramfs). Any Ideas?

---

### Post by Orlsend on 2008-09-17
> **ZjosH said:**
> I just tried to install wubi 8.10 alpha, and it installed without errors in windows. But then I needed to reboot my computer, and I got through grub, selected Ubuntu. It did the usual loading bar stuff. But then it gave me a busybox built in terminal, and I have no clue what to do when I get it. It didnt say anything about what to do eighter, the only thing I saw was the name of the user ( I suppose ) and it was (initramfs). Any Ideas?
You need to do a proper shutdown by loading windows and then when you get to the login screen just click "shut down" right away. the turn on your computer select Ubuntu see what happens, If not successful the check for errors on the HD in windows.

---

### Post by ago on 2008-09-17
> **ZjosH said:**
> I just tried to install wubi 8.10 alpha, and it installed without errors in windows. But then I needed to reboot my computer, and I got through grub, selected Ubuntu. It did the usual loading bar stuff. But then it gave me a busybox built in terminal, and I have no clue what to do when I get it. It didnt say anything about what to do eighter, the only thing I saw was the name of the user ( I suppose ) and it was (initramfs). Any Ideas?

Do as Orlsend suggested, if you still end up in busybox type:

cat /proc/cmdline
cat /proc/mounts
grep err /carsper.log
grep mount /carsper.log

And post here the ouput

---

### Post by avanhel on 2008-09-20
I have a small problem with the startup for WUBI. It could also be a problem with ubuntu itself. 
I have installed WUBI 10Gb and it downloaded the ubuntu, I think the dutch version.
When I rebooted the computer to load Ubuntu I get the normal start screen where the bar fills up but after that I get a screen with stripes in different colors and no reaction from the computer. ubuntu 8.04 worked pretty well on this same computer. 
If you can tell me which log files to post I should be able to do it.

thanks for the help

---

### Post by ago on 2008-09-21
That might be a video issue in 8.10. Check whether there are known problems for your video card. Relevant logs are Xorg and syslog

---

### Post by kl.u on 2008-09-22
I tried an install on a Acer Inspire One, which has a Atheros AR242x 802.11bg adapter installed.

It installed with the Atheros driver automatically but does the wireless does not work. I cannot turn on the wireless function which turns on automatically when I run windows XP(it came installed with XP Home). Any suggestions?

I also notice that some of the applications which has windows with height higher than the screen resolution do not have the scroll bar, hence I cannot get to the bottom of the window. This may be more of a Ubuntu problem than a Wubi specific problem. (Acer Inspire One is a sub notebook with a 8.5" screen and a resolution of 1024x600).

---

### Post by ago on 2008-09-22
> **kl.u said:**
> 
It installed with the Atheros driver automatically but does the wireless does not work. I cannot turn on the wireless function which turns on automatically when I run windows XP(it came installed with XP Home). Any suggestions?

I also notice that some of the applications which has windows with height higher than the screen resolution do not have the scroll bar, hence I cannot get to the bottom of the window. This may be more of a Ubuntu problem than a Wubi specific problem. (Acer Inspire One is a sub notebook with a 8.5" screen and a resolution of 1024x600).

Both issues look like generic Ubuntu problems

---

### Post by bouta on 2008-09-23
okay so im trying the latest wubi Wubi-8.10-rev507 .and i got the latest alpha release 6 and put both files in the same folder. when i launch wubi ,it starts downloading the Image file. why didnt wubi detect it ? and is alpha 6 supported by wubi?

---

### Post by ago on 2008-09-23
Wubi alpha tries to use the latest daily ISO. If you want to use an older ISO diconnect from the internet during windows side installation or run wubi with the  "--skipmd5check" argument

---

### Post by bouta on 2008-09-23
sorry if im being a pain in the... where do i enter the argument as well as other arguments such as skipmemorycheck?

---

### Post by ago on 2008-09-23
start > run > cmd
go to the dir containing wubi.exe and and type
wubi.exe --skipmd5check

---

### Post by masterwillems on 2008-09-25
Well i installed it on my PC where Windows Vista Ultimate X64 is on and installation whent wel only reboot didnt work, no screen and wasnt comming up, save mode also didnt work.

And when i tried to uninstall it...it didnt work, well lets get it out of Vista manualy then, my computer specs:

Intel C2Q 6700
4gb memory
Nvidia XfX Geforce 8800GT 512mb
Windows Vista Ultimate x64

---

### Post by ago on 2008-09-25
can you check with easybcd to see if there was an entry in the boot menu?

---

### Post by masterwillems on 2008-09-25
> **ago said:**
> can you check with easybcd to see if there was an entry in the boot menu?

There was a entry in the boot menu but when i selected it and it would start up ubuntu i only saw something like the following:

Ubuntu started and everything looked normal
but when you would get to the loading screen of ubuntu (with the logo and the orange meter) you didnt saw that but only vertical yellow stripes (about 300 pixels wide and they wernt of the same length)
And when i tried the save mode (for graphical) i came in a text based linux but i could not login.

I removed most of the ubuntu files now from my computer but the only thing that is still standing is the boot menu (that i can select ubuntu.) very difficult to change that.

Edit: i would not mind to install wubi 8.10 again for a more accurat report, but first id like to know how i can get ubuntu out of my boot files when im done so i can keep my computer nice and clean.

---

### Post by ago on 2008-09-26
> **masterwillems said:**
> 
Edit: i would not mind to install wubi 8.10 again for a more accurat report, but first id like to know how i can get ubuntu out of my boot files when im done so i can keep my computer nice and clean.
You can use easybcd for that or from the control panel

---

### Post by masterwillems on 2008-09-26
> **ago said:**
> You can use easybcd for that or from the control panel

A college of mine knew a other way in windows, al check that first and if that doesnt work (although i think its 100% correct) i will try to use easybcd
You will hear if i succeded at 7PM GMT+1

---

### Post by masterwillems on 2008-09-26
> **ago said:**
> You can use easybcd for that or from the control panel

Thanks o great Ago for opening my eye's and see the convenience of easybcd.
(i just wanted to look if it also could be done without a tool:lolflag:)

Installing Wubi 8.10 now

edit:
Hmmm great talk about murphy's law...now i see everything....well i will keep you updated.

edit 2:
Well everything works fine, it even sees my Wlan card (8.4 didnt see it automaticly)
Adding a wlan connection is a little bit different and although i was just able to use the old version, i like the new way more.
I will post updates when i see something that is different then 8.4 and tell how i experience it.

edit 3:
Now i see it, there is finaly a indicator for the wlan signal strength, on my laptop i still use kwifimanager to see that.

edit 4:
My verdict until now:
There are nice improvements (like the network) in ubuntu 8.10 but i got to say that it isnt very stable (which isnt bad since it is still in alpha stage.) I have the feeling that the overall support in hardware is better then with 8.0.4 and im looking forward to a more stable version, until that time, I will use a dualboot of ubuntu 8.0.4 and windows vista ultimate x32 on my laptop and a dualboot of windows vista ultimate X64 with ubuntu 8.10 (although i probably wont use it untill there will be a more stable version.) (By the way, there isnt a "loading bar" when i start ubuntu 8.10.)

---

### Post by ZjosH on 2008-10-07
Today I tought... Beta's out... lets try wubi again... and IT WORKED! I now have a fully functioning Ubuntu system! I used the latest Wubi from the minefields :)

---

### Post by elfgoh on 2008-10-07
> **ZjosH said:**
> Today I tought... Beta's out... lets try wubi again... and IT WORKED! I now have a fully functioning Ubuntu system! I used the latest Wubi from the minefields :)

May I know where is where is "Wubi from the minefields"? Is it 8.04.1 from [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php) ?

---

### Post by ZjosH on 2008-10-07
> **elfgoh said:**
> May I know where is where is "Wubi from the minefields"? Is it 8.04.1 from [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php) ?

[http://www.wubi-installer.org/devel/minefield/](http://www.wubi-installer.org/devel/minefield/) this is the link to the minefields... You should know ofcource, this isn't meant for unexperienced people... I had to use it becouse of some weirdo bug I had in 8.04.1. If you can get it working with the normal beta I would reccomend that.

---

### Post by brandon88tube on 2008-10-07
> **kl.u said:**
> I also notice that some of the applications which has windows with height higher than the screen resolution do not have the scroll bar, hence I cannot get to the bottom of the window. This may be more of a Ubuntu problem than a Wubi specific problem. (Acer Inspire One is a sub notebook with a 8.5" screen and a resolution of 1024x600).
> **ago said:**
> Both issues look like generic Ubuntu problems

This actually seems to be a gnome problem as the same problems happened in Fedora. It is very noticeable when the resolution is set to 800x600 or lower. It may even happen on 1024x768 resolutions as well. I would like to seem them implement a scroll bar of some sort for problems like this. As for right now the best thing to do is use Alt+Click Drag. That lets you move the window anywhere, even outside the screen so that you can view the rest of it.

---

### Post by elfgoh on 2008-10-10
> **ZjosH said:**
> [http://www.wubi-installer.org/devel/minefield/](http://www.wubi-installer.org/devel/minefield/) this is the link to the minefields... You should know ofcource, this isn't meant for unexperienced people... I had to use it becouse of some weirdo bug I had in 8.04.1. If you can get it working with the normal beta I would reccomend that.

Thanks, your tip has been so helpful.

I have successfully installed intrepid beta using Wubi minefield.

---

### Post by Openrulers on 2008-10-11
I was trying to install Ubuntu 8.10b with Wubi 8.10rev510.
I was getting error messege with download.
I am using Zone Alarm 8.0 security Suite. 
Tried with disabling Zone Alarm Firewall.
This is what they saying.
[http://osalerts.zonelabs.com/osanalyze.jsp?record=ZLN08638527045097-1025/214f6b011ce6f403670010b4&tab=overview](http://osalerts.zonelabs.com/osanalyze.jsp?record=ZLN08638527045097-1025/214f6b011ce6f403670010b4&tab=overview)

[http://osalerts.zonelabs.com/osanalyze.jsp?record=ZLN08638527045097-1025/1d74c03011ce6bcc44200b6d&tab=overview](http://osalerts.zonelabs.com/osanalyze.jsp?record=ZLN08638527045097-1025/1d74c03011ce6bcc44200b6d&tab=overview)

What work around you suggest?

[COLOR="Red"]I believe Ubuntu 8.10 supports RAID utility.[/COLOR]
Cheers

---

### Post by mikedep333 on 2008-10-12
Openrulers, you could try downloading the latest iso manually and putting that in the same directory.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

However I think some other step would be required to do this based on last time I tried. I think you might have to use a console switch to tell it to use the iso rather than download a new one.

---

### Post by ago on 2008-10-13
> **mikedep333 said:**
> 
However I think some other step would be required to do this based on last time I tried. I think you might have to use a console switch to tell it to use the iso rather than download a new one.

If the ISO is the actual latest one, then it will be used, if a new ISO is made available on the server, wubi will try to use that instead so it will start to download. A simple trick is to disconnect the machine from the internet and force Wubi to use the available local ISO.

---

### Post by Openrulers on 2008-10-14
thank you mikedep33 and ago for your advice. 
I did the same and I added the programme to Zone alarm.

It worked well.
Asked for reboot. I rebooted correctly.
It started saying in the bottom of screen "system kernel Alive. System Kernel really alive".
then it gone to
(  2.286855) Can`t read CTR while initialising
loading please wait..
Busybox v1.10.2 Ubuntu 1.1.10.2-1ubuntu6

initramfs_

I tried with menu like safe mode, verbose mode, demo live CD. 
all ended with same error messege.
Please help

Where can i find a log file for that failed booting in Ubuntu?

---

### Post by ago on 2008-10-15
[http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)

If you still end up in busybox, boot in verbose mode and report the output of the following commands:

cat /proc/cmdline
cat /proc/partitions
cat /proc/mounts
grep err /casper.log
grep mount /casper.log

---

### Post by obsrv on 2008-10-24
It does not download cdimage for me :(

---

### Post by ago on 2008-10-24
today the release candidate is out, so the servers might be a bit stretched.
In any case please submit the log, it is in your temp folder, type %temp% in windows explorer.

---

### Post by xBIGx on 2009-01-29
Hey there all,
I've used a few different Linux distros in the past but for some reason since i upgraded my pc i wasn;t able to install any version of linux. Last night i stumbled upon the wubi installer, figured i would give it a shot. I must say from my point of view (I'm a Linux Noob) it had to be the easiest install of linux i have ever done!!! Also i'm using the Windows 7 Beta which ran and installed wubi with no problems. Just figured i would post my experience. 

Cheers
ckfisher

---

