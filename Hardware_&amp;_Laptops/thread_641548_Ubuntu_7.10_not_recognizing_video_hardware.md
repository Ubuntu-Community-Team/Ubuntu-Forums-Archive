---
title: "Ubuntu 7.10 not recognizing video hardware"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by basil787stag on 2007-12-15
Hello,

I have a newly-bought Sony VGN-NR180E (notebook), with Vista HP on it. I recently made it a dual-boot Vista + Ubuntu, but Ubuntu's not properly recognizing my video adapter!

Okay, so when i hit the start-up button,  i see the normal loading screen, and then there's like a green bar at the top of the screen, and then a pop-up tells me that Ubuntu is running in low-graphics mode because it didn't detect my monitor or video card properly. I continued like that and i tried to set the drivers under the Display tab (i forgot what it was called, but it was under administrative options) thing to the Intel 965 chipset (i have an x3100 GMA). Ubuntu told me that i had to log off for the settings to take effect, so I did. Then i get the weird green bar thing again, plus some other random stuff, and then ubuntu goes on to tell me its running in low graphics mode and i have to hit the configure button, so I do... then it goes to the log-on and then i go through the entire process again, with the same result. I've tried restarting, shutting down, then turning back on, and all the other usual stuff. But noo, Ubuntu won't recognize it. I searched all over and everyone's problems seem to be with expanded monitors or with desktops that have actual video cards.

So, my problems:
Ubuntu won't recognize driver/card/monitor
resolution wont go above 640 x some number i can't remember
Frustrated beyond belief...

Laptop:
2 gigs pc-5300 667 RAM
200 GB HDD 4200 rpm (sliced & diced into several partitions)
15.4" Widescreen x-brite eco monitor
intel GMA x3100
Vista HP/Ubuntu

please help!! :(

---

### Post by birdywa on 2007-12-17
I am having the same problem as well. My resolution is st right, but everything else is the same. The screen manager keeps reverting back to generic VESA driver or some crap no matter what I do. No 3d apps work at all. this is very frustrating. From what I understand, this is a fairly common graphics card, so this should be top priority for you ubuntu people i you want linux mainstream. Ridiculous problems like this that can't be solved without going to a forum are what ruins linux for a lot of people.

---

### Post by deadowl on 2007-12-18
I've had this problem, but not to the degree that it takes me into reduced graphics mode (at which point it doesn't give an easy means of configuration).

My problems lie in i810 vs intel and bcm43xx vs ndiswrapper

Anyways, I would think that you want the xorg-video-intel driver.

On the command line, type:
sudo dpkg-reconfigure xserver-xorg

Attempt to autodetect video hardware? NO
Pick intel from that list
If the video card doesn't have its own memory, you'll need to assign it some at some point in the rest of the process. Generally you want to look at the specifications for how much memory is recommended and then convert it to that amount in kb.

Other than that, it should be pretty much straight forward.

---

### Post by basil787stag on 2007-12-18
Yeah, I tried all that, and it still didn't work!!

But here's what i did to fix it:

I found out that my core2duo T5250 was x86 64-bit, so i decided to simply uninstall the 32-bit version that I had currently installed (more info on that later), and install the 64-bit version. Took me half an hour, and now the driver's set as intel experimental modesetter, but hey the stuff works at the right resolution... and it just works. Now, on to getting Compiz support. =D

My process of uninstalling Ubuntu:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

I used the EasyBCD method, since its labeled as applying to Vista users. The process is quite easy, but make sure you read all the instructions and understand them before going on with it. As with any major disk operation, back up your files and stuff, just in case you accidentally delete your windows partition or something crazy like that.

Thanks!

---

### Post by deadowl on 2007-12-18
Quick question: Does your resolution still stretch when you set it to a resolution with a different aspect ratio?

I've found that on my computer, I can get the Windows driver configured to maintain the aspect ratio of an intel 945GM (which it is by default), but not with Linux. The video bios only lists stretched and standard (where the resolution doesn't stretch to any edge of the screen). The Windows option of maintain aspect ratio will maximize the amount of space used while maintaining aspect ratio. This is by far the most preferable option. Setting it to that in Windows will set the video bios to stretched mode.

Of course, I have had some fairly ugly problems with the intel driver in terms of suspend/resume (it might be time to try using again though). Hibernate has hated me whether or not I use i810 or intel.

So yea, I guess I'll test the intel driver while uninstalling 915resolution again, and then get back to this thread.

...Okay, so that turned out quite nicely. If you're answer to my initial question is yes, then could you send me your xorg file so I can use it as a basis to reconfigure mine?

---

### Post by basil787stag on 2007-12-19
Uh, even if i knew how to open my xorg file, or knew what it was, It wouldn't be of much use. I think you said you were on a 945GMA chipset, i'm using a 965GMA chipset. 

i haven't tried resizing my resolution because i have no need to.. its set as i want it by default.

---

### Post by birdywa on 2007-12-22
You people still haven't fixed my problem. It has actually gotten worse. No matter what driver I select, when I restart X, it goes back to Intel experimental and the only resolution available is 640x480. I have searched the forums and only come up with useless answers and others with problems not fixed. If I cant fix this, I'm switching to a distro where I don't have these ridiculous problems. I shouldn't have to reconfigure X when the driver is listed right there! This gutsy "upgrade" has been anything but an upgrade.

---

### Post by basil787stag on 2007-12-22
What are your computer specs? Theres more factors to this than just the graphics card.

I gave you my solution, so don't expect me to provide you with a solution to your problem, when I haven't any information to go on. 

Btw, I agree that you shouldn't have to change your xorg file. I didn't.

---

### Post by birdywa on 2007-12-25
I have a thinkpad R61i with 2 gigs of ram. Not much else to say that could affect the problem.

---

