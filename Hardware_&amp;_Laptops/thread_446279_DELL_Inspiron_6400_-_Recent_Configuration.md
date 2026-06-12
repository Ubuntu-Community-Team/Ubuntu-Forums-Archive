---
title: "DELL Inspiron 6400 - Recent Configuration"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by mrbujuntu on 2007-05-16
Hello everybody, i'm an happy new ubuntu user, i'm going to buy an inspiron 6400, but i'm not sure everything i've chosen is compatible with ubuntu, is there anyone who can help me about it? Here it is the configuration i'd like to get: Processor Intel® Core™ 2 Duo T7200 (2 GHz, cache L2 4 MB, FSB 667 MHz) 2048MB 667MHz DDR2 SDRAM (2x1024) internal keyboard, italiano (QWERTY) NVIDIA® GeForce™ Go 7300 TurboCache™ with 256 MB Hard Disk SATA 160 GB 5400 rpm DVD+/-RW Mini card Intel® Next-Gen Wireless-N (for processors Core 2 Duo) Module Bluetooth 2.0 Dell Wireless 355 (til 3 Mb/s) Display TFT widescreen UltraSharp™ WXGA+ (1440 x 900) da 15,4" con TrueLife™ I've noticed that on the international site is not possible to buy this configuration, this is the configuration that i've chosen on italian site. Thanks everybody and many italian kisses!!!

---

### Post by nachotronics on 2007-05-17
I got a 6400 mostly like yours except for the Video an Wifi cards, i have the ATI X1400 and the Dell 1390 WLAN, wich i managed to get to work, not out of the box, but easily. The nVidia cards are suposed to be more linux compliant than ATIs, the same for the Intel WLAN card. Bluetooth works without any hacking.

Hope this helps :wink:

---

### Post by mrbujuntu on 2007-05-17
Hey, thanks a lot for your answer,
I have posted this questions on other forums too, here it is the link to another discussion too, it coul be useful

[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=9255#M9255]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=9255#M9255")

from the link above i submitt another question:

I don't know the medium longness it take to make a new driver the linux community, can you tell me something? Maybe if it is not much I could buy it now and wait a bit, or is there the risk to have a laptop that cannot connect by wifi when running linux?!  Ehm.........it's amletic.... 

Kisses:guitar:

---

### Post by revilodraw on 2007-05-17
i have a new 6400 same as nachotronics... everything works beautifully... word of warning, once u have installed ubuntu, try not to touch the mediadirect button or u might get some ugly problems (which are still easily fixe)...ask dell if they can pls not have a mediadirect button...

---

### Post by nachotronics on 2007-05-17
I don't really know how long it can take, it usually depends on how many people has the same WLAN card you have, for that is the amount of people trying to get it to work. In my case, Dell 1390 WLAN card, my card is NOT supported for linux, there's no linux driver for my card. Still, i got it working by using a program called ndiswrapper, wich configures your wlan card using the windows driver. 

So eventually even if there is no support for that card in linux you can still use this method, wich is widely used, because not so many manufacturers provide linux drivers, the open source driver programmers do the best they can, but there are SO MANY different pieces of hardware out there...

I configured the mediadirect button to launch my media player, through System-Preferences-Key combinations. It launchs rhythmbox by default, if you want to change that to any other program let me know. :wink:

---

### Post by thayerw on 2007-05-17
The Inspiron 6400 is in my opinion THE best notebook you can buy for that price.  I bought mine from the Dell Canada website, similar specs too:

Intel Core Duo T2500 (2 x 2 GHz)
Intel Mobile 82945 Express Chipset
1GB DDR2 Memory (Now upgraded to 2GB)
100GB SATA Hard Drive (Toshiba MK1032GSX)
8x DVD+-RW/DL (Sony DW-Q58A)
15.4&#8243; WSXGA+ Truelife LCD Display (1680×1050) 
256MB ATI Radeon X1400 Graphics
Sigmatel STAC 92xx Audio
Ricoh R5C8xx Multi-Card Reader
Intel PRO Wireless 3945 (ABG modes)
Broadcom 440 Ethernet 10/100Mbit
Conexant D110 HDA MDC v.92 Modem
85WHR 9-Cell Lithium-Ion Battery

Everything has worked out-of-the-box except for the 3D-accelerated video drivers and full resolution, however there are several posts within these forums that will walk you through the simple steps of getting those working too.

If you plan to run only GNU/Linux, then I would recommend removing the Windows and Media Direct partitions before you install Ubuntu, but FIRST make sure you back them up on CD/DVD.  Dell doesn't include the Windows Restore CD unless you request it at the time of purchase.  As someone pointed out already, the Media Direct button will open your media player when you're running Ubuntu.

Also, even if you're running Linux you should keep an eye on the BIOS updates at Dell's website.  For instance, I'm now running A14 which was released just last month (April).  Here's a great tutorial on updating the BIOS without Windows or a floppy disk:

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

Good luck and I hope you enjoy your new notebook!

---

### Post by KAding on 2007-05-17
I have a 6400 as well. With a X1400 ATI card.

Everything seems to work very well, even beryl works great without any noticeable performance problems.

Except the sleep and suspend functions. Neither of them seems to work. When I try to sleep it blanks the screen, but it never actually goes on standby (the power LED just stays on, so do the fans and stuff). At that point I have no choice but to do a hard reboot using the power button. 

When I hibernate it also blanks the screen and seems to be working, but then the screen turns on again. I can't use my keyboard at that point, its as if gnome is no longer accepting input. CTRL+ALT+Backspace works though.

Anyone have any ideas?

---

### Post by mrbujuntu on 2007-05-17
I think it is going to be a good discussion here, it will be very useful to community AND TO ME :)

this made me curious:
> Still, i got it working by using a program called ndiswrapper, wich configures your wlan card using the windows driver

Do you know if there are softwares like this for other hardware too?

---

### Post by nachotronics on 2007-05-18
> With ndiswrapper, most miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network cards work in Linux with x86 or x86-64. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., ethernet cards, USB to serial port device, home phone network device etc.

What kind of hardware are you talking about? Ndiswrapper is for wireless cards in general, there's a _**[list of cards known to work on their web page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/")**_. If your card isn't on that list it may still work, you have to try, and find the right drivers. I had to try a few different drivers for my wlan card(Dell 1390).

---

### Post by mrbujuntu on 2007-05-18
I have a canner, Canon 4200F, and there is no driver for linux, do you know if is there a wrapper for scanners?
:|

---

### Post by Lapino on 2007-05-21
> **nachotronics said:**
> I configured the mediadirect button to launch my media player, through System-Preferences-Key combinations. It launchs rhythmbox by default, if you want to change that to any other program let me know. :wink:

Well, I'd like to know how to have it start vlc. And if you have any idea  how to get the play/pause, forward,back and stop buttons to work in vlc too, I'd be ever so grateful.

---

### Post by nachotronics on 2007-05-21
Ok, i couldn't find any way to change that key's function, so i came up with this solution, wich basically consists in renaming the rhytmbox executable file to some other, i used "rhythmbox2" and then crate a link to the program you want to use, in my case xmms, and rename the link to "rhythmbox" so whenever gnome tries to start rhythmbox it will open xmms. You'll have to modify the rhythmbox menu shortcuts to point to the new rhytmbox2 file.

Here's how to:
open a terminal and go to /usr/bin
```
cd /usr/bin
```

then rename the existing "rhytmbox" file to something else: (i used rhythmbox2)
```
sudo mv rhythmbox rhythmbox2
```

now create a symbolic link to the program you want to start when "rhythmbox" is called
```
sudo ln -s vlc rhythmbox
```

Any time you run rhytmbox, vlc will start.

Now you should go to System - Preferences - Main Menu, and change the menu shortcuts so they call "rhythmbox2" instead of "rhythmbox". Wich is done by right click - properties.

Thats it..., if you want to revert changes just delete te symbolic link and rename rhytmbox2 to rhytmbox.

You should try keytouch for the play/pause, etc keys.
```
sudo apt-get install keytouch
```

Then on System - Administration you should see the keytouch configuration wizard. I had to restart for changes to happen.


Hope this helps :wink:

---

### Post by Lapino on 2007-07-02
I didn't really like the idea of changing filenames and stuff, so I decided to try it another way. Your hint to use keytouch made this possible. I made a keyboard file for the inspiron 6400 and assigned the vlc command to the media button. Didn't think it would be that simple.
I mailed the file to the developer of keytouch, but it's not yet on the site, so I've attached it to this post if anybody needs it.
Controlling vlc with the other media buttons still doesn't work tough. Probably something to do with vlc.

---

### Post by Praill on 2007-07-02
Everything there WILL work great with ubuntu except possibly the wireless card. If at all possible I would just downgrade the wireless card to the PRO abg because that one definently works. Who needs a wireless N internal network anyways? Your ISP wont be able to keep up with even a G once it leaves your house, guaranteed. So unless youre operating off a network server, wirelessly, theres no real advantage of choosing N over G... yet.

---

