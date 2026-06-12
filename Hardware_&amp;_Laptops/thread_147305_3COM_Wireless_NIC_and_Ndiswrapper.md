---
title: "3COM Wireless NIC and Ndiswrapper"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by methods_madness on 2006-03-19
Hello All,

I am new to ubuntu and linux. I am currently a windows user looking for an alternative. So far I must say I am very impressed, I think ubuntu is great. Now here is my problem, I have a 3COM 3CRWE154G72 11G Wireless nic, and a 3COM AP. I am using a Dell Latitude P3 650MHz, 512MB ram. When I plug in the wireless nic the 2 lights are on but very dim. I have done some research and found that I need ndiswrapper. I downloaded it and attempted to install it as directed by the install instructions, but I am unable to get anywhere, it tells me make is an unknown command. Is there a ubuntu ndiswrapper that can be installed, or is my wireless nic even compatible with ubuntu? not quite sure what Iam doing  wrong, since I am completely new to linux, so Iam unsure of how to get it to work. Any help would be  greatly appreciated. 

Thank You In advance,
Method

---

### Post by Zelut on 2006-03-19
Well I think this is the 4th ndiswrapper + wireless question I've answered today, but I'll give it a shot.

To install ndiswrapper you can do the following:
Open Synaptic (System > Admin > Synaptic) and search for / install the 'ndiswrapper-utils' package.
[or type 'sudo apt-get install ndiswrapper-utils' from the Terminal (Applications > Accessories > Terminal)

next step we'll need to find the driver for your wireless card.  Do the following return anything?
lspci | grep 802.11
lspci | grep Wireless

---

### Post by methods_madness on 2006-03-20
Thank You for the quick reply,

I tried to install using the synaptics package manager but I dont see the package come up when I search the way you said. When I run, sudo apt-get install ndiswrapper-utils, I get this......

sudo apt-get install ndiswrapper-util
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ndiswrapper-util

I  tried  this command from the terminal as a user, and i also tried as su. I also tried as soon as I open the terminal from the home directory, and I tried navigating to the directory with the ndiswrapper download and runnning it.
Can you suggest what to do now, thank you again.

---

### Post by Zelut on 2006-03-20
Well you will, of course, need some access to the internet in order to do a few of these steps.  is it possible to use a wired connection until we can get the wireless to work?  We'll need a connection in order to install the ndiswrapper-utils & download the driver..

Try to get a wired connection if possible and then we'll try again.  In the meantime (sorry) I need to get to bed ;)

---

### Post by methods_madness on 2006-03-20
Kuyaedz,

I do have a wired connection to the internet while I am doing this, I have a Xircom 10/100 Ethernet/Modem PCMCIA card. Anyway, well talk about it tommorow,  I hear yah, Iam going  to bed myself. goodnight, thanks for your time.

---

### Post by Zelut on 2006-03-20
Are you able to get online using that Xircom wired card?  If so I'm guessing the trouble with connecting to the above has something to do with your sources.list.  (I also noticed you ommited an S when typing your command.  It should read 'sudo apt-get install ndiswrapper-utils')

Let me know that you can get online (browser, chat, etc) without trouble and we'll look a little deeper.

---

### Post by methods_madness on 2006-03-20
Yes, Iam able to get online with it. After last night I ran "apt-get update" and it downloaded all sorts of fun updates. I was then able to install ndiswrapper-utils using the 'sudo apt-get install ndiswrapper-utils' command. I ran the 2 commands you specified, lspci | grep 802.11, and lspci | grep Wireless. Only the lspci | Wireless returned anything, it displayed my 3com wireless nic with its model number, 3CRWE154G72, and mac address. What would you like me to try next? 

Thanks again for all your time, I appreciate it very much.

---

### Post by Zelut on 2006-03-20
can you please post the output of 'lspci | grep Wireless' and also the output of 'lspci -n'

Thanks

---

### Post by methods_madness on 2006-03-20
Kuyaedz,

Here is the output of both commands, Thanks

lspci | grep Wireless
0000:06:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)

lspci -n
0000:00:00.0 0600: 8086:7190 (rev 03)
0000:00:01.0 0604: 8086:7191 (rev 03)
0000:00:03.0 0607: 104c:ac1c (rev 01)
0000:00:03.1 0607: 104c:ac1c (rev 01)
0000:00:07.0 0680: 8086:7110 (rev 02)
0000:00:07.1 0101: 8086:7111 (rev 01)
0000:00:07.2 0c03: 8086:7112 (rev 01)
0000:00:07.3 0680: 8086:7113 (rev 03)
0000:00:08.0 0401: 125d:1998 (rev 10)
0000:01:00.0 0300: 1002:4c4d (rev 64)
0000:06:00.0 0280: 10b7:6001 (rev 01)

---

### Post by Zelut on 2006-03-20
Ok I've found what is supposed to be the driver to use with that card.  I've never used that card before so I'm not 100%--we can give it a try though.

You'll need to download & unpack this file.  It includes the drivers:
[http://christer.homeip.net/3com.10b7.6001.zip](http://christer.homeip.net/3com.10b7.6001.zip)

Also are you able to connect using that machine at all?

---

### Post by methods_madness on 2006-03-20
Ok great,

I got it downloaded and extracted the files to my home directory in a folder called 3com. How do we go about installinig them? Yes I am able to connect to  the internet and my network, but i have  to use my xircom nic, if I try to use the 3com  wireless nothing happens. I just switch  back and  fourth during the testing and stuff we have been doing.

Thanks

---

### Post by methods_madness on 2006-03-20
I checked out your website and found that wireless tutorial you have posted, this is where Iam:

I extracted  the 3com drivers you had linked,  opened a terminal and navigated to  the 3com directory  I extracted the files to. I ran ' sudo ndiswrapper -i 3C154G72.inf', then ran 'sudo ndiswrapper -l',  it then said 'Installed ndis drivers:
3c154g72 invalid driver!' Your guide basically stopped if it did not work, any suggestions on what to do now?

Thank You Again, btw nice site.

---

### Post by Zelut on 2006-03-20
Hmm.. as I mentioned before I have never had opportunity to setup this card before so this is trial-and-error for me as well.  I am using suggested drivers from the ndiswrapper supported list, so I'm not just guessing blindly ;)

This is what I'm getting my [information]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#0-9") from (#5).  That looks like the same card you have and it matches the PC ID we found.  Now the two other things I can think of are:

We could try a later version of ndiswrapper.  It may have added support that the Ubuntu version doesn't have.  Also, this is more guess than knowledge but I have needed to use the 'linux-wlan-ng' driver for other Prism based cards.  This could help.

So, lets try this..

[B]sudo apt-get install linux-wlan-ng
[/B]
After this lets try a reboot and:
[B]sudo ndiswrapper -e 3C154G72
sudo ndiswrapper -i 3C154G72.inf
sudo ndiswrapper -l
[/B]
Any better results?

---

### Post by methods_madness on 2006-03-28
Sorry for not updating, I have been busy this week. As for my 3com wireless nic issue, I tried your guide on your website and got everything working, or atleast thought I did, and still was unable to get it to work. I did some additional research, searching various linux forums and found that my nic is a revision 2, which apparently will not work. 3com uses some sort of softmac setup with there nics and this is why it does not work. In a nutshell 99% of the posts I found said they resolved there issue by getting a different nic. This is what Iam going to do as well, because I would like to use ubuntu to the fullest extent. If you think we still will be able to get the 3com working, all suggestions would be appreciated. Thank You for all your help.

---

### Post by manu.b on 2006-05-01
Hi All,

I'm new to Ubuntu, but also trying to have my 3C154G72 card to work. I've found out the ndiswrapper trick, but this does not work for me, ndiswrapper -l says "Invalid Driver!"

Any other idea ?

Ubuntu Breezy Badger

Rgds,
Manu

---

### Post by manu.b on 2006-05-01
Just a quick update to let ypu know the solution that worked for me :
instead of using the driver on the cd, I downloaded it from the 3com website. 

Strange : it is the exact same version, but instead of copying only the inf file, I copied the whole "Driver" folder. 

Now I have to fix 2 or 3 things so that It would be activated at boot by puting the "prism54" module to blacklist... Will I guess so.

Rgds,
Manu

---

### Post by manu.b on 2006-05-02
Ok, I've had some trouble having it work form boot, but I found out that "ndiswrapper" module was not in the /etc/modules file, so I had to load it manually each time. now it works just fine.

---

