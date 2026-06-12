---
title: "Ipod Classic 80 GB on Ubuntu?"
date: 2008-10-27
forum: Hardware
---

### Post by palmboompie on 2008-10-27
Hi Guys!

I just installed ubuntu because i just couldn't reach my windows anymore. I used linux before but only for reapairing things because my windows xp crashed. (and vista). Now my harddisk got stuck and it was so bad i even couldn't install windows xp anymore. So i decided to get linux (ubuntu) on it. I only have a little knowledge of linux but I managed to get all my drivers....

But here comes the problem I can't get my Ipod connected to linux, normally if I can't connect it to a computer it will charge but I just can't put music on it. But now it even doesn't charge. So could anybody help me? 
I have heard something of libgpod but I don't really get how it works/how to install it/which version to download of it.

Thank you very much, all help is appreciated. 
(even guides on how the linux-terminal works, because i figured out that it works totally not as windows)


Jacco


Excuse for my bad english, it is not my main language.

---

### Post by palmboompie on 2008-10-28
Bump:( I really need my music (wich is only on my ipod) for school. So please help me!

---

### Post by Brandel Valico on 2008-10-28
Try clicking the Applications menu at the upper left corner of the screen (if you haven't changed the default position) Click Add/Remove at the bottom of the list. Then do a search for ipod in the search box. It should bring up several ipod specific programs. I got 7 results. Since I don't have an Ipod. I can't honestly confirm any will work or not. But from what they show it seems that Hipo IPod Managment Tool or GTKPod are probably going to be the ones you should test.

Hope they do what you want them to. But the fact that it won't even charge on when connected makes me worry. Have you tried plugging it in to a different computer and seeing if it charges or connects on a Mac or a Windows PC? I'm asking because it seems like it should still charge even if you can't edit the song list. So it may be a cable issue.

---

### Post by palmboompie on 2008-10-28
> **Brandel Valico said:**
> Try clicking the Applications menu at the upper left corner of the screen (if you haven't changed the default position) Click Add/Remove at the bottom of the list. Then do a search for ipod in the search box. It should bring up several ipod specific programs. I got 7 results. Since I don't have an Ipod. I can't honestly confirm any will work or not. But from what they show it seems that Hipo IPod Managment Tool or GTKPod are probably going to be the ones you should test.

Hope they do what you want them to. But the fact that it won't even charge on when connected makes me worry. Have you tried plugging it in to a different computer and seeing if it charges or connects on a Mac or a Windows PC? I'm asking because it seems like it should still charge even if you can't edit the song list. So it may be a cable issue.

I installed serveral programs:
- GTKpod
- Hipo Ipod Managment Tool
- Amarok
- GPXpod

None of them 'sees' my Ipod. It is no cable issue because it charges at a windows computer. 

Anyone knows some more?

---

### Post by sofixy89 on 2008-10-28
Did u try different usb port? Because it should charge even when OS doesnt recognize it. Or it could be connection on your Ipod. I got 80 gb ipod too and it works with ubuntu (8.4 and 8.10) out of the box.

---

### Post by palmboompie on 2008-10-28
> **sofixy89 said:**
> Did u try different usb port? Because it should charge even when OS doesnt recognize it. Or it could be connection on your Ipod. I got 80 gb ipod too and it works with ubuntu (8.4 and 8.10) out of the box.

Tried all ports, but i just found out that no usb ports work. With all kind of devices. Does anybody know a driver for this?

---

### Post by semitone36 on 2008-10-28
I have not yet tested this but you could try an application that mimics iTunes called [songbird]("http://getsongbird.com/").  If you want to download it I would get the package [here]("http://www.getdeb.net/search.php?keywords=songbird") OR if you have a 64 bit architecture get it [here]("http://www.getdeb.net/search.php?search_distro_id=10&keywords=songbird").

I use songbird for my music and they claim to have excellent support for iPods, although I dont have one so I cant test this.  Hopefully this helps!

---

### Post by palmboompie on 2008-10-28
> **semitone36 said:**
> I have not yet tested this but you could try an application that mimics iTunes called [songbird]("http://getsongbird.com/").  If you want to download it I would get the package [here]("http://www.getdeb.net/search.php?keywords=songbird") OR if you have a 64 bit architecture get it [here]("http://www.getdeb.net/search.php?search_distro_id=10&keywords=songbird").

I use songbird for my music and they claim to have excellent support for iPods, although I dont have one so I cant test this.  Hopefully this helps!

Already use songbird... It really is a great program indeed ;)

But like I said prob my usb ports don't work. Is this a driver issue?

---

### Post by semitone36 on 2008-10-28
> **palmboompie said:**
> Tried all ports, but i just found out that no usb ports work. With all kind of devices. Does anybody know a driver for this?

Hmm.  If your iPod was able to charge but just wasnt recognized I would say it was a driver problem but if it wont even charge AND your other devices wont work with your ports, then this sounds like faulty hardware.  Is your computer still under warrantee?

---

### Post by palmboompie on 2008-10-28
> **semitone36 said:**
> Hmm.  If your iPod was able to charge but just wasnt recognized I would say it was a driver problem but if it wont even charge AND your other devices wont work with your ports, then this sounds like faulty hardware.  Is your computer still under warrantee?

No... because there's linux on it... But the ports do work kinda i just found out. When I start up my USB optical mouse is going on and my ipod charges. But as soon linux is started up (after BIOS screen) it all goes of.

And i don't know wich chipset/motherboard I have to get a driver....

---

### Post by semitone36 on 2008-10-28
> **palmboompie said:**
> No... because there's linux on it... But the ports do work kinda i just found out. When I start up my USB optical mouse is going on and my ipod charges. But as soon linux is started up (after BIOS screen) it all goes of.

And i don't know wich chipset/motherboard I have to get a driver....

Wow haha that is a new one for me.  Then yes that sounds like a driver problem to me.

Try this: go to System -> Administration -> Hardware Devices and see if any of your drivers are disabled.  If they are, enable them.  If all of your drivers are enabled and your ports STILL dont work, then you will have to find out what kind of hardware and drivers you have and try to find drivers that work.  

Unfortunately that is about the extent of my knowledge.  Hopefully there is someone else here who can give you better advice if this does not work.

---

### Post by Brandel Valico on 2008-10-28
Changing the OS shouldn't void a hardware warranty. Anyone who says it does is probably lying to you. 

Lets see if Ubuntu is seeing your usb ports or not.

With it fully loaded open the terminal. Then type in "lsusb" and hit enter.

That will show a list of the devices plugged into your USB ports.

For example my list currently shows
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Hopefully your's will give similar results.

See if it shows your devices and for example the Ipod

---

### Post by palmboompie on 2008-10-28
> **semitone36 said:**
> Wow haha that is a new one for me.  Then yes that sounds like a driver problem to me.

Try this: go to System -> Administration -> Hardware Devices and see if any of your drivers are disabled.  If they are, enable them.  If all of your drivers are enabled and your ports STILL dont work, then you will have to find out what kind of hardware and drivers you have and try to find drivers that work.  

Unfortunately that is about the extent of my knowledge.  Hopefully there is someone else here who can give you better advice if this does not work.

Sorry pal all hardware is enabled ;) But thanks for all the help!

---

### Post by palmboompie on 2008-10-28
> **Brandel Valico said:**
> Changing the OS shouldn't void a hardware warranty. Anyone who says it does is probably lying to you. 

Lets see if Ubuntu is seeing your usb ports or not.

With it fully loaded open the terminal. Then type in "lsusb" and hit enter.

That will show a list of the devices plugged into your USB ports.

For example my list currently shows
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Hopefully your's will give similar results.

See if it shows your devices and for example the Ipod
It was in the warranty i got with my laptop. If i ever would install any other OS then Vista i wouldn't have any waranty anymore. Well this is how it went:
- I hate vista, but worked with it.
- Vista crashed, xp installed.
- I don't like xp, but had to work with it
- Xp crashed so hard i couldn't install a new xp 
- Linux installed

Anyway it's giving this results:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

It is true i have 3 ports...
In 1 my ipod, in the other my external sound card, and in the other my wireless mouse.

But it doesn't show them :S

---

### Post by palmboompie on 2008-10-28
Anyone knows how to discover what kind of driver I need?

---

### Post by palmboompie on 2008-10-29
Bump

Sry people but I'm really desperate... I need my music for school, and don't have anyway to put it on my laptop. Can't do it with a memory stick caus my usb ports doesn't work :S.

---

### Post by scottuss on 2008-10-29
Hi, your computer is not seeing your ipod, or any other USB devices as far as I can tell from your response.

There could be several reasons for this. Firstly, can you use any other USB devices? If they don't work, there could be a problem with your USB hub / card / connectors etc.


Problem is, at the moment if you have things plugged into your USB ports when you did lsusb, it's looking like you have a USB problem.

Edit: Oh by the way, are the ports you are trying inside your computer or are they in a hub? I just re-read your OP and it says you can't charge your iPod from any of the ports, this would suggest their is no power in the ports (the iPod does not need to be recognised by the PC to charge)

---

### Post by palmboompie on 2008-10-29
> **scottuss said:**
> Hi, your computer is not seeing your ipod, or any other USB devices as far as I can tell from your response.

There could be several reasons for this. Firstly, can you use any other USB devices? If they don't work, there could be a problem with your USB hub / card / connectors etc.


Problem is, at the moment if you have things plugged into your USB ports when you did lsusb, it's looking like you have a USB problem.

Edit: Oh by the way, are the ports you are trying inside your computer or are they in a hub? I just re-read your OP and it says you can't charge your iPod from any of the ports, this would suggest their is no power in the ports (the iPod does not need to be recognised by the PC to charge)
Nope can't use any USB devices. But I think they do work. Because when I put my Ipod in the  the screen lights up (from the ipod, if it was on standby). So it is giving _some_ power. But it just wont charge.

Probably not enough power to light up a mouse or something, those won't work.

Can anybody just tell me is there a possibility that there is no good driver? If so where can I get USB driver's/controller's.

---

### Post by scottuss on 2008-10-30
As you say there is not enough power, getting drivers will not change this. Drivers are not required for USB ports to give power to devices. All I can suggest is that your USB ports are faulty. Can you try a USB PCI card?

Again you don't say if the USB ports you are trying are directly inside your computer (on the motherboard) or if they are on a hub plugged into a USB port on your computer. Further information could help.

Like I said though, a driver won't make any difference to power output.

---

### Post by palmboompie on 2008-10-30
> **scottuss said:**
> As you say there is not enough power, getting drivers will not change this. Drivers are not required for USB ports to give power to devices. All I can suggest is that your USB ports are faulty. Can you try a USB PCI card?

Again you don't say if the USB ports you are trying are directly inside your computer (on the motherboard) or if they are on a hub plugged into a USB port on your computer. Further information could help.

Like I said though, a driver won't make any difference to power output.
Nope. Not enough room in my laptop for a PCI card.

It's not ahub but on the motherboard. 

Is there just a usb driver for linux available? Because my mouse won't even be recognized (not even one that need's no power)...

---

### Post by scottuss on 2008-10-31
> **palmboompie said:**
> Nope. Not enough room in my laptop for a PCI card.

It's not ahub but on the motherboard. 

Is there just a usb driver for linux available? Because my mouse won't even be recognized (not even one that need's no power)...

Firstly, the mouse DOES need power to function, which your USB port should provide. If the mouse lights up during POST when the BIOS is loading then it sounds like the ports are OK. 

I would post a bug report to say that your USB ports aren't functioning on Launchpad because I've never heard of USB ports being detected but not functioning at all, certainly not in this way.

---

