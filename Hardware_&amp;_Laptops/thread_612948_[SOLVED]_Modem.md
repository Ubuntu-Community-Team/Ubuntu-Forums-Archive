---
title: "[SOLVED] Modem???"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by diwas on 2007-11-14
Let me be straight forward to what iam facing with.
i used live cd feature of ubuntu 7.10, everything was all right except the modem. I have dial up internet and no alternative. I looked at the device manager it shows my modem(company name, etc)...i tired to configure it in Networks...i did and selected Modem connection, but still in the notification area "no network device has been found" is notified. 
please help me out guys...im a rookie at linux.
thank you

---

### Post by l2thet on 2007-11-14
I havent tried to do anything with modems in Linux, but I can understand why its giving you that error, as your not connected to a network with it.  

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

That should give you all the info you need to get your modem dialing out and connecting.

---

### Post by Bartender on 2007-11-14
diwas -
Read my ongoing dial-up thread
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

You have to change some things in Ubuntu, like making the /etc/resolv.conf file.  I've tried setting up a dial-up connection from the LiveCD, and it didn't work, which kind of makes sense if you think about it.  The exact same steps did work when Ubuntu was installed to a HDD.

I was able to dial out with Mint Linux Bianca, a KDE-based distro, from a LiveCD.  I'm not exactly sure why that was so.  

The first thing you have to do to actually trouble-shoot your own dial-up situation (figure out whether your modem is compatible and whether your ISP will cooperate) is install Ubuntu to a HDD.  It'd be good if you have an old spare HDD laying around so you don't take a chance with your Windows install.

---

### Post by diwas on 2007-11-15
Thanks a lot for ur help. I checked in the post earlier too...but i was too much confused abt it. I have just entered the world of linux...never mind i used to say the same thing 2 mnths before...i left linux juss because of this modem problem. but i will check it out..install ubuntu in my HDD.
well can u tell me where the dial option comes in ubuntu 7.10? like u have connect to in windows. 
thank you.

---

### Post by Bartender on 2007-11-15
diwas -
Do you have access to broadband at work or school or wherever?  

What I'm getting at is, can you download an entire distro someplace else to a thumb drive, then bring it home, burn it, and install it?

That's my situation - I'm stuck with dial-up at home but can borrow broadband at another location.

If dial-up is #1 on your priority list, and you can borrow some broadband, and your heart's not absolutely set on using Ubuntu, I'd suggest getting your hands on a copy of Kubuntu instead.  That's what I'm gonna do for right now.  The only reason I suggest this is because it appears that KPPP works better than GNOME-PPP.

According to Duncan, GNOME-PPP is acting flaky in Ubuntu 7.10.  He suggested using KPPP.  I just tried yesterday without success to install KPPP from a Kubuntu CD by adding the CD to the Ubuntu sources list.  It shoulda worked but didn't.  The Kubuntu CD was recognized, and according to Synaptic it was added to the list of Third-Party sources, but when I went back to Synaptic and typed in "KPPP" it just kept pulling a blank.  If I could figure out what I'm doing wrong as far as making Synaptic utilize the Kubuntu CD I'd probly just install the entire kubuntu-desktop package to Ubuntu :cool:

EDIT:  You ask where the dial-up option comes in.  It's sort of the same as the Windows dialer but not.  You start up pppconfig, or wvdial, or GNOME-PPP, or KPPP, and tell the program to dial.  Unless you're carefully watching the log, you don't even know you're online until you click on Opera or Firefox or Thunderbird or go back to Synaptic Package Manager and ask it to "Reload".

---

### Post by diwas on 2007-11-17
No dude...i dont have a broadband connection anywhere...damn its too remote out here...so only dial up is here...(thankfully). 
Hey of u dont mind...can u tell me How to dial...plz dont mind...im completly new to linux and i have a very deep windos background...which is very bad...( which i have realized it now!).
hey yeah...there is smthg more...in one of the forums..i saw dat for PCTEL modem some kernel stuff is to be downgraded...i have a Hsp56 PCTEL modem...56K so do i have to do dat?

---

### Post by Bartender on 2007-11-18
Hi, diwas -

No broadband at all, anywhere?  Damn.

Pretty much everything I've learned about dial-up is in that thread.  It's sort of my online dial-up diary, graciously hosted by the Ubuntu Forums.   :)

If I were to try and describe a dial-up troubleshooting procedure as briefly as possible, it'd go something like this.

#1 Buy an external hardware US Robotics modem (5686 model, 56K, the black ones are the newest) at a garage sale, ebay, craigslist, wherever you can find one.  Make sure the #3, 5, and 8 dipswitches on the back are in the "down" position.  If your PC doesn't have a serial port, buy the Sabrent adapter cable described in my thread.   
(Note: there are internal modems that work, but I don't know anything about them and it seems like the drivers crash after Linux updates)
There are other hardware externals out there, such as the Amigo (Newegg) but I only have experience with the USR's.
First problem taken care of - now you have the modem situation in hand.  If you plug the modem into the first serial port, it'll be at /dev/ttys0.  With the Sabrent adapter it'll be different of course, as described in diary.

#2 Make sure your ISP is Linux-friendly.  If they're not, dump 'em.  Juno, PeoplePC, AOL, etc. aren't Linux-friendly.  BasicISP, Copper.net, US Netizen are a few U.S. ISP's that work just fine with Linux - there are many more.
Second problem resolved - now you have a cooperative ISP waiting to serve you.

#3 Start with pppconfig.  I think most of us who are accustomed to the glossy Windows world are prejudiced against a primitive-looking interface like pppconfig's.  But you know what?  It works, it's stable, and it's fast.  (thank you, duncan)  Just be careful when you're entering the values.  As I mentioned earlier, it's easy to set it to Manual DNS by mistake.  Once pppconfig is set up properly, it doesn't get much easier than opening a terminal and typing "pon" to get on, "plog" to see a basic log, then "poff" to disconnect.

#4 Once you've seen the PC connect you may want an "easier" way to dial.  Get offline, create the /etc/resolv.conf file, then go back online and get GNOME-PPP or import it from a Windows PC as described in my diary.  Apparently it's a little flaky in 7.10 but it worked for me so worth a try.  Configuring GNOME-PPP is pretty straightforward.

I'm trying very hard to decide whether to recommend Kubuntu or Ubuntu to someone who doesn't have any access to broadband at all.  A couple of days ago it was Kubuntu, but Kubuntu doesn't have GIMP or Firefox in the default install and I've never had any luck getting online with Konqueror.  If you had Kubuntu you could download mozilla-firefox from the repositories.  That shouldn't take more than an afternoon :(  
Downloading GIMP, however, would be a massive undertaking.

I think I'm leaning towards Ubuntu again.  One complaint I have against Ubuntu's default install is lack of a good CD/DVD burning utility, but was happily surprised to find out that braseros is not a huge download.  Downloaded/installed it on dial-up in a half-hour or so.  

Dial-up just sucks.

---

### Post by diwas on 2007-11-18
Thank you man...but i live in nepal...so there is not much of modem's option here. i guess i have to work offline now. there is simply no way dat i can use internet through ubuntu. damn.
By the way thanks a lot for helpin me out. but its too frustratin now. 
Hey yeah...just one last favor..can u provide me some link for a mp3 codec...so dat i can play mp3 songs in linux. yeah...plz gimme a package which wont have any dependency problem. Ur help will be appreciable.
Thanks a lot again.

---

### Post by Bartender on 2007-11-19
diwas -
You live in Nepal?  Wow

I would love to see that part of the world some day.

Having said that, my sympathies go out to you.  From what I've seen and read on these forums, I could multiply my dial-up frustrations by by ten to get some idea of your situation.  

With a little patience and some scrounging, I can find cheap used external modems.  With a decent external the hardware part is solved.  Different countries have different dialing rules too, don't they?  I mean, would a US Robotics modem intended for the North American market even work in Nepal without having to tweak everything?
I can buy a brand-new Amigo serial external on Newegg for about $20.  UPS will bring it to my door.  Do you have any online retailers and a delivery infrastructure?

There are at least a hundred ISP's with local access numbers ready to take my money and let me use their network, so there's plenty of competition.  How many ISP's are available to you?

I'm not trying to make you feel bad and I hope I don't sound condescending.  I'm just curious to hear about your obstacles.  It doesn't help you one bit to say things like "pick up a USR modem on eBay" if you can't do that.  I'd like to be able to give you something that actually helped.

Regarding mp3's, I haven't looked into that at all.  I could check into what's available as a package.

Would it be impossible to send a CD or DVD to Nepal?  I was thinking of the full Mint KDE package if you have a DVD drive.  Mint is supposed to come with all the multimedia stuff already included.  What you need is a distro that's as complete as possible out of the box.

---

### Post by diwas on 2007-11-19
Yeah i dont think there are same dialin rules all over the globe(but not sure though..hehe). I guess i have more to see the world since its been juss 17 years i was born...
But hey im learnin everytime.
I wish i was there in some Western countries...where u have WiFi, broadband like..like toilets in each house(i couldnt think of any other thing!!! lol).
Yeah we have DHL. I ddnt download Ubuntu too...i ordered it...so i guess canonical company has a link to here.
Hey i have a DVD RW drive...so can u send me the DVD in anyway?? but before sendin me tell me the price...as i cannot afford too much amt of money for delivery...
Hey by the way...if u dont mind can u gimme ur yahoo or/and hotmail id...so dat i can have personal talks abt linux...but its completly okay if ur not into PMs...

Oh yeah 1 thing more...i think my modem is supported coz in the hardware profiles my modem is clearly shown...

---

### Post by swudee on 2007-11-19
Hi Diwas

Hey Nepal. Thats cool
Anyway to help you we will need to know what modem you are using.
Internal, PCI or external USB?
Try opening a terminal window and typing  lspci  That may identify it, or try opening the computer and identify the modem type or the IC number on the largest chip.
Until a year ago I was using dial up as well. I still have one machine at work that I use on dial up,
Still on 7.04 until I find drivers for 7.10

Regards  David

---

### Post by Bartender on 2007-11-20
diwas -
I'll PM you.  I'm certainly not going to charge you money for a couple of CD's or DVD's.  
Sounds like DHL might be the best way to send them to you?

swudee, what's the modem you're using?

---

### Post by diwas on 2007-11-20
Hey Im usin PCI modem. Its HSP56 PCTel Modem...need anythin more?

---

### Post by diwas on 2007-11-20
If u cud send me DVDs and all...i'd really appreciate it. Thanks...

---

### Post by swudee on 2007-11-21
Hi Diwas

Sorry working late these days.
It looks like Linux support for PCTel modems is fairly limited. Some people got it working on Ubuntu up to the 2.15 kernel. I am using an Intel 536 chipset. Philippe Vouters maintains the driver for this. For Feisty it is a deb file that can easily installed. He has just started working on the Gutsy version, Some people have had some success using the Feisty version, but Phillipe expects to have the driver ready in a week or two, so maybe it is better to wait.
You can find the thread here [http://ubuntuforums.org/showthread.php?t=471503](http://ubuntuforums.org/showthread.php?t=471503)

Also have a look here if you can find another modem.  [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
It may be a month or so before people update it for Gutsy. I used to wait a few months before upgrading to give time for the how to to be updated:)
They were planning to work toward dialup modems for Gutsy, but I am not sure how far they got, maybe in Hardy

Good luck

David

---

### Post by Bartender on 2007-11-21
I wish I knew more about the Linux OS.  I don't understand why serial modems just keep working whether you're using Breezy or Dapper or Feisty or Gutsy, whereas drivers like those for the Intel 536 become useless after an update.

The Dell Conexant drivers are the same.  The Dell modems stopped working when people upgraded to 7.10.

There were plans to develop better winmodem support in 7.10, but it didn't happen.  

$60 to send a small package to Kathmandu Nepal from Chehalis Washington.  Sheesh

---

### Post by diwas on 2007-11-21
But But...wat abt PCTel?? guys...am I neva able to use my modem in Linux??? gosh.....

---

### Post by swudee on 2007-11-22
Hi Diwas

Yes I think it probably does.
I will have another look around on the weekend for you if I have time.
In the mean time you can have a look at [http://www.linmodems.org](http://www.linmodems.org) and try their scanModem tool. Follow the instructions to unzip and make the file executable.
Note the Capital M in scanModem!
I imagine exchanging a modem might not be easy in Nepal?
Shame my wife came back from Thailand this week. I am sure it would have been cheaper to send things from there.
Bartender,If you read that link, you will find explanations about the difference between serial modems and Winmodems.

David

---

### Post by diwas on 2007-11-22
Today i installed Ubuntu 7.1 permanently in my system wid dual boot XP. I also installed gnome ppp dialer or smthg like dat..its easy to use...it has an option sayin scan modem...here everythin goes wrong...it says there is no modem detected. but in the hardware profiles...my modem is shown.
Another thing...in my modem drivers cd...there is a separate folder for linux...and a .doc file sayin everythin... it says:

Make a Node for the modem (only one time)
If you don&#8217;t already have a File Manager window open with path file:/root,
launch it by clicking on the Home icon on the task bar. Click on the &#8220;File&#8221; menu
on the title bar.  From the drop down list, select Open Terminal to open a working
terminal.  This will open another window.  
In the terminal window, type the following.  Make sure you type everything as it appears below. This will make a node for the modem, give access to everyone and make a link between that mode and /dev/modem. Linux is case sensitive.  This is done only once after a fresh installation of the OS.

	mknod  /dev/ttyS15  c  62  79 
	chgrp uucp  /dev/ttyS15
	chmod 666  /dev/ttyS15
	ln &#8211;s  /dev/ttyS15  /dev/modem

I did accordingly...and yeah it worked...now the next step was:

Load and unload PCTEL Linux driver
For loading, run installation script by typing  &#8220;chmod  777  install_oasis_beta&#8221; and followed by &#8220;./install_oasis_beta&#8221;
For unloading, please type &#8220;rmmod  ptserial; sleep 1s; rmmod pctel&#8221; 

now here everythin goes wrong..this is the final step i supose...but on enterin this "load modem driver command", it says no file found(ie of install_oasis_beta) wats the problem now??
Everytime its one step closer but...smthg has to be the obstacle!! LOL hehe

---

### Post by swudee on 2007-11-23
OK you found some modem drivers.

I found this site  

[http://www.linuxquestions.org/questions/linux-hardware-18/pctel-hsp-modem-not-working-in-man9-or-man10-292512/](http://www.linuxquestions.org/questions/linux-hardware-18/pctel-hsp-modem-not-working-in-man9-or-man10-292512/)

One post says "Its actually a stupid winmodem and the drivers, as far as I know support only 2.4 kernels. Works well with 2.4 kernels though."

That is what I had seen previously.
Gutsy uses a 2.6 kernel

There seem to be a number of different devices labeled as HSP56, can you run the command

lspci -d 134d: -n

I found a PCTel modem that gives me this output, maybe its the same as your?
Anyway we will need that to find the right driver. you can have a look here too.

[http://xmodem.org/chipsets/pctel/pctel_1789.html](http://xmodem.org/chipsets/pctel/pctel_1789.html)

David
02:0c.0 0703: 134d:7891 (rev 02)

---

### Post by diwas on 2007-11-24
Yes i had checked in some sites it said dat i have to change the kernel version or smthg like dat...but doin this i think there will be problems wid other features of the OS.

But i will check the sites...

Sorry for replyin late...i had to go out of valley for 2 days!!

---

### Post by swudee on 2007-11-25
No problem

If you have the same modem as I have here I can try to get it going here and tell you what I find.

David

---

### Post by diwas on 2007-11-25
Ok here is the specimen of my MODEM.
HSP56 Micromodem...PCTel.
PCT1688W
Internal Modem.

Anythin more u need???? Plz feel free to ask.

I wanna thank u for replyin me...u guys are really helpful for me.Thank u again.

---

### Post by swudee on 2007-11-27
Hi

I had a look around on the weekend, it doesn't look very promising. The links I found were very old and mostly gone. I Haven't found much for the chipset you said. Mostly Windows users looking for drivers. It seems PCTel sold there end user modem business to Conexant and just make the chipsets now.
I have one other idea. I will get back to you in a day or two

David

---

### Post by diwas on 2007-11-27
Hmmm...they are really irresponsible..
okay...tell me if u've found anythin...but plz be in contact..

---

### Post by madjr on 2007-12-22
> **Bartender said:**
> diwas -
Do you have access to broadband at work or school or wherever?  

What I'm getting at is, can you download an entire distro someplace else to a thumb drive, then bring it home, burn it, and install it?

That's my situation - I'm stuck with dial-up at home but can borrow broadband at another location.

If dial-up is #1 on your priority list, and you can borrow some broadband, and your heart's not absolutely set on using Ubuntu, I'd suggest getting your hands on a copy of Kubuntu instead.  That's what I'm gonna do for right now.  The only reason I suggest this is because it appears that KPPP works better than GNOME-PPP.

According to Duncan, GNOME-PPP is acting flaky in Ubuntu 7.10.  He suggested using KPPP.  I just tried yesterday without success to install KPPP from a Kubuntu CD by adding the CD to the Ubuntu sources list.  It shoulda worked but didn't.  The Kubuntu CD was recognized, and according to Synaptic it was added to the list of Third-Party sources, but when I went back to Synaptic and typed in "KPPP" it just kept pulling a blank.  If I could figure out what I'm doing wrong as far as making Synaptic utilize the Kubuntu CD I'd probly just install the entire kubuntu-desktop package to Ubuntu :cool:

EDIT:  You ask where the dial-up option comes in.  It's sort of the same as the Windows dialer but not.  You start up pppconfig, or wvdial, or GNOME-PPP, or KPPP, and tell the program to dial.  Unless you're carefully watching the log, you don't even know you're online until you click on Opera or Firefox or Thunderbird or go back to Synaptic Package Manager and ask it to "Reload".

install gnome-ppp patched:
[http://launchpadlibrarian.net/106924....24-1_i386.deb](http://launchpadlibrarian.net/106924....24-1_i386.deb)

bug report for patch found here:
[https://bugs.launchpad.net/ubuntu/+s...pp/+bug/121487](https://bugs.launchpad.net/ubuntu/+s...pp/+bug/121487)

---

