---
title: "Laptop install impresed"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by wizardks on 2006-12-23
I have a compaq presario 715us laptop
1.2g amd w/power now
384m ram
cd-r/rw dvd-rom combo

After years of running MS on it I installed Ubuntu.
using the Livecd I had to;
boot in safe graphics mode
F6 remove splash and change quiet to verbose
Why oh Why isn't there an option on liveCD to bypass booting into the OS and go straight to install!  

Some of the things that always ticked me off
Bought a laptop which at the time was cutting edge.
Cd would only complete a successful write, maybe 30% of the time
Modem rarely worked 
MS updates usually broke the thing
DVD movies play back - marginal (low ram problem?)

I took the plunge as stated above, now (been little less than a week) it has completed evey cd I tried to write.  Plays DVD's pretty darn good.  After some major hassles I got networking working.

It booted up and almost everything worked.  Saw my linksys wireless card, the AP I have running, got on the net etc.  It also picked up my smb/winblows shares, and was able to browse them.  (something I could never get my Fedora 5 box to do).  Haven't attempted to use the modem yet.  4-way scroll buttons under the touchpad partially workin. ( need to figure out how to fix it) In fact, the touchpad is now very responsive, all most too responsive.  Can't tap n drag, have to use the left cilcknhold to drag items.(can get used to that)

Now about the networking, initially I booted with the linksys B card it worked.  I setup a profile for it. (came up as eth0 not wlan0)  Then I switched to wired lan it worked, came up as eth0.  Well ok that's what it usually is in linux so I setup a profile.  Went back to the WiFi, it came up as eth1 (still no wlan0) and worked just fine, added a profile (deleted the old one of course).  Went back to wired to see if all was well, hmmmm not working at all.  Checked some forums, installed a Network manager still no go with wired lan.
Ended up modifying the alias file, and one other file (can't recall which one) now I'm good to go.

Now after, what, 4-5 years I have a fully functional laptop, almost but lots better than Under Winblows. :D 

 I have another machine that was running FC5, I decided I was tired of not being able to see/connect to smb/win shares.  Actually, the only way I can was to manually type the machine URI.   And the upgrades have always been a pain in the neck.  Anyway, when I tried to install Ubuntu on here, it would not even boot into Live CD.  I even tried the tricks noted above - no go. Again, Why isn't there an option on the Livecd to go straight to install?  I need to have a box that I can run Apache, php, and mysql at least.  

I installed FreeSP on here, no problems at all there.  Well, one problem  Fox now has a habit of locking when there are multiple tabs open.  Only way to fix is to shut fox down, sometimes it won't exit all the way, have to reboot to fix.  Kind of aggravating since I need the net to get apache php etc.  I used cnr and installed Fox 2.0, it won't update to 2.0.0.1!  So I fixed fox so the check for updates in the browser works, still won't update to 2.0.0.1.  Not sure if I like the CNR thing, I got comfortable with yumex.  BTW anyone know of a good prog. that'll let me monitor system logs in real time.  Am thinking that maybe the fox lockup maybe a FreeSP bug.

I live in the sticks and I'm forced to use a type of wireless net connection at around 384k 1500k burst.  So I guess I'll have spend another 6 hours downloading the alternate install iso.  Oh well.

Hope this post helps anyone with a similar laptop.  Every OS has it's ups and downs.  When I pay good money for a thing I expect it to work.  I don't expect to pay to beta test someone's OS, nor do I expect to buy a system or new version, then spend hours if not days getting updates/security fixes. That seems to be the MS philosophy!  And I am not really complaining about the challenges associated with linux installations.  Gives me something to do, just looking for 1 that will do what I need with minimal hassle.   I see lots of posts from folks wanting to run MS apps/games on Linux boxes.  If I need to use MS I use my MS machine, yep I have one and only one!  As for games well there is always th PS2.  I have noticed a trend in the gaming industry towards online games.  Looks like eventually games will be a non issue.  However, I can see this coming, "Where as you can go to Wally World and buy a PC game, and play it forever on the PC , now we have games going online and they'll charge you yearly to play."    

Just my 2 cents worth   I am thankful that we have the option to chose Linux.  Robust, secure, free, not spyware infested, and challenging LINUX.  Yes I said spyware infested, I sometimes monitor the actual data going to and from my machines.  Why would my MS machine be constantly sending data to MS?  It's not auto update etc. those are all firewalled/off etc.  I had a prog.(disappeared when my machine installed sp2 -auto update was off!) that managed to decode some of the packets going to MS, was data about installed programs even some relating to supposedly private documents.  You know stuff documents I had created with word etc.  I'll have to dig up the prog. in case anyone is interested do remember it was a real real pain to get it to install! (been awhile can't even remember the prog. name).

Enough ranting/raving for now.  Thanks for your time don't blast me to much for this post  :) 

Best wishes to all this holiday season

 btw i noticed that a script "Google analytics" is tryin to run on this site what's up with that?

---

