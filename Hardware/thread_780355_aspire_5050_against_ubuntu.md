---
title: "aspire 5050 against ubuntu"
date: 2008-05-03
forum: Hardware
---

### Post by sardus76 on 2008-05-03
hi everybody!
ive just installed the last ubuntu on my acer aspire 5050 and ive got a series of problems...
1st i cant get the wireless to work ive got a on off button but i doesnt change anything, the terminali thingy finds the wireless card but cant get it to work!
2nd the audio doenst work and here again i dunno hoe to switch it on..:confused::confused:

3rd .... im trying to installed other program like messenger or emule but it doesnt work either! maybe something ubuntu friendly?

i hope somebody can help me !!!

thanks guyz!!!

---

### Post by Zorael on 2008-05-03
Please post the output of the following commands, entered in a terminal.
```
$ lshw -C network
$ lshw -C multimedia
$ aplay -l
```
(Omit the dollar-signs.)

---

### Post by sardus76 on 2008-05-04
hello there, thanks to reply!
 ive done what u told me to do, and now what s the next step?

---

### Post by sardus76 on 2008-05-04
> **sardus76 said:**
> hello there, thanks to reply!
 ive done what u told me to do, and now what s the next step?
hello there, thanks to reply!
ive done what u told me to do, and now what s the next step?

---

### Post by Zorael on 2008-05-04
Well, uh, enter those commands in a terminal, copy paste what it says and post it here.

---

### Post by LaHire on 2008-05-06
Hey there!, i too have a Acer Aspire 5050 and it gives me nightmares.
The results of lshw -C network:

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:16:5c:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes


the results of -C multimedia:

  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel


and for the aplay -l:

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


 I am a noob, but the "UNCLAIMED" part on the lshw -C network is kinda...suspicious, 

could this be the wifi on/off button?, how can i wrap the turn on/off function to another key?

thanks!

---

### Post by LaHire on 2008-05-07
i'm losing my faith.... :(

i have tried ndiswrapper...but i do not know what to do (or how to handle it)....

help?

thanks!

---

### Post by Zorael on 2008-05-07
Regarding your wireless, see if you can find anything of interest over at [http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros](http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros).

As for your sound, *do* check that you haven't muted any channels in alsamixer (run **alsamixer** from a terminal). If everything in there checks out, you can find comfort in that a lot of people have had issues with the snd_intel_hda driver, including myself. I found a solution wherein I added a line to /etc/modprobe.d/alsa-base, which fixed everything. There are a whole bunch of chipsets that use that driver, though, so I'm not sure this will help your card at all. Read this post of mine, and the following post I linked to in there.

[http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649)

Else, your best bet would be lurking [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu). Perhaps someone has already posted a similar bug, else you could add your own.

---

### Post by Icemanbr on 2008-05-08
Hi everybody,
I've seen lots of posts about wireless on Acer Aspire 5050. My laptop is an Acer 5050-4598 and i have the same problems on Ubuntu 8.04: wireless anda sound.
Other posts [http://ubuntuforums.org/showthread.php?t=512828&highlight=build+essentials]("http://ubuntuforums.org/showthread.php?t=512828&highlight=build+essentials")
have a way to configure and use wireless but we do need to install build-essentials package.  I can't install this package. Can you help me?

thanks.

PS: i'm a new user of linux and, as you can see, i don't speak english very well ;-)

---

### Post by Zorael on 2008-05-08
The build-essential package should be in the main repositories, so just open up Synaptic, search for it, tag it to be installed and apply.

Alternatively, enter this in a terminal.
```
$ sudo aptitude install build-essential
```

---

### Post by LaHire on 2008-05-08
Well...it worked!, :D

Thanks to :
[http://ubuntuforums.org/showthread.php?t=768871&highlight=atheros+AR5BXB63](http://ubuntuforums.org/showthread.php?t=768871&highlight=atheros+AR5BXB63)

For that, i used the drivers that you can found here:

[http://support.acer-euro.com/drivers/notebook/as_5050.html](http://support.acer-euro.com/drivers/notebook/as_5050.html)

EDIT:
[B]First, disable the restricted drivers on System >> Administration >> Restricted Drivers:

* Atheros Hardware Access Layer (HAL)
* Support for Atheros 802.11 wireless LAN cards
[/B]

I used the one called 

"Atheros_WLAN_XB63_Driver_5.1.1.9_XP.zip"

and i isntalled it with "Windows Wireless Drivers" (check synaptic), but, if you like the "pro/geek way" (a.k.a. console), you can do this:

$ sudo apt-get install ndisgtk

then...
"unzip" the recently downloaded Atheros driver

System >> Administration >> Windows Wireless Drivers

there, click "Install new driver", and then look for the .inf file. 
Install it

and sudo reboot yourself, and the machine (well...not yourself)

It shoul work. i hope

good luck! :)

---

### Post by Icemanbr on 2008-05-08
Hi!
Thanks Zorael. I did'nt install the build essential package, but my wireless is working!
My sound problem isn't fixed yet. I tested my microphone line-out and it works, instead of my speakers don't work anyway.
So, sardus76, you can try your phones.

About wireless, i installed the ndiswrapper and configured it with my windows' drivers. Then, i disabled "atheros hal" on Hardware Monitor. After this, my net manager detected my wireless card, but still didn't work.
On the left side of timer, i choosed wireless network. There isn't anything, but i put my wireless network's name conection and ... my wireless got on!

Now, my laptop found available wireless network around ... and everything finishes good.

Thanks everybody for your atention and help.

---

### Post by Darkchef on 2008-05-11
> **LaHire said:**
> Hey there!, i too have a Acer Aspire 5050 and it gives me nightmares.
The results of lshw -C network:

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:16:5c:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes


the results of -C multimedia:

  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel


and for the aplay -l:

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


 I am a noob, but the "UNCLAIMED" part on the lshw -C network is kinda...suspicious, 

could this be the wifi on/off button?, how can i wrap the turn on/off function to another key?

thanks!
yeah I also have the same problems with the wireless and sound with my acer aspire 5050 laptop. ive actually wanted to install ubuntu on here for a while as i have preinstalled vista on here still which is just stupidly slow.... any new fixes for this ??

---

### Post by inportb on 2008-05-11
Is the "AR242x 802.11abg Wireless PCI Express Adapter" the chipset of AR5007EG? Because that's what I've got and that's what it shows up as. If that's the case, there is an **i386-only** native driver for you that does not depend on WinXP drivers.

You can get this patched MadWifi driver: [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)
Or this one if you want injection support (for Aircrack-ng and the like) too: [http://files.filefront.com/madwifi+nr+r3366ar5007airktgz/;10002443;/fileinfo.html](http://files.filefront.com/madwifi+nr+r3366ar5007airktgz/;10002443;/fileinfo.html)

First, enable the proprietary driver. And make sure you have build-essential and the appropriate linux-headers installed, because you're going to be compiling this one:

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Next, unpack your newly downloaded tgz, and run:

```
make
sudo make install
```

Then unload the old drivers and enable the new drivers:

```
sudo modprobe -r ath_hal
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

---

### Post by LaHire on 2008-05-12
Sometims madwifi does not work with certain chipsets...

and ndiswrapper is not a...very cute way to solve things (because it uses windows drivers)


in my previus post, i commented about how i solved this issue with wifi.... altough you can try with madwifi. 

Hope it works for you! :-D


sorry about my -bad- english :)

---

### Post by Darkchef on 2008-05-14
so theres no way of getting the sound working at all then ?? i was going to attempt to install it on my laptop but im having doubts..

---

### Post by rajagurusanjeev on 2008-06-10
tHIS wORKS.. gREAT. Can Somebody Help me with Sound?

---

### Post by LaHire on 2008-07-04
wow....

back to the main wifi problem.

today, i turned on the laptop and....no more 

maybe an update?

---

### Post by Crana on 2008-07-05
Bah, I can't even INSTALL Ubuntu on my Aspire 5050 :(  I get a BIOS BUG error and the progress bar freezes :(

I've been able to install earlier versions of Ubuntu with no problems though.

---

### Post by InTheShires on 2008-08-01
> **Crana said:**
> Bah, I can't even INSTALL Ubuntu on my Aspire 5050 :(  I get a BIOS BUG error and the progress bar freezes :(

I've been able to install earlier versions of Ubuntu with no problems though.

My post here [http://ubuntuforums.org/showthread.php?t=766100&page=2](http://ubuntuforums.org/showthread.php?t=766100&page=2) tells you how I got round this problem, which was driving me nuts too!

---

### Post by Schok on 2008-12-31
> **LaHire said:**
> wow....

back to the main wifi problem.

today, i turned on the laptop and....no more 

maybe an update?


Hey im using 8.10 with aspire 5050. Had the wireless solved, but everytime i reboot i need to manually connect it. Here's what i do:

1.Right click on the connection icon and click on 'Edit Connection'
2.On the 'Wireless' tab, edit the connection that you're trying to connect
3.I made sure 'system setting' is ticked [ticked it the 1st time and it doesnt need to be retick-ed]
4. Click OK and it will prompt u for ur password, and then it will try to connect to the network.

Had to do this everytime i reboot, since clicking on the network icon and choosing my connection will only say that im am disconnected from the network. I hope there's an easier way..

---

