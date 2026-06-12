---
title: "Acer Aspire One 533 Compatible?"
date: 2010-11-10
forum: Hardware
---

### Post by guimaster on 2010-11-10
Greetings,

 I have been Googling for compatibility info on this particular Netbook: _Acer Aspire One 533_, as I am looking to buy a new Netbook.
[U]
[/U] The good news is that I haven't found any bad news about this laptop regarding Ubuntu compatibility. The bad news is that I haven't found any good news about this laptop regarding Ubuntu compatibility. However, since most hardware tends to have problems with Ubuntu, I am leaning toward this being a very good sign.

 As well, there is apparently a version of Linux called: Jolicloud which runs well on this Netbook, making me think this could work well with Ubuntu.

 Any help appreciated!

---

### Post by darkhelmetchris on 2010-11-11
> **guimaster said:**
> ... However, since most hardware tends to have problems with Ubuntu, I am leaning toward this being a very good sign

Hmm, strange statement.  I would tend to say that most hardware works perfectly with Ubuntu.

For netbooks:  I have an Acer Aspire One ZG5 netbook and an Acer Aspire One D250 netbook, and both of them work very well with Ubuntu.  There are few, if any problems.  I have used 8.10, 9.10, and 10.10 with them.  8.10 needed a little tweaking, but 9 and 10 are terrific.  In fact, I put an OCZ SSD drive in the D250 and it just flies with Ubuntu.  I couldn't be happier with that one, and I use that for my primary work laptop.  Also, I recently set up a Joey netbook with Ubuntu for my Mom.  All the hardware is working fast and smooth - she loves it.  I even have an older Asus eeePC 2G surf which I loaded Ubuntu on, and it's great on there too (even if the on-board SSD is very slow, but that is no fault of Ubuntu).  No problems to speak of.  I would say .. go for it.  My experience has been very positive.

For desktops:  I have a varied range of hardware, and all are working perfectly with Ubuntu.  I use Intel-based and AMD-based systems with Asus, Gigabye, and Intel mainboards.  Ubuntu is currently my primary OS-of-choice and works flawlessly with all that hardware.

---

### Post by guimaster on 2010-11-19
> **darkhelmetchris said:**
> Hmm, strange statement. I would tend to say that most hardware works perfectly with Ubuntu.
 
 Based on my search through the Ubuntu compatibility lists, the vast majority of laptops/netbooks work... almost perfectly. They very nearly always list a problem or three. Excellent in my mind means that Lucid boots without an error message and every button works, etc.. Few, if any problems is not "excellent" in my mind.
 
> For netbooks: I have an Acer Aspire One ZG5 netbook and an Acer Aspire One D250 netbook, and both of them work very well with Ubuntu. There are few, if any problems. I have used 8.10, 9.10, and 10.10 with them. 8.10 needed a little tweaking, but 9 and 10 are terrific. In fact, I put an OCZ SSD drive in the D250 and it just flies with Ubuntu. I couldn't be happier with that one, and I use that for my primary work laptop. Also, I recently set up a Joey netbook with Ubuntu for my Mom. All the hardware is working fast and smooth - she loves it. I even have an older Asus eeePC 2G surf which I loaded Ubuntu on, and it's great on there too (even if the on-board SSD is very slow, but that is no fault of Ubuntu). No problems to speak of. I would say .. go for it. My experience has been very positive.
 
For desktops: I have a varied range of hardware, and all are working perfectly with Ubuntu. I use Intel-based and AMD-based systems with Asus, Gigabye, and Intel mainboards. Ubuntu is currently my primary OS-of-choice and works flawlessly with all that hardware.
 
 Thanks for the reponse. I purchased a D255 from Acer as it was only $299. There is an error on boot about WMID devices but there is a fix online. Funny that version 10.04.1 hasn't fixed that error and neither have the updates I downloaded after install. The compatibility list that I found for Ubuntu listed this netbook as working in everyway except for a card-reader problem that - if I remember correctly - indicated the issue should be fixed in a later Linux Kernel. I haven't tested it yet.

---

### Post by muleyyy on 2010-11-20
i have had a bit of experience loading ubuntu onto various laptops and computers. i had zero problems with my mums old acer laptop, my samsung n150 had a few problems with wifi and function keys, however, there is a repository with tools that fix everything.

the main problem with laptops is wifi cards. especially cheap and nasty ones. intel wireless cards will always work, i have had problems with realtek ones (not all the time though) however realtek have the linux drivers for their products on their website

---

### Post by mutas on 2010-11-30
To answer your original question: Yes, it seems to work fine with Ubuntu 10.10 (netbook).  Suspend, wireless, webcam, sound, and most of the buttons with the exception of the one that disables the wifi radio.  It also doesn't like the card reader works out-of-the-box. From my perspective, however, I call that "not bad."

---

### Post by BFG on 2010-12-07
Sorry this is so late - I have two of these in our household both dual-booting ubuntu and windows 7.

They are 98% compatible. Everything works, even suspend and hibernate. Function keys, webcam, etc etc etc.  The wireless card needed extra hardware drivers on one, and the wired network needed drives on the other. One had atheros, one had broadcom.

Strange that.  And the source was this....

There are a quite a few varied specifications for these laptops under the same model no.  For instance, the Acer site says that the machine has a 3g slot. Mine, bought from argos in the UK did not.   It's very difficult to work this out, so make sure you get the spec you're after from the retailer.

---

### Post by Sandworm on 2011-01-18
I've got a shiny new aspire 533 sitting on my desk right now.  Niether standard 10.04 nor 10.10 support ANY of the network devices, forcing my to troll through forums for a way to build my own drivers.... this is not a good day for me and ubuntu.  

Update: I've given up.  Now trying puppy linux.

---

### Post by minorzero on 2011-01-31
Hey all,

Sorry to bring up an old post.. But im really having problems here and i can figure out the solution :(

I just bought a net netbook, Acer Aspire on3 533 which came with windows 7starter. It working ok i guess, but a friend pointed me towards Ubuntu Netbook Edition.
So i've installed the 10.10 version of Ubuntu Netbook edition and it seems to run pretty fast..

One problem though, i cant seem to get the network (both wireless and wired to work)
I've been doing some research on this forum and Google and found some helpfull stuff but seeing as its my first time working with Ubuntu i cant get it to work.. Can anyone help me?

Info:
> 
According to windows 7 system info i seem to have:

Naam	[00000007] Atheros AR8152 PCI-E Fast Ethernet Controller (NDIS 6.20) (wired?)

Naam	[00000011] Broadcom 802.11n Network Adapter (wireless?)
Servicename	BCM43XX

Am i right in saying that once i get the wired internet connection to work i can just update the drivers needed for wireless through the build in updater?

One the forums i found this:

[http://ubuntuforums.org/showthread.php?t=1505697&highlight=aspire+533&page=12](http://ubuntuforums.org/showthread.php?t=1505697&highlight=aspire+533&page=12)
In post 117 someone had the same problem. He got redirected to post 115 which seemed to fix it for him..

So i tried this:

> -----Wired------:
1. Download official Atheros driver, from their website: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) (file: AR81Family-linux-v1.0.1.9.tar.gz)
2. tar -xvf AR*
3. make
4. sudo make install
5. restart

So i went to the site, downloaded "AR81Family-linux-v1.0.1.14.tar.gz" put it onto a usb key.. Booted Ubunto.. Put the file in my homefolder, went to the terminal and typed 

"tar -xvf AR81Family-linux-v1.0.1.14.tar.gz"
([http://pic80.picturetrail.com/VOL2131/2279143/11334541/394909536.jpg](http://pic80.picturetrail.com/VOL2131/2279143/11334541/394909536.jpg))

Then the terminal does some stuff
([http://pic80.picturetrail.com/VOL2131/2279143/11334541/394909538.jpg](http://pic80.picturetrail.com/VOL2131/2279143/11334541/394909538.jpg))

Then i typed 'make' aand i get some errors
([http://pic80.picturetrail.com/VOL2131/2279143/11334541/394909540.jpg](http://pic80.picturetrail.com/VOL2131/2279143/11334541/394909540.jpg))

. Am i doing it wrong? should i not be doing it this way? is there another solution?

I sure hope someone can help me! sorry if im asking stupid questions but im new to all of this :)

---

### Post by BFG on 2011-02-06
I got your PM - Sorry for late reply, been on holiday.

you must have build-essential installed....

sudo apt-get install build-essential


If you can't get because of  lack of internet, use the respository on the USB install flash.

/etc/apt/sources.list

Add:

deb file:/media/60E4-720E/ lucid main  
deb-src file:/media/60E4-720E/ lucid main  

Of course don't forget to make as root:

```
mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
[COLOR="Blue"]sudo su[/COLOR]
make install
modprobe atl1e
exit
```

---

### Post by BrianG61UK on 2011-07-23
I just set up dual boot Win7 / Ubuntu 11.04 on my AO533-N55Dkk and I found that in my case the best way to get everything recognized and working was to make sure everything was enabled and on at the stage when I booted the Ubuntu CD and did the installation.

So I
1. Connected the internet via the wired connector.
2. Put a card in the card reader.
3. Booted Windows and made sure Bluetooth and WiFi were both on before booting the Ubuntu CD.

As far as I can see everything was correctly recognized and works, except the FN/F3 key combination that should allow enabling/disabling of Bluetooth and WiFi in any combination seems to behave erratically, sometimes resulting in WiFi being disabled until I reboot.

---

