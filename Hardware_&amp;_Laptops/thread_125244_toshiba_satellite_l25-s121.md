---
title: "toshiba satellite l25-s121"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by mikey on 2006-02-03
as indicated in the wiki, this laptop has a video problem at install. can anyone help me overcome this and get this laptop running graphically.the card is an ati radeon xpress 200m series.

---

### Post by Kiran on 2006-02-04
I have a similar problem, with a Toshiba Satellite 1800  100.  I tried to load ubuntu from the live disk.  The screen wallpaper appeared, but no icons.  A friend who is knowledgeable with Linux tried various commands to correct it, but no use.

It has a celeron 700 (?) MHz chip, 128 MB Ram -- don't know other hardware details.  I checked on Toshiba sites (linux-laptop.net) plus laptopz.ca, but haven't isolated the problem.  I noticed several references that the software modem won't work with Linux, but I am using an ethernet card.

I also hope to use the KDE environment--I used it before with Red Hat.  I wonder if there are any significant differences in compatibility between ubuntu and kubuntu?

I posted on the "Installation and Upgrades Help" forum, but no solutions offered there yet.  There are also some other requests for help with laptops there.

Thanks, anyone who can offer advice.  I really want to get out from under Bill Gates' thumb.:confused:

---

### Post by stangbang on 2006-02-04
Mikey,
can you give a little more detail as to what it is doing. is there no video during the install process, is the video not readable??? also a link to the wiki you are refering to might help.

Kiran,
You might try installing ubuntu or kubuntu on your system. Some times the live cd's dont run everything like a full install would. also the main differences in gnome and kde is that gnome uses gtk and is programed in c while kde uses qt and is programed in c++. You can still run all the same application in both as long as you have all the dependancys. There is also the option of installing both if you are not sure what one will work best for you. ("sudo apt-get install ubuntu-desktop" from kubuntu, "sudo apt-get install kubuntu-desktop" from ubuntu)

---

### Post by Kiran on 2006-02-05
Thanks Stangbang:

Think I'll try partitioning, installing Kubuntu & keeping my windows for now.

:)

---

### Post by mikey on 2006-02-06
Dear kiran and stangbang
haven't had a chance to formally respond with as much info as the community deserves so I thought I would just for the moment send off a note which briefly indicates what I did.
it might have been from an earlier thread, maybe it was stangbang that advised using dpkg. to reconfig the peripherals:that is, the monitor keyboard and mouse. I did that and I also began fooling around with the flgrx, I believe, driver to replace the ati one. lo and behold, the ubuntu start up screen booted up nicely. the only downside I've notice is that pdf's in evince are not visually crisp and are therfore not very readable. I don't know if that's a problem inherent to evince or its just that this ati 200x drive is just not happening. 
this laptop is functioning now. I did get the atheros wifi card up too . I just have problems playing online streaming audio and video which I don't on my other laptop p3 thinkpad running pro mepis. I will in a bit get back to this thread and try to post a more thorough explanation of what I did but I think stangbang is more capable and knowledgeable than I regarding that need.
best to all and  this community and the general community of linux users is what the net should be about. the future of civilized world, I truly think, depends on it. as an aside, kiran you might try puppy linux. I was able to run it live but could not get wifi going. it is truly a great intro to linux and is very easy to get up and running in no time

---

### Post by Kiran on 2006-02-10
Good News!  Re my Toshiba Satellite 1800--My friend was available again today and this time he had a live CD for Kubuntu (which was the one I really wanted).  Previously we had tried Ubuntu and the wallpaper showed up, but no icons to work with.  Today we tried the Kubuntu live disk and it seemed to work OK so we cleaned out the hard drive and loaded Kubuntu.  It worked.  So now I am learning how to use it and make it serve my needs.

So far I haven't figured how to get access to the Kingston stick memory which has all my old files.  But it's early in the game.

Thanks for helpful advice Stangbang & Mikey.
:-D

---

### Post by mikey on 2006-02-11
DEAR KIRAN
great news . was that a breezy ver. of kubuntu? I wonder why that installed and not ubuntu. maybe someone with real insider knowhow will comment. 
I've had good results with ubuntu recognizing pendrives etc so I'm confident you'll be able to get your old files in.
you could also burn your files to a cd and get them in that way which is not bad since you'd have a permanent backup of your stuff.
best mike

---

