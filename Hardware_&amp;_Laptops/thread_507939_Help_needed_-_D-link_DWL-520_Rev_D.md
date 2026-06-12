---
title: "Help needed - D-link DWL-520 Rev D"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by firestrap on 2007-07-23
first, i'm very to new to ubuntu and linux and general.

i recently installed feisty fawn on an old computer to test out ubuntu linux. everything went very smoothly except for my wireless card - d-link dwl-520 rev. d.

i tried using ndiswrapper to no avail and even the ndisgtk (gui) just in case i messed something up -- nothing. the driver installs, hardware present.

everything looks good after this command: ndiswrapper -l, but when i go to the network panel, the connection is not listed. the wired connection works fine, but i don't need to be moving my modem and router every time i want to use the internet.

the router is fine. there is no WEP. i use two other computers at home that connect just fine.

this is straight from the ndiswrapper website concerning the specific card:

> AP isnt found automagically but iwlist wlan0 scan shows AP’s.

i'm not sure what that will do for me, as i'm very new to linux.

has anyone successfully installed the driver for this card? should i give up and buy another card?

thanks for any help in this matter. i'm very anxious to test out the soulseek linux version.

---

### Post by fredj on 2007-07-24
I have successfully installed this card using win XP drivers and ndiswrapper. However there is a problem
with the version of ndiswrapper in Feisty and it often doesn't install drivers properly. 
Open a terminal and type 
sudo ndiswrapper -v 
Post the ouput from that here. 
The only way round that is to download the latest source files from the ndiswrapper site, then install the
build-essential package and recompile ndiswrapper.
With the proper version of ndiswrapper I have installed three different DLink cards with no problems.
With the ndiswrapper supplied with Feisty none of them would work.

---

### Post by firestrap on 2007-07-24
thanks for helping.

here's the output...

utils version: 1.7
driver version:   1.38


i have no experience with recompiling anything, so hopefully i can get this to work.

---

### Post by firestrap on 2007-07-25
update:

it's working! I can't quite beleive it, but it is.

I tried what you said worked -- installed build-essential package, downloaded ndiswrapper 1.47 (latest stable release) and recompiled.

still didn't see my wireless connection anywhere. i opened up Wicd Manager, went into preferences and entered "wlan0" in the "wireless interface" field, and my network was found right away.

i'm sure there's a way to do what i did without Wicd Manager, but being such a newb i used graphical means.

thanks again for your help. knowing it was possible made a big difference.

---

### Post by Permafrost91 on 2007-08-07
could you detail please how you solved your problem? I still don't have my DWL-520+ PCI card working under Feisty. Thanks!

---

### Post by firestrap on 2007-08-10
i'll detail what i did, and hopefully it'll work for you.

1. first i downloaded the latest stable version of ndiswrapper:

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)


2. follow the instructions for installing ndiswrapper 1.47 using build install (see attached .txt file)

3. install XP driver using ndiswrapper. i don't remember exactly how to do this off hand, but a search should yield good results rather quickly.

4. at this point, the driver was installed successfully, but no wireless networks were being found. i'll let you know how i did it, but i'm nearly 100% sure you can do it from the terminal without installing or uninstalling anything else. iwlist maybe?

i installed wicd - [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) - followed instructions for installation and what to uninstall. then i opened up Wicd Manager, went into preferences and entered "wlan0" in the "wireless interface" field.

after that, i did nothing. it automatically found my network and connected.

i hope this helps. good luck.

---

### Post by peebly on 2007-08-31
Hello

Just to say I have managed to install this card quite easily using the windows wireless drives app in gutsy.

How to.

First you need to get the drivers from dlink, I had to move my computer to the room where the router was so I could connect the computer to it using a network cable. what a fart on.

then

Use add/remove to install the windows wireless drivers app, its under system tools, application will appear in system - administration. (*internet connection required*)

run the application and select install new driver, navigate to the driver folder, mine was on the desktop. You want the net5513.inf file.

I had to restart my computer to get it up and running. once at the desktop the network-manager popped up and asked for the wpa key, entered it and it works.

So far the DWL-G520M MIMO pci Card is running at 54 mb/s, wpa works. I don't have a router that supports 108G so I dont know if the card would run at that speed under ubuntu.

If I have any problems I will post them back but so far it seems fine.

getting there,:popcorn:

---

