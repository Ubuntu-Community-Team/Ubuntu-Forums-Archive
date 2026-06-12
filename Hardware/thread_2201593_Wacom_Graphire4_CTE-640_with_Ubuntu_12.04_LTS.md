---
title: "Wacom Graphire4 CTE-640 with Ubuntu 12.04 LTS"
date: 2014-01-25
forum: Hardware
---

### Post by captain_chaos2 on 2014-01-25
Hi I am running on an HP with Intel Pentium (R) 4 CPU 2.80GHz x2 with 1GB memory 120GB Disk and unknown on-board graphics. I run Blender 2.69, Gimp2.6, Inkscape and a number of CAM and CAD programs. I recently purchased a Wacom Graphire4 CTE-640 6x8 USB pen and tablet. The pen worked pretty good after configuring in Gimp and worked OK in Blender, but in the Wacom Graphics Tablet app setup the Map Buttons had an empty field. I tried " [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") " and some how messed something up. When I now go to the Wacom Graphics Tablet app it says "No tablet detected" and "Please plug in or turn on your Wacom tablet" when I do this the computer goes immediately into sleep mode and all I can do is turn off the machine and re start. If I boot up with the tablet plugged in, as soon as the desktop flashes up it goes into sleep mode. Any ideas? totally lost.

---

### Post by captain_chaos2 on 2014-01-27
OK tried a whole host of things, although I have been using Linux for about 3 years now I am still pretty much a novice, I tried updating, recovery mode, used an older Kernel and even removed all the Wacom packages but ended up backing up all my files and doing a complete reinstall. All back to normal and the pen is working.
 		 			  				

 		
 	

 		 			 				:confused: But still can't figure out how to get the Tablet buttons to work??:confused:

---

### Post by captain_chaos2 on 2014-01-28
OK no help here, I tried > [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562), Bamboo how to and followed it as religiously as my understanding could prevail, three days of googeling or should I say DuckDuckGoing and it seems as though Wacom treats the Graphire4 6X8 tablet as an orphan and Sourceforge seems never to have herd of it. Sooo back to yet another reinstall!! 

Thanks to those who took enough interest to view my thread.

---

### Post by mörgæs on 2014-01-28
Is the new install going to be 13.10?

---

### Post by captain_chaos2 on 2014-01-29
Hi Morgaes the reinstall is Ubuntu 12.04

Thanks for your interest I have been using Ubuntu linux for about three years now and definitely regard myself as an absolute beginner. I only got over my fear of terminal about a year ago. I have been running Linux CNC formally EMC2 on Ubuntu 10.04 as it supports Linux CNC. I set up 12.04 LTS on this computer to try to learn Linux as it was the newest long term support distro at the time and feel that if I keep jumping distros I am not likely to learn anything. I have set up and run programs on 12.04 in Python and Mono, albeit with a lot of hand holding.

Now I can run the Graphire4 on an equivalent old machine in Windows XP that hasn't seen the internet since service pack 2 and it runs perfectly. I have only just got it to run on Windows 7 with a huge amount of effort and a phone call to the local agents to get the latest driver, as their web site is a bit of a mess with 404 errors, on my latest all singing all dancing computer. Once I get a little more confident with Linux I will install a second hard drive on this computer with Ubuntu as I can't afford to wreck my MS 7 just yet.

---

### Post by mörgæs on 2014-01-29
I meant that if you after repeated reinstalls of an old version still have problems there's a good reason to try 13.10. If you have space for a new partition you could have the two releases side by side so you don't have to abandon 12.04.

---

### Post by captain_chaos2 on 2014-01-29
Great Idea, I actually have a 165GB hard drive with 10GB Fat32 and 35GB unallocated, so I will try and set up a separate root partition for 13.10. Wish me luck as step out of my comfort zone.

I checked out "**Quick Links -> Unanswered Posts"** as suggested but couldn't find anything there unfortunately.

---

### Post by captain_chaos2 on 2014-01-30
OK finally got 13.10 loaded not much configure-ability for the pad so looks like I will have to unfortunately stick with Windows 7 till Wacom wake up to the growing relevance of Ubuntu.

 For some reason when I downloaded 13.10, checked mirror with winMd5sum and burnt the Iso file on windows7 as I have in the past the Iso bombed out my Ubuntu 12.04 with a Grub Error 2. 
As I could not understand the reason for this after googling around for some hours I decided to reinstall 12.04 and attempted another install of 13.10 and it bombed again same error.

I then checked the 13.10 iso disc with winMd5sum and that checked out, I then went back to the download page to see if I had done something wrong only to find they recommend Infranview to burn the disk :confused::confused: so I downloaded and burnt the Iso on a new disc with Infranview and it worked perfectly:biggrin:

What I can't work out is why the mirror checked out with the downloaded Iso file and the the disc burnt with Windows DVD maker or something like that gave an error, yet burning the same file to a new disc with Infranview worked perfectly? 
Surely if the mirror checks out on the _disk_ the disck should be good.  Any way just another 8 hours in a noobs day, still learning.

---

