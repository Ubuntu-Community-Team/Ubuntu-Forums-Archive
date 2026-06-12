---
title: "Raspberry Pi 2 [RPi2]"
date: 2015-06-06
forum: Hardware
---

### Post by acedia2 on 2015-06-06
Just purchased a new piece of hardware[title^]. I got the newer model since quad core is pretty standard. I got it with noobs which is Debian based.  (I know, not ubuntu. I hope to get a ubuntu distro working soon though. This is a really recent purchase) 

Who else is using this piece of hardware, what did you install and how's it working out?

I plan to make it a 720p/1080p video media center also stream my music library and basic Web browsing. 

My final intentions are to make it  potable so I have my library while abroad and also be able to run basic video/music applications. 

Has anyone tried using a portable battery supply? Which wifi doggle worked best while abroad? 

My desktop computer currently is using 15.04 vivid vervet, I hope to run the device on something as polished but I also understand the scale back I will need to make since I only have 1gb of ram to play with. 

Thank for reading and if any of you personally use a rpi2 feel free to get in touch with me, even if you don't own one but intend too, I will for sure help you out getting started. This project of mine is for educational purposes and I'm more than willing to share how it works out for me.

Enjoy &#128522; [Please move this thread to the most appropriate place, I hope to demonstrate the RPi2's caplibilty using Ubuntu]

---

### Post by Bucky Ball on 2015-06-06
Have moved on to the Odroid now, but the RPi is great. Installed RaspBMC and used for what it sounds like you are intending to use it for. Worked a treat. Basically, RaspBMC is Xbmc for the RPi. Perfect media server.

Never used a battery;
If the wifi dongle works in one country it will work in another so doesn't matter about 'abroad';
You will not get a full-blown Ubuntu 15.04 on that dinky thing. Stick to the images that are available specifically for the RPi.

Sharing how it works for you and helping others is what this forum is all about. There are lots of people that use the RPi here so you will have no shortage of helpers in return. RPi also has a forum. 

Good luck and enjoy the fantastic little mite. ;)

PS: Just to confirm that you realise you will need an external USB hard drive if you want to have your entire media collection with you when you travel. There is not the room on the RPi for that kind of luggage, not by a long way. Think media server, not main storage device (the 2Tb hard drive you plug into it, of course, is the storage device).

The RPi is portable by nature. It is just like any other computer. You can take your laptop anywhere. No different with the Pi, just easier. Take it anywhere and plug it into a monitor when you get there. Done.

---

### Post by tgalati4 on 2015-06-06
I've used gel-cell batteries to power a Pi before but I would be concerned taking something like that through airport security.  Please tell us of your experiences with the final configuration that you settle on.

---

### Post by coldraven on 2015-06-07
I have just bought my third RPi2. The first one is just running a kiosk mode browser in a local museum, see my post here if you're interseted.
[http://ubuntuforums.org/showthread.php?t=2280089](http://ubuntuforums.org/showthread.php?t=2280089)

The second one I gave to a friend who only has 12 volt power in his house. It's running OpenElec with the Kodi media player. It's connected to his little 12V television composite video inputs but even so it works beautifully. I also bought a £5 IR remote control that worked out of the box. it even has a little mouse built in!
My friend is amazed that he now has thousands of channels of music and video.
[http://www.ebay.co.uk/itm/USB-Remote-Control-for-Raspberry-Pi-XBMC-Media-Centre-/131521842562?pt=LH_DefaultDomain_3&hash=item1e9f500d82](http://www.ebay.co.uk/itm/USB-Remote-Control-for-Raspberry-Pi-XBMC-Media-Centre-/131521842562?pt=LH_DefaultDomain_3&hash=item1e9f500d82)

The third one is sitting on my desk waiting to be connected up. I plan to use it for a media player and I'm going to try OSMC 
[https://osmc.tv/](https://osmc.tv/)
This RPi has a 16GB SD card. After burning the image it has a 268MB system partition and a 15GB storage partition. That should be enough for my media collection but it's easy to plug in more if needed.

---

### Post by acedia2 on 2015-06-07
Currently I am configuring the settings. I got a good power cable and wall adaptor (5.2volt-2.1amps) and have it on RPi2 overclock. Right now I am logging temperature how well it fuctions with my devices. I plan to get a 7ish inch display and camra model too. I have a few thumb drives with tons of storage but 16gb is fine for now. I need to do some math on how big of a battery bank I will need the setup inorder to make it portable. I am probably going to use plexy glass and velcro so I can swap and stick on things. Iceweasel seems to be the best functioning browser for my needs but there will need to be more testing done. I am already getting use to the terminal commands that Iuse regularly, its a pretty straight forward machine.

---

### Post by Bucky Ball on 2015-06-07
You might want to start [here]("http://www.fanjita.org/serendipity/archives/60-Running-a-Raspberry-Pi-from-batteries.html") re. batteries. There is a ton of information available re. running the RPi on batteries so you have plenty of source material to research.

---

### Post by acedia2 on 2015-06-07
I checked out your link above. 18650 cells are the best way to go. I have tons of them laying around after salvaging old laptop batteries. They work good in my e-cig. Anyways I plan have the screen and pi running from a board thats connected to the battery. This will help make sure it is getting the right power to each device and I should be able to use it while charging. I'm thinking of using it to take notes on since I got full libre office working. It's crazy the possibilities. I'm basically making a list of what to order off Amazon at the moment. I might even go with a 10.1 inch screen but the 7inch is touch enabled and "pi friendly" and uses less power so I still haven't decided. I want the encasing to show all the inner workings. Whether that's everything stuck to a board with velcro and the cables tied using zaps or build a proper enclosure, I still have to get all the component and get it working before I decide how to enclose it all. I looked at the 3D printed Pi-top but that is too cookie cutter, I want to make something myself.

---

### Post by Bucky Ball on 2015-06-07
You can order the RPi in a plastic case which is clear. You can see everything. That is what I ordered when I got mine. You should find them on the [RPi site]("http://au.element14.com/multicomp/mc-rp002-clr/raspberry-pi-b-enclosure-abs-clear/dp/2426744") (the link is to an Australian site and I have the RPi B so case slightly different to the one pictured).

---

### Post by The Cog on 2015-06-07
My PI model B is running a chat server (mumble) and print server for our USB printer.
My Pi Model B2 is attached to our TV for watching streaming videos.

---

