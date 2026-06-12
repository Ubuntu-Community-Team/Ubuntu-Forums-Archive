---
title: "How To: Installing Belkin Wireless USB Adapter F5D7050 on Dapper Drake"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by ontologicalbach on 2006-09-20
I just spent today trying to get my Belkin wireless USB adapter F5D7050 working, and finally... success. I'm not sure if these forums are supposed to be used for how to sort of things, but hopefully this will get crawled by google soon enough and might be of use to somebody. For this install, I was running Dapper Drake (Ubuntu 6.06 LTS) on a Dell Inspiron 1100. Anyway, here goes.

I lost my box and driver cd a long time ago, so I opened up my adapter to figure out which version I have. There are apparently four version of the F5D7050 USB adapter out now, which I surmised from Belkin's latest available drivers (v.4). In little white print on the chip inside it said V02, so I assumed the ver2 drivers would work. I actually ended up having to use the Version 3 drivers, downloaded from the Belkin website here:

[http://www.belkin.com/support/download.asp?lang=1&download=F5D7050_v3&mode=](http://www.belkin.com/support/download.asp?lang=1&download=F5D7050_v3&mode=)

I have no idea why the version 2 drivers didn't work for me, but I can attest to the version 3 drivers working with the chip that says version 2 on it...

I used the WindowsXP download link on the website. I just put it on my desktop, and then opened a terminal to extract the compressed folder (the file is a .exe, but is just a self-extracting zip file).

In the terminal, use unzip to extract the folder:

unzip /home/noah/desktop/F5D7050_v3.exe

There will be a folder named F5D7050_v3 in the same folder that you extracted the .exe file in (mine was on my desktop, obviously).

Next you need to install ndiswrapper. I did this through Synaptic Package Manager, and it worked fine. All you have to do is type the following into a terminal:

sudo synaptic

It will ask you for an admin password, and then the application will open. Search for "ndiswrapper" and a program titled ndiswrapper-utils should appear. My version was 1.8. Check the box and commit to install.

Now go back to a terminal and run the following commands:

1. sudo ndiswrapper -i /home/noah/desktop/F5D7050_v3/drivers/1.0.0.0/Win2KXP/rt73.inf (replace this with your own path, obviously)

2. sudo ndiswrapper -m

3. sudo modprobe ndiswrapper

I'm not actually sure what these last two commands do, seeing as I am very new to this whole thing. But I used them, and things worked out fine.

After those commands, I think I had to shut down and power up again (that always seems to work better than just restarting... weird). After you reboot, go to System->Administration->Networking and a wlan0 connection should be there. You can edit the properties (DHCP, static IP, DNS, etc) of the connection there. The Networking window freezes on me when I click OK to exit, but I just clicked the X and it closed fine and my new preferences were still intact. 

If I remembered everything correctly, those are the steps to a life of crappy wireless access through the good old Belkin USB. I'll try to answer questions if anyone has any, but seeing as I didn't really understand what I did, I may not be of much help.

---

### Post by bodycoach2 on 2006-09-20
The Belkin 54G Wireless USB Network adapter worked 'out of the box' for me. I've set up 12 machines so far, half of them Xubuntu, and the Belkin USB adapter works on all of them. Sometimes Network Manager freezes, but if you go through the steps one at a time, it should work perfect. 

So far, it's the only one that's worked that easily for me.

> **ontologicalbach said:**
> I just spent today trying to get my Belkin wireless USB adapter F5D7050 working, and finally... success. I'm not sure if these forums are supposed to be used for how to sort of things, but hopefully this will get crawled by google soon enough and might be of use to somebody. For this install, I was running Dapper Drake (Ubuntu 6.06 LTS) on a Dell Inspiron 1100. Anyway, here goes.

I lost my box and driver cd a long time ago, so I opened up my adapter to figure out which version I have. There are apparently four version of the F5D7050 USB adapter out now, which I surmised from Belkin's latest available drivers (v.4). In little white print on the chip inside it said V02, so I assumed the ver2 drivers would work. I actually ended up having to use the Version 3 drivers, downloaded from the Belkin website here:

[http://www.belkin.com/support/download.asp?lang=1&download=F5D7050_v3&mode=](http://www.belkin.com/support/download.asp?lang=1&download=F5D7050_v3&mode=)

I have no idea why the version 2 drivers didn't work for me, but I can attest to the version 3 drivers working with the chip that says version 2 on it...

I used the WindowsXP download link on the website. I just put it on my desktop, and then opened a terminal to extract the compressed folder (the file is a .exe, but is just a self-extracting zip file).

In the terminal, use unzip to extract the folder:

unzip /home/noah/desktop/F5D7050_v3.exe

There will be a folder named F5D7050_v3 in the same folder that you extracted the .exe file in (mine was on my desktop, obviously).

Next you need to install ndiswrapper. I did this through Synaptic Package Manager, and it worked fine. All you have to do is type the following into a terminal:

sudo synaptic

It will ask you for an admin password, and then the application will open. Search for "ndiswrapper" and a program titled ndiswrapper-utils should appear. My version was 1.8. Check the box and commit to install.

Now go back to a terminal and run the following commands:

1. sudo ndiswrapper -i /home/noah/desktop/F5D7050_v3/drivers/1.0.0.0/Win2KXP/rt73.inf (replace this with your own path, obviously)

2. sudo ndiswrapper -m

3. sudo modprobe ndiswrapper

I'm not actually sure what these last two commands do, seeing as I am very new to this whole thing. But I used them, and things worked out fine.

After those commands, I think I had to shut down and power up again (that always seems to work better than just restarting... weird). After you reboot, go to System->Administration->Networking and a wlan0 connection should be there. You can edit the properties (DHCP, static IP, DNS, etc) of the connection there. The Networking window freezes on me when I click OK to exit, but I just clicked the X and it closed fine and my new preferences were still intact. 

If I remembered everything correctly, those are the steps to a life of crappy wireless access through the good old Belkin USB. I'll try to answer questions if anyone has any, but seeing as I didn't really understand what I did, I may not be of much help.

---

### Post by surplusxmas on 2006-09-22
Bravo!  Well done!  Thank you very much, ontologicalbach, for this excellent How To.  Yes, it has been indexed by Google (already) and is the first result for:
```
Ubuntu +F5D7050
```
Notice how I didn't even have to throw "+Belkin" in. ;) 

Only one question: Why is this on Laptop Support?  Could it be that the Belkin F5D7050 was designed for a laptop?  I don't think so, though, because it was recommended to me by Circuit City (I know, I know...) for my desktop PC, and I've only used it on desktops since...I wouldn't think that something so bulky and that sticks out so far would be meant for a laptop.  But that's only a theory.

**[EDIT]** I spoke too soon.  It does not show up in the networking list at all.  I guess I'll have to search the web and post what I find here.
**[EDIT2]** I tried doing what tible said in the following post.  If I don't say otherwise in a future edit, it worked.
[http://ubuntuforums.org/showpost.php?p=1189280&postcount=6](http://ubuntuforums.org/showpost.php?p=1189280&postcount=6)
**[EDIT3]** What I said in EDIT2 didn't work.  I'm starting to beleive that I'm screwed.
**[EDIT4]** I've been having all these problems because I'm running Breezy (5.10).  I didn't expect it to matter much, but I'm going to upgrade to Dapper and see if that works.

---

### Post by ontologicalbach on 2006-09-23
Yes, surplusxmas, you are correct. I don't think I was thinking straight. It sould be in the How To section or the wireless networking section. I was thinking about reposting it, but on a lot of forums the admins get really mad if you double up a post.

---

### Post by surplusxmas on 2006-09-25
You should request that it be moved.  Send a private message to a moderator.

---

### Post by siiib on 2006-09-27
FWIK the reason there is so much confusion is that some models use a ralink chipset and some don't.. there are linux drivers available for these versions but not the others.. note that some versions of this dongle will work with macintosh osX as well..
 mine was the wrong version.. <sigh>](*,)

---

### Post by SamFeltus on 2006-10-04
My experience was slightly different, works well now

Ubuntu 6.06.1 Desktop 
Old AMD 1800 with ECS Mobo
Belkin F5D7050B USB Wireless card ( from Fry's )
Drivers were different on CD
rt73.inf

Open Terminal - Card is plugged in
1. Copy drivers in home_dir and cd home_dir
2. sudo ndiswrapper -i rt73.inf
3. sudo modprobe ndiswrapper
4. ndiswrapper -l

Printed
Installed ndis drivers:
rt73            driver present, hardware present

5. Went to network settings and it was working

SamFeltus.com

---

### Post by SamFeltus on 2006-10-05
When I rebooted, the Internet was down.

Doing this restored it...

sudo modprobe ndiswrapper

---

### Post by mr_cazorp on 2007-02-21
My experience was slightly different. Installed v3 of the drivers with ndiswrapper - 

ndiswrapper -l 
driver installed, device present. 

But wlan0 no showy up in network config. 

so I installed my kernel headers and build and all that malarky and compiled the Linux native driver, and still nothing. 

so I installed v1 of the driver from the CD ROM and got "invalid driver!"

so I uninstalled ndiswrapper and built the latest version and then reinstalled the driver from the CD ROM 
blkwgu : driver installed
        device (050D:705C) present

But wlan0 still no showy up in network config.  #-o 

So now I'm gonna reboot and see what happens. 

LINUX!!!  ](*,)

---

