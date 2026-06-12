---
title: "Simple Wireless LAN config procedure"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by wh0rd on 2005-08-02
Okay, I'm very new to the Linux world so I downloaded Ubuntu and installed it last night. After hours of trying to configure the network cards Ethernet and Wireless LAN for my Sony Vaio PCG-Z1WA I decided to reinstall Ubuntu 5.04.

On the second install I manually disabled (turned the switch off for Wireless LAN, most laptops come with this switch to turn off the Wireless LAN.) Then began installing Ubuntu, through out the installation Ubuntu found two cards one was the Ethernet and the other one was the Wireless LAN (keep in mind this was my crucial point in configuring the network cards). In this option I made sure to choose the Ethernet NOT the Wireless LAN as the primary.  I made sure the Ethernet cable was plugged into my laptop then proceeded with the installation. 


Ubuntu finished installing and flawlessly connected to the Internet through the Ethernet. 
What I did next was update Ubuntu for all the updates and new patches.

Then I proceeded to enter the WEP encryption key for my Wireless Router:

1. I went to System > Administration > Networking. It asked me to enter a password
which is the same one I  used to log in.

2.Clicked on the Ethernet connection and the clicked on Deactivate.

3.Clicked on Wireless connection

4.Clicked on Properties.

5.Checked “This device is configured.” 

6.Entered the Network name (ESSID) usually when you configure the Wireless   Router you enter it or the default “linksys” if it's a Linksys router.

7.Type in WEP key (this is because I set that security feature, if I didn't set the key I would've left it blank).

8.In the Configuration option select DHCP.

9.Click OK!

10.Click OK again on the Network settings window.

Now that configured my Wireless LAN. I then tested the Wireless LAN and it worked perfectly.  I still saw the little Network Monitor icon on the top tool bar indicating that the Network is disabled but that's just for the Ethernet. Then I added a Network Monitor icon for the Wireless LAN:

1.Right click on the top tool bar > Add to Panel.

2.Scroll down to Network Monitor, click on Add.

Now I have a small Network Monitor icon just for the Wireless LAN along side the disabled Ethernet Network Monitor icon.

Keep in mind:
In the Network configuration utility the Ethernet is eth0 and Wireless LAN is eth1 when I went through that procedure of installing Ubuntu.

Oh yeah, I had a dual booting with Grub so when I did the second installation of Ubuntu I deleted the swap/ext partitions and let Ubuntu configure the partition with its Auto feature. For the dual Windows/Linux booters: just keep in mind that the NTFS is the Windows partition so don't mess with that.

I was thinking in the beginning it was the hardware problem but it actually wasn't. Without luck I dough through tons of forums trying to figure it. I don't know if this is already on this forum but I thought since it helped me a lot and saved me more frustration I would share this experience. I hope this helps, happy ubuntuing!  \\:D/

---

### Post by jimmyv3 on 2006-05-25
I did the same thing.  i unistalled and reinstalled Kubuntu and selected the eithernet vs. the wireless connection.  Kubuntu recognized the wireless as the primary.  

I still can not connect wirelessly to to make matters worse, when i re booted and logged in the nex day i did not have administrative rights.  I click admin rights and entered the same password as i used to log in to Kubuntu but nothinging is highlighted and i have no access.  

I dont get it.  Help.My wireless card is an Intel pro series 2100.  I went to Intel and noticed they had a driver for Linux but the procedure for installing it seemed real complex.

---

### Post by rossakared on 2006-05-26
I tried doing the same thing and it did not work for me either.  I installed ubuntu without a internet connection hooked up but did select ethernet as the default connection.  I entered in all the information for the wireless connection and did all the steps above and still got no connection.  Is there something else that has to be done in order to connect.  I am new to linux and do not know that much.  Any help would be great.

---

