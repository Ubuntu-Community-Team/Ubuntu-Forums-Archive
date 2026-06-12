---
title: "Gnomad2 with Creative Zen"
date: 2005-11-26
forum: General Help
---

### Post by BurningSnowman on 2005-11-26
Hi there,

I'm still not too competent with anything more than basic operations, but have been happily using Ubuntu as my main desktop system for a few months now. I upgraded to 5.10 a little while back.

I've just bought a Creative Zen. Not a Zen Micro or Zen Touch or Zen Xtra or Zen Anything Else, just a Zen. It's not been released loudly, but apparently it's big in Asia. I've dubbed it the 'Zen Nothing' for clarity. Amazon UK are [selling them](http://www.amazon.co.uk/exec/obidos/ASIN/B000BLEW9I/qid=1133047111/sr=8-1/ref=sr_8_xs_ap_i1_xgl/202-7843215-3523064), and the capacity/bulk/price balance appealed to me. (Even though I've just noticed that they dropped the price &#163;5 immediately after I bought it. :rolleyes:  ) Wikipedia can [tell you more](http://en.wikipedia.org/wiki/Creative_Zen#Creative_Zen). From what I've read, it not only looks like a fattened up Micro, but should also behave much like a Micro.

I've tried to install Gnomad2 in various ways, starting with the easy Synaptic method, moving on to various commands and shell scripts I don't really understand. I've installed every related program under the sun, including the much-noted libnjb(5). Basically, installing an old version of Gnomad leads it to not recognise the player ("No jukeboxes found on USB bus"), both launching from the menu and via a 'sudo gnomad2' in the terminal. Using the latest version (2.8.0-2) as I ought to, I get the same result, but with the addition of the following error in the terminal when running the command in said terminal:
> (gnomad2:10104): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed

I realise the model is somewhat unusual, but [Gnomad's home page](http://gnomad2.sourceforge.net/) lists "Creative Zen" as a supported model, and I was pretty hopeful that this was the same thing as my Zen Nothing. I somehow determined/read that my device's details would be in **/proc/bus/usb/devices** if it was connected and recognised somehow. It is, which is nice. Everything seems to work in theory, until you actually try to use the program. The relevant portion of the devices file is:
> T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=411d Rev= 1.00
S:  Manufacturer=Creative Technology Ltd
S:  Product=Creative Zen
S:  SerialNumber=0105255199038F78
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
After skipping over the parts I didn't understand (everything), I noticed that the '411d' was rather close to some of the 3rd values in **/etc/hotplug/usb/nomad.usermap** (which I *think* is used to determine supported models, right?), and '041e' matches most of the 2nd values, so I boldly added a line which would seem to be a logical extension to all these values I don't understand, and which I hoped would match up with my Zen's data, into the nomad.usermap file:
> nomadjukebox	0x0003	0x041e	0x411d	0x0000	0x0000	0x00	0x00	0x00	0x00	0x00	0x00	0x00000000
No difference. File saved correctly, changes survive a restart, but program's behaviour is unchanged.

Am I even warm? Numerous tutorials seem to have led me round in (Apple patented ;)) circles, always to get the same errors.

Any help would be most appreciated. Educated guesses and ideas for trial and error are welcome too: you may have noticed that my method thus far has not been based entirely on precise and considered logic. :)

---

### Post by fog on 2005-11-27
My Creative Jukebox 3 works fine with gnomad2 until the last updates
a few days before.
Now:
> (gnomad2:11924): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed
Xlib: unexpected async reply (sequence 0x79b)!


Thanks for your help

---

### Post by psypher on 2005-12-21
I JUST got a new Creative Zen and am VERY eager to start using it and actually have some tunes on it. And I too am having the exact same problem as everybody above. What the trouble, I see LOST of other people have similar problems and the same problem. Some say use root, that don't work. Please help, this is annoying!

I run Breezy and installed the libnjb and gnomad2 packages from synaptic.

---

### Post by BathroomNinja on 2005-12-21
I have this working at home with a Creative Zen Micro and a Creative Zen Jukebox Xtra (that's a REALLY long name for an mp3 player).

When I get home in about 13 hours, I'll look and see how I did it.  I know I searched the forums here and found the answer at some point.

---

### Post by bigzak on 2005-12-21
You could try installing njbtools to check the Zen for visibility. Use njbtracks to list the tracks on the Zen, both with sudo and without.

There appears to be two versions of libnjb available; libnjb1 and libnjb5. njbtools uses version 1, while gnomad2 uses version 5. Not sure if that's particularly relevent, but if njbtracks can see the Zen and Gnomad2 can't, then it could be an avenue of investigation.

---

### Post by cbudden on 2005-12-21
I will be able to test my Zen on friday, when I get it for my birthday.  The zen micro works fine on my laptop.

---

### Post by BathroomNinja on 2005-12-21
I found the guide I used!

[http://doc.gwos.org/index.php/GnomadnCreative](http://doc.gwos.org/index.php/GnomadnCreative)

---

### Post by cbudden on 2005-12-22
[QUOTE=BathroomNinja]I found the guide I used!

[http://doc.gwos.org/index.php/GnomadnCreative](http://doc.gwos.org/index.php/GnomadnCreative)[/QUOTE]


Have you got a mirror for this site?  I cannot seem to get on it.

edit

Site is back up, and my Zen still does not want to play.

---

### Post by BurningSnowman on 2005-12-23
[QUOTE=BathroomNinja]I found the guide I used!

[http://doc.gwos.org/index.php/GnomadnCreative](http://doc.gwos.org/index.php/GnomadnCreative)[/QUOTE]
I too found it was down before, but got the site today. And it actually worked!
With some changes to the instructions to match all the requirements of new versions, I seem to actually have Gnomad2 working with my 'Zen Nothing'. I love you! Thanks!

How far are you getting, cbudden? I had to download the files manually, as the URL format in the instructions downloaded HTML files from Sourceforge instead of the source, for some reason.

---

### Post by linuxbtdsc on 2005-12-23
My Creative Zen works fine. To get it to work though I have to run gnomad2 as root (sudo gnomad2) otherwise I get those errors also. Try that....

-linuxbtdsc

---

### Post by cbudden on 2005-12-23
I tried this morning, and it failed when trying to compile gnomad2 from source.  Said in ./configure that my libnjb files were not found or not in the correct place.   I installed them from synaptic and the -dev ones, which then did not help.  Unfortunatly i cannot again get on the link.  Thanks for your help/

---

### Post by Confuse on 2005-12-23
Guys, just to let you know, the latest version of banshee music player supports nomad jukeboxes!! But I don't know when and if it'll enter breezy.

---

### Post by cbudden on 2005-12-23
Ok, when I tried installing libnjb again it worked as did installing gnomad2 from source, but it still says about not detecting.  What was that about mapping something or other in the link?

---

### Post by cbudden on 2005-12-24
Anyone?

---

### Post by cbudden on 2006-01-01
I have now been able to get my Zen to work by using gnomad2 and libnjb packages from Dapper.  If anyone would like these, post a message here or PM me.

---

### Post by BurningSnowman on 2006-01-06
Glad you got it to work, and sorry I didn't respond sooner.

I probably inadvertently did much the same thing, since I ended up manually downloading at least one package that was more recent than the current Breezy version. I still don't know what the hell I'm doing when I compile stuff from source via the terminal, but damned if I didn't manage it anyway. :D

Gnomad's still working nicely for me now, and I've just worked out how you're supposed to do playlists, which should be a *lot* more convenient than doing it on the Zen itself. Very nice.

---

### Post by Omnios on 2006-01-11
Hi I just got a Creative ZEN micro 6 GB mp3 player. I tryed one of the guides but the link was kind of bad. I also tryed downloading from synpatic but it can not find a jukebox though checking my usb ports shows the player is there. Do I have to mount it? or something?

---

### Post by cbudden on 2006-01-11
[QUOTE=Omnios]Hi I just got a Creative ZEN micro 6 GB mp3 player. I tryed one of the guides but the link was kind of bad. I also tryed downloading from synpatic but it can not find a jukebox though checking my usb ports shows the player is there. Do I have to mount it? or something?[/QUOTE]


What did you try downloading from synaptic?  The program you need is called gnomad2.

---

### Post by Omnios on 2006-01-11
It installs with the lib5 version which did not detect my Zen micro 6GB

---

### Post by BurningSnowman on 2006-01-11
Which link was bad? I found that using the Sourceforge link with a question mark in it (as per one of the tutorials) resulted in the HTML download page being saved, so I had to run the download manually and proceed from there.

If you can get it functional through Synaptic alone, you've done better than me. Much like you, I was getting a similar lack of detection through the nomad-type stuff, even though the device was recognised on USB. I think the only difference in what I ended up using was that some of the versions were more up to date than those offered in the Ubuntu repositories.

---

### Post by Omnios on 2006-01-11
I tryed installing it using the [http://doc.gwos.org/index.php/GnomadnCreative]("http://doc.gwos.org/index.php/GnomadnCreative") how to the library is still there but there is a new Gnomad2 player that requires a newer library version. Im just wondering if all the config stuff will be the same for the new library. Think it as lib 2.5 or something instead of 2.0. Im going to try it with the new lib when I get around to it as I realy do not want to boot win to load music onto my Zen Mini

---

### Post by Omnios on 2006-01-11
K downloaded the libnjb 2.2.4 and used the same instruction however when I t ry to launch gnomad2 I get the following error 
 
 ```
No Jukeboxes found on USB bus
```

 ANy syggestions my windows explorer can not seem to find it ether but it works in media player. ?????

 It seems that the player is mounting though

```
tom@reboot:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda2 on /media/Documents type vfat (rw,noexec,nosuid,nodev,gid=100,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
tom@reboot:~$

```

 K one thing MyZen Micro is a Zen Micro 6 gig I do not see the word jukebox anyware on my documention. Is there a difference?

 I think it has something to do with the Zen Micro beign usb2.

---

### Post by cbudden on 2006-01-12
Put the files I have attached in /etc/hotplug/usb/ and then do 
sudo /etc/init.d/hotplug restart

Plug your Creative in and give gnomad2 a go.  Good luck.

---

### Post by Omnios on 2006-01-12
K aperently the Zen Micro Media explorer does not work in XP, I needed to install the Zen Micro Media explorer (for Playforshure devices). This does work in XP. My firmware version is 2.21.1. Is there a play for shure library?

---

### Post by cbudden on 2006-01-12
[QUOTE=Omnios]K aperently the Zen Micro Media explorer does not work in XP, I needed to install the Zen Micro Media explorer (for Playforshure devices). This does work in XP. My firmware version is 2.21.1. Is there a play for shure library?[/QUOTE]


XP?  Did you do what I suggested in the previous post?

---

### Post by Omnios on 2006-01-12
I think I tryed just about every how to to try to make it work except trying KDE. I had a problem in windows where the zen micro would not connect with media explorer, I went to the Creative site and downloaded the updates that installed Media Explorer for playforshure devices) and that worked in windows. I just bought my Zen yersterday so there may be something new for the ne players. Its also a HD based player wich maybe differnt from the flash players.

---

### Post by Omnios on 2006-01-12
I messaged KingBahamut about the links on the How to on this site being out of date and no longer available. Aperently they are looking into it and hopefully it may be updated.

---

### Post by BurningSnowman on 2006-01-13
[QUOTE=Omnios]K aperently the Zen Micro Media explorer does not work in XP, I needed to install the Zen Micro Media explorer (for Playforshure devices). This does work in XP. My firmware version is 2.21.1. Is there a play for shure library?[/QUOTE]
PlaysForSure is proprietary Microsoft DRM "technology", and I don't think there's a way for Linux applications to support it. You probably can't downgrade the player's firmware, and it sounds like the Micros now ship with Playsforsure firmware (which I think is any Zen firmware > 2.0).

Note the Micro entry under 'Working devices' on the Howto you linked to:
> -Creative Nomad Jukebox Zen Micro (Without the 2.x MTP/PlaysForSure upgrade!)
Unfortunately you appear to have this 2.x firmware version already installed, unless you actually 'upgraded' it yourself.

Sorry, but I don't think this will work. Consider it a 'MicrosoftLockInForSure' label. If I were to "upgrade" my Zen Nothing's firmware I would suffer the same fate, as I understand it. Creative are fairly friendly with Microsoft now.

---

### Post by Omnios on 2006-01-13
From the creative site. 

> Filename: ZenMicroPDE_PCFW_LB_1_11_01.exe

This web release enables you to upgrade the firmware for your 1, 4, 5 or 6GB Creative Zen Micro player, and provides Microsoft® Windows® XP Professional x64 Edition support for your player.

You can upgrade from Creative Zen Micro firmware 1.02.05 or earlier, or Zen Micro PlaysForSure™ firmware 2.00.12 or later. 

 So apperently you can downgrade though I have not tryed it as of yet. Not 100% shure if you can downgrade though thats what it seems to be saying

---

### Post by Omnios on 2006-01-13
K I used the other firmaware package "1.11.01" for my 6gig Zen Micro which I think is the latest non Playforshure firmware. Basicly it is the same as the playforsure but without the playforshure package. 1.11.01 is confirmed to work with the Ubuntu Gnomad2 packages. 

 Also im not 100% shure if the Zen Micro I bought two days ago came with the playforshure firmware or if it was installed when I installed the software that came with XP. Can someone please confirm this??????

---

### Post by extraspecialbitter on 2006-01-17
After installing libnjb and gnomad2 via Synaptic, I was able to get the program to work with my *Creative Zen Touch*, but only by executing the following at the command line:

[FONT="Courier New"]gksudo gnomad2[/FONT]

Via this kludge, I was able to transfer files from my hard drive to the player - or so I thought.  When I attempt to play music, most tracks - but not all - fail with the less-than-helpful message:

[FONT="Courier New"]Playback error.[/FONT]

I would like very much to overcome this issue, as it really is my last obstacle to a Micro$oft-free life...

---

### Post by Timn on 2008-02-15
Hi All,

The easiest way I found to get the Creative Zen to work is install Gnomand2, libnjb5 and libnjb1 via synaptic. From there all you have to do is plug in your Creative Zen then start Gnomad by going to Applications then Sound & Video then finally clicking on Gnomad 2 or you can go to the terminal and type sudo gnomad2. It should work from there.

---

