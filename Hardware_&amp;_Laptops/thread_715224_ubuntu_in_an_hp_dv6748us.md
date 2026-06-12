---
title: "ubuntu in an hp dv6748us"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Llewxam on 2008-03-04
greetings to all.

i have just purchased an hp laptop (model noted on title) and i was wondering if i can easily install ubuntu on this? obviously don't wanna have to use vista :-& so i'm planning on formatting the hard drive sometime soon. if anyone knows how well can ubuntu work on it before i do something dumb (compatibilities and all) please share whichever information you can. thanks in advanced.

---

### Post by jeffus_il on 2008-03-04
You can test what your install will be like by downloading and burning the Ubuntu livecd. Boot from the livecd and use Ubuntu, remember it will be slower than Ubuntu installed on the hard disk, but you will be able to find out if all your hardware is compatible. Connect to the network, browse and when you feel that you want to install it, click on the install button.

---

### Post by Llewxam on 2008-03-04
:( feeling dumb now. completely forgot about that. :lolflag: thanks.

---

### Post by Llewxam on 2008-03-05
well running the live cd last night showed that ubuntu ran fine. found a website in italian (translated to english) that stated that all hardware in this new computer works with 7.10. now my question is: i tried to run dban to format the hard drive and install ubuntu from my usb but that failed, is there a way to do this with the installation straight off the cd?

---

### Post by jeffus_il on 2008-03-05
Yes, run ```
sudo gparted
``` from a terminal, I think it may be Partition Manager in the system menu.

---

### Post by Llewxam on 2008-03-05
done and done. just need to configure the integrated wireless and the nvidia graphics card. resolution won't go higher than 800 x 600. now i know the drivers are in synaptic so i'll work around with those, it's in fact the wireless that worries me more. it's a broadcom modem, bcm4328.

---

### Post by jeffus_il on 2008-03-05
> **Llewxam said:**
> done and done. just need to configure the integrated wireless and the nvidia graphics card. resolution won't go higher than 800 x 600. now i know the drivers are in synaptic so i'll work around with those, it's in fact the wireless that worries me more. it's a broadcom modem, bcm4328.

Here is the howto:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by Llewxam on 2008-03-05
following the instructions in there i can't find the device in the restricted drivers manager. i'll keep tweaking around sure i'll get it. 

also for the nvidia card, i still can't go over 800x600 res.

---

### Post by Llewxam on 2008-03-06
](*,) graphics fixed. wireless not. i found and read so many how to's and tried everything and nothing. 

if anyone can help me with this please 'fore i go crazy :(

---

### Post by jeffus_il on 2008-03-06
What is the status now?
Do you have the driver installed?
Is the module being loaded with modprobe. Check with ```
lsmod | grep bcm43
```Do you have a wireless device? check with ```
iwconfig
```Is there any relevant output to ```
dmesg
```?

Don't go crazy yet, there are much better opportunities in life to go crazy than an incident with a stupid wireless card.

---

### Post by Llewxam on 2008-03-06
amen to that. 
alright, ran iwconfig i get this:

```
lo        no wireless extensions.

eth6      no wireless extensions.
```

lsmod did not show anything up. now, i followed a thread in which (the link i don't have right at this very moment) that explained how to use ndiswrapper with the winxp drivers. i got the driver but it's in an .exe file. 
now i was gonna try running that .exe in a windows box and see if i can extract the .inf file from there. but that will have to wait 'cause i got a few appointments to take care of.

---

### Post by Limbic on 2008-03-06
I had a freaking nightmare problem with the wireless for my DV2715nr, but I finally got it fixed. The most important bit, I think, is making sure you're using the correct driver for your card.  If it's a Broadcom BCM4310 (rev 1) and it appears there are at least two variations of this card, so it could use one of several different drivers.  

My problem originally looked like an issue with NDISWrapper but that wasn't it. I tried all the different ways of installing it, but now that I have the right driver it works immediately with the NDISWrapper version from the Repositories.n a fresh install if I'm tinkering around with different distros or what-not.

Here's what made it work for me, but bear in mind I'm very much a Linux noob. Here's [the guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and [the drive]("http://ubuntuforums.org/showthread.php?p=4379996")r I used to get mine working.

The most important part for me was getting the right driver, as I said, so here's the step from the above guide that made all the difference:

> 
3.2.1. PCI Wireless Adapter

1. Open a Terminal (Applications | Accessories | Terminal), type
```
lspci
```
and press the return/enter key.
2. Look through the output of the lspci command for an entry for your wireless card.
3. Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0.
4. Now, type
```
lspci -n
```
into the Terminal and press return.
5. Find the PCI ID for your device. Your device will be referred to in the output of the command by the identifier which you just made a note of, e.g. 0000:00:0c.0. The PCI (chipset) ID will be in the third column of the output and will be in the form 104c:8400.
The PCI ID that came up for my dv2715 was 14e4:4315 which keys to the driver I linked above. If you search around on the web, you'll find some of the same wireless card that use 14e4:4312 as a PCI ID, but the drivers aren't the same. That four digit code behind the colon is the important bit; the "lspci" command tells you the card is a Broadcom BCM4310 (rev 1) the driver and NDISWrapper instead sees it as a Broadcom 4315. Likewise with the BCM4310 (rev 1) that the drivers and NDISWrapper see as a Broadcom 4312.

Once I had the correct driver I was able to install it with the GUI from the System -> Administrative ->"Windows Wireless Drivers" and can have it up and running a few minutes after an OS install.

---

### Post by Llewxam on 2008-03-06
i feel REALLY dumb now. since i had downloaded that .exe file before and had no idea how to extract it, i suddenly read all that you posted (big thanks to all by the way) and transferred it to my desktop. lo and behold, i extracted the files there and from that i took the .inf file i needed. it works now. so that's two down one more to go and that would be the integrated webcam. getting to work on that now. 

thanks again for all the help. would you happen to know how to work with the integrated webcam? how to get it working? ...by any chance? :)

---

### Post by Limbic on 2008-03-06
My webcam was actually detected and the drivers were installed just fine.  The problem was actually that specific programs couldn't see it.  You can check to make sure it's installed with this command from the command line:
```
lsusb
```

You should see the camera in the list out of the box.  If it shows up, go into the Repository and grab a program called "Cheese"; that should work just fine without any tweaking or extra steps necessary.

---

### Post by Llewxam on 2008-03-06
yep. it works. tried it out with camorama at first and it didn't want to recognize the device. but once i went into amsn it worked. 

everything works now, but the last single problem i got is flash on opera. i can't stream vids off youtube ... that is the last thing i gotta fix to then work with the rest of the stuff i already know.

---

### Post by Limbic on 2008-03-06
Here you go, then.  [This]("http://ubuntuforums.org/showthread.php?t=661833") should do it for you.   :)

---

### Post by Llewxam on 2008-03-06
that's mostly from firefox. just skimming over it. i need it for opera :(

---

### Post by tp69 on 2008-04-02
> **Llewxam said:**
> ](*,) graphics fixed. wireless not. i found and read so many how to's and tried everything and nothing. 

if anyone can help me with this please 'fore i go crazy :(

How did you get the 1280 x 800 mode to operate.  I can only get the 1024 by 760 using the restricted driver.

---

### Post by tp69 on 2008-04-02
I'm also a noob to Ubuntu.  I got my wireless driver working under fedora 8 but I can't seem to get it to work for ubuntu.  What were your steps?

Tim

---

### Post by Llewxam on 2008-04-02
> **tp69 said:**
> I'm also a noob to Ubuntu.  I got my wireless driver working under fedora 8 but I can't seem to get it to work for ubuntu.  What were your steps?

Tim

i reconfigured x with dpkg reconfigure command in terminal. the precise command i can't recall at the moment. but i'll search around for it and let you know. 
as for the wireless, ndiswrapper and searching for the chipset drivers. it was an .exe, i "installed" that on a windows box 'cause i didn't have wine at the time and from there i took the .inf file and copied it over to ubuntu. with the ndiswrapper gui applications i installed the inf file and that fixed the issue. 

the process i recommend you search for ndiswrapper in the forums or in wiki. it should give you a much detailed process. for the resolution issue, i'd suggest the same but i'll try and do it with the crawling speed of my univs connection.

edit: the command for fixing resolution is: ```
sudo dpkg-reconfigure xserver-xorg
```
run it in terminal.

---

### Post by tp69 on 2008-04-02
Does anyone else have any suggestion on how to get my wireless working.

Tim

---

### Post by tp69 on 2008-04-02
I really don't know what I did to get my resolution but I follow your commands and had to do an update on the prop. driver.  I still don't have wireless connectivity.  I tried using the gui program from darknoob but so far no luck.

---

### Post by Llewxam on 2008-04-02
ndiswrapper can be installed in both synaptic and via terminal. synaptic is in System -> Administration -> Synaptic Package Manager

via terminal ```
 sudo apt-get install ndiswrapper
```

---

### Post by tp69 on 2008-04-07
I got the wireless card working now.  I used the gui for ndiswrapper on 8.04.  My only now is that I can not connect to a secure network.  I'm having issues with wpa.  So I am now working this issue.

---

### Post by Llewxam on 2008-04-24
anyone know how well hardy works with this model? debating on upgrading.

still got that internal mic issue and the media card reader that won't mount psp memory cards. pro duo to be more precise.

---

