---
title: "Wireless"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by dannytyson on 2007-08-27
ok well i have a research machines laptop from school which i was allowed to keep and would like to install ubuntu on. The problem is i cant find a driver for my wireless card. the card is a Microstar International MSI 8366 1814 0201 G wireless adapter. the driver i can only find from RM site the spec is:
Processor
    * Mobile AMD Athlon™ 8482; XP-M (LV)
    * Front Side Bus: 266Mhz
Chipset
    * VIA KT266
    * Cache: 512K Level 2
    * Supports PC-2100 DDR RAM
Memory
    * Standard DDR SDRAM - 256MB
    * Maximum DDR SDRAM - 1GB (2*512MB SODIMMs) 
Storage
    * Hard Drive - 20GB, 40GB or 60GB EIDE hard drive
    * CD-ROM x 24 (optional upgrade to DVD-ROM or DVD/CDRW Drive)
 Display
    * 14.1" XGA TFT LCD: up to 1024 x 768, 32-bit colour
 Video
    * Integrated S3 ProSavage DDR
    * Up to 32MB shared memory
    * 256 Bit
    * 2D/3D Graphics Accelerator
    * 4x AGP architecture graphics capability
Audio
    * AC97 Codec
    * Two built-in speakers
    * Microphone-in and headphone-out

The driver is here [http://www.rm.com/_RMVirtual/Media/Downloads/nB3000_WiFiG.exe]("http://www.rm.com/_RMVirtual/Media/Downloads/nB3000_WiFiG.exe")

Thanks

---

### Post by dannytyson on 2007-08-27
Please Help me!

---

### Post by dannytyson on 2007-08-28
I have no idea how to install my driver i need a step by step on how to use this prog. really need the help this is the only reason im thinking of goin back to XP. I dont know how to install things and struggle to fint tutorials that i understand. Can anyone help me please?

---

### Post by siralphred on 2007-08-29
> **dannytyson said:**
> Why does nobody help? I am trying to find how to install wireless card in linux (xubuntu) and your tellin me u all read without knowing how to do it? Cheers for nothing

what card is it? if by any chance its a broadcom, then go here [http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless)

---

### Post by dannytyson on 2007-08-29
That i have made over 3 posts now and not one single word of help i have an msi mini pci in the laptop it is a msi 6833 wireless g card. the card is in the connections list but will not enable so guessin it cant enable it all i want is an easy understandable guide when on google i get linux able users doin stuff i have no idea what they mean

---

### Post by lavinog on 2007-08-29
looking at that driver it looks like you may want to check out this link
[http://ubuntuforums.org/showthread.php?t=525833]("http://ubuntuforums.org/showthread.php?t=525833")

What I did was I used windows to extract the files from the archive (it could be done in linux via wine, but tI had a winxp computer handy so I used it.)

In the xinxp folder of the driver there are rt2500.inf and rt2500.sys
I then did a search for rt2500 and found the above page.

those files could also be used with ndiswrapper if that other page doesn't help, but since I don't have that type of card I am not sure I can help you further...but that should get you headed in the right direction.

Before you start getting frustrated you should keep in mind that getting help from the forums will take time...If you have ubuntu (or any distro of linux) installed then take some time to get to know it.
not having wireless capability shouldn't be discourage you from continuing on.

Some things that can help your situation would be to be more specific with your thread title.
Many people are just going to read the thread title, so it is important that you name it carefully.
There are thousands of threads that are titled "wireless problem," "ndiswrapper," or "why won't it work." Many people just skip it because they don't have the time to read every post...but if you renamed the title to something like "research machine laptop: msi wireless" someone would scan the forum and may say "hey i have the same machine, or card, I can probably help."

If you like tinkering with stuff, Ubuntu is a great way to start with linux. If you are just looking for a replacement for windows without getting your hands dirty ubuntu is also a great option, but expect missing functionality...this is not because ubuntu is unfinished or broken but many times it is due to legal reasons.

---

### Post by RageOfOrder on 2007-08-30
Here's some quick ndiswrapper instructions.

Take the two files given by the previous poster and put them in a folder.
Then install ndiswrapper (it's in synaptic)

Once you have it installed, enter the following commands

sudo ndiswrapper -i /path/to/file.inf
sudo ndiswrapper -m
sudo echo ndiswrapper >> /etc/modules.autoload.d/kernel-2.6


Now you should have a working wireless adapter. Either use
dhcpcd wlan0
to connect, or use a graphical tool of some sort.

---

### Post by dannytyson on 2007-08-30
i know nothing of command i need a step by step seriously where these commands go and when but really guys thanks for helpin

---

### Post by benson444 on 2007-08-30
Enter the commands RageOfOrder gave you in a terminal, Applications > Accessories > Terminal, pressing enter after each line.

Oh, and when you have to enter your password you won't see any characters on the screen. That's what should happen. Just type the password and press enter.

---

### Post by RageOfOrder on 2007-08-30
> **benson444 said:**
> Enter the commands RageOfOrder gave you in a terminal, Applications > Accessories > Terminal, pressing enter after each line.



You'll have to replace "/path/to/inf" with the path to the .inf file included in that zip file.

So if the file were called driver.inf and in the /home/yourname/ folder, the command would be

sudo ndiswrapper -i /home/yourname/driver.inf

---

### Post by rustybronco on 2007-08-30
Have you tried a different distribution to see if it may work with your hardware? or possibly a different version of bunu? i.e. 6.06 6.10 7.04?

what version of ubuntu are you using?

do you know the wireless card number or chipset?

this may help... [http://linux-wless.passys.nl/query_part.php?brandname=MSI](http://linux-wless.passys.nl/query_part.php?brandname=MSI)

do you know how to access the terminal?

I'm not that proficient with linux yet, but will help with all that I can. 
I've been using ubuntu/sabayon since october '06 and i've yet to ask a question, all that I needed to know I have found with a search.

***edit*** If your chipset is a rt2500 it works on my desktop machine in fiesty (7.04) although at times it will quit and I have to do a " sudo ifdown rausb1 " and then a " sudo ifup rausb1 " in the terminal, but that is the price I pay (small in my opinion) to use linux... 7.04 on my laptop works just fine.

welcome to learning, It's a good thing no?

---

### Post by dannytyson on 2007-08-30
ill let you know

---

### Post by dannytyson on 2007-08-30
> **RageOfOrder said:**
> sudo echo ndiswrapper >> /etc/modules.autoload.d/kernel-2.6

I couldnt do that one? unknown syntax or somethin cant remember exact wording

---

### Post by linux noooob on 2007-08-30
Try wicd it works for me, easy graphical interface!!: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by dannytyson on 2007-08-30
ok i just installed that wicd and it sees my network but at -1%? and wont connect? Ideas?

---

### Post by dannytyson on 2007-08-30
Also in applications/system/network  should i have anything set in there? i have to put a essid if i want to activate it i cant just enable it

---

### Post by dannytyson on 2007-08-30
its a 2500 i seem to have installeed the drivers but need help with configuring the whole network connections. i have also installed Wcid manager and it finds my network but with -1% strength so im guessin something funny goin on there as its next door

---

### Post by imdano on 2007-08-30
You have to make sure you get the newest update of wicd for things to be displayed right if you're using a card with the rt2500 driver. First make sure you have version 1.3.3 of wicd installed, then go here:[http://wicd.svn.sourceforge.net/svnroot/wicd/testing/](http://wicd.svn.sourceforge.net/svnroot/wicd/testing/)

Download all the new .py files and put them in your /opt/wicd/ folder.  Close the tray icon and gui if you have them open, then open a command prompt and type ```
sudo /etc/init.d/wicd start
```

Open up wicd, click preferences, and choose "ralink legacy" from the wpa supplicant driver menu.  Then try connecting.  It might work, but it might not.  Unfortunately your driver doesn't really follow any standard linux conventions for encrypted networks, which makes it difficult to integrate into a connection management app.  We're hoping to have it working for the next version of wicd, though.

---

### Post by rustybronco on 2007-08-31
Yes on my rt2500 strength doesn't report correctly either, but connects just fine. 

I'm not at home to check but this should be correct, please excuse me if i'm a little off in my statement.
 
first you need to enable networking, right click on the networking icon (top rh looks like two monitors) and make sure networking is enabled then go to... systems>applications>network and click on it, it will bring up a window 
un-check enable roaming and enter your essid (network id name) next enter your WEP (the rt2500 I believe cannot use wpa) in either hex (example... d35188bbde) or ascii (example... nonewshoes) then click on ivp4 (for me I have a problem and this is how mine works) and it will bring up changing??? interface, when the task bar is finished close the window then go back to "systems>applications>network" click on it again and click on use DHCP! it will enable the interface (same as before) when its done with it's MARCH :) tick the wireless box and un-check the others.

It should be working.
if it doesn't work play with it (thats how i learn) or ask again for help.

***you do have the essid and passkey from the router dont you?***

THIS IN FIESTY 7.04 what do you use?

---

### Post by dannytyson on 2007-08-31
yeah the router is names Fredrick (which is Essid) and the pass is acs6c6c863a55 which is hex?

---

### Post by rustybronco on 2007-08-31
> **dannytyson said:**
> yeah the router is names Fredrick (which is Essid) and the pass is acs6c6c863a55 which is hex? to me this code doesn't sound correct, and if I believe the hex code in this box goes only to the letter f... 0-1-2-3-4-5-6-7-8-9-a-b-c-d-e-f  , someone please correct me if i'm wrong, it has been awhile.
> **dannytyson said:**
> Will do thanks but it didnt have replies for a while thats why i posted this one. Just got annoyed you know how it is

Dan life is a challange, it's how we handle it that makes us human or not. 
in time it will come if you choose.

---

### Post by dannytyson on 2007-08-31
Managed to instlall the wireless and very chuffed and thanks for all the help and sorry for the moaning ive done :D

---

### Post by rustybronco on 2007-08-31
Glad to hear it...

---

### Post by dannytyson on 2007-08-31
Im in love already! But more questions. Can the program that makes the screen turn be installed in xubuntu? :D

---

### Post by RomeReactor on 2007-09-01
Hi. Do you mean the desktop effects, such as the rotating cube and transparencies? If so, and If your PC only has the S3 ProSavage integrated video, as you said n your first post in this thread, then you would probably need another video card; I think the linux drivers for Savage cards don't give you direct rendering, which means no 3D.

I've found [this thread]("http://ubuntuforums.org/showthread.php?t=104355")--which mentions what looks to be your Savage card--and it says you need to install the newest (at the time) Xorg from [here]("http://dri.freedesktop.org/wiki/") to get direct rendering. However, the thread is two years old and the [page with the instructions]("http://doc.gwos.org/index.php/3D_Graphic_Cards") is down at the moment, so I couldn't verify if the information is still there. I think 3D support for Savage cards went out with the 2.4 kernel; since we're now at 2.6, that would make getting 3D to work on that integrated video card highly improbable. Then there's also the performance issue; the Savage card only has 32 MB of RAM to work with, which is probably not enough to get the desktop effects working.

Sorry for the long post; I could be wrong, and maybe you *can* get direct rendering working with the Savage card. You should do a search of the [Desktop Effects & Customization]("http://ubuntuforums.org/forumdisplay.php?f=223") and the [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=138") sections of these forums to see if there are threads addressing your issue, and post there if you can't find anything.

Just keep in mind that it is very unlikely you would get decent performance out of that card.

Hope this helps.

---

