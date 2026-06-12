---
title: "Logitech QuickCam Pro 9000"
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by dynacrylic on 2008-03-28
I'm considering buying the Logitech QuickCam Pro 9000 as I canceled my landline and plan to use Skype and Ekiga. I looked in the supported list and saw that the 9000 is supported for Skype, but I'm curious about how people like it?

If not the 9000, what else would you recommend (and it doesn't have to be Logitech)?

thanks

---

### Post by mal on 2008-03-28
I recently purchased a Logitech Quickcam Communicator STX and it worked with Gutsy and Skype 2.0.0.63.  I also have a Quickcam 9000 for my work computer and when I tried it at home on my Gutsy machine, it seemed to work with Skype, but not with any other applications, like Ekiga, xawtv, Camerama, etc.  I haven't tried to figure out what the problem was.

Regards,

Mal

---

### Post by simplejordon on 2008-03-30
I am definitely keen if it has any extra functionalities over logitech quickCam communicate STX webcam, if any...and do I need to install any extra drivers to get it run with my [http://www.rhubcom.com]("http://www.rhubcom.com") turbomeeting.  Looking forward to some reviews..

---

### Post by ridgeland on 2008-04-01
I bought a Pro9000 because I saw on the web that it "Just Works".  It didn't work.  I could not get it to work with 7.04.  With 7.10 in Kopete it starts up then the image breaks up.  This in on a Dell-Ubuntu PC.
I installed 8.04alpha6 on my old Gateway and the Pro9000 worked right from the start.  I used Skype to talk to a niece overseas.  Great problem solved.  I ordered a second Pro9000 because I'm setting the Gateway up for my Mom to use (1600 km away).
Went back to the Dell and with 8.04 the Pro9000 still does not work.  It starts with Skype or Kopete then loses it, lots of scrambled lines.   Ekiga works but with a very low resolution.  But... with the Dell and SuSE 10.3 it works great!
So on my Dell-Ubuntu I'll keep SuSE 10.3 on one partition so I can use Skype.  Yeah for multi-boot!

---

### Post by dynacrylic on 2008-04-03
Wonderful, I'm holding off for the official 8.04. Hopefully I'll have a cam by then.

---

### Post by dartnall on 2008-05-19
Just upgraded fron gutsy to hardy and bought a logitech quick cam pro 9000 for use with skype (grandkids in Africa). Downloaded source code, compiled and installed uvcvideo module, and it only works intermittently...
Shows a good consistent image with luvcview, nithing with camstream and a picture sometimes using cheese. Skype is not successful either!
Has anyone any ideas on where I could go from here?
People seem to be having similar problems but I haven't yet found a definite answer.

---

### Post by ridgeland on 2008-05-19
Hi dartnall,
I got the web cam working in Ubuntu by editing the Skype configuration file.
$ gedit /home/myusername/.Skype/myskypename/config.xml
edit (copy and replace original <Video> section)
    <Video> 
      <AutoSend>1</AutoSend> 
      <CaptureHeight>120</CaptureHeight> 
      <CaptureWidth>160</CaptureWidth> 
      <Fps>8</Fps> 
    </Video>
Without this the image starts and breaks up.  Be sure to have the webcam connected when you first install Ubuntu.  This is for 7.10 and 8.04.  With 7.04 a lot more has to be done.
I installed Ubuntu 8.04 on this 2007 Dell-Linux PC (specs below) and on a 2002 Gateway single core PC.  On the Gateway Skype works with 320x240 resolution in Ubuntu 8.04, no tweaks needed just install and play.  With this Dell+Ubuntu Skype breaks up if not forced to 160x120 as above.  With SuSE Skype starts at 320x240 then freaks a little and switches to 160x120 and continues.
My solution was keep Ubuntu 8.04 on the Gateway.  But for the Dell I settled on Mandriva 2008.1.  It works with Skype at 320x240 with no tweaks.
If you have Linux you should be able to multi-boot.  I have several Ubuntus, SuSE, Fedoras and Mandriva.
I'm taking the Gateway to my Mom in June (1000 miles from here).  She will use Ubuntu 8.04, I'll use Mandriva 2008.1.  Her granddaughter overseas is using Windows.  All Skype.

First step - try the above edit then see if Skype works.  Post back and I'll try to help you.

---

### Post by vaibshah on 2008-06-18
Hello!

How could you get your QuickCam 9000 get to work with Skype 2.

I am a novice working on Ubuntu 6.06, and my skype installation doesn't work. It shows an error about some dependency libasound2.

What to do?

Would be great to have your help.


Thanks ahead!

> **mal said:**
> I recently purchased a Logitech Quickcam Communicator STX and it worked with Gutsy and Skype 2.0.0.63.  I also have a Quickcam 9000 for my work computer and when I tried it at home on my Gutsy machine, it seemed to work with Skype, but not with any other applications, like Ekiga, xawtv, Camerama, etc.  I haven't tried to figure out what the problem was.

Regards,

Mal

---

### Post by ridgeland on 2008-06-18
Hi vaibshah
My suggestion is Multi-Boot.  Free up enough space for another partition and install another Linux version there.  Plug in the camera then install Mandriva 2008.1 or Ubuntu 8.04 or SuSE 10.3.  For me all three worked with Skype + QuickCam Pro 9000 right from the start, nothing hard about it.

Keep your 6.06 just as it is.  Just add another Linux to your PC.

After months of trying everything to get Skype to work on Ubuntu 7.04 it did but I now have no idea what were the steps that helped and what was just noise.

---

### Post by vaibshah on 2008-06-18
Hi!
Thanks for the suggestion! I am now talking with my vendor (right now) and he says that the application we need (EMC2 from [http://www.linuxcnc.org](http://www.linuxcnc.org)) to use (along with the working camera) needs to communicate in Real-time with kernel, and that was available so far with version 6.06. But as per the latest info, they have just launched their application for 8.04 also.

But I am not sure how would I get to do partition. Unless, you help me for that, step by step! :)

I would appreciate this a lot.

Thanks a lot!

Vaibhav
  

> **ridgeland said:**
> Hi vaibshah
My suggestion is Multi-Boot.  Free up enough space for another partition and install another Linux version there.  Plug in the camera then install Mandriva 2008.1 or Ubuntu 8.04 or SuSE 10.3.  For me all three worked with Skype + QuickCam Pro 9000 right from the start, nothing hard about it.

Keep your 6.06 just as it is.  Just add another Linux to your PC.

After months of trying everything to get Skype to work on Ubuntu 7.04 it did but I now have no idea what were the steps that helped and what was just noise.

---

### Post by ridgeland on 2008-06-18
Hi vaibshah,
What capacity is your hard drive?  
Multiple hard drives?
Can you download and burn CDs?

---

### Post by vaibshah on 2008-06-18
Well I have around 64 GB free, and I use only one harddrive. 
Yes, I can download and burn CDs. Can you give me the link, and steps. Also, can I do this (downloading and burning CDs) on the same machine which I want to upgrade, and run the setup while the 6.06 is running or I need to format the harddrive?

> **ridgeland said:**
> Hi vaibshah,
What capacity is your hard drive?  
Multiple hard drives?
Can you download and burn CDs?

---

### Post by ridgeland on 2008-06-18
Sorry ... gotta run
I'll be back in about 6 to 8 hours.
Download System Rescue CD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
I'll help you when I get back.

---

### Post by vaibshah on 2008-06-18
No Problems!

I already started downloading the ISO for 8.04 from the developers of EMC program which I need to work with the machines.

So, if this goes well, I should be getting my computers working well by the night. :)

Do you know if I should format the harddisk before installing 8.04 or it will do all the necessary stuff automatically?

Thanks. 
> **ridgeland said:**
> Sorry ... gotta run
I'll be back in about 6 to 8 hours.
Download System Rescue CD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
I'll help you when I get back.

---

### Post by ridgeland on 2008-06-18
Hi Vaibhav,

Back again.

Here is where I was heading:

1 - Use SystemRescueCD to partition the hard-drive, resize existing partitions and define number of partitions and sizes.
With 64 GB I recommend 4 OS partitions of 8-10 GB each and the rest in a single partition to share (/Data for /Data/Music, /Data/Photos, /Data/Internet/bookmarks etc)
2 - Download Ubuntu 8.04
3 - Install Ubuntu 8.04 on one of the four of the newly created OS partitions.
4 - Download and install Mandriva 2008.1
5 - Download and install SuSE 11 (I haven't yet)

Here is my view of partitioning:
One partition for each OS to include: /root, /boot, /home
One large shared partition for /Data - to hold all the music, photos etc that are totally OS independent.
I use a shared partition to also hold Thunderbird and the bookmarks for Firefox.

I've seen lots of posts that say "I upgraded my Linux to a new level and now I'm screwed, the new level doesn't work and I cannot go back to the old level"

My approach is to always install the new Linux OS in a fresh partition and keep my favorite Linux OS out of danger.  This has been my approach going from Fedora Core 4 to FC6 to SuSE 10.1 to Ubuntu 7.04 to Mandriva 2008.1  I've tried twenty other versions and OSes in between, but always clung to one stable reliable OS until the new one totally lured me in.

So details on how to partition in SystemRescueCD.
Burn the CD and boot it.  When it boots wait out options like keyboard and let it default.  When it gets to the prompt "%" I think then start the GUI with % startx.  In the GUI launch gparted, an icon on the right side.  In gparted you can resize partitions to free up some space and then create new partitions.  Partitions 1 to 4 are primary, 5-15 are extended.  Set 1 to 3 as needed.  Set 4 to be all that is left.  Then set 5 to 15 to be a sub-set of partition 4.  I'll say that again.  Maybe it's legacy from the world of DOS but you can only have 4 primary partitions.  You can sub-divide a primary partition.  Linux can only see 15 partitions max.  So for example on my PC partitions 1 to 3 are 10 GB.  Partition 4 is 240 GB.  Partitions 5 to 14 are 10 GB partition 15 is all thats left.  Partitions 5 to 14 are all a sub-partition of partition 4.

Think through it.  Any questions?

Assumptions: you have 512MB or more of RAM.  You make good backups of everything that you would cry about losing.  You don't have Vista.

---

### Post by vaibshah on 2008-06-19
Hi ridgeland!

Thanks a lot for your very descriptive message. I appreciate this a lot. I also believe in this kind of messaging, but unfortunately, not always I get this.

Ok, about the upgradation!
Yesterday, after sending that message to you, I started downloading the ISO from the [www.linuxcnc.org](www.linuxcnc.org) which also gives the simulator for machine controller so it was an obviously preferred OS source for me.
And, I selected the option to install the new OS on the complete disk, removing older version and not creating any partition. 

Well, I took a backup of my old data before doing this, but yes, I missed to take those bookmarks. Infact, I due to the work pressure, I didn't think a lot and didn't take the precautions which I usually take while upgrading my windows system.

Do you think if I am able to create partitions next time I install any other OS that you've mentioned, while maintaining this one and the data? Right now I have the OS on just one HDD, without any partitions.

Anyways, if we go ahead from this point, I tried to connect my QuickCam 9000 camera with this upgraded version of OS, and it still doesn't do anything. So, it doesn't play just by plugging in.

Any suggestions?

Thanks again!

---

### Post by ridgeland on 2008-06-19
Now you've reformatted the whole hard drive and installed something other than Ubuntu.  Since this did not work I would:
Download Ubuntu 8.04 (not something that says it's based on Ubuntu)
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Delete the newly installed OS by using SystemRescueCD.  In SystemRescueCD use startx then gparted to delete the existing partition.  Create three 8GB primary partitions of type ext3 then 1 extended partition of all that remains.  Then click [Apply].  Once OK then split the extended partition into another 8GB partition, a 1GB partition of type linux-swap, then all the rest for a Data partition.
Then install Ubuntu 8.04 on the first partition.

---

### Post by ridgeland on 2008-06-19
Reading better I see:
EMC2 is a software system for computer control of machine tools such as milling machines, cutting machines, robots, hexapods, etc.
So you are using this PC to control factory equipment?
Even so you can have multiple partitions.  One where CNC works but not the web cam.  One where the web cam works but not the CNC. Another where you experiment to get both working at the same time.

---

### Post by vaibshah on 2008-06-19
Hi!
I would need something of that third type. Because, I must have the CNC and webcam working at the same time.

I lost a lot of time getting this webcam work with my ubuntu 6.06 and now, I am just sitting on the deadline, so will not experiment more, and will make the application without the webcam, but will continue with this approach as you said, of multiple partitions and experimenting with them once I am done with my current tasks. Because, for now, I must get the CNC machines working (using that EMC program) and that's more critical. Just trying to figure out which options to select to get it working.

> **ridgeland said:**
> Reading better I see:
EMC2 is a software system for computer control of machine tools such as milling machines, cutting machines, robots, hexapods, etc.
So you are using this PC to control factory equipment?
Even so you can have multiple partitions.  One where CNC works but not the web cam.  One where the web cam works but not the CNC. Another where you experiment to get both working at the same time.

---

