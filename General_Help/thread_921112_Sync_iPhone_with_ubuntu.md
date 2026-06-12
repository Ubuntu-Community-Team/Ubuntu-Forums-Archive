---
title: "Sync iPhone with ubuntu"
date: 2008-09-15
forum: General Help
---

### Post by Scypher on 2008-09-15
Ok, here is the big question. I am currently thinking about buying an iPhone. The only problem that I have is that I cant find any explanation on the internet on how to sync a Evolution Mail calendar and contacts with the iPhone.

If anyone can come to my help it would be great.

I dont mind changing my calendar to a Google calendar one if it's necessary but I would like to keep my contacts on Evolution or on Thunderbird as I dont mind using this other software if it can make my iPhone sync easier.


Sorry for my bad grammar and syntax, I am not a native English speaker.

---

### Post by arch0njw on 2008-09-16
At the moment, you cannot sync this.  It can sync with an Exchange server or with Apple's software.  I have even tried running iTunes in a VM with no luck.  The iPhone is mounted and "recognized" as a camera, but I cannot even get pictures off the device.

At this point, the iPhone is a brick as far as Ubuntu is concerned.  Sadly, it helps to partially justify having Windows on my work PC.

---

### Post by Scypher on 2008-09-16
So you mean that even if I use a VM like... virtualbox... I cant use my iphone to sync anything ?

---

### Post by arch0njw on 2008-09-16
Correct.  If there is a way, whoever has found out how to do it isn't sharing.  :-(

---

### Post by RedGreen on 2008-09-16
> **Scypher said:**
> Ok, here is the big question. I am currently thinking about buying an iPhone. The only problem that I have is that I cant find any explanation on the internet on how to sync a Evolution Mail calendar and contacts with the iPhone.

If anyone can come to my help it would be great.

I dont mind changing my calendar to a Google calendar one if it's necessary but I would like to keep my contacts on Evolution or on Thunderbird as I dont mind using this other software if it can make my iPhone sync easier.


Sorry for my bad grammar and syntax, I am not a native English speaker.

I setup a 2 way sync with my google calender and the iPhones. calendar using a free service provided by nuevasync.com they also will sync your contacts with your google contacts. Warning: syncing will erase iPhone calendar and contacts data, but once you've done that everything will work just fine

---

### Post by arch0njw on 2008-09-17
> **RedGreen said:**
> I setup a 2 way sync with my google calender and the iPhones. calendar using a free service provided by nuevasync.com they also will sync your contacts with your google contacts. Warning: syncing will erase iPhone calendar and contacts data, but once you've done that everything will work just fine

Right, but doesn't that sync over the air as apposed to a wired sync?  It's a very good option to know about though.

Aside:  the mutually exclusive contacts setup is the biggest gripe I have (aside from "doesn't work with Linux).  I submitted a FR about that, but I don't know what flavor of black hole Apple is when it comes to that.

---

### Post by RedGreen on 2008-09-17
> **arch0njw said:**
> Right, but doesn't that sync over the air as apposed to a wired sync?  It's a very good option to know about though.

Aside:  the mutually exclusive contacts setup is the biggest gripe I have (aside from "doesn't work with Linux).  I submitted a FR about that, but I don't know what flavor of black hole Apple is when it comes to that.

No. If you had actually looked at the first page of their website you would see in the first paragraph that it does support over the air sync.

"NuevaSync allows direct, over-the-air, native synchronization of certain smart phones and PDA devices with public PIM, and calendaring services including Google Calendar. NuevaSync does not need any software installed on your device because it uses synchronization protocols that are already built in."

I'f I make an edit to my calender on a computer then it shows up on my phone, if I make a change on my phone I can login to my google calender and see it there. No wired syncs required.

I highly recommend the service, and once I figure out a good way to get my contacts out of my phone and into my google contacts, then I will use their contact sync as well.

---

### Post by arch0njw on 2008-09-18
RedGreen:  Thanks for providing a "from the user's" point of view of NuevaSync.  I always appreciate the answers from that POV as apposed to the "what we say it *should* do" POV of the provider's site.  I'll definitely keep this in mind as an alternative to using an Exchange server.

BTW -- awesome scene from Firefly.

---

### Post by darksoul7 on 2008-09-19
I just got an iPhone and I'm pretty bummed I can't get my music on there while using Ubuntu. Ugh, another reason why I can't completely pull away from Windoze. 

Oh well, with all the gadgets the iPhone has, I guess I can deal with booting into Windoze once in a while :P

---

### Post by jack frost on 2008-10-01
> **RedGreen said:**
> I setup a 2 way sync with my google calender and the iPhones. calendar using a free service provided by nuevasync.com they also will sync your contacts with your google contacts. Warning: syncing will erase iPhone calendar and contacts data, but once you've done that everything will work just fine
When you say erase.. it just erases the data and not the calendar or contacts app itself.. just wanted to be sure
 
edit:
 
I went to their site and it appears there is a new config guide that shows how to set up so it doesn't delete the calendar and contact data already in the phone on the sync.
 
[http://nuevasync.blogspot.com/](http://nuevasync.blogspot.com/)

---

### Post by jack frost on 2008-10-08
If you have virtual box in ubuntu.. I did this and can sync now with itunes in xp vm....used this post:
 
 
*I was able to get my iPhone to sync. My setup:*
 
*Ubuntu 8.04 (Hardy Heron)*
*[[COLOR=#444444]VirtualBox 2.0.2[/COLOR]]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")*
*iPhone 3G (Software version 2.1)*
 
*I followed the steps mentioned in the thread on the virtualbox website*
 
*[[COLOR=#444444]http://www.virtualbox.org/ticket/491#comment:52[/COLOR]]("http://www.virtualbox.org/ticket/491#comment:52")*
 
*In particular, I did this:*
 
*[FONT=Courier New]sudo apt-get build-dep linux-source-2.6.24[/FONT]*
*[FONT=Courier New]sudo apt-get install linux-source-2.6.24 build-essential[/FONT]*
*[FONT=Courier New]tar -jxvf /usr/src/linux-source-2.6.24.tar.bz2[/FONT]*
*[FONT=Courier New]cd linux-source-2.6.24/drivers/usb/core[/FONT]*
*[FONT=Courier New]perl -pi.bak -e 's/16384/131072/' devio.c[/FONT]*
*[FONT=Courier New]make -C /lib/modules/`uname -r`/build/ M=`pwd` modules[/FONT]*
*[FONT=Courier New]strip --strip-debug usbcore.ko[/FONT]*
*[FONT=Courier New]sudo install -m644 -b usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core[/FONT]*
*[FONT=Courier New]sudo depmod -ae[/FONT]*
*[FONT=Courier New]sudo update-initramfs -u[/FONT]*
*[FONT=Courier New]sudo reboot[/FONT]*

---

### Post by arch0njw on 2008-10-09
> **jack frost said:**
> If you have virtual box in ubuntu.. I did this and can sync now with itunes in xp vm....used this post:
 
 
*I was able to get my iPhone to sync. My setup:*
 
*Ubuntu 8.04 (Hardy Heron)*
*[[COLOR=#444444]VirtualBox 2.0.2[/COLOR]]("http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb")*
*iPhone 3G (Software version 2.1)*
 


Fantastic!  I'll have to give this a try...

---

### Post by buck2825 on 2009-02-03
so i have a 3g iphone, dell D620 on 8.10 and a home brew server running desktop 8.04.2.  I have tried wine, and vmware virtual server running XP with no luck even if i had luck with vmware this is still windows.  yes a little more convenient but still a dual boot none the less.  Virtual box is also just another way to dual boot.  I want iphone sync on ubuntu. the official site gives this lam a$$ explanation of how to hack the iphone to "sync" it.  transferring songs is not a sync!!

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Syncing is the backing up of all user data and merging that data with the appropriate software, ie Thunderbird for email and so on.  come on people you wrote an entire OS, but can't transfer some files?!  I have read on a dead thread somewhere that the usb connection from the iphone to windows is a ssh tunnel.  

someone a few weeks ago broke into a national credit card system my wife and I had two cards compromised.  Is the iphone really harder to break then the systems that handle our way of life!! 

HELLO IS ANYONE OUT THERE!!!!!

---

### Post by buck2825 on 2009-04-07
Guess not!!!!

---

### Post by mb_webguy on 2009-04-07
You would get more responses if you created your own thread, rather than riding the coattails of another.  Most people who read this thread from the beginning would think, rightly, that the OP's question was answered, and stop reading.

The problem with connecting to an iPhone from Linux has nothing to do with Linux, and everything to do with the proprietary technologies involved with the iPhone, and Apple's lack of support for Linux.  The protocol Apple uses to connect to the iPhone is proprietary, and Apple won't release the specifications so that Linux developers can write an application to connect to an iPhone.  Until Apple either stops being so secretive or decides to support Linux, or Linux developers manage to reverse-engineer the protocol (which is extraordinarily difficult, especially since Apple periodically modifies it), iPhones will continue to be a problem for Linux users.

---

### Post by dannymichel on 2009-07-23
this is disappointing
such a powerful OS but...

---

### Post by Chronon on 2009-07-23
I would rather say about Apple's products: 
This is disappointing. . .
such pretty products, but such unnecessary proprietary lock in.

---

### Post by arch0njw on 2009-07-23
> **Chronon said:**
> I would rather say about Apple's products: 
This is disappointing. . .
such pretty products, but such unnecessary proprietary lock in.

I was just going to reply with something to that effect.

Apple *owns* the iPhone.
Apple *owns* the protocol to talk to the iPhone.
Apple *chooses* who and how the iPhone is accessed, not anyone else.
Apple doesn't like to play with the other kids apparently.

The fact that some developers have been able to hack the iPod protocol is great.  But that is no sign of "compatibility" because that implies cooperation from Apple -- which there was none.

The crazy thing is that they *could* provide a library, even a closed library, and just simply say "use this to talk to the iPhone".  They'd still have totalitarian control over the protocol, but they just apparently don't want to play.

---

### Post by CamT on 2009-07-23
In Jaunty I'm able to access full iPhone sync functionality using an XP virtual machine running under VirtualBox.  Google around for more information, but ultimately you're going to want to install the newest version of the non-open source VirtualBox and then allow it to write to USB devices.

---

### Post by dannymichel on 2009-07-26
> **CamT said:**
> In Jaunty I'm able to access full iPhone sync functionality using an XP virtual machine running under VirtualBox.  Google around for more information, but ultimately you're going to want to install the newest version of the non-open source VirtualBox and then allow it to write to USB devices.i think were all looking for a way to do this in linux rather than windows. using a virtual machine is never a linux solution.

---

### Post by Julolidine on 2009-07-30
> **dannymichel said:**
> i think were all looking for a way to do this in linux rather than windows. using a virtual machine is never a linux solution.


The linux solution is to not buy an iphone, because for the foreseeable future there won't be a way to do anything in linux with the iphone.

---

### Post by arch0njw on 2009-07-30
> **Julolidine said:**
> The linux solution is to not buy an iphone, because for the foreseeable future there won't be a way to do anything in linux with the iphone.

Bingo.  :-)

I find a lot of this i[Device] incompatibility annoying, but the bottom-line is that they never agreed to play nice with FOSS.  Their protocol is proprietary.  Until such time they want to play with the FOSS kids a pure Linux solution is going to happen only as a result of hacking.

---

### Post by ads2k2 on 2009-07-30
I got my iPod touch a year ago.  At the time I wasn't using linux full time.  Just kind of playing around occasionally.  Well, recently, I tried to start using jaunty for everything.  I had jailbroken my iPod etc.  Which has to be done in either windows or os x, at least when I attempted it.  Luckily I left my main machine dual-boot.  Then I tried the OTA syncing.  No luck, at all. :(  I couldn't get anything but gtkpod to mount, then, it wouldn't write the ipod db (for videos) properly...  So after about a week of fighting and a practically unusable ipod, I ended up having to reformat it and go back to syncing with iTunes.  I really love Jaunty, it's on all of my machines, but it's not my primary anymore on one machine (because my wife is afraid of it and refuses to let me show her how to do anything on it).  After this though, I think that Apple won't be on the new purchase list.  I'll go with something a little more FOSS friendly.  I spoke with a friend who works at Apple about it, and it boiled down to "iTunes was ported to Windows because it's a huge part of the market, it's not gonna get ported to Linux" citing Cocoa and Aqua being the primary problems...

---

### Post by brucewagner on 2010-01-28
See the very bottom of this page:  [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) 

**Alternative Options**

There are other ways to achieve similar results without the need to "jailbreak" the iPhone, and without any modifications to your systems. One way is to simply use the web browser of the iPhone, or other device, in conjunction with sophisticated new web-based services.

For one example of this, see the How To article entitled, "How to Wirelessly Synch an iPhone / iPod Touch / Android to Ubuntu / Mac / Windows / Any Browser":   [http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch](http://brucewagner.posterous.com/how-to-wirelessly-synch-an-iphone-ipod-touch)

---

### Post by winjeel on 2010-02-12
> **arch0njw said:**
> 
Apple *owns* the iPhone.
Apple *owns* the protocol to talk to the iPhone.
Apple *chooses* who and how the iPhone is accessed, not anyone else.
Apple doesn't like to play with the other kids apparently.
...

Apple made my iPhone, they don't own it anymore, I do. If they want me to own another one, they'd better start playing with the other children. I got my iPhone for a few reasons, one being able to travel with it. I got reassured on the Apple forums that my iPhone that I would (now 'did') buy in Japan would work overseas, including Australia. However, that's not the case. There's a lock on it, so it will only work in Japan, or with my Japanese carrier in Australia, making me pay exorbitant fees just to recieve text messages, e-mails, and calls I don't want to pay for. Grrrr

There are instructions here: [http://ubuntuforums.org/showthread.php?t=1355610&highlight=iphone+synch](http://ubuntuforums.org/showthread.php?t=1355610&highlight=iphone+synch) and they apparently work, though I haven't tried, yet.

---

### Post by kcreek33 on 2010-04-21
Good news for all those planning to upgrade to Ubuntu 10.04!

Support for iPhone/Touch is included automatically. :)  I have personally confirmed this as Rythmbox recognized and could play songs on my iPhone without any extra configuration.

Here is an article talking about some of the features: [http://www.osnews.com/story/22942/Ubuntu_10_04_To_Support_iPhone_iPod_Touch_]("http://www.osnews.com/story/22942/Ubuntu_10_04_To_Support_iPhone_iPod_Touch_")

---

### Post by dannymichel on 2010-04-21
horay for linux! im sure it doesnt know what a milestone this is for it

---

### Post by alnixx on 2010-06-23
If you update to iOS 4, Rhythmbox is no longer able to synchronize your musics with iphone. Nautilus is still able to access iphone folders and files. I don't know if Apple deliberately did this but it is very inconvenient. Any way around this?

---

### Post by dannymichel on 2010-06-23
devious bastards

---

### Post by alnixx on 2010-07-07
In my new Ubuntu installation, Rhythmbox v0.12.08 is able to synchronize with my iPhone OS4. I am not sure what was wrong with my previous installation.

---

