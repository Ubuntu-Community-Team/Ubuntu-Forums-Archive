---
title: "Tired of fighting Linux/Ubuntu. Uninstall help?"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by ZenWarrior on 2009-04-11
I'm very frustrated and completely exhausted from fighting Linux and Ubuntu. Might someone please tell me how to uninstall it and fully return my system to Vista? Vista may indeed suck, but at least it allows me to get work done. (Sorry, Linux/Ubuntu. I gave you a trial of almost a full year but you're just not ready for the desktop.)

---

### Post by sgosnell on 2009-04-11
You should be able to just boot from the Vista DVD or CD and run the install program.

---

### Post by ZenWarrior on 2009-04-11
Thank you for responding,but it will be a tremendous hassle to wipe my Vista installation clean and start from scratch. Is there a way to uninstall without it costing me everything presently Windows? Again, thank you.

---

### Post by coffeecat on 2009-04-11
No, of course you don't have to reinstall Vista. It's a simple 2-stage process.

1 Delete the Ubuntu partitions and reuse them.

2 Repair the MBR

[Here's a useful link to tell you how to "uninstall" Ubuntu and repair the mbr]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

As far as deleting the Ubuntu partitions, you could boot up with an Ubuntu live CD and use System > Administration > Partition Editor. Delete and create new partitions. Or just delete and use the Vista resizing tool to enlarge your Vista partition into the space previously used by Ubuntu. Or, no doubt, you could delete the Linux partitions from within Vista.

Just be aware that as soon as you delete the Ubuntu root partition, you'll no longer be able to boot into Vista until you have repaired the mbr.

Or you could repair the mbr to make sure you can boot into Vista, and then use the Ubuntu live CD to do your partition work. So long as you don't start the installer (which I'm sure you won't :wink:), the live CD won't affect the mbr.

Good luck.

---

### Post by sgosnell on 2009-04-11
I obviously misunderstood your situation.  I didn't think you had Vista still installed.  You should be able to boot Vista and just delete the Ubuntu partitions and grow the Vista partition back, as coffeecat said.

---

### Post by ZenWarrior on 2009-04-11
Thank you for the informative and kind reply. I truly wish I found Ubuntu easier to use. I despise paying the Microsoft tax. However, simply installing a new application in Ubuntu can be a major nightmare. That's what happened today. What would have taken 2 minutes in Windows seemed impossible with Ubuntu, or at least it was for me--even after reading documentation for an hour.

I continue to get the feeling that Linux users, although at the same time saying Linux will soon take over the world, much prefer being recognized as some sort of exclusive club where certain initiation rights are required for admission. Or, maybe it's just that geeks truly have no idea how to make something easy--and I do mean easy, not brainless. 

I'll give Linux another look in another couple of years. Maybe one day only an intelligent person will be able to use it, not someone willing to waste hours and hours to accomplish tasks which in the two other predominant operating systems have been made easy enough even for most grandmothers.

Again, thank you.

---

### Post by coffeecat on 2009-04-11
> **ZenWarrior said:**
>  simply installing a new application in Ubuntu can be a major nightmare. That's what happened today. What would have taken 2 minutes in Windows seemed impossible with Ubuntu, or at least it was for me--even after reading documentation for an hour.

If you're still around, can you say what the software was? Was it something really obscure? You see, my experience is quite the opposite of yours. 95% of what I want is in the Ubuntu repos and installing just involves a couple of mouse clicks. Truly much nicer than Windows. Then, for the next 4% I find a deb file on the application website, download it to the desktop, double click on it, and gdebi automatically installs it for me. Again, usually smoother than my Windows experience. That leaves just 1% where, I agree, trying to install can be a nightmare.

I am not trying to proselytise. You must use the platform you are comfortable with. But it depresses me seeing some of the threads on this forum (and other Linux forums) where a new user asks a question, the answer to which involves a couple of mouse clicks and some spotty urchin posts a reply along the line of: 'open a terminal and...

```
incomprehensible gobbledegook
```:cry:

:wink:

---

### Post by iheartubuntu on 2009-04-11
I agree in a way with both of you. Ive been using Ubuntu for what, almost 3 years now. I now use ONLY Ubuntu. But, learning linux was difficult at first becuase i LOVE to tinker around. I screwed things up a few times, but I kept at it and thankfully I didnt jut give up and run away. Are Ubuntu and linux users in an exclusive club? I dont think so. Maybe so for people who like to tinker... can you fix something if you go to root and mess it up? It DOES take some patience if you go root, screw something up, and expect an easy fix. Ubuntu does make this process easier if you screw things up... we have a great forum here to get info. Go on ebay and buy some $50 cheapo computer with a P3 in it, put TinyME on it as a backup if you must to rescue your main unit. But really, did you ever go root in XP or Vista? Probably not.

Im a html coder, web designer, graphics artist (and probably not a great one after seeing so much great stuff around the world!) so it was a bit of a brain ache making the full switch. Could I still do Photoshop? Yep. Dreamweaver? Yep. I was able to make the switch. For Windows programs, get WINE on your Ubuntu system. For some select few programs use WINE DOORS to install windows programs. But after a while, I wanted to learn more about open source programs similar to the windows programs Ive been using for years. GIMP and INKSCAPE in the repositories more than make up for Photoshop.... you just need to know how to use them (there are some great howto blogs that update regularly). Thats been my personal situation. But most all programs you need you can find in the add/remove and search around.

getdeb.net is a great site for finding software. Browse around the net for ubuntu and linux blogs. If youre looking for something specific, ask right here in the forums. People can guide you to something exactly to fit you bill many times.

Id say dont give up yet. It sounds like you have a dual boot setup? Keep Ubuntu even if you go back to Vista.

Can we all ask you what specifically are you mad at, giving up on, and ready to call it quits? Whats pissing you off about Ubuntu compared to XP/Vista? Maybe in a few months when Vista slows down for you, boot up times become unbearable and the latest greatest virus infects you you might rethink checking Ubuntu again.

I love the fact if I need a program, I can find it for free here in the forums or in the reps. There is a few programs like "TwitterFriendAdder" I use, it doesnt work through Wine, so I use XP within Virtual Box to run that software. No big deal. And i dont use that software often so its all good.

Hey, my dad is 75 years old. He has Ubuntu Jaunty (just upgraded all) on his laptop at work, his Acer 10.1" netbook when he travels, and his home desktop. He has everything he needs. Access to the internet/email, word processing, free games, watching movies, etc.

If you are giving up on Ubuntu it sounds like you have some very specific programs? Otherwise how can you go wrong with free and safe?

---

### Post by Galban on 2009-04-11
You konw Coffeecat, I do really understand and emphasize with ZenWarrior feelings. It is undeniable that unfortunately Linux still not to be that "average user friendly" and just this, is somehow frustrating. Myself, after years using Linux, still facing troubles at every Ubuntu upgrade version to make some piece hardware/software work as it is supposed and intended to do.

I think that if I keep trying is because I like break my head finding the way to put together this kind of "Linux puzzle".
And somehow to the fact that I'm convinced for ethics and principles reasons that Linux is the future.

Coffeecat you said, 90 and some % ends to be just question of couple mouse clicks to get it fixed. So then watch my thread and tell me if it is the case for my RAID O dual boot install problem. I wish you are right!

---

### Post by ZenWarrior on 2009-04-11
Maybe it is, but I don't consider Second Life obscure at all. Upon trying to run it, I kept getting an error about window creation. The documentation stated that meant I have out of date Nvidia drivers, which I do not. They are the most recent release. Also, I've received that same error now across three updates of the Nvidia drivers. 

Still, I then continued to follow instructions regarding a fix and never got anywhere. To install Second Life on Windows is brainless, but was a nightmare which would not end when attempted with Ubuntu. I couldn't even "run" the file as specified in the instructions and I think I'm better than most at both first reading documentation/instructions and following it. But over an hour later, I'd accomplished nothing but pulling my hair out.

I've had  the same problem with other software which is not at all "obscure" to Windows, but seems totally out of the ballpark with Ubuntu. And for what it's worth, I'm hardly a newbie. Granted, I've not kept my skills honed, but I grew up with mainframes, VAX, and other arcane operating systems. I taught myself SAS even, from only their voluminous manuals. I began with IBM punchcards back in 1975.

I was reading and downloading graphics files from Usenet when there were only 1000 newsgroups and it took 3-4 separate applications just to view a graphics file. So although I no longer "tinker," I'm hardly afraid of doing it--and even thought it would be fun to do so with Unbuntu/Linux. However, it's only been an exercise in frustration 90% of the time.

One thing I feel is sorely missing--documentation in "english." If there is a simple dictionary of terms like grep and what it's supposed to do, I've not found it. Most everything Linux seems to be defined only in context. That is, if you read enough you eventually get an idea of what it means. But after reading and reading, many Linux terms still mean nothing to me and a simple dictionary with examples would have made all the difference.

However, I think I realize that is where capitalism comes in vs. open source. Open source means *maybe* someone decided to be nice and take time to do certain things. With capitalism, you have no choice if you plan on taking any money to the bank. Maybe being free is both the blessing and curse of Ubuntu and Linux. No one has the financial motivation to do things certain given ways which provide little other reward than boosting self-esteem. 

YMMV. The above is merely my opinion and assessment of what I've seen. 

(BTW, this is not unique to Ubuntu. I also installed PCLinuxOS on another computer and life there is no different--maybe worse. It's back to Windows, with the greatest of regrets.)

---

### Post by ZenWarrior on 2009-04-11
> **coffeecat said:**
> But it depresses me seeing some of the threads on this forum (and other Linux forums) where a new user asks a question, the answer to which involves a couple of mouse clicks and some spotty urchin posts ***a reply along the line of: 'open a terminal and...***

Precisely!!! That's why fairly easily comprehended documentation in *English* is required. I'm not asking this be made brainless, just possible without dealing with such responses--and even coming  to expect them. Thank you for being so observant.

---

### Post by iheartubuntu on 2009-04-11
So your frustrations are trying to run Windows software on a Linux system.

Heck, I installed this a year ago without a problem. I dont play it, but it installed and played fine. I too have nVidia card here and it works fine.

Here is where I went to download it and it worked fine (a deb file):

[http://www.getdeb.net/search.php?search_distro_id=9&keywords=second%20life](http://www.getdeb.net/search.php?search_distro_id=9&keywords=second%20life)

---

### Post by ZenWarrior on 2009-04-11
> **shirteesdotnet said:**
> So your frustrations are trying to run Windows software on a Linux system.

I'm not certain by what you mean in saying "trying to run Windows software on a Linux system," but there is a Linux version of Second Life at the official web site. That is what I've attempted to install and run for over six months now with zero success. It's found at:

[http://download.cloud.secondlife.com/SecondLife-i686-1.22.11.113941.tar.bz2]("http://download.cloud.secondlife.com/SecondLife-i686-1.22.11.113941.tar.bz2")

Thank you for the other link. I'll give it a try. (And what the hell is a "windows creation error?" The documentation concerning the error message, which I've read and reread, gets me nowhere.)

---

### Post by ZenWarrior on 2009-04-11
Clearly I am clueless. The provided link gives me an error message about wrong architecture. I give up.

---

### Post by iheartubuntu on 2009-04-11
Have you searched your problem? How about this...

[http://kubuntuforums.net/forums/index.php?topic=3102752](http://kubuntuforums.net/forums/index.php?topic=3102752)

To fix the prob it says...
> 
You have a hidden file under your home account called ".secondlife".

Rename it to ".secondlife_old".

Start your Sl client. 

Your name AND password will have to be re-entered.

---

### Post by iheartubuntu on 2009-04-11
Also, you may need to be running 24 bit mode for your graphics card. Some people getting the same error message you are if they have lower graphics settings. Check your NVIDIA X server settings just in case.

---

### Post by iheartubuntu on 2009-04-11
> **ZenWarrior said:**
> Clearly I am clueless. The provided link gives me an error message about wrong architecture. I give up.


??? Is your system 64 bit or 32 bit? Im 32 bit and its all good.

---

### Post by iheartubuntu on 2009-04-11
> **shirteesdotnet said:**
> So your frustrations are trying to run Windows software on a Linux system.

Heck, I installed this a year ago without a problem. I dont play it, but it installed and played fine. I too have nVidia card here and it works fine.

Here is where I went to download it and it worked fine (a deb file):

[http://www.getdeb.net/search.php?search_distro_id=9&keywords=second%20life](http://www.getdeb.net/search.php?search_distro_id=9&keywords=second%20life)

At the bottom of the getdeb page for Second Life there is a 64 bit version too. Here is the direct link...

[http://www.getdeb.net/search.php?search_distro_id=10&keywords=second%20life](http://www.getdeb.net/search.php?search_distro_id=10&keywords=second%20life)

Maybe that will help?

---

### Post by juancarlospaco on 2009-04-11
I have Portable Hippo if you want send me a PM, just like Portable Apps on Windows, 
ah...  Hippo is a GPL clone *(without trademarks)* of SL client.

---

### Post by jmore9 on 2009-04-11
I went over to the ' cloud second life ' web page ( i haven't a clue what cloud second life is ), and at the bottom of the page is the system requirements and linux is listed as a supported platform.

It said that any recent distro is compatible with the software.  It does seem to me that is has a high graphic requirement with only a few video cards being loisted as tested.

If you could tell me what is is what it does i might be able to help but i haven't been able to figure out what it is, as yet.

And the download for the software is in tarball form so you have to 1. make your own deb from scratch,  or 2. just install by using the tar ball.

If you need help with installing via tarball then just go to the search here on the board and type tarball or the .tar or what ever is after the dot at the end .  Also use google google is your buddy with all distros not just linux.

If you explain what you are trying to do maybe i can help, maybe not , but i can try.  About the only item i found that will not run on todays versions of linux digital tv tuner cards and the like and windows software that deals with hardware.

---

### Post by Mark Phelps on 2009-04-11
Everyone's experiences are going to be different, but I can certainly sympathize with the OP's feelings. While it's true that the Linux distros have come a long way from the early days, in terms of ease of installation and ease of use, the sorry fact remains that the available universe of MS-Windows compatible hardware and drivers still exceeds that of the Linux world.

As a case in point, I have an older HP laptop that I tried for over six months to get fully working using several different Linux-based distros. In every case, some piece of hardware would NOT work.  In every case, I went to the appropriate Linux forum, posted the details, got some help ( and that's the GOOD NEWS about Linux -- people ARE willing to help), tried the various solutions -- and always, without success.

After all this trial-and-error, gave up and reloaded XP Pro on it.  Not surprisingly, ALL the hardware works, without any problems of any kind.

But before everyone attacks me as an MS-fan, let me assure you, I am NOT.  I use Ubuntu every day to do 95% of my computing -- and that's not by installing Wine or Crossover and running MS Windows apps; that's by finding Linux equivalents and learning how to use them.

However, the sorry truth is that folks like us are in the minority.  Most people out there buy PCs to get something done.  They don't know how the PCs work, and they don't want to learn. You can see the latter with all the folks coming here wanting to know how to run their <favorite-app>.exe file in Ubuntu.

They don't want to learn anything; they just want to run the apps they know.  So, really, they should stay with what makes them comfortable -- MS Windows.

Tragically, I have personally observed a much higher rate of early "failures" in the more recent Ubuntu distros.  Remember that laptop I mentioned? The newer the distro I loaded, the greater the failures.  I also have a tablet PC that works fine under 8.04 and fails miserably under anything more recent.

Just look at all the posts here from people that install 8.10, or upgrade to 8.10, and they get no video.  Yeah, in many cases, WE know how to fix that.  But, they're not interested in doing repairs, they just want their machine to work. And, as the OP indicated, they're not interested in opening a terminal and typing commands.

As for me, I came to Linux largely due to my disappointment with Vista and looking for an alternative.  I was very impressed with Ubuntu specifically, and with the Linux community in general.

But my own expriences with 8.10 and 9.04 on my tablet PC (generating problems no one has been able to tell me how to fix) have been disturbing.  And, not everyone is willing to spend weeks or months "fixing" their machine to get something simple like video or keyboard functions to work.

If the greater Ubuntu community is OK with it being largely hobbyists, then the community has no worries.  But I'll give you a personal example of what Canonical needs to do if the community wants to see major growth.  My tablet PC will not handle special keys (on the bezel) with any distro newer than Hardy.  AFAIK, this is because Canonical decided to change the way that such keys are handled.  OK, understand that.  But what they did NOT do was any of the following: (1) provide an alternate way that was compatible with the Hardy approach, or (2) provide a utility for converting the configuration files used in the Hardy approach with the files needed by Intrepid or newer, or (3) given that (2) might not be possible, provide a tutorial that walks us through manually converting the old way to the new way.  In other words, they left us to figure this out on our own.  And, given the lack of successful technical advice to do that on this forum, (3) must be a really hard thing to do.

I don't know the "rules" by which Ubuntu upgrades are done, but one "rule" which should be in place is that no distro upgrade should "break" anything that's in place with a previous version. If a new way of doing something is the default, it should provide a means of converting the old to the new. In the case of my tablet PC, that was clearly NOT followed. The tablet-specific entries in the xorg.conf file were commented out and no substitute was created in the fdi file(s), and xev simply quit working.  After weeks of postings and hundred of google searches, I had no choice to give up and go back to Hardy.

Like the OP said, people need machines that just work -- and if decisions by Canonical produce distros that don't work, people are not likely to hang around.

Sorry for the long rant.

---

### Post by iheartubuntu on 2009-04-11
No, rightly so... we have all had our share of problems. I recently donated 5 older PCs sitting around my work. I tried several distros on them (beginning with Ubuntu) and they had a prob finding a particular hardware. Whether it was a sound card, a hard drive, a wifi card, an old video card... whatever. I ended up putting Ubuntu 8.04 on all of them though. My biggest problem with linux was finding the modems, so I took out all the modems and put ethernet cards in them. I had plenty of old video cards laying around and sound cards too so with enough trial and error I finally found a combo that worked. The computers worked decent and happy that they all have been put to use already. The only final problem I had was two computers didnt have sound. Oh well :)

As with your tablet PC... Im in a similar situation that hasnt yet been fixed. On my computer here at work, I have kpilot installed since 7.04. Every time I have upgraded and this system now runs Jaunty 9.04 beta. Works great! But.... on computers newer than 8.04 (i think) Ubuntu dropped kpilot. On my two computers at home I have fresh installs of 8.10, upgraded to 9.04 and installing kpilot is not an option. Anytime I want to backup my Palm Tungsten C, I need to do it from this computer. I realize palms are now outdated for the most part and have turned into Treos and Blackberries and netbooks, but why junk my Palm when it works fine?? (damn! if only I could get Ubuntu Remix working on it!) It has wi-fi, I can check email, chat if I need, browse the web with Opera, check my itineraries (i mostly use it if I go on a trip)... I even have Google Maps on it.

---

### Post by ZenWarrior on 2009-09-27
Me again.  Thanks for the replies.  Honestly, I gave up on Ubuntu and never followed-up to resolve my original problem.  Instead, I began using Ubuntu as a not-so-pleasant diversion at times--but with hopes of eventually understanding it all. However, I now have a problem which prevents it from even being a diversion.

My volume control has gone missing.  There is a red X to the right of the volume control applet and I get a message about "No volume control GStreamer plugins and/or devices found."  I don't even get that god-awful jungle drumbeat at start-up.  (Who chose that, btw?  Ouch!)

At this point, I will indeed stop and follow-up just long enough to learn how to *uninstall* Ubuntu and never look at it again.  In the responses above, I am told to remove the partitions and fix my MBR, but I am not at all certain how to do the latter. I read thru the links but once again it appeared somehow by magic I was simply supposed to know some things. (Maybe I'm not a good reader.)

As much as I hate it doing it, I now just want to restore my system to Windows in its entirety.  I keep thinking I'll one day "get" Ubuntu, but clearly not.  I do not mean to offend anyone or the community, but Ubuntu just isn't ready for prime time when arcane language and instructions continue to be used for, what with Microsoft, are indeed very simple tasks.  Even the problems I encountered with Vista were a piece of cake to resolve compared to almost any problem I encounter with Ubuntu.  

So again, I would appreciate **very specific instructions !in English!** about how to restore all aspects of my PC to a Windows world I'd hoped to leave behind long ago.  And again, no offense intended to all those who love Ubuntu/Linux and think it's the greatest thing since sliced bread.  After all, maybe it is and I just like my bread in whole loaves.

---

### Post by presence1960 on 2009-09-27
> **ZenWarrior said:**
> 

I continue to get the feeling that Linux users, although at the same time saying Linux will soon take over the world,

Again, thank you.

It is only the zealots who make claims like that. I personally do not care if another person decides to use Linux. If someone does decide to use Linux and needs help I will gladly try to help. 

But it is your choice which OS you use. There is no shame in using Windows. 
Linux is not for everyone. Windows is not for everyone. Mac is not for everyone. There are other OSs out there too. So you see the choice is yours which OS you will use. make your choice without lamenting about the other OSs. It falls on deaf ears anyway, especially since you have so many options.

---

### Post by presence1960 on 2009-09-27
> **Mark Phelps said:**
> Everyone's experiences are going to be different, but I can certainly sympathize with the OP's feelings. While it's true that the Linux distros have come a long way from the early days, in terms of ease of installation and ease of use, the sorry fact remains that the available universe of MS-Windows compatible hardware and drivers still exceeds that of the Linux world.

As a case in point, I have an older HP laptop that I tried for over six months to get fully working using several different Linux-based distros. In every case, some piece of hardware would NOT work.  In every case, I went to the appropriate Linux forum, posted the details, got some help ( and that's the GOOD NEWS about Linux -- people ARE willing to help), tried the various solutions -- and always, without success.

After all this trial-and-error, gave up and reloaded XP Pro on it.  Not surprisingly, ALL the hardware works, without any problems of any kind.

But before everyone attacks me as an MS-fan, let me assure you, I am NOT.  I use Ubuntu every day to do 95% of my computing -- and that's not by installing Wine or Crossover and running MS Windows apps; that's by finding Linux equivalents and learning how to use them.

However, the sorry truth is that folks like us are in the minority.  Most people out there buy PCs to get something done.  They don't know how the PCs work, and they don't want to learn. You can see the latter with all the folks coming here wanting to know how to run their <favorite-app>.exe file in Ubuntu.

They don't want to learn anything; they just want to run the apps they know.  So, really, they should stay with what makes them comfortable -- MS Windows.

Tragically, I have personally observed a much higher rate of early "failures" in the more recent Ubuntu distros.  Remember that laptop I mentioned? The newer the distro I loaded, the greater the failures.  I also have a tablet PC that works fine under 8.04 and fails miserably under anything more recent.

Just look at all the posts here from people that install 8.10, or upgrade to 8.10, and they get no video.  Yeah, in many cases, WE know how to fix that.  But, they're not interested in doing repairs, they just want their machine to work. And, as the OP indicated, they're not interested in opening a terminal and typing commands.

As for me, I came to Linux largely due to my disappointment with Vista and looking for an alternative.  I was very impressed with Ubuntu specifically, and with the Linux community in general.

But my own expriences with 8.10 and 9.04 on my tablet PC (generating problems no one has been able to tell me how to fix) have been disturbing.  And, not everyone is willing to spend weeks or months "fixing" their machine to get something simple like video or keyboard functions to work.

If the greater Ubuntu community is OK with it being largely hobbyists, then the community has no worries.  But I'll give you a personal example of what Canonical needs to do if the community wants to see major growth.  My tablet PC will not handle special keys (on the bezel) with any distro newer than Hardy.  AFAIK, this is because Canonical decided to change the way that such keys are handled.  OK, understand that.  But what they did NOT do was any of the following: (1) provide an alternate way that was compatible with the Hardy approach, or (2) provide a utility for converting the configuration files used in the Hardy approach with the files needed by Intrepid or newer, or (3) given that (2) might not be possible, provide a tutorial that walks us through manually converting the old way to the new way.  In other words, they left us to figure this out on our own.  And, given the lack of successful technical advice to do that on this forum, (3) must be a really hard thing to do.

I don't know the "rules" by which Ubuntu upgrades are done, but one "rule" which should be in place is that no distro upgrade should "break" anything that's in place with a previous version. If a new way of doing something is the default, it should provide a means of converting the old to the new. In the case of my tablet PC, that was clearly NOT followed. The tablet-specific entries in the xorg.conf file were commented out and no substitute was created in the fdi file(s), and xev simply quit working.  After weeks of postings and hundred of google searches, I had no choice to give up and go back to Hardy.

Like the OP said, people need machines that just work -- and if decisions by Canonical produce distros that don't work, people are not likely to hang around.

Sorry for the long rant.

Well said Mark  +1

---

### Post by presence1960 on 2009-09-27
> **ZenWarrior said:**
> Me again.  Thanks for the replies.  Honestly, I gave up on Ubuntu and never followed-up to resolve my original problem.  Instead, I began using Ubuntu as a not-so-pleasant diversion at times--but with hopes of eventually understanding it all. However, I now have a problem which prevents it from even being a diversion.

My volume control has gone missing.  There is a red X to the right of the volume control applet and I get a message about "No volume control GStreamer plugins and/or devices found."  I don't even get that god-awful jungle drumbeat at start-up.  (Who chose that, btw?  Ouch!)

At this point, I will indeed stop and follow-up just long enough to learn how to *uninstall* Ubuntu and never look at it again.  In the responses above, I am told to remove the partitions and fix my MBR, but I am not at all certain how to do the latter. I read thru the links but once again it appeared somehow by magic I was simply supposed to know some things. (Maybe I'm not a good reader.)


As much as I hate it doing it, I now just want to restore my system to Windows in its entirety.  I keep thinking I'll one day "get" Ubuntu, but clearly not.  I do not mean to offend anyone or the community, but Ubuntu just isn't ready for prime time when arcane language and instructions continue to be used for, what with Microsoft, are indeed very simple tasks.  Even the problems I encountered with Vista were a piece of cake to resolve compared to almost any problem I encounter with Ubuntu.  

So again, I would appreciate **very specific instructions !in English!** about how to restore all aspects of my PC to a Windows world I'd hoped to leave behind long ago.  And again, no offense intended to all those who love Ubuntu/Linux and think it's the greatest thing since sliced bread.  After all, maybe it is and I just like my bread in whole loaves.


To restore Vista to MBR do this:

To restore the Windows Vista bootloader, you must first boot off your Windows Vista installation DVD.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

Now close the two windows and click "Restart."

You should boot directly into windows vista. Now you have 2 choices to remove the ubuntu partitions. You can use vista's disk management utility to delete the partitions and create NTFS partitions or merge the former Ubuntu space with the C: drive. Or you can boot the Ubuntu Live CD and use gparted to delete the Ubuntu partitions. You can then still in gparted create a partition(s) in NTFS for Vista to use or boot back into Vista and use it's disk management utility to merge the former ubuntu partitions free space into C:

---

### Post by nitstorm on 2009-11-11
> **coffeecat said:**
> No, of course you don't have to reinstall Vista. It's a simple 2-stage process.

1 Delete the Ubuntu partitions and reuse them.

2 Repair the MBR

[Here's a useful link to tell you how to "uninstall" Ubuntu and repair the mbr]("http://www.users.bigpond.net.au/hermanzone/p18.htm")




The link doesn't work, could u please repost a working one, that would be helpful, thnx :)

---

### Post by coffeecat on 2009-11-11
> **nitstorm said:**
> The link doesn't work, could u please repost a working one

The site seems to be defunct, which is a pity.

Anyway - this is my recommended process.

1 - Backup all important data. You are about to delete some unneeded partitions. Very rarely the partition table gets corrupted which will make **all** partitions inaccessible. So...

2 - Backup any important data.

3 - And don't forget: backup your data.

4 - Boot up with an Ubuntu live-CD, go to Gparted and delete your Ubuntu partitions. There are probably two: the root (/) one (ext3 or 4) and a swap partition.

5 - Download [Super Grub Disk]("http://www.supergrubdisk.org/"). Burn this to CD and boot up with it. In the extremely user-hostile menu are two options for Windows: one to simply boot into Windows, the other to repair the mbr and then boot into Windows. If you choose the one that repairs the mbr, the next time you reboot (without the Super Grub Disk) you'll simply boot straight into Windows. By this time Ubuntu and grub will have been deleted from your machine and you can use the Vista utility to create a partition in the now unallocated space - or expand you C: partition to use that space.

Lastly - did I say to back up all your files before you do this?

If you need more details, please start your own support thread - linking to this one if necessary. I won't be posting to this thread again - it has run its course.

---

### Post by nitstorm on 2009-11-11
Thanks :D

---

### Post by romg6696 on 2010-02-08
> **coffeecat said:**
> No, of course you don't have to reinstall Vista. It's a simple 2-stage process.

1 Delete the Ubuntu partitions and reuse them.

2 Repair the MBR

[Here's a useful link to tell you how to "uninstall" Ubuntu and repair the mbr]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

As far as deleting the Ubuntu partitions, you could boot up with an Ubuntu live CD and use System > Administration > Partition Editor. Delete and create new partitions. Or just delete and use the Vista resizing tool to enlarge your Vista partition into the space previously used by Ubuntu. Or, no doubt, you could delete the Linux partitions from within Vista.

Just be aware that as soon as you delete the Ubuntu root partition, you'll no longer be able to boot into Vista until you have repaired the mbr.

Or you could repair the mbr to make sure you can boot into Vista, and then use the Ubuntu live CD to do your partition work. So long as you don't start the installer (which I'm sure you won't :wink:), the live CD won't affect the mbr.

Good luck.

Does this work with Windows 7? i have partitioned my hard drive and i want to make sure that this method of uninstalling Ubuntu work with windows 7?

---

### Post by oldfred on 2010-02-08
Vista and 7 have the same procedures:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by viper250 on 2010-02-08
from zen's point of view I understand the frustration, going from windows to linux is not an easy task because you need to unlearn all the crap from microsoft and then face a daunting task of learning a new style of os.
Ubuntu is a good program and it has a lot of flavors to it. 
but it would be better for a windows user to migrate to xandros or pclinux os.
migrating from windows takes a lot of dedication to learning something new.
usually they are tired of the foibles of microcrap and they are a bit antsy about trying something new.
they expect the new os to be a lot similar to the old os and forget the first rule of linux(LINUX IS NOT WINDOWS) 
as a user of both linux and microsoft products I have a large knowledge base to work with
and I recommend anyone trying linux to make frequent use of the forums and its members 
we are after all here to help each other.

---

