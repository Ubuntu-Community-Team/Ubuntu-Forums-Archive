---
title: "Asus Network Switch Not Working. Please Help."
date: 2013-03-10
forum: Hardware
---

### Post by Smallwheels on 2013-03-10
I searched the forum for the Asus switch and the model number GX-D1051 and got no results. Thus I'm asking for assistance. 

I bought this 10/100/1000 switch so I could connect my HP/Ubuntu 10.04 LTS computer and my Mac Book to my cable modem. It only has one ethernet port. 

The Mac Book connected just fine. 

The HP/Ubuntu computer isn't so lucky. It does connect but the time it takes for web sites to open is so long that some sites time out. The HP pops up the box saying that Etho Port 01 has been found. I have tried using other ports on the five port switch and the results are the same.

How do I fix this so that both computers can zoom through this switch and give me internet on both machines? The connection without the switch is a 15 Mbps download and 1.5 Mbps upload at optimum speed. With the switch in line the HP is slower than dial up in action. It is so slow that the speedtest.net site times out before the page loads. 

Thank you for your help.

Smallwheels

---

### Post by Smallwheels on 2013-03-10
I have additional information. Since attaching the switch I've learned that it somehow changed something within the computer. How do I know this? I disconnected the switch and connected the computer directly to the cable modem. Connecting directly also has an extremely slow speed now.

I did restart the computer a few times and select previous updates. That had no effect.

I did try using the Midori browser too. No difference.

The network switch didn't come with any more instructions than a few sentences describing the ports. There were three diagrams labeling the ports. That is all that came with this unit. 

In addition to connecting the switch and making it work I now need instructions on how to make the computer connect to the internet faster. It is times like this that the Apple computers and maybe the other OS from Redmond, make me feel that Linux is beyond my abilities, even when it is the easiest it has ever been.

---

### Post by RoosterHam on 2013-03-10
So have you plugged the modem into the Asus switches VIP port? (I don't think this will really make a huge difference, but worth a shot checking)

Do you know the IP address of your Modem? Do you know if there's any kind of QoS or bandwidth quota enabled on the modem? Some modems support different modes of opperation such as bridging or router/gateway mode. This depends on your internet connection. What type of connection do you have to the internet?

If you know the IP address of your modem, connect your Ubuntu computer to the switch, and click on your connection icon in the systray. Go to the information menu item and check that the IPv4 section lists your modem's IP address as the Default Route/Gateway.

Are you familiar with the terminal, or willing to use it?

---

### Post by Smallwheels on 2013-03-10
After your suggestion I did connect the Ubuntu computer into the VIP port and move the modem ethernet cable to a different position. There is no noticeable difference. The Mac Book seems to connect just fine with the modem cable attached in the different position. 

The Speedtest.net site lists the IP address. If it is the same thing as the modem's IP address then I do know it. 
I don't know of any bandwidth quota on my modem. I don't have restricted internet access in my home. I just get unlimited connectivity at the speeds for which I pay (most of the time). 

I don't know anything about bridging or router/gateway mode. I can't answer that question.

If I go to System and select Network Tools a window opens. It has many tabs. The first one is Devices. There are two lines. One is IPv6 and the second one is IPv4. the IP Address column and Netmask/Prefix column have what look like IP addresses but neither is the one listed on the Speedtest.net page. I don't see the term default anywhere on this page.

There is a drop down menu called Network Device: There are two choices. One says Ethernet Interface (ethO) and the other selection is Loopback Interface (lo). They both affect the columns below it. Still neither of the sets of numbers are the one I see when I connect to Speedtest.net.

I have done some copying and pasting into the Terminal interface before. I was given exact instructions and followed them. Everything worked out when I did that. So whoever was helping me really knew what he was doing. 

I wish I could take screen shots and send them. All of this typing is being done from my Mac Book.

---

### Post by RoosterHam on 2013-03-10
Cool. Now the the IP address the website show you is your public address. that's the global address that your modem gets for your ISP. generally in most situations all your devices have a private network address that are only visible inside your network, and the modem will translate everything your devices want to 'do' on the internet as coming from the modems public address.

lo is what is called a loopback interface. All you'll need to know for now is that it's a special device that you should leave lone and ignore for now.

Plug your modem into your switches VIP port, and your other systems into, say 2 and 3. Then see if you can connect yet.

Since I doubt it would have miraculously resolved, next try entering the following commands at the terminal and post the output.

:~$ ifconfig -a
:~$ ping -c 5 8.8.8.8
:~$ traceroute 8.8.4.4

Something I think I should mention is. if you see the public address that the speedtest website show's as yours, don't post it on here, or anywhere, or tell anyone. change it to something like ######## or <my.pub.add>

---

### Post by Smallwheels on 2013-03-10
I have no idea what happened but everything is working now. This happened after I opened an internet file on my desktop. It opened in the Chrome browser. I closed it and then opened another file stored on the desktop and selected Open with Firefox. It opened quickly which didn't surprise me because it was stored on the computer. I then clicked on an icon in the toolbar in the new Firefox browser window and a new site opened. It opened quickly. Then I started clicking on other icons on my toolbar and they opened quickly. I went to Youtube and videos played normally. 

What do you think happened? Were there specific web connection setting stored in those files that were on my desktop? Did opening those files change something relating to the ability to connect to the internet? I didn't click anything else on the computer or change any settings. 

My Dropbox folder quickly updated and notified me after these browsers started working again. Anybody have any clues about what changed and how to fix this problem should it occur again?
I really want to know.

---

### Post by RoosterHam on 2013-03-10
I doubt that it has corrected by opening saved links or files... more likely to me is that if you have been plugging and unplugging and plugging-back-in to different ports of the switch, it seems to me that network manager was not getting dhcp (your private addresses and other network defaults that your modem/router provides automatically) leases/information correctly. You modem may not have been giving this information out properly (your mac may have just gone to prefered/last-used lease) or your Ubuntu system may have been acting up.

Restarting networking (killing the processes, or unplugging the cable) or rebooting the system often gets these automatic things going properly.

Great news though. :-)

---

### Post by Smallwheels on 2013-03-10
I did switch the cables from the Ubuntu computer to the VIP port and got no change. It sat there for a while. During that time I typed my other posts. I did open the Network Tools window and look at the things that were listed but I didn't make any changes to them. I have not restarted anything since the earlier post where I mentioned that I tried restarting a few times. 

Will it be safe for me to put the cables back into the previous position (VIP to modem cable, HP and Mac cables to other ports)? 

Now that I have two computers connected to this one modem, with the HP connected to the VIP port instead of the cable modem, is there a way for my Mac to read the files on the Ubuntu machine and vice versa? 

In the Mac there is a menu item called Go. When I look at it there is the choice of Network. I opened it and there was nothing there. I also don't see any new icons on the Mac's desktop.

In Ubuntu > Places there is also a Network selection. I opened it and it said Windows Network. It failed to open anything (the HP is dual booted with Windows).

Thank you for your help RoosterHam. I really appreciate it.

---

### Post by RoosterHam on 2013-03-10
You should be right to plug the modem to the vip port. If you get troubles again, try a reboot.

There are a few options to share files between Linux and Mac. The two are much more similar under the skin than either are to Windows. If you know any windows users that you might wish to share files with, you can use Samba to share between your Mac and Your Linux system. You could share between your Mac and your Windows with Samba. There are also things such as NFS and SSHFS that could be suitable, but they could require a fair bit of learning.

Here are some useful links:
NFS- [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
Samba- [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
SSHFS- [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)
Some discussion- [http://austinseraphin.com/2011/08/07/how-to-share-files-between-mac-and-linux-the-easy-way/](http://austinseraphin.com/2011/08/07/how-to-share-files-between-mac-and-linux-the-easy-way/)

I am not very familiar with proper or advanced MacOSX usage, so you may want to check more on Mac's support for all of the above.

---

### Post by Smallwheels on 2013-03-11
Thanks for the information. I'll look into it.

---

