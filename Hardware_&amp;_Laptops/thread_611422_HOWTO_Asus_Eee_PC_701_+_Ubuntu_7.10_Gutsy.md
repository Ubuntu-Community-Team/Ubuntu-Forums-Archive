---
title: "HOWTO: Asus Eee PC 701 + Ubuntu 7.10 Gutsy"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by rapido on 2007-11-12
Following are notes to install Ubuntu 7.10 Gutsy on an Asus Eee PC.  These notes and scripts are derived from: [http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)

The initial os install can be performed in quite a number of different ways.  There are choices to be made with respect to installation media, drive partitioning schemes, file system types, and even the location of the resultant os components.  Each of those choices comes with pros and cons. 

The outline below is simply based upon my choices and attempts to reduce writes to the flash drive.  For the time being, I will be using Ext2 for a filesystem, among other tricks.  This comes at a price in that the file system is subject to potential data loss during power failure ( and other catastrophes ).  I am willing to take this risk as the limitation of the eee's internal storage will likely dictate that I am keeping little of value on it in the first place.  

I may change this approach as I learn more about the volume of writes that a journaling filesystem requires.  If you feel more comfortable using a filesystem like Ext3, by all means, just substitute it at the appropriate place in this guide.

This guide now includes the new, interactive post-installer.  This script will handle most post-installation fixes.


GUTSY INSTALL

* Load the Ubuntu 7.10 Alternate CD into a USB external CD/DVD drive ( connected to the eee of course )

* Upon boot, enter into the BIOS ( F2 ) and change the boot order.  F2 > Boot > Boot Device Priority
  1st Boot Device [ATAPI CD-ROM]
  2nd Boot Device [HDD: SM-SILICONMOTI]

* I have also changed the boot messaging from terse/splash screen to verbose. F2 > Boot > Boot Settings Configuration
  Quick Boot [DISABLED]
  Quiet Boot [DISABLED]

* Save changes and boot using the Ubuntu CD

* Install in text mode

* Partition method: manual
  - Delete all existing partitions
  - Create one partition consuming the entire disc with the following specs:
    Use as: Ext2 file system
    Format the partition: yes, format it
    Mount point: /
    Mount options: noatime
    Bootable flag: on
  - Continue without defining a swap space

* Don't select any X screen resolutions

* Complete the install

* Reboot to the internal drive ( remove the USB external CD/DVD drive )

* Login

* Gutsy should come up with Compiz, max screen resolution ( 800x480 ) and functional ethernet


GUTSY POST-INSTALL

* Fetch this help guide and unpack it.
  $ wget [http://www.shiftingheat.com/packages/ubuntu/eee_gutsy_install.tar](http://www.shiftingheat.com/packages/ubuntu/eee_gutsy_install.tar)
  $ tar -xvf eee_gutsy_install.tar

* Run the new, interactive post-installer.  This script will selectively perform the following steps:
  Upgrade the os, reduce logging ( writes to the drive ), install wireless, repair suspend/resume/powerdown,
  and configure the microphone.
  $ cd eee_gutsy_install
  $ ./post_install.sh

---

### Post by PartisanEntity on 2007-11-13
Thanks for the HowTo! One question, why use Ext2? Why not Ext3?

---

### Post by Straylit Me on 2007-11-13
Ahh ive been waiting for someone to write this. I just ordered my Eee yesterday and am very excited for it to arrive. I do have a few statements and questions, though.

1) How fast does it boot Ubuntu as compared to Xandros?
2) Why were the quick/quiet boots disabled?
3) What benefits did you obtain by using Ext2 instead of Ext3? As i understand it, 3 is simply 2 with journaling.
4) What exactly does the noatime boot parameter do?
5) Do to the 800mhz processor and 512ram, wouldnt it be a better idea to use, say, Fluxbuntu, Xubuntu, or Gutsy Barebones?
6) And lastly, do you notice any bugs or other negative effects of using *buntu on the Eee?

---

### Post by VitaminBB on 2007-11-13
Anyone have this loaded on an EEE?

A few earlier questions really stood out ..

[b]- What is the load time with ubuntu on the EEE ?

- Why use Ext2 and not Ext3?[/b]

Fluxbuntu sounds perfect for this, though I suspect regular Ubuntu would work fine on the EEE

So who has their Asus EEE loaded with Ubuntu ?

---

### Post by VitaminBB on 2007-11-14
Heres a video of bootup  ...

[http://www.youtube.com/watch?v=-9G012o8ENI](http://www.youtube.com/watch?v=-9G012o8ENI)

---

### Post by Joners on 2007-11-14
To answer a couple of the questions that were listed here. (im from the eeeuser forums, however not associated in them in any professional manor)

1. - Ext2 was used due to the reduced write cycles that it places on the SSD, there were some initial concerns that continual writing to the drive could wear them out, as they have a finite life cycle. However at this point no one is going to be able to tell until these things have been out on the open market for a a good space of time.

2. - Boot time varies. Using the default Xandros OS that is on the system it takes approximately 20-30 seconds to boot from cold, however this is in to the 'easy' mode, time taken if the system is altered to boot in to the 'advanced mode' is approx another 5 seconds or so.

Seems that most installs with ubuntu have been relatively free of worry however 

a. You still have to use ndiswrapper to get the wifi working, then it works fine

b. Issues with the battery monitor, ubuntu seems to think that the battery is bad, and wont hold a charge. However the battery is fine and works properly.

c. Suspend mode doesn't work, think that this has now been resolved.

Thats pretty much it.

I know that people really would like a customized version of ubuntu created so that they wouldn't have to go though any of these issue to get the OS on the system.

---

### Post by clevin on 2007-11-14
what are the differences in the guide if i neen to install it to a SD card without any impacts on original system?

thanks

---

### Post by VitaminBB on 2007-11-14
Has Asus shown any intention to make the laptop easier to setup for other OS? (besides Xandros and Windows XP).

---

### Post by clevin on 2007-11-15
asus is now in hogs heaven, they probably will first make sure their official repo is properly maintained before worrying about other distroes.

---

### Post by moephan on 2007-11-17
I've mentioned this on another thread, but thought I'd say it again. I have Ubuntu set up on my eee this way, and it works flawlessly. Boot up time, etc... is fine. I can only tell it's a slower machine when sometimes switching between apps is a little slow. I have my RoR web site set up on it, so I can do web programming on the bus, works great. After enabling the camera in the bios and then installing a program called "cheese" even the web cam works flawlessly.

I have had this machine for a week, and I am still incredibly impressed.

Cheers, Rick

---

### Post by dunkgreen on 2007-11-18
> **rapido said:**
> Following are notes to install Ubuntu 7.10 Gutsy on an Asus Eee PC. ...

Thank you!  This worked very well.  The only thing I have to add is that not plugging in the network plug before the installation caused me some grief.

Regards,

Bill D-G

---

### Post by mendieta on 2007-11-18
> **moephan said:**
> I've mentioned this on another thread, but thought I'd say it again. I have Ubuntu set up on my eee this way, and it works flawlessly. Boot up time, etc... is fine. I can only tell it's a slower machine when sometimes switching between apps is a little slow. I have my RoR web site set up on it, so I can do web programming on the bus, works great. After enabling the camera in the bios and then installing a program called "cheese" even the web cam works flawlessly.

I have had this machine for a week, and I am still incredibly impressed.


This is fantastic news Rick! How about the screen resolution ? This is the only thing holding me back. I know it's a bargain, but  ... does it bother you for RoR development ? It seems not ;) How about web surfing ? I guess there is **no way to increase resolution** a bit, right ? I read in newegg someone saying that this can be done with a "driver update", but I doubt it ...

Cheers ! And kudos to Asus !

---

### Post by rapido on 2007-11-18
Recently I thought I would give the external vga a try.  Upon boot, the external monitor was recognized and the screen resolution was automatically adjusted to 1280x1024 to match that of my test lcd.  Not only did it look great, but even "normal" Compiz visual affects were still driven quite well.

This is one way to get a higher screen res.  

> **mendieta said:**
> This is fantastic news Rick! How about the screen resolution ? This is the only thing holding me back. I know it's a bargain, but  ... does it bother you for RoR development ? It seems not ;) How about web surfing ? I guess there is **no way to increase resolution** a bit, right ? I read in newegg someone saying that this can be done with a "driver update", but I doubt it ...

Cheers ! And kudos to Asus !

---

### Post by mendieta on 2007-11-18
Gracias Rapido!

> **rapido said:**
> 
This is one way to get a higher screen res.

That's a great idea, especially if you already have a spare flat monitor around.

Otherwise, I guess the answer is no (increasing the resolution on the 7" monitor). It's a shame they couldn't get a slightly larger monitor with a bit more resolution. At least 800x600, maybe 960 x 600 or so. 

Anyways, how about you, does the low resolution bother you at all ?

Cheers !

---

### Post by PartisanEntity on 2007-11-19
Thanks for the news and feedback. Some stores have started selling the ASUS Eee PC 701 4G here in Austria, so far the cheapest offer I have seen is &#8364;302. I am very tempted to get one.

---

### Post by moephan on 2007-11-21
In response to questins about RoR development on the eee pc:

Keep in mind that I use this on the bus for about 25 minutes at a time, not extended usage. I use my three normal tools, terminal window, gedit and Firefox with firebug installed. All of this works fine on the small screen. The only thing I wish for now is some kind of menu in gedit where I can pick all of the methods in a file from a list. This is because scrolling through the limited vertical space can make it hard to find the right place in a long file.

I use it for web browsing around the house all the time now. In fact, I hardly touch my other laptop now. Web browsing is fine. I use F11 and hide the nav bar in FF. That's it. I also use Thunderbird for mail, and that works fine as well. The size and lack of heat makes it better for casual surfing. I also think I am saving a ton of electricity compared to my old laptop.

Cheers, Rick

---

### Post by mendieta on 2007-11-21
Thank you Moephan! The info is greatly appreciated, very detailed and useful. I'll grab one, they are selling a "surf" version in the US, for USD 350, which is getting into the "this is a joke" price dept. AFAICT, it's only missing the webcam, and I can live without it. It's a small enough investment that I won't mind the limited screen, which is my only concern. 

BTW, for anyone living in the States, if you heard of any Black Friday Eee deal, please spread the word! I think I can wait two more days ;-)

Cheers !

---

### Post by imabuddha on 2007-11-21
The surf version also has a smaller capacity battery, 4400mAh vs. 5200mAh, giving a rated time of 2.8 hrs vs. 3.5 hrs.  That's not much of a difference, but that plus the webcam were worth the $50 to me.  While the webcam quality isn't great, it does work well with the latest skype beta.  With a notebook this tiny you can easily carry it around to show the other person different locations, etc.

So far I haven't heard of any black Friday deals on the eee, and since it is still selling out quickly I doubt we'll see any.  Although there's the good deal on the dell vostro 1k, and a super cheap notebook deal at best buy, I'm happy with the eee!

---

### Post by mendieta on 2007-11-21
> **imabuddha said:**
> The surf version also has a smaller capacity battery, 4400mAh vs. 5200mAh, giving a rated time of 2.8 hrs vs. 3.5 hrs.  That's not much of a difference, but that plus the webcam were worth the $50 to me.  While the webcam quality isn't great, it does work well with the latest skype beta.  With a notebook this tiny you can easily carry it around to show the other person different locations, etc.

Yeah, you're probably right. The other difference is that you can't upgrade the memory. I just found this article after posting, and I was going to link it here:

[http://www.dailytech.com/Newegg+ZipZoomFly+Get+Onboard+With+350+ASUS+Eee+PC+4G+Surf/article9749.htm](http://www.dailytech.com/Newegg+ZipZoomFly+Get+Onboard+With+350+ASUS+Eee+PC+4G+Surf/article9749.htm)

I'm still not sure, but I'll get one or the other. Thanks for the info !

---

### Post by imabuddha on 2007-11-26
BTW, Asus have released the source for the acpi module, so now the fn keys should be able to work: [ftp://ftp.asus.com/pub/ASUS/EeePC/701/ASUS_ACPI_071126.rar](ftp://ftp.asus.com/pub/ASUS/EeePC/701/ASUS_ACPI_071126.rar)

---

### Post by Longhorn Engineer on 2007-11-27
How would one go about using that source code to get the FN keys to work? I have exhausted google and I still can't figure it out.

---

### Post by imabuddha on 2007-11-27
I haven't installed ubuntu on my eee yet, but here's a post on the eeeuser forums with some info about the asus eee acpi: [http://forum.eeeuser.com/viewtopic.php?pid=32677#p32677](http://forum.eeeuser.com/viewtopic.php?pid=32677#p32677)

BTW, I highly recommend eeeuser.com's forums & wiki for eee users.

---

### Post by yochaigal on 2007-11-27
Let me just say:

So far I've gotten ubuntu to work almost flawlessly on the eeepc 701 4G with one exception: hibernate mode.  I believe this has something to do with swap space.  Anyone found a solution?

By the way, the guides (and the scripts!) have been incredible!

thanks

---

### Post by yochaigal on 2007-11-27
And one more thing: 

This is not so much a problem, but does anyone know how to make windows maximize automatically in gnome?  

Thanks

---

### Post by mendieta on 2007-11-27
This is great news (module source). In the meantime, I decided to **vote with my wallet and buy one** (the white 701, I decided it was worth the extra 50 over the surf). I'll keep Xandros until there is an easy way to install a fully working Kubuntu without tinkering. I wonder if it would be possible in the future to make a "live SD" .. can you boot from the external card ? Anyone knows ?

Cheers!

---

### Post by jfernyhough on 2007-11-28
Yes, you should be able to make a "Live SD" in the same way as a Live USB, the process should be exactly the same (if you use a USB card reader).

---

### Post by Longhorn Engineer on 2007-11-28
Ok I figured out how the acpi module works and I coded the mute/volume buttons

link here [http://forum.eeeuser.com/viewtopic.php?id=3573](http://forum.eeeuser.com/viewtopic.php?id=3573)

I am going to install the original OS on an external harddrive and pull some of the files I need to get the wireless and F5-F6 keys working.

On the Xandros Os the file in etc/acpi/events capture the scan codes and send them to a script called etc/acpi/hotkeys.sh

Hotkeys.sh then calls abunch of other scripts like /proc/acpi/asus/wlan.sh and /proc/acpi/asus/disp, Also with theres another program called asusosd that is bundled with that asus_acpi download. Compiled it and ran it in terminal. It seems to run along side of asus_acpi and it calls functions like

/usr/local/share/asus_osd/wlanoff.png
/usr/local/share/asus_osd/lcd.png
ect....

To get them completely working you will need everything from the Xandros OS that is located in /etc/acpi/, /etc/acpi/events/, /proc/acpi/asus/, and /usr/local/share/asus_osd/. Then have both asus_acpi and asusosd running. 

Once I get a copy of Xandros working again I can copy erm and see it it truly works.

If anyone out there still has there Xandros working on the EEE can yah send me those directories?

---

### Post by mendieta on 2007-11-28
> **Longhorn Engineer said:**
> Ok I figured out how the acpi module works and I coded the mute/volume buttons


Awesome!

> 
If anyone out there still has there Xandros working on the EEE can yah send me those directories?

I'm getting mine this Thursday, I can hopefully send you this stuff over the weekend, please post a reminder if I forget. I'll need an email address, you can send me a private msg.

Thanks for the great work, cheers !

---

### Post by Longhorn Engineer on 2007-11-28
pm sent

---

### Post by hottyson on 2007-11-29
First of all THANK YOU RAPIDO very much for the help. Your contribution to the eee pc Ubuntu install is very helpful to us.
> **rapido said:**
> 
GUTSY POST-INSTALL

* Fetch this help guide and unpack it.
  $ wget [http://www.shiftingheat.com/packages/ubuntu/eee_gutsy_install.tar](http://www.shiftingheat.com/packages/ubuntu/eee_gutsy_install.tar)
  $ tar -xvf eee_gutsy_install.tar

* Run the new, interactive post-installer.  This script will selectively perform the following steps:
  Upgrade the os, reduce logging ( writes to the drive ), install wireless, repair suspend/resume/powerdown,
  and configure the microphone.
  $ cd eee_gutsy_install
  $ ./post_install.sh

I tried the above directions after my live cd graphical install and it didn't work. So... I just copied all the text from each one and pasted into Terminal. Then I rebooted and my wireless seems to work now. [COLOR="Red"]**How do I go about checking to see if the other items worked/installed?**[/COLOR] Help is greatly appreciated.
:)   Thanks

---

### Post by Longhorn Engineer on 2007-11-29
You can check it my manually going to each file it altered. Theres a wiki at eeeuser.com that shows how to install Ubuntu on the eee and which files to edit.

---

### Post by rapido on 2007-11-29
The other key visible patches ( other than wireless ) provided by the interactive installer are suspend/resume/powerdown and the microphone.  Simply test those items.  If they now function properly, the interactive installer did its job.

If you want to know that files were modified towards patching those items, you could view a few key files that were changed or see if a backup was produced.  Most of the installation steps will back up the configuration files prior to modification in case you would like to revert.  They are backed up with a timestamp representing the time the installer ran.

suspend/resume/powerdown
/etc/default/acpi-support and /etc/init.d/halt
microphone
/etc/modprobe.d/alsa-base


> **hottyson said:**
> First of all THANK YOU RAPIDO very much for the help. Your contribution to the eee pc Ubuntu install is very helpful to us.


I tried the above directions after my live cd graphical install and it didn't work. So... I just copied all the text from each one and pasted into Terminal. Then I rebooted and my wireless seems to work now. [COLOR="Red"]**How do I go about checking to see if the other items worked/installed?**[/COLOR] Help is greatly appreciated.
:)   Thanks

---

### Post by mendieta on 2007-11-30
Guys, I thought I should briefly post to say I got mine and I am loving it. Thanks to all who gave me excellent info t make the decision. The screen could have been made a bit larger, with some more resolution. All the area around it looks a bit ugly, and there is a bit of waste. This is the only thing I'd improve. Otherwise, it looks terrific, and it's so simple to use. I got mine, unpacked, and we were watching internet tv 10 minutes later (yes, this includes unpacking and assembling). Amazing gadget.

---

### Post by jlapier on 2007-11-30
> **moephan said:**
> The only thing I wish for now is some kind of menu in gedit where I can pick all of the methods in a file from a list. This is because scrolling through the limited vertical space can make it hard to find the right place in a long file.


You mean the [[COLOR="Blue"]class browser plugin for gedit[/COLOR]]("http://www.stambouliote.de/projects/gedit_plugins.html")?

Hearing someone is actually getting a little RoR work done on this is pushing me to get one. I really just want it for portable word processor and web surfing, but occasional hacking (or system administration via ssh) would really make it handy.

BTW, if you haven't seen this before, here's a good article on [[COLOR="Blue"]plugins for gedit that will help with RoR[/COLOR]]("http://grigio.org/textmate_gedit_few_steps") development (note that this article was pre-gutsy, so any references to gtksourceview-1.0 should be changed to 2.0).

- Jason

---

### Post by moephan on 2007-11-30
> **jlapier said:**
> You mean the [[COLOR="Blue"]class browser plugin for gedit[/COLOR]]("http://www.stambouliote.de/projects/gedit_plugins.html")?

BTW, if you haven't seen this before, here's a good article on [[COLOR="Blue"]plugins for gedit that will help with RoR[/COLOR]]("http://grigio.org/textmate_gedit_few_steps") development (note that this article was pre-gutsy, so any references to gtksourceview-1.0 should be changed to 2.0).

- Jason

Thanks for the tips Jason. I'll check out the class browser plugin and see how it works on the small screen. 

I was thinking maybe I could figure out how to add a menu to the menu bar that when pulled down, each menu item is a method in the file. 

> 
Hearing someone is actually getting a little RoR work done on this is pushing me to get one. I really just want it for portable word processor and web surfing, but occasional hacking (or system administration via ssh) would really make it handy.


I spent a few commutes this week using OO Writer to write a help document. That went fine. The one thing that I have been finding frustrating is taking screenshots and cropping images. It all works, but the screen is small enough that it can be a little tough to get the crops just the size I want them. HTH

Cheers, Rick

---

### Post by Duffy on 2007-12-01
> **Joners said:**
> To answer a couple of the questions that were listed here. (im from the eeeuser forums, however not associated in them in any professional manor)

1. - Ext2 was used due to the reduced write cycles that it places on the SSD, there were some initial concerns that continual writing to the drive could wear them out, as they have a finite life cycle. However at this point no one is going to be able to tell until these things have been out on the open market for a a good space of time.

I know that people really would like a customized version of ubuntu created so that they wouldn't have to go though any of these issue to get the OS on the system.

Huh, since when does solid state memory have a finite life cycle? You seem to indicate that the more you write to the memory in the Eee, that it will wear out? I've never heard of such a thing.

---

### Post by imabuddha on 2007-12-01
He's not talking about the main memory (RAM), but about the SSD which uses flash memory.  Modern flash memory still has a limited number of write cycles, but except for some unusual usage scenarios this shouldn't be  a problem.  

I'm using ext3 myself, and the stock Asus/xandros install does use ext3 on the user data partition.

---

### Post by imabuddha on 2007-12-01
BTW, Atheros has released a Madwifi patch, so ndiswrapper is no longer needed!

See [this page]("http://wiki.eeeuser.com/ubuntu#wireless_internet_using_native_madwifi_drivers") for info.  :D

---

### Post by uzd4ce on 2007-12-01
Sorry if (since) this is a dumb question, but I went through the steps to set up the madwifi driver, and everything seemed fine, but how can I tell if it really worked?

I un-blacklisted ath_pci, but after the reboot, when I look at the connection properties in NetworkManager, it still shows Ndiswrapper as the driver.

Do I also have to disable ndiswrapper separately?

Thanks

---

### Post by Longhorn Engineer on 2007-12-01
Yes you have to uninstall ndiswrapper


OK!! 

With the madwifi patch I now have a working Wireless on off key!

All that I have to work on is the F6 key which is supposed to open the System manager. I can get it to open the system manger once but it won't open again till I reboot. It is not the key because I have tested it with other functions

My code to open the system manager is below.

/bin/su parker -c "gnome-system-monitor"

Is that correct?

---

### Post by Mateo on 2007-12-01
isn't Ubuntu a bit slower to boot?  I saw a video on YouTube and it seemed to take much longer than the default OS.

---

### Post by starbase1 on 2007-12-02
Hi All, I got my eee on Friday Evening and I am very impressed with all aspects of it - I was particularly impressed with the general feel and build quality. And the price! Also nice to see it play vid files and MP3 straight from the box. In fact in makes a very handy portable video player...

The size is great and I have no problems typing on it - though I am a 2 fingered typist so those who do it properly may have a different experience! My only gripe is that I find the touchpad VERY fiddly, so I am learning keyboard short cuts fast!

Of course though, I want to get Ubuntu onto it, but have not got a wireless connection available, (plus it does not seem to work when I plug in a LAN cable).

So has anyone saved off a pre-configured Ubuntu for eee, which I could download as a torrent or something, and put onto an SD card or USB drive to boot from?

For those asking about more res on the display, I think this may refer to screen driver tricks which down sample the web page, to fit more on screen at a time... 

Personally I am also very interested to see the XP version come out - I think this will really put the microsoft tax clearly on display, and make people wonder what they get for this!

Nick

---

### Post by imabuddha on 2007-12-03
> **Mateo said:**
> isn't Ubuntu a bit slower to boot?  I saw a video on YouTube and it seemed to take much longer than the default OS.

Yes, Asus & xandros put a lot of effort into making the factory installed OS boot quickly.  However, the trade-off is that not all of the normal linux/unix services are started.  For example, you can't use more than 1 user account on the eee. :|

Even though the eee's power consumption in suspend mode is high, most of the time during a working day you can keep it running, occasionally plugging in or suspending, so you shouldn't have to reboot very often.

---

### Post by Bezdomny on 2007-12-03
Just a few points from reading the posts here...

Some of the windows in gnome won't maximise properly therefore you need to use the ALT + CLICK + DRAG method to get at the buttons.  One slight problem here, if you are running compiz you can't drag it up.  There seems to be a ceiling limit.  I have removed compiz and have gone back to plain old metacity and although the boot time is the same the speed has significantly increased when going from GDM to desktop.

I have tried changing the Atheros card for the more supported intel ipw3945 and there is no joy there. Asus seemed to have locked the bios and the card isn't recognised.  My wasted time at :o :

**[eeebuntu]("http://www.eeebuntu.org/viewtopic.php?t=2")**

I did try to patch madwifi and although the card was recognised I just couldn't get it to connect.  In the end I regressed back to ndiswrapper. I'll try again with the latest source.

starbase1: If by no wireless available you mean that your wireless doesn't work then try downloading the XP drivers to your SD from another PC.  Install ndiswrapper from the Alternate Install CD and install the XP drivers.  Then your connection should be up and running over wireless. It's strange that your wired network card hasn't been recognised. How did you install Ubuntu?

---

### Post by bluedragon436 on 2007-12-03
You know I have been looking at the EEEand would really love to purchase one, but am going to wait a bit in hopes that they can get one out with a CD drive...even if it is only a CD not a DVD drive they could do a slim one with just a slot instead of an actual drawer....but that is just me, and that is the only thing holding me back as of right now....I love the size though....I might just have to suck it up and deal without the drive though....we will have to see what the next series of EEE's has to offer.....  and what the reviews are from our fellow EEE Ubuntu users....

---

### Post by starbase1 on 2007-12-03
> **bluedragon436 said:**
> You know I have been looking at the EEEand would really love to purchase one, but am going to wait a bit in hopes that they can get one out with a CD drive...even if it is only a CD not a DVD drive they could do a slim one with just a slot instead of an actual drawer....but that is just me, and that is the only thing holding me back as of right now....I love the size though....I might just have to suck it up and deal without the drive though....we will have to see what the next series of EEE's has to offer.....  and what the reviews are from our fellow EEE Ubuntu users....

I've not got Ubuntu onto mine yet, but I am seriously impressed with it so far. (2 days in).

The build quality was a major nice surprise, particularly given the price. Obviously given the size, the keyboard is a little cramped, but as a 2 fingered typist I found it very easy to adjust to, though those who do it properly may have problems.

The 3 USB ports make it a doddle to stick extra stuff onto it, (including CD Rom drives if you wish...) it plays MP3's and loads of video / dvd formats out of the box, the screen is nice and bright, w-ifi detection seems to work very nicely...

The only I really don't like is the touch pad, which I find very fiddly indeed. But I bunged a USB mouse on, and it worked instantly.

But the best bits are definitely the size and the price. I'm really hoping that someone will knock up an Ubuntu download that works directly with it for the command line challenged like me.

I think I can honestly say it's the first computer that has me excited since I bought my first Atari ST. A looooong time ago!

Nick

---

### Post by Bezdomny on 2007-12-04
Actually, I don't think there is room to put in a cd/dvd even a slot drive into the EEE.  It's pretty packed in there having seen the insides after ripping mine to pieces to change the wifi (link to photos of the naked eee on my previous post in this thread).  You could pick up a USB2.0 slim DVDRW from ebay (mainly from hong kong) for around 30 GBP (40 ish euro). The drive takes power from the USB but continuous use on batteries will flatten them a lot quicker. Though I would recommend you get one.  Alternatively, copy the stuff you need to the SD.  The EEE can use the high capacity SD cards so you can quite happily run with 8GB. 

All in all I would recommend the EEE to anyone that doesn't need the speed and flexibility of a full blown notebook.  I travel a lot, Manchester to Moscow (connecting flights and messing around) and it's a lot lighter to carry and less fiddly to mess around with when you're crammed in your seat. Videos and Music sit on the SD, plug in the headphones and the flight time just disappears.  Even beyond the two finger typists :-) you get used to the keyboard. I wouldn't use it to write code but for writing up specifications and formalising my notes it's pretty good.  One thing I would recommend is that you get the 2GB RAM upgrade, openoffice can be memory intensive, especially if you have a few things open.  To fit the RAM means breaking the warranty void seals though, unless you know an approved man who can ;-)

If you've got the cash, get one. You won't regret it.  Though, if you're on a long journey you will probably need a spare battery. My Manchester to Moscow trip is two flights, 1.5hrs to some airport in western europe then 3-4 hrs to moscow, the battery on the EEE lasts around 3 hrs to 3.5 hrs at a push. 

Steve.

---

### Post by starbase1 on 2007-12-04
> **Bezdomny said:**
> Actually, I don't think there is room to put in a cd/dvd even a slot drive into the EEE.  It's pretty packed in there having seen the insides after ripping mine to pieces to change the wifi (link to photos of the naked eee on my previous post in this thread).  You could pick up a USB2.0 slim DVDRW from ebay (mainly from hong kong) for around 30 GBP (40 ish euro). The drive takes power from the USB but continuous use on batteries will flatten them a lot quicker. Though I would recommend you get one.  Alternatively, copy the stuff you need to the SD.  The EEE can use the high capacity SD cards so you can quite happily run with 8GB. 

All in all I would recommend the EEE to anyone that doesn't need the speed and flexibility of a full blown notebook.  I travel a lot, Manchester to Moscow (connecting flights and messing around) and it's a lot lighter to carry and less fiddly to mess around with when you're crammed in your seat. Videos and Music sit on the SD, plug in the headphones and the flight time just disappears.  Even beyond the two finger typists :-) you get used to the keyboard. I wouldn't use it to write code but for writing up specifications and formalising my notes it's pretty good.  One thing I would recommend is that you get the 2GB RAM upgrade, openoffice can be memory intensive, especially if you have a few things open.  To fit the RAM means breaking the warranty void seals though, unless you know an approved man who can ;-)

If you've got the cash, get one. You won't regret it.  Though, if you're on a long journey you will probably need a spare battery. My Manchester to Moscow trip is two flights, 1.5hrs to some airport in western europe then 3-4 hrs to moscow, the battery on the EEE lasts around 3 hrs to 3.5 hrs at a push. 

Steve.

As you say, superbly portable. I love mine! I think it's a mistake to get one if you are looking for a powerful machine though. It's cut down to make it very portable, and that's reasonable.

But according to the eee forums, Asus are now saying the will honour guarantees if you upgrade the memory.

Nick

---

### Post by mendieta on 2007-12-04
Guys, hope someone can help. 

I am trying to open apps, such as KMail, from my Kubuntu desktop into my eee, using ssh. Essentially, I do "xhost +" in the eee (still running Xandros), and I ssh into my Kubuntu box. But the DISPLAY environment is set up for the Desktop, not for the eee. Shouldn't ssh automatically set this to the eee X Server ? It used to work like this in Mandriva ...

Thanks for any help, I am LOVING my eee (not only me, everyone in my family)!

---

### Post by mendieta on 2007-12-04
> **mendieta said:**
> 
I am trying to open apps, such as KMail, from my Kubuntu desktop into my eee, using ssh. Essentially, I do "xhost +" in the eee (still running Xandros), and I ssh into my Kubuntu box. But the DISPLAY environment is set up for the Desktop, not for the eee. Shouldn't ssh automatically set this to the eee X Server ? It used to work like this in Mandriva ...


Ok, I did some research. This is X forwarding. It's not working ! Using -X when invoking ssh should activate it, and set $DISPLAY to myEeeIp:0, but it's not. Even if I set up the environment manually, I get an error message that the display can't be opened, despite having run xhost +. Oh well ! Any hints will be appreciated, I couldn't find anything in a search in eeeuser.com

---

### Post by tristan on 2007-12-06
> **rapido said:**
> Following are notes to install Ubuntu 7.10 Gutsy on an Asus Eee PC.  These notes and scripts are derived from: [http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)

Rapido, thanks very much for this script, which pretty much worked perfectly for me (I manually ran each of the scripts). I now have a perfectly functioning Eee/buntu system.

Madwifi recently released a patch so that their drivers work properly to allow true native wifi on the Eee without the need for ndiswrapper. I compiled it in manually myself, but is there any chance of including the compiled modules in your scripts instead of ndiswrapper for others who want a simple way to convert to Eee/buntu?

---

### Post by mahousaru on 2007-12-06
Many thanks for the script, I used it as a guide to set up my own as I wanted to use the native wifi drivers but it was really helpful none the less.

Anyone figured out how to get past the xv issue for skype?  I tried using the xorg.conf from the wiki and the xandros intel_drv.so, but all I got was that my mplayer etc all crashed when i tried to play on xv mode :(, oh and skype video didn't work.

I think I might restore xandros and have it quick boot for skyping on the move and keep ubunu on a usb hdd and slow boot to that if i want to do some real work...

---

### Post by rapido on 2007-12-07
> **tristan said:**
> Madwifi recently released a patch so that their drivers work properly to allow true native wifi on the Eee without the need for ndiswrapper. I compiled it in manually myself, but is there any chance of including the compiled modules in your scripts instead of ndiswrapper for others who want a simple way to convert to Eee/buntu?

Thanks for the tip and the suggestion.  I have updated the wireless_install.sh script to include a madwifi install.  The wireless installer is now interactive.  It prompts the user with a choice of madwifi or ndiswrapper.  During the install of the user's choice ( madwifi or ndiswrapper ), the installer will revert the alternate choice ( ndiswrapper or madwifi respectively ).  i.e., one can always switch between wireless choices.

This updated wireless_install.sh can be run independently, or as part of the larger interactive installer, post_install.sh.

---

### Post by jsully1 on 2007-12-07
I'd just like to chime in and say that there should be absolutely *no* concern regarding the write life of the EEE's SSD.  The EEE uses a 4GB NAND solid state drive.  High end NAND flash has a life of between 1 and 5 million write cycles.  Assuming the Asus EEE's drive is at the low end of 1 million writes, you're going to need to write roughly 4 **PetaBytes** to the drive before it dies.  Thanks to hardware write leveling, if you somehow managed to pump 25MBps into the drive 24 hours a day, it would take you over 5 years to get there.

---

### Post by imabuddha on 2007-12-07
I agree that there shouldn't be any great concern about the eee's SSD write life.  However, the flash chips used in it have a far lower life than 1 million writes.  I don't recall the exact #, but I think it's 100k min. write cycles.  Someone on the eeeuser.com forums found the spec for the chips.  Search there if you want the exact info.

Couldn't find the post with the link to the chip manufacturer, but did find this: [http://forum.eeeuser.com/viewtopic.php?pid=24843#p24843](http://forum.eeeuser.com/viewtopic.php?pid=24843#p24843)

---

### Post by mahousaru on 2007-12-07
> **jsully1 said:**
> I'd just like to chime in and say that there should be absolutely *no* concern regarding the write life of the EEE's SSD.  The EEE uses a 4GB NAND solid state drive.  High end NAND flash has a life of between 1 and 5 million write cycles.  Assuming the Asus EEE's drive is at the low end of 1 million writes, you're going to need to write roughly 4 **PetaBytes** to the drive before it dies.  Thanks to hardware write leveling, if you somehow managed to pump 25MBps into the drive 24 hours a day, it would take you over 5 years to get there.

The really cheap pci-e mini slot has been dropped from my poor little thing, me thinks that the flash is not going to be high end :)

Would be nice if we could get a manufacturers spec from the chips themselves.

---

### Post by imabuddha on 2007-12-08
> **mahousaru said:**
> Would be nice if we could get a manufacturers spec from the chips themselves.
A recent post on the eeeuser pointed me to the link for the spec from the manufacturer of the flash chips (Samsung).  They are indeed rated for 100,000 write cycles.  See page 3 of: [http://www.samsung.com/global/system/business/semiconductor/product/2007/6/11/NANDFlash/SLC_LargeBlock/8Gbit/K9F8G08U0M/ds_k9f8g08x0m_rev10.pdf](http://www.samsung.com/global/system/business/semiconductor/product/2007/6/11/NANDFlash/SLC_LargeBlock/8Gbit/K9F8G08U0M/ds_k9f8g08x0m_rev10.pdf)

---

### Post by mahousaru on 2007-12-08
Nice find

A lot less then 1 mil ;)  I am glad that I went for a more anal write approach.

ext2 for all flash drives with noatime

tmpfs for:

var/log
var/lock
var/run
var/tmp
tmp
firefox cache

Can anyone think of anything else please?

For Big Jobs (TM) I have a usb hdd with a swap file on it.  I only plan on using this when I don't need to move and have a power supply.

My apt/cache is on this drive, so I need to plug it in to update

---

### Post by mendieta on 2007-12-08
> **imabuddha said:**
> A recent post on the eeeuser pointed me to the link for the spec from the manufacturer of the flash chips (Samsung).  They are indeed rated for 100,000 write cycles.  See page 3 of: [http://www.samsung.com/global/system/business/semiconductor/product/2007/6/11/NANDFlash/SLC_LargeBlock/8Gbit/K9F8G08U0M/ds_k9f8g08x0m_rev10.pdf](http://www.samsung.com/global/system/business/semiconductor/product/2007/6/11/NANDFlash/SLC_LargeBlock/8Gbit/K9F8G08U0M/ds_k9f8g08x0m_rev10.pdf)

This is probably one more reason to put Ubuntu in the external SD, and keep the default Xandros in the internal one. At least that's what I'll do. I like this approach:

[http://wiki.eeeuser.com/installonsd](http://wiki.eeeuser.com/installonsd)

You use a bootable USB Key, and install to the external SD Card.

Cheers!

---

### Post by imabuddha on 2007-12-09
Someone has posted new pics of the eee's mb on eeeuser, and in that machine flash chips from intel are used.  No word yet of their write cycle rating.

I guess if you plan on using your eee for many years then being conservative about writes is good.  Personally, I like using ext3 (data integrity is more important than hw longevity), and running the OS from the SSD which is much faster than SDHC.  I do have an SDHC for extra storage, and will use tmpfs for the dirs mahousaru listed.

Honestly, 100k writes to the same physical location on a chip with wear-levelling will take a long time to occur.  As others have written, these flash chips also contain a few % spare blocks to utilize when needed to replace those that have failed.  After all the spares are used the available disk space will shrink.  Thus a heavily-written SSD won't just suddenly stop working.

---

### Post by mahousaru on 2007-12-09
I've been thinking about the maths behind wear levelling.  When people do their guestimates do they do it for the full drive size or for the amount of space they have left?

Personally I'm caching my files to the SD card (ext3 now)  and accessing everything else via the internet.  

I've disabled thumbnailing and moved .thumbnails to tmpfs so that I can still use gThumb.  I've also disabled Recent documents as I can remember what I've accessed last :p]

I tried to get ubuntu onto the sd card but it isn't easily achieved with full disk encryption, it kept complaining that it couldn't find the luks partition even though it was using uuid and not /dev/ notation.  I am carrying all my ssh keys, cisco confs and other stuff on my little baby so encryption is a must.

---

### Post by starbase1 on 2007-12-10
I'm hoping that someone will knock up a nicely tweaked and optimised Ubuntu version for the eee, so that the more challenged users like myself can let rip!

I'm really enjoying the eee though, even as supplied!

Nick

---

### Post by tristan on 2007-12-10
> **rapido said:**
> Thanks for the tip and the suggestion.  I have updated the wireless_install.sh script to include a madwifi install.  The wireless installer is now interactive.  It prompts the user with a choice of madwifi or ndiswrapper.  During the install of the user's choice ( madwifi or ndiswrapper ), the installer will revert the alternate choice ( ndiswrapper or madwifi respectively ).  i.e., one can always switch between wireless choices.

This updated wireless_install.sh can be run independently, or as part of the larger interactive installer, post_install.sh.

No worries! I tried the v0.4 script on a fresh xubuntu install and it worked like a charm.

---

### Post by jjacobs2 on 2007-12-12
I noticed there's an eee ubuntu support package offered at google code.  Has anyone tried this?  Does it provide any additional functionality?
[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

---

### Post by violajack on 2007-12-12
The package from google code comes from here:
[http://forum.eeeuser.com/viewtopic.php?id=4066&p=1](http://forum.eeeuser.com/viewtopic.php?id=4066&p=1)
It adds a lot of functionality - function keys working, overclocking, native wifi.

There is now an easy image for getting xubuntu onto the eee here:
[http://forum.eeeuser.com/viewtopic.php?id=5005](http://forum.eeeuser.com/viewtopic.php?id=5005)
This image inludes native wifi and the desktop is well setup for the smaller screen.  It does not include the function keys however.

---

### Post by Jack78 on 2007-12-15
My eee should be in in 3 days time :) I will probably end up installing Ubuntu on it. This [eeeXubuntu]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home") looks interesting too, I might try it.

---

### Post by jakson84 on 2007-12-15
Hi,
Can anyone help me how to Install Ubuntu 7.10 properly. Nothing comes after loading. I get CPU frequency scaling not supported as error. And also **AIGLX: Screen 0 is not DRI capable as error**. I tried sudo **dpkg-reconfigure xserver-xorg **and set the appropriate values. But i can see my gnome is running. I get half my background in the display and the remaining half i get 2 ubuntu logo which is 4 bit colour.

I have AMD Semphron and Samsung 17 inch monitor.

 Some one please help me i need it very urgently. Thanks.

---

### Post by mendieta on 2007-12-15
> **Jack78 said:**
> My eee should be in in 3 days time :) I will probably end up installing Ubuntu on it. This [eeeXubuntu]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home") looks interesting too, I might try it.

Yeah, I think they got it right: they made a liveCD that you can boot in your main computer, and you can make from there a USB bootable pendrive running a script.

Also, they went for the lightest *buntu. What I'd do is to install kubuntu-desktop on top. Now, the question is: I'm thinking of installing in an SDHC card (so I can keep the default Xandros in the SSD) /. Someone in this thread made the point that reading/writting is a lot slower from the SDHC. Anyone knows how much slower it is ? I don't have an sdhc yet. I'd love to know what numbers you get from hdparm.

This is what I get for the ssd:

```

eeepc:/root> hdparm -tT /dev/sda1
/dev/sda1:
 Timing cached reads:   610 MB in  2.00 seconds = 304.37 MB/sec
 Timing buffered disk reads:   70 MB in  3.07 seconds =  22.77 MB/sec

```

Cheers!

---

### Post by IanW on 2007-12-16
The instructions on [PendriveLinux]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") worked for me. (Posting this from my Ubuntu-driven EeePC).

---

### Post by markp1989 on 2007-12-17
excelent, i brought one of these a few days ago and will be trying this soon!!  thankyou!

---

### Post by markp1989 on 2007-12-17
thankyou, the script worked perfectly, i am using it now, took me less than an hour to set up, i love me eee

---

### Post by Muttley99 on 2007-12-18
I bought mu eee PC about two weeks ago and have found it to be great value for money and so easy to use but after installing Ubuntu (Gutsy) on to the thing it has given me headaches! :(
When i first installed Ubuntu and the drivers and tweaks all worked well, my wifi was ok and I was happy but, the next morning i turned on the thing and no wifi!
after spending a good five hours trying to get the wifi back I gave up and reinstalled Gutsy and ran V0.7 of the patch program with the wrapper rather than the atheros linux driver and still no wifi :oops:
Anyone kind enough to list some troubleshooting tips here would be most welcome [-o<
By the way the router is configured correctly with no filtering and i have a blue light for the wireless so it has to be the pc?
TIA

---

### Post by Muttley99 on 2007-12-18
Finally got wifi up after multiple attempts installing, only problems seem to be the WPA key missing on start-up so i have to keep typing it in at each boot. Any ideas?
Can anyone recommend a good wifi strength indicator for Ubuntu? 
Thanks to the guy who put the hard work into the patch program, great work and well done!!

---

### Post by Muttley99 on 2007-12-20
Given up on Ubuntu! Too many problems;

Wifi it temperamental, sometimes working, sometimes not.
PC will not mount devices from the USB ports - I fixed it but took me a few hours of messing.
Wifi WPA key sometimes disappears from the list and has to be typed back in. (about 1 in every 5 boots)

I may install Xubuntu as i've heard its more compatible with the eee, otherwise i'll put the original Xandros back on from the DVD.

---

### Post by w116tjb on 2007-12-20
I've been toying around with the idea of buying one of these for awhile now. I would love to use it as an ultra portable pentesting laptop.

Concerning the updated Madwifi drivers... Does Kismet or aircrack-ng function at all with the wifi card? I know neither program will run using NDISWrapper, so it was a big relief to me when Atheros posted the update.

Thanks for any info.

---

### Post by Muttley99 on 2007-12-21
Definitely worth the expense, cost me £220 ($400), but i think we pay more for it here in the UK! I bought a 15" laptop last year for over a £1,000 and I'm selling that now I have the eee PC. The Xandros install is great and all you'll need. As you can see, i lost patience with Ubuntu especially the WiFi connection but have installed Netapplet and have found (up to now) the WiFi connects and disconnects as normal. I'll give it a few more days before i decide whether to go back to Xandros.

---

### Post by mendieta on 2007-12-21
I agree with Mutley, worth the expense, even my 100% non-geeky wife is totally excited with the eee. Regarding the install: I also think the default Xandros works just fine, I won't touch it. I'll wait for things to settle. Maybe in a year or two I'll upgrade the memory and SSD, and install Kubuntu. By that time, hopefully the patches needed to have the eee running 100% supported will have been included upstream. 

The other option would be to install in an SDHC, but I am not sure about performance, and no one here reported, I'll probably lurk a bit en eeeuser.com ... In any case, I am not wiping out the Xandros default any time soon.

Cheers !

---

### Post by ArbitraryC on 2007-12-24
Got an Eee 8G on Thursday. Gutsy installs okay as long as you turn off Compiz due to aforementioned window dragging issues.

eee-ubuntu-support 0.7 from Google Code works great. Exceptions:

-Overclocking doesn't work on my Eee. I imagine this depends on your particular CPU, as with any overclocking. I'm not really that worried about this. I did delete the scripts responsible for the overclocking, so I wouldn't have a "crash my machine" button next to the volume controls.
-Mute key doesn't work (though the other two volume keys do work)
-Can't hibernate. This might be because I didn't make a swap partition.
-Compiz and suspend don't seem to get along. That's fine, I already disabled it so I could drag windows.
-Charging the battery takes forever if you're running. Shut down or sleep.

Stuff that works fine:
-Suspend works fine, works on lid close if you configure it that way, etc.
-Wifi works fine. Also works with the wifi control button to turn it on/off.
-Ethernet works fine.
-The battery applet warns me about my battery, but after you tell it to shut up it seems to report percentages and estimated times okay.
-The scrolling is a bit awkward in Firefox. I installed Firefox 3 beta 2, because this provides real zooming (eg not just fonts, images and flash work too).

All in all, I'm very pleased. I think this is the first laptop I've owned that was small and light enough that I could take it everywhere. It's also my first non-Apple laptop that can turn the heads of Mac users. :cool:

---

### Post by saunders on 2008-01-03
Hi

I'm trying to install Gutsy on the Eee after a failed attempt to install Xubuntu...

The install for both goes OK, with the desktop working perfectly. Problems arise when I come to set up the Wifi. It just doesn't want to see the wireless network.

The restricted driver warning pops up to tell me that the Atheros Wifi chip is enabled...

I've run the post_install.sh from the eee_gutsy_install.tar. The Wireless configuration script flashes up a stream of errors all based around **"implicit incompatible declaration of built in function..."**, then says wireless installation complete. 

Here's the terminal...apologies for the length!

Any idea where I'm going wrong?


madwifi-ng-r2756-20071018/net80211/version.h
madwifi-ng-r2756-20071018/net80211/ieee80211_node.h 
madwifi-ng-r2756-20071018/net80211/ieee80211_xauth.c 
madwifi-ng-r2756-20071018/net80211/ieee80211_monitor.c 
madwifi-ng-r2756-20071018/net80211/ieee80211_power.h 
madwifi-ng-r2756-20071018/net80211/ieee80211_acl.c 
madwifi-ng-r2756-20071018/net80211/Makefile 
madwifi-ng-r2756-20071018/net80211/ieee80211_crypto_wep.c 
madwifi-ng-r2756-20071018/net80211/ieee80211_scan_sta.c 
madwifi-ng-r2756-20071018/net80211/_ieee80211.h 
madwifi-ng-r2756-20071018/net80211/ieee80211_proto.h 
madwifi-ng-r2756-20071018/net80211/ieee80211_proto.c 
madwifi-ng-r2756-20071018/COPYRIGHT 
madwifi-ng-r2756-20071018/ath_rate/ 
madwifi-ng-r2756-20071018/ath_rate/onoe/ 
madwifi-ng-r2756-20071018/ath_rate/onoe/onoe.c 
madwifi-ng-r2756-20071018/ath_rate/onoe/Makefile.kernel 
madwifi-ng-r2756-20071018/ath_rate/onoe/onoe.h 
madwifi-ng-r2756-20071018/ath_rate/onoe/Makefile 
madwifi-ng-r2756-20071018/ath_rate/minstrel/ 
madwifi-ng-r2756-20071018/ath_rate/minstrel/minstrel.h 
madwifi-ng-r2756-20071018/ath_rate/minstrel/minstrel.c 
madwifi-ng-r2756-20071018/ath_rate/minstrel/minstrel.txt 
madwifi-ng-r2756-20071018/ath_rate/minstrel/Makefile.kernel 
madwifi-ng-r2756-20071018/ath_rate/minstrel/Makefile 
madwifi-ng-r2756-20071018/ath_rate/sample/ 
madwifi-ng-r2756-20071018/ath_rate/sample/sample.c 
madwifi-ng-r2756-20071018/ath_rate/sample/sample.h 
madwifi-ng-r2756-20071018/ath_rate/sample/Makefile.kernel 
madwifi-ng-r2756-20071018/ath_rate/sample/Makefile 
madwifi-ng-r2756-20071018/ath_rate/amrr/ 
madwifi-ng-r2756-20071018/ath_rate/amrr/amrr.c 
madwifi-ng-r2756-20071018/ath_rate/amrr/amrr.h 
madwifi-ng-r2756-20071018/ath_rate/amrr/Makefile.kernel 
madwifi-ng-r2756-20071018/ath_rate/amrr/Makefile 
madwifi-ng-r2756-20071018/ath_rate/Makefile 
madwifi-ng-r2756-20071018/include/ 
madwifi-ng-r2756-20071018/include/compat.h 
madwifi-ng-r2756-20071018/include/sys/ 
madwifi-ng-r2756-20071018/include/sys/queue.h 
madwifi-ng-r2756-20071018/Makefile.inc 
madwifi-ng-r2756-20071018/kernelversion.c 
madwifi-ng-r2756-20071018/README 
madwifi-ng-r2756-20071018/Makefile.kernel 
madwifi-ng-r2756-20071018/INSTALL 
madwifi-ng-r2756-20071018/SNAPSHOT 
madwifi-ng-r2756-20071018/contrib/ 
madwifi-ng-r2756-20071018/contrib/madwifi.spec.in 
madwifi-ng-r2756-20071018/contrib/madwifi.spec 
madwifi-ng-r2756-20071018/Makefile 
madwifi-ng-r2756-20071018/hal/ 
madwifi-ng-r2756-20071018/hal/ah_devid.h 
madwifi-ng-r2756-20071018/hal/COPYRIGHT 
madwifi-ng-r2756-20071018/hal/public/ 
madwifi-ng-r2756-20071018/hal/public/ap30.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/i386-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/ap30.inc 
madwifi-ng-r2756-20071018/hal/public/i386-elf.inc 
madwifi-ng-r2756-20071018/hal/public/mips-le-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/ap51.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/sparc-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/xscale-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/xscale-le-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/alpha-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/wackelf.c 
madwifi-ng-r2756-20071018/hal/public/ap43.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/sparc64-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/armv4-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/ap30.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/alpha-elf.inc 
madwifi-ng-r2756-20071018/hal/public/ap61.inc 
madwifi-ng-r2756-20071018/hal/public/mipsisa32-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/powerpc-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/mipsisa32-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/sparc64-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/mips1-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/sh4-le-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/arm9-le-thumb-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/mips1-le-elf.inc 
madwifi-ng-r2756-20071018/hal/public/powerpc-be-eabi.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/powerpc-be-eabi.inc 
madwifi-ng-r2756-20071018/hal/public/mips-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/powerpc-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/powerpc-be-eabi.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/mips1-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/mips1-le-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/sh4-le-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/powerpc-le-eabi.inc 
madwifi-ng-r2756-20071018/hal/public/xscale-le-elf.inc 
madwifi-ng-r2756-20071018/hal/public/armv4-le-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/powerpc-le-eabi.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/x86_64-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/mipsisa32-le-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/sh4-le-elf.inc 
madwifi-ng-r2756-20071018/hal/public/arm9-le-thumb-elf.inc 
madwifi-ng-r2756-20071018/hal/public/powerpc-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/mips1-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/alpha-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/arm9-le-thumb-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/mips-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/mips-le-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/ap43.inc 
madwifi-ng-r2756-20071018/hal/public/mips-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/ap51.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/mipsisa32-le-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/ap61.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/armv4-le-elf.inc 
madwifi-ng-r2756-20071018/hal/public/armv4-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/i386-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/armv4-le-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/mips1-le-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/x86_64-elf.inc 
madwifi-ng-r2756-20071018/hal/public/mipsisa32-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/ap51.inc 
madwifi-ng-r2756-20071018/hal/public/sparc-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/armv4-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/mips-le-elf.inc 
madwifi-ng-r2756-20071018/hal/public/xscale-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/mipsisa32-le-elf.inc 
madwifi-ng-r2756-20071018/hal/public/sparc-be-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/powerpc-le-eabi.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/xscale-be-elf.inc 
madwifi-ng-r2756-20071018/hal/public/ap61.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/x86_64-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/public/ap43.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/sparc64-be-elf.hal.o.uu 
madwifi-ng-r2756-20071018/hal/public/xscale-le-elf.opt_ah.h 
madwifi-ng-r2756-20071018/hal/ah_soc.h 
madwifi-ng-r2756-20071018/hal/README 
madwifi-ng-r2756-20071018/hal/version.h 
madwifi-ng-r2756-20071018/hal/ah.h 
madwifi-ng-r2756-20071018/hal/ah_desc.h 
madwifi-ng-r2756-20071018/release.h 
./wireless_install.sh: line 23: patch: command not found 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \ 
                make -C $i clean; \ 
        done 
make[1]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath' 
rm -f *~ *.o *.ko *.mod.c .*.cmd 
rm -f .depend .version .*.o.flags .*.o.d 
rm -rf .tmp_versions 
make[1]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath' 
make[1]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal' 
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd 
rm -f .depend .version .*.o.flags .*.o.d 
rm -rf .tmp_versions 
make[1]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal' 
make[1]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate' 
for i in amrr/ onoe/ sample/ minstrel/; do \ 
                make -C $i clean; \ 
        done 
make[2]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/amrr' 
rm -f *~ *.o *.ko *.mod.c 
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd 
rm -rf .tmp_versions 
make[2]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/amrr' 
make[2]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/onoe' 
rm -f *~ *.o *.ko *.mod.c 
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd 
rm -rf .tmp_versions 
make[2]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/onoe' 
make[2]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/sample' 
rm -f *~ *.o *.ko *.mod.c 
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd 
rm -rf .tmp_versions 
make[2]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/sample' 
make[2]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/minstrel' 
rm -f *~ *.o *.ko *.mod.c 
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd 
rm -rf .tmp_versions 
make[2]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate/minstrel' 
make[1]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_rate' 
make[1]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/net80211' 
rm -f *~ *.o *.ko *.mod.c 
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd 
rm -rf .tmp_versions 
make[1]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/net80211' 
make -C ./tools  clean 
make[1]: Entering directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/tools' 
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info core a.out 
make[1]: Leaving directory `/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/tools' 
rm -rf .tmp_versions 
rm -f *.symvers svnversion.h 
Checking requirements... ok. 
Checking kernel configuration... ok. 
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  CC [M]  /home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath/if_ath.o 
  CC [M]  /home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath/if_ath_pci.o 
  LD [M]  /home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath/ath_pci.o 
  CC [M]  /home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/ah_os.o 
  HOSTCC  /home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c: In function 'uudecode_usage': 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c: At top level: 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:40: error: expected ')' before '*' token 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:70: error: expected ')' before '*' token 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c: In function 'main': 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: for each function it appears in.) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose' 
make[3]: *** [/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode] Error 1 
make[2]: *** [/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal] Error 2 
make[1]: *** [_module_/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
make: *** [modules] Error 2 
Checking requirements... ok. 
Checking kernel configuration... ok. 
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  HOSTCC  /home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c: In function 'uudecode_usage': 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c: At top level: 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:40: error: expected ')' before '*' token 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:70: error: expected ')' before '*' token 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c: In function 'main': 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: for each function it appears in.) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function) 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu' 
/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose' 
make[3]: *** [/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal/uudecode] Error 1 
make[2]: *** [/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018/ath_hal] Error 2 
make[1]: *** [_module_/home/hala/Desktop/eee_gutsy_install/madwifi-ng-r2756-20071018] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
make: *** [modules] Error 2 
ath_pci 
 
COMPLETED step Install Wireless Support 
 
STARTED step Configure Suspend/Resume/Powerdown 
 
 
COMPLETED step Configure Suspend/Resume/Powerdown 
 
STARTED step Install Microphone Support 
 
options snd-hda-intel model=3stack-dig 
 
COMPLETED step Install Microphone Support 
hala@laptop:~/Desktop/eee_gutsy_install$ ./post_install.sh 
hala@laptop:~/Desktop/eee_gutsy_install$

---

### Post by bagguley on 2008-01-13
I think I agree about the wait and see. Iv not yet bought one but pay day is only 2 weeks away! Id love to install xbuntu on to it. However, the thing I love about u/k/xbuntu is that it just works. I am not a techie by any stretch of the imagination so ill get one, play with xandros and look forward to a truly stable xbuntu release. And on that note, thankyou all for putting the work in now that will result in eeebuntu!

ps. compiz-fusion on a eee?? I do love ambition!

---

### Post by Skigi on 2008-01-16
Okay, I just got my Eee yesterday, and I've been trying to decide if it's worth switching over to Ubuntu. I really want to, but I'm nervous about the wireless card and the fn keys. Will it all work if  I switch to Gutsy?

---

### Post by mendieta on 2008-01-18
> **Skigi said:**
> Okay, I just got my Eee yesterday, and I've been trying to decide if it's worth switching over to Ubuntu. I really want to, but I'm nervous about the wireless card and the fn keys. Will it all work if  I switch to Gutsy?

For what I read, your best shot is currently eeexubuntu:
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home)

It looks like at least some of the function keys are working:
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization](http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization)

Personally, I am still running Xandros, I love how everything just works. I'd rather have Kubuntu on it, and I wish Asus partnered with Canonical instead of Xandros, but hey!

Update: I forgot to add. I am running the advanced desktop:
[http://wiki.eeeuser.com/howto:getkde](http://wiki.eeeuser.com/howto:getkde)

---

### Post by Mateo on 2008-01-18
i wouldn't recommend the "advanced" (which is a misnomer really) desktop.  It slows down you boot time considerably.

---

### Post by Skigi on 2008-01-19
First chance I got I switched to the Desktop mode, because it does open up a few other options. And as far as Xandros goes, I like it for what comes but not much else.

---

### Post by mendieta on 2008-01-19
> **Skigi said:**
> First chance I got I switched to the Desktop mode, because it does open up a few other options. And as far as Xandros goes, I like it for what comes but not much else.

Yeah, the issue is when you want to add more stuff, the offical repositories have very little software, and software from other sources doesn't always work. 

The other 2 minute mod that I liked is "overclocking" to 900 Mhz. I just installed the precompiled kernel module:
[http://wiki.eeeuser.com/howto:overclockfsb](http://wiki.eeeuser.com/howto:overclockfsb)

I have a script to load it on demand. I run this script automatically in the .xinitrc, before running startkde. Boot up time is totally acceptable for my usage 35 secs from power up to complete KDE login with Wifi connection  up (at home). As pointed out by Mateo, it does slow bootup time down.

What a lovely machine :-)

---

### Post by Mateo on 2008-01-19
you can add the xandros repos and they work fine.  just make sure you set it up so that it checks the Eee repos first.

---

### Post by mendieta on 2008-01-19
> **Mateo said:**
> you can add the xandros repos and they work fine.  just make sure you set it up so that it checks the Eee repos first.

Thanks! Yeah, as explained here:

[http://wiki.eeeuser.com/addingxandrosrepos](http://wiki.eeeuser.com/addingxandrosrepos)

Many things work, but others don't. Some games seg-fault.  And KDE apps won't install, because of the pinning to the older KDE version provided in the asus repositories (Xandros uses a newer kdebase). Still, I was able to customize my eee beautifully, I have a bunch of games, I couldn't be happier !

---

### Post by Muttley99 on 2008-01-19
> **saunders said:**
> Hi

I'm trying to install Gutsy on the Eee after a failed attempt to install Xubuntu...

The install for both goes OK, with the desktop working perfectly. Problems arise when I come to set up the Wifi. It just doesn't want to see the wireless network.

The restricted driver warning pops up to tell me that the Atheros Wifi chip is enabled...

I've run the post_install.sh from the eee_gutsy_install.tar. The Wireless configuration script flashes up a stream of errors all based around **"implicit incompatible declaration of built in function..."**, then says wireless installation complete. 

Here's the terminal...apologies for the length!

Any idea where I'm going wrong?



You need to Blacklist the original Athos drivers that came with Ubuntu. You should find out how to do that on the forum somewhere - sorry i cant remember!

---

### Post by Cresho on 2008-01-28
> **PartisanEntity said:**
> Thanks for the HowTo! One question, why use Ext2? Why not Ext3?

I read somewhere journaling of ext3 will write a sector in the internal memory of the eee to death.  so ext2 is preffered for longetivity.

---

### Post by rapsodia on 2008-01-31
> **Muttley99 said:**
> You need to Blacklist the original Athos drivers that came with Ubuntu. You should find out how to do that on the forum somewhere - sorry i cant remember!

i dont know if you have tried to use the shiftingheat patch to fix your wireless problems it worked for me, just use the ndiswrapper instead of the madfi native drivers i would recomend to do a fresh install of ubuntu, it didnt work for me at first after i tried to fix the wireless by myself just install ubuntu then run the code below.
-------------------------------------------------------------------------------------------------------------------------------
GUTSY POST-INSTALL

* Fetch this help guide and unpack it.
$ wget [http://www.shiftingheat.com/packages...sy_install.tar](http://www.shiftingheat.com/packages...sy_install.tar)
$ tar -xvf eee_gutsy_install.tar

* Run the new, interactive post-installer. This script will selectively perform the following steps:
Upgrade the os, reduce logging ( writes to the drive ), install wireless, repair suspend/resume/powerdown,
and configure the microphone.
$ cd eee_gutsy_install
$ ./post_install.sh

from rapido HOWTO: Asus Eee PC 701 + Ubuntu 7.10 Gutsy forum.
-------------------------------------------------------------------------------------------------------------------------------

---

### Post by Fuzzypiggy on 2008-02-03
My Ubuntu  experience.

I spent 2 days with Xandros and it's OK. I spent another day getting standard Ubuntu 7.10 up on my EEE and I must say it's far, far superior. The only niggles I have left are some function keys don't work, like FN+whatever for vol+-, the battery warning when it first boots is misleading, however the Ub battery monitor on the desktop works great. 

I booted bog-standard boot.img from a USB. I formatted the internal HD to jfs no swap and use a tmpfs in fstab for the swap space and temp areas. Use madwifi atheros patched drivers, they work a treat for getting the wireless up and running. xrandr lets me run the external VGA socket to 1360x768 on my TV/monitor for DivX playback or playing OpenTTD. Webcam still works great with ucview. 

The best thing was the speed increase! dosbox under ASUS Xandros is absolutely awful, but dosbox under Ubuntu screams along, I can happily play Warcraft 2 in dosbox, running of my SDHC. I bought a 16GB SDHC for about 50 quid ( UK ebay ), formatted to ext3, works a treat for fast storage. I actually formatted the SDHC, installed and booted Ubuntu 7.10 from the SDHC card, worked fine, even say it was slightly quicker to boot than the internal drive. 

I used these two guides to get me going, loads of useful info about making Gusty work on 701/4G.

[http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/](http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/)
[http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)

---

### Post by rapsodia on 2008-02-04
> **Skigi said:**
> Okay, I just got my Eee yesterday, and I've been trying to decide if it's worth switching over to Ubuntu. I really want to, but I'm nervous about the wireless card and the fn keys. Will it all work if  I switch to Gutsy?

i just made a little script that will help you install ubuntu from creating the bootable usb to tweaking everything you need to make it work at its best 

you can download the tar file from here 

[http://www.freewebs.com/myfirstscripts/usbeeeubuntu.tar](http://www.freewebs.com/myfirstscripts/usbeeeubuntu.tar)

make sure you read the " README first " it is very important. so let me know how that goes and if you have any questions i put my email on the "README first" file. well good luck and i hope my little script makes installing ubuntu easier.

---

### Post by Captain Llama on 2008-02-05
I bought the 4G Eee PC and installed Xubuntu on it from a usb thumb drive.  Then I used the post_install.sh script to install the native wireless driver, and now Xubuntu doesn't recognize any of my network adapters.  I've tried configuring the networking manually, but it still doesn't recognize any of my adapters.  Does anyone have any ideas?

---

### Post by dgifford on 2008-02-24
question

How do I move .thumbnails to tmpfs?  I have tmpfs setup, but am having a "senior Moment" on linking thumbnails to tmpfs successfully

can y'all help?  THanks

---

### Post by sordello on 2008-02-25
Hi. I have been using Linux off and on for over 12 years - starting with Red Hat and others - and recently discovered Ubuntu. It has been my best and easiest installations to date. I have a couple projects in the works right now. One is building a Linux multimedia PC with the M2A-VM HDMI motherboard.

While working on one project I discovered the eeepc and realized that it was what I was waiting for... The perfect traveling PC. I have been playing with it quite successfully for a couple weeks. I have tried Xubuntu and Gutsy with considerable success but realized they were not ready for prime time yet. Mostly due to the small screen size...

In the end I am using the original Xandros OS in advanced mode. The other OS I tried loaded and booted fine from the thumb drive but, I have a issue that troubles me. After installing a different OS on the thumb drive the Grub boot loader expects to see that thumb drive in the USB port. If it is not installed then the boot fails.  Is there any way to solve this without reinstalling everything. I would like the machine to boot the native Xandros OS without the thumb drive and automatically switch to the Ubuntu OS when the thumb drive is installed. 

Thanks... Bruce

Still a lernin - or is it playin!!!

---

### Post by mdurham on 2008-02-26
Hi Guys, Is there an eee Ubuntu ISO anywhere for download?
Cheers, Mike

---

### Post by jabana on 2008-02-28
> **mdurham said:**
> Hi Guys, Is there an eee Ubuntu ISO anywhere for download?
Cheers, Mike

Here you can find everything you need: [http://ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page](http://ubuntu-eee.tuxfamily.org/index.php5?title=Main_Page)
Ilona

---

### Post by puccaso on 2008-03-01
> **imabuddha said:**
> Yes, Asus & xandros put a lot of effort into making the factory installed OS boot quickly.  However, the trade-off is that not all of the normal linux/unix services are started.  For example, you can't use more than 1 user account on the eee. :|

Even though the eee's power consumption in suspend mode is high, most of the time during a working day you can keep it running, occasionally plugging in or suspending, so you shouldn't have to reboot very often.



ok - well it booted REALLY fast in xandros... do u know what services are disabled? what services wouldnt i need? the boot doesnt take that long (im using hardy alpha 5) but the xandros booted fastttttttt dude.....


what can we take off the boot?

---

### Post by GNUtoo on 2008-03-02
hello,
i am concerned by the life of the ssd drive
mabe it would be better to have:
*jffs2
or:
*jffs2+squashfs(read only) or jffs2+squashfs+unionfs

the first is proposition is easier because we need to:
->recompile the kernel(don't know how to do that in ubuntu,i suppose i have to make a package cause "make xconfig","make","make modules_install" + installing the kernel into grub won't work)
->modify the grub boot command permanantly(so it stay after a kernel upgrade)

and i have no idea on how to do the second one...because it would work but how to upgrade,install...the software...
mabe with unionfs2(so i have a ro partition and it writes the changes to a rw one...)

---

### Post by qpsk1half on 2008-03-04
> **Joners said:**
> 
a. You still have to use ndiswrapper to get the wifi working, then it works fine.

I use madwifi and the patch that ASUS released. Works like a champ for me.

> Originally Posted by DemonBob
Madwifi Patch for this card: [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Madwifi Other Card Thread: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Patch was removed from Madwifi due to API Breakage on non I386/686 platforms. I was able to grab a new link to it from #eeepc channel

Download, source + patch [http://quaggaspace.org/eee/madwifi-eee.tar.bz2](http://quaggaspace.org/eee/madwifi-eee.tar.bz2).

It does work.

Madwifi is talking to Athero's about getting this working across all platforms, and included in an offical release. Right now it only works on i386 and not x64. It does work on Acer 5315.

Happy hunting

---

### Post by puccaso on 2008-03-06
bump - on the suspend issue? using gutsy...

---

### Post by RealG187 on 2008-03-10
I am thinking of getting one.

I have some questions, there is one with "Linux" on it, I dont know which Distro, it just says EEE PC version x.yx

Can I install another OS without a USB CD drive, like I have USB flash and hard drives, is there a way I could copy and ISO if the XP/Ubuntu disk onto a USB Drive and then boot the drive and have an "emulated" CD from the ISO?

How fast it it, like GHz and MHz? Can I run VM on it to maybe run XP off a USB hard drive. Could I dual boot off the 4 GB hard drive?

---

### Post by starbase1 on 2008-03-11
I can't answer all the questions, but for the ones I can...

Yes, it will boot from USB or the SD cards. Given how cheap SD cards are these days, it would seem very practical to keep a few of those with different OS on!

The distro included is a version of Xandros, with the clever stuff turned off. (You can turn it on again easily enough).

With half a gig of memory you are really pushing it to run XP in a VM, though it might just be possible with a very small footprint host OS. I think you'd really need to have a memory upgrade to make it worth using though.

I have used mine with a chunky USB powered hard hard drive attached, it was able to run it just fine - not sure what it would do to the battery life as I didn't run it right down.

I'd say the most important thing in getting the most from it would be a decent wifi signal.

Loads more info on the eee user forums:
[http://www.eeeuser.com/](http://www.eeeuser.com/)

I'm very impressed with my one - it's not remotely powerful but it is superbly portable, and very well made. Makes a great portable media player...

Nick

---

### Post by RealG187 on 2008-03-11
Could I put the Ubutnu ISO on as SD card? Like "burn" it on (instead of writing the data to a CD, write it to the SD card) and make it bootable, or could I do the same with and XP dsk/ISO?

How long have you had it for, my Acer Aspire 9410 is a batttery w*0re (not using it as an insult, so it shoudnt offend anyone). I get around an hour, maybe between one and two per charge. Would the eee be easier on power?

---

### Post by starbase1 on 2008-03-12
> **RealG187 said:**
> Could I put the Ubutnu ISO on as SD card? Like "burn" it on (instead of writing the data to a CD, write it to the SD card) and make it bootable, or could I do the same with and XP dsk/ISO?

How long have you had it for, my Acer Aspire 9410 is a batttery w*0re (not using it as an insult, so it shoudnt offend anyone). I get around an hour, maybe between one and two per charge. Would the eee be easier on power?

Yes, it will boot from SD card or USB drive without problems.

I'd seriously think about more memory if you are planning on running XP, but then again memory is cheaop these days.

I've had it a few months, I think 3 to 3.5 hours is typical. A larger battery pack has been announced, for 5 hours - not sure if it is in the shops yet.

I'm very happy with it - the real strengths are low price, small size, and very good build quality. It's not a powerful box though so if this is important, it's not for you. 3 USB ports are very handy for expansion. The keyboard is small but usable - and a larger one would make it less portable.

The only thing I'd really think might be worth holding off for is if you are not particuarly worried about spending a bit more - the 9 inch screen version is almost exactly the same sized case, (a little thicker I understand), and that would be very nice to have.

If you want to know what others have done in the way of operating systems etc, take a look at the most popular eee forums here: 
[http://www.eeeuser.com/](http://www.eeeuser.com/)

Nick

---

### Post by RealG187 on 2008-03-12
So I dont need a USB CD drive since I could just copy to an SD?

I dont know how to install memory in laptops though...

re: eeuser forums, I am not sure yet so I an not ready to sign up for any new site.

---

### Post by starbase1 on 2008-03-13
> **RealG187 said:**
> So I dont need a USB CD drive since I could just copy to an SD?

I dont know how to install memory in laptops though...

re: eeuser forums, I am not sure yet so I an not ready to sign up for any new site.

Yep, SD is just as good (and does not stick out the side of the machine). I got into the habit if having 3 or 4 SD cards with different stuff on them in my wallet.

Memory into laptops - it should just be a case of popping out the old chip and popping in the new one - no skill required (and I speak as someone with 6 left thumbs on my right hand...)

As for the forums, no need to sign up to read them, but it will give you a good idea of how many operating system are being put on it by others - some are even making customised versions of distros optimised for this very machine, which is about as easy as it can get...

One rather clever chap even managed to get the Mac OS running on an eee, though this was not at all simple!

---

### Post by RealG187 on 2008-03-13
I cant even get Mac OS running on my Acer...

Does it come with a recovery disk for the Xandros OS? Is the Xandros there the exact same one, or is it made for EEE or if I go and install Xandros will any PC have the same interface (what's wierd is the theme looks like XP silver, did ASUS have to pay MS royalties on that, and if they did would the free Xandros not have that?)

---

### Post by mendieta on 2008-03-13
Just a quick queeestion ;-) I got an 4G SDHC card for my eee, mostly to store music and videos. It came formated as vfat, and it seems to be working fine. Is it still better to reformat to ext2 ? (in terms of speed, etc). I found this info, but it's not all that usefull.

[http://wiki.eeeuser.com/execute_apps_off_sd](http://wiki.eeeuser.com/execute_apps_off_sd)

 Thanks in advance!

---

### Post by starbase1 on 2008-03-14
> **RealG187 said:**
> I cant even get Mac OS running on my Acer...

Does it come with a recovery disk for the Xandros OS? Is the Xandros there the exact same one, or is it made for EEE or if I go and install Xandros will any PC have the same interface (what's wierd is the theme looks like XP silver, did ASUS have to pay MS royalties on that, and if they did would the free Xandros not have that?)

Yes, it comes with a disk that makes it VERY simple to restore it back to factory state.

It's not standard Xandros, they hacked the interface in particular to make it fit the eee screen, and changed it to a few large tabs. You can go advanced though, and it will generally take progs from the Xandros repositories.

You are not the first to notice the XP resemblance! The popular theory was that it was done to make things a bit easier for those who are used to windows...

Nick

---

### Post by xclegend on 2008-03-14
Firstly thanks for the script. It worked 99% . I am still not able to use wifi. It seemed that the wifi drivers installed. But I srill cannot connect in wifi still just a wired connection showing in Network manager.when i did lsmod | gerp ath   the result is ath_pci     ******    o
                                                                                wlan         ******     1 ath_pci
                                                                                ath_hal     ******     1 ath_pci


When i run iwconfig it shows     lo            no wireless connections
                                                    eth0        no wireless connections

I have now done two installs of ubuntu on the eeepc and neither yielded results getting wireless working. I may just sell the eeepc . I have never had so much trouble using ubuntu(which I have used since it came out) Any suggestions I at least installed the madwifi drivers with your script. Is there something I am missing? Is my restricted modules version wrong? i did an update and mine are :
linux-restricted-modules-2.6.22.4-1402.6.22.4-14.10    

I hope someone can help me with  this wifi nightmare. Any help would be appreciated. Thanks

---

### Post by xclegend on 2008-03-14
Firstly thanks for the script. It worked 99% . I am still not able to use wifi. It seemed that the wifi drivers installed. But I srill cannot connect in wifi still just a wired connection showing in Network manager.when i did lsmod | gerp ath   the result is ath_pci     ******    o
                                                                                wlan         ******     1 ath_pci
                                                                                ath_hal     ******     1 ath_pci


When i run iwconfig it shows     lo            no wireless connections
                                                    eth0        no wireless connections

I have now done two installs of ubuntu on the eeepc and neither yielded results getting wireless working. I may just sell the eeepc . I have never had so much trouble using ubuntu(which I have used since it came out) Any suggestions I at least installed the madwifi drivers with your script. Is there something I am missing? Is my restricted modules version wrong? i did an update and mine are :
linux-restricted-modules-2.6.22.4-1402.6.22.4-14.10    

I hope someone can help me with  this wifi nightmare. Any help would be appreciated. Thanks

---

### Post by xclegend on 2008-03-14
I finally fixed the wifi issue. Dumb mistake on my part. Just had to reinstall madwifi a second time . the script provided in the beginning of the original post worked better than all others i had tried even at eeeuser forums. Thanks for the scripts and all the help:)

---

### Post by RealG187 on 2008-03-14
> **starbase1 said:**
> Yes, it comes with a disk that makes it VERY simple to restore it back to factory state.

It's not standard Xandros, they hacked the interface in particular to make it fit the eee screen, and changed it to a few large tabs. You can go advanced though, and it will generally take progs from the Xandros repositories.

You are not the first to notice the XP resemblance! The popular theory was that it was done to make things a bit easier for those who are used to windows...

Nick

Like a CD, so I could boot that from a USB CD Drive or copy to an SD card?

So it's modifed to include the XP? Did they have to pay MS, cuz wouldnt that be copyrighted?

Also I heard that they might stop shipping EEE's with Linux and ship windows, is this true? The one I seen had Linux, should I get it while I can? I dont wanna pay for XP, already have it, and would be more exicted about Linux!

Also could I install additional progams like Wine?

---

### Post by mendieta on 2008-03-16
> **mendieta said:**
> Just a quick queeestion ;-) I got an 4G SDHC card for my eee, mostly to store music and videos. It came formated as vfat, and it seems to be working fine. Is it still better to reformat to ext2 ? (in terms of speed, etc). I found this info, but it's not all that usefull.

[http://wiki.eeeuser.com/execute_apps_off_sd](http://wiki.eeeuser.com/execute_apps_off_sd)


Well, I'll answer myself in case it helps other ubunteros/as. I reformated to ext2, and performance was a lot worse, copying 120 Mb in large files would take, I think 3 to 4 times slower (didn't benchmark properly) on the SDHC card. I guess  that's why in the wiki above they suggest using vfat for data. I reformatted to fat32 and things are speedy again. 

I am pretty puzzled! Why would a native format as ext2 be so low in an sdhc card, I am sure there is something odd. I think I read in eeeuser.com that the default mounting options for the sdhc card in ext2 are wrong. Oh well

---

### Post by Hesperion on 2008-04-29
> **jfernyhough said:**
> Yes, you should be able to make a "Live SD" in the same way as a Live USB, the process should be exactly the same (if you use a USB card reader).
Not so sure; unless you are referring to something different...

[http://samiux.wordpress.com/2008/04/26/ubuntu-804-lts-on-asus-eee-pc/](http://samiux.wordpress.com/2008/04/26/ubuntu-804-lts-on-asus-eee-pc/)

---

### Post by RealG187 on 2008-04-29
I heard with Daimen tools one could make a bootable USB/Card, for exmaple take a Ubuntu CD and put on on the drive and then put Daimen on it, boot the drive (which boots Daimen) and select the ISO, so then the SD will be just like the Ubuntu CD!

---

