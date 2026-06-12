---
title: "Old hardware - what to do?"
date: 2012-12-27
forum: Hardware
---

### Post by ArminasAnarchy on 2012-12-27
Since hardware is always coming down in price, and since it also quickly becomes obsolete, it seems inevitable that you'll build up a collection of old computers.

As well as having my own, I've also been given some stuff by relatives, meaning that I now have 2 laptops and 2 computers that are completely redundant, sitting unused and unloved.

If the worse comes to the worse, I'm perfectly happy to just amuse myself dismantling them - kind of in the Raspberry Pi spirit of learning how stuff works from the bottom up.

It would be interesting however to actually use the hardware. One idea I've got is to set up a server - it would mean I could host my own email, as well as having files backed up and available on the move. Has anyone done this? What are the specs, how difficult was it to set up/use, what OS are you running?

Another idea - which would really be something of a mega project - is to hook up all the hardware together to use it in a cluster - I've read stuff about this thing called a "Beowulf cluster". Again, has anyone any experience with this? Again, it'd be interesting to hear about operating systems in particular - I'd want something relatively easy to set up and configure since I'm not really a computer master!

---

### Post by xedi on 2012-12-27
Depending on how old the hardware is, you could use the computers to do scientific research in a distributed computing project such as [folding@home]("http://folding.stanford.edu")

---

### Post by zombifier25 on 2012-12-27
I second using them to set up a cheap web server. I haven't tried it though, I don't really have a lot of hardware parts lying around.
And/Or, like xedi said, folding@home. Don't forget to fold for TeamUbuntu (team 45104)

---

### Post by ArminasAnarchy on 2012-12-27
> **xedi said:**
> Depending on how old the hardware is, you could use the computers to do scientific research in a distributed computing project such as [folding@home]("http://folding.stanford.edu")

> **zombifier25 said:**
> I second using them to set up a cheap web  server. I haven't tried it though, I don't really have a lot of hardware  parts lying around.
And/Or, like xedi said, folding@home. Don't forget to fold for TeamUbuntu (team 45104)

I agree, this would be a really good use of the hardware, and something I've already considered. However, I think this is something that would be best done once I'd build the cluster. If it can be done? 

Having a "virtual computer" linking all these together really would be cool, even if it would cost loads in electricity. The making it happen is the hard part however, thinking about what each node would run etc even before they're all linked seems like a big challenge.

---

### Post by lykwydchykyn on 2012-12-27
I've found it challenging to find uses for old stuff like this, but if it's decent you can always install a minimal-yet-functional environment on it and pass it on to a deserving young person.

I've been blogging about my recent attempts to find a suitable open-source OS for Windows-98-era computers, you might find this compelling depending on the age of your hardware:

[http://www.alandmoore.com/blog/2012/12/14/replacing-windows-98-and-other-seemingly-impossible-tasks/](http://www.alandmoore.com/blog/2012/12/14/replacing-windows-98-and-other-seemingly-impossible-tasks/)

---

### Post by haqking on 2012-12-27
[http://www.itforcharities.co.uk/donorinf.htm](http://www.itforcharities.co.uk/donorinf.htm)

[http://www.epa.gov/epawaste/conserve/materials/ecycling/donate.htm](http://www.epa.gov/epawaste/conserve/materials/ecycling/donate.htm)

[http://www.computersforcharities.org/](http://www.computersforcharities.org/)

---

### Post by mrjava on 2012-12-27
What you do with it depends on how old the hardware is. I have a 2002 desktop computer that was designed for Windows XP, now running Ubuntu 12.04...and it's speed is comparable to a Win7 laptop my brother owns, that has 50% higher processing power. Add to that a 500GB external drive...

For something well beyond the 10-12 year mark, data storage, especially for things like text files, etc, is a nice way to "recycle".

---

### Post by ArminasAnarchy on 2012-12-27
So I'm guessing there is a degree of consensus that any sort of Beowulf cluster is unworkable (or at least, I would be striking out into virgin territory if I attempted it - since I don't have much experience networking, this might be something a little challenging).

The computers are of varying ages - one's a relatively new Acer laptop (5470G I think, the only reason it was replaced was because of a) it's weight and b) the power supply port/jack was starting to become knackered). Another is a computer that I've only just been given, it's got 250GB harddrive, a pentium 3/4 and 1GB RAM. The other laptop is an AMD Turion, from around 2006/7. It was dropped and the screen is working but the backlight went - I've since found out it is possible to repair this, but at the time thought it was rendered worthless. Finding the charger for it might be challenging - does anyone have a work around they could suggest if I can't find it?
The final PC I'm pretty sure is ancient. Probably from around the year 2000, the motherboard has no built in ethernet/sound. The port again on the PSU is a little damaged, but i'm thinking if I'm VERY careful, it could be made safe.

In addition to that, I have a choice of making one of two computers the master node, were I to go down the Beowulf route. One is a custom build, running W7 Ultimate x64 for gaming. The other is my main computer - a laptop bought in Sept, running A8 CPU/GPU thing. Since I can do pretty much all the tasks I require on this computer, I'd decide to the beowulf for one of two reasons:

1) The hell of it - having all that power is VERY appealing :D
2) To improve the gaming ability (I don't do any other especially processor intensive tasks, and the 9800GTX in the gaming rig is starting to show it's age, even if the Q6600 (overclocked to 3.2GHz) is still running fine.

I'm sure I'd be more than able to think of uses for a server, but I think that would just involve upgrading and possibly RAIDing the HDDs on the newer of the 2 towers. I've heard unless multiple computers are accessing it at the same time, things should be fine, even with basically no processing power.

---

### Post by mystmaiden on 2012-12-27
I've had a lot of fun playing with Puppy linux retro versions and older hardware - then after I am finished makin them all snazzy, I either use them for file storage or give them away. Theres always the option I think you mentioned - takin' them apart. I have boxes of stuff sitting around from dismantling computers just cause I can. Its amazing how often this or that will come in useful.

---

### Post by lykwydchykyn on 2012-12-28
I was interested in setting up a cluster once, but after reading up on it a bit it seemed like the kind of thing that would take a lot of effort, trial and error, and research to get going; with a final result that would be more of a curiosity than an actually useful thing.  I can't speak with absolute authority, but my limited understanding of clusters is that it isn't the kind of power that translates into gaming performance.

I play with a lot of old hardware, and to me "ancient" means a turbo button and a 5 1/4" floppy.  With the right Linux distro just about any of those machines could be a serviceable workstation for somebody.  Remove the broken LCD from the laptop and connect it to a spare monitor or TV.  

As for servers: home servers don't need RAID.  I've run a home server for years (currently using an old beige box P4 running debian) without RAID; just keep a good regular backup.  It does Squid/Dansguardian for two desktops, LAMP applications, Samba, CUPS, and a few other things, and we can have as many as five or six systems going at once in our house (I got a lot of kids).

---

### Post by Bucky Ball on 2012-12-28
I have a P4 CPU with 1Gb of RAM running Xubuntu 12.04 faultlessly. It is about ten years old ...

Just throwing that in ...

I'd experiment with each one and see what's possible. You might try that with a minimal install and use a lightweight desktop environment.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by mamamia88 on 2012-12-28
or you could donate them to people who can make use of them. better then letting them collect dust and you feel good about yourself

---

### Post by VinDSL on 2012-12-28
> **Bucky Ball said:**
> I have a P4 CPU with 1Gb of RAM...

It is about ten years old ...

Just throwing that in ...
Bwahahahaha!  Me too!  Look at my sig!  :D

I use it to test dev releases...

```

vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~" && echo -n "Current Date/Time: " && date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Xserver Xorg Core Branch:" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo  && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 12.12.06 (vindsl.com) ~
Current Date/Time: Fri Dec 28 00:32:54 MST 2012
[B][COLOR="Red"]Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.8.0-030800rc1-generic
Gnome Release: GNOME Shell 3.7.3
Unity Release: unity 6.6.0[/COLOR][/B]

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 106
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2+edgers
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

Xserver Xorg Core Branch:
  Installed: 2:1.13.0.902+git20121207+server-1.13-branch.ede07c1a-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (339x271 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

---

### Post by ArminasAnarchy on 2012-12-28
> **lykwydchykyn said:**
> As for servers: home servers don't need RAID.  I've run a home server for years (currently using an old beige box P4 running debian) without RAID; just keep a good regular backup.  It does Squid/Dansguardian for two desktops, LAMP applications, Samba, CUPS, and a few other things, and we can have as many as five or six systems going at once in our house (I got a lot of kids).

RAID meaning RAID 1 rather than RAID 0/software RAID. It would just mean that the backing up would be automatic :P

Squid/Dansguardian? LAMP? Samba? Cups is something to do with printing, right?

At home at the moment, there's me (when I'm home from University), my sister (in the same position), two younger siblings (each using different computers - things I've had that were originally running Windows and have been given a new lease of life through Linux), my Mam using an old laptop, and her husband with a work laptop, and a tablet. I've got a tablet as well as a laptop too. It sounds like we're in relatively similar positions in terms of hardware needs. There's occasionally family visiting, game consoles etc.

---

### Post by lykwydchykyn on 2012-12-28
> **ArminasAnarchy said:**
> RAID meaning RAID 1 rather than RAID 0/software RAID. It would just mean that the backing up would be automatic :P

Be careful with that mindset.  You'd be better off putting one of those other machines in another part of the house and pulling a copy of the server over the network each night.  What happens if the motherboard or power supply goes wrong in your server and blows all the HDDs in the machine?  What happens if you accidentally delete a file?  A real backup saves you from more than just bad sectors.

> 
Squid/Dansguardian? LAMP? Samba? Cups is something to do with printing, right?

Squid/Dansguardian is internet filtering for the kids' computers.
LAMP means web applications.  I have several going, some from the repos, some custom-written.
Samba is file sharing.
CUPS is printer sharing.

Anyway, the point of listing these was to show that even a P4 with IDE hard drives can handle running many services for a house full of people.

> 
At home at the moment, there's me (when I'm home from University), my sister (in the same position), two younger siblings (each using different computers - things I've had that were originally running Windows and have been given a new lease of life through Linux), my Mam using an old laptop, and her husband with a work laptop, and a tablet. I've got a tablet as well as a laptop too. It sounds like we're in relatively similar positions in terms of hardware needs. There's occasionally family visiting, game consoles etc.

What would you want your server to do for all of them?

---

### Post by Rickubun2 on 2012-12-28
I have two old IBMs at home:


  IBM  5150 with 16 KB RAM and no floppy disk units (we used cassettes to load & store programs back in those days)  



  IBM PS/1  with a 486 processor integrated into the motherboard. 2.5 MB RAM and 250 MB HD running Windows 3.1 and MS-DOS 6.2.


  I guess all I can do with them is keep them stored for display (if I ever start my own PC museum)

---

### Post by Gremlinzzz on 2012-12-28
:popcorn:oldest computer i own
Upgrade Options for your SONY VAIO-PCG-9201:
Computer Info
CPU:	Intel Pentium III 750MHz
Memory Type:	PC100 100MHz SDRAM
Standard Memory:	64MB, 128MB (removable)
Max Memory:	256MB
Memory Expansion Slots:	2 Sockets
Memory Size:	144 pin
PC Card Slots:	Two Type I,II or One Type III PC Card Slot - 16/32-bit CardBus
USB Ports:	Two USB 1.1 Compliant Ports
Firewire Ports:	One 4-pin IEEE-1394 Firewire / I.Link Port
Card Reader:	None
Original Hard Drive(s):	6.0GB, 10.0GB, 15.0GB, 20.0GB 4200RPM ATA
Original Optical Drives:	24X CD-ROM , DVD-ROM

sold with Windows 98 second Edition

---

### Post by mörgæs on 2013-01-04
A cluster only works well if it's built on computers of more or less same performance. Don't mix significantly different hardware. 

Also consider the power consumption in a cluster, which can be high. Best is to measure the actual current (be aware of the initial spike) for each unit separately, as one should not trust the markings on the hardware. After that you can calculate how much it costs to run such a setup for a year.

This often leaves 'install a [light distro]("http://ubuntuforums.org/showthread.php?t=1582027") and sell or give for charity' as the best option. Also a nice way of promoting Buntu.

---

### Post by Bucky Ball on 2013-01-04
*Thread moved to** Hardware***

... as I probably should have done in the first place. This is really a support question and the ***Community Cafe*** is not about support questions. Cheers. ;)

---

### Post by Fahim Abdun-Nur on 2013-01-04
Hmm...time to dig up the old IBM Ambra Ispirati :-)

---

### Post by ArminasAnarchy on 2013-01-07
> **lykwydchykyn said:**
> Be careful with that mindset.  You'd be better off putting one of those other machines in another part of the house and pulling a copy of the server over the network each night.  What happens if the motherboard or power supply goes wrong in your server and blows all the HDDs in the machine?  What happens if you accidentally delete a file?  A real backup saves you from more than just bad sectors.


As a rule, anything important is sym-linked into my Dropbox folder (to ensure I can't forget to update something, and since it's backed up online, even something like a house-fire can't cause catastrophic data loss. I know it's not perfect, but it's probably as good as I'm going to get (reliance on Dropbox aside). RAID would really be for convenience - rather than having to download any uploaded data, there'd be another image instantly available, settings and any installed software included.

> **lykwydchykyn said:**
> 
Anyway, the point of listing these was to show that even a P4 with IDE hard drives can handle running many services for a house full of people.
What would you want your server to do for all of them?

I suppose the priorities would be: printing, email, files (music&photos in particular). If it were possible, it might be interesting to set the computer up to act as a form of router - being able to connect all the computers to the server, and then have the server anonymise all traffic via something like Tor would be cool. I'd have to do a bit of research around teaching myself networking, but if I could pull it off that it would save having to set it up with every device in the house - which is particularly troublesome with something like a games console.

> **mörgæs said:**
> A cluster only works well if it's built on  computers of more or less same performance. Don't mix significantly  different hardware. 

Also consider the power consumption in a cluster, which can be high.  Best is to measure the actual current (be aware of the initial spike)  for each unit separately, as one should not trust the markings on the  hardware. After that you can calculate how much it costs to run such a  setup for a year.

This often leaves 'install a [light distro]("http://ubuntuforums.org/showthread.php?t=1582027") and sell or give for charity' as the best option. Also a nice way of promoting Buntu.

Yeah, honestly, the more I think about the cluster idea, the more troublesome it becomes. I'm starting to think it's more trouble than it's worth, I think what I might do is freecycle/donate to charity/tinker with most of the hardware, and keep one machine back for establishment of a server.

> **Bucky Ball said:**
> *Thread moved to** Hardware***

... as I probably should have done in the first place. This is really a support question and the ***Community Cafe*** is not about support questions. Cheers. :wink:

Apologies for this - I'd disagree it's support I'm looking for exactly. More than anything else, I was interested in canvassing opinion and having a general discussion - hence I figured the Cafe would be appropriate. It can't really be support since support is fixing issues you've encountered - since this is all hypothetical at the moment, obviously I can't have encountered issues! But point taken none the less. :)

---

### Post by Yellow Pasque on 2013-01-07
I think the problem with older hardware is its efficiency (performance/watt). Just because you have an old P4 on hand doesn't mean you should press it into service for folding, especially in warm weather when you're running AC. The Northwood P4's weren't too bad, but the Prescott P4's were terrible.

The Acer laptop sounds the most promising. Open that baby up and fix the power jack. As for the other stuff, recycle/donate it.

---

