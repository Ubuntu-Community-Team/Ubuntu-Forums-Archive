---
title: "Tracker Applet error after upgrade to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by leeds on 2009-04-24
Just upgraded to 9.04, installation was smooth. Was indexing files in 8.10, however after upgrade getting the error "Traker - There was an error while performing indexing: Index corrupted" I have the option to reindex which I have already tried twice, same error comes back. I have disabled indexing. Please help (NB: I am new to Ubuntu).

---

### Post by mikex on 2009-04-24
> **leeds said:**
> Just upgraded to 9.04, installation was smooth. Was indexing files in 8.10, however after upgrade getting the error "Traker - There was an error while performing indexing: Index corrupted" I have the option to reindex which I have already tried twice, same error comes back. I have disabled indexing. Please help (NB: I am new to Ubuntu).

Same exact thing here - I can't get it to work even when requesting a new index. Same message every bootup.

---

### Post by ivia77 on 2009-04-24
Same for me. I've tried Alt+F2 and run tracker-processes -r as suggested in the [_release notes_]("http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption") but it gave me this error mesage 

Error stating file '/home/matt/tracker-processes -r': No such file or directory

---

### Post by Jack Shankle on 2009-04-24
I also have the same bug. 
Everything else is working fine on a triple boot system.
I upgraded from 8.10 to 9.04 and I was using ext3 (I think)
on 8.10 and guess I am still using ext3 in 9.04. The upgrade
didn't ask anything about ext4.

---

### Post by mikex on 2009-04-24
Found a solution that fixed it for me, here it is -


> [I]Found a workaround/fix that's more user friendly:

sudo apt-get install tracker-utils
tracker-processes -r # --hard-reset

Then I logged out and back in so the processes that I had previously killed by hand would restart in a normal fashion.

Note that this probably gets rid of data that would be useful in finding a fix for others, which is sad.[/I]


[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

---

### Post by pistos on 2009-04-24
I have the same error coming up after upgrading from 8.10 to 9.04 too. I have disabled Tracker for now.

---

### Post by nobodie on 2009-04-24
I have exactly the same error with two different machines, the first was upped to jaunty RC1 the the other just finished upping to the final product. I tried the suggestion mentioned above and it has seemed to work on both my machines, so I recommend: 

in the terminal of your choice

$sudo apt-get install tracker-utils
$tracker-processes -r

since it seems to have worked for me

---

### Post by skyydiver on 2009-04-24
Thanks.  I have now killed tracker too.

---

### Post by Gyo on 2009-04-25
> **nobodie said:**
> 
$sudo apt-get install tracker-utils
$tracker-processes -r


this worked great for me :KS

---

### Post by leeds on 2009-04-25
Thanks - codes worked for me as well.

---

### Post by eltiojuanillo on 2009-04-25
same problem after upgrading to 9.04. Solved after 

sudo apt-get install tracker-utils
tracker-processes -r

I recommend doing the same

---

### Post by Nhorning on 2009-04-25
The above solved it for me as well

---

### Post by suresnjain on 2009-04-25
I was getting the same error.After getting advise from the forum,I have done 2 steps (1)    sudo apt-get install tracker-utils       and (2)   tracker-processes -r   Now  trcker icon is gone from the right side of the top panel.So, the third step advised  # --hard-reset  how to do this # in the terminal.

---

### Post by scientist47 on 2009-04-25
Also updated from intrepid to jaunty, and got the same error message. The suggested solution worked for me as well.
suresnjain: The text after a '#' is ignored by bash. It is only a comment to explain the 'r' flag in the command. 
Below is the suggested solution plus the commands to start the tracker gain:
bash code:
```
sudo apt-get install tracker-utils
tracker-processes -r # --hard-reset
/usr/lib/tracker/trackerd &
tracker-applet &
disown -a
```
the disown command detaches the tracker processes from the bash terminal, so that they will live on if the terminal is closed.

---

### Post by PGAMan on 2009-04-26
This solution worked for me.  Thank you.

---

### Post by bbradley on 2009-04-26
I just disabled it in system/preferences/startup applications
and rebooted the machine

Hopefully the bug will be fixed soon

---

### Post by dpdamato on 2009-04-26
Thanks much!  Solution worked for me also.

---

### Post by carrierpilot1357 on 2009-04-26
I was having the exact same problem. codes worked for me also.

(by the way, i'm running 9.04. my profile just says 8.04.)

---

### Post by caiocgo on 2009-04-28
I am facing the same problem here. The only thing is that the tracker issue only start when I plug in an USB drive of some sort.

Is the solution the same?

---

### Post by deepnum09 on 2009-04-28
I had the same problem with tracker and just removed it in System->Preferences->Startup Applications so it wouldn't start each time I reboot. Tracker was using a huge chunk of my cpu (made my cpu usage go to 98%) so I killed both process associated with it (tracker and tracker applet ... or something like that).

---

### Post by Cold-Gin on 2009-04-28
Thank you very much. Had the same problem, and the commands seem to work for me also... Really appreciate it.

---

### Post by HolyJoe on 2009-04-28
This solution works for me too. 
Thanks.

> **mikex said:**
> Found a solution that fixed it for me, here it is -





[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

---

### Post by jejones3141 on 2009-04-29
I will disable tracker myself--upgraded my wife's laptop to 9.04, and woke up to find not only the described error, but also a process running "tracker-indexer" eating 75% of available RAM and bringing the laptop to its knees with thrashing.

---

### Post by Timpotten on 2009-04-29
It worked for a while and then......[IMG]http://www.t-im.es/Screenshot-Tracker Applet.png[/IMG]

Whichever option, it loops endlessly. 

**>system>Admin>System monitor**

"Kill" both "Tracker" process for the session.

The remove (-r) does remove the process, but then it somehow gets reinstalled - It is also possible (and maybe more convenient?) to use 

**>system>Admin>Synaptic**

Search for tracker and mark it for complete removal.

Tracker is an advanced framework for first class objects with associated metadata and tags. 
It provides a one stop solution for all metadata, tags, shared object databases, search tools and indexing.

So maybe killing and deleting it is not such a hot idea?

---

### Post by pistos on 2009-04-29
All I did to "remove" Tracker was un-check Tracker and Tracker Applet in System>Preferences>Startup Applications. Is there something else I should have done?

I figured I would leave it installed, so that when the bug is fixed, it will get fixed and I can then reactivate it.

---

### Post by pbhill on 2009-04-30
It also worked here. It also stopped the 99% CPU usage that tracker was causing, slowing down the whole system. Thanks.

---

### Post by Paperloader on 2009-05-02
[QUOTE=eltiojuanillo;7141448]same problem after upgrading to 9.04. Solved after 

sudo apt-get install tracker-utils
tracker-processes -r

This worked for me too. Thanks

---

### Post by Stereo_Junkie on 2009-05-02
sudo apt-get install tracker-utils
tracker-processes -r


Thanks for posting this fix.

---

### Post by su-37 on 2009-05-03
> **mikex said:**
> Found a solution that fixed it for me, here it is -





[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361560)

Yeah i tried this and did what you said it helped with me.

---

### Post by CarolusGomes on 2009-05-03
The sugestion « $sudo apt-get install tracker-utils
$tracker-processes -r » worked fine for me too. After rebooting, all was fine!

---

### Post by etienne@Rofti on 2009-05-03
```
sudo apt-get install tracker-utils
tracker-processes -r
```
What do the above commands do? I'm a bit scared of just running them without knowing what they actually do...
And, what exactly is the use of Tracker? I cannot remember ever specifically using it...

Thanks!
Etienne

---

### Post by Artemis3 on 2009-05-13
I just uninstalled all the tracker packages except for libtrackerclient0 which is sadly tied to totem. This bug is really bad... And i don't need tracker anyway, the file search tool in places works just fine.

---

### Post by sabutuga on 2009-05-13
> **nobodie said:**
> I have exactly the same error with two different machines, the first was upped to jaunty RC1 the the other just finished upping to the final product. I tried the suggestion mentioned above and it has seemed to work on both my machines, so I recommend: 

in the terminal of your choice

$sudo apt-get install tracker-utils
$tracker-processes -r

since it seems to have worked for me
I had the same problem and this worked great for me.

cheers

---

### Post by JimBuntu on 2009-05-13
Of course, same tracker applet error here. Was wondering if anyone's case alarm has been going off too? My internal case alarm goes off almost every day and I just restart the computer which pisses me off but I don't know any other way to fix that. I kind of think that it is related to this tracker error. This is the first time I've seen a tracker error while using Ubuntu and also first time for this alarm...very annoying.

---

### Post by ojmc on 2009-05-14
here's the official fix   [http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption](http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption)

---

### Post by tomdkat on 2009-05-14
I was encountering this as well and the tracker-processes -r  solution worked well for me too!  :)

Peace...

---

### Post by eivind on 2009-05-15
Tracker schmacker. I uninstalled it. :-)

---

### Post by thimmet on 2009-05-28
Works for me, thanks! :)

---

### Post by Inbredplayer on 2009-06-01
had the same problem but the fix seems to have worked for me thanks

---

### Post by torchfire on 2009-06-01
I had the same problem, and it was causing all my cpu's to be maxed out.  (According to the system monitor.) 

I disabled tracker.

I've run the code above, re-enabled tracker, and at the moment, everything seems fine. 

Tracker indicates that all indexing has been paused by the system at this point.  I'm wondering whether it will eat up all my cpu resources when the system un-pauses the indexing process?   I'll let you know if I find out. 

Thanks so much for providing the code. 

Now, to find solutions for my other two problems related to the upgrade... 

I learn so much after an upgrade.  :)

---

### Post by jgcamp99 on 2009-06-02
I completely uninstalled tracker, booted & rebooted a couple of times, then completely reinstalled it. This takes maybe all of 10 minutes, but whatever statistics were collected before aren't corrupt, it's using them right now and tracker is idling along without a hitch. CPU usage is normal too. 

I think if tracker gets corrupted again, I'll do the complete removal w/ complete installation again. The problem isn't with the metadata or the indexes, the problem is tracker itself. My biggest concern was having to sit thru another reindex process, that never occurred as tracker was properly installed this time thru synaptic, not the upgrade process that didn't install the tracker utilities and whatever else. I didn't even have to run the command:

"tracker-processes -r"

I hope my post allays any concerns about the method that I used to fix tracker on Ubuntu 9.04 ?

---

### Post by torchfire on 2009-06-02
My CPU resources are fine, and Tracker is now running great.  :D

---

### Post by ophie99 on 2009-06-09
[http://www.thisworked.com/](http://www.thisworked.com/)



Quick problem I encountered when I upgraded my [Ubuntu]("http://www.ubuntu.com/") distro to 9.04 from 8.10.  Periodically a dialog would pop up from the Tracker app saying something like this:

Tracker Applet
There was an error while performing indexing:
Index corrupted

 Three buttons to either "Reindex all", "Cancel" or "Accept" (if I recall correctly.)  Clicking these in just about any combination doesn't seem to do anything as the dialog keeps coming up.  Here's what to do:

**Problem**
Ubuntu Linux 9.04 Tracker Applet stuck in an error loop where it's claiming "index corrupted."  There is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/361205") that will be fixed soon (it's actually already fixed and committed, but the patch has yet to roll out through the Ubuntu updater.)  Clicking any of the buttons will do apparently nothing, bringing up the error dialog again... you won't get any work done if you keep clicking that button.  If you're looking for a stupid button to click, you might as well score some points doing it! :P

**This Worked**
Quick fix is to do this stuff -- I don't know what it really does, and can't be bothered to research it -- to kill off the error and make life grand again:

Open Terminal of your choice (*ahem* [Yakuake rocks]("http://yakuake.kde.org/")! *cough*) & run these commands:


sudo apt-get install tracker-utils
tracker-processes -r

---

### Post by aklilom on 2009-08-17
> **nobodie said:**
> 
$sudo apt-get install tracker-utils
$tracker-processes -r



Thanks a lot. It worked for me too.

---

### Post by kakaz on 2009-10-26
I have problem my tracker-applet do not work at all  - it just disappear! And I cannot switch it on again - it just run in background but was not visible/accessible on desk-bar. Procedure You follow do not work for me. 

But I downgrade tracker from 0.6.93-0ubuntu3 to 0.6.93-0ubuntu1 and after that it seems to work! :p

Nop! It just start indexing but after 3 hours it pause, and never awake. It has no error message only information that it is idle, and had to be paused due to lack of disk space ( there is a plenty of free) or excessive disk usage ( there is none beside tracker itself). It was smail on my face when I open search box and obtain 70 entries on my search query but there was no thumbnails and no information about documents, only counter... So I am probably looser - I remove tracker ( which works great for me on previous Ubuntu release) and install Recall instead. Wow! It has realtime tracking of chosen directories,  DVI  ( and many more) formats works from the beginning, performance is not so bad, there are external helper applications based on mime types with reasonable config dialogue window! What a pity that tracker does not have one....

---

