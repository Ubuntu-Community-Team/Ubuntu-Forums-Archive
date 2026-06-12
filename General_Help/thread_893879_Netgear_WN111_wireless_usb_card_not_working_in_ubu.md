---
title: "Netgear WN111 wireless usb card not working in ubuntu"
date: 2008-08-18
forum: General Help
---

### Post by Ryujon on 2008-08-18
Hello folks I am a relatively new user to linux and ubuntu HH, and I absolutely love it however I have one problem. My superfast Netgear WN111 usb wireless adaptor does not work with Ubuntu...only a prehistoric PCI adaptor that requires me to turn my computer around to catch the signal. Unfortunatly...this is a serious dealbreaker for me because lets face it computers suck without internet...however the Windows errors and messages are driving me to the point of insanity.

Somebody please tell me how I can get my internet on ubuntu 8.04 HH to work with the Netgear WN111 so I can use this great OS

Thanks
Pete

---

### Post by BlazinNightSkye on 2008-08-18
I have that same adapter, and sadly i have not figured how to work with it yet myself. I had read once that you have to take a special file out of the windows setup and put it in a specific folder under ubuntu. Though i do not know the details. hopefully someone has found a much easier way to do it.

---

### Post by x5x_tim on 2008-09-01
Same prob here. I am a super Ubuntu(/any Linux-ish OS) newb, but wanted to try it. I liked the simpleness of GNOME, so I decided if I could set up my wireless connection i would keep it... PCI-E realtek won't work. Netgear WN111 won't work. plz help out the newbs here:KS

---

### Post by Subban on 2008-09-01
One way to eliminate all the wireless probs could be to grab a wireless bridge wouldn't it? They just slap into the ethernet port and will connect to a wifi network themselves OS independent. 

Its either that or check for compatibility and pick up a cheap card, which I had to do a few years ago. At the end of the day the £10-£15 the netgear card cost was easily easier and less stressful than fighting with the existing card for two days only to lose at the end anyway. 

If I had to do it again, I'd try a wireless bridge as you also have more choice for positioning it for a better signal strength too.

---

### Post by AmpersUK on 2008-12-29
Yes, **same problem**. I bought a **DG834N** *(RangerMax Next Router)* which is Linux friendly in so much as they give you detailed instructions on how to get it working in Linux.

I bought the **WN111** as it works with the **DG834N** and found that whilst the **DG834N** has instructions for Windows, Mac and Linux, the **WN111** only has software to work with Windows.

I need the **WN111** for my **Notebook** which won't take cards.

I have added my tuppence worth here so I can learn whether there is anything in Linux for this to work.

Hopefully **Netgear** will come to the rescue?

---

### Post by orlox on 2008-12-29
Have you tried ndiswrapper??

Try installing ndisgtk from synaptic, and then look for the .inf file that should come with the installer for windows.

---

### Post by AmpersUK on 2008-12-30
> **orlox said:**
> Have you tried ndiswrapper??

Try installing ndisgtk from synaptic, and then look for the .inf file that should come with the installer for windows.

Thanks, I have been carefully through the WN111 CDROM and the only .inf file on the whole disk is the "autorun.inf" file.

Under the sub-directory "drivers" is a "setup.exe" program so I guess it is incorporated in that. But of no use to me :-(

---

### Post by kingcharles1666 on 2008-12-31
You will need to run the setup.exe file on a windows machine to get the files needed for ndiswrapper.
You could try getting the files by using wine but that may not work

or google for the files, maybe somebody posted them.

You could also try the Netgear forum if they can send them to you. But my experience is that they are not very helpful to linux users...

---

### Post by ju2wheels on 2008-12-31
If you have a cdrom with a setup installer for drivers instead of the driver itself, then try right clicking on the setup.exe and open it with the archive manager. This will typically allow you to extract individual files inside the installer. If not you will need to find a "setup unpacker" or "installshield unpacker" for Windows.

---

### Post by SteveDee on 2008-12-31
I had similar problems with a Netgear WG111v3 running under Hardy, and spent days trying to get it to work. 

Eventually I bought a SafeCom 54Mbps USB adapter for less than GB£15 and gave the Netgear adapter to my son to run on his Windows box.

The SafeCom unit works like a dream (in fact I now have 2).

I also find my WiFi runs more reliably now I'm using Intrepid.

Take my advice and get a cheap Linux compatible WiFi adapter...life's too short.

---

### Post by AmpersUK on 2008-12-31
[quote=kingcharles1666;6467352]You will need to run the setup.exe file on a windows machine to get the files needed for ndiswrapper.
You could try getting the files by using wine but that may not work

First of all thanks for your help.

I tried Wine and got the following *.inf files...

**netmw245.inf** and **oem0.inf**

Not sure which one it is but there is no hardship adding them both.

But I am new to this so which sub-directory should I add these files to?

Ampers

---

### Post by SteveDee on 2008-12-31
Its netmw245.inf.

Check this link: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

---

### Post by mixtri on 2009-01-07
> **AmpersUK said:**
> [quote=kingcharles1666;6467352]You will need to run the setup.exe file on a windows machine to get the files needed for ndiswrapper.
You could try getting the files by using wine but that may not work

First of all thanks for your help.

I tried Wine and got the following *.inf files...

**netmw245.inf** and **oem0.inf**

Not sure which one it is but there is no hardship adding them both.

But I am new to this so which sub-directory should I add these files to?

Ampers
Hello AmpersUK. Please help. I would appreciate if you could kindly send me the netmw245.inf fle you were able to extract usig wine. 
I have the same router and usb wireless adapter, but cannot seem to extract the windows file from the installation disk using wine. The process causes wine to hang then I have to shut down and start again.

Also, where possible please include the .SYS file as well, as I read in a thread somewhere that both files are needed for the installation i.e. both files should be placed within the same folder prior to installation using either ndiswrapper or ntgdisk.

Please let me know if you require an email to send the file across.

thanking you very very much in advance.

---

### Post by kill.dash.9.luser on 2009-01-28
go to [http://legroom.net/software/uniextract](http://legroom.net/software/uniextract) and download the software under windows.  copy the setup.exe to your hard drive, and right click on it.  you can extract the package (use the /b option) and an msi is extracted.  extract that the same way and you should get a windows folder that contains the drivers.  beats me which one we need to use, but at least you can get them and start experimenting... :)

---

### Post by Sheepdisease on 2009-04-06
To make your lives easier, I have extracted the .inf files from the installation CD (WN111 v2).

The files can be found here: [http://www.2shared.com/file/5264436/f17d8d56/files.html](http://www.2shared.com/file/5264436/f17d8d56/files.html)

---

### Post by x5x_tim on 2009-06-17
Thanks for those files, was just trying to get them out of the CD myself, but couldn't find them. It's strange, but when I ran a liveCD on my laptop (wich had vista installed with the driver) it just worked all of a sudden... So I thought the new release just supported it, but I guess the liveCD got my drivers...

---

### Post by Sheepdisease on 2009-06-17
Awesome, you are welcome!

---

### Post by x5x_tim on 2009-06-17
mmmm... those are not the files I am looking for I think... I got ndiswrapper installed properly, and I got wn111.sys from my windows\system32\drivers folder, but I can't find the right .inf file. [This](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB) document says it can run fine with ndiswrapper and netmw245.inf... So I copied netmw245.inf to the machine and try to install it with ndiswrapper -i [location]\netmw245.inf, but then it starts looking for netmw245.sys. So I try searching these forums for 'the' "sticky on Ubuntu on how to setup ndiswrapper" as pointed out in that doc. No luck. (can't I use the search engine or are the forumes jsut too crowded with ndiswrapper questions?

I hope you can help me,

x5x_tim


EDIT: I got a whole bunch of files out of the setup package using the above described extracting method, including netmw245.in, wn111.inf and wn111.sys... let's see how this one turns out!

EDIT2: YEAH. "netmw245: driver installed
device (0846:9000) present" :D
Now I'll just have to find out how to actually **use** it :P
let's reboot!

---

### Post by AmpersUK on 2009-06-17
> **mixtri said:**
> [QUOTE=AmpersUK;6468801]
Hello AmpersUK. Please help. I would appreciate if you could kindly send me the netmw245.inf fle you were able to extract usig wine. 
I have the same router and usb wireless adapter, but cannot seem to extract the windows file from the installation disk using wine. The process causes wine to hang then I have to shut down and start again.

......

Please let me know if you require an email to send the file across.

thanking you very very much in advance.

Sorry, I have just noted this. The files I downloaded weren't the right files so I have still not got it working. I have now wired direct to the lounge and given up on wireless.

---

### Post by x5x_tim on 2009-06-17
Yeah. I did it. Guess how I am posting this message?

I&#314;l tell you how, over wlan0 :D

What I did was:
Install ndiswrapper
Get the wn111.inf & wn111.sys & netmw245inf files out of the setup.exe file on the installation CD
sudo ndiswrapper -i netmw245.inf
Plug it in
sudo modprobe ndiswrapper
Wait... Wait... 
Try to iwconfig
Wait... Wait...
Pick network
Surf the net :D


x5x_tim

---

### Post by frankida on 2010-03-05
> **AmpersUK said:**
> [QUOTE=mixtri;6510294]

Sorry, I have just noted this. The files I downloaded weren't the right files so I have still not got it working. I have now wired direct to the lounge and given up on wireless.


I too gave up however go to Synaptic Package Manager and try installing the Gnome Network Admin.

Started working for me.  

Frank

---

### Post by AmpersUK on 2010-03-05
I'll try that in the morning, thanks.

---

### Post by pasqualino31 on 2010-03-11
ndiswrapper -l
"netmw245 : "Driver installed"

lsusb
"Bus 001 Device 003: ID 0846:9000 Netgear inc. WN111(v1) ReangeMax Next Wireless"  

iwconfig
"lo    no wireless extensions" 
"etho  no wireless extensions" 

This device is currently working in the same machine under win2k.

Any suggestions?
:-? [http://ubuntuforums.org/images/smilies/icon_confused.gif](http://ubuntuforums.org/images/smilies/icon_confused.gif)

---

