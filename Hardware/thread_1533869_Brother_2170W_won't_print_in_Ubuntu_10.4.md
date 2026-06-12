---
title: "Brother 2170W won't print in Ubuntu 10.4"
date: 2010-07-18
forum: Hardware
---

### Post by tinmanic on 2010-07-18
I cannot get my Brother 2170W printer to print, except for two random successes a couple of hours ago when I was able to print a test page and another one-page document, although each of them took forever to print.  Now I can't print anything at all.  I've Googled and I've searched the Ubuntu forums and I've tried various suggestions I've seen online, and nothing is working.

I'll try to list as much information as I can.

(1) I'm pretty new to Linux.

(2) I have Ubuntu installed on my Windows XP machine via the wubi installer.

(3) I can print wirelessly just fine via Windows.

(4) I've updated my printer with the latest firmware.

(5) I've followed a suggestion at [http://www.lwp.ca/james/2010/06/installing-brother-hl-2170w-laser-printer-on-ubuntu/](http://www.lwp.ca/james/2010/06/installing-brother-hl-2170w-laser-printer-on-ubuntu/) I downloaded cupswrapperHL2170W-2.0.2-1.i386.deb and brhl2170wlpr-2.0.2-1.i386.deb and entered the terminal commands he suggests.  No success.

(6) I've deleted and re-installed the printer numerous times.  Ubuntu can detect the printer wirelessly -- it just won't print.

(7) Document Print Status (my jobs) in the top panel lists several attempted print jobs and they all say "Processing."

Nothing is working.  I'm pretty frustrated.  Any help would be greatly appreciated.

---

### Post by tinmanic on 2010-07-18
So far I have received no responses to this question.  I'd really appreciate it if someone could help me out.  Thanks.

---

### Post by tinmanic on 2010-07-19
Hi all.  It would be really helpful if someone could help me out here.  I thought that's what the Ubuntu forums were for.  Thanks.

---

### Post by Mid West Kevin on 2010-07-19
Hey; I'm new here, and Ubuntu.  My focus is using Ubuntu with Citrix and HP printers.  The site has been very useful and feedback is positive.  The experts may be on vacation it is July.   So let's see if I'm missing some information.
 
Have you tried both Wireless and USB setups?  It sounds like you have setup the printer as a Wireless?  Have you tried setting it up as a USB printer?  I'm thinking if it works with the USB setup, then you can isolate the problem to the Wireless setup. 
 
I'll try to watch this post and help the best I can.
 
Kevin

---

### Post by tinmanic on 2010-07-19
Thanks Kevin.  I'll give that a try tonight and see if it works.

---

### Post by Mid West Kevin on 2010-07-19
I found this link at the Brothers site.  
[FONT=Calibri][SIZE=2][http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00091](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00091)[/SIZE][/FONT]
 
Your problem may get more reponses there, if you haven't already posted there.

---

### Post by tinmanic on 2010-07-19
OK, I connected the printer via USB, and it did print something, but it took several minutes before it finally printed a page!  And then several minutes went by and it printed a second page, and then a few more minutes and then a third page, and then a couple of minutes and the last page.  But... I only requested it to print the first page, not all four.

So: wireless still isn't working; with USB it takes forever to print just one page; and I asked it to print just the first page but it printed four.

I also tried following the directions on that Brother link you posted.  I opened the terminal and typed:

sudo dpkg -P cupswrapperHL2170W-2.0.2-1.i386.deb

And the response I got was:

"dpkg: you must specify packages by their own names, not by quoting the names of the files they come in"

What does that mean?

Then I followed the next step -- I typed:

mkdir /usr/share/cups/model

And the response was:

"cannot create directory '/usr/share/cups/model': File exists"

I guess that's because I already created that directory by following the instructions here: [http://www.lwp.ca/james/2010/06/installing-brother-hl-2170w-laser-printer-on-ubuntu/](http://www.lwp.ca/james/2010/06/installing-brother-hl-2170w-laser-printer-on-ubuntu/)

Right?

I am totally confused as to what's going on here!

---

### Post by Mid West Kevin on 2010-07-20
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Wow! There’s a lot going on here. [/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]I think starting with the small success of printing. So congratulations! [/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Questions that need to be answered:[/SIZE][/FONT][/FONT][/COLOR]
 
[FONT=Arial][SIZE=3][COLOR=black][FONT=Verdana]1.) [/FONT][/COLOR][COLOR=black][FONT=Verdana]Is it Possible that the extra print jobs came from the other attempts when you tried to print from the Wireless setup? Has the computer been turned on since those failed attempts? Maybe there old print jobs?[/FONT][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=3][COLOR=black][FONT=Verdana]2.) [/FONT][/COLOR][COLOR=black][FONT=Verdana]The long delays in your print cycle could be due to the computer’s hardware? It’s a guess. What are the specs of the computer you’re working with? RAM, Hard Drive space, Processor.[/FONT][/COLOR][/SIZE][/FONT]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Go to this web site and download this manual. [/SIZE][/FONT][[FONT=Arial][SIZE=3][COLOR=blue]http://www.ubuntupocketguide.com/index_main.html[/COLOR][/SIZE][/FONT]]("http://www.ubuntupocketguide.com/index_main.html")[FONT=Arial][SIZE=3] It goes thru a very nice tutorial and commands that will address your next questions.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]NOTE: Ubuntu is Case Sensitive so make sure you type the correct Case. A capital letter must be a capital letter.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Ubuntu as are all the Linux based OS is locked down tight. Hence it’s a Virus free environment. [/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]“SUDO” stands for “SuperUser DO”. It gives you rights to install and make changes, Read more at [/SIZE][/FONT][[FONT=Arial][SIZE=3][COLOR=blue]http://kb.iu.edu/data/amyi.html[/COLOR][/SIZE][/FONT]]("http://kb.iu.edu/data/amyi.html")[/FONT][/COLOR]
 
[FONT=Arial][SIZE=3][COLOR=black][FONT=Verdana]“DPKG” [/FONT][/COLOR][FONT=Verdana]Dpkg is the Ubuntu package manager. dpkg is a medium-level tool to install, build, remove and manage Ubuntu packages. The primary and more user-friendly front-end for dpkg is dselect.dpkg itself is controlled entirely via command line [FONT=Arial][SIZE=3][COLOR=black]parameters,which consist of exactly one action and zero or more options. The action-parameter tells dpkg what to do and options control the behavior of the action in some way. Read more at, [/COLOR][/SIZE][/FONT][[FONT=Arial][SIZE=3][COLOR=blue]http://www.ubuntugeek.com/reference-guideubuntu-package-management-using-dpkg.html[/COLOR][/SIZE][/FONT]]("http://www.ubuntugeek.com/reference-guideubuntu-package-management-using-dpkg.html")[/FONT][/SIZE][/FONT]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]“cupswrapperHL2170W-2.0.2-1.i386.deb” This package has to be downloaded from the Brothers site. Usually to the your desktop, and once the package is locally stored you’ll be able to run the command with better success.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]sudo dpkg -P cupswrapperHL2170W-2.0.2-1.i386.deb[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Your next problem is making a directory you used, mkdir /usr/share/cups/model that is incorrect for your user’s privileges.[/SIZE][/FONT][/FONT][/COLOR]
 
[FONT=Arial][SIZE=3][COLOR=black][FONT=Verdana]Inorder to use the command make-a-directory “mkdir” and you need to use the “sudo” to do this. You should type: sudo mkdir /usr/share/cups/model[/FONT][/COLOR][/SIZE][/FONT]
 
 
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]Go slow and read thru the references that are above. The Pocket Reference is a great read. I’m using Ubuntu 8.04 not 10.04 because is been around longer and its solid. The newer version tend to need more twicking, for the most part the commands are the same. [/SIZE][/FONT][/FONT][/COLOR]
 
[FONT=Arial][SIZE=3][COLOR=black][FONT=Verdana]I’ll get back to you on the wireless install. I’m currently working on installing Ubuntu / setting it up on a older laptop that I plan to use with a wireless card on. I’ll go thru and note the steps and see if they would be useful for your problem. There’s a utility “synaptic package manager”, this is another resource that will help to understand. [/FONT][/COLOR][/SIZE][/FONT]
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE]

---

### Post by Mid West Kevin on 2010-07-20
[FONT=Arial][SIZE=2]I found this link [/SIZE][/FONT][[FONT=Arial][SIZE=2][COLOR=#444444]http://www.linuxquestions.org/questi...driver-801845/[/COLOR][/SIZE][/FONT]]("http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-9-04-64bit-and-brother-dcp-7030-cannot-install-driver-801845/")
[FONT=Arial][SIZE=2]you can read thru it.  It appears the Brother printers are a bit of trouble, although they advertise them as being linux compatible.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Also in the previous post there is the .deb extension shown in the command line sudo dpkg -P cupswrapperHL2170W-2.0.2-1.i386.deb.  There are different file extension .deb is for debian.  You'll need to be aware of the differences and the commands used for these different file extension.  The Pocket Reference Guide talks about a few of them.  You'll better your understanding by researching them.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Be Patient with yourself and when posting.  A lot of the time people are here trying to figure out their own mess and don't have time to help.  Your problem is a bit complicated, so I suspect that's the reason for No responses.  It happens that I have some extra time right now, so I learn from reading the posts and trying to help.  [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]This is from Chuck Swindoll, it fits if you're stressing about stuff.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][LEFT]"Some things are better felt than telt," say our Scottish friends. And that is so true. Take insight, for example---that elusive weave of intuition, perception, alertness, and sensitivity. You just can't teach it. You can, however, nurture it. You can even expand it. But there's no one-two-three process that suddenly makes one insightful. Yet insight is essential in things like teaching or counseling or writing. When insight is present, those skills literally come alive. Insight makes the simple profound and the difficult understandable. Those who have it were not taught it; they caught it. From God.
 
Somethings you need to give away before you get it. [/LEFT]
[/SIZE][/FONT][FONT=Arial]
[SIZE=2][/SIZE][/FONT]
[COLOR=black][/COLOR]

---

### Post by tinmanic on 2010-07-20
Hi Kevin --

It was a unique print job; I tried printing something I hadn't tried before.  So the output could only have been a result of that particular printing attempt.

Here are my specs:
 
RAM: 1GB

Hard drive space: the hard drive actually has 60GB and I have a 300GB external drive, but Ubuntu is using 6GB that I dedicated to it via the wubi installer.

Processor: Pentium 4, 2.53GHz.

As far as the terminal -- I did a little reading and did put "sudo" before the relevant commands, but I think the problem was that I needed to remove the ".deb" at the end of the sudo dpkg command I quoted above.  Because after I did that, it seemed to delete it as requested.

I still can't print properly, though.

> &#8220;cupswrapperHL2170W-2.0.2-1.i386.deb&#8221; This package has to be downloaded from the Brothers site. Usually to the your desktop, and once the package is locally stored you&#8217;ll be able to run the command with better success.
 
sudo dpkg -P cupswrapperHL2170W-2.0.2-1.i386.deb

Actually, I had already downloaded that package to my desktop as suggested at this link: [http://www.lwp.ca/james/2010/06/installing-brother-hl-2170w-laser-printer-on-ubuntu/](http://www.lwp.ca/james/2010/06/installing-brother-hl-2170w-laser-printer-on-ubuntu/)

Isn't -P a "purge" command though?  i.e. a command to delete the file?

---

### Post by tinmanic on 2010-07-20
Just saw your newest post... I'll check that link out as well.  Thanks.

---

### Post by Mid West Kevin on 2010-07-20
Your computer specs are far better then what I'm using for a computer.  That's not the problem.
 
Yeah, don't use purge until you done with the packages.
 
Did you do the following using the Terminal from the <Applications><Accersories><Terminal>
 
cd ~/Desktop
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo ln -s /etc/init.d/cups /etc/init.d/lpd
sudo mkdir /var/spool/lpd
sudo dpkg  -i  --force-all brhl2170wlpr-2.0.2-1.i386.deb
sudo dpkg  -i  --force-all cupswrapperHL2170W-2.0.2-1.i386.deb
 
If I were you I stay with the idea of getting the USB working smoothly before moving to the wireless challenge
 
I'm still looking at my wireless install, so I can't add anything.

Its just another adventure

---

### Post by Mid West Kevin on 2010-07-20
**[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][SIZE=2]Take a look at this post, he did a nice job.[/SIZE][/FONT][/COLOR][/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][SIZE=2][/SIZE][/FONT][/COLOR][/FONT][/COLOR]** 
**[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][SIZE=2]HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies[/SIZE][/FONT][/COLOR][/FONT][/COLOR]**
**[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][SIZE=2][/SIZE][/FONT][/COLOR][/FONT][/COLOR]** 
**[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][[SIZE=2]http://ubuntuforums.org/showthread.php?t=590793&highlight=HOWTO%3A+Ubuntu+Brother+Printer+Scanner+Driver+Installation+Newbies[/SIZE]]("http://ubuntuforums.org/showthread.php?t=590793&highlight=HOWTO%3A+Ubuntu+Brother+Printer+Scanner+Driver+Installation+Newbies")[/FONT][/COLOR][/FONT][/COLOR]**

---

