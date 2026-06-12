---
title: "Brasero DVD Burning problems..."
date: 2009-01-10
forum: Hardware
---

### Post by ioanghosh on 2009-01-10
I installed ubuntu 8.10 on my desktop which has a dvd writer (LG). After installing the OS I wanted to test the dvd burning... it burns 100% ..but at the end, at the "fixation" phase returns an error with a log and declares the dvd burning is unsucessful... I carried out another burning process (but this time in simulation mode) but the results were the same...here's the end line of the log message.... 

Padblock                         Start Block 1430835
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 1430985 extents written (2794 MB)
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1.000000)
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: updating RMA
BraseroGrowisofs stderr: /dev/scd0: closing session
BraseroGrowisofs stderr: :-[ CLOSE SESSION failed with SK=5h/SESSION FIXATION ERROR - INCOMPLETE TRACK IN SESSION]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2527)

Can anyone suggest what i should do to solve this problem?

Thanks in advance..

Ioan...

---

### Post by Phasma on 2009-01-11
> **ioanghosh said:**
> I installed ubuntu 8.10 on my desktop which has a dvd writer (LG). After installing the OS I wanted to test the dvd burning... it burns 100% ..but at the end, at the "fixation" phase returns an error with a log and declares the dvd burning is unsucessful... I carried out another burning process (but this time in simulation mode) but the results were the same...here's the end line of the log message.... 

Padblock                         Start Block 1430835
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 1430985 extents written (2794 MB)
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1.000000)
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: updating RMA
BraseroGrowisofs stderr: /dev/scd0: closing session
BraseroGrowisofs stderr: :-[ CLOSE SESSION failed with SK=5h/SESSION FIXATION ERROR - INCOMPLETE TRACK IN SESSION]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2527)

Can anyone suggest what i should do to solve this problem?

Thanks in advance..

Ioan...

Bump

I am having this same issue and have been for a while now.

---

### Post by HDTimeshifter on 2009-01-11
Brasero is a POS.  It gets stuck at 2% and takes forever almost everytime just trying to copy an audio CD on my 22x LG Lightscribe DVD/CD burner (I don't use the Lightscribe feature, but it was the same price as the non Lightscribe, so I bought it if I should ever want to waste $ on expensive Lightscribe discs).

I installed k3B and it had a similar problem, taking forever but finishing, and saying failed burn when I tried to burn using "clone copy".  So I set it to "normal copy" and it works fine.  My guess is that Brasero only does "clone" (or exact 100% bit copies) and fails on every little scratch rather than using error correction to skip over occasional bad bits.  Try k3B and hopefully that will work with DVDs as well.

---

### Post by Phasma on 2009-01-12
> **HDTimeshifter said:**
> Brasero is a POS.  It gets stuck at 2% and takes forever almost everytime just trying to copy an audio CD on my 22x LG Lightscribe DVD/CD burner (I don't use the Lightscribe feature, but it was the same price as the non Lightscribe, so I bought it if I should ever want to waste $ on expensive Lightscribe discs).

I installed k3B and it had a similar problem, taking forever but finishing, and saying failed burn when I tried to burn using "clone copy".  So I set it to "normal copy" and it works fine.  My guess is that Brasero only does "clone" (or exact 100% bit copies) and fails on every little scratch rather than using error correction to skip over occasional bad bits.  Try k3B and hopefully that will work with DVDs as well.

I have a the same problem with gnome-baker, and k3b

---

### Post by adamlau on 2009-01-12
Try Xfburn. No wodim/dvd+rw-tools dependencies to deal with (since Brasero, GB and K3B all failed). I started with the version from the repositories, no coasters through tens of discs. Built 0.4.0 against the latest libburnia libraries, no coasters as of yet through tens of discs :) .

---

### Post by insane999 on 2009-02-03
hey guys...I just installed ubuntu 8.10...
i was trying to burn .avi files onto a DVD...i loaded everything and proceeded but in the end the burn option does not highlight!!! As in am not able to proceed to burn the disc only...could someone tell me whats wrong???:(

and people who just wana data burn can drag the stuff into the CD/DVD creator that comes pre-installed in ubuntu and just normally burn...that works all cool...no errors yet doing that!:)

---

### Post by aby23 on 2009-02-25
> **insane999 said:**
> hey guys...I just installed ubuntu 8.10...
i was trying to burn .avi files onto a DVD...i loaded everything and proceeded but in the end the burn option does not highlight!!! As in am not able to proceed to burn the disc only...could someone tell me whats wrong???:(

and people who just wana data burn can drag the stuff into the CD/DVD creator that comes pre-installed in ubuntu and just normally burn...that works all cool...no errors yet doing that!:)

I am facing the same problem!...please help!

---

### Post by StephenOK on 2009-02-25
Yeah, I'm having similar problems. I tried to - unsuccessfully - burn an .iso image of Ubuntu stuido and I wasn't even able to access the burn feature during setup. Then I tried cd/dvd creator and it keeps telling me to insert a rewritable or blank disc - all of which I've already done.
I'm a bit puzzled by this.
Any advice would be appreciated.

---

### Post by StephenOK on 2009-02-26
Bump

---

### Post by dLeon on 2009-02-26
Try the command line version of CD/DVD burners. I notice a command line application specificaly for DVD-R/RW burning in main repo. Note; I just move to Ubuntu around 4 months ago. So I'm not yet follow what Ubuntu repo's offer for burning stuff.

---

### Post by StephenOK on 2009-02-26
> **dLeon said:**
> Try the command line version of CD/DVD burners. I notice a command line application specificaly for DVD-R/RW burning in main repo. Note; I just move to Ubuntu around 4 months ago. So I'm not yet follow what Ubuntu repo's offer for burning stuff.

Thanks, man. I'll give that a shot in the morning.

---

### Post by Cha0tik on 2009-03-06
I'm having a similar issue described here: 
[http://ubuntuforums.org/showthread.php?t=1079938](http://ubuntuforums.org/showthread.php?t=1079938)

Did anyone here have any luck? My other thread is not generating any interest !

---

### Post by StephenOK on 2009-03-06
> **Cha0tik said:**
> I'm having a similar issue described here: 
[http://ubuntuforums.org/showthread.php?t=1079938](http://ubuntuforums.org/showthread.php?t=1079938)

Did anyone here have any luck? My other thread is not generating any interest !

Not yet. Been terribly under the weather with the flu. Haven't had the opportunity to try aforementioned suggestion. Hopefully I'll be able to drag myself to the Ubuntu system tonight.

---

### Post by GZ Expat on 2009-03-07
> **insane999 said:**
> hey guys...I just installed ubuntu 8.10...
i was trying to burn .avi files onto a DVD...i loaded everything and proceeded but in the end the burn option does not highlight!!! As in am not able to proceed to burn the disc only...could someone tell me whats wrong???:(

and people who just wana data burn can drag the stuff into the CD/DVD creator that comes pre-installed in ubuntu and just normally burn...that works all cool...no errors yet doing that!:)

Me too...been struggling with this for quite a while.  Seems pointless to even have Brasero on my desktop if I cannot use it to burn avi or mp4 files to dvd format.

---

### Post by SkankinRatFink on 2009-03-07
I noticed two of you are using LG drives. How about the rest of you?

I buy Lite-On burners and I use Brasero all the time. Never any problems.

---

### Post by insane999 on 2009-03-21
hey guys....okhay firstly! burning a data disc the way i said earlier also showed hell lot of problems for me. it shows burn successful but when i checked the disc the data in was corrupt!! :( wasted 5 dvds and lost "n" no. of movies because of that! :'(
anyways am using Xfburn now.
could someone help me with this software?
what on world is write mode : TAO & SAO??? :shock::-s
and some tips would also be useful! ;)

---

### Post by HDTimeshifter on 2009-03-21
> **SkankinRatFink said:**
> I noticed two of you are using LG drives. How about the rest of you?

I buy Lite-On burners and I use Brasero all the time. Never any problems.

Hmm, that's interesting.  I have a Lite-On in my Mythbuntu HTPC and would try burning a disc, but Mythbuntu doesn't come with Brasero.  However, since the same problem occurred with both Brasero and K4b with clone copy, I think it's the copy process rather than the drive.  I didn't find a non-clone copy option in Brasero, so wasn't able to try that.  In Windoze, I never had problems copying audio CDs with a Memorex DVD drive or E-machines CD drives.

---

### Post by JordanMcSwifty on 2009-03-26
Im having that problem too. 


And my drive is an LG...

---

### Post by Agent.Logic_ on 2009-04-03
I have a Samsung drive, and I'm trying to burn the Xubuntu LiveCD image so that I can install it on my laptop. For whatever reason, it's been stuck at 33% for over half an hour. Keeps saying "Creating image checksum." Really annoying. :mad: The estimated time remaining just keeps climbing up. It currently reads 51:57 left, and going up by the second.

---

### Post by stargate2500 on 2009-04-03
this worked for me


6. Burning the ISO files
Using Ubuntu

1. Insert a blank CD into your burner. A "CD/DVD Creator" or "Choose Disc Type" window will pop up. Close this, as we will not be using it.
2. Browse to the created ISO image in the file browser
3. Right click on the ISO image file and choose Write to Disc.
4. Select the write speed. It is recommended that you write at the lowest possible speed.
5. Start the burning process and repeat these steps until all ISOs are done.

Using Kubuntu

1. Find the ISO image in the file browser (available at System Menu > Home Folder on bottom of the screen next to KMenu.)
2. Right click on the ISO &#8594; Actions &#8594; Write CD Image with K3b...
3. K3b will now automatically verify the md5sum, make sure these match.
4. Place Blank CD in burner and click on start.


Using Xubuntu

1. Launch the burning tool, xfburn (available at Applications &#8594; Accessories &#8594; xfburn.)
2. Choose from the main toolbar, or from the menu Actions the option "Burn CD Image",
3. From the Burn CD Image dialog box, click over (None) from "image to burn", and find the ISO image in the file browser
4. In the dialog, click 'Burn Image'.

---

### Post by stargate2500 on 2009-04-03
I almost bought another dvd burner until I found it was stalling out. Because of the software....

---

### Post by Agent.Logic_ on 2009-04-03
> **stargate2500 said:**
> this worked for me


6. Burning the ISO files
Using Ubuntu

1. Insert a blank CD into your burner. A "CD/DVD Creator" or "Choose Disc Type" window will pop up. Close this, as we will not be using it.
2. Browse to the created ISO image in the file browser
3. Right click on the ISO image file and choose Write to Disc.
4. Select the write speed. It is recommended that you write at the lowest possible speed.
5. Start the burning process and repeat these steps until all ISOs are done.

Cheers mate, will give that method a try.

---

### Post by m.srivathsan on 2009-07-29
Hi all,

Seems like there is an issue with Ubuntu 8.04 and LG DVD Writer.

I had successfully burnt DVDs (especially DVD Movies as backup) from ISO images in the past i.e., more than 6 months back.  But a few days back, I noticed something strange.  I could successfully burn a DVD movie (shrunk to 4.5GB as my writer couldn't do dual layer) but while playing it back from the fresh DVD using VLC, It get's stuck (literally).  How much ever I repeatedly try, the playback gets stuck in the same spot.

But when I played the DVD on Windows PC (the DVD-drive is not LG), It plays wonderfully well - didn't get stuck anywhere!!  I checked atleast 3 such DVDs that stalled in Ubuntu 8.04.3 but played fine on Windows.

Something to do with Ubuntu + LG DVD drive?  Any hints, clues would be helpful.

Thanks and rgds,
Watson

---

### Post by pablosanchezuy on 2009-07-29
Thanks adamlau , xfburn did it .

Pablo

---

### Post by orwonthe on 2009-08-05
I was able to solve the problem by first creating a .iso file for the DVD and then using brasero to burn that file.

I created the .iso file using DeVeDe installed from synaptic package manager. I suspect that any program to make a .iso file would have succeeded.

---

### Post by MScapee on 2009-08-18
Xfburn did the trick for me.  It works flawlessly, it's fast burning and it's Gnome-friendly (I absolutely despise KDE apps).  Also worth noting, Xfburn is actively being developed.

---

### Post by musselcracker on 2009-11-04
I just successfully burned a DVD disc with Brasero using UBUNTU 9.04. I will not upgrade to 9.10 to avoid having the same problem you are. Perhaps , you could go back to version 9.04. :)

---

### Post by DeborahSu on 2012-06-19
I can't believe this problem is so old, yet the same buggy software is STILL included with the distro.  Brasero is stalled at "creating image checksum" on the 12.4 cd that I'm trying to burn in order to install on my laptop.  Geez.  I can see needing to find other software for various things, but kind of expect basic stuff like burning software to work as installed.

---

### Post by dandnsmith on 2012-06-19
You'd be better off creating your own thread - after all interest in an (almost0 3 year old thread has long since vanished, and the probable causes of your problem will be different (because all the software involved is newer versions). At one stage brasero had burning problems (again), this time with missing modules for the burning.
Modules have been again updated, and I've no problems using UB 10.04, 11.04, Mint12.

I advise googling for your problem (with specific version info), and you'll probably find (as I did 2 years ago) that your problem already has a posted solution.

Good luck

---

