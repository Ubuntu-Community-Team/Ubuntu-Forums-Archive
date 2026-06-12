---
title: "Halp"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by 0V3RC10CK3D on 2005-09-20
Okay so i just installed ubuntu but i'm a bit of a linux noob

I got the wireless card to half work on my laptop but i'm not sure whats wrong

I can send and recieve packets, i can connect to my router and login to the config panel of it, i was assigned a dhcp ip and everything

but i cant do jack online, i cant connect to anything or load any websites, the dns servers are set but i think they should be assigned with dhcp anyhow. halp?

---

### Post by matthew on 2005-09-20
What card do you have? 
What type of router are you connecting to? 
Are you using DHCP or a static IP? EDIT: Scratch that one, he already answered it. My bad.
Are you using any sort of wireless encryption like WEP or WPA?
Anything else you could add to make the diagnosis easier?

---

### Post by 0V3RC10CK3D on 2005-09-20
[QUOTE=matthew]What card do you have? 
What type of router are you connecting to? 
Are you using DHCP or a static IP? EDIT: Scratch that one, he already answered it. My bad.
Are you using any sort of wireless encryption like WEP or WPA?
Anything else you could add to make the diagnosis easier?[/QUOTE]

DLink 524 Router
DHCP
128bit WEP
AirPlusG DWL-G630 Wireless Networking Card

So i can connect to the router, but not access any computers on the network or the internet, but for some reason about 15 minutes later it started working for no reason, so i restarted and it stopped working again, could it be it's just taking years for the WEP handshake thingy to take place?


EDIT: So i figured out that i need to disable my wired networking port before the wireless kicks in.... =\, anyway around having to do that every time? And when i restart the computer it spends 5 minutes trying to synchronize the clock while loading because it's not getting any conectivity until after i login and deactivate the wired port.

---

### Post by matthew on 2005-09-20
[QUOTE=0V3RC10CK3D]DLink 524 Router
DHCP
128bit WEP
AirPlusG DWL-G630 Wireless Networking Card

So i can connect to the router, but not access any computers on the network or the internet, but for some reason about 15 minutes later it started working for no reason, so i restarted and it stopped working again, could it be it's just taking years for the WEP handshake thingy to take place?


EDIT: So i figured out that i need to disable my wired networking port before the wireless kicks in.... =\, anyway around having to do that every time? And when i restart the computer it spends 5 minutes trying to synchronize the clock while loading because it's not getting any conectivity until after i login and deactivate the wired port.[/QUOTE]

It looks like you are making good progress figuring out the problems. It is possible to skip past the clock synchronization by hitting control-c. I think a good next step is to try to make the wireless connection the primary/default connection.

System->Administration->Networking. Enter password. 
In the Network Settings window disable the ethernet connection and configure the wireless as needed. Then, at the bottom of the window choose your wireless connection as the default gateway device. Click OK.

Hopefully that will do it. I'm not sure why it seems to be taking so long to make the connection from the router to the internet. If you are able to connect to your router through the wireless card from your computer then the WEP stuff is configured properly.

Maybe after doing all the above, try to turn the router off and back on in order to reset it and force it to get a fresh connection to the internet this time. In the meanwhile turn your computer off and don't boot again until after the router is reset and see if it works right off.

---

### Post by 0V3RC10CK3D on 2005-09-21
I think i got the networking all figured out now, i had already set the wireless for default and such, how come when i try to update the system it says

" it is not possible to upgrade all packages "

mozilla-openoffice.org
openoffice.org2
openoffice.org2-base
openoffice.org2-calc
openoffice.org2-common
openoffice.org2-core
openoffice.org2-draw
openoffice.org2-evolution
openoffice.org2-gnome
openoffice.org2-impress
openoffice.org2-l10n-en-gb
openoffice.org2-l10n-en-us
openoffice.org2-math
openoffice.org2-writer
python-uno

What's it trying to tell me? They're already up to date? Or they cant be updated because some reason? I dont see the point in the box poping up unless it's warning me of something that i could do about it.

---

### Post by 0V3RC10CK3D on 2005-09-21
I disabled the wired port, updated a few things that were on the updates list,  and now when i restart i get an error

"Failed to start the X server"

---

### Post by 0V3RC10CK3D on 2005-09-21
any ideas? i've confirmed it wont start X Server after i update all the files, shall i just reinstall and not update?

---

### Post by matthew on 2005-09-21
Try this. From a command line:

```
sudo dpkg-reconfigure xserver-xorg
```

Go through the process. Just choose the defaults unless you know for sure they are wrong.

When finished you can reboot if you like or try:

```
sudo /etc/init.d/gdm start
```

---

### Post by 0V3RC10CK3D on 2005-09-21
I ended up just reinstalling breezy, i got everything setup, ( didnt update, LOL )

I installed VLC media player, figured out how to install the libdvdcss2 stuff so i could play dvds and such

But...next problem, the video is super choppy, any way to fix that? possibly new video drivers? Dare i try to install some?

I have a Dell Inspiron 5100 laptop
2.8ghz P4
radeon mobility 7500
512MB DDR2100 RAM
40GB 5400RPM 16MB cache harddrive ( wasnt stock, LOL )

and...i think that's all that is relevant, is there a way to check what drivers i'm currently using for my video card? most likely the universal shitty mode ones.

And thanks for all your help mathew you seem to be very knowledgable, do you have aim, msn xfire or any instant messaging services incase you'd be willing to help me with some little stuff like this?

---

### Post by 0V3RC10CK3D on 2005-09-21
So aparently it's only choppy the first time i play a segment of the movie, if i skip back 5 seconds and replay it then it goes smooth, so i figured the dvd drive wasnt reading fast enough or something, for some reason. So i enabled DMA, or i think i did, i uncommented the section for it in that one file, but it still runs choppy, any ideas?

---

### Post by matthew on 2005-09-21
[QUOTE=0V3RC10CK3D]I ended up just reinstalling breezy, i got everything setup, ( didnt update, LOL )[/QUOTE]
Okay. Well, I'm sorry we couldn't get it going another way, but I'm glad things are working for you.
> I installed VLC media player, figured out how to install the libdvdcss2 stuff so i could play dvds and such

But...next problem, the video is super choppy, any way to fix that? possibly new video drivers? Dare i try to install some?
Before trying anything else out, take a look at this and make sure DMA is activated for your dvd drive. That is likely to take care of your problem.
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#speedupcddvdrom](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#speedupcddvdrom)

> is there a way to check what drivers i'm currently using for my video card? most likely the universal shitty mode ones.

If you haven't done anything to install different ones you will probably want the ATI drivers. These can be tricky. My best advice is to do a search on these forums for threads about ATI and read, read, read. I had some problems myself. However, if everything works right now and after enabling DMA for your dvd drive, you really don't need the ATI drivers except for 3D acceleration. I am far from an expert on these, though and would have to tell you to ask around...a good idea would be to start a new thread.

> And thanks for all your help mathew you seem to be very knowledgable, do you have aim, msn xfire or any instant messaging services incase you'd be willing to help me with some little stuff like this?
You are welcome. There are others in these forums and elsewhere that are far more knowledgable than me...I just happened to be the one to help this time. On irc you can check in #ubuntuforum or #ubuntu (use Xchat. It's in the repos if it isn't already installed). There are usually helpful and knowledgable people there.

One more bit of advice, read the links in my signature. The ubuntuguide seems to be down right now, but there's a mirror at: [http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)
These will be very helpful to you.

---

### Post by matthew on 2005-09-21
[QUOTE=0V3RC10CK3D]So aparently it's only choppy the first time i play a segment of the movie, if i skip back 5 seconds and replay it then it goes smooth, so i figured the dvd drive wasnt reading fast enough or something, for some reason. So i enabled DMA, or i think i did, i uncommented the section for it in that one file, but it still runs choppy, any ideas?[/QUOTE]
You posted this while I was writing the other one. I don't use VLC, but I know others here do. I think your best bet at this point is to start a new thread and see if someone who knows a bit more about this specific issue might see it. Maybe title it something like "DVD playback choppy in VLC with DMA enabled" and then put the same computer info in the post that you posted here along with the description of the problem. Hopefully we can get this figured out pretty quickly.

---

### Post by 0V3RC10CK3D on 2005-09-21
Yeah, I've been following that guide a bit and thats what i added to the file, didnt work

/dev/cdrom {
       dma = on
}

But i was searching through the /dev/ folder and i saw a folder called dvd, so for the hell of it i changed the file to this

/dev/dvd {
       dma = on
}

and guess what?  =D


IT WORKS!!, i'm so happy, hehe, sofar i've figured out most of my problems in ubuntu, just takes a bit of thinking

---

### Post by 0V3RC10CK3D on 2005-09-22
I created a guide for how i got VLC to work in Breezy, incase anyone else ponders

[http://www.ubuntuforums.org/showthread.php?p=364500](http://www.ubuntuforums.org/showthread.php?p=364500)

---

### Post by matthew on 2005-09-22
Congratulations, dude! It's a good feeling, isn't it?

---

### Post by 0V3RC10CK3D on 2005-09-22
^^

---

