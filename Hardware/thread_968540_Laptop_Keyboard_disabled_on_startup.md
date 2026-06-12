---
title: "Laptop Keyboard disabled on startup"
date: 2008-11-02
forum: Hardware
---

### Post by BBXiong on 2008-11-02
Hi, i am using a BenQ s42 laptop. When i try to install kubuntu 8.10 last night, i found out that my keyboard have been disabled during kubuntu start up...
Can anyone please help me with that??

thank you

---

### Post by mbitesd on 2009-01-06
Any suggestions for this problem? I've tried both the desktop and alternate iso's but in both cases the keyboard doesn't work. Would a usb keyboard be a work around?

---

### Post by mbitesd on 2009-01-06
Ok perhaps some more information would help.

When I run the live cd a menu pops up giving me the option to "run ubuntu without changing the hard drive", "install ubuntu" etc, and I can use the keyboard to scroll around those menus and change things. However when I select the live cd option, ubuntu shows a loading screen for a while and then boots into a cli, not a gui as I expect it should. At the cli the keyboard doesn't do anything.

I thought the problem might actually be related to the DVD drive, so I tried the suggestions here [https://bugs.launchpad.net/ubuntu/+bug/217616/comments/8]("https://bugs.launchpad.net/ubuntu/+bug/217616/comments/8") to no avail.

So any ideas?

---

### Post by mbitesd on 2009-01-06
Ok I think I've made a little headway. This laptop has "hybrid graphics"- two video cards, a high performance NVidia 9600m and some intel video card for power saving.

Apparently laptops with hybrid graphics fail to boot to X ([https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/304445]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/304445")) unless the bus ID is specified.

My question is then: how can I specify which graphics card to use so that I can complete the installation successfully?

---

### Post by lswest on 2009-01-06
You should be able to disable one of the cards in your laptop's BIOS.  You can probably reach this by hitting the delete key or F12 as it's starting up (there should be instructions on how to reach the BIOS or the Setup page in the first few moments of boot).

About the keyboard, you may need to, once you have graphics, go to the control panel, find the regional and language options, and then under keyboard layout and keyboard information, change it to be an "evdev-managed keyboard".  At least, that's what I had to do on my laptop running ArchLinux with KDE 4.2 Beta.

---

### Post by mbitesd on 2009-01-06
Unfortunately there isn't a way to disable one of the graphics cards in the bios. I think then I will need some way to pass the bus ID information as a boot option.

---

### Post by mbitesd on 2009-01-06
Well the same thing happened when I tried to install ubuntu from windows. All that seemed to happen was the live CD was copied to the hard drive and ubuntu was added to the master boot record.

Would using one of the more advanced windows installation methods ([https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")) lead to a different result? If X was actually installed from windows then I might be able to edit the xorg.conf and add the correct busid (BusId "1:0:0" ?).

Also, is there a way to dump all the text you see when you remove "quiet" from the boot options? Remembering that I'd need to do this using a boot option, as the installation hangs part way through.

---

### Post by mbitesd on 2009-01-07
What about creating a custom Ubuntu live cd with a modified xorg.conf file? Unfortunately all the methods for doing this require a Linux install, something which I don't have easy access to.

Would that work?

---

### Post by mbitesd on 2009-01-07
One last bump. Any ideas or suggestions would be much appreciated.

---

### Post by shadz on 2009-01-07
Hi, I have the same laptop, BenQ S42 and unfortunately the same problem as well. Right now I'm using an external usb keyboard to type this post. Like mbitesd said, the laptop keyboard works during the live cd start menu, but it fails to work after logging in. I tried to type in gedit using the laptop keyboard but nothing registers. My external usb keyboard works however.

Is there a solution for this? I am using Ubuntu 8.04.

---

### Post by mbitesd on 2009-01-08
> **shadz said:**
> Hi, I have the same laptop, BenQ S42 and unfortunately the same problem as well. 

Hi shadz. Does that mean the dual graphics cards are working fine, and that the only problem you have is with the keyboard? If so, did the live CD boot into the gui correctly?

---

### Post by butrousity on 2009-01-08
I am also a s42 user. I managed to get ubuntu installed using a usb keyboard and the 8.10 amd64 alternate cd. I then inserted the live cd and then mounted the linux hard drive and edited the xorg file. I am running a resolution of 1024 x 768 using the vesa drivers and the intel graphics card. I have no idea about the keyboard issue. I tried changing to evdev-managed but it did nothing. I've seen something at another forumn about hybrid graphics. I will try and set it up and then post my final xorg.conf file if anyone wants it.

---

### Post by BBXiong on 2009-01-08
my problem now is not the hybrid problem cos i already disabled it in the bios, to do that, you have to download the latest bios version from benQ australia, and it can only be installed under XP environment. Also, after installing that one, the intel card will not be there anymore, as in, being disabled by bios, and will not be able to be detected under ANY os, including windows vista....
as for now, i am still having the keyboard issue that i am facing earlier..i actually thought of getting an external keyboard, but that would be pointless if i wanted to use my ubuntu when i am outdoor unless i want to bring a big external keyboard out  =_="

---

### Post by butrousity on 2009-01-08
Bad news guys. I checked the system under ubuntu and found no mention of mouse of keyboard input devices apart from the usb mouse and keyboard i am currently using. It looks like ubuntu is not recognising the ps/2 keyboard and mouse. I'm not certain if this is the same on everyone elses computers (looks like it could be as everyone is complaining of the same issue) but it does look like ubuntu won't work on this laptop. Maybe future releases of ubuntu and perhaps even other linux distro's may work. I'm sure it won't be too much longer before it will work. It does seem that alot of people have purchased an s42 and you have to assume someone is already figuring this out but for the time being we have to sit back and wait. All i can say is thank god i have a desktop with working ubuntu installation.

---

### Post by mbitesd on 2009-01-08
I'm the first to admit I don't understand what's going on with the keyboard, but if an old operating system like Windows xp can detect it, I can't see why a modern operating system like Ubuntu can not. There must be a solution.

---

### Post by mbitesd on 2009-01-11
Has anyone with working ubuntu installation done some digging (log files etc) to look for possible solutions to he internal keyboard problem?

---

### Post by aaron552 on 2009-01-14
> **mbitesd said:**
> I'm the first to admit I don't understand what's going on with the keyboard, but if an old operating system like Windows xp can detect it, I can't see why a modern operating system like Ubuntu can not. There must be a solution.

I agree. There must be something else going on that is preventing the keyboard from being detected. Because the keyboard works fine in the bootloader, I'd guess that this is a kernel-level issue >.<

---

### Post by mbitesd on 2009-01-23
So how does one get some help on this keyboard issue? What sort of logs etc would be needed to post a bug report? Or would it be better to try and find someone who is familiar with how the kernel handles keyboards and contact them directly?

No shortage of people who have this problem, but a real shortage of expertise unfortunately (not a complaint!).

---

### Post by voidman on 2009-01-26
Has anyone tried new kernel?
Or (sorry) different distros?

---

### Post by butrousity on 2009-02-08
Hi, I thought I'd post an update on what I've been able to achieve so far.

I managed to get the keyboard running. I (and I'm sorry to have to mention other distributions, but it helps with diagnosing the problem) decided to try running a few other distributions and nothing worked until I came across current release of Debian (Debian Etch 4.0r6). It has the 2.6.18 kernel. Keyboard runs fine but the mouse doesn't work yet. The issue with the mouse is most likely caused because the Synaptics touchpad driver hasn't been installed. The Intel wireless card is not supported until kernel 2.6.24/2.6.26, however, there are drivers you can download and install (see [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) for information on how to install the drivers).  The next release of Debian (Lenny 5.0) is scheduled for release in the next week. I downloaded the rc2 version to test and found that the keyboard doesn't work. The kernel version this release is 2.6.24. It does seem that the keyboard (and possibly the mouse) work in older versions of the kernel but not some of the latest ones. What I'm planning to do is compile some different kernel versions from source under Debian in the hope that I can get a more updated version of the kernel with support for the mouse and keyboard. I know I could have done this with Ubuntu as well since I did manage to get that installed too, but I think it's better off to start with a working system first. I'd ask anyone else who has the time to try the same thing too. To successfully install Debian you will need to change the hard drive bios settings to IDE hard drive. I have not yet found the correct module needed for SATA. Of course this will mean that if you want to boot into windows you'll have to change the bios back otherwise you get the BSOD.

Another option is to try and download the 2.6.18 kernel to use in Ubuntu, however I can't see this being the best option as it could lead to some compatibility problems with both hardware and some programs.  

Thats all I've figured out so far, I'll post again once I have a version of the kernel that will work for Ubuntu.

P.S. I have also tried running the alpha 4 version of Jaunty (Ubuntu 9.04) and had no luck. Jaunty uses kernel 2.6.28.6

---

### Post by dtuza on 2009-02-10
Hi, confirming the aforementioned issues with keyboard not recognized, and difficulties with X loading, what with hybrid graphics and all. I'm a S42 user as well.

I don't consider myself knowledgeable enough to really worry terribly over installing ubuntu on this PC, but would quite like to in the future. Does anyone know if hybrid graphics etc etc will be supported in jaunty (or prior)?

---

### Post by ubstanley on 2009-03-03
Has anyone tried the kernel parameter "irqpoll"? I am not an S42 user, but it seems to solve the most common "keyboard undetected" problems on the net.

---

### Post by stephen53 on 2009-03-04
I built a desktop computer recently. Sometimes I notice the usb keyboard wouldn't be working when I booted up. I would unplugged my key then back in and it would work. I checked my bios menu and found that usb was ticked off. I ticked it to be on and the problem went away. Check your bios and see if the problem might be there.

---

### Post by freaksterr6676 on 2009-03-06
My keyboard is working on intrepid perfectly.  Simply add the following to your kernel boot parameters to fix the keyboard and trackpad:

i8042.nomux=1 i8042.noloop=1

Also the "|" isn't correctly mapped, you need to create a file ~/.xmodmap. In it, you need the following entry:
keycode 94 = backslash bar

---

### Post by zombrax on 2009-08-04
> **freaksterr6676 said:**
> My keyboard is working on intrepid perfectly.  Simply add the following to your kernel boot parameters to fix the keyboard and trackpad:

i8042.nomux=1 i8042.noloop=1

Also the "|" isn't correctly mapped, you need to create a file ~/.xmodmap. In it, you need the following entry:
keycode 94 = backslash bar


ok i have the same problem as everyone else with the S42 laptop. 

As I'm a total newbie could someone please be kind enough to show me how 
1) Get into kernal boot parameters
2) create a file (as in how and where) 

many thanks
zX

---

