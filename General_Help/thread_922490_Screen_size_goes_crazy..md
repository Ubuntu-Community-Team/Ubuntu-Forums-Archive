---
title: "Screen size goes crazy."
date: 2008-09-17
forum: General Help
---

### Post by jerlinux on 2008-09-17
I was reading an email with evolution ubuntu 8.04 when suddenly the screen wanted to be 6 foot high by 6 inches wide.

I have moved the ubuntu hard drive into other machines and gotten the same screen.  It is impossible to see the upper task bar and you have to guess at the turn off computer button.

Anybody ever seen anything like this before?

And before I give up and reinstall, is there some way to back up all the email addresses etc before I throw my arms in the air?

Thanks

---

### Post by Infinite Indefinite on 2008-09-17
Check your xorg.conf

**sudo gedit /etc/X11/xorg.conf**

Maybe the screen resolutions are off.  (Check sections such as Section "Monitor", Section "Screen", Section "screen" and Section "monitor".)

---

### Post by jerlinux on 2008-09-18
I have found this:

Section Monitor
        Identifier         Generic Monitor
        Option             DPMS
        Horizsync          28-51
        VertRefresh        43-60

Section Screen
        Identifier         Default Screen
        Device             Silicon Integrated Systems (SIS) PCI/AGP VGA Display Monitor
        Monitor            Generic Monitor
        Default depth      24

There follows a lot of subsections which spell out display levels from 1 to 24.

Do you think changing the default depth would have an effect?

One thing is for sure.  When and if I have to rebuild this box, I will keep a log of everything I did.  I can't remember how I got the network to function and I have forgotten all the things I went through to fire up wine.

And if I somehow rescue this machine, I WILL find a back up.

The next thing that I am going to try is to boot the knoppix dvd that I have - just to see if the screen will accomidate this package.

Thanks again for the help.

---

### Post by Infinite Indefinite on 2008-09-18
Actually, Defaultdepth looks right.  Best to leave it alone, and add some extra lines.  To decide which lines, take a look at my xorg.conf which I post below:

In my Section "Screen":

[B]Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"
	EndSubSection
EndSection
[/B]
In Section "Monitor", I have these lines at the end:

[B]modeline  "1280x800@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
[/B]
However, the main thing is that there are two other sections - Section 'screen' (Small s; Linux is case sensitive) and Section 'monitor'.  Let me give you mine:
[B]
Section "screen" #       
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x800@60"
	EndSubSection
EndSection

Section "monitor" #       
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "1280x800@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection[/B]

I'd recommend backing up xorg.conf - and then making the necessary changes.  Restart after you've made changes.  If at first it doesn't work, open up xorg.conf again and make new changes.  Repeat until you get what you want: don't worry, perseverence pays off in Linux.

---

### Post by jerlinux on 2008-09-18
Is it against the law to attach a file?

I think that I can get that done but I have also discovered that I can no longer network so I would have to be able to copy the file to a flop or something and then drag it up here.

Also, the knoppix dvd boots ugly.  So, I suspect that there is something wrong with the MB.  But, I put in a windows hard drive and when the "linux" machine tries to boot I get a hard drive failure error.

So I tried to put the linux hard drive into the windows machine and it gives me the high narrow screen.  It is beginning to appear that some bad amps came down the wire and took out a couple of things at the same time.

I have to keep moving slowly.  In my younger days, I would just blow up everything and start over.  Or, in my haste, break good things trying to fix one bad apple.

I think that the next time I turn off this machine, I will try and boot the knoppix disk just to see something work correctly in Linux.

I will hunt around in the basement to see if I can't find another windows machine and take the hard drive out of that one to see if I can boot good windows on the sick unit.

---

### Post by Infinite Indefinite on 2008-09-20
*Is it against the law to attach a file?*

Heavens, no.  Sorry, I should have attached mine.  Here it is.

---

### Post by jerlinux on 2008-09-20
Yesterday I actually had to go to work and could not look further into my problem.  But I thought about it all day and by the time I got home, I had convinced myself that only hardware could suddenly fail in the middle of an operation.

So, this AM, I was determined to find a windows machine that would accept the 160G hard drive that has the Ubuntu installation.  Most of my basement machines are so old that the bios has drive size limits.

Finally I found one that seemed to listen but when I turned on the machine, all I got was random lights and rapidly rolling pictures of nothing.  In the past, I would give up and pull the plug but this time I decided to let the machine run until it gave up.

It took almost 10 minutes but finally a single line of text appeared that stated Ubuntu would now be running in low graphics.

Then my "normal" sign on screen appeared and I was able to fire up the system.  I did not go any further than the first screen as I did not want to write any more than necessary to the hard drive in the "low graphics" mode.

But that was enough to prove the theory that I have a hardware problem.

The only question now is how much to buy.  I have found in the past that if I just order up a new MB the CPU or the RAM will not work.  I could order up a new combo but then I am tempted to order more muscle than this machine has and replace this machine putting the Ubuntu hard drive in this box and moving it to the basement.

Anyway, my problem is solved.  Thanks for taking the time to respond to my plight.  The next time I turn on the Ubuntu drive, I will copy my x11.cong file to a flop - maybe even my network will now function - I was so excited to see the familiar home screen that I turned off the machine and ran upstairs for a victory coffee before I tried to make the machine do anything.

I would still be interested in finding out why my file does not contain the sections you mentioned.

---

### Post by jerlinux on 2008-09-20
I am attaching my xorg.conf file.  I had to rename it xorg.txt so it could be attached but it opens in M$ word so it should open in other software also.  Maybe, when the dust really settles, we can figure out why the sections you mentioned are not in mine.

I also now have two additional xorg.conf files.  One is backup and one is failsafe.  I ASSUME that they were created when I looked at the file with gedit?  I THINK I can probably erase them although they are so small that I am sure they will not be a problem even if they stay.

In the meantime, does ubuntu have a program to back up the computer or should I be looking around for a good backup program for Linux?

I don't want to be out there in the cold again.

Thanks

---

### Post by Infinite Indefinite on 2008-09-21
> **jerlinux said:**
> 
In the meantime, does ubuntu have a program to back up the computer or should I be looking around for a good backup program for Linux?

I don't want to be out there in the cold again.

Thanks

Well, there are numerous ways to backup on Ubuntu.

My preferred option is Flyback.  The instructions are here:

[http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10](http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10)

---

### Post by jerlinux on 2008-09-26
Thanks for the back up program.
I am still waiting by the mailbox for my new mother board.
I hope I have gotten this correct - at one point I changed the bios to pci and added a video card to the system.  But I still got the tall narrow screen when I booted the box.
In the meantime, somebody threw away a Intel Pentium II the other day and I threw it in the car.  Maybe I will drop my 160G drive with Ubuntu into that machine and see what happens.

---

### Post by jerlinux on 2008-09-30
Just to follow up on this, I have to report that the new motherboard did not fix this.  In fact, now I get the following messages:

Failed to start X server.  It is likely that it is not set up correctly.  Would you like to view the xserver output?
Then:
Warning failsafe was already started falling back to gdm to report the issue.
Finally:
XServer disabled.  Restart GDM when it is correct.

At this point, I can log on and I am in the non graphic mode.  

I have also brought over a windows hard drive and it fails to boot in this machine.  It looks like my cpu is dying.  If I buy the new chip, is there an easy way to reset the xserver?

Thanks again.

---

### Post by Infinite Indefinite on 2008-10-01
> **jerlinux said:**
>   If I buy the new chip, is there an easy way to reset the xserver? 

I believe the key combination CONTROL-ALT-BACKSPACE does that.

This and other solutions can be found at the following link:

[http://www.linuxquestions.org/questions/linux-newbie-8/restarting-xserver-282299/](http://www.linuxquestions.org/questions/linux-newbie-8/restarting-xserver-282299/)

---

### Post by jerlinux on 2008-10-04
The pest is back.

With new motherboard and now a new cpu, I am able to see a reasonable screen but I cannot get better than 800 X600 with a 60 rate.  I can see a very tall screen if I reset the rate to 56 so I bet that is one of the things that got stepped on when the failure occured.  But now, how can I get my screen resolution stepped back up?  It is possible that the new board cannot support better than 800 but I doubt it.
Is now the time to insert the extra words into my xorg.conf file?
Thanks again.

---

### Post by jerlinux on 2008-10-04
My present xorg.cong file has about 10 lines and spells out only the 800 X 600 video setting.  That likely explains why I cannot select higher graphics.
I have done the sudo dpkg-reconfigure -phigh xserver-xorg.  The machine generates a backup copy of the file and then builds a new one that is the same 10 lines.
I have found a previous back up xorg that contains the 1024 verbage but it also specifys sis interface for the video and the new board does not have the same feature.
I have started the program in the recovery mode and selected the repair the x server option but it does not change the xorg file.
If I wait for an update to Ubuntu, it may not even load a new xorg so I guess I had better get hot see if I can build a new and better xorg.  It is still not clear why the xorg would be changed by a hardware failure but it looks like I was just lucky.

---

