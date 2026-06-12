---
title: "(SOLVED?) 14.04.3 Z87 Nvidia audio occasionally cuts out .5 sec video full screen"
date: 2015-12-24
forum: Hardware
---

### Post by Kris_M on 2015-12-24
(EDIT: jump to post #8 for "solution" )

I'll start this in Hardware.

Noob.

Geek to windows7. (tried 10 in VM. : BAH!)
Mobo is in sig below...
Have not played with Linux for several years. and that was not debian.

A few days ago installed 14.04.3 dual boot with windows 7. Set up printer, phone, camera.  Run FF with 100 tabs and TBird. Got them all working perfectly. Viewed video full screen on TV and sound was perfect.  Started Backup as auto weekly and also went offline and used Clonezilla to back up the ext4 partition to my 1T HD.  Probably did a little something else but don't remember what - I am not trying to be sophisticated with this build.
Viewed a video and got the 1/2 second skips occasionally/randomly (did replay a section and skips different). No "crackle" or "pop".

Vid card is Gigabyte GeF 650 GTX Ti which is Nvidia. 
Mobo is Gigabyte GA-Z87N-WIFI (with the wifi card removed).
Player is internet site putlocker.ms - whatever player they use - it plays right in that tab.

Sammy 913BMPlus referbed 1280x1024 monitor connected via DVI/DVI to Nvidia card:
   >>no audio skips either regular or full screen.
Vizio E400i-C2 40" HDTV HDMI in - via HDMI out from Nvidia card (no adapters):
   >>few audio skips if regular, definite audio skips when video is full screen.

--> NOTE there are NEVER any video skips - smooth as silk!

So ? loading?  I checked processes in terminal but only BASH and whatever the other one is.
I made sure that FF and TBird were not running.
I googled and saw problems supposedly related to Alsa, Z87/97, and life in general.

-->  The Ubuntu ext4 and swap partitions are in a 70GB area in the middle of a Samsung 250GB SSD. Fast.

-->  We are not dealing with internet download speed here because it had already downloaded all the way to the end. So it was just playing a temp file wherever Linux puts such things.

--> Note: Sound is coming from the mobo when using the Sammy monitor and from the Nvidia card/HDMI when using the Vizio TV.

I'm back on Win7 *$%#*##! but with a clearer head and thought I'd ask for help.  Google and these forums have been infinitely helpful in getting my Canon MG7520 printer/scanner, Moto Atrix HD MB886 phone memory, and Canon elph camera working perfectly.  Hopefully I can get past this!

Ubuntu is sweet!

Thanks!!!
Kris

GA-Z87N-WIFI mobo, i5 4670K, CoolerMaster Hyper TX3 hsf, 8GB ballistix 1600(2x4), Win7 Pro x64 SP1 current, Sammy 250GB Evo SSD, BitFenix Prodigy black case.

---

### Post by Vladlenin5000 on 2015-12-24
> **Kris_M said:**
> --> Note: Sound is coming from the mobo when using the Sammy monitor and from the Nvidia card/HDMI when using the Vizio TV.

So, considering this is the only setup you're complaining of -and- that the audio via HDMI is managed by the graphics driver, the question is: Which drivers are you running? The default open source *nouveau* or Nvidia's proprietary drivers? If the latter, which version?

---

### Post by Kris_M on 2015-12-24
Huge thanks for reply - was looking for commands - 4 files attached - nouveau but no version number.

EDIT: I am d/ling 352.63 from Nvidia and will try to install and will report back.
EDIT2: marked executable and am installing. (I love system monitor - I can tell that it's working when bar seems static! :) )

---

### Post by Vladlenin5000 on 2015-12-24
As expected.

You should try the nividia drivers for optimal performance.
Nvidia suggests 352.xx for your card. 355.xx should also be fine. The bad news is you don't have either version available in the standard repositories of 14.04.
You can follow this instructions to add a PPA: [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Reboot and test (you may notice the startup splash screen won't look as pristine as before but it's only a small annoyance resulting from less than proper code from Nvidia; there are a few "fixes" but I wouldn't bother with something that shows up for a couple of seconds at most).

---

### Post by Kris_M on 2015-12-24
This is the reason I dropped it last night and went back to Win7.  I just spent a few hours chasing my tail.  Thankfully I made a Clonezilla backup before I did all this. So far I have restored that partition 4 times.

_**Warning - if you follow that link and execute those commands you will destroy your system:**_
reboot gives [ some number] ACPI PCC probe failed and then a dead computer.  Reboot to Clonezilla and restore ext4 image.

If you download the .run file from Nvidia and then try to execute it in a terminal you are stopped when it senses you are running an X server.  Trying to stop it by running something like 
sudo service lightdm stop kills your boot.  Fortunately a reboot gives you a machine back.

So no Nvidia yet. :(

---

### Post by Vladlenin5000 on 2015-12-24
Sorry, I don't understand what you mean...

Do NOT use the driver directly from Nvidia. The drivers you can install, either from the official repositories or the aforementioned semi-official PPA, have been tested and patched whenever needed to assure performance and stability in Ubuntu. Plus, if you use the Nvidia installer you'll have to do it all over again for each an every kernel upgrade.

Again, after adding the PPA (required because you're running an old(ish) Ubuntu release; not required for the current 15.10 and the same card) you can either install via commands as mentioned in the article or simply go to System Settings > Software & Updates > Additional drivers (tab) and select & apply the desired version there. Again, the recommended one is [B]352.

[/B]*IMPORTANT*
Considering you have been messing with several versions already, _before you attempt a new installation **always** remove the previous drivers_:
```
sudo apt-get purge nvidia*
```

---

### Post by Kris_M on 2015-12-24
No.

My clonezilla partition backup was from before any thoughts of Nvidia drivers so was as ubuntu 14.04.3 made it. Clean.

The solution is to go to **system settings / software and updates / additional drivers** and select the "_**352-updates**_" driver and let it do its thing.
**HOWEVER** that is not sufficient. You then have to run  "sudo nvidia-xconfig" to update the conf pointer from nothing to nvidia. THEN reboot.

My key to this solution came from this site part way down:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I tried 
sudo ubuntu-drivers devices
sudo apt-get install nvidia-352

but that didn't boot.
when I added sudo nvidia-xconfig for "driver not active" further down the page, it booted to desktop but no mouse. So I tried the above and it worked.

You have to understand that between each of these attempts I had to use clonezilla to restore back to 
before any changes because I had a non-working Linux partition.  I did each of these attempts on a clean system.

Now I will test to see if it fixed my problem.

EDIT: the problem remains. 6 hours shot to hell.

I'm going to mark this solved with a question mark.
For whatever reason, there are no cutouts at the moment.

I have done a lot of playing and clonezilla restoring. Maybe another 6 hours since my last post.

I tried to remove pulseaudio but that resulted in a system with no sound.
Besides using the top command (below) it showed that it's only using 1%!  Not a problem!

One thing that stands out is that I tried installing a bunch of different mixers from "ubuntu software center" one at a time, not liking them and then uninstalling them.  One crashed mid install and I had to reboot.  I think it was jackmixer but I forget. None of them add anything except maybe gmerlinmixer which I notice is installed at the moment.  But all of those installs and uninstalls clearly left something different.

I also used top - in a terminal type "top" without quotes hit enter and then type the number 1 to get cpu info.
This told me that when using FireFox, Flash was using about 30% and FF was using 30%.  So I tried QupZilla - that used about 30% and X used 10% - also the browser and Linux were very nicely dividing the load among my quad core to about 10% each - much more reasonable.

I had been using QupZilla for about 10 builds but on this one, maybe with all the mixer playing, no cutouts.  I viewed part of one video and all of another (feel the force!) and no cutouts.(where I was getting cutouts maybe every 10-30 seconds before)

Since I don't know what fixed it I have no idea if it will stay fixed, but I will see.

I personally don't think that changing to the Nvidia driver had anything to do with it.
I also don't think that Z87 had anything to do with it - just a popular chipset.
I don't think that Flash was a "cause" but unnecessarily loads the system and on a slower cpu will definitely cause problems.
Pulseaudio is not the cause since I'm running with a perfectly normal alsa/pulseaudio.
Oh, my "mouse lost" problem was that the mouse pointer was effectively 2 or 3 "screens to the right" so I just moved my mouse left a few times and there it was.

Some CODEC or mux... #$*#*$

---

