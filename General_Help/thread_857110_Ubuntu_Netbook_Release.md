---
title: "Ubuntu Netbook Release"
date: 2008-07-12
forum: General Help
---

### Post by postmortemMT on 2008-07-12
Hey Guys,

Is there any news when the Ubuntu Netbook remix wil be released?

also will this be an OS on its own or you'll need a previous Unbunto and install the remix upon it?

Recently I've purchased an Asus 333 900. Does it fit the specs for Ubuntu Netbook?

Yea I'm still a newb on Linux systems but I can't wait to start playing around. I've been really impressed by the OS so far :)

Regards And Thanks,
Sam Spiteri

---

### Post by der_joachim on 2008-07-12
I assume that you meant the EEE900. ;) The netbook site lists an Intel Atom processor as an explicit requirement. Since the 900 does not have one, I doubt whether Netbook Remix supports the EEE900 out of the box. 

The linux community would not be the linux community though when there wasn't an alternative. Have you looked at [eeeXubuntu]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home")?

[Edit] Whoops! I am wrong! [This thread]("http://www.eeebuntu.org/forum/viewtopic.php?p=620") hopefully gives you some information you need.

---

### Post by tact on 2008-07-13
I have an eee 900.  It does not have the atom processor and the ubuntu netbook remix runs on it nicely... VERY nicely.

You do have to have a working ubuntu install, then add the netbook repository, then use synaptic or apt-get to install the appropriate packages.  After that there is some manual setup needed to get the panels as they should be (delete the bottom panel, delete some applets from the top panel, then add the window-picker and go-home applets)

There is only one package that you must NOT install - it is specific to atom processors and the warnings which package not to install are clear.

Its the first step that is the hard one!  i.e. Getting a working ubuntu install on the eeepc.  Make sure you have that all sorted before you try changing the interface.

On my eeepc 900 I have a couple of normal user accounts (hardy heron of course) and I created a separate user account to try out the netbook remix.

Very cool...  log in as one user and get the normal ubuntu desktop.  Logon as a different user and get the netbook remix interface.  Same ubuntu under the hood.

There are a few gotcha's with the install.  So you gotta be prepared to think on your feet and face some degree of manual intervention.   e.g. when you install the remix in one user account - some of the changes are propagated to all other accounts on the same PC - so next time you log in to a "normal" ubuntu desktop account you will find the ume-launcher running and will need to open up system monitor to kill it, and then open "sessions" and disable it from starting next time.

How is it!?  I find the netbook remix interface to be a very attractive interface and it works great.  Nice transparencies in places..  nice effects...  all without using compiz.  It seems to use less resources and is quite snappy.

All in all - it is very good effort and you don't have to make any allowances for it being a work in progress - its just good!

---

### Post by der_joachim on 2008-07-13
Thanks for the info tact. One question though: my 900 with the default Xandros install boots in about 15 seconds. How about your NBR installation?

---

### Post by postmortemMT on 2008-07-13
Hey Tact,

I've just installed eeeXubuntu on my machine but I'd rather have Ubuntu netbook. The interface looks way cooler.

Can you please describe me the process of installing Ubuntu netbook on my Asus EEE. Please describe the process from A to Z because I'm still a newb also please provide links from where I can download the necessary OS software.

Thanks a lot for bearing with me.

Regards,
Sam

---

### Post by tact on 2008-07-13
> **der_joachim said:**
> Thanks for the info tact. One question though: my 900 with the default Xandros install boots in about 15 seconds. How about your NBR installation?

I will time the boot up this evening when I get back from the office.  I suspect its a bit longer than the default xandros install - its a full ubuntu install really.  The remix just changes the user interface from standard gnome.

---

### Post by tact on 2008-07-13
> **postmortemMT said:**
> Hey Tact,

I've just installed eeeXubuntu on my machine but I'd rather have Ubuntu netbook. The interface looks way cooler.

Can you please describe me the process of installing Ubuntu netbook on my Asus EEE. Please describe the process from A to Z because I'm still a newb also please provide links from where I can download the necessary OS software.

Thanks a lot for bearing with me.

Regards,
Sam

Hi there Sam,  I am not the right person to assist you there.  I have zero experience with Xubuntu or Kubuntu.  Only ever used the gnome (ubuntu) user interface.

There are packages you can find in synaptic called ubuntu-desktop, xubuntu-desktop and kubuntu-desktop.  I have seen threads where people have said you can change environments by just installing the appropriate package...  eg. to get the gnome (ubuntu) environment install "ubuntu-desktop".  

You would really need to read up, search, to confirm this.  As you read up on it keep in mind that (I guess) installing "ubuntu-desktop" would install ALL the bits and pieces of the gnome (ubuntu) environment on your system.   This may use up precious space on your eeepc.  (not sure whether installing ubuntu-desktop uninstalls xubuntu-desktop????)

I guess it would also depend on how you have setup (k/x)ubuntu on your eeepc 900.   If you tried to keep the Xandros install when you installed xubuntu you might be pressed for space.

I completely wiped the Xandros installation out - then installed / on the first 4Gb SSD.   I partitioned the 16Gb SSD so that there was 4Gb for /usr and the rest, 12Gb, set aside for /home.   So space is not such an issue for me.

---

### Post by postmortemMT on 2008-07-13
> **tact said:**
> Hi there Sam,  I am not the right person to assist you there.  I have zero experience with Xubuntu or Kubuntu.  Only ever used the gnome (ubuntu) user interface.

There are packages you can find in synaptic called ubuntu-desktop, xubuntu-desktop and kubuntu-desktop.  I have seen threads where people have said you can change environments by just installing the appropriate package...  eg. to get the gnome (ubuntu) environment install "ubuntu-desktop".  

You would really need to read up, search, to confirm this.  As you read up on it keep in mind that (I guess) installing "ubuntu-desktop" would install ALL the bits and pieces of the gnome (ubuntu) environment on your system.   This may use up precious space on your eeepc.  (not sure whether installing ubuntu-desktop uninstalls xubuntu-desktop????)

I guess it would also depend on how you have setup (k/x)ubuntu on your eeepc 900.   If you tried to keep the Xandros install when you installed xubuntu you might be pressed for space.

I completely wiped the Xandros installation out - then installed / on the first 4Gb SSD.   I partitioned the 16Gb SSD so that there was 4Gb for /usr and the rest, 12Gb, set aside for /home.   So space is not such an issue for me.


I see I see. I think I know what to do but can you please tell me from where you had downloaded unbunto netbook remix please?

Cheers Man.

---

### Post by tact on 2008-07-13
Start here:
[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)

It has some install info, then links to a page where you can find the repo addresses.  

You add the repo lines for hardy to your software sources list, update, then use synaptic or apt-get to install what you want.

---

### Post by tact on 2008-07-13
> **der_joachim said:**
> Thanks for the info tact. One question though: my 900 with the default Xandros install boots in about 15 seconds. How about your NBR installation?

On eeepc-900:
From pressing the power-on button to GDM username/password login prompt is 45 seconds.  (Includes a 3 second delay "press esc to open grub menu" that could be eliminated).

From pressing enter after entering username/password at the GDM prompt to having a useable netbook remix desktop - 15 seconds.

Pls realise that (at least right now?)  the "NBR installation" is only a different face on a full ubuntu installation.  The normal compiz/gnome desktop environment is replaced by a different launcher and window switcher is replaced by window-picker.   It is not a custom made kernel or anything like that.

---

### Post by postmortemMT on 2008-07-14
Is it possible to Install Ubuntu 8.04 on the Asus Eee 900 via USB flash memory bootable? or do you require byforce an external CD\DVD-Rom Drive?

Thanks,
Sam

---

### Post by tact on 2008-07-14
> **postmortemMT said:**
> Is it possible to Install Ubuntu 8.04 on the Asus Eee 900 via USB flash memory bootable? or do you require byforce an external CD\DVD-Rom Drive?

Thanks,
Sam

Absolutely the best way is to create a USB stick that acts like the liveCD.

What you need:
- Download the latest hardy liveCD ISO  - v8.04.1
- A USB stick (1GB is plenty)
- go download this handy utility that automatically takes whats on the liveCD and puts it onto the USB stick and makes it bootable:   [https://launchpad.net/~probono/+archive]("https://launchpad.net/%7Eprobono/+archive")

(Just add the repo for the hardy version to your software sources, and apt-get it.)

You do not even need a CDROM drive -  you can make the liveUSB direct from the ubuntu liveCD ISO without even burning it to a CD.  Instead - mount the "ubuntu-8.04.1-desktop-i386.iso" on /media/cdrom

 ```
sudo mount -o loop /home/your_username/ubuntu-8.04.1-desktop-i386.iso /media/cdrom
```Then insert your USB stick into a USB port, run the liveUSB install program (System>Admin>Install LiveUSB), make sure that the correct USB device is selected as the target...  and watch the magic.
(assumes the ISO file is in your home folder)
(BTW all data on the USB stick will be wiped off in the process - so make sure you have no treasures stored on it first).

---

### Post by postmortemMT on 2008-07-14
I've managed to produce a Ubuntu bootable USB. Thanks so much for the  help :)

Now I was wondering how to best partition my system.

It has 2 Hard Disks. 1 is 4GB and the other is 16GB.

Should I produce a Ext2 3.5GB root, 500mb swap and 16GB as free space?

If yes can somebody please tell me how to properly manage this>? since I'm not knowledgeable enough when it comes to linux partitioning.

Thanks so much :)

---

### Post by tact on 2008-07-15
There are some good tips on this ubuntu community site
[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

Basically the suggestion is that for a SSD best to limit the number of writes to it...  so use ext2 not ext3 or any other journalling file system.  Don't use a swap file at all.

As for the sizing of partitions - thats pretty individual.  In my case (same situation as you - one  4GB and one 16GB drive...) what I did was:
- checked the used space on / on my other laptop that has been running full ubuntu hardy install since before Hardy was released (want to be careful that I don't run into a shortage of space after a few months, after installing programs etc).
-  On that system / (or rather everything other than /home) was using 4.5GB, /usr was the biggest contributor with about 3GB soooooo... wanting to allow for more expansion if needed I partitioned like this:
/  got the entire first SSD (4GB)
/usr got 4GB of the second SSD
and the remainder of the second SSD went to /home  (12GB)

This is not necessarily the best, and certainly not the only, way to partition up the available space.

How to do it?  Well boot from the USB installer stick.  When you get to the place where it wants to set up partitions select manual.... delete all existing partitions and create new ones the way you want it to be.  

Warning - doing this destroys all that is on the drives.. you will be blowing away your Xandros as well as recovery partitions they have hidden on the drive etc.   You still have the Xandros install CD that came with the Eeepc though - right?  ;)

Cheers

---

### Post by tact on 2008-07-15
...google around a bit.  There are lots of other possibilities..  some people even buy something like an 8GB SD card, leave it in the SD slot, and install ubuntu on that.

---

### Post by tilapia on 2008-07-16
I installed Netbook Remix on an Asus Eee 8G and it works like a charm. Really looking forward to the final release of this. You'll need to do some fiddling to get things working properly, including turning off Compiz if it's running. I followed the guide here: [http://techpad.co.uk/content.php?sid=36](http://techpad.co.uk/content.php?sid=36)

---

