---
title: "Does UNR work on the Asus eee pc 1005HA-H?"
date: 2009-10-05
forum: Hardware
---

### Post by jamieleshaw on 2009-10-05
Hello, I'm considering buying an Asus eee pc 1005HA-H.
I would like to if things like Wireless, Blue tooth, Hot keys, Web cam will work out of the box, and if not what configuration steps are necessary.
:popcorn:

---

### Post by jamieleshaw on 2009-10-06
bump.........

---

### Post by Chronon on 2009-10-06
Unless you know something I don't. . . 

I am using it on the 1000HEB and it works nicely (though I'm looking forward to improvements in graphics support in Karmic).  I'm not sure what the difference in hardware is on that model, but AFAIK there's a decent track record with the Eee PC netbooks.  

I think I had to install eee-control to improve the hotkey support, but camera, card reader and wireless worked out of the box.  My unit is the cheapo sibling of the 1000HE, so it didn't have bluetooth out of the box.  I picked up a tiny USB dongle for like $20 which worked without any tweaks.

---

### Post by jamieleshaw on 2009-10-06
Thanks, I think it should work (hopefully):)

---

### Post by jamieleshaw on 2009-10-06
Anyone else have any thoughts?

---

### Post by AppleBonker on 2009-10-07
I've installed Jaunty on my 1005HA.  Wireless and wired ethernet do not work out of the box.  If I remember correctly, wireless is supported with the latest kernel, but that needs to be updated after install (which is problematic if you don't have a wired connection).  I found the help I needed [here](http://ubuntuforums.org/showthread.php?t=1197614).  Once you get the wired driver (there is a link somewhere on that thread), you can update and wireless should be golden.  Other than that, I've had no issues.

If I remember reading correctly, Karmic works out of the box with both wired and wireless on the 1005.  It might be worth waiting for that official release (unless you want to run the beta for now) or you can use the tip above to get internet working in Jaunty.  Post back if you have any issues.

---

### Post by jamieleshaw on 2009-10-07
> **AppleBonker said:**
> I've installed Jaunty on my 1005HA.  Wireless and wired ethernet do not work out of the box.  If I remember correctly, wireless is supported with the latest kernel, but that needs to be updated after install (which is problematic if you don't have a wired connection).  I found the help I needed [here](http://ubuntuforums.org/showthread.php?t=1197614).  Once you get the wired driver (there is a link somewhere on that thread), you can update and wireless should be golden.  Other than that, I've had no issues.

If I remember reading correctly, Karmic works out of the box with both wired and wireless on the 1005.  It might be worth waiting for that official release (unless you want to run the beta for now) or you can use the tip above to get internet working in Jaunty.  Post back if you have any issues.
Did the bluetooth work out of box on yours?

---

### Post by AppleBonker on 2009-10-07
I had some coupons/etc for Best Buy so I bought mine there.  The particular 1005HA they carry does not have bluetooth on it.  In retrospect, I should've gotten mine on-line for a better battery mainly.  I don't use bluetooth for much of anything, so on the netbook it wasn't a concern for me.  Sorry I cannot be of more assistance on this one.

As far as your original post, I did run skype very briefly (not for me, but to help setup skype for my sister) and the webcam worked fine without any additional work.

---

### Post by jamieleshaw on 2009-10-07
Thanks, as someone else in this thread said they have a good track record.
So I'd say it will be fine.

---

### Post by AppleBonker on 2009-10-07
I'm sure you'll be fine as long as your comfortable enough getting the wired/wireless working as I posted earlier.  It was quite simple (even for me - the eee was my first foray into Ubuntu).  I consider myself fairly computer literate, but it was still a whole new world for me.  I'm quite happy with how well it runs on that netbook.  So happy, in fact, that I'm planning on ditching the dual-boot (I have Win7 installed as well) and running only Ubuntu once I upgrade to Karmic on that device.  Since I like installing the OS from scratch, I can just wipe the whole drive and start fresh.

---

### Post by jamieleshaw on 2009-10-07
Well, I will be waiting until Karmic Koala is released. So I'm hoping The Koala will provide me with out of box hardware.

---

### Post by mbernasocchi on 2009-10-08
yep, all works pretty well, here all the info you need[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/")
the only thing is battery life on my 1005HA-H (sold as 10.5H) is shorter, probably around 7-8. I haven't tweaked it yet) and the fan always reports between 3900 and 4020 RPM even when noise level change drastically... maybe it's correct maybe not...

but it's a pleasure to use...

Marco

---

### Post by trapperjohn on 2009-10-08
I installed the daily build of Karmic UNR today on my 1005HA-H and everything works out-of-the-box: Wireless, bluetooth, webcam, sound, even suspend. The only thing I could not get working is the microphone. The microphone jack seems to be available in the Pulseaudio configuration but not the internal mic.

Any tips how to get it working?

edit: Okay, alsamixer knows the internal mic, I can switch the "Input Source" between "Front Mic" and "Int Mic". But this has no influence on a running pulseaudio and recording does not work.

---

### Post by jamieleshaw on 2009-10-08
Thanks, that was extremely helpful.
:)

---

### Post by trapperjohn on 2009-10-09
Okay, this is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/440251?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/440251?comments=all)

---

### Post by trapperjohn on 2009-10-09
Okay, another problem:

I am running the most current BIOS version and it looks like the ACPI state of my battery does not change. The battery applet shows always about 97% (and /proc/acpi/battery/BAT0/state's remaining capacity stays at 5289 mAh)

I'm not sure if this is because of the new BIOS version or if it's a generic problem.

---

### Post by trapperjohn on 2009-10-09
I downgraded to BIOS version 0703 - but without an effect. I think I need to install XP again to check if it is no hardware problem ...

---

### Post by AppleBonker on 2009-10-09
Sorry to get slightly off-topic:

trapper,

Don't bother reinstalling Xp.  I'm pretty sure this is a bug in Karmic.  I'm having a similar issue on my HP laptop.  It was lagging for me before when identifying the battery percent.  If I was fully charged and unplugged the AC cable, the battery would show at full charge for a while, then drop to 94%.  Updates since then have fixed this, but it cannot calculate the discharge or charge rate:

$acpi -ab
Battery 0: Charging, 92%, charging at zero rate - will never fully charge.
Adapter 0: on-line

I think this is a Karmic-wide bug.  See bug 393008

Other than the power (which like I said seems to be bothering a lot of laptops and apparently netbooks) and mic, have you noticed any other problems in Karmic?  I'm too lazy right now to upgrade the netbook to check for myself.  I'm going to wait til I can afford an SSD for it and install the release version of Karmic probably early next month.

---

### Post by trapperjohn on 2009-10-10
Nope, no other issues yet, I'm really impressed. Only Maximus needs to be fine-tuned because there are a lot of applications which shouldn't be maximized (like the gnome-terminal). But this can be easily done via GConf and has nothing to do with the netbook itself.

Nevertheless will I check the battery problem in Win XP because I've read of other 1005HAs which had the same issue. 

I think, the indicator LED doesn't work correctly either - because after the netbook was fully uncharged i plugged in the power cord and the LED became instantly green. According to the manual it should be a flashing orange. And this is not controlled by the OS, I think.

---

### Post by jamieleshaw on 2009-10-10
Well, i'm sure they will fix the alsa thing, I don't think the lights are os controlled charging one's anyway

---

### Post by trapperjohn on 2009-10-11
Battery state is definitely broken on my 1005HA-H - even Win XP always shows 98%. I'll return the netbook and wait for a replacement ...

BTW, multitouch didn't work out-of-the-box on Karmic. But I think this is just an issue of configurability.

---

### Post by trapperjohn on 2009-10-14
Replacement Eee is here and the battery state works fine. I also got multitouch scrolling working, just had to add a config file for synaptics. Instructions can be found easily on the web.

---

### Post by trapperjohn on 2009-10-15
This is the corresponding bug for the microphone issue:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/449855](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/449855)

Please add yourself to the list of affects-me-too people and nominate for karmic release ...

---

### Post by jamieleshaw on 2009-10-15
Done, I should be getting my net-book soon.

---

### Post by AppleBonker on 2009-10-15
> **jamieleshaw said:**
> Done, I should be getting my net-book soon.

Congrats.  I can now also confirm that Karmic seems to work out of the box for me (other than the microphone -don't use- and bluetooth - don't have).  I've also got compiz running and it seems to function fairly well.  I'm not sure if I'll keep compiz going, but I'm just playing with it for now.

It seems to boot quickly, but part of that might be because I just swapped my HD to SSD.  I didn't try running Karmic on the stock drive as I was waiting to do a fresh install on the new drive.  I ended up ordering the new drive a bit before I originally planned, so I am giving it a go with 9.10 for now.  I'll let you know if I happen to notice any problems.

As of right now, I have no use for the mic so I probably wont be doing any testing with that.

---

### Post by Mouth on 2009-10-16
I get a eee 1000HE in a few days, and looking forward to putting Karmic UNR on it :)

For anyone with the same question as the OP for this or other netbooks, check the Wiki :) [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by jocheem67 on 2009-10-18
I'm using a 1005HA-H now a couple of weeks. 

Thingies:

Had to reinstall 2 times ( 9.04 ) because with switching between the netbook and classic interface I lost my gnome-panel...no way in getting it back and return to a stable state.
Wired and wireless are easily get up and running, with a little bit of ubuntu-knowledge.
I ditched pulse-audio for the latest stable alsa drivers, it gives me more volume out of the headphone jack and better sound ( highly subjective ). The front-mic does work with skype:)
Flash and 2d/3d could definitely be better: waitin for karmic and hopefully a better intel-driver here...there are patches which I might try later on.

I'm pretty satisfied with the thing. Use it mostly now for some quick internet searching, mail and especially music organizing and playing. Which it does fine:)

---

### Post by trapperjohn on 2009-10-18
I wouldn't spend too much time in fine-tuning Jaunty anymore. Karmic works already a lot better and there are only 11 days left until they release the final version. Just install the current Karmic daily build and enjoy the new features today! :)

edit: If anyone wonders why it is not possible to receive files via Bluetooth: Install gnome-user-share and enable BT file receiption via its settings dialog (in German it's "System" -> "Persönliche Dateifreigabe", so it should be something like "Personal File Sharing" ...)

---

### Post by jocheem67 on 2009-10-18
Well...I 'm gonna wait, got no time now besides.

Jaunty doesn't run that bad.:)

---

### Post by AppleBonker on 2009-10-18
> **jocheem67 said:**
> Had to reinstall 2 times ( 9.04 ) because with switching between the netbook and classic interface I lost my gnome-panel...no way in getting it back and return to a stable state.


I had this happen when I first installed.  There is a bug posted for this, and a fix that worked for me.  I don't remember the bug number, but if you search you might be able to find it.

I have not had a similar issue in Karmic.  It seems the bug might have been fixed with the new distro.

---

### Post by jamieleshaw on 2009-10-19
I've ordered it, should be here sooooon.

---

### Post by jocheem67 on 2009-10-20
The gnome-panel issue gone in Karmic??
Good news.

I'm looking forward to the new UNR, especially the flash support. Hope it's better than with jaunty.

---

### Post by hoggarth on 2009-10-20
I got a 1005HA which is a great little machine. XP networks fine. 9.04 wired was fine having followed the steps described, and wireless worked somewhat, but very low signal strength and lots of dropped connections. 9.10 turned out to be the same. Strange thing is, I loaded Fedora 11 with 2.6.28.something Kernel(older the 9.10 Ubuntu) and it's wireless connection was just fine. Any ideas? I undated BIOS to latest level and tried everything else I could think of.

---

### Post by scottsmith77 on 2009-10-21
> **hoggarth said:**
> I got a 1005HA which is a great little machine. XP networks fine. 9.04 wired was fine having followed the steps described, and wireless worked somewhat, but very low signal strength and lots of dropped connections. 9.10 turned out to be the same. Strange thing is, I loaded Fedora 11 with 2.6.28.something Kernel(older the 9.10 Ubuntu) and it's wireless connection was just fine. Any ideas? I undated BIOS to latest level and tried everything else I could think of.

There are backports for karmic already, and they fix the wireless - package linux-backports-modules-wireless-karmic-generic. Works great.

What drives me nuts is the touchpad kill switch - worked with SHMConfig on in Jaunty, but since hal is not used in Karmic, SHMConfig won't work. Some of the function keys don't work either. I guess after a few more weeks, those details will be ironed out.

---

### Post by scottsmith77 on 2009-10-22
> **scottsmith77 said:**
> There are backports for karmic already, and they fix the wireless - package linux-backports-modules-wireless-karmic-generic. Works great.

What drives me nuts is the touchpad kill switch - worked with SHMConfig on in Jaunty, but since hal is not used in Karmic, SHMConfig won't work. Some of the function keys don't work either. I guess after a few more weeks, those details will be ironed out.

Of course, after I reply, I sought out more answers, and found more details.

EeePc plus Karmic plus wireless-backports plus [[COLOR="Blue"]Fewt's ACPI scripts[/COLOR]]("http://www.statux.org/ubuntu/pool/main/e/eeepc-acpi-utilities/?C=N;O=D") equals great linux netbook.

Fewt's ACPI scripts allow all the function keys to work, including the touchpad kill switch.

Oh, and a last point - flash with the Chromium browser is definitely better than on Firefox.

---

### Post by trapperjohn on 2009-10-22
Nice! And even better: Installing the alsa backports module also solves the microphone issue!

---

### Post by tipiglen on 2009-10-23
Just setting up karmic UNR on a new 1005HA.  All has worked well so far, including sound and wireless.  Haven't tried the mic/recording functions yet - may report back on that.

Loaded a live version of eeebuntu and re-partitioned disk before installing, and gave myself 112G of /home, 20G root, and reducedXP to 18G (harmless and possibly useful).  eeebuntu didn't work wireless (as expected) so used xp to get a karmic UNR iso and unetbootin to make a bootable sd card.  Installed fine.  Then copied in my old /home files from external backup of old 9.04 installation on laptop.  So far so good.

Then I made sure to copy in my old profiles for firefox and thunderbird, and now I've got them working as well as before.  flash in firefox needs the proper non-free plugin, though, as the free ones just don't work.

The karmic GUI seems to opt to put everything up in 'full screen', with no useful re=size, including gedit, which is a pain, but I expect twiddling some preferences somewhere will sort that.  Touchpad awkward, but i'll learn...A great wee machine, though, and it's awaiting the arrival of an extra gig of ram.  Time to edit my sig, I guess.

More later
Ciao
ed

---

### Post by tipiglen on 2009-10-23
Microphone (internal) doesn't work in karmic UNR - at least not so far

---

### Post by trapperjohn on 2009-10-24
> **tipiglen said:**
> Microphone (internal) doesn't work in karmic UNR - at least not so far

As mentioned above: just install the alsa backports modules.

---

### Post by tipiglen on 2009-10-24
> As mentioned above: just install the alsa backports modules. 
Thanks for the effort, Trapper, but I've gone to synaptics and installed all the backports which seemed appropriate.  rebooted, and still no functioning microphone.  (It works in xp, so it wasn't DOA)

an you perhaps give me guidance on which backports and from where?  I'm competent in a terminal, as root or not.

It's a great wee machine, and seems fine in the karmic beta installation.  Got most of my previous functionality transferred from my damn-near=dead laptop, memory upgraded to 2 gig, and wireless fine.  Even getting used to the wee keyboard and touchpad...

Thanks in anticipation.  
Ciao
ed

---

### Post by tipiglen on 2009-10-24
> I've gone to synaptics and installed all the backports which seemed appropriate. rebooted, and still no functioning microphone. (It works in xp, so it wasn't DOA)

Scratch  that!  Mic and output were (unaccountably?) shut off in alsa mixer!

Everything's ticketty boo!

Now for the next hurdle....waiting to see whatr happens if I let the battery run right down (6.9% and counting - says 25 minutes)
[http://home2.btconnect.com/tipiglen/loveandpeace3.gif]("http://home2.btconnect.com/tipiglen/loveandpeace3.gif")
Salaam/Shalom/Shanthi/Peace
   Namaste -ed

---

### Post by T3CHKOMMIE on 2009-10-24
ive got the dailybuild on my 1005ha right now. everything works well so far, except the mic. i love the new interface. it is very clean looking and runs like a dream. i have to say this new 9.10 puts a smile on my face almost everytime i boot. 

i had droped wireless connections with jaunty about onces every 10 min. that is all gone now after i did a fresh resintall of 9.10. i wanted the new grubloader and the ext4 formatting. 

im supper happy that now my phone can (atleast) pair with bluetooth. but i still cant get it to send or recive files, or browse the device for that matter, anyone know about bluetooth not syncing well with their phones? 

other than that things are great for me. lots of daily updates. 

another question.... when the new general version is released in a few days, and im going to have to re imaged? or will my install just be updated to the current final build? anyone know?


thanks

---

### Post by tipiglen on 2009-10-25
> everything works well so far, except the mic. 

Look back a couple of posts.  Do the backports (they're in synaptics) and check your alsamixer settings.  

I find the mic level goes up if you set the "front" mic lower in the mixer, and the "sound" setter in the "system" applications section allows up to 150% output.

I agree about the new interface, but:
**some dialog popups seem to have size issues with the wee screen which make it tricky to get to "ok" - they aren't resizable or scrollable, unless someone knows a tweak**

Hint: <Alt><space> takes you to the "file" menu, and  "c" will close the application, but not always the same as "ok"

Still learning
ed

---

### Post by trapperjohn on 2009-10-25
@T3CHKOMMIE: Sending files from Ubuntu to my phone worked out-of-the-box, the other way needs some additional effort:

> **trapperjohn said:**
> If anyone wonders why it is not possible to receive files via Bluetooth: Install gnome-user-share and enable BT file receiption via its settings dialog (in German it's "System" -> "Persönliche Dateifreigabe", so it should be something like "Personal File Sharing" ...)

---

### Post by trapperjohn on 2009-10-25
> **tipiglen said:**
> 

I agree about the new interface, but:
**some dialog popups seem to have size issues with the wee screen which make it tricky to get to "ok" - they aren't resizable or scrollable, unless someone knows a tweak**



You can drag the dialog around while holding the [Alt] key.

If you don't want to have some (or all) applications maximized, just edit the settings of "Maximus" using gconf-editor.

---

### Post by tipiglen on 2009-10-25
> If you don't want to have some (or all) applications maximized, just edit the settings of "Maximus" using gconf-editor.
Thanks for that.  a great help to have stuff open small but enlargeable at will.  I like 'decorated' too.  Still awkward with popups.  the <alt> trick helps, but the one for 'add new card' in Thunderbird's address book is a right pain.  You move it up, and then it needs re-sizing, and the touchpad is none too easy at that...

I still reckon it's a great wee machine and a great installation.

Ciao

---

### Post by tipiglen on 2009-10-26
From Mozillazine forum (TB=Thunderbird):
> I've not seen this before, but TB will not Save or Send for me now. I'm on a Mac, OS 10.4.11, using TB 2.0.0.23 and I'm getting "Send Message Error Sending of message failed. Unable to open the temporary file. Check your 'Temporary Directory' setting." on attempts to send, and "Save Draft Error Unable to save your message as draft. Unable to open the temporary file. Check your 'Temporary Directory' setting." on attempts to save. Receiving messages is unaffected.

I just hit this problem, and I can't get gedit, Office writer, or even a terminal to open writable, so I can't save the meail before re-booting, and I can't change the file permissions because I ain't root, and can't get a terminal....

Grrrr! Going to try GKSU Nautilus

Even gksudo nautilus failed.  ctrl-alt-delete the only way out!
rebooting dropped me to a root prompt (but impotent in a read-only file system!)  
full permissions were already in place, and the problem was apparently fixed by running fsck "manually" and answereing all prompts "yes".

Now I can send emails again, but had to re-type the one I was working on.

Grrr!

New Asus eee 1005HA running ubuntu 9.10 beta netbook remix  Pretty good until this episode.

---

### Post by trapperjohn on 2009-10-26
Wow, that's bad. Sounds like an Ext4 corruption to me - but it's just a guess. Is there something in your /var/log/messages that indicates a critical filesystem error?

---

### Post by tipiglen on 2009-10-26
> Wow, that's bad. Sounds like an Ext4 corruption to me - but it's just a guess. Is there something in your /var/log/messages that indicates a critical filesystem error?

Dunno. Here's a dump of kern log:
```
Oct 26 11:29:11 asus kernel: [40728.026163] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Oct 26 11:41:55 asus kernel: [41492.201481] usb 1-3: USB disconnect, address 4
Oct 26 15:39:26 asus kernel: [55742.257135] usb 1-3: new high speed USB device using ehci_hcd and address 5
Oct 26 15:39:26 asus kernel: [55742.390160] usb 1-3: configuration #1 chosen from 1 choice
Oct 26 15:39:26 asus kernel: [55742.400209] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 26 15:39:26 asus kernel: [55742.405490] usb-storage: device found at 5
Oct 26 15:39:26 asus kernel: [55742.405502] usb-storage: waiting for device to settle before scanning
Oct 26 15:39:26 asus kernel: [55742.607252] usb 1-3: USB disconnect, address 5
Oct 26 15:39:27 asus kernel: [55743.889173] usb 1-3: new high speed USB device using ehci_hcd and address 6
Oct 26 15:39:27 asus kernel: [55744.023124] usb 1-3: configuration #1 chosen from 1 choice
Oct 26 15:39:27 asus kernel: [55744.037205] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 26 15:39:27 asus kernel: [55744.056008] usb-storage: device found at 6
Oct 26 15:39:27 asus kernel: [55744.056015] usb-storage: waiting for device to settle before scanning
Oct 26 15:39:32 asus kernel: [55749.072087] usb-storage: device scan complete
Oct 26 15:39:32 asus kernel: [55749.084482] scsi 6:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
Oct 26 15:39:32 asus kernel: [55749.088566] sd 6:0:0:0: Attached scsi generic sg1 type 0
Oct 26 15:39:33 asus kernel: [55749.599855] sd 6:0:0:0: [sdb] 1950720 512-byte logical blocks: (998 MB/952 MiB)
Oct 26 15:39:33 asus kernel: [55749.600730] sd 6:0:0:0: [sdb] Write Protect is off
Oct 26 15:39:33 asus kernel: [55749.600742] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Oct 26 15:39:33 asus kernel: [55749.600750] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct 26 15:39:33 asus kernel: [55749.632343] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct 26 15:39:33 asus kernel: [55749.632359]  sdb: sdb1
Oct 26 15:39:33 asus kernel: [55749.640341] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Oct 26 15:39:33 asus kernel: [55749.640356] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Oct 26 16:16:55 asus kernel: [57992.127011] usb 1-3: USB disconnect, address 6
Oct 26 18:13:50 asus kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Oct 26 18:13:51 asus kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 26 18:13:51 asus kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 26 18:13:51 asus kernel: [    0.000000] Linux version 2.6.31-14-generic-pae (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 (Ubuntu 2.6.31-14.48-generic-pae)
Oct 26 18:13:51 asus kernel: [    0.000000] KERNEL supported cpus:
Oct 26 18:13:51 asus kernel: [    0.000000]   Intel GenuineIntel

```I did pull out an SD photo card without unmounting  ;-(

I can't be sure of the time because I was so pissed off, but it was after 1700 when I found myself unable to post an email (or save it or open gedit, etc.)  And I reckon the 18:13:50 series is my successful re-start following the events described in my previous post (root shell, read only, fsck). Here's a huge dump of Messages

```
Oct 26 16:16:55 asus kernel: [57992.127011] usb 1-3: USB disconnect, address 6
Oct 26 16:25:58 asus pulseaudio[1398]: ratelimit.c: 3 events suppressed
Oct 26 18:13:50 asus kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Oct 26 18:13:50 asus rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="806" x-info="http://www.rsyslog.com"] (re)start
Oct 26 18:13:51 asus rsyslogd: rsyslogd's groupid changed to 102
Oct 26 18:13:51 asus rsyslogd: rsyslogd's userid changed to 101
Oct 26 18:13:51 asus kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 26 18:13:51 asus kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 26 18:13:51 asus kernel: [    0.000000] Linux version 2.6.31-14-generic-pae (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 (Ubuntu 2.6.31-14.48-generic-pae)
Oct 26 18:13:51 asus kernel: [    0.000000] KERNEL supported cpus:
Oct 26 18:13:51 asus kernel: [    0.000000]   Intel GenuineIntel
Oct 26 18:13:51 asus kernel: [    0.000000]   AMD AuthenticAMD
Oct 26 18:13:51 asus kernel: [    0.000000]   NSC Geode by NSC
Oct 26 18:13:51 asus kernel: [    0.000000]   Cyrix CyrixInstead
Oct 26 18:13:51 asus kernel: [    0.000000]   Centaur CentaurHauls
Oct 26 18:13:51 asus kernel: [    0.000000]   Transmeta GenuineTMx86
Oct 26 18:13:51 asus kernel: [    0.000000]   Transmeta TransmetaCPU
Oct 26 18:13:51 asus kernel: [    0.000000]   UMC UMC UMC UMC
Oct 26 18:13:51 asus kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000] DMI present.
Oct 26 18:13:51 asus kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Oct 26 18:13:51 asus kernel: [    0.000000] last_pfn = 0x7f7a0 max_arch_pfn = 0x1000000
Oct 26 18:13:51 asus kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 26 18:13:51 asus kernel: [    0.000000] Scanning 0 areas for low memory corruption
Oct 26 18:13:51 asus kernel: [    0.000000] modified physical RAM map:
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 0000000000100000 - 000000007f7a0000 (usable)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 000000007f7f0000 - 000000007f800000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Oct 26 18:13:51 asus kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
Oct 26 18:13:51 asus kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 26 18:13:51 asus kernel: [    0.000000] RAMDISK: 3789d000 - 37fef218
Oct 26 18:13:51 asus kernel: [    0.000000] Allocated new RAMDISK: 008b5000 - 01007218
Oct 26 18:13:51 asus kernel: [    0.000000] Move RAMDISK from 000000003789d000 - 0000000037fef217 to 008b5000 - 01007217
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: RSDP 000fb9e0 00014 (v00 ACPIAM)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: RSDT 7f7a0000 0003C (v01 A_M_I_ OEMRSDT  10000916 MSFT 00000097)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: FACP 7f7a0200 00084 (v02 A_M_I_ OEMFACP  10000916 MSFT 00000097)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: DSDT 7f7a0430 080AF (v01  A1311 A1311000 00000000 INTL 20051117)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: FACS 7f7ae000 00040
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: APIC 7f7a0390 0005C (v01 A_M_I_ OEMAPIC  10000916 MSFT 00000097)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: MCFG 7f7a03f0 0003C (v01 A_M_I_ OEMMCFG  10000916 MSFT 00000097)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: OEMB 7f7ae040 00061 (v01 A_M_I_ AMI_OEM  10000916 MSFT 00000097)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: HPET 7f7a84e0 00038 (v01 A_M_I_ OEMHPET  10000916 MSFT 00000097)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: SSDT 7f7aeb40 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Oct 26 18:13:51 asus kernel: [    0.000000] 1149MB HIGHMEM available.
Oct 26 18:13:51 asus kernel: [    0.000000] 889MB LOWMEM available.
Oct 26 18:13:51 asus kernel: [    0.000000]   mapped low ram: 0 - 379fe000
Oct 26 18:13:51 asus kernel: [    0.000000]   low ram: 0 - 379fe000
Oct 26 18:13:51 asus kernel: [    0.000000]   node 0 low ram: 00000000 - 379fe000
Oct 26 18:13:51 asus kernel: [    0.000000]   node 0 bootmap 00012000 - 00018f40
Oct 26 18:13:51 asus kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
Oct 26 18:13:51 asus kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Oct 26 18:13:51 asus kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Oct 26 18:13:51 asus kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Oct 26 18:13:51 asus kernel: [    0.000000]   #3 [0000100000 - 00008ad9a0]    TEXT DATA BSS ==> [0000100000 - 00008ad9a0]
Oct 26 18:13:51 asus kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Oct 26 18:13:51 asus kernel: [    0.000000]   #5 [00008ae000 - 00008b41e0]              BRK ==> [00008ae000 - 00008b41e0]
Oct 26 18:13:51 asus kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Oct 26 18:13:51 asus kernel: [    0.000000]   #7 [00008b5000 - 0001007218]      NEW RAMDISK ==> [00008b5000 - 0001007218]
Oct 26 18:13:51 asus kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Oct 26 18:13:51 asus kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Oct 26 18:13:51 asus kernel: [    0.000000] Zone PFN ranges:
Oct 26 18:13:51 asus kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 26 18:13:51 asus kernel: [    0.000000]   Normal   0x00001000 -> 0x000379fe
Oct 26 18:13:51 asus kernel: [    0.000000]   HighMem  0x000379fe -> 0x0007f7a0
Oct 26 18:13:51 asus kernel: [    0.000000] Movable zone start PFN for each node
Oct 26 18:13:51 asus kernel: [    0.000000] early_node_map[2] active PFN ranges
Oct 26 18:13:51 asus kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 26 18:13:51 asus kernel: [    0.000000]     0: 0x00000100 -> 0x0007f7a0
Oct 26 18:13:51 asus kernel: [    0.000000] Using APIC driver default
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 26 18:13:51 asus kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 26 18:13:51 asus kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 26 18:13:51 asus kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 26 18:13:51 asus kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Oct 26 18:13:51 asus kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Oct 26 18:13:51 asus kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 26 18:13:51 asus kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Oct 26 18:13:51 asus kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Oct 26 18:13:51 asus kernel: [    0.000000] Allocating PCI resources starting at 7f800000 (gap: 7f800000:7f600000)
Oct 26 18:13:51 asus kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Oct 26 18:13:51 asus kernel: [    0.000000] PERCPU: Embedded 14 pages at c2002000, static data 35612 bytes
Oct 26 18:13:51 asus kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517951
Oct 26 18:13:51 asus kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=4f5dd19c-2d99-4a9e-bac7-09c93fae1fd2 ro quiet splash
Oct 26 18:13:51 asus kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 26 18:13:51 asus kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 26 18:13:51 asus kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 26 18:13:51 asus kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 26 18:13:51 asus kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 26 18:13:51 asus kernel: [    0.000000] Initializing CPU#0
Oct 26 18:13:51 asus kernel: [    0.000000] allocated 10442560 bytes of page_cgroup
Oct 26 18:13:51 asus kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 26 18:13:51 asus kernel: [    0.000000] Initializing HighMem for node 0 (000379fe:0007f7a0)
Oct 26 18:13:51 asus kernel: [    0.000000] Memory: 2044384k/2088576k available (4588k kernel code, 42880k reserved, 2148k data, 544k init, 1177224k highmem)
Oct 26 18:13:51 asus kernel: [    0.000000] virtual kernel memory layout:
Oct 26 18:13:51 asus kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Oct 26 18:13:51 asus kernel: [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
Oct 26 18:13:51 asus kernel: [    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
Oct 26 18:13:51 asus kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
Oct 26 18:13:51 asus kernel: [    0.000000]       .init : 0xc0795000 - 0xc081d000   ( 544 kB)
Oct 26 18:13:51 asus kernel: [    0.000000]       .data : 0xc057b314 - 0xc07946e8   (2148 kB)
Oct 26 18:13:51 asus kernel: [    0.000000]       .text : 0xc0100000 - 0xc057b314   (4588 kB)
Oct 26 18:13:51 asus kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Oct 26 18:13:51 asus kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Oct 26 18:13:51 asus kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Oct 26 18:13:51 asus kernel: [    0.000000] Fast TSC calibration using PIT
Oct 26 18:13:51 asus kernel: [    0.000000] Detected 1666.487 MHz processor.
Oct 26 18:13:51 asus kernel: [    0.001659] Console: colour VGA+ 80x25
Oct 26 18:13:51 asus kernel: [    0.001665] console [tty0] enabled
Oct 26 18:13:51 asus kernel: [    0.001909] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Oct 26 18:13:51 asus kernel: [    0.001920] Calibrating delay loop (skipped), value calculated using timer frequency.. 3332.97 BogoMIPS (lpj=6665948)
Oct 26 18:13:51 asus kernel: [    0.001955] Security Framework initialized
Oct 26 18:13:51 asus kernel: [    0.001992] AppArmor: AppArmor initialized
Oct 26 18:13:51 asus kernel: [    0.002006] Mount-cache hash table entries: 512
Oct 26 18:13:51 asus kernel: [    0.002216] Initializing cgroup subsys ns
Oct 26 18:13:51 asus kernel: [    0.002226] Initializing cgroup subsys cpuacct
Oct 26 18:13:51 asus kernel: [    0.002235] Initializing cgroup subsys memory
Oct 26 18:13:51 asus kernel: [    0.002246] Initializing cgroup subsys freezer
Oct 26 18:13:51 asus kernel: [    0.002251] Initializing cgroup subsys net_cls
Oct 26 18:13:51 asus kernel: [    0.002275] CPU: L1 I cache: 32K, L1 D cache: 24K
Oct 26 18:13:51 asus kernel: [    0.002281] CPU: L2 cache: 512K
Oct 26 18:13:51 asus kernel: [    0.002286] CPU: Physical Processor ID: 0
Oct 26 18:13:51 asus kernel: [    0.002290] CPU: Processor Core ID: 0
Oct 26 18:13:51 asus kernel: [    0.002296] mce: CPU supports 5 MCE banks
Oct 26 18:13:51 asus kernel: [    0.002310] CPU0: Thermal monitoring enabled (TM2)
Oct 26 18:13:51 asus kernel: [    0.002317] using mwait in idle threads.
Oct 26 18:13:51 asus kernel: [    0.002329] Performance Counters: Atom events, Intel PMU driver.
Oct 26 18:13:51 asus kernel: [    0.002340] ... version:                 3
Oct 26 18:13:51 asus kernel: [    0.002344] ... bit width:               40
Oct 26 18:13:51 asus kernel: [    0.002348] ... generic counters:        2
Oct 26 18:13:51 asus kernel: [    0.002352] ... value mask:              000000ffffffffff
Oct 26 18:13:51 asus kernel: [    0.002357] ... max period:              000000007fffffff
Oct 26 18:13:51 asus kernel: [    0.002361] ... fixed-purpose counters:  3
Oct 26 18:13:51 asus kernel: [    0.002365] ... counter mask:            0000000700000003
Oct 26 18:13:51 asus kernel: [    0.002373] Checking 'hlt' instruction... OK.
Oct 26 18:13:51 asus kernel: [    0.019919] ACPI: Core revision 20090521
Oct 26 18:13:51 asus kernel: [    0.040493] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 26 18:13:51 asus kernel: [    0.081188] CPU0: Intel(R) Atom(TM) CPU N280   @ 1.66GHz stepping 02
Oct 26 18:13:51 asus kernel: [    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
Oct 26 18:13:51 asus kernel: [    0.004000] Initializing CPU#1
Oct 26 18:13:51 asus kernel: [    0.004000] Calibrating delay using timer specific routine.. 3332.91 BogoMIPS (lpj=6665832)
Oct 26 18:13:51 asus kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
Oct 26 18:13:51 asus kernel: [    0.004000] CPU: L2 cache: 512K
Oct 26 18:13:51 asus kernel: [    0.004000] CPU: Physical Processor ID: 0
Oct 26 18:13:51 asus kernel: [    0.004000] CPU: Processor Core ID: 0
Oct 26 18:13:51 asus kernel: [    0.004000] mce: CPU supports 5 MCE banks
Oct 26 18:13:51 asus kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM2)
Oct 26 18:13:51 asus kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Oct 26 18:13:51 asus kernel: [    0.168971] CPU1: Intel(R) Atom(TM) CPU N280   @ 1.66GHz stepping 02
Oct 26 18:13:51 asus kernel: [    0.168999] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 26 18:13:51 asus kernel: [    0.172048] Brought up 2 CPUs
Oct 26 18:13:51 asus kernel: [    0.172055] Total of 2 processors activated (6665.89 BogoMIPS).
Oct 26 18:13:51 asus kernel: [    0.172305] Booting paravirtualized kernel on bare hardware
Oct 26 18:13:51 asus kernel: [    0.172460] regulator: core version 0.5
Oct 26 18:13:51 asus kernel: [    0.172460] Time: 18:13:39  Date: 10/26/09
Oct 26 18:13:51 asus kernel: [    0.172460] NET: Registered protocol family 16
Oct 26 18:13:51 asus kernel: [    0.172460] EISA bus registered
Oct 26 18:13:51 asus kernel: [    0.172460] ACPI: bus type pci registered
Oct 26 18:13:51 asus kernel: [    0.172571] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Oct 26 18:13:51 asus kernel: [    0.172578] PCI: Not using MMCONFIG.
Oct 26 18:13:51 asus kernel: [    0.172870] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Oct 26 18:13:51 asus kernel: [    0.172875] PCI: Using configuration type 1 for base access
Oct 26 18:13:51 asus kernel: [    0.177118] bio: create slab <bio-0> at 0
Oct 26 18:13:51 asus kernel: [    0.192374] ACPI: Interpreter enabled
Oct 26 18:13:51 asus kernel: [    0.192387] ACPI: (supports S0 S1 S3 S4 S5)
Oct 26 18:13:51 asus kernel: [    0.192443] ACPI: Using IOAPIC for interrupt routing
Oct 26 18:13:51 asus kernel: [    0.192559] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Oct 26 18:13:51 asus kernel: [    0.194234] ACPI: BIOS _OSI(Linux) query ignored
Oct 26 18:13:51 asus kernel: [    0.197242] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Oct 26 18:13:51 asus kernel: [    0.197249] PCI: Using MMCONFIG for extended config space
Oct 26 18:13:51 asus kernel: [    0.210578] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Oct 26 18:13:51 asus kernel: [    0.210585] ACPI: EC: driver started in poll mode
Oct 26 18:13:51 asus kernel: [    0.211050] ACPI: No dock devices found.
Oct 26 18:13:51 asus kernel: [    0.211310] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 26 18:13:51 asus kernel: [    0.211739] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.211747] pci 0000:00:1b.0: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.211851] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.211860] pci 0000:00:1c.0: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.211966] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.211975] pci 0000:00:1c.1: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.212095] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.212103] pci 0000:00:1c.3: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.212589] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.212597] pci 0000:00:1d.7: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.212784] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Oct 26 18:13:51 asus kernel: [    0.212793] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Oct 26 18:13:51 asus kernel: [    0.212801] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0380 (mask 0003)
Oct 26 18:13:51 asus kernel: [    0.212809] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 0007)
Oct 26 18:13:51 asus kernel: [    0.212817] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
Oct 26 18:13:51 asus kernel: [    0.213009] pci 0000:00:1f.2: PME# supported from D3hot
Oct 26 18:13:51 asus kernel: [    0.213016] pci 0000:00:1f.2: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.213291] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.213301] pci 0000:02:00.0: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.213603] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 26 18:13:51 asus kernel: [    0.213612] pci 0000:01:00.0: PME# disabled
Oct 26 18:13:51 asus kernel: [    0.213786] pci 0000:00:1e.0: transparent bridge
Oct 26 18:13:51 asus kernel: [    0.236028] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Oct 26 18:13:51 asus kernel: [    0.236287] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 26 18:13:51 asus kernel: [    0.236539] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 26 18:13:51 asus kernel: [    0.236792] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 26 18:13:51 asus kernel: [    0.237045] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 26 18:13:51 asus kernel: [    0.237300] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 26 18:13:51 asus kernel: [    0.237553] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Oct 26 18:13:51 asus kernel: [    0.237806] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 26 18:13:51 asus kernel: [    0.238210] SCSI subsystem initialized
Oct 26 18:13:51 asus kernel: [    0.238246] usbcore: registered new interface driver usbfs
Oct 26 18:13:51 asus kernel: [    0.238246] usbcore: registered new interface driver hub
Oct 26 18:13:51 asus kernel: [    0.238246] usbcore: registered new device driver usb
Oct 26 18:13:51 asus kernel: [    0.238246] ACPI: WMI: Mapper loaded
Oct 26 18:13:51 asus kernel: [    0.238246] PCI: Using ACPI for IRQ routing
Oct 26 18:13:51 asus kernel: [    0.248021] Bluetooth: Core ver 2.15
Oct 26 18:13:51 asus kernel: [    0.248066] NET: Registered protocol family 31
Oct 26 18:13:51 asus kernel: [    0.248066] Bluetooth: HCI device and connection manager initialized
Oct 26 18:13:51 asus kernel: [    0.248066] Bluetooth: HCI socket layer initialized
Oct 26 18:13:51 asus kernel: [    0.248066] NetLabel: Initializing
Oct 26 18:13:51 asus kernel: [    0.248066] NetLabel:  domain hash size = 128
Oct 26 18:13:51 asus kernel: [    0.248066] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 26 18:13:51 asus kernel: [    0.248078] NetLabel:  unlabeled traffic allowed by default
Oct 26 18:13:51 asus kernel: [    0.248148] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 26 18:13:51 asus kernel: [    0.248159] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Oct 26 18:13:51 asus kernel: [    0.265058] pnp: PnP ACPI init
Oct 26 18:13:51 asus kernel: [    0.265097] ACPI: bus type pnp registered
Oct 26 18:13:51 asus kernel: [    0.269337] pnp: PnP ACPI: found 13 devices
Oct 26 18:13:51 asus kernel: [    0.269344] ACPI: ACPI bus type pnp unregistered
Oct 26 18:13:51 asus kernel: [    0.269352] PnPBIOS: Disabled by ACPI PNP
Oct 26 18:13:51 asus kernel: [    0.269379] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269399] system 00:08: ioport range 0x25c-0x25f has been reserved
Oct 26 18:13:51 asus kernel: [    0.269407] system 00:08: ioport range 0x380-0x383 has been reserved
Oct 26 18:13:51 asus kernel: [    0.269413] system 00:08: ioport range 0x400-0x41f has been reserved
Oct 26 18:13:51 asus kernel: [    0.269420] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Oct 26 18:13:51 asus kernel: [    0.269427] system 00:08: ioport range 0x800-0x87f has been reserved
Oct 26 18:13:51 asus kernel: [    0.269434] system 00:08: ioport range 0x480-0x4bf has been reserved
Oct 26 18:13:51 asus kernel: [    0.269442] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269449] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269461] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269469] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269476] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269483] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
Oct 26 18:13:51 asus kernel: [    0.269498] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 26 18:13:51 asus kernel: [    0.269506] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269518] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
Oct 26 18:13:51 asus kernel: [    0.269533] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Oct 26 18:13:51 asus kernel: [    0.269540] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Oct 26 18:13:51 asus kernel: [    0.269547] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Oct 26 18:13:51 asus kernel: [    0.269554] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
Oct 26 18:13:51 asus kernel: [    0.304398] AppArmor: AppArmor Filesystem Enabled
Oct 26 18:13:51 asus kernel: [    0.304476] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
Oct 26 18:13:51 asus kernel: [    0.304482] pci 0000:00:1c.0:   IO window: disabled
Oct 26 18:13:51 asus kernel: [    0.304491] pci 0000:00:1c.0:   MEM window: disabled
Oct 26 18:13:51 asus kernel: [    0.304499] pci 0000:00:1c.0:   PREFETCH window: disabled
Oct 26 18:13:51 asus kernel: [    0.304508] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Oct 26 18:13:51 asus kernel: [    0.304513] pci 0000:00:1c.1:   IO window: disabled
Oct 26 18:13:51 asus kernel: [    0.304523] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xfbffffff
Oct 26 18:13:51 asus kernel: [    0.304533] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
Oct 26 18:13:51 asus kernel: [    0.304546] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01
Oct 26 18:13:51 asus kernel: [    0.304553] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
Oct 26 18:13:51 asus kernel: [    0.304563] pci 0000:00:1c.3:   MEM window: 0xf7f00000-0xf7ffffff
Oct 26 18:13:51 asus kernel: [    0.304571] pci 0000:00:1c.3:   PREFETCH window: disabled
Oct 26 18:13:51 asus kernel: [    0.304580] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Oct 26 18:13:51 asus kernel: [    0.304585] pci 0000:00:1e.0:   IO window: disabled
Oct 26 18:13:51 asus kernel: [    0.304594] pci 0000:00:1e.0:   MEM window: disabled
Oct 26 18:13:51 asus kernel: [    0.304601] pci 0000:00:1e.0:   PREFETCH window: disabled
Oct 26 18:13:51 asus kernel: [    0.304644] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 26 18:13:51 asus kernel: [    0.304681] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 26 18:13:51 asus kernel: [    0.304716] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 26 18:13:51 asus kernel: [    0.304862] NET: Registered protocol family 2
Oct 26 18:13:51 asus kernel: [    0.305076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 26 18:13:51 asus kernel: [    0.305703] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 26 18:13:51 asus kernel: [    0.306635] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 26 18:13:51 asus kernel: [    0.307054] TCP: Hash tables configured (established 131072 bind 65536)
Oct 26 18:13:51 asus kernel: [    0.307061] TCP reno registered
Oct 26 18:13:51 asus kernel: [    0.307256] NET: Registered protocol family 1
Oct 26 18:13:51 asus kernel: [    0.307390] Trying to unpack rootfs image as initramfs...
Oct 26 18:13:51 asus kernel: [    0.654196] Freeing initrd memory: 7496k freed
Oct 26 18:13:51 asus kernel: [    0.661132] cpufreq-nforce2: No nForce2 chipset.
Oct 26 18:13:51 asus kernel: [    0.661192] Scanning for low memory corruption every 60 seconds
Oct 26 18:13:51 asus kernel: [    0.661399] audit: initializing netlink socket (disabled)
Oct 26 18:13:51 asus kernel: [    0.661428] type=2000 audit(1256580818.661:1): initialized
Oct 26 18:13:51 asus kernel: [    0.678218] highmem bounce pool size: 64 pages
Oct 26 18:13:51 asus kernel: [    0.678230] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 26 18:13:51 asus kernel: [    0.681227] VFS: Disk quotas dquot_6.5.2
Oct 26 18:13:51 asus kernel: [    0.681356] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 26 18:13:51 asus kernel: [    0.682573] fuse init (API version 7.12)
Oct 26 18:13:51 asus kernel: [    0.682753] msgmni has been set to 1710
Oct 26 18:13:51 asus kernel: [    0.683188] alg: No test for stdrng (krng)
Oct 26 18:13:51 asus kernel: [    0.683221] io scheduler noop registered
Oct 26 18:13:51 asus kernel: [    0.683226] io scheduler anticipatory registered
Oct 26 18:13:51 asus kernel: [    0.683230] io scheduler deadline registered
Oct 26 18:13:51 asus kernel: [    0.683335] io scheduler cfq registered (default)
Oct 26 18:13:51 asus kernel: [    0.684405] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 26 18:13:51 asus kernel: [    0.684632] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 26 18:13:51 asus kernel: [    0.684908] ACPI: AC Adapter [AC0] (on-line)
Oct 26 18:13:51 asus kernel: [    0.685076] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Oct 26 18:13:51 asus kernel: [    0.685084] ACPI: Power Button [PWRF]
Oct 26 18:13:51 asus kernel: [    0.685207] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Oct 26 18:13:51 asus kernel: [    0.686466] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 26 18:13:51 asus kernel: [    0.711844] ACPI: Lid Switch [LID]
Oct 26 18:13:51 asus kernel: [    0.711962] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Oct 26 18:13:51 asus kernel: [    0.711969] ACPI: Sleep Button [SLPB]
Oct 26 18:13:51 asus kernel: [    0.712080] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
Oct 26 18:13:51 asus kernel: [    0.712087] ACPI: Power Button [PWRB]
Oct 26 18:13:51 asus kernel: [    0.713462] ACPI: SSDT 7f7ae180 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Oct 26 18:13:51 asus kernel: [    0.714497] ACPI: SSDT 7f7ae410 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Oct 26 18:13:51 asus kernel: [    0.715401] Marking TSC unstable due to TSC halts in idle
Oct 26 18:13:51 asus kernel: [    0.715436] ACPI: CPU0 (power states: C1[C1] C2[C2])
Oct 26 18:13:51 asus kernel: [    0.715492] processor LNXCPU:00: registered as cooling_device0
Oct 26 18:13:51 asus kernel: [    0.715501] ACPI: Processor [CPU0] (supports 8 throttling states)
Oct 26 18:13:51 asus kernel: [    0.716237] ACPI: SSDT 7f7ae0b0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
Oct 26 18:13:51 asus kernel: [    0.716927] ACPI: SSDT 7f7ae380 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
Oct 26 18:13:51 asus kernel: [    0.717939] ACPI: CPU1 (power states: C1[C1] C2[C2])
Oct 26 18:13:51 asus kernel: [    0.717987] processor LNXCPU:01: registered as cooling_device1
Oct 26 18:13:51 asus kernel: [    0.717996] ACPI: Processor [CPU1] (supports 8 throttling states)
Oct 26 18:13:51 asus kernel: [    0.726807] thermal LNXTHERM:01: registered as thermal_zone0
Oct 26 18:13:51 asus kernel: [    0.726825] ACPI: Thermal Zone [TZ00] (57 C)
Oct 26 18:13:51 asus kernel: [    0.726973] isapnp: Scanning for PnP cards...
Oct 26 18:13:51 asus kernel: [    0.790605] ACPI: Battery Slot [BAT0] (battery present)
Oct 26 18:13:51 asus kernel: [    1.081535] isapnp: No Plug & Play device found
Oct 26 18:13:51 asus kernel: [    1.084205] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Oct 26 18:13:51 asus kernel: [    1.086802] brd: module loaded
Oct 26 18:13:51 asus kernel: [    1.087757] loop: module loaded
Oct 26 18:13:51 asus kernel: [    1.087926] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Oct 26 18:13:51 asus kernel: [    1.088163] ahci 0000:00:1f.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
Oct 26 18:13:51 asus kernel: [    1.088344] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
Oct 26 18:13:51 asus kernel: [    1.088352] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
Oct 26 18:13:51 asus kernel: [    1.088607] scsi0 : ahci
Oct 26 18:13:51 asus kernel: [    1.088816] scsi1 : ahci
Oct 26 18:13:51 asus kernel: [    1.088942] scsi2 : ahci
Oct 26 18:13:51 asus kernel: [    1.089090] scsi3 : ahci
Oct 26 18:13:51 asus kernel: [    1.089461] ata1: SATA max UDMA/133 abar m1024@0xf7db7800 port 0xf7db7900 irq 27
Oct 26 18:13:51 asus kernel: [    1.089468] ata2: DUMMY
Oct 26 18:13:51 asus kernel: [    1.089471] ata3: DUMMY
Oct 26 18:13:51 asus kernel: [    1.089475] ata4: DUMMY
Oct 26 18:13:51 asus kernel: [    1.091420] Fixed MDIO Bus: probed
Oct 26 18:13:51 asus kernel: [    1.091498] PPP generic driver version 2.4.2
Oct 26 18:13:51 asus kernel: [    1.091708] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 26 18:13:51 asus kernel: [    1.091771] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 26 18:13:51 asus kernel: [    1.091810] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 26 18:13:51 asus kernel: [    1.091906] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Oct 26 18:13:51 asus kernel: [    1.095829] ehci_hcd 0000:00:1d.7: debug port 1
Oct 26 18:13:51 asus kernel: [    1.095869] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7db7c00
Oct 26 18:13:51 asus kernel: [    1.108024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Oct 26 18:13:51 asus kernel: [    1.108184] usb usb1: configuration #1 chosen from 1 choice
Oct 26 18:13:51 asus kernel: [    1.108247] hub 1-0:1.0: USB hub found
Oct 26 18:13:51 asus kernel: [    1.108263] hub 1-0:1.0: 8 ports detected
Oct 26 18:13:51 asus kernel: [    1.108413] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 26 18:13:51 asus kernel: [    1.108454] uhci_hcd: USB Universal Host Controller Interface driver
Oct 26 18:13:51 asus kernel: [    1.108520] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 26 18:13:51 asus kernel: [    1.108541] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 26 18:13:51 asus kernel: [    1.108609] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 26 18:13:51 asus kernel: [    1.108647] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
Oct 26 18:13:51 asus kernel: [    1.108811] usb usb2: configuration #1 chosen from 1 choice
Oct 26 18:13:51 asus kernel: [    1.108875] hub 2-0:1.0: USB hub found
Oct 26 18:13:51 asus kernel: [    1.108890] hub 2-0:1.0: 2 ports detected
Oct 26 18:13:51 asus kernel: [    1.108980] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 26 18:13:51 asus kernel: [    1.108999] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 26 18:13:51 asus kernel: [    1.109062] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Oct 26 18:13:51 asus kernel: [    1.109111] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
Oct 26 18:13:51 asus kernel: [    1.109276] usb usb3: configuration #1 chosen from 1 choice
Oct 26 18:13:51 asus kernel: [    1.109335] hub 3-0:1.0: USB hub found
Oct 26 18:13:51 asus kernel: [    1.109349] hub 3-0:1.0: 2 ports detected
Oct 26 18:13:51 asus kernel: [    1.109438] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 26 18:13:51 asus kernel: [    1.109458] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 26 18:13:51 asus kernel: [    1.109525] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Oct 26 18:13:51 asus kernel: [    1.109572] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
Oct 26 18:13:51 asus kernel: [    1.109735] usb usb4: configuration #1 chosen from 1 choice
Oct 26 18:13:51 asus kernel: [    1.109795] hub 4-0:1.0: USB hub found
Oct 26 18:13:51 asus kernel: [    1.109809] hub 4-0:1.0: 2 ports detected
Oct 26 18:13:51 asus kernel: [    1.109899] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Oct 26 18:13:51 asus kernel: [    1.109922] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 26 18:13:51 asus kernel: [    1.109987] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Oct 26 18:13:51 asus kernel: [    1.110034] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
Oct 26 18:13:51 asus kernel: [    1.110196] usb usb5: configuration #1 chosen from 1 choice
Oct 26 18:13:51 asus kernel: [    1.110255] hub 5-0:1.0: USB hub found
Oct 26 18:13:51 asus kernel: [    1.110270] hub 5-0:1.0: 2 ports detected
Oct 26 18:13:51 asus kernel: [    1.110458] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct 26 18:13:51 asus kernel: [    1.132152] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 26 18:13:51 asus kernel: [    1.132166] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 26 18:13:51 asus kernel: [    1.132307] mice: PS/2 mouse device common for all mice
Oct 26 18:13:51 asus kernel: [    1.132565] rtc_cmos 00:03: RTC can wake from S4
Oct 26 18:13:51 asus kernel: [    1.132638] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Oct 26 18:13:51 asus kernel: [    1.132680] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Oct 26 18:13:51 asus kernel: [    1.132927] device-mapper: uevent: version 1.0.3
Oct 26 18:13:51 asus kernel: [    1.133631] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Oct 26 18:13:51 asus kernel: [    1.133822] device-mapper: multipath: version 1.1.0 loaded
Oct 26 18:13:51 asus kernel: [    1.133829] device-mapper: multipath round-robin: version 1.0.0 loaded
Oct 26 18:13:51 asus kernel: [    1.134124] EISA: Probing bus 0 at eisa.0
Oct 26 18:13:51 asus kernel: [    1.134172] EISA: Detected 0 cards.
Oct 26 18:13:51 asus kernel: [    1.134517] cpuidle: using governor ladder
Oct 26 18:13:51 asus kernel: [    1.134707] cpuidle: using governor menu
Oct 26 18:13:51 asus kernel: [    1.135786] TCP cubic registered
Oct 26 18:13:51 asus kernel: [    1.136158] NET: Registered protocol family 10
Oct 26 18:13:51 asus kernel: [    1.137119] lo: Disabled Privacy Extensions
Oct 26 18:13:51 asus kernel: [    1.137803] NET: Registered protocol family 17
Oct 26 18:13:51 asus kernel: [    1.137848] Bluetooth: L2CAP ver 2.13
Oct 26 18:13:51 asus kernel: [    1.137853] Bluetooth: L2CAP socket layer initialized
Oct 26 18:13:51 asus kernel: [    1.137859] Bluetooth: SCO (Voice Link) ver 0.6
Oct 26 18:13:51 asus kernel: [    1.137862] Bluetooth: SCO socket layer initialized
Oct 26 18:13:51 asus kernel: [    1.137952] Bluetooth: RFCOMM TTY layer initialized
Oct 26 18:13:51 asus kernel: [    1.137960] Bluetooth: RFCOMM socket layer initialized
Oct 26 18:13:51 asus kernel: [    1.137964] Bluetooth: RFCOMM ver 1.11
Oct 26 18:13:51 asus kernel: [    1.138815] Using IPI No-Shortcut mode
Oct 26 18:13:51 asus kernel: [    1.138998] registered taskstats version 1
Oct 26 18:13:51 asus kernel: [    1.139207]   Magic number: 13:57:242
Oct 26 18:13:51 asus kernel: [    1.139337] rtc_cmos 00:03: setting system clock to 2009-10-26 18:13:40 UTC (1256580820)
Oct 26 18:13:51 asus kernel: [    1.139345] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 26 18:13:51 asus kernel: [    1.139350] EDD information not available.
Oct 26 18:13:51 asus kernel: [    1.150980] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Oct 26 18:13:51 asus kernel: [    1.416093] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 26 18:13:51 asus kernel: [    1.418119] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Oct 26 18:13:51 asus kernel: [    1.418506] ata1.00: ATA-8: ST9160314AS, 0002SDM1, max UDMA/133
Oct 26 18:13:51 asus kernel: [    1.418518] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Oct 26 18:13:51 asus kernel: [    1.420077] usb 1-2: new high speed USB device using ehci_hcd and address 2
Oct 26 18:13:51 asus kernel: [    1.421023] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
Oct 26 18:13:51 asus kernel: [    1.421425] ata1.00: configured for UDMA/133
Oct 26 18:13:51 asus kernel: [    1.436364] scsi 0:0:0:0: Direct-Access     ATA      ST9160314AS      0002 PQ: 0 ANSI: 5
Oct 26 18:13:51 asus kernel: [    1.436643] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 26 18:13:51 asus kernel: [    1.436763] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Oct 26 18:13:51 asus kernel: [    1.436897] sd 0:0:0:0: [sda] Write Protect is off
Oct 26 18:13:51 asus kernel: [    1.436974] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 26 18:13:51 asus kernel: [    1.437330]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3 sda4
Oct 26 18:13:51 asus kernel: [    1.492140] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 26 18:13:51 asus kernel: [    1.492189] Freeing unused kernel memory: 544k freed
Oct 26 18:13:51 asus kernel: [    1.492648] Write protecting the kernel text: 4592k
Oct 26 18:13:51 asus kernel: [    1.492793] Write protecting the kernel read-only data: 1836k
Oct 26 18:13:51 asus kernel: [    1.630655] usb 1-2: configuration #1 chosen from 1 choice
Oct 26 18:13:51 asus kernel: [    1.782121] acpi device:39: registered as cooling_device2
Oct 26 18:13:51 asus kernel: [    1.782536] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:36/input/input6
Oct 26 18:13:51 asus kernel: [    1.782648] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Oct 26 18:13:51 asus kernel: [    1.831582] Linux agpgart interface v0.103
Oct 26 18:13:51 asus kernel: [    1.842323] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Oct 26 18:13:51 asus kernel: [    1.842609] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Oct 26 18:13:51 asus kernel: [    1.845529] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Oct 26 18:13:51 asus kernel: [    1.997997] [drm] Initialized drm 1.1.0 20060810
Oct 26 18:13:51 asus kernel: [    2.058084] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 26 18:13:51 asus kernel: [    2.287323] [drm] fb0: inteldrmfb frame buffer device
Oct 26 18:13:51 asus kernel: [    2.287340] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 26 18:13:51 asus kernel: [    2.612479] [drm] LVDS-8: set mode 1024x600 e
Oct 26 18:13:51 asus kernel: [    3.023489] Console: switching to colour frame buffer device 128x37
Oct 26 18:13:51 asus kernel: [    3.631721] PM: Starting manual resume from disk
Oct 26 18:13:51 asus kernel: [    3.667382] EXT4-fs (sda5): barriers enabled
Oct 26 18:13:51 asus kernel: [    3.678459] kjournald2 starting: pid 376, dev sda5:8, commit interval 5 seconds
Oct 26 18:13:51 asus kernel: [    3.678508] EXT4-fs (sda5): delayed allocation enabled
Oct 26 18:13:51 asus kernel: [    3.678516] EXT4-fs: file extents enabled
Oct 26 18:13:51 asus kernel: [    3.683461] EXT4-fs: mballoc enabled
Oct 26 18:13:51 asus kernel: [    3.683491] EXT4-fs (sda5): mounted filesystem with ordered data mode
Oct 26 18:13:51 asus kernel: [    4.457488] type=1505 audit(1256580823.816:2): operation="profile_load" pid=399 name=/sbin/dhclient3
Oct 26 18:13:51 asus kernel: [    4.458047] type=1505 audit(1256580823.816:3): operation="profile_load" pid=399 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Oct 26 18:13:51 asus kernel: [    4.458370] type=1505 audit(1256580823.816:4): operation="profile_load" pid=399 name=/usr/lib/connman/scripts/dhclient-script
Oct 26 18:13:51 asus kernel: [    4.496808] type=1505 audit(1256580823.856:5): operation="profile_load" pid=400 name=/usr/bin/evince
Oct 26 18:13:51 asus kernel: [    4.505436] type=1505 audit(1256580823.864:6): operation="profile_load" pid=400 name=/usr/bin/evince-previewer
Oct 26 18:13:51 asus kernel: [    4.510672] type=1505 audit(1256580823.868:7): operation="profile_load" pid=400 name=/usr/bin/evince-thumbnailer
Oct 26 18:13:51 asus kernel: [    4.546379] type=1505 audit(1256580823.904:8): operation="profile_load" pid=402 name=/usr/lib/cups/backend/cups-pdf
Oct 26 18:13:51 asus kernel: [    4.547082] type=1505 audit(1256580823.904:9): operation="profile_load" pid=402 name=/usr/sbin/cupsd
Oct 26 18:13:51 asus kernel: [    5.439008] Adding 3582452k swap on /dev/sda7.  Priority:-1 extents:1 across:3582452k 
Oct 26 18:13:51 asus kernel: [    5.644076] udev: starting version 147
Oct 26 18:13:51 asus kernel: [    6.297676] eeepc_laptop: Eee PC Hotkey Driver
Oct 26 18:13:51 asus kernel: [    6.298484] eeepc_laptop: Hotkey init flags 0x41
Oct 26 18:13:51 asus kernel: [    6.298783] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
Oct 26 18:13:51 asus kernel: [    6.301417] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
Oct 26 18:13:51 asus kernel: [    6.303525] eeepc_laptop: TPD (8000000) not reported by BIOS, enabling anyway
Oct 26 18:13:51 asus kernel: [    6.303534] eeepc_laptop: Get control methods supported: 0xe101713
Oct 26 18:13:51 asus kernel: [    6.303666] input: Asus EeePC extra buttons as /devices/virtual/input/input7
Oct 26 18:13:51 asus kernel: [    6.392958] Linux video capture interface: v2.00
Oct 26 18:13:51 asus kernel: [    6.608207] cfg80211: Calling CRDA to update world regulatory domain
Oct 26 18:13:51 asus kernel: [    6.719161] intel_rng: FWH not detected
Oct 26 18:13:51 asus kernel: [    6.725938] atl1c 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Oct 26 18:13:51 asus kernel: [    6.726046] atl1c 0000:01:00.0: PME# disabled
Oct 26 18:13:51 asus kernel: [    6.726057] atl1c 0000:01:00.0: PME# disabled
Oct 26 18:13:51 asus kernel: [    6.734341] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (13d3:5071)
Oct 26 18:13:51 asus kernel: [    6.753323] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8
Oct 26 18:13:51 asus kernel: [    6.753478] usbcore: registered new interface driver uvcvideo
Oct 26 18:13:51 asus kernel: [    6.753490] USB Video Class driver (v0.1.0)
Oct 26 18:13:51 asus kernel: [    6.766749] lp: driver loaded but no devices found
Oct 26 18:13:51 asus kernel: [    6.804383] eeepc_laptop: Backlight controlled by ACPI video driver
Oct 26 18:13:51 asus kernel: [    6.841843] atl1c 0000:01:00.0: version 1.0.0.1-NAPI
Oct 26 18:13:51 asus kernel: [    7.311789] EXT4-fs (sda5): internal journal on sda5:8
Oct 26 18:13:51 asus kernel: [    7.474572] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 26 18:13:51 asus kernel: [    7.635544] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000
Oct 26 18:13:51 asus kernel: [    7.718331] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Oct 26 18:13:51 asus kernel: [    7.765632] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 26 18:13:51 asus kernel: [    7.912947] cfg80211: World regulatory domain updated:
Oct 26 18:13:51 asus kernel: [    7.912955] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 26 18:13:51 asus kernel: [    7.912963] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 26 18:13:51 asus kernel: [    7.912969] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 26 18:13:51 asus kernel: [    7.912976] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 26 18:13:51 asus kernel: [    7.912982] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 26 18:13:51 asus kernel: [    7.912988] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 26 18:13:51 asus kernel: [    8.206994] Registered led device: ath9k-phy0::radio
Oct 26 18:13:51 asus kernel: [    8.207054] Registered led device: ath9k-phy0::assoc
Oct 26 18:13:51 asus kernel: [    8.207113] Registered led device: ath9k-phy0::tx
Oct 26 18:13:51 asus kernel: [    8.207174] Registered led device: ath9k-phy0::rx
Oct 26 18:13:51 asus kernel: [    8.207225] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf82c0000, irq=17
Oct 26 18:13:51 asus kernel: [    8.318286] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 26 18:13:51 asus kernel: [    8.697304] hda_codec: ALC269: BIOS auto-probing.
Oct 26 18:13:51 asus kernel: [    8.697918] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
Oct 26 18:13:51 asus kernel: [   10.967042] EXT4-fs (sda6): barriers enabled
Oct 26 18:13:51 asus kernel: [   10.968984] kjournald2 starting: pid 763, dev sda6:8, commit interval 5 seconds
Oct 26 18:13:51 asus kernel: [   10.969669] EXT4-fs (sda6): internal journal on sda6:8
Oct 26 18:13:51 asus kernel: [   10.969683] EXT4-fs (sda6): delayed allocation enabled
Oct 26 18:13:51 asus kernel: [   10.969693] EXT4-fs: file extents enabled
Oct 26 18:13:51 asus kernel: [   10.982032] EXT4-fs: mballoc enabled
Oct 26 18:13:51 asus kernel: [   10.982071] EXT4-fs (sda6): mounted filesystem with ordered data mode
Oct 26 18:13:51 asus kernel: [   12.005204] __ratelimit: 3 callbacks suppressed
Oct 26 18:13:51 asus kernel: [   12.005215] type=1505 audit(1256580831.364:11): operation="profile_replace" pid=843 name=/sbin/dhclient3
Oct 26 18:13:51 asus kernel: [   12.006033] type=1505 audit(1256580831.364:12): operation="profile_replace" pid=843 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Oct 26 18:13:51 asus kernel: [   12.006487] type=1505 audit(1256580831.364:13): operation="profile_replace" pid=843 name=/usr/lib/connman/scripts/dhclient-script
Oct 26 18:13:51 asus kernel: [   12.015281] type=1505 audit(1256580831.372:14): operation="profile_replace" pid=845 name=/usr/bin/evince
Oct 26 18:13:51 asus kernel: [   12.025026] type=1505 audit(1256580831.384:15): operation="profile_replace" pid=845 name=/usr/bin/evince-previewer
Oct 26 18:13:51 asus kernel: [   12.031572] type=1505 audit(1256580831.388:16): operation="profile_replace" pid=845 name=/usr/bin/evince-thumbnailer
Oct 26 18:13:51 asus kernel: [   12.046315] type=1505 audit(1256580831.404:17): operation="profile_replace" pid=848 name=/usr/lib/cups/backend/cups-pdf
Oct 26 18:13:51 asus kernel: [   12.047325] type=1505 audit(1256580831.404:18): operation="profile_replace" pid=848 name=/usr/sbin/cupsd
Oct 26 18:13:51 asus kernel: [   12.056977] type=1505 audit(1256580831.416:19): operation="profile_replace" pid=850 name=/usr/sbin/tcpdump
Oct 26 18:13:52 asus kernel: [   12.849105] ppdev: user-space parallel port driver
Oct 26 18:13:52 asus kernel: [   13.266554] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 26 18:13:52 asus kernel: [   13.283791] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 26 18:14:22 asus kernel: [   43.089120] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 26 18:14:22 asus kernel: [   43.101154] cfg80211: Calling CRDA for country: GB
Oct 26 18:14:22 asus kernel: [   43.105611] cfg80211: Regulatory domain: GB
Oct 26 18:14:22 asus kernel: [   43.105615] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 26 18:14:22 asus kernel: [   43.105622] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
Oct 26 18:14:22 asus kernel: [   43.105631] cfg80211: Regulatory domain: GB
Oct 26 18:14:22 asus kernel: [   43.105634] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 26 18:14:22 asus kernel: [   43.105640] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 26 18:14:22 asus kernel: [   43.105646] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 26 18:14:22 asus kernel: [   43.105652] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 26 18:14:22 asus kernel: [   43.105657] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Oct 26 18:14:22 asus kernel: [   43.105666] cfg80211: Regulatory domain: 98
Oct 26 18:14:22 asus kernel: [   43.105669] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 26 18:14:22 asus kernel: [   43.105675] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 26 18:14:22 asus kernel: [   43.105696] cfg80211: Current regulatory domain updated by AP to: GB
Oct 26 18:14:22 asus kernel: [   43.105701] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 26 18:14:22 asus kernel: [   43.105707] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 26 19:09:19 asus pulseaudio[1382]: ratelimit.c: 104 events suppressed
Oct 26 19:41:58 asus kernel: [ 5299.321034] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 26 23:06:04 asus kernel: [17545.624195] CE: hpet increasing min_delta_ns to 22500 nsec
Oct 26 23:06:04 asus kernel: [17545.624325] CE: hpet increasing min_delta_ns to 33750 nsec

```
Syslog looks virtually identical.  I can't make any sense of it, but it's working OK now.  I had Transmission torrent client runnung since last night, and one of the two torrents finished after the mess-up, and the file seems fine.  The other is still down/uploading....

Anyway, all that ends well,...

Peace
ed

---

### Post by jamieleshaw on 2009-10-26
I ordered mine over a week ago, still haven't got gees jb-hifi are taking ages.

---

### Post by T3CHKOMMIE on 2009-10-27
> **trapperjohn said:**
> @T3CHKOMMIE: Sending files from Ubuntu to my phone worked out-of-the-box, the other way needs some additional effort:
  
@Trapperjohn, what kind of phone do you have?

i have an LG from sprint and i can pair but thats it. i downloaded that user-share through synaptic... no go. i cant send or recive, i had a problem with my mac... someproblem with onx

browse works well, and i can send from pc to handy, but cant from handy to pc. any ideas on how to get from my phone to my pc? thanks for your wisdome i REAALLY appriciate learning more about this stuff :)

---

### Post by trapperjohn on 2009-10-27
I have a Samsung Jet S8000 - after installation of gnome-user-share and enabling bluetooth file receiption by its settings dialog, the whole bluetooth thing works like a charm (for me ...).

---

### Post by tipiglen on 2009-10-30
Official 9.10 installed and working well.  A new, clean install instead of an upgrade.  Still required backports to get microphone working.  Most everything else completely cool because I keep (and recommend) a separate /home partition. also if one has any customised files in the root filesystem, they should be copied into a folder in the /home directory before (re)installation, e.g. .profile, .bashrc, /etc/environment (PATH), etc.

Also, if you need java, you'll have to install it, and my Thunderbird went missing, too - but not its configuration profiles, etc.

Ciao
ed

---

### Post by YanB on 2009-10-30
you said that you used the backports to get the microphone to work... how did you do that?
I installed the standard Karmic on the 1005-ha, and it doesn't recognize the webcam. However, if I boot with a USB with the netbook remix, it does. Any hints as to how to proceed to fix this?
thanks

---

### Post by tipiglen on 2009-10-30
I went to synaptic package manager
(in karmic: programs>system>synaptic)
entered "backports" and then selected all the ones in the list which mentioned alsa.  Marked them for installation, clicked apply,

and now it works.  I also find the GNOME ALSA mixer (available from the ubuntu software center or probably synaptics) very useful.  You need to have the "record" box checked for the mic to work.

Hope that's helpful, but please ask for more help if it isn't enough

Ciao
ed

---

### Post by tipiglen on 2009-10-30
Yan, > I installed the standard Karmic on the 1005-ha, and it doesn't recognize the webcam. 
Forgot to say,

The webcam application is at Programs>sound&Video>Cheese

---

### Post by Silver Doctor on 2009-10-30
Hi, I'm new to Ubuntu but installed (clean) 9.10 on an Asus 1005HA today. So far no problems with webcam, wireless, sound. Only issue so far is function keys, 

Iain

---

### Post by infernox on 2009-10-31
I have the 1005HA on 9.04 and worked real hard on hacking and configuring it to finally work well and have been holding off on installing 9.10. Mic / webcam has to work for me since I use Skype to communicate with my kids when I travel. Same for Function keys. I'm looking forward to everyone's post on this. Thanks for the help. I'm going to wait a little longer to make sure function keys work.

---

### Post by sharkcohen on 2009-10-31
9.10 will not install on my 1005HA.  The installation hangs at 80% 'configuring apt'.

Edit: /var/log/messages shows apt is still downloading from repositories.  Guess it's taking its own sweet time.

---

### Post by YanB on 2009-10-31
> **infernox said:**
> I have the 1005HA on 9.04 and worked real hard on hacking and configuring it (...) Mic / webcam has to work for me since I use Skype
what did you do to make skype work? the webcam in 9.04 worked out of the box, but the mic didn't.

> **tipiglen said:**
> 
The webcam application is at Programs>sound&Video>Cheese
Yes, I tried that. With UNR, the webcam is recognized, but with standard Karmic, it isn't.
I prefer to use the standard Karmic, and not the UNR, but maybe I shouldn't... I didn't know the distro was so different. Is it?

Also, I installed ALSA, as suggested, but I still don't seem to get the mic to be recognized/work. Any suggestions?  Thanks again!

---

### Post by DarthScape on 2009-10-31
I still have wireless drop after 10 min. Even in 9.10 final.

---

### Post by sharkcohen on 2009-10-31
Ok 9.10 on the 1005HA just kicks ***.  I'm throwing h.264 encoded video files at it and the playback is flawless.  The netbook as a whole is peforming very well.  I came from the Moblin 2.0 beta.  Moblin has its heart in the right place, but it's just not mature and the peformance was below my expectations.  My netbook is now useable.

---

### Post by Silver Doctor on 2009-10-31
Quick update, had the mic problem with NBR, seems partly resolved with the ALSA backports - at least Skype worked until it dropped the connection then I could reconnect with video OK, but no mic. Had to restart and all is well again. So, a bit confused but still largely happy with NBR on a 1005HA.

Iain

---

### Post by tipiglen on 2009-10-31
Darth,> I still have wireless drop after 10 min. Even in 9.10 final.I'm getting drops for no apparent reason.  Then it asks for encryption key, which is taken care of automatically at boot, and should be in case of a dropped connection.

Puzzling.Looking at syslog, there seems to be rather a lot of wlan checking and associating, etc.

---

### Post by DarthScape on 2009-11-01
I remember when i had karmic beta and had the backports, it wouldn't just drop connections, i would get a kernel panic instead.

---

### Post by trapperjohn on 2009-11-01
Weird - I had no problem with the wireless driver from out-of-the-box-Karmic, just a little low signal level. The updated backports driver solved this for me.

---

### Post by tipiglen on 2009-11-01
The connection-dropping behaviour seems to be pretty random and intermittent here.  For example up, connected and running for quite a while now```
root@asus:/home/ed/bin# uptime
 12:12:14 up 10:47,  2 users,  load average: 0.14, 0.21, 0.18

```Looking into the log viewer:
```
Warning: Could not open the following files:
/var/log/apport.log: Error stating file '/var/log/apport.log': No such file or directory
/var/log/apport.log.1: Error stating file '/var/log/apport.log.1': No such file or directory
/var/log/btmp: You don't have enough permissions to read the file.

```
And, from Syslog:```
Nov  1 12:17:01 asus kernel: [39133.320074] wlan0: authenticated
Nov  1 12:17:01 asus kernel: [39133.320085] wlan0: associate with AP 00:24:56:e7:5b:11
Nov  1 12:17:01 asus wpa_supplicant[1028]: Associated with 00:24:56:e7:5b:11
Nov  1 12:17:01 asus wpa_supplicant[1028]: CTRL-EVENT-CONNECTED - Connection to 00:24:56:e7:5b:11 completed (reauth) [id=0 id_str=]
Nov  1 12:17:01 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov  1 12:17:01 asus kernel: [39133.332217] wlan0: RX ReassocResp from 00:24:56:e7:5b:11 (capab=0x431 status=0 aid=1)
Nov  1 12:17:01 asus kernel: [39133.332226] wlan0: associated
Nov  1 12:17:01 asus NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Nov  1 12:17:01 asus CRON[6122]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 12:17:06 asus NetworkManager: <debug> [1257077826.003636] periodic_update(): Roamed from BSSID (none) ((none)) to 00:24:56:E7:5B:11 (BTBusinessHub-447)
Nov  1 12:17:47 asus wpa_supplicant[1028]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:19:47 asus wpa_supplicant[1028]: CTRL-EVENT-SCAN-RESULTS 
Nov  1 12:21:47 asus wpa_supplicant[1028]: CTRL-EVENT-SCAN-RESULTS 


```
etc., etc.,  Seems to be constantly at work keeping connection live, and spamming the syslog all the while.  

?;-(?

---

### Post by jamieleshaw on 2009-11-01
I've finally got Ubuntu Netbook Remix 9.10 on my epc, overall very happy.
Just a few downfalls, Wifi connection is all over the place low signal, max signal etc.
and battery life seems a little weak.
but i'm very happy with netbook remix(though the netbook interface is a little buggy)
so YAY! i've got ubuntu on my eeeeee!

---

### Post by fugyfudy on 2009-11-04
I'm also getting a kernel panic on the 1005ha with 9.10.

Here's the kernel log from when it happened.

```
Nov  4 16:17:14 eee kernel: [   47.071105] wlan0: deauthenticating from 00:22:75:25:51:d3 by local choice (reason=3)
Nov  4 16:17:14 eee kernel: [   47.076762] wlan0: direct probe to AP 00:22:75:25:51:d3 (try 1)
Nov  4 16:17:14 eee kernel: [   47.120563] wlan0: direct probe responded
Nov  4 16:17:14 eee kernel: [   47.120576] wlan0: authenticate with AP 00:22:75:25:51:d3 (try 1)
Nov  4 16:17:14 eee kernel: [   47.122493] wlan0: authenticated
Nov  4 16:17:14 eee kernel: [   47.122540] wlan0: associate with AP 00:22:75:25:51:d3 (try 1)
Nov  4 16:17:14 eee kernel: [   47.126430] wlan0: RX AssocResp from 00:22:75:25:51:d3 (capab=0x411 status=0 aid=1)
Nov  4 16:17:14 eee kernel: [   47.126439] wlan0: associated
Nov  4 16:17:14 eee kernel: [   47.136103] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov  4 16:17:14 eee kernel: [   47.136207] cfg80211: Calling CRDA for country: US
Nov  4 16:17:14 eee kernel: [   47.145293] cfg80211: Received country IE:
Nov  4 16:17:14 eee kernel: [   47.145303] cfg80211: Regulatory domain: US
Nov  4 16:17:14 eee kernel: [   47.145309] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  4 16:17:14 eee kernel: [   47.145319] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
Nov  4 16:17:14 eee kernel: [   47.145325] cfg80211: CRDA thinks this should applied:
Nov  4 16:17:14 eee kernel: [   47.145331] cfg80211: Regulatory domain: US
Nov  4 16:17:14 eee kernel: [   47.145336] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  4 16:17:14 eee kernel: [   47.145346] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov  4 16:17:14 eee kernel: [   47.145355] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Nov  4 16:17:14 eee kernel: [   47.145363] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  4 16:17:14 eee kernel: [   47.145372] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  4 16:17:14 eee kernel: [   47.145381] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Nov  4 16:17:14 eee kernel: [   47.145388] cfg80211: We intersect both of these and get:
Nov  4 16:17:14 eee kernel: [   47.145393] cfg80211: Regulatory domain: 98
Nov  4 16:17:14 eee kernel: [   47.145398] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  4 16:17:14 eee kernel: [   47.145408] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov  4 16:17:14 eee kernel: [   47.145422] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
Nov  4 16:17:14 eee kernel: [   47.145429] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
Nov  4 16:17:14 eee kernel: [   47.145437] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
Nov  4 16:17:14 eee kernel: [   47.145451] cfg80211: Current regulatory domain updated by AP to: US
Nov  4 16:17:14 eee kernel: [   47.145457] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov  4 16:17:14 eee kernel: [   47.145466] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Nov  4 16:17:14 eee kernel: [   47.266428] padlock: VIA PadLock not detected.
Nov  4 16:17:25 eee kernel: [   58.076060] wlan0: no IPv6 routers present
Nov  4 16:18:44 eee kernel: [  142.906021] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
Nov  4 16:19:15 eee kernel: [  174.444204] ACPI: EC: missing confirmations, switch off interrupt mode.
Nov  4 16:19:16 eee kernel: [  174.964177] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
Nov  4 16:19:16 eee kernel: [  174.964226] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.BST2] (Node f70130a8), AE_TIME
Nov  4 16:19:16 eee kernel: [  174.964344] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.CBST] (Node f7017090), AE_TIME
Nov  4 16:19:16 eee kernel: [  174.964439] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.BAT0._BST] (Node f7016fc0), AE_TIME
Nov  4 16:19:16 eee kernel: [  174.964548] ACPI Exception: AE_TIME, Evaluating _BST 20090521 battery-385
Nov  4 16:19:45 eee kernel: [  203.940881] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
```

Happens about once a day, although I had an uptime of 3 days before it happened today.

Edit: I've noticed that this problem only happens sometime after I've closed the lid, but other than that, it's still happening.

---

### Post by T3CHKOMMIE on 2009-11-10
> **DarthScape said:**
> I still have wireless drop after 10 min. Even in 9.10 final.

it feels like lately i have been the king of droped wifi connections. It seemed to me that my wifi experiences problems when im charging my machine and using it a bit. it leads to overheating. my machine gets to about 160 F and then locks up... about 5 min before it locks up, the wifi goes out.

if my machine isnt running hot it dosnt drop the connection. i know what you mean mine asks for the WPA password again. 

as for me, im pretty sure my problem started when i opened synaptic and started installing some things i probably shouldnt have been messing with.

unfortunately it is my sad experience that the only real solution is a fresh reinstall. im a pro at reimaging my machine... just did as a matter of fact.

now WIFI is doing well... except when im running hot. 

is your machine running hot? do you have the large copassity batt? its a real nuisance so i would recommend backing everything up, and doing a "do over"

hope this helps!

---

### Post by project4 on 2009-11-11
> **tipiglen said:**
> Darth,I'm getting drops for no apparent reason.  Then it asks for encryption key, which is taken care of automatically at boot, and should be in case of a dropped connection.

Puzzling.Looking at syslog, there seems to be rather a lot of wlan checking and associating, etc.


I am using WICD to manage my wireless networks. Works much better than the standard network-manager

It can be downloaded from the synaptic repository. Need to uninstall network-manager first, though...

try to first save the WICD deb file on the desktop before removing the network-manager.

---

### Post by movieman on 2009-11-12
I just installed 9.10 UNR on an Asus eee PC 1005HAB, and so far it just works other than playing movies and audio files. I have heard some sound come out, so something is able to play files!

---

### Post by trapperjohn on 2009-11-12
> **movieman said:**
> I just installed 9.10 UNR on an Asus eee PC 1005HAB, and so far it just works other than playing movies and audio files. I have heard some sound come out, so something is able to play files!


Make sure to install the restricted formats:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Maybe also add Medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by movieman on 2009-11-12
Thanks, I was trying to remember what I needed to install for the other codecs. I rebooted afterwards to ensure that everything was using up to date files and now I can play movies but only some programs can play audio files :).

---

### Post by dangerstat on 2009-12-05
I'm just installing it now on my new 1005HA. It will be interesting to see which of the problems listed in the thread I encounter (few I hope). A little annoying to see Asus shipping this with XP home and not U NBR in my opinion. Ah well 98% so will hopefully be posting back in here when I reboot :P

EDIT 1: Oooohhhhh 9.10 is flashy isn't it! So wired AND wireless is working out of the box. Absolutely top notch to you guys. 

I really like the interface, very sexh. Shame I'll be using openbox !

---

### Post by imaqt55 on 2009-12-14
I did not read through all of the replies, so I apologize if some of my comments are a bit redundant, but I have had an EEE 1005-HA for a few months now and will list the ongoing (seemingly unfixable) problems I have had with the Netbook Remix in case they may help anyone with this decision.

-If you set it to suspend on idle, it will suspend on idle when the screen is open, but it will never suspend when the screen is closed (unless you set it to suspend as soon as you close the screen - not what I want).  This seems so silly to me and I searched and searched and searched for a solution to no avail.
-It randomly suspends while I am in the middle of typing - clearly not idle
-The battery life is about half what it is if I run Windows on the same computer
-Microphone doesn't work
-Periodically random pieces of text from emails or word documents (or sometimes the text and graphics from an entire web page I previously viewed) will get pasted while I am typing even though I never copied or pasted anything. This happens frequently enough to be quite a hassle, and it is very bizarre
-Remote desktop freezes many times a day and restarting remote desktop is the only solution
-Scrolling can sometimes feel very slow - there is a noticeable lag compared to windows

I hope this is helpful - let me know if you have questions.

---

### Post by trapperjohn on 2009-12-14
> **imaqt55 said:**
> 

-It randomly suspends while I am in the middle of typing - clearly not idle
-Microphone doesn't work
-Periodically random pieces of text from emails or word documents (or sometimes the text and graphics from an entire web page I previously viewed) will get pasted while I am typing even though I never copied or pasted anything. This happens frequently enough to be quite a hassle, and it is very bizarre
-Scrolling can sometimes feel very slow - there is a noticeable lag compared to windows


I think these issues are specific to your configuration - none of them apply to my 1005HA-H. 

I only had the mic problem first but instantly got rid of it after installing the backports module.

About the copy+paste problem: Maybe your touchpad recognizes some kind of third-button-emulation (multitouch-click or something like that) and that's why you paste text you've marked before?

---

### Post by imaqt55 on 2009-12-14
trapperjohn,

You may be right that these problems are unique to my computer, as I have searched for solutions for all of them and cannot find anyone else with the same complaints.  However I am not sure what it is about my configuration that would be causing these problems - I bought it at Best Buy, installed 9.04 NBR and that's it.  I am new to Linux, so a friend tried to fix the microphone for me with no success. I'm not sure what the backports module is.

Re: the copy and paste issue, I was thinking that might be what's happening - somehow something other than mouse clicking or ctrl+c and ctrl+v are serving as copy and paste - the weird thing is, it happens only while I am typing (and not touching the mouse).

---

### Post by trapperjohn on 2009-12-14
> **imaqt55 said:**
> 
 installed 9.04 NBR and that's it. 

What about 9.10? \\:D/

---

### Post by imaqt55 on 2009-12-14
> **trapperjohn said:**
> What about 9.10? 

I just installed 9.10 yesterday and it seems it solved some problems and created others.  The issue with the computer not going on idle while the screen is closed appears to be fixed (though I am still having another problem I forgot to list in my original post - sometimes the power management features stop working and it won't go idle even though it is inactive, and the only solution is to restart).

But, now periodically, I get disconnected from my wireless network and then it acts as if there are no wireless networks available (even though there is and it is working fine).  The only solution is to restart. Any suggestions?

As for most of the other problems, as they happen unpredictably, I am not sure yet of their status.  Mic still doesn't work.

---

### Post by trapperjohn on 2009-12-15
Try to install the backports packages:

linux-backports-modules-alsa-karmic-generic
linux-backports-modules-wireless-karmic-generic

Maybe also the pulse audio volume control:
pavucontrol

I sometimes have to disable/enable the mic in pavucontrol to make it work.

---

### Post by AlbinoGoudvis on 2009-12-17
I've installed UNR 9.10 on my new 1005HA-M.
As google & this forum told me, problems with wireless connection are not uncommon.  But my problem seem to be about something different.

I can connect, I can ping various sites but in two days I've been able to reach google (in firefox after +10 minutes) only twice.  It's as if my speed is one byte/a second.

On Windows 7 (dual boot) wlan works perfect. On my toshiba-laptop with jaunty wlan works perfect too.

The problem only seems to happen with UNR 9.10: installed on the Asus EEE, with live USB on both the Asus EEE and my other laptop.

I've downloaded a new version of UNR 9.10, but that doesn't help.  I assume there's something about the connection which UNR doesn't like?

---

### Post by AlbinoGoudvis on 2009-12-18
> **AlbinoGoudvis said:**
> I've installed UNR 9.10 on my new 1005HA-M.
As google & this forum told me, problems with wireless connection are not uncommon.  But my problem seem to be about something different.

I can connect, I can ping various sites but in two days I've been able to reach google (in firefox after +10 minutes) only twice.  It's as if my speed is one byte/a second.

On Windows 7 (dual boot) wlan works perfect. On my toshiba-laptop with jaunty wlan works perfect too.

The problem only seems to happen with UNR 9.10: installed on the Asus EEE, with live USB on both the Asus EEE and my other laptop.

I've downloaded an other version of UNR 9.10, but that doesn't help.  I assume there's something about the connection which UNR doesn't like?

I've tried the original 9.10 (live cd).  It couldn't connect on three different laptops.  On 9.04, windows 7, it does work.  

Should I change some wireless settings? :confused:

---

### Post by imaqt55 on 2009-12-22
> **trapperjohn said:**
> Try to install the backports packages:

linux-backports-modules-alsa-karmic-generic
linux-backports-modules-wireless-karmic-generic

Maybe also the pulse audio volume control:
pavucontrol

I sometimes have to disable/enable the mic in pavucontrol to make it work.

Ok, I did this and it solved my wireless problem completely. It doesn't drop the connection anymore, and the signal is much better.

But, the other solution did not fix my microphone. Worse, after installing pavucontrol, my music player will not work anymore. How do I uninstall?

---

### Post by trapperjohn on 2009-12-22
Well, pavucontrol is only a volume control frontend for pulseaudio, it should not have side-effects on a running system.

When you start music (even if you do not hear anything), do you see its output in pavucontrol? Maybe you just have to unmute the stream or select another output sink?

Or are there any errors (like messageboxes etc.) when you start playback?

Of course you can also uninstall pavucontrol (using 'apt-get remove pavucontrol' or the apt GUI) - but I don't think it will solve your problem.

---

### Post by Squideshi on 2010-05-02
> **tipiglen said:**
> 
/var/log/btmp: You don't have enough permissions to read the file.


[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

### Post by sgbeamer on 2010-10-30
Most of your questions are answered here[ https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")

---

