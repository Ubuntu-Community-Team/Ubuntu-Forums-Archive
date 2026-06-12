---
title: "how to get D-Link DWA-525 working on Ubuntu 10.04"
date: 2010-08-23
forum: Hardware
---

### Post by Golesy on 2010-08-23
Hey guys,

so today i bought myself the DWA-525 wireless PCI desktop card, and had a heck of a time installing it in ubuntu 10.04, until i found this! So i thought i'd share it with others who are in the same situation! I tried to make this a noob friendly as possible

[B]MAKE SURE THE CARD IS NOT IN YOUR COMPUTER BEFORE STARTING!!
[/B]

0. Remove the PCI card from the computer (if you plugged it in already)

1. Download the attached file (i didn't make this, and i don't know where i found it, its a result of 4 hours of digging through the net :P)

2.unzip the file

3.open a terminal and find the unzipped folder

4.once in the folder type "make" and hit enter

5.When that's done, type "sudo make install" and hit enter

6.once thats complete, turn off your pc and plug in the card

7. turn on your pc... and DONE! it should be working wonderfully now! or at least it did for me. good luck anyone trying this!

---

### Post by Arte Aplicada on 2010-09-08
Man, I tried EVERYTHING in the last 2 months, and the only thing that worked was THIS. I was as simple as installing the drivers with the card disconected! AMAZING!

Thanks! I love you!

Jorge.-

---

### Post by chuck.tweedy on 2010-09-19
I just used the above zipped driver code with 10.10 (beta) & a DWA525 - It worked!!
Thanks - I've been trying for a week to get this thing online
You rock Golesy

---

### Post by Melnarie on 2010-09-20
Thanks _[Golesy]("http://ubuntuforums.org/member.php?u=1135921")_ this thing works perfectly!

Oh..and a hint, you don't even have to remove the card, i forgot, and was sure i made a mistake...but hey...it works!

---

### Post by TeaFiend on 2010-09-25
Yay, it worked (after hours of stuffing around)! I also didn't have to remove the card. Thanks so much.

---

### Post by TeaFiend on 2010-09-26
I found where the driver came from: [http://ftp.dlink.ru/pub/Wireless/DWA-525/Drivers/Linux/](http://ftp.dlink.ru/pub/Wireless/DWA-525/Drivers/Linux/)

I was a bit worried about it being an alpha version, but I guess coming directly from a d-link site gives it a bit more credibility, though I couldn't find an actual link to the driver the from the Australian, US or Russian sites.

---

### Post by jratliff on 2010-10-04
Thanks a lot. This saved me untold time and frustration. It worked without removing the card - just needed a reboot after installing.

---

### Post by Lloyd Welch on 2010-10-15
I was abit scared, but after following the instructions; I was able to get it to work.

THANKS!!

---

### Post by eldudorinio on 2010-11-10
Hi,

The driver seems to have installed correctly, but I cannot seem to connect to my wireless router.

What I get from *lshw -C network*:

*-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: wlan0
       version: 00
       serial: f0:7d:68:5f:4c:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic-pae firmware=N/A latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn

And this is what I get from *iwconfig*:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


I have also configured the SSID, MAC Address and password (WPA Personal) of my router in the Network Connections.

Could it be that my wireless adapter does not work properly?
Any help is much appreciated :)

---

### Post by eldudorinio on 2010-11-11
Hi,

After following the steps in these threads:

[http://ubuntuforums.org/showpost.php?p=10055176&postcount=4](http://ubuntuforums.org/showpost.php?p=10055176&postcount=4)
and
[http://ubuntuforums.org/showpost.php?p=9660765&postcount=4](http://ubuntuforums.org/showpost.php?p=9660765&postcount=4)

I managed to get the wireless adapter to work.

Basically the only thing I was missing was to blacklist rt2800pci driver in the /etc/modprobe.d/blacklist.conf file

Also in the 2nd link I mention above you can find newer drivers to the ones posted [a few posts above]("http://art.ubuntuforums.org/showpost.php?p=9893068&postcount=6")

Thanks :)

---

### Post by squack on 2010-12-12
Work just fine thank you very much!! Awesome!

---

### Post by this_costs_more_cell_bill on 2010-12-29
You won't believe this, but I used the attachment & followed the steps from [Golesy]("http://ubuntuforums.org/member.php?u=1135921")'s first post, and though spending lots of money on an international cell call, I manage to guide a guy that don't even know where the keys are on the keyboard and we hardly agreed on what is the pronunciation of each character from each word! After all steps were followed, I used teamviewer to get control on his desktop through lots of firewalls and NATs, and fixed the sound in Ubuntu as well.

All due to exactly detailed & simple steps wrote by [Golesy]("http://ubuntuforums.org/member.php?u=1135921") !!!
Dude, I would hire you to write documentation and tutorials!

---

### Post by hamid1362512 on 2011-01-20
taaaaaaaaaaaaaaaaanks 
:*************

---

### Post by lisofm on 2011-02-03
Great job. Works like a charm.
Thanks..!

---

### Post by Overkille on 2011-02-15
Hey there buddy,

Thanks a lot for this! You rock dude! Works awesome!

---

### Post by Lorenzon Diego on 2011-03-18
Thank you for the info.
It worked fine for me.
Now the WIFI connection is working, but the sound disappear.
Sombodi know how to resume the sond?
Thanks in advance:)

---

### Post by pietro1963 on 2011-03-22
Just try it,  on a Dell GX150, not problem with 10.04

I began with 10.10 and no card activation. Tryed different installation as descrive as above form different threats, with no success.
new user of linux and Ubuntu

---

### Post by gbernadet on 2011-04-04
Awesome! I just had to deactivate the rt2800pci driver as eldudorinio did, and everything works just fine!! Thank a lot!!

---

### Post by jackk32 on 2011-04-21
thank you!!

---

### Post by denisk on 2011-05-05
Only after following [this advice]("http://ubuntuforums.org/showpost.php?p=10055176&postcount=4"), namely editing black list, was I able to make my DWA-525 work. Without blacklist driver installation hasn't worked in Kubuntu 11.04.
Thank you for this topic, it makes so many people happy!:popcorn:

---

### Post by Reaper450 on 2011-05-26
Confirming this works for 11.04 after blacklisting the ralink drivers like so

follow instructions for installing the driver that golesy (legend :guitar: ) gave but before rebooting do the following....

```
gksudo gedit /etc/modprobe.d/blacklistconf
```then add

blacklist rt2800pci
blacklist rt2x00pci

save then exit (after you exit it may give some errors about file not found, just ignore them it still works) then shut down, put the card back in and start her up. It should all work fine then and also fixes problem some have had with natty hanging when trying to shutdown or reboot.

EDIT: just found out that after any kernel update you will need to repeat step 5 on golesy's list. That is go into the folder where the driver is and type

```
sudo make install
```

then reboot

---

### Post by jcpache1 on 2011-05-27
Thank you soo much. Spend a hour or so trying just the blacklist thing, and even different wireless cards. Finally got it working

---

### Post by Hradcany on 2011-07-17
I am really new, less than an hour on Linux. I downloaded the file cited above, extracted it, moved to that directory and typed "make" as instructed. Error: no makefile. So, I looked at the files and noticed that the makefile was actually "Makefile", so typed "make Makefile". Error: no rule. OK, I am stumped. All of the messages indicate that this process was facile. The only difference I can see is that I am using a later version (downloaded a day or so ago from the Ubuntu site). Please help and remember: I have never used Linux before.

---

### Post by Hradcany on 2011-07-17
Whoops! When I looked for my post, I realized there were more than three pages. I followed the blacklist advice and also discovered I was in the wrong directory. I am now using my wireless card. Thanks to the posters above. Sorry for the noise.

---

### Post by this_costs_more_cell_bill on 2011-10-09
This is still working in October 2011! :guitar:

---

### Post by pro_mvb on 2011-11-18
hi
I have a big problem  about installation of wireless driver in backtrak5:(
(I have a linux backtrack 5.)
I have  downloaded  dwa525 driver but when i write "make" , it shows me this error:

"```

root@bt:~/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# make
make -C tools
make[1]: Entering directory `/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools/bin2h
cp -f os/linux/Makefile.6 /root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/Makefile
make -C /lib/modules/2.6.39.4/build SUBDIRS=/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux modules
make: *** /lib/modules/2.6.39.4/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


```"

then , I created that folder by myself ( the folder name is "build")
and when I tried it again , it shows me this error in this time:
"```

root@bt:~/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# make
make -C tools
make[1]: Entering directory `/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools/bin2h
cp -f os/linux/Makefile.6 /root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/Makefile
make -C /lib/modules/2.6.39.4/build SUBDIRS=/root/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.39.4/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.39.4/build'
make: *** [LINUX] Error 2


```"
could you please help me how should I solve it?

with best regards.

---

### Post by pro_mvb on 2011-11-18
any body there??????????:confused:

---

### Post by pro_mvb on 2011-11-20
??????????????????????????????????????????????????:o

---

### Post by siddharthx64 on 2012-01-06
Thanks bro!
this worked, without any restarting. 

But the notification area stopped showing my network icon, and no amount of coaxing cud bring it back. 
finally, got the right way of solving that in [this post]("http://askubuntu.com/questions/4360/no-network-manager-icon-in-the-notification-area-so-i-cant-use-my-vpn-connecti")
hope it helps those rare guys who, in future, face my problem

---

### Post by elbakly on 2012-01-09
for me this did not work but i'm using 11.04  but  i solved it this way 

1. Install the card and power up the machine.

2. Open the terminal and run

lspci

In the list you will see:

Network Controller: Ralink Device 3060 0

So now we know what device we need drivers for.

3. Go to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and download the RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) drivers.

You’ll be prompted for your name and email but you don’t need to sign into anything.

4. Extract the package and cd to the directory.

5. We need to make a slight modification to the configuration for the driver:

nano os/linux/config.mk

And set:

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y

# Support Native WpaSupplicant for Network Manager
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

By default they are both set to ‘n’. Save and close the file.

6. From the top level directory, compile and install the driver:

sudo su
make && make install

You need to use ‘sudo su’ and not just ‘sudo’ so it creates the directories properly.

7. After compilation, and whist still root, modprobe the driver:

modprobe rt3562sta

You should get no output signalling success.

8. Now an important step. We need to blacklist a conflicting driver that will be loaded preferentially for this network card.

sudo nano /etc/modprobe.d/blacklist.conf

and enter the following line at the bottom of the file:

blacklist rt2800pci

Save and close.

9. Restart the machine.

10. When the machine is back up, verify the driver has been loaded and is being used by the device:

lsmod

You should see the following in the list:

rt3562sta     924607     1

11. Now, launch the Network Manager and it should have detected the available wireless networks and you can configure the one you want.

---

### Post by alexblodøks on 2012-03-07
edit: stupid question, i forgot to install gcc...

---

### Post by YashiroDK on 2012-09-17
Thank you man, It works to the perfection :)

---

### Post by gbirkett on 2013-02-17
Hello guys.
First of all thanks for making this forum such a nice way for learning to use ubuntu and linux.

I'm trying to make my wireless board works but i cant. In my last try i got these erros:

> root@dktp:/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# make
make -C tools
make[1]: Entering directory `/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools'
/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/tools/bin2h
cp -f os/linux/Makefile.6 /home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/Makefile
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o
/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:1646:10: error: unknown field &#8216;ndo_set_multicast_list&#8217; specified in initializer
make[2]: *** [/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [LINUX] Error 2
root@dktp:/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# ^C
root@dktp:/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# 

> root@dktp:/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# make install
make -C /home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux'
rm -rf /etc/Wireless/RT3060STA
#
#mkdir /etc/Wireless/RT3060STA
mkdir -p /etc/Wireless/RT3060STA
cp /home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/RT3060STA.dat /etc/Wireless/RT3060STA/.
install -d /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3562sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux'
make: *** [install] Error 2
root@dktp:/home/gabriel/Desktop/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2# 


I'm noob on linux and i don't know exactly what that means. Can anyone help me to find out how to fix that?

Thanks very much!

---

### Post by laprise on 2013-03-14
Hello,

Does this works with ubuntu server 12.04 ?

I have the DWA-525 5360.

When I do the command :

Make

 I get this error :



make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /home/laprise/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o
/home/laprise/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.c:1646:10: error: unknown field ândo_set_multicast_listâ specified in initializer
make[2]: *** [/home/laprise/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/laprise/2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [LINUX] Error 2


Please help, it's my second week trying to find the problem.

Thank you ! :)

---

### Post by vezolmi on 2013-04-11
For the 5360 model I solved it with [http://ubuntuforums.org/showthread.php?t=2008849&p=12302336#post12302336](http://ubuntuforums.org/showthread.php?t=2008849&p=12302336#post12302336)

Good luck!

---

