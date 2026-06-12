---
title: "eeeXubuntu"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by C.S.Cameron on 2007-12-13
Has anyone tried eeeXubuntu on their new eeepc yet?
Got one for my daughter, but she prefers Ubuntu to Xandros.
Tried DamnSmallLinux from a thumbdrive and it seemed to work ok except for touchpad and wireless.
Could not get my primary Umbuntu thumbdrive with 7.10 to get into x.
(but it is tuned to my office station).

---

### Post by bluedragon436 on 2007-12-14
not really on your topic, and sorry to jack your thread...I have actually been considering one of these, how does she like the eeePC????  The only thing holding me back as of right now is the lack of CD drive....  but still may purchase one anyways.....after I see what people have to say about them...

---

### Post by C.S.Cameron on 2007-12-14
I'm sure she will love it once she gets it away from me.
If I don't brick it first.
It doesn't have a floppy drive ether.
About the only thing I use optical drives for now days is backups,
The eee's 4G drive is not hard to backup to pendrive,
and ripping movies,
The eee does DivX, 8 of which fit onto a 8G pendrive.
Cork

---

### Post by r-mo on 2007-12-14
No reason why you can't plug in a usb optical or floppy drive.  I've not got one yet.  My main concern is 800x480 screen resolution and what would fit onto that nowadays.  I'm also thinking I may wait for the 8GB version with 1GB RAM

---

### Post by IanW on 2007-12-14
Remember that a _full resolution_ DVD uses 720x576 (720x480 in US).

Any dialogue boxes that go off the edge of the screen can be moved around using Alt+Left click+move.

The RAM can be upgraded without voiding warranty, it's just a standard 667MHz DDR2 laptop stick.

---

### Post by C.S.Cameron on 2007-12-14
Well I gave her one of my 19" monitors, (an excuse to upgrade to dual 24's), bought her a USB keyboard and mouse and gave her a spare 8G thumb drive.
Makes for a very compact desktop. 
After a while you don't even miss the noise.
Once plugged into VGA it gets full resolution.

---

### Post by violajack on 2007-12-14
Typing from eeeXubuntu now.  It works as advertized.  I installed it last night from a usb stick.  Everything works except the funciton keys (birghtness keys do work, just not volume or wireless on/off).  There is another script pack at google code for getting those to work, but I haven't had the time to try it yet.  I was able to connect to WAP encrypted wireless with the live cd running off the usb stick.  The install was a standard ubuntu install.  I chose to wipe the whole drive and no swap.  I have a gig of RAM and didn't want to loose a gig of hard drive space just to hibernate, but others have reported hiberate working wihtout problems.  

I had a full Ubuntu install on the eee, but was running low on SSD space, even with all of my docs on an SD card.  With eeeXubuntu, I now have 2 gig free on the SSD.

---

### Post by C.S.Cameron on 2007-12-14
Thanks Violajack
Tried installing eeeXbuntu to a 2G thumbdrive that was running DSL using the instructions at:
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home)
But it did not seem to like DSL's partitions.
Did the instructions work for you?
Unplugged the HD, booted the CD with TD attached.
Selected install eee option.
Ended up at GUI, selected Install, selected format entire disk.
Answered standard questions.
Seems to have worked, but still have 2 partitions and looks like I am missing 500MB of space.
To make things worse my daughter found out I was hiding her computer under my pillow, grabbed it and headed off to Whistler, hopefully for just the weekend.
Cork

---

### Post by violajack on 2007-12-15
I put the iso on a usb stick with the fun little isotostick script.  Note that only release 2 of the iso works with the script.  I booted the eee from that and chose manual partitioning to wipe the SSD and create one big partition for xubuntu to have all of.

---

### Post by fbny71 on 2007-12-17
I installed the eeeXubuntu. I was quite pleased overall. My only concerns: the SD card slot produces a "can't mount" arror with any card I insert and I thought the internet worked kinda slow! I can't wait to try the next release. 

I installed Gutsy right off the installation it worked like a charm but I am going to do it again as per Rapido's guide to try out his post-install script:

[http://ubuntuforums.org/showthread.php?t=611422&highlight=eeexubuntu](http://ubuntuforums.org/showthread.php?t=611422&highlight=eeexubuntu) 

I have to say, I love this little machine!

---

### Post by IanW on 2007-12-17
> **fbny71 said:**
> My only concerns: the SD card slot produces a "can't mount" arror with any card I insert!

Check your /etc/fstab.
Mine had a line mounting the SD card slot to /media/cdrom.
I commented out that line, and have had no trouble since.

---

### Post by ljonesj on 2007-12-17
that little computer looks good for a college person they need the portabilty i was thinking the 8gb unit was out new egg list them i have thought of getting ne but i do have a linux laptop that runs full 7.10

---

### Post by skmassey on 2007-12-19
I finally got xubuntu on my EEE thanks to this thread. :guitar: I'm soo happy with my eee.  I wish the function keys worked, but I can deal with it.  Thanks for the help!:)

---

### Post by ljonesj on 2007-12-19
given time i am suren those function keys will work

---

### Post by ebash on 2008-01-13
The function keys work with the 3rd release of eeeXubuntu (see [http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#fn_keys]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#fn_keys")).   The problem is that apparently Asus changed the ACPI codes between revision updates and the 3rd release provides only the codes for one kind of revision.

If the Fn keys don't work on your model, you can change the ACPI codes manually in order to fix the issue. This task is not difficult, at first the ACPI codes need to be found to do it simply do:
```
tail -f /var/log/acpid
```

Then press the Fn keys and look for the codes, the codes are displayed in lines that look like:

```
[Sun Jan 13 18:14:28 2008] received event "hotkey ATKD 00000012 00000000"
```

Only three parts are needed from these output lines, the ones listed in the example below. The last part consists of a counter and is not relevant. For instance, on my EEE PC the key "Fn + F6" gives me this ACPI code:

```
hotkey ATKD 00000012
```

Finally, look in the folder /etc/acpi/events and update the files starting with asus- or eee- based on their names and on the codes that you have collected. If you don't have these files then download the scripts provided by [http://code.google.com/p/eee-ubuntu-support/]("http://code.google.com/p/eee-ubuntu-support/") and install the acpi add ons.

In order to apply the changes automatically simply restart the ACPI service:

```
sudo /etc/init.d/acpid restart
```

The keys should be working. Depending on the kernel that you are using the mute key might not work as expected. The key will mute the volume but it can't be used to unmute, instead the "volume up" key needs to be pressed multiple times in order to restore the volume. If that's the case then take a look at this post: [http://forum.eeeuser.com/viewtopic.php?id=9437]("http://forum.eeeuser.com/viewtopic.php?id=9437")

---

### Post by tedrampart on 2008-02-23
regarding the fn keys, I got them to work in regular ubuntu from this page [http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

now I'm not sure if its been mentioned, or if it will even work, but I thought it may help.. the only thing that didnt work was the webcam, (turned out it worked natively, but my cam was actually off in the bios)

hope it helps

---

### Post by boulderbound on 2008-03-02
Hey all - 

I've just installed eeeXubuntu on my 3e...and have been really happy with it to some extent and am having some problems as well...

The install went smoothly overall, had some issues making my thumbdrive bootable using a VM on my iMac, but it finally worked...after that the install went smoothly.

The reason for my post:

I can't get anything to install! I'm trying to get openoffice from the add/remove tool, and it says I can't install it on my architecture (i386)...huh?!?!

Heads up, relative Linux newb here...

also trying to install Skype from a download, it's not in any repositories, and that tells me that there's a dependancy that is missing...


Any assistance with this would be really appreciated, I'm trying to set the eee up for my mom to use on an upcoming vacation and need it to work smoothly.


Oh, and sorry for the thread hijack, hopefully I'll be able to repay you later!

---

### Post by Fransiscus on 2008-03-03
Installed eeeXubuntu on Asus eeePC. Its working smoothly, but I am looking for solutions for three problems:

1. The PC wont suspend/hibernate

2. It wont shutdown properly. The screen will get black but actually its not shut down before the Start/Shut -button has been pressed long. If you dont, the battery is soon empty and it takes some tiime before you can figure out why.

3. Installation problems, as someone reported before. Cant install skype

4. It wont mount USB memory sticks.

Fixes for these?

---

### Post by boulderbound on 2008-03-03
> **Fransiscus said:**
> Installed eeeXubuntu on Asus eeePC. Its working smoothly, but I am looking for solutions for three problems:

1. The PC wont suspend/hibernate

2. It wont shutdown properly. The screen will get black but actually its not shut down before the Start/Shut -button has been pressed long. If you dont, the battery is soon empty and it takes some tiime before you can figure out why.

3. Installation problems, as someone reported before. Cant install skype

4. It wont mount USB memory sticks.

Fixes for these?

I'd suggest making sure it's fully updated first off...

I solved my Skype and OpenOffice issues by adding another universe repository to the software sources pane...was then able to get both installed and running without further issue...

I'll post the repository I added when I get home tonight, don't have the 3e with me today...

---

### Post by Fransiscus on 2008-03-05
OK, it is fully updated. I hope you get the stuff here...

---

### Post by boulderbound on 2008-03-05
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

that's the repository I added to get open office and skype to work. I know it's for an old version, but it worked...and I could update the software once installed to make sure it was current...

---

### Post by happy-and-lost on 2008-05-24
Any news on an update to support the EeePC 900?

---

