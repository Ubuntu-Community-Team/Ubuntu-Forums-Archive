---
title: "Don't use Dapper as your primary desktop OS (discussion)"
date: 2005-11-15
forum: General Help
---

### Post by ubuntu_demon on 2005-11-15
This is the discussion thread for this sticky :
[http://www.ubuntuforums.org/showthread.php?t=93157](http://www.ubuntuforums.org/showthread.php?t=93157)

---

### Post by overcast on 2005-11-19
well dapper drake is test release but we can provide help for it.anyway,any geek is in trouble feel free to ask questions.

---

### Post by kristian on 2005-11-19
You don't really have a choice when g++ & libtool are incompatible in Breezy...

---

### Post by ubuntu_demon on 2005-11-19
I don't disencourage people to test Dapper. Just don't use it as your primairy desktop.

see also :

[http://www.ubuntuforums.org/showthread.php?t=86198](http://www.ubuntuforums.org/showthread.php?t=86198)

---

### Post by lean on 2005-11-19
It would be really nice if there were a guide (wiki) on how and when to test.
What problems are the developers aware of at a certain fase in the development?
When should I download a development version and report every little problem I find? When can I report kernel problems? User interface problems? And so on...
How can I help do regression tests - e.g what have been tested, what needs to be tested by real users?

---

### Post by samdude9 on 2005-11-19
It would also be nice if someone [SIZE="7"]told me where to get it![/SIZE]
sorry it makes me angry:mad:

---

### Post by Ampersand on 2005-11-19
If you're asking how to get dapper, just go through your /etc/apt/sources.list and replace every mention of breezy with dapper, then do an 'apt-get update'.

---

### Post by Chickenmonger on 2005-11-19
[QUOTE=samdude9]It would also be nice if someone [SIZE="7"]told me where to get it![/SIZE]
sorry it makes me angry:mad:[/QUOTE]

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

Daily CD image builds. Install and enjoy. Or, as the previous poster said, dist-upgrade to Dapper from Breezy.

---

### Post by floam on 2005-11-19
And, make sure if you're currently on the us.archive... servers that you change to the main ones.

---

### Post by psusi on 2005-11-21
[QUOTE=floam]And, make sure if you're currently on the us.archive... servers that you change to the main ones.[/QUOTE]

Seriously, what is the deal with the broken us mirrors?

And after the apt-get update, don't forget to apt-get dist-upgrade.

---

### Post by ofek on 2005-11-21
I use Dapper as my main distro on my laptop. I have a nice slackware to save me if I do something stupid but overall its not so hard to handle Dapper. For an alpha build its already pretty stable.

---

### Post by ygarl on 2005-11-21
Ditto - though I use Agnula as a backup cuz I like that Synaptic thang. Also have a DyneBolic live CD I use as well now and again...

---

### Post by ygarl on 2005-11-21
Ditto - though I use Agnula as a backup cuz I like that Synaptic thang. Also have a DyneBolic live CD I use as well now and again...

---

### Post by jatos on 2005-11-21
Actually I was planning on using it for my desktop OS, I have a live CD to save me

40 in fact, my shipIT has just arrived.

---

### Post by r4ik on 2005-11-21
My kids are om my primary and not planning to give it back. :)
So this is my primary now.
What on earth can go wrong after the W os?
Gonna ride this one out learn to understand Dapper.
Bugs crashes i dont care rebuild and learn.
Its the only way.
Read my sig.

---

### Post by ubuntu_demon on 2005-11-21
[QUOTE=r4ik]My kids are om my primary and not planning to give it back. :)
So this is my primary now.
What on earth can go wrong after the W os?
Gonna ride this one out learn to understand Dapper.
Bugs crashes i dont care rebuild and learn.
Its the only way.
Read my sig.[/QUOTE]

As long as your /home is on a seperate partition (and backed up) and you are willing to reinstall breezy when major breakage occurs probably nothing :)

---

### Post by SlowJet on 2005-11-21
If the CD Image is daily, why is it 3 days old?
When will it be built again?

I would like to install clean and try to rid the Synapic obsolete list.
I'm also getting network is obsoleted and it has resolving probelms (but boots ok)

The other thing is on one machine the ubuntu-desktop and hpijs printer package will not update but on the other they are updated. Both machines use a win smb shared printer so they are the same.

SJ

---

### Post by E-werd on 2005-11-21
Well, three days isn't going to make a major difference.  Your're going to do an update after you install anyways, right?  Three-days worth of updates is only around 100 (give or take) updates anyhow.

---

### Post by grumpymole on 2005-11-21
[QUOTE=SlowJet]
The other thing is on one machine the ubuntu-desktop and hpijs printer package will not update but on the other they are updated. Both machines use a win smb shared printer so they are the same.
SJ[/QUOTE]

I had the same problem.  Remove ubuntu-desktop, then update should bring everything back into sync.

Regards

Warren

---

### Post by SlowJet on 2005-11-22
Thanks Warren,

 I got 26 more updates after removing them and the HP was part of that batch.
The unbntu=desktop didn't go in but is in the not installed list.
The problem is I'm not sure if this is newer or the old one.

I got caught by the pcima-cs on the 2.6.15 kernel (A soft lockup)
So after 3 reboots (falling back) the remaining updates configured.
I then remove (totally) pcima-cs and went back in to the new kernel.
All worked again but ubuntu-desktop is not installed as I don't know it it is old or new. Version 82?

SJ

---

### Post by Anthem on 2005-11-22
I used Breezy from Colony 2 onward as a primary desktop without too many problems.

---

### Post by darius779 on 2005-11-22
Is this sticky basically saying "Warning: we are about to break X!"?

I hope so.. it would be worth it for X.org 7.0 :p

---

### Post by squibbon on 2005-11-22
So what's new with the Dapper? Can't find any difference from it's Screenshots at [http://shots.osdir.com](http://shots.osdir.com).

---

### Post by ubuntu_demon on 2005-11-22
[QUOTE=darius779]Is this sticky basically saying "Warning: we are about to break X!"?

I hope so.. it would be worth it for X.org 7.0 :p[/QUOTE]
Well probably

---

### Post by rwabel on 2005-11-22
I guess if people read carefully in this forum about problems while upgrading one can avoid a lot of problem by not blindly dist-upgrade all the time :-)

For example during a huge change (like gtk or xorg in breezy) I have been waiting until it got more secure to upgrade.

and if I'm no wrong when doing only upgrade you won't break much

---

### Post by ubuntu_demon on 2005-11-22
[QUOTE=rwabel]I guess if people read carefully in this forum about problems while upgrading one can avoid a lot of problem by not blindly dist-upgrade all the time :-)

For example during a huge change (like gtk or xorg in breezy) I have been waiting until it got more secure to upgrade.

and if I'm no wrong when doing only upgrade you won't break much[/QUOTE]
"dist-upgrade" can do it bit more and it is bit smarter than "upgrade"."dist-upgrade" can also install new packages. "upgrade" can only upgrade packages. Both can introduce breakage. Upgrading is a bit more safe regarding apt-get-hell prevention.

If you insist on running Dapper as primary OS instead of as test OS you can choose to only dist-upgrade during "colony cd" releases this way you have less chance of breakage(still very much possible!) but you are longer vurnarable to security problems. 

There will be a few "colony cd's" before the Dapper release. If I remember correctly breezy had 4 colony cd's, a preview release,and a RC before actually releasing.

---

### Post by rwabel on 2005-11-22
[quote=ubuntu_demon]dist-upgrade can introduce new packages and upgrade existing ones. upgrade can only upgrade packages. Both can introduce breakage. Upgrading is a bit more safe regarding apt-get-hell prevention.

If you insist on running Dapper as primary OS instead of as test OS you can choose to only dist-upgrade during "colony cd" releases this way you have less chance of breakage(still very much possible!) but you are longer vurnarable to security problems. 

A new colony cd may get released each couple of weeks (If I remember correctly breezy had 4 colony cd's and a preview release before actually releasing).[/quote]

thanks for the information. So far dapper works fine ;-) no wonder there aren't many differences, mainly sync to sid I guess.

---

### Post by trinaryouroboros on 2005-11-24
[QUOTE=ubuntu_demon]I don't disencourage people to test Dapper. Just don't use it as your primairy desktop.

see also :

[http://www.ubuntuforums.org/showthread.php?t=86198](http://www.ubuntuforums.org/showthread.php?t=86198)[/QUOTE]

Sorry but, I couldn't resist. Hoary Hedghog made me ditch my Windows Disks, and, I was a bit worried about changing from something that worked so good, to the originally very buggy Breezy, but Dapper Drake is awesome. Good work, and, don't be mad if I keep it as my Primary Desktop, please.

I promise I won't litter the forums with my n00b mistakes.

---

### Post by Jonne on 2005-11-24
I'm using dapper as sort of a crash course to Linux. If stuff breaks, i'll learn a lot more about Linux then running a smooth, stable release version ;).

Besides, I don't need much. As long as apache, mysql, a browser and a text editor are available, i can be productive ;). (I've had some problems after I upgraded the kernel, but it keeps running anyway, so it's not really a priority for me to find out what's wrong).

I also have the liveCD of Hoary and a partition with windows to fall back on.

---

### Post by ubuntu_demon on 2005-11-24
[QUOTE=trinaryouroboros]Sorry but, I couldn't resist. Hoary Hedghog made me ditch my Windows Disks, and, I was a bit worried about changing from something that worked so good, to the originally very buggy Breezy, but Dapper Drake is awesome. Good work, and, don't be mad if I keep it as my Primary Desktop, please.

I promise I won't litter the forums with my n00b mistakes.[/QUOTE]
I haven't encountered much bugs in breezy. But that's where repositories like breezy-updates and backports are for they make breezy very usable for the average desktop user.

---

### Post by Burning Bronx on 2005-11-24
As for now Breezy is acting more stable than Breezy for me. Even the 2.6.15 kernel and the xorg 7.0.0 RC2 are acting quite smooth...

---

### Post by trinaryouroboros on 2005-11-24
> **Jonne]I'm using dapper as sort of a crash course to Linux. If stuff breaks, i'll learn a lot more about Linux then running a smooth, stable release version  said:**
> 

That's the way to be my man, good times, and good luck with your learning adventure.

[QUOTE=ubuntu_demon]I haven't encountered much bugs in breezy. But that's where repositories like breezy-updates and backports are for they make breezy very usable for the average desktop user.

This is true, point taken. I'm not against Breezy, mind you. I think it's a bit more simplified than Hoary too, so in leui of said response I've actually just got mail with 10x Breezy CD-Roms (32-bit) to distribute, and 5x 64-bit versions, for those around me intending to get the most out of their new processors. 

It's a bit easier to work with than Hoary too. The main reason I guess I like Hoary alot more is because I notice a difference in speed, and originally like I said, there was more stability. Breezy seems pretty stable now, however, since it's official release and it's definitely my choice for the average user.

Like Jonne said, I'm diving back into Linux, and Hoary was the original inspiration - and dropping all fear I've plunged into Dapper Drake a bit more armed than before, and in better hopes of learning more.

Also, I had originally decided to be indifferent about Linux altogether since...way back when. I believe Slackware 8 was just released when I decided to quit in fact, so it's been a re-learning + new-learning experience, and a wonderful one at that.

---

### Post by limit223 on 2005-12-09
What I've done so far just trying to get rid off some problems in Breezy I upgraded most of multimedia programs from Dapper and the result was really amazing...vlc was behave normally, alsa lost that bothering buzz in sound, Kaffeine was more stable than in Breezy and probably many other worked better. 
Reading all above, you convince me to have a try upgrading whole system to Dapper after a complete image of actual system (backup) as long as I do not concern about the kernel (I've got lots of helping hints how to compile myself acording to my hardware architecture).

---

### Post by Anthem on 2005-12-09
[QUOTE=limit223]What I've done so far just trying to get rid off some problems in Breezy I upgraded most of multimedia programs from Dapper and the result was really amazing...vlc was behave normally, alsa lost that bothering buzz in sound, Kaffeine was more stable than in Breezy and probably many other worked better.[/QUOTE]
Are those using gstreamer .8 or .10?

---

### Post by limit223 on 2005-12-09
0.8 is the one installed in my system

---

### Post by benplaut on 2005-12-13
is there a list anywhere of new stuff breezy > dapper? 

i think i'll install after colony 3 (or whatever they're called), same as i did with breezy. I'll have 2 systems by then, so i can mess around with one :)

---

### Post by Burning Bronx on 2005-12-14
The new stuff for breezy is in the backports repos and even if something is nto there you can always try to compile it on your own. Also you can check other distro's releases with alien. You can check those alternatives out and also check the backports forum right here to see what plans lie in the backports project ~_~ 

Paz.

Oh yeah almost forgot - Dapper dev branch releases are called "Flight" (flight is to Drake the same way colony is to Badger :P )

---

### Post by christooss on 2005-12-15
Which Gnome version is in dapper?

It would be really nice if we could find list of new packages.

---

### Post by shrift on 2005-12-15
[QUOTE=christooss]Which Gnome version is in dapper?

It would be really nice if we could find list of new packages.[/QUOTE]

Dapper currently runs  Gnome 2.13.3

---

### Post by fog on 2005-12-15
2.13.3

[IMG]http://img528.imageshack.us/img528/7568/screenshot7cy.jpg[/IMG]

Edit:you are fast :)

---

### Post by earobinson on 2005-12-15
Use it as your primary OS if you like, use it to defend the free world, Just expect it not to work all the time :)

Disclamer/Edit: I have not read the whole thread just wanted to get my $0.02 in.

---

### Post by Mizzou_Engineer on 2005-12-16
[QUOTE=squibbon]So what's new with the Dapper? Can't find any difference from it's Screenshots at [http://shots.osdir.com](http://shots.osdir.com).[/QUOTE]

Actually, Dapper runs better on my computer than Breezy did. Especially when you update KDE to 3.5 on Breezy. I can *finally* suspend to RAM and hibernation looks like it will work in the final release. Neither worked in Breezy. And yes, I have /home on its own partition so I can reinstall pretty quickly if I need to.

---

### Post by anil_robo on 2005-12-22
I'm downloading dapper right now and I will use this as my ***only*** OS.
(Don't worry I have taken a backup of all my important data and have live cds of Breezy and Knoppix at hand) :)

---

### Post by anil_robo on 2005-12-22
By the way, one safe way of trying Dapper would be to run it from Breezy using Vmware player! Am I correct?:confused:
But from where will I get a vmware image of Dapper?

---

### Post by trinaryouroboros on 2005-12-22
[QUOTE=Mizzou_Engineer]Actually, Dapper runs better on my computer than Breezy did. Especially when you update KDE to 3.5 on Breezy. I can *finally* suspend to RAM and hibernation looks like it will work in the final release. Neither worked in Breezy. And yes, I have /home on its own partition so I can reinstall pretty quickly if I need to.[/QUOTE]

This is true for me as well, I'm not positive, but perhaps amd64 is favored in dapper?

---

### Post by ameerirshad on 2005-12-22
[quote=Jonne]I'm using dapper as sort of a crash course to Linux. If stuff breaks, i'll learn a lot more about Linux then running a smooth, stable release version ;).

Besides, I don't need much. As long as apache, mysql, a browser and a text editor are available, i can be productive ;). (I've had some problems after I upgraded the kernel, but it keeps running anyway, so it's not really a priority for me to find out what's wrong).

I also have the liveCD of Hoary and a partition with windows to fall back on.[/quote]

Counts for me too! I have my info secure set away, so if my Dapper crashes, I just start all anew :razz:

---

### Post by paddy2706 on 2005-12-22
[quote=anil_robo]By the way, one safe way of trying Dapper would be to run it from Breezy using Vmware player! Am I correct?:confused:
But from where will I get a vmware image of Dapper?[/quote]
look for it, i saw it just yesterday here in the forums:)

---

### Post by anil_robo on 2005-12-22
[quote=anil_robo]I'm downloading dapper right now and I will use this as my ***only*** OS.
(Don't worry I have taken a backup of all my important data and have live cds of Breezy and Knoppix at hand) :)[/quote]

I told Breezy install CD to resize a windows partition. It resized it within 3 minutes and the partition icon was shown by a "smiley" in the partitioner. I think the smiley indicates a healthy partition.

Next, I setup windowsXP first on my laptop and I see that the resized parition is no longer working. When I click on it, windows asks "this partition is not formatted. Do you want to format it now?" Obviously, resizing has been unsuccessful!

Then I try to install Dapper by using their daily CD image for 21st December 2005. I boot through the CD well. There are a few errors in the setup, the most notable being "The setup cannot detect a valid linux kernel. WIthout it, the installatino would be unsuccessful. Would you still like to continue? I tried to continue still, but so many error messages were popping up. Did I download the wrong CD image?

I installed Breezy again, took about two hours to set it up. Then as I popped in the dapper CD, Breezy detected it and wanted to run synaptic. I said "OK". It asked about updating some 300+ packages. I said yes. Lots of error messages (can't update, can't upgrade, try dist-upgrade etc). I rebooted (old habit - I've been on windows for more than ten years now) and saw a broken X.

Screwed up everything very badly! :(

---

### Post by vvlist on 2005-12-22
Use Dapper only for bug reporting, development, or if you want to learn how to use debian-based distros with or without the x-server. And there's always those bleeding-edgers too, that must have the latest and greatest, who don't care about stability. I've used Dapper from the beginning, and I must say, it has been  a learning experience. Just backup your stuff, it would be a good idea.

---

### Post by trinaryouroboros on 2005-12-23
[QUOTE=vvlist]Use Dapper only for bug reporting, development, or if you want to learn how to use debian-based distros with or without the x-server. And there's always those bleeding-edgers too, that must have the latest and greatest, who don't care about stability. I've used Dapper from the beginning, and I must say, it has been  a learning experience. Just backup your stuff, it would be a good idea.[/QUOTE]

Damnit, you got me on all three counts.

:lol:

---

### Post by autocrosser on 2005-12-23
Well-I triple-boot--Dapper-Breezy & OSX (I boot OSX less than once a month now!!:D ). I installed Dapper right before flight2 & have had only minor issues with X & gnome panel----on top of all that, Dapper runs slightly faster on my Dual 1.25G MDD Mac. 
 
All-in-all, I'm ready for any major bumps in the road (I backup my Dapper user in Breezy & on a seperate external drive) & really like doing the troubleshooting when it comes up. 
 
If that makes me a geek----bring it on-------I am doing what I can to help the community.:smile:
 
And hey--I just talked my wife thru a problem (on the phone!!!!!) to get her back to the desktop------& she understood it!!!!

---

### Post by bites on 2005-12-23
Hi!

I've been using Dapper as my primary OS for a few weeks now, and I haven't encountered any serious problems so far :-)  Even if Dapper is considered "unstable", it seems to be more stable than the distro I used before (ArchLinux, a great distro, but sometimes a bit too unstable and it required quite a bit of configuration).

---

### Post by nystire on 2005-12-24
[QUOTE=Ampersand]If you're asking how to get dapper, just go through your /etc/apt/sources.list and replace every mention of breezy with dapper, then do an 'apt-get update'.[/QUOTE]

I tried this on my test pc (thank $DEITY for those) and it does on the locale packages. Nothing I can think of works. Apparently dpkg returns an error of 1 when trying to install/uninstall/fiddle with locales, and languagepack_en for base and for gnome. 

Sorry for the lack of correct names and clarity, but I'm doing this through a haze produced by too much sleep, flu and some drugs which are supposed to help with the flu but which somehow are not producing the correct effect.

I'm downloading the latest build image. Maybe that will work. If not, does anybody have any suggestions? As I said, this is a test pc so I can wipe the hard-drive clean with no problems at all...

---------------------------------------------------------------------------------------------------------
:$ Never mind. I have to put a HUGE notice next to my monitor telling me to FIRST search the forums and only if I don't find anything to then post. I'd blame my current state of mind, but I doubt it would help matters.

---

### Post by erdalronahi on 2006-01-15
Hi,

I wanted to try Dapper without making a new partition or endangering my breezy installation. So I tried to upgrade from Breezy in a virtual machine (VMware Player) running under Windows XP. I didn't believe my eyes: It just worked perfectly!

Here is how I did it:

First I replaced all occurences of "breezy" with "dapper" in synaptic. No commandline needed here.

Then I rebooted and went into the recovery mode. Here all I did was 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

It took about one hour, afterwards I started with "startx" and everything, just everything worked. Inside Windows XP! Unbelieveable!!! Sure there is no "safer" way of trying Dapper.

Great thanks to the Ubuntu team and to VMware.

---

### Post by erdalronahi on 2006-01-15
[QUOTE=erdalronahi]It took about one hour, afterwards I started with "startx" and everything, just everything worked.[/QUOTE]

Well, it seems I was too enthusiastic too early. It worked exactly until the reboot. That was the end of all my dreams. Dapper doesn't find "/dev/sda1" and stops quite early in the boot process.

But until the reboot everything worked fine, including internet, sound etc.  :)

Anyway, VMware Player looks like a nice chance to try, now I can clone my breezy installation in 10 seconds and give it another try.

---

### Post by bonzodog on 2006-01-15
I have decided to replace breezy with dapper today, have to say it seems stable enough. I am the sort of person though who can cope with breakages, as I am an ex slackware user and helped on the devel of slamd64. Editing conf files, and manually doing things in the CLI is no biggy to me.

---

### Post by Ainvar on 2006-01-15
I am taking the plunge on a perfectly working boot of breezy on my Dell M70 laptop and upgrading it to dapper. I do have my /home on a seperate partition that I backed up already to an external drive and also onto a couple of dvd-rws

If all else fails I can reformat and go from there or just wipe it all out from windows and start agian also.

---

### Post by Anthem on 2006-01-15
Breezy's been working fine for me... I've been running it as my primary for a week now.

---

### Post by BoyOfDestiny on 2006-01-16
[QUOTE=Anthem]Breezy's been working fine for me... I've been running it as my primary for a week now.[/QUOTE]

I think you mean Dapper.

Anyway, I've been running Dapper amd64 since the 7th of january. I'm getting better 3d with open source radeon driver [radeon 9250] (better since in breezy amd64 glxinfo would hang for me). 

The only downside is that it no longer sees my gamepad (psx controller+ radioshack usb) which worked fine in hoary and breezy... mounts them to input/blah instead of dev/js0 (from memory, forgive me if those are way off).

As for the warning... doesn't matter. I have another machine with breezy as a backup [laptop], various live cd's, and a breezy amd64 install disc (which I reinstalled once just for kicks, had my system up and running in less than 30minutes).

My only advice is if you foul something up (which I did when I ran breezy during testing), always put /home on another partition. Makes reinstalling painless. And of course to remember this is not a 'stable' release, even though I've yet to see it crash. Just expect that things might go wrong, and make sure you have a plan b, c, .... maybe up to j. ;)

Happy testing!

---

### Post by Ali_Baba on 2006-01-16
I've been using Dapper since the repos were opened.It has been fun and I think really stable also.Only the ati drivers are broken now.Haven't had to play with X or like with keyboard.Much better than it was before with Breezy development.Thanks to everyone who is developing Dapper :D

---

### Post by MaX on 2006-01-16
[QUOTE=erdalronahi]Well, it seems I was too enthusiastic too early. It worked exactly until the reboot. That was the end of all my dreams. Dapper doesn't find "/dev/sda1" and stops quite early in the boot process.

But until the reboot everything worked fine, including internet, sound etc.  :)

Anyway, VMware Player looks like a nice chance to try, now I can clone my breezy installation in 10 seconds and give it another try.[/QUOTE]

That's not dappers fault realy... you need to change a line in the vmx file...
Something to do with how the disc is read. You should be able to find it by searching on the forum....

---

### Post by bonzodog on 2006-01-16
I have noticed a curious niggling little problem...
I have installed the nvidia 3D drivers successfully, but my monitor is running at 75hz, which for some (unknown) reason, makes it create a blurry line on the left hand side. If i bump the frequency down to 60hz the line disappears, and it is all crystal clear. Thing is, I have altered it in gnome's resolution config, but I use WindowMaker as my primary desktop, so need to actually alter xorg.conf, but cannot for the life of me remember where the overall refresh rate is set. The vertical refresh rate in the 'monitor' section reads '43-60', so it's not there....
Ideas anyone?

---

### Post by jbaloul on 2006-01-17
been on dapper since day 1...
have a few words of wisdom as well:
"only the strong survive"
"what does not kill you makes you stronger"
"latest & greatest = bleeding edge = sleepless nights"

Love my Dapper and would not trade it for anything else!!!

---

### Post by geekphreak on 2006-01-23
OK, Dapper is not my primary desktop OS b/c I was unable to install it for some reason. But if I continue using Breezy, will I still be abke to upgrade to Dapper w/o reinstalling everything? How would that work considering all the planned changes for Dapper in contrast to Breezy?

---

### Post by geekphreak on 2006-01-23
Where's the delete post button? I'm kinda not seeing it...

---

### Post by TheDude on 2006-01-23
I finally made the plunge to Dapper and it's working fine so far\\:D/

---

### Post by earobinson on 2006-01-23
Im pretty sure this post was started when dapper was made before flight 1 I still used it but you cant expect it to work all the time.

---

### Post by christooss on 2006-01-24
Im using dapper for a day. And I like its speed and that there is no problems with slownig down.

---

### Post by fannymites on 2006-01-24
I've been using dapper since day one and although I've had no breakages or any major problems at all, the computer is running horribly slow with 2.6.15-xx kernels.  Slow to the point of being almost unusable.  I'm running another install of dapper as my "stable" os but with udev pinned and the kernel held back to version 2.6.12-10 and it runs like the wind.
I know the 2.6.15-xx kernels are running fine for many other people but i can't work out what the problem is.  I'm running a 2.6.15-xx on suse and that runs very fast so it's obviously something specific to the ubuntu package that's giving me jip.
If it's running this slow when dapper goes final I'm worried I'll have to give up on ubuntu.

---

### Post by scpike on 2006-01-24
so is dapper getting to a point where it is stable enough to use on a day-to-day basis, as long as you're willing to cope with occasional breakages?

---

### Post by RAOF on 2006-01-24
[QUOTE=scpike]so is dapper getting to a point where it is stable enough to use on a day-to-day basis, as long as you're willing to cope with occasional breakages?[/QUOTE]
It's been that way for a couple of months, at least for me :)

---

### Post by SlowJet on 2006-01-25
No, not quit. A few more fixes and then if you install a clean CD and don't update it will be pretty good. Flight 4 may be a good time?


SJ

---

### Post by gn0me on 2006-01-27
Personally, really loving where Ubuntu's going. Currently a semi-Windows user (I don't even use the computer that much as I work so much), but tried a dapper upgrade with apt-get and killed it on the reboot, and for some reason it hates my USB keyboard and I'm not able to type anything during the boot-up process. Just downloading an overnight ISO and going to try it when I wake up, but yeah.. definitely loving where it's going and have been watching WINE's development daily (religiously (I actually really don't like Windows much and can't wait to be 100% linux-user (damn you gaming addiction (parenthesis power)))). 

Just a bit of a newbie lately, but slowly learning how to get linux going and eventually going to move more into hosting stuff. I got Apache and all that working slowly, hoping to eventually use Ubuntu in my friend's LAN center for the server box.

Keep up the good work and I hope the awesome changes in dapper are only the beginning. :D

---

### Post by skyboy on 2006-01-27
I did the big Jump too :) I love it, things went pretty smoothly for me. Just for me, and in my opinion, kaffeine shouldn't be included as default application. Xine-ui is much better for me for DVD and movies, amarok for music. Kaffeine is just good for dvb, otherwise it is pretty lame application but again that is my opinion.

---

### Post by fannymites on 2006-01-27
The dapper experience has been different for so many people.  It was my primary os 
until about a week ago but now I'm finding it's getting worse by the day.
I did a fresh install from the flight 3 cd yesterday and it hasn't improved.
I've re-installed breezy on another partition because dapper has really become really unusable to me now and it's hard to do any subjective testing of anything when it's running so badly.
I can't really put my finger on what's wrong, I've mentioned in a couple of other threads that my computer has been running horribly slowly with the 2.6.15-xx kernels but there are no real specific problems.  I've no intention of giving up just yet though.  I'll still keep messing around with it and doing my updates but I can't use it as a primary or much of anything else right now.
I'm looking for a new toy for now.  I'm already bored of gentoo and I got bored of fedora rawhide long ago so without dapper I'm lost.

---

### Post by trinaryouroboros on 2006-01-27
[QUOTE=gn0me]Personally, really loving where Ubuntu's going. Currently a semi-Windows user (I don't even use the computer that much as I work so much), but tried a dapper upgrade with apt-get and killed it on the reboot, and for some reason it hates my USB keyboard and I'm not able to type anything during the boot-up process. Just downloading an overnight ISO and going to try it when I wake up, but yeah.. definitely loving where it's going and have been watching WINE's development daily (religiously (I actually really don't like Windows much and can't wait to be 100% linux-user (damn you gaming addiction (parenthesis power)))). 

Just a bit of a newbie lately, but slowly learning how to get linux going and eventually going to move more into hosting stuff. I got Apache and all that working slowly, hoping to eventually use Ubuntu in my friend's LAN center for the server box.

Keep up the good work and I hope the awesome changes in dapper are only the beginning. :D[/QUOTE]

I actually have the same problem, but it's not relative to the OS('s) installed. The BIOS just has no idea how to treat USB keyboards, pretty silly too, considering it's bleeding edge equipment I have.

---

### Post by trinaryouroboros on 2006-01-27
[QUOTE=fannymites]The dapper experience has been different for so many people.  It was my primary os 
until about a week ago but now I'm finding it's getting worse by the day.
I did a fresh install from the flight 3 cd yesterday and it hasn't improved.
I've re-installed breezy on another partition because dapper has really become really unusable to me now and it's hard to do any subjective testing of anything when it's running so badly.
I can't really put my finger on what's wrong, I've mentioned in a couple of other threads that my computer has been running horribly slowly with the 2.6.15-xx kernels but there are no real specific problems.  I've no intention of giving up just yet though.  I'll still keep messing around with it and doing my updates but I can't use it as a primary or much of anything else right now.
I'm looking for a new toy for now.  I'm already bored of gentoo and I got bored of fedora rawhide long ago so without dapper I'm lost.[/QUOTE]

I liked pre-flight3, was lightning quick with my hardware.

---

### Post by unf on 2006-01-27
I love it, dapper flight 3 and everything work right with begin... just fantastic its on my primary desktop!!

---

### Post by eeclark on 2006-01-27
Flight 3 worked great...then I did an upgrade. Now I get errors that the sound card is not detected (but it still plays sound). Go figure.

I love it anyways. Breezy was good (of course it was, I was using a final rev.) :-) Dapper will be great when finished.

---

### Post by trinaryouroboros on 2006-01-27
Has anyone had fun with Kubuntu Dapper? So far, I'm pretty impressed! Plus, no real trouble detected.

---

### Post by livingtarget on 2006-01-27
Once dapper hits i'm gonna go off these development releases I think, it's nice to be on the bleeding edge but it takes quite a lot of effort. 

It's running fine as my primary desktop though, but there is plenty of breakage and most notably some application breakage.

---

### Post by leech on 2006-01-27
I was going to stick with Breezy, but too many things were broken in it for my tastes .  (Mainly the GCC stuff).  I do use Breezy on my server.

Leech

---

### Post by trinaryouroboros on 2006-01-28
[QUOTE=livingtarget]Once dapper hits i'm gonna go off these development releases I think, it's nice to be on the bleeding edge but it takes quite a lot of effort. 

It's running fine as my primary desktop though, but there is plenty of breakage and most notably some application breakage.[/QUOTE]

I second that motion, who has this much time to troubleshoot?

Especially when you serve a large portion of the community's troubleshooting needs anyway.

---

### Post by OneSeventeen on 2006-02-17
I'm assuming I could dual boot until the official release, correct?

Meaning I'd like to have Dapper as primary (so it forces me to fill out bug reports) but have Breezy as a backup.

Any tips on doing this, or is it the same method as dual-booting windows and linux?  (If there are no differences between doing this and dual-booting any other two linux OSes, just let me know and I'll google for it, to keep this topic on track)

---

### Post by fannymites on 2006-02-17
No difference.  Just think of it as a seperate distro.  Unless you are planning to share any directories.

---

### Post by Nyati on 2006-02-21
I've recently installed Dapper on my IBM T30 with no problems except being able to connect to the internet.

I developed a script which enabled me to connect to the net using my usb Speedtouch 330 modem.

I attempted an installation of the packages required and everything was accepted, although these were the required packages for 5.10.

On command: #tail -f /var/log/messages

I plugged in my usb modem and got the response:

usb 2-2: new full speed USB device using uhci_hcd and address 4
usb 2-2: reset full speed USB device using uhci_hcd and address 4
speedtch 2-2:1.0: no stage 1 firmware found!

Can anybody tell me where I can get a workable firmware download that is compatible with Dapper, please?

---

### Post by steveneddy on 2006-02-22
Maybe I missed it, but, what Kernel version will we get when Dapper is finally released? 

I'm looking forward to the new Gnome and the shiney new Ubuntu. 

At this time I would like to thank everyone that gave us this wonderful distro we know as Ubuntu. May the world be made a better place and peace come to all because we are using Ubuntu. :D

PIII (935mhz), 512mb, 40gig x2, Ubuntu 5.10 "Breezy Badger", Dual boot with the "W" word. I also have a Mac Power PC that still works and still gets on the internet from time to time.

---

### Post by lompolo on 2006-02-23
How about adding link to flight live-cd:s and comment like this "If you want to test your hardware with dapper or see how good dapper is now  you can use live-cd:s without (big) risk."?

---

### Post by obe1kenobi on 2006-02-28
Will this cause any problems if I install it on another partition from my Breezy?

---

### Post by jstueve on 2006-02-28
[QUOTE=obe1kenobi]Will this cause any problems if I install it on another partition from my Breezy?[/QUOTE]

I did it on my system no problem.

I usr LVM, and the installer was able to distinguish which partitions were which after enabling LVM, (manual partitioning).

worked fine... you may have some trouble if home is on a separate partions and have the same account on both Breezy and Dapper...

I ended up biting the bullet, and will work with Dapper from now on, it has been stable enough.

---

### Post by cowmix on 2006-03-13
Ok.. I am about to deploy two desktops and one server in a small office.. Do I dare try Dapper for this?   I just think it would be a shame to do Breezy if Dapper is pretty much done..

If I do Dapper, will it allow me to upgrade without doing a complete reinstall when the true release comes out?

---

### Post by sandyeggoboy on 2006-03-13
GEEZ!! I sure wish I had known that a loooonnnggggg time ago. now here i sit looking out over my desk, ihave disks from hoary, disks from breezy, downloads from dapper 1, 2, 3, and now 4. Backups for MY DATA from every version so i am totally lost when someone asks me for a file i have to go through a hundred CDs to find it. Its that simple? You gotta be kidding me ..........


(FEELING REALLY STOOPID)

---

### Post by anil_robo on 2006-03-14
Ubuntu should have a "UNIVERSAL INSTALL CD" which would be internet based. The CD would boot up as a live cd, connect to the internet to find all the available releases of ubuntu, and then give the user an option to install the most updated version from the internet.

The same CD could be utilized to install any release of Ubuntu, because it's totally internet based!!

Anyone supports this idea? Or has it already been done by someone??

---

### Post by jakeee on 2006-03-14
I have once again experienced the reason why I should not use unstable distros. My X broke and it had something to do with fonts but luckily I managed to fix it :)

---

### Post by trinaryouroboros on 2006-03-17
[QUOTE=anil_robo]Ubuntu should have a "UNIVERSAL INSTALL CD" which would be internet based. The CD would boot up as a live cd, connect to the internet to find all the available releases of ubuntu, and then give the user an option to install the most updated version from the internet.

The same CD could be utilized to install any release of Ubuntu, because it's totally internet based!!

Anyone supports this idea? Or has it already been done by someone??[/QUOTE]

That is an incredibly smart idea, but doesn't each distro automatically update itself and download fresh files off the Internet anyway during installation? I see wget being used a million times during the install.

---

### Post by anil_robo on 2006-03-18
[quote=trinaryouroboros]That is an incredibly smart idea, but doesn't each distro automatically update itself and download fresh files off the Internet anyway during installation? I see wget being used a million times during the install.[/quote]

Yes each distro does upgrade itself through internet, but we still have to download 600MB data each time, and burn a fresh CD in order to install that. 

If such a "Universal Install CD" is made, it will tremendously reduce the hassle of downloading large data and burning a fresh CD each time we want to install the latest Ubuntu. The number of CDs from shipit over an year or two will reduce as well. It'll be so nice to see that I can use the same CD to install/upgrade Warty, Hoary, Breezy, Dapper, Groundhog, Elephant and so on... This will reveal the true power of linux, when the same CD will be able to install the latest release of Linux even after a decade!

I know I am sounding too ambitious, but I think it should be possible.

By the way: Unfortunately not all people are able to "upgrade" successfully from one Ubuntu version to the next. For example, I had to reinstall Dapper afresh before I could use it (and I broke it twice, to reinstall it again). In this situation, the user can use the same CD to install either of these distros (Warty, Hoary, Breezy, Dapper, Groundhog, Elephant or whatever) and stick with what works best. Imagine having to download 600MB for each of these and then burning each in a CD to try it out.

---

### Post by shamrock_uk on 2006-03-18
[QUOTE=cowmix]Ok.. I am about to deploy two desktops and one server in a small office.. Do I dare try Dapper for this?   I just think it would be a shame to do Breezy if Dapper is pretty much done..[/quote]

It depends how badly you want to avoid downtime. It's just bugfixes from here on in AFAIK, so things should be less likely to break, but the disclaimer still applies - you shouldn't *expect* it to work without faults. For a critical server I would recommend Debian Sarge in any case - you should be using something that has at least a year of testing rather than an 'in development' distro like Dapper.

I have to say that the current Dapper is the most stable desktop linux distro I've ever used, but whether to risk it in an office is entirely up to how much money in lost revenue it'll cost you if something breaks.


> If I do Dapper, will it allow me to upgrade without doing a complete reinstall when the true release comes out?

In practice, the dist-upgrade from Breezy seems to be several hundred megabytes for me - I suspect that it's almost as much as installing from scratch. Personally, I would recommend a fresh install in any case, both out of prudence (to avoid being stuck with old config files) and because a dist-upgrade from Breezy borked my installation.

---

### Post by fannymites on 2006-03-18
This speak of a universal cd sounds like a good idea, as long as it is alongside regular installation cd's and not instead of.
Some people on dial-up or people like me who use an adsl modem with the eciadsl driver or any driver that needs compiling need a working install to be able to compile the driver before they have internet access at all.

---

### Post by anil_robo on 2006-03-18
[quote=fannymites]This speak of a universal cd sounds like a good idea, as long as it is alongside regular installation cd's and not instead of.
Some people on dial-up or people like me who use an adsl modem with the eciadsl driver or any driver that needs compiling need a working install to be able to compile the driver before they have internet access at all.[/quote]

True! I love this idea! Now who will write the spec for it? :rolleyes:

---

### Post by Gallows on 2006-03-19
If you wanted to use a "Universal Install CD" try the Debian [netinst]("http://www.debian.org/CD/netinst/") CD.  Assuming you have fast ethernet presented Internet access, boot the machine up and perform a minimal install.  Once you minimal Debian install is up and running modify the apt sources.list file (found in /etc/apt/sources.list) with whaever version of Ubuntu you want to install.

And as root:
```
apt-get upgrade
apt-get dist-update
apt-get install ubuntu-desktop
```

Perhaps it's not the best way of installing Ubuntu over the network but it's a start.

---

### Post by Bosonator on 2006-03-28
So I have this... *ahem*... "friend" who upgraded his primary system to Dapper and I want... I mean "he" wants to revert to Breezy. "He" tried to replace all occurances of  'dapper' with 'breezy' in "his" sources.list, but apt won't revert back to the old packages. Any suggestions for my "friend"?

---

### Post by The Warlock on 2006-03-28
[QUOTE=Bosonator]So I have this... *ahem*... "friend" who upgraded his primary system to Dapper and I want... I mean "he" wants to revert to Breezy. "He" tried to replace all occurances of  'dapper' with 'breezy' in "his" sources.list, but apt won't revert back to the old packages. Any suggestions for my "friend"?[/QUOTE]


Back up your home folder and break out your Breezy install disc?

---

### Post by aamukahvi on 2006-03-28
At moments like this, a "Told you so" is just... :mrgreen:



Sry.

---

### Post by Turgon on 2006-03-28
[QUOTE=Bosonator]So I have this... *ahem*... "friend" who upgraded his primary system to Dapper and I want... I mean "he" wants to revert to Breezy. "He" tried to replace all occurances of  'dapper' with 'breezy' in "his" sources.list, but apt won't revert back to the old packages. Any suggestions for my "friend"?[/QUOTE]

IM sorry, but I don't think its passable to revert without a reinstalation.

Anyway, why would you friend like to go back?

---

### Post by shrift on 2006-03-28
[QUOTE=Bosonator]So I have this... *ahem*... "friend" who upgraded his primary system to Dapper and I want... I mean "he" wants to revert to Breezy. "He" tried to replace all occurances of  'dapper' with 'breezy' in "his" sources.list, but apt won't revert back to the old packages. Any suggestions for my "friend"?[/QUOTE]


The reason that apt won't revert to breezy packages is because it will only install "updated" packages. That is packages that have a newer version # than the ones you have installed. Becauseo of this apt won't replace any packages until Breezy has a "newer" to replace it with, and because breezy is the stable release, it only gets security updates, which means that it will never really update itself back to all breezy. 

The suggestion above about saving your home folder then reloading from a breezy disc is the easiest. Alternatively you could *try* to tell apt to reload old versions of all the packages, but that would be painstaking and I would highly discourage trying to do that as, inevitably, some package would get left behind and would screw stuff up. 

But as queried above.... why go back to breezy? Dapper is tons better!

---

### Post by DarkDancer on 2006-04-08
So, how much would be involved with moving over to Dapper (I am sort of new to Linux and have never changed distros, breezy was my first one). Can I do an upgrade or do I need to do a full reinstall? Someone said something about backing up my home directory.....?

---

### Post by CyberCam on 2006-04-08
The best thing to do is find yourself an old hard drive... say a 10GB to 20GB and use that as your beta testing drive. That's what I do! That way I don't break anything in my primary desktop OS. :)

---

### Post by DarkDancer on 2006-04-08
So are you saying that I should just hang here with Breezy till Dapper is "finished"? (Seriously I don't have the extra drive space to throw on another partition and I don't have a 10 or 20 gig drive lying around.... ;) )

---

### Post by CyberCam on 2006-04-08
I'm saying you should use the suggestion above (backing up your /home directory and reinstalling). Then if you want to mess around with any future betas, go to a computer store that sells old hardware and buy yourself an old hard drive, that way if you break anything or do not like what the new beta has to offer then you just switch back... no problems. That's the way we do it in the IT biz (we usually have another old pc but I don't expect you to purchase another pc). ;) It's the poor man's way of beta testing!

---

### Post by DarkDancer on 2006-04-08
Oh, that's ok, I have no desire to use any betas (unless like Dapper, they are so close to final release that they might as well be in final release.).

---

### Post by SlCKB0Y on 2006-04-09
I formally used Debian Unstable which is  more or less the same as using Dapper. I used it for years, and if you know what you are doing, most times you can fix any small problems which might occur. I never found it an issue if for example I couldnt play mp3's for a week. I guess it all comes down to what you expect to get out of your computer.

I mean If im ever using dapper or deb unstable and something breaks (thank god iver never had X break in any major way that I cant fix..touch wood), I just think back to the time when I was using linux 8 or so years ago, where a stable release back then was probably more buggy than an developement release now. The exception back then was always Slackware and Debian. Those ones could always be trusted to be rock solid even that long ago. 

I'm not claiming to be a linux guru, because I am not, I am simply a very experience linux user who has used linux as his primary desktop for about 7 years. These days I wont even tarnish my MBR by ever installing Windows on my computer. Since I am not an avid gamer, I have everything i need and more. 

Put simply, in terms of eyecandy and both hardware support and detection, linux users today are absolutely spolt by comparison. Back then if you wanted everything to work, you not only had to either be very lucky, or go out and buy hardware which you knew worked with linux. It was also oldish hardware. Oh and then there was the fun of compiling a kernel to support most if not all of you required hardware, OR sourcing drivers from cvs for pretty much everything and editing the config files for all the nonkernel applications to use you hardware.

So basically, stop your whining :D 

/me hugs his dapper install

---

### Post by htinn on 2006-04-09
Dapper beats the heck out of the twice daily crashes, the constant spy-ware infections, and the occasional unidentified ROOTKIT I would get in Wind'ohs.

---

### Post by Anthem on 2006-04-09
[QUOTE=htinn]Dapper beats the heck out of the twice daily crashes, the constant spy-ware infections, and the occasional unidentified ROOTKIT I would get in Wind'ohs.[/QUOTE]
I love this forum, but I wish people would stop this silliness.

I obviously prefer Ubuntu.  But lets be realistic, here.  If your XP box is crashing twice a day, then it's administrator (i.e., user) error.  I've been running an XP box pretty much nonstop for a year now (media server / gaming machine), and it's still storming along.

---

### Post by htinn on 2006-04-09
I'm not kidding. This box which hasn't crashed in weeks on Dapper crashed AT LEAST twice a day on Winblows XP. And it wasn't due to any error of mine.

EDIT: Well, now that I think about it, it probably was my fault. I was experimenting with a lot of different video encoders then. :P

---

### Post by Anthem on 2006-04-09
[QUOTE=htinn]EDIT: Well, now that I think about it, it probably was my fault. I was experimenting with a lot of different video encoders then. :P[/QUOTE]
Not that I'd ever try to convince you to go back (once you've kicked the habit, stay clean!), but I'm willing to be that if you gave it a clean install and took care of it, you'd be ok.

I don't recommend it, though.  Setting up a fresh Windows install is a pain, especially after you've installed Linux a time or two.  MS has a long way to go before their product is ready for the desktop ;)

---

### Post by diablozx9 on 2006-04-17
LOL Anthem,,,
Long way to go before MS ready for the desktop....

I AM using Dapper as my primary desktop and LOVE it.
I liked Breezy but, Dapper is already much better (Well, I was
using 64 bit Breezy, now using 32bit Dapper).

AND, despite using Anti Virus, Anti Spyware (2 types), Registry checkers, etc, etc, etc,
XP (ie MS crap) always ended up getting hosed.

---

### Post by RRS on 2006-04-17
Have Dapper and a broken xp on this machine, second (spare) machine has Breezy and woking xp. 

Haven't turned on the other box in a couple weeks now and most of the bugs I've found in Dapper have been self induced.

Guess I'm trying to say that even for a newbie, Dapper's good enough for only desktop, not just primary.

Can't wait till it's officially "ready" :)

---

### Post by mattisking on 2006-04-17
Dapper is now PLENTY close enough to use for more than 99% of users considering it's past the original deadline and now working on polish. Does this thread really need to live anymore?



..... of course the irony is that I just helped keep it going. Sigh.

---

### Post by livingtarget on 2006-04-17
[QUOTE=Anthem]I obviously prefer Ubuntu.  But lets be realistic, here.  If your XP box is crashing twice a day, then it's administrator (i.e., user) error.  I've been running an XP box pretty much nonstop for a year now (media server / gaming machine), and it's still storming along.[/QUOTE]

Not to defend him, but i can tell you windows does crash a lot for me. Whereas linux does not, sure if you run pretty safe stuff on it like servers *yawn* it should not be that much of a difference. But take games. I've got UT2004, I can run it on windows and on linux. Windows will hang (= machine locks up you have to press reboot switch) at least twice a day when playing more often, linux is a lot more stable in this regard. I've seen such a difference, it crashes-to-desktop only rarely (= once a week) in linux. That problem occurs on same hardware at least a couple of up to date drivers 2 windows reinstalls and a generally cleanly managed machine (on winXP that is). Imagine having to reboot twice in the middle of an online game with your friends, that is tough.

So there is a point, you are right that you shouldn't just bash Windows because people mismanage their machines. However there's more issues at work then just not-setting-up your PC ok. :KS

Anyhow more on topic, I've been digging dapper since the beginning. I love it to be honest and it's looking nicely.

---

### Post by udanton67 on 2006-04-18
Hi!

As a former FC4 user, now Ubuntu user, I'm used to ultra latest packages, Ubuntu Dapper is pretty stable. I use it for daily purposes, and hava had no trouble, so far. 

That doesn't mean I recommend it for newbies, although the Gnome 2.14 plus kernel with PREEMPT is worth it...

my 2¢.

---

### Post by maxx_730 on 2006-04-18
Well my dad, sister and mother have been using it exclusively for several weeks now. So i guess it is possible to use dapper as a primary desktop os.

---

### Post by leeley on 2006-04-21
I Dapper as my main desktop as it is the only one that I have found that works with my system and my dsl. Been using it now four 6-7 weeks and never had so much as a tick. Love it. Never going back to windows or anyother disto.[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by imacQ on 2006-04-22
i want to try the new dapper "stuff"  esp. what i hear/read are new energy saving settings allowing for mac sleep. 

in synaptic package manager what address do i put to include dapper updates/upgrade? :-k 

i'm running breezy on an imac g3 600, are updates/upgrades address different for mac then for windows machine? 

BELOW IS DIALOGE BOX FROM SYNAPTIC
"Enter the complete APT line of the repository that you want to add

The APT line contains the type, location and content of a repository, for example "deb [http://ftp.debian.org](http://ftp.debian.org) sarge main"."

---

### Post by ubuntu_demon on 2006-04-22
With the release of the Dapper Beta more people are encouraged to try Dapper. Although Dapper still shouldn't be used for really important data and stuff.

---

### Post by dusanyu on 2006-04-22
I have been useing Dapper on my Desktop for about a month its broken a fewe times (not always the fault of devlopment goo thing for backups :) ) but it has been rock solid and beutafull thus so far 

My laptop i am useing the tryed and true Breezy but everything Works on my lappy as they say if it is not broke ....

---

### Post by ryan on 2006-04-22
I have been using Dapper on my main desktop at work for around 3 weeks. I upgraded from Breezy. There have been a few quirky issues mostly with Evolution when I connected to an Exchange Server with the Exchange settings, when I switched to IMAP it helped a great deal and then Beagle started to index my mail as before it didn't.

I am on a Windows domain with a number of XP boxes and some Ubuntu desktops. We run an Exchange server which I connect to via IMAP in Evolution and T'bird. The Open office suite is what I use for compostion and editing of .rft and .doc files daily. I use calc non stop every day for my work. All in all I am very happy with Ubuntu and feel it is very solid and dependable. I used Fedora for 2 1/2  years before switching to Breezy 6 months ago.

As far as my experience and expertise I would say that I was an above average XP user before switching to Linux and I know enough about linux to stay out of trouble. I generally don't use an bleeding edge stuff and I would say that I have a fairly "conservative" installation as I can't afford to have things not work as I don't have the time to mess around  too much. I think that Linux in general and Ubuntu in particular is very well suited for the business desktop as far as stability and general working environment. I prefer the gnome desktop to KDE as I personally feel it is simpler and less cluttered which is  a help to me. I have used Suse and Xandros in the past as well. I have been very impressed with the improvements I have seen in Ubuntu over the last 6 months and feel that new features and polish in Dapper are exceptional and make it a real quality product. The community involvement is a plus as well and I usually can find the answers to my questions on the forums or other Ubuntu sites in Ubuntu wiki and Breezy Crust have been especially helpful.

Keep up the good work !

---

### Post by detyabozhye on 2006-04-22
I upgraded on thursday and I'm using Dapper as my main OS now. :p I know I'm taking a risk and I take all responsibility if anything goes wrong, but I like Dapper and I don't want to wait til June. :p:p

---

### Post by ardchoille on 2006-04-23
I have been using Ubuntu Dapper Drake flight 6 as my primary desktop OS for 13 days and I have yet to see any problems at all. It's fast, stable and hasn't pissed me off :)

If this is a beta release, then I can't wait to get my hands on the final release!

---

### Post by detyabozhye on 2006-04-23
well, the worse thing that ever happened to me on Dapper was printing with samba was broken, I fixed it with the hack in my sig.

---

### Post by ardchoille on 2006-04-23
[QUOTE=anil_robo]Ubuntu should have a "UNIVERSAL INSTALL CD" which would be internet based. The CD would boot up as a live cd, connect to the internet to find all the available releases of ubuntu, and then give the user an option to install the most updated version from the internet.

The same CD could be utilized to install any release of Ubuntu, because it's totally internet based!!

Anyone supports this idea? Or has it already been done by someone??[/QUOTE]
This is an **awesome** idea. Each time I install Ubuntu, I have to install a ton of updates. Doing a "net install" would save a lot of time because the installer would grab the newest packages from the repos rather than from the CD - the CD could be months old. I never upgrade from one version to the next (ex. Breezy to Dapper), I always do a fresh install.

I believe this would also take a huge load off of the Ship It costs.

Seriously, someone should look into this.. I'd be willing to help if I possibly could.

---

### Post by aysiu on 2006-04-23
Isn't that essentially the same as doing a server install and then adding the appropriate desktop metapackage from there...?

---

### Post by detyabozhye on 2006-04-23
OK, CUPS 1.2 RC2 is completely borked. So..... maybe I should have taken ur advice. XD
Edit: Never mind, it was the !@#$$% postscript driver :D

---

### Post by daverab on 2006-05-06
I swapped earlier in the week to Beta 1 (probably Mondayish) and haven't looked that much back. The only thing I really had to do was change over my storage drive from NTFS to EXT2 (thank you windows ext2 driver). Since then I've been in Ubuntu and using vmware when I "need" to use a program through windows (website checker because the firefox extension one sorta sucks at this point).

There have been little bumps like enabling dual monitors and getting mp3s and other media to work, but the wiki's and help guides got me through it.

Hell, I was able to get XGL+compiz working on the first day (not using regularly since it's still alpha and whatnot).

I even did stupid things. Installing both the expose like task switchers (skippy totally killed x) and I was able to recover. I also installed xubuntu, kubuntu and edubuntu and then swapped things around till Ubuntu was back to its normal splash screens and theme-ing.

The only thing I've been able to do is get update-manager to kill x. That was my own doing and I'm trying to find a solution, for now I'm still using synaptic to get around that little pest.

I really like what's been done with Ubuntu. I toyed a little with the live-cd of Breezy Badger, and took a leap with this. I can't wait to see when XGL+Compiz gets formally and defaultly thrown in.

At this point I personally think June 1 will be a little blip on the radar screen, Dapper Drake is 99.9% there.

---

### Post by ubuntu_demon on 2006-05-10
I'm using Dapper as my primary OS at my own risk, I'm an experienced Ubuntu user and I have Breezy installed on another partition to fall back on if needed. 

I'm looking forward to June 1 :)

---

### Post by Sq322 on 2006-05-16
I am so tempted to install from the live CD and just go for it..
I am having far too much fun with Dapper to outweigh the extra 2 weeks until the FINAL is released !

---

### Post by BitTorrentBuddha on 2006-05-19
With the release of flight 8 I find that it's more than ample to be used as a primary desktop OS.

---

### Post by detyabozhye on 2006-05-20
I upgraded the day or the day after beta 1 came out.

---

### Post by phillywize on 2006-05-23
Man, I just came over from Fedora, which, I have to say, is a formidable distro, and nothing to sneeze at.  But I was looking for a change, grabbed Breezy, and loved it.  Then in an act of complete derring-do, I moved to Dapper, and have loved it even more.  Ubuntu really is the open source answer, I think.  Without a lot of brushing up, this is a system that normal people can use.  I am truly amazed.  FC was great, but it's not for the faint of heart.  My mom could roll with Ubuntu though...

Anyhow, I think the Dapper betas I've been trying are great.  There have been a few problems here and there, but nothing major.

---

### Post by woopud on 2006-05-23
I've been using Dapper as my primary OS for 'bout three months now, my only problem is printing photo's wich has me boot back to XP.  I have a Canon i560s Printer.

Bert

---

### Post by detyabozhye on 2006-05-24
I've been using it as my primary OS since beta 1

---

### Post by BobSongs on 2006-05-26
I don't have a Dapper Drake CD, but I've got a fast Internet connection. Anyone have a suggest about what I'm thinking of doing?

Install Breezy but just the basic Network install
Change the references in /etc/apt/sources.list from 'breezy' to 'dapper'
Do a 'sudo apt-get update' then a 'sudo apt-get dist-upgrade'
Finish off with 'sudo apt-get install ubuntu-desktop'

I figure there would be less to 'upgrade'. Would this be second best to a Dapper CD install?

---

### Post by aysiu on 2006-05-26
It's not that there would be less to upgrade, but you would be less likely to run into dist-upgrade problems than from a full Breezy install.

I've actually done several times on my test box what you're proposing, and it works perfectly with a broadband connection.

---

### Post by BobSongs on 2006-05-26
[QUOTE=aysiu]It's not that there would be less to upgrade, but you would be less likely to run into dist-upgrade problems than from a full Breezy install.

I've actually done several times on my test box what you're proposing, and it works perfectly with a broadband connection.[/QUOTE]Thanks, dude. Okay. I'm going to give it a whirl. My current Breezy/Gnome setup failed when I did dist-upgrade. X won't start. But I'm not nervous about rebuilding the O/S.

Here goes. . .

---

### Post by czambran on 2006-05-26
[QUOTE=BobSongs]Thanks, dude. Okay. I'm going to give it a whirl. My current Breezy/Gnome setup failed when I did dist-upgrade. X won't start. But I'm not nervous about rebuilding the O/S.

Here goes. . .[/QUOTE]

Why not use gksudo update-manager -d after you have installed breezy, eventhough I fail to see why wouldn't u just download a dapper cd

---

### Post by bruce89 on 2006-05-26
Too late now but you should have used
```
gksu "update-manager -d"
```
It does the whole upgrade process automatically.

---

### Post by aamukahvi on 2006-05-26
[QUOTE=bruce89]Too late now but you should have used
```
gksu "update-manager -d"
```
It does the whole upgrade process automatically.[/QUOTE]
Does that mean you won't have to answer any questions about which files to update etc? I did the deed back when automatic wasn't an option.

---

### Post by bruce89 on 2006-05-26
[QUOTE=aamukahvi]Does that mean you won't have to answer any questions about which files to update etc? I did the deed back when automatic wasn't an option.[/QUOTE]
I don't know, when I tried this (a long time ago, about flight 3), I had to answer questions.  I think this is no longer the case.

---

### Post by AnnevO on 2006-05-31
[QUOTE=bruce89]Too late now but you should have used
```
gksu "update-manager -d"
```
It does the whole upgrade process automatically.[/QUOTE]

I did that just now, after trying it on my laptop first. :KS  It worked perfectly fine after I removed my manual firefox upgrade.

---

### Post by rcarring on 2006-05-31
In my experience it takes about the same time to download the iso image, burn it and install it as it does to perform a dist-upgrade. The advantage of a clean install is you don't need to install Breezy first.

---

### Post by ubuntu_demon on 2006-05-31
Now that the release candidate of Dapper is released and Dapper is almost released I **encourage** all users who have some experience with Ubuntu to try Dapper. Although you should make a backup of your personal files. Here's more information : [https://wiki.ubuntu.com/DapperRC](https://wiki.ubuntu.com/DapperRC)

---

### Post by fut21 on 2006-05-31
I think we have dapper right now, in the last 10 hours i havent got any updates to my dapperRC version.

---

### Post by ubuntu_demon on 2006-05-31
[QUOTE=fut21]I think we have dapper right now, in the last 10 hours i havent got any updates to my dapperRC version.[/QUOTE]
I don't think there will be much upgrades anymore. But you'll never know ofcourse :).

---

### Post by rcarring on 2006-05-31
Please dont tweak OOo. I think I have updated it 12 times in the last three weeks judging by the build numbers at the end (beta 2 said ubuntu1, latest is ubuntu12). =D

---

### Post by trakeen on 2006-05-31
[QUOTE=ubuntu_demon]I don't think there will be much upgrades anymore. But you'll never know ofcourse :).[/QUOTE]


great, I was hoping they'd fix samba before the official release (which got broken in the last upgrade, at least for me and several other people)

---

### Post by ubuntu_demon on 2006-05-31
[QUOTE=trakeen]great, I was hoping they'd fix samba before the official release (which got broken in the last upgrade, at least for me and several other people)[/QUOTE]

Let's hope it will get fixed.

---

### Post by ubuntu_demon on 2006-05-31
I will close this thread as it has served it's purpose.

---

