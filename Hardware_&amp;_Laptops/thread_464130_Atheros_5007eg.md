---
title: "Atheros 5007eg"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by why? on 2007-06-04
Madwifi does not work with (k)Ubuntu 7.04 and the Atheros 5007eg as the chip is yet to be supported. I am hoping to use ndiswrapper to get this card to work. 

What kills me is that Kubuntu works with so many things out-of-box, but not this wireless card. I have many USB devices that are recognized through Kubuntu without any tinkering at all. My phone works without fail from Kubuntu, whereas windows won't without installing the phone's CD. So many things work better or without modification in Kubuntu that this one thing, the wireless card, isn't going to deter me. 

I know madwifi is supposed to support Atheros, but as of this writting, the AR5007eg is not supported by madwifi. 

I want to make sure I do this correctly and I don't know where to disable other drivers or anything. I'm fairly new to Kubuntu and completely new to command prompts and such. I'm a GUI computer user, so a lot of the command line work eludes me. 

So, if anyone has had any experience using the Atheros chip and ndiswrapper, I could sure use a point in the right direction. I have the ndiswrapper source and the windows drivers on thumbdrive.

---

### Post by oooooops on 2007-06-05
I also have an Atheros and have been swapping over to the ndiswrapper.  While I can't (yet) connect to my WPA protected network I have been able to connect to my neighbour's unsecure access point :) you know just to check to make sure I can connect somewhere.

My experience thus far has been knetwork-manager has not been useful (I'm on Kubuntu Feisty)  That's just a side note.  I've tried wicd as well - it didnt' help with the problem I have now.

Here are the posts I've been using

[http://ubuntuforums.org/showthread.php?p=2688436]("http://ubuntuforums.org/showthread.php?p=2688436")

[http://ubuntuforums.org/showthread.php?t=419348]("http://ubuntuforums.org/showthread.php?t=419348")

[http://ubuntuforums.org/showthread.php?t=419709 ]("http://ubuntuforums.org/showthread.php?t=419709")  (This is probably the step I"m at now but I have yet to get the WPA part working)

I found ndiswrapper much easier to use from command line than from the GUI.  And wine by default (if like me your drivers are in an EXE) extracts to ~/.wine/blah/blah/blah directory to start with (sorry not on the machine I'm configuring right now).  I did a softlink to make it easier to get to them

ndiswrapper -i <inf_file_name> installs the drivers

Be sure to follow the part about blacklisting the ath (madwifi) drivers if they are loaded.  And make sure you don't type in aht when you blacklist it can cause a migraine to figure out :)

Good luck.

And if you get iwconfig/iwprivate working please reply and let me know.  I'll do the same ...

---

### Post by why? on 2007-06-05
At least I have ndiswrapper installed and the driver installed, at least according to the ndis interface, but still, there's no connection. It doesn't even show a hardware device for my Atheros 5007eg. No matter what driver I try, the device still doesn't show in the network configuration panel.

I bought another card, hoping it would work (Asus WL-107g) but it doesn't work either :(

---

### Post by Platypi007 on 2007-06-20
Yeah, I've been having the same problem and thus far everything I have found seems to point to no one having been able to get this card working with NDISWrapper *or* MadWifi as of yet...

I only hope that MadWifi will offer support soon since they support the other cards in this series from what I've seen.

---

### Post by why? on 2007-06-22
I finally have it working with ndiswrapper in pclinux. It's not Kbuntu, but it does work and it worked with the Win XP 32 bit driver from Atheros.cz 

It was a clean install. Hardware wasn't recognized device showed as "null" in the PCLinux PCC, but I used the ndiswrapper and viola - open, WEP, WPA, the all work, even with TKIP - it works. And the range compared to XP is fantastic!

---

### Post by Platypi007 on 2007-06-22
I used ndiswrapper and the driver off that site but it didn't seem to detect the card...  Perhaps I should try again.

---

### Post by why? on 2007-06-22
I only got it working with PCLinux 2007.  I still can't get it to work under Kubuntu.

---

### Post by Mr. P. on 2007-07-10
I use SIDUX so far -- the Ndiswrapper install works even right on the Live-CD. :D

The -buntus are not recent enough yet :( Ndiswrapper > 1.45 is required.

[http://ubuntuforums.org/showthread.php?p=2998296#post2998296]("http://ubuntuforums.org/showthread.php?p=2998296#post2998296")

---

### Post by ntlam on 2007-08-16
> **oooooops said:**
> I also have an Atheros and have been swapping over to the ndiswrapper.  While I can't (yet) connect to my WPA protected network I have been able to connect to my neighbour's unsecure access point :) you know just to check to make sure I can connect somewhere.

My experience thus far has been knetwork-manager has not been useful (I'm on Kubuntu Feisty)  That's just a side note.  I've tried wicd as well - it didnt' help with the problem I have now.

Here are the posts I've been using

[http://ubuntuforums.org/showthread.php?p=2688436]("http://ubuntuforums.org/showthread.php?p=2688436")

[http://ubuntuforums.org/showthread.php?t=419348]("http://ubuntuforums.org/showthread.php?t=419348")

[http://ubuntuforums.org/showthread.php?t=419709 ]("http://ubuntuforums.org/showthread.php?t=419709")  (This is probably the step I"m at now but I have yet to get the WPA part working)

I found ndiswrapper much easier to use from command line than from the GUI.  And wine by default (if like me your drivers are in an EXE) extracts to ~/.wine/blah/blah/blah directory to start with (sorry not on the machine I'm configuring right now).  I did a softlink to make it easier to get to them

ndiswrapper -i <inf_file_name> installs the drivers

Be sure to follow the part about blacklisting the ath (madwifi) drivers if they are loaded.  And make sure you don't type in aht when you blacklist it can cause a migraine to figure out :)

Good luck.

And if you get iwconfig/iwprivate working please reply and let me know.  I'll do the same ...


I followed those steps and many in other threads but no success. I am so screwed now. 
I have a satellite u305 and my wireless info: atheros ar5007eg.
any help please....
Lam

---

### Post by ntlam on 2007-08-16
Actually my wireless worked before i got my partitions deleted while trying to merge them...

---

### Post by ntlam on 2007-08-16
and now i dont remember how i did before...
my life seems being over...

---

### Post by ntlam on 2007-08-16
Here's what i tried with no happiness

Step 1: Disable ath_pci

sudo rmmod ath_pci
sudo gedit /etc/modprobe.d/blacklist-common

add the following line at the end of the file

blacklist ath_pci

Save and close

Restart computer

step 2. remove old ndiswrapper by using synaptics

Step 3: Build essentials
Use the synaptic package manager
Install the package called "build-essential" in the group called "Development"
But I already got it installed

Step 4: Install Ndiswrapper.

Go to [http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)
Download ndiswrapper-1.47.tar.gz to folder /home/username

Code:

cd /home/username/
sudo tar xvzf ndiswrapper-1.47.tar.gz
cd /home/username/ndiswrapper-1.47/
sudo make
sudo make install

Step 5: Load drivers with ndiswrapper.
sudo ndiswrapper -i net5211.inf

installing net5211 ...

forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
........ a lot of lines like above...

then:
sudo ndiswrapper -l
net5211 : driver installed
device (168C:001C) present (alternate driver: ath_pci)

Step 6: Load ndiswrapper and check if it worked
sudo modprobe ndiswrapper

Check it:
iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

Then I did:

sudo ndiswrapper -m


But no wireless after reboot

---

### Post by ntlam on 2007-08-16
[http://ubuntuforums.org/showthread.php?p=3202754#post3202754](http://ubuntuforums.org/showthread.php?p=3202754#post3202754)
got it

---

