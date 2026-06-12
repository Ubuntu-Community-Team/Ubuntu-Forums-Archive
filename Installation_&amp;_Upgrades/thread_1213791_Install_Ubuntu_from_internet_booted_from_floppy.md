---
title: "Install Ubuntu from internet booted from floppy?"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Chaos Punk on 2009-07-15
After hours of fooling with my laptop which has no cd drive and can't boot from usb, I finally found a way to install Debian on it. I made these four boot floppys that started the process and then it downloaded everything else from the web. The first floppy was a "boot" image, then next was a "root" image, and the next two were network drivers. I then just plugged in the ethernet port which was already connected to my router and it installed Debian. I was very excited that I finally got a working OS on my laptop (it had Windows XP, but it got a virus preventing me from booting.) But what I really want is Ubuntu, is there any way to do an internet install like this where I download all neccessary components directly from hosts? And I don't mean TFTP or DHCP booting and installing from host PC's, I couldn't get that to work no matter what.

---

### Post by Chaos Punk on 2009-07-15
Bump, I hope I didn't bump to early, from what I understand you can bump once a day right?

---

### Post by Chaos Punk on 2009-07-15
I actually just thoaught of another possiblility that might work, I just found out about the "Mini-ISO". Is there a way to maybe fit this onto multiple floppies? I don't care if it takes 10 or 20 floppies to do so, but is this a possibility?

---

### Post by LepeKaname on 2009-07-15
I tried also once to install Ubuntu from a floppy disk but the drive failed so it was impossible. 

If ( you have windows in that computer ) {[INDENT]try WUBI {

[http://wubi-installer.org/](http://wubi-installer.org/)

Its an official Ubuntu windows-installer and you will not need a CD or USB to dual boot. Once in Linux, you can get rid of your windows (if you want).

}[/INDENT]

} else {

[INDENT]There is a way to boot over the network. Many computers (even olders) are capable of that... but I tried once and I couldn't. 

This link could help you:
[http://nixcraft.com/getting-started-tutorials/474-ubuntu-linux-network-installation-using-boot-server.html](http://nixcraft.com/getting-started-tutorials/474-ubuntu-linux-network-installation-using-boot-server.html)[/INDENT]

}

---

### Post by Chaos Punk on 2009-07-15
It deosn't have windows, it had gotten a virus and is the very reason I'm installing a new OS, it was unbootable. I managed to get Debian on it and managed to make it boot the minimal cd from the harddrive, but now it's having trouble configuring the network which is weird because Debian did it just fine. Do I need to load some kind of network drivers? It doesn't seem to detect my network hardware at all.

---

### Post by lindsay7 on 2009-07-15
You could take out the hard drive and install an os using another computer. You can buy the cabling on ebay for less the $10. It allows for the conncetion of 2.5 inch or 3.5 inch drives that are either IDE or SATA and you connect to the computer with an USB cable.  

You could install the OS as a full OS or a usb drive and then put it back into your laptop.

---

### Post by sailthesea on 2009-07-15
I was trying something similar a little while back I wanted to get a live session running from a floppy but it wasn't the fix I needed However some of the tiny linux distros I looked at may help you Check this thread 

[http://ubuntuforums.org/showthread.php?t=1203869](http://ubuntuforums.org/showthread.php?t=1203869)

 One of these could get you enough connection to install a full version
 Hope you find what you need :p

---

### Post by Chaos Punk on 2009-07-15
> **lindsay7 said:**
> You could take out the hard drive and install an os using another computer. You can buy the cabling on ebay for less the $10. It allows for the conncetion of 2.5 inch or 3.5 inch drives that are either IDE or SATA and you connect to the computer with an USB cable.  

You could install the OS as a full OS or a usb drive and then put it back into your laptop.
Yea, I COULD do that, but I would like to have that be a last resort, which it might come down to. As for the tiny distros, I'd rather just stick with Debian than resort to those.

---

### Post by Chaos Punk on 2009-07-17
> **lindsay7 said:**
> You could take out the hard drive and install an os using another computer. You can buy the cabling on ebay for less the $10. It allows for the conncetion of 2.5 inch or 3.5 inch drives that are either IDE or SATA and you connect to the computer with an USB cable.  

You could install the OS as a full OS or a usb drive and then put it back into your laptop.
I've come to the conclusion that this is my only option. So I went down to my local computer shop, The Computer Depot, and wow, that place is a joke. I knew more about his job than the guy at the counter. The moment the phrase, "Operating System" came out of my mouth I knew I lost him. So needless to say he had no idea what a 2.5 inch to 3.5 inch hard drive adapter was.

---

### Post by lindsay7 on 2009-07-17
[http://computers.shop.ebay.com/?_from=R40&_npmv=3&_trksid=p3910.m38.l1311&_nkw=usb+sata+adapter&_sacat=58058](http://computers.shop.ebay.com/?_from=R40&_npmv=3&_trksid=p3910.m38.l1311&_nkw=usb+sata+adapter&_sacat=58058)



[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&CatId=3770](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&CatId=3770)


I bought one on ebay a while back for about $5
 

These two sites should get you started.

---

### Post by lindsay7 on 2009-07-17
Here is a picture,

[ATTACH]121448[/ATTACH]

---

### Post by Chaos Punk on 2009-07-18
> **lindsay7 said:**
> [http://computers.shop.ebay.com/?_from=R40&_npmv=3&_trksid=p3910.m38.l1311&_nkw=usb+sata+adapter&_sacat=58058](http://computers.shop.ebay.com/?_from=R40&_npmv=3&_trksid=p3910.m38.l1311&_nkw=usb+sata+adapter&_sacat=58058)



[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&CatId=3770](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&CatId=3770)


I bought one on ebay a while back for about $5
 

These two sites should get you started.
Thank you.

---

### Post by Chaos Punk on 2009-07-18
Actually, I'm not sure it's a 2.5 hard drive. I don't know what kind it is. I'll post a pic when my mom wakes up (need her iPhone.)

---

### Post by lindsay7 on 2009-07-18
As far as I know. All laptops except for the solid state new drives used 2.5 drives the older ones used IDE or Pata (they are basically the same), new newer ones use Sata.  The difference is that IDE and PATA drives have a multi-pin connection on the back.  Sata drives just use one small cable.

These adapter kits have the pin connections for both 2.5 and 3.5 inch drives and will connect either a IDE or a Sata dirve.

When you connect a IDE drive be careful to get the pin connection aligned the correct way and not backward. There are reference pegs to align the pins but it is possible to force in the drive backward or upside down if you push it in real hard.  It should go in without force.

In the picture of the adapter you will see a flat black thing connected to the usb cable, that is what you connect to the 2.5 or 3.5 drive or cd drive. It also has a Sata cable connection on one side.

---

### Post by Chaos Punk on 2009-07-18
> **lindsay7 said:**
> As far as I know. All laptops except for the solid state new drives used 2.5 drives the older ones used IDE or Pata (they are basically the same), new newer ones use Sata.  The difference is that IDE and PATA drives have a multi-pin connection on the back.  Sata drives just use one small cable.

These adapter kits have the pin connections for both 2.5 and 3.5 inch drives and will connect either a IDE or a Sata dirve.

When you connect a IDE drive be careful to get the pin connection aligned the correct way and not backward. There are reference pegs to align the pins but it is possible to force in the drive backward or upside down if you push it in real hard.  It should go in without force.

In the picture of the adapter you will see a flat black thing connected to the usb cable, that is what you connect to the 2.5 or 3.5 drive or cd drive. It also has a Sata cable connection on one side.
Well I know what IDE is, and I think I know what sata is, but this doesn't look like those to me, here
[IMG]http://i31.tinypic.com/ndsri8.jpg[/IMG]

---

### Post by lindsay7 on 2009-07-18
I have no idea what that is.  What are the specs on your computer??

---

### Post by Chaos Punk on 2009-07-18
> **lindsay7 said:**
> I have no idea what that is.  What are the specs on your computer??
What kind of specs? Like the Hardware? Well it's a CF-28 Panasonic Toughbook, those really rugged laptops. Sorry the pic kinda sucks, iPhone camera.

---

### Post by lindsay7 on 2009-07-18
I looked around the internet and it looks like this is a solid state drive, so, I have no idea on how you would work on one of these.

---

### Post by Chaos Punk on 2009-07-19
> **lindsay7 said:**
> I looked around the internet and it looks like this is a solid state drive, so, I have no idea on how you would work on one of these.
It's an SSD? Really? Hm... I have an external 320 gig hard drive. It connects via USB. I know inside the case of that is an SSD, if I took it out the case, you think I could hook my laptop hard drive to that?

---

### Post by Chaos Punk on 2009-07-19
Ok, I found this thread from another site, [http://toughbooktalk.com/public_downloads/HDD%20%26%20CDD%20swap/CF28%20-%20Change%20Your%20Hard%20Drive.htm]("http://toughbooktalk.com/public_downloads/HDD%20%26%20CDD%20swap/CF28%20-%20Change%20Your%20Hard%20Drive.htm")

It shows how to take my ACTUAL hard drive out. That silver thing is just the case for my laptop model. So, in the thread is my hard drive bare, I just removed it myself, is that the connection that the adapter connects to? I actually think this will connect directly to my desk top. I'm going to log off for a few minutes and see if I'm right. Thanks for your help lindsay, I REALLY appreciate it, most helpful member on these forums so far!

---

### Post by lindsay7 on 2009-07-19
It looks like the connections to this drive are like a 2.5 inch ide hard dirve. If it is then I would think that you could connect it to the adapter kit and make your changes.  You miay also be able to install a new 2.5. IDE drive in that enclouser and go from there too.

---

### Post by lindsay7 on 2009-07-19
I just thought of one other option for you if you do not want to get the adapter kit.  You can buy drive enclousers for 2.5 Ide drives to convert them to portable drives.  These connect to your computer with a usb cable.  If you have a 2.5 inch portable drive you might be able to take out that hard drive and temporarilly install the drive for your laptop and do your programing. Or you could buy an enclourser and put your laptop drive into it an go from there.  At a later point you could buy and extra 2.5 drive and make yourself a portable drive with that enclouser and the nes drive. or put the new drive in your laptop and put the old drive in the enclouser.

---

### Post by Chaos Punk on 2009-07-19
> **lindsay7 said:**
> It looks like the connections to this drive are like a 2.5 inch ide hard dirve. If it is then I would think that you could connect it to the adapter kit and make your changes.  You miay also be able to install a new 2.5. IDE drive in that enclouser and go from there too.
Yea, I'll definately consider gettinga bigger Hard drive, the one I have is only 30 gigs and my desktop is only 20. Thanks again for the help, I'll get one of those adapters and cross my fingers!

---

### Post by Chaos Punk on 2009-07-19
> **lindsay7 said:**
> I just thought of one other option for you if you do not want to get the adapter kit.  You can buy drive enclousers for 2.5 Ide drives to convert them to portable drives.  These connect to your computer with a usb cable.  If you have a 2.5 inch portable drive you might be able to take out that hard drive and temporarilly install the drive for your laptop and do your programing. Or you could buy an enclourser and put your laptop drive into it an go from there.  At a later point you could buy and extra 2.5 drive and make yourself a portable drive with that enclouser and the nes drive. or put the new drive in your laptop and put the old drive in the enclouser.
Wow, your just a wealth of great ideas! Basically upgrade my laptop one and recycle the old one to a portable drive. Thanks for the idea!

---

