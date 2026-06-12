---
title: "turn on my wireless hardware, how?"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by jollyr0ger on 2005-05-12
Hi! I've got an Acer 4101Lmi, a centrino notebook. my ubuntu find him automatically and driver seem that are working. i've visited my LUG, they said that the wireless module, are not ignited.
thesre is the button tu turn on and off the wireless, in windows it work, but in linux not.
how i can turn on it?

thanks

---

### Post by Rik on 2005-05-12
Hi.  This is probably not the most helpful reply you`ll ever see.

I have managed to use wireless on my Acer TravelMate 4100LMI, using a Hoary pre-release, without lots of messing around.  However, in a fit of stupidity I decided to nuke my installation and re-install.  Since then I haven`t been able to make the wlan work, and I can`t remember how I got it working first time around.  But it is possible!

I`m not sure if the 4101LMI is the same shape as the 4100LMI, but the wireless LAN activation button will not light up even when the wireless link is up, so this is nothing to be worried about.  The key things are to check the output of  /var/log/messages and dmesg to see how if things are working.

I do remember I had to write a little script to change the channel / essid / mode (I use Ad-Hoc) and manually add some configuration to /etc/network/interfaces as the Gnome networking tool never did the trick.

I will try again to get this little pig working, and hopefully document what I did!

---

### Post by az on 2005-05-13
[QUOTE=jollyr0ger]Hi! I've got an Acer 4101Lmi, a centrino notebook. my ubuntu find him automatically and driver seem that are working. i've visited my LUG, they said that the wireless module, are not ignited.
thesre is the button tu turn on and off the wireless, in windows it work, but in linux not.
how i can turn on it?

thanks[/QUOTE]


You need to know what hardware you have

lspci -v

That will show you the pci bus hardware.

You peobably have a wireless card that is not supported natively in linux.  If it were supported, Ubuntu would have turned it on.  You probably can get it working by using ndiswrapper.

Basically, that uses your windows driver for the device in linux.

Look up ndiswrapper.  It is included precompiled in Ubuntu.  I am pretty sure that ndiswrapper-utils is even installed by default.

---

### Post by Photog_7 on 2005-05-13
Actually, ndiswrapper 1.1, which is what you need, is NOT included with the latest version of Ubuntu.  If you drop to a terminal window and type the ndiswrapper command to install your wireless card driver (which you must find yourself from the Windows XP drivers,) you will find that ndiswrapper still needs to be downloaded and installed.  I'm a Linux newbie, so that's what stopped me in my tracks and sent me back to Linspire, which includes ndiswrapper.  I *was* able to get my wireless driver working in Linspire, but ndiswrapper and its utilities do not even show up in the list of software that you can install from the Ubuntu distribution.  I tried following the directions at:
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)
but unfortunately, they stop working when I get to steps 6 and 7, probably because I am running an AMD64 and the instructions are written for Intel CPUs.  The two new .DEB package files are not there after step 6.
   This would all be much easier if Ubuntu just had ndiswrapper 1.1 included in the distribution.  If I could just get wireless working, I'd switch back to Ubuntu in a heartbeat.

---

### Post by snop on 2005-05-13
Hi,

I own an Acer Travelmate 4001Wlmi. My wireless work fine. Looking at your laptop specs they seem to be similar to mine regarding to wireless. Since it's a centrino the driver you need is ipw2200 (there's no need for ndiswrapper I guess).

Check if your driver is already loaded:
```
lsmod | grep ip2200
```

My output as an example (you should see something similar):
```
snop@portatil:~ $ lsmod | grep ipw2200
ipw2200                91528  0
ieee80211              24804  1 ipw2200
ieee80211_crypt         5736  3 ieee80211_crypt_wep,ipw2200,ieee80211
firmware_class          9984  1 ipw2200
```

If it's loaded then probably your wireless settings are not right. Check [this](http://ubuntuforums.org/showthread.php?t=33057)  for some advice on how to manually configure and test your wireless connection. I'm also working on packages for new drivers since ipw2200 supplied with hoary is quite buggy (check  [this](http://ubuntuforums.org/showpost.php?p=167782&postcount=46) ). Keep in mind that those packages are very new yet and not tested (only tested be me by now).

SnOp

---

### Post by luca_linux on 2005-05-13
Just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by az on 2005-05-13
[QUOTE=Photog_7]Actually, ndiswrapper 1.1, which is what you need, is NOT included with the latest version of Ubuntu.  If you drop to a terminal window and type the ndiswrapper command to install your wireless card driver (which you must find yourself from the Windows XP drivers,) you will find that ndiswrapper still needs to be downloaded and installed.  I'm a Linux newbie, so that's what stopped me in my tracks and sent me back to Linspire, which includes ndiswrapper.  I *was* able to get my wireless driver working in Linspire, but ndiswrapper and its utilities do not even show up in the list of software that you can install from the Ubuntu distribution.  I tried following the directions at:
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)
but unfortunately, they stop working when I get to steps 6 and 7, probably because I am running an AMD64 and the instructions are written for Intel CPUs.  The two new .DEB package files are not there after step 6.
   This would all be much easier if Ubuntu just had ndiswrapper 1.1 included in the distribution.  If I could just get wireless working, I'd switch back to Ubuntu in a heartbeat.[/QUOTE]


ndiswrapper is included in Ubuntu. the modules are included in the stock kernel and the ndiswrapper comman line utility is in the ndiswrapper-utils.  They are on the install cd.

There are few reasons to need the very latest version of ndiswrapper, but you can always compile it from source, using the utilities on the cd.

Most wireless cards that require ndiswrapper because they do not have linux drivers work out-of-the-box for ubuntu.

When the next version of Ubuntu will be ready for release, the version of ndiswrapper that is then being used will become the version that ships.  This is how it works.  Once something is released, you cannot change it, just make security and bug fixes.

---

### Post by luca_linux on 2005-05-13
Why not using ipw2200 instead of ndiswrapper? It works great to me, with WPA too.

---

### Post by Photog_7 on 2005-05-13
[QUOTE=azz]ndiswrapper is included in Ubuntu. the modules are included in the stock kernel and the ndiswrapper comman line utility is in the ndiswrapper-utils.  They are on the install cd. . . . [/QUOTE]

azz, as I said before, I'm a Linux newbie, so please forgive my ignorance.  When I dropped to a command line interface in the terminal window, I typed the line:
ndiswrapper -i ~netbc564.inf
I was in the same directory where I put the two 64-bit driver files for my Broadcom wireless card, including netbc564.inf.  I received an error message which indicated that ndiswrapper was a bad command.  Do I have to install the ndiswrapper-utils from the CD, and if so how do I do that?  When I run the Synaptic Package Manager I do not see anything about ndiswrapper-anything in the list, even when I put the CD in.  What am I doing wrong?  As I said before, I successfully did this in another distribution, so I must be missing something.

---

### Post by Psy31 on 2005-05-14
Hi,
 i don't think use NDiswrapper is a good way for using your wireless  [-X 

Your wireless card is recognize by ipw2200 so use it !  ;-) 
What the result of :
 cat /sys/bus/pci/drivers/ipw2200/0000:06:03.0/driver/0000:06:03.0/rf_kill
(adapt the '0000:06:03.0' to your install) ??

If 2, rf_kill is active so your card is unactive. Click on your panel button and re-do the cat /sys/...
To have your wireless card active, the result have to be at 0.

Other think :
 what the result of iwconfig ?
 and iwlist scan (for scanning your access point) ?

PS : sorry for my bad english   :-# 


++ 
 - Psy -

---

### Post by cowdinosaur on 2005-09-02
I've got an Acer Travelmate 3212 and I have the same problem with the ipw2200 driver on Ubuntu Hoary.

In essence, cat /sys/bus/pci/drivers/ipw2200/0000:06:03.0/driver/0000:06:03.0/rf_kill will return a 2, meaning the hardware switch is off. Nothing I do can switch on the orange led button for my wireless. Not even acerhk

Now, my friend lent me a Mepis 3.3.1 CD, and it works out of the box. The orange lits up like a bloody christmas tree upon booting. I'm trying to figure out how? Does anyone know how I can find out what patches and kernel configuration the Mepis kernel use?

I'm not giving up! I'm sure it's possible!!!

---

