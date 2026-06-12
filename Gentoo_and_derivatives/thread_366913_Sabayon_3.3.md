---
title: "Sabayon 3.3"
date: 2007-02-21
forum: Gentoo and derivatives
---

### Post by mips on 2007-02-21
I'm really looking forward to this release.

The one major gripe people have with sabayon is the slow boot times. This will be addresses by [eINIT]("http://wiki.jyujin.de/doku.php")  which is apparently faster than upstart. The other nice thing about eINIT is that it saves all the configs/scripts etc in one central xml file.

Then there is the rewritten Acceleration Manager using QT 4.2 although I don't really know what this will do for me as i don't currently use it.

Then there is project Entropy which they are being tight lipped about. Anyone know more about this ? (Don't say you know but can't tell!)

Besides that new artwork will see the light of day.

---

### Post by unbuntu on 2007-02-23
Do you happen to know is there a way to do a system upgrade like apt-get dist-upgrade in Ubuntu?  I currently have 3.26 installed and downloading the whole DVD release takes a bloody long time.

---

### Post by mips on 2007-02-24
I do not know but that is not to say it's not possible. 3.3 will only be out a bit later so maybe wait and see if it is possible.

---

### Post by FyreBrand on 2007-02-26
The best place to research on upgrading is really the Sabayon forums.  From what I've read there the analogous operation in Gentoo to apt-get dist-upgrade is emerge world.  I find Portage really tricky though. The recommendation from the Sabayon forum members is that emerge world can break your system easily and isn't for the faint of heart.

---

### Post by igknighted on 2007-02-27
You need the cd or dvd to upgrade (unless you want to do an emerge world... not recommended, packages will likely break).  I personally only use the mini-edition (too much junk on the DVD), so I will wait for that much more reasonable download to upgrade.  But if you run the full DVD version, I would carefully consider whether you want to upgrade the whole system, or just individual packages through portage.

---

### Post by mips on 2007-02-27
> **igknighted said:**
> But if you run the full DVD version, I would carefully consider whether you want to upgrade the whole system, or just individual packages through portage.

I also use the mini version and so far i have only upgraded individual packages.

---

### Post by rai4shu2 on 2007-02-27
Will they have xdeltas or is it going to be too big a change for that?

---

### Post by igknighted on 2007-02-28
> **mips said:**
> I also use the mini version and so far i have only upgraded individual packages.

Looking at what they want to add in 3.3, it might be worth the install... einit, the mystical entropy, etc.

---

### Post by RAV TUX on 2007-03-01
> **igknighted said:**
> the mystical entropy, etc.I actually know what entropy is about and it is simply awesome...my lips are sealed on any further detail beyond that:)

---

### Post by zaratustra on 2007-03-01
is eINIT merged already? can someone tell something about it... there is someting similar called initng in gentoo...
btw, RAV, what is entropy? I'd like to know but I haven't found any concrete info

---

### Post by FuturePilot on 2007-03-01
Any word on a release date? I hope they fixed that Firefox bug.

---

### Post by NocheBoy on 2007-03-01
hey y'all. Im running sabayon mini 3.1 and i want to upgrade to 3.26 with a dvd. i originally tried a fresh install, but it got to 90.5% file installation and stopped. im scared the same will happen if i try to upgrade. should i re-burn the image onto a different DVD?

---

### Post by .aku on 2007-03-02
> **FuturePilot said:**
> Any word on a release date? I hope they fixed that Firefox bug.

quote from Sabayon forums: 
"3.3 will not be out by the weekend and I seriously doubt it will be out by next weekend. The testers are waiting for the beta to even test it yet, so it will be a bit yet. I don't want to see a rushed 3.3."

---

### Post by RAV TUX on 2007-03-02
> **zaratustra said:**
> 
btw, RAV, what is entropy? I'd like to know but I haven't found any concrete infoI honestly should not say.

---

### Post by Rodneyck on 2007-03-02
A quick look through their forum reveals that Entropy is an alternate package manager type system they are working on and rightly so, Kuroo is horrid.

---

### Post by FyreBrand on 2007-03-02
> **Rodneyck said:**
> A quick look through their forum reveals that Entropy is an alternate package manager type system they are working on and rightly so, Kuroo is horrid.Kuroo is horrid.  I tried using it to start with and it didn't work well.

I really don't know what all the super secret hype is about this entropy.  It seems pretty silly to me to make such a super secret out of it.  Also only the "cool" people on the Sabayon forums know anything about it.  Nothing like being made to feel like a left out noob. :(

---

### Post by Rodneyck on 2007-03-02
They were also posting on the forum for anyone who knew python to work on this super secret project. If you ask me, if the people running the ship don't know how to program, it does not sound like a safe place to call home.  I would go pure Gentoo if I wanted a source-base distribution...my opinion.

---

### Post by FyreBrand on 2007-03-02
> **Rodneyck said:**
> They were also posting on the forum for anyone who knew python to work on this super secret project. If you ask me, if the people running the ship don't know how to program, it does not sound like a safe place to call home.  I would go pure Gentoo if I wanted a source-base distribution...my opinion.
Well I don't really know one way or another about that, but I like the idea of what they're doing and it seems like an easy introduction to portage.

Lots of stuff works fairly smooth and it has nice desktop effects.  I'm not really sure what they're aim is.  There is tons of stuff installed by default which is okay because I have lots of room, but I didn't understand why it was all there.  They had an AMP (apache mysql and php) stack installed but not configured.  So I didn't get why they would spend the room to install it.  Even then I don't think it was installed properly because php extensions weren't installed to talk to mysql.  So php and pear would have to be re-compiled and setup anyways I think.  I don't know portage well enough to know for sure how that works.

I'll definitely try out the 3.3 release and see what they've done with it.  I think it would be nice if they used Anaconda to it's fuller potential.  It's a pretty powerful installer and it would be nice if you could choose what desktop environments, packages, or meta-groups you wanted installed rather than have everything dumped on the hd.

---

### Post by mips on 2007-03-02
> **FyreBrand said:**
> 
I really don't know what all the super secret hype is about this entropy.  It seems pretty silly to me to make such a super secret out of it.  Also only the "cool" people on the Sabayon forums know anything about it.  Nothing like being made to feel like a left out noob. :(

From what I gather entropy might only make it into sabayon by 3.4 and not 3.3. Information is available to developers & beta-testers. This information is usually not shared with the public at large. Pretty common elsewhere including commercial companies. Geez some will even make you sign a NDA.

---

### Post by zaratustra on 2007-03-02
> **RAV TUX said:**
> I honestly should not say. Am very sorry, I only glanced your post and didn't read the part about sealed lips. Sorry once again.

> **Rodneyck said:**
> A quick look through their forum reveals that Entropy is an alternate package manager type system they are working on and rightly so, Kuroo is horrid.
Kuroo isn't pack-manager, it is only portage front-end. Are they making new frontend to portage or replacement for whole portage?

---

### Post by FyreBrand on 2007-03-02
> **mips said:**
> From what I gather entropy might only make it into sabayon by 3.4 and not 3.3. Information is available to developers & beta-testers. This information is usually not shared with the public at large. Pretty common elsewhere including commercial companies. Geez some will even make you sign a NDA.Maybe the that's the thing I find irritating about it because this isn't a closed, proprietary project.  I think that is one major reason I love open source so much.  There isn't much of the secretive surprise thing going on and more of the here's what we're doing.  The idea of taking an NDA approach to open source development isn't that appealing to me.  What purpose could it possibly serve?

I understand being careful with over committing to details or features early on in a project because you don't want to over promise.  I don't see disclosing major project goals as over committing though.

---

### Post by RAV TUX on 2007-03-03
> **FyreBrand said:**
> Maybe the that's the thing I find irritating about it because this isn't a closed, proprietary project. I think that is one major reason I love open source so much. There isn't much of the secretive surprise thing going on and more of the here's what we're doing. The idea of taking an NDA approach to open source development isn't that appealing to me. What purpose could it possibly serve?

I understand being careful with over committing to details or features early on in a project because you don't want to over promise. I don't see disclosing major project goals as over committing though.

This is more the rule then the exception in Linux.

Sabayon Linux has and also is Open Source, these guys give more to all of Linux in general by actively writing patches for the Linux kernel that all of Linux is based on. Give them time and when they are done they will give you the code so you can use it for your personal use, no need to fret.

---

### Post by FyreBrand on 2007-03-03
I don't really want the code or idea for my own project and I'm sure they will eventually open the code base.

I'm also sure they give a lot back, but that's not really what's irritating.  It's the fact they leak a "really cool" project is in the works and then it seems they make sure that everyone knows a few "important" people know what it's all about.  Do you see the kind of message that's sending?  It also doesn't excite me one bit about the distributions projects overall.  What's the point in hanging around there discussing or being a part of the project if unless you're one of the important people?

When I want to see what's happening in development release X in Ubuntu I can follow what's happening and participate to the degree I'm able.  Even if I'm not immediately privy to all the details I still feel welcomed into the project.  If I read through the KDE development news and blogs I can get an idea of what is happening and even an opportunity to contribute.  Just being able to give feedback in the comments of blogs or news posts makes users feel welcome.

Sabayon looks really nice.  I also think they've done an amazing job with 3.26.  I'm not going to go to their forums and criticize them either, but I just like communities and projects that are a little more transparent and a lot more inviting.  That is a bottom line factor why I stick with K/X/Ubuntu.

---

### Post by zaratustra on 2007-03-03
@ FyreBrand - At first glance, it really sounds like a commercial trick to get attention and differs from Open Source we got used to. But, you have to see things from other side. There is possibility that their code has promising core, but it is still full of bugs. Maybe they really worked hard on it and are afraid of bad conclusions which could be made about unfinished product making it doomed before it is even born yet. Even if it isn't like that, who says that they must open their code? This isn't comunism and nobody forces anyone to share his goods. I hope you understand what I mean. But I agree that they should not talk about something they hide so carefully. I found that irritating too.

---

### Post by igknighted on 2007-03-03
The source is available, go to their svn.

[http://www.sabayonlinux.org/forum/viewtopic.php?t=4157](http://www.sabayonlinux.org/forum/viewtopic.php?t=4157)
[QUOTE=lxnay]It's all open, and code is available on our SVN, the tricky thing is... that I don't talk about it yet, since it's not yet done Smile[/QUOTE]

To be honest, I think it is great fun.  I think the anticiaption of new features is great, and I agree that to give it to everyone before it is done really would diminish the cool factor, as people would grumble about its shortcomings.  What bothers me more is that sabayon doesn't release public beta's, but, being a gentoo distribution, what would the point be.  It's a rolling release anyway.

---

### Post by manmower on 2007-03-03
Has anyone actually seen the source code? Or does anyone have a direct link to it? They claim it's on there but I have no idea where to look. I was browsing the svn the other day but found nothing.

---

### Post by RAV TUX on 2007-03-04
> **FyreBrand said:**
> I don't really want the code or idea for my own project and I'm sure they will eventually open the code base.

I'm also sure they give a lot back, but that's not really what's irritating.  It's the fact they leak a "really cool" project is in the works and then it seems they make sure that everyone knows a few "important" people know what it's all about.  Do you see the kind of message that's sending?  It also doesn't excite me one bit about the distributions projects overall.  What's the point in hanging around there discussing or being a part of the project if unless you're one of the important people?

When I want to see what's happening in development release X in Ubuntu I can follow what's happening and participate to the degree I'm able.  Even if I'm not immediately privy to all the details I still feel welcomed into the project.  If I read through the KDE development news and blogs I can get an idea of what is happening and even an opportunity to contribute.  Just being able to give feedback in the comments of blogs or news posts makes users feel welcome.

Sabayon looks really nice.  I also think they've done an amazing job with 3.26.  I'm not going to go to their forums and criticize them either, but I just like communities and projects that are a little more transparent and a lot more inviting.  That is a bottom line factor why I stick with K/X/Ubuntu.Not sure what the controversy is about they they tell you what the Project Entropy is about on the front page, key words, "initial work"...


> you were great and Sabayon Linux 3.3 release, the new upcoming website, the [COLOR=Red]initial work on the Project Entropy (binary packages on steroids, yeah!)[/COLOR], the new artwork and forum are some of the things that we are now able to provide you.[http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

> **manmower said:**
> Has anyone actually seen the source code? Or does anyone have a direct link to it? They claim it's on there but I have no idea where to look. I was browsing the svn the other day but found nothing.

manmower if you are talking about the source code for the Project Entropy, how can you expect the code to be released when it is still a work in progress?

If you are talking about the source code for the rest of Sabayon, remember Sabayon is simple pre-compiled Gentoo,...I suspect your source Code will be found on the Gentoo website. If not send an e-mail to one of the devs I am sure they will get back to you, or simply ask your question at freenode #sabayon or #sabayon-dev-help

---

### Post by manmower on 2007-03-04
> **RAV TUX said:**
> manmower if you are talking about the source code for the Project Entropy, how can you expect the code to be released when it is still a work in progress?

:confused: 

It's quite common for **open source** projects to share the code while the work's in progress, to allow volunteers to help out, the obvious example being the Linux kernel.

But I'm not even saying the code needs to be open per se at this time, but lxnay's post [here](http://www.sabayonlinux.org/forum/viewtopic.php?p=26939#26939) suggests exactly that.

---

### Post by RAV TUX on 2007-03-04
> **manmower said:**
> :confused: 

It's quite common for **open source** projects to share the code while the work's in progress, to allow volunteers to help out, the obvious example being the Linux kernel.

But I'm not even saying the code needs to be open per se at this time, but lxnay's post [here]("http://www.sabayonlinux.org/forum/viewtopic.php?p=26939#26939") suggests exactly that.did you simply e-mail Fabio Erculiani					 and ask him for it?
or simply ask your question at freenode #sabayon or #sabayon-dev-help

---

### Post by mips on 2007-03-05
> **manmower said:**
> :confused: 
But I'm not even saying the code needs to be open per se at this time, but lxnay's post [here]("http://www.sabayonlinux.org/forum/viewtopic.php?p=26939#26939") suggests exactly that.

From that post I gather that the code & info is on the svn site and available for all to see . He is just not talking about it.

What stops you from browsing the site and reading up on it ? The same you would go and do over at freashmeat or whatever.

---

### Post by manmower on 2007-03-05
I have browsed their SVN, as mentioned earlier, but since Entropy is going to be a set of applications or whatever I don't really know what to look for, and just searching the svn site for Entropy (using Google) returns nothing. I am not complaining about the fact they are not disclosing what Entropy will be or even that I can't find the code, so there really is no need to be defensive about it. I was just wanting to have a look at it and hazard a guess as to what they have in store for their users, but I've already stopped caring.

---

### Post by RAV TUX on 2007-03-08
> **mips said:**
> From that post I gather that the code & info is on the svn site and available for all to see . He is just not talking about it.

What stops you from browsing the site and reading up on it ? The same you would go and do over at freashmeat or whatever.

> **manmower said:**
> I have browsed their SVN, as mentioned earlier, but since Entropy is going to be a set of applications or whatever I don't really know what to look for, and just searching the svn site for Entropy (using Google) returns nothing. I am not complaining about the fact they are not disclosing what Entropy will be or even that I can't find the code, so there really is no need to be defensive about it. I was just wanting to have a look at it and hazard a guess as to what they have in store for their users, but I've already stopped caring.

this is a post from the freenode, #sabayon IRC channel , which is public knowledge:

> [22:39] <random-sab> so is 3.3 going to have entrophy or is it too early in its development?
[22:41] <wolfpoint> entrophy is long ways away
[22:42] <wolfpoint> its in svn if you want to check it out tho
[22:42] <wolfpoint> I have no interest in binaries

---

### Post by igknighted on 2007-03-09
> **RAV TUX said:**
> this is a post from the freenode, #sabayon IRC channel , which is public knowledge:

I'll second that opinion.  Why use gentoo and then use binary packages?  If they have found a way to use deb's and rpm's I'll be excited, and think its a great development, but I won't use it over portage.  Why use a binary when you can compile?

---

### Post by watson540 on 2007-03-10
gee, I could have sworn debs and rpms **were** binaries, in the sense thats whats in them. as far as your second comment, you should be compiling everything under ubuntu as well, instead of using apt, using your logic

---

### Post by RAV TUX on 2007-03-10
> **watson540 said:**
> gee, I could have sworn debs and rpms **were** binaries, in the sense thats whats in them. as far as your second comment, you should be compiling everything under ubuntu as well, instead of using apt, using your logic

It's elementary, my dear Watson.

---

### Post by FyreBrand on 2007-03-10
> **igknighted said:**
> I'll second that opinion.  Why use gentoo and then use binary packages?  If they have found a way to use deb's and rpm's I'll be excited, and think its a great development, but I won't use it over portage.  Why use a binary when you can compile?Maybe I'm a little confused but aren't e-builds binaries?  Compiling is great when it's required but not every application gains a speed or stability boost from compiling.  Sometimes it's worth the time just to install a binary.

---

### Post by .aku on 2007-03-11
> **FyreBrand said:**
> Maybe I'm a little confused but aren't e-builds binaries?  Compiling is great when it's required but not every application gains a speed or stability boost from compiling.  Sometimes it's worth the time just to install a binary.

Nope, ebuilds are not binaries !

Ebuilds are just *bash scripts* for emerge to perform the compilation and installation of software, but it can be used to install binaries too.

//aku

---

### Post by FyreBrand on 2007-03-11
Thanks aku.  I'm still trying to wrap my head around portage.  It's a pretty complex and powerful tool.  It can look simple, and I suppose behave that way if it's configured well.  I really like it.  I'm going to try a ground up install this summer.  I've started doing my reading and research now, hahaha.

---

### Post by Rodneyck on 2007-03-12
Not good news from the mothership...

> Can anything be done to reverse the situation and to return Gentoo on the path of its former glory? Without the radical overhaul of the Gentoo power structures, it's highly unlikely that anything positive will be done to Gentoo in the near future. With the developer turnover at an all-time high, there is little chance that even the minimum of release and bug-fixing goals will be met. But since the current project leaders are unable to see the rapid downfall of the distribution and unwilling to take any radical measures to reverse the trend, there is little hope for the project. Unless they wake up soon, Gentoo Linux, once the most innovative and refreshing of all distributions, will become nothing more than an average, buggy operating system characterised by endless bickering among the few developers that will bother to remain with it.

[http://distrowatch.com/weekly.php?issue=20070312#future](http://distrowatch.com/weekly.php?issue=20070312#future)

---

### Post by zaratustra on 2007-03-12
So sad... Something should be done soon, or I(we) will loose primary operating system:confused: :mad: :(

---

### Post by igknighted on 2007-03-12
> **zaratustra said:**
> So sad... Something should be done soon, or I(we) will loose primary operating system:confused: :mad: :(

Honestly I think looking into the future this is an issue Ubuntu may deal with at some point.  Debian is not terribly far behind Gentoo in terms of internal struggles and decreasing popularity, but there is one point with them that really concerns me.  It is their adherence to free software principles.  Don't get me wrong, I think those principles are great and I support them fully, but look at the distros gaining popularity using Debian code:  Xandros, Freespire, Mepis, Mint, etc.  Heck, Debian folk are already uneasy about Ubuntu using their code.  If Debian starts sliding towards obscurity quicker than they are now, and they look around and see those distro's using their code and becoming immensely popular while flying in the face of free software principles,  then Ubuntu might really be in trouble.  But hopefully I am wrong :)

---

### Post by RAV TUX on 2007-03-12
> **Rodneyck said:**
> Not good news from the mothership...



[http://distrowatch.com/weekly.php?issue=20070312#future](http://distrowatch.com/weekly.php?issue=20070312#future)

> **igknighted said:**
> Honestly I think looking into the future this is an issue Ubuntu may deal with at some point.  Debian is not terribly far behind Gentoo in terms of internal struggles and decreasing popularity, but there is one point with them that really concerns me.  It is their adherence to free software principles.  Don't get me wrong, I think those principles are great and I support them fully, but look at the distros gaining popularity using Debian code:  Xandros, Freespire, Mepis, Mint, etc.  Heck, Debian folk are already uneasy about Ubuntu using their code.  If Debian starts sliding towards obscurity quicker than they are now, and they look around and see those distro's using their code and becoming immensely popular while flying in the face of free software principles,  then Ubuntu might really be in trouble.  But hopefully I am wrong :)

Interesting...I do believe that the **[Sabayon]("http://cafelinux.org/forum/index.php/board,3.0.html")** Devs would make up for any shortfalls if Gentoo did falter, just as I believe the Ubuntu Devs would make up for any shortfalls when Debian eventually fractures and falters...

I honestly believe that in the long run **[Wolvix]("http://cafelinux.org/forum/index.php/board,5.0.html")** Hunter has much more to offer, and the longevity of a Slackware based distro may prove to be more dependable...

Also **[rPath]("http://cafelinux.org/forum/index.php/board,4.0.html")** is a serious contender to watch.

---

### Post by FyreBrand on 2007-03-12
> **RAV TUX said:**
> Interesting...I do believe that the **[Sabayon]("http://cafelinux.org/forum/index.php/board,3.0.html")** Devs would make up for any shortfalls if Gentoo did falter, just as I believe the Ubuntu Devs would make up for any shortfalls when Debian eventually fractures and falters...

I honestly believe that in the long run **[Wolvix]("http://cafelinux.org/forum/index.php/board,5.0.html")** Hunter has much more to offer, and the longevity of a Slackware based distro may prove to be more dependable...

Also **[rPath]("http://cafelinux.org/forum/index.php/board,4.0.html")** is a serious contender to watch.Well since we've totally derailed mips thread (sorry mips hope you're not mad, hehe) I'm curious about a couple things.

You've brought up Wolvix a couple times now.  Why do you think Hunter has much more to offer?  Since you evaluate so many distributions what do you consider strengths and weaknesses in a distro?  What are absolute deal breakers for you (ie: they just aren't worth considering) ?

---

### Post by igknighted on 2007-03-13
> **RAV TUX said:**
> Interesting...I do believe that the **[Sabayon]("http://cafelinux.org/forum/index.php/board,3.0.html")** Devs would make up for any shortfalls if Gentoo did falter, just as I believe the Ubuntu Devs would make up for any shortfalls when Debian eventually fractures and falters...

I honestly believe that in the long run **[Wolvix]("http://cafelinux.org/forum/index.php/board,5.0.html")** Hunter has much more to offer, and the longevity of a Slackware based distro may prove to be more dependable...

Also **[rPath]("http://cafelinux.org/forum/index.php/board,4.0.html")** is a serious contender to watch.

In the long run I worry about anything Slack based.  Any distro completely made by one guy worries me.  If he gets bored ever or god forbid anything bad happens to him, no more Slack?

The rPath one does intrigue me.  That uses Conary, right?  I've heard a lot of good things about that package manager.  In fact, on the Sabayon forum today a lot of people were wishing for Sabayon to jump ship on Gentoo and go to a Conary based system.  Obviously its not that easy, but I'm gonna have to check out what the buz is all about ;-)

---

### Post by tchoklat on 2007-03-31
queation?

I have Sab 3.25 installed and have a 64bit system. I have ordered the 3.3 64bit version on DVD. Will I be able to upgrade to the new 64 bit version without losing anything, eg settings etc.


Tony

---

### Post by igknighted on 2007-04-01
> **tchoklat said:**
> queation?

I have Sab 3.25 installed and have a 64bit system. I have ordered the 3.3 64bit version on DVD. Will I be able to upgrade to the new 64 bit version without losing anything, eg settings etc.


Tony

Yes, the Sabayon upgrade works fairly well.  I would back up however, because anything is possible.

---

### Post by darksong on 2007-04-01
I was really disapointed with Sabayon 3.3 MINI - the Kde seemed cut down and it done a really poor job on detecting my hardware, escpcialy my monitor. Is the DVD any better?

---

### Post by hanzomon4 on 2007-04-02
> **darksong said:**
> I was really disapointed with Sabayon 3.3 MINI - the Kde seemed cut down and it done a really poor job on detecting my hardware, escpcialy my monitor. Is the DVD any better?

I 2nd that request

---

### Post by obocho on 2007-04-02
hey guys, 
I just wanted to say; SABAYON is really coooool!!!

almost everyrthing is faster than all other distro I tried...

maybe sabayon liked my laptop, I don't know the reason... but it works great!!!

---

### Post by igknighted on 2007-04-02
> **darksong said:**
> I was really disapointed with Sabayon 3.3 MINI - the Kde seemed cut down and it done a really poor job on detecting my hardware, escpcialy my monitor. Is the DVD any better?

Yeah, for some reason the normally superb monitor detection was off this release... after install its an easy fix, but its nice to have just work.  There have been lots of posts in the Sabayon forums about this issue.  I'm sure with the next release this will be back to how it was before.

The DVD does have more, but you would be better off installing what you want on the mini because you cannot subtract easily from the DVD.  Like if you wanted the kicker menu, look on the Sabayon forums for a how to on what you need to emerge to get it.

---

### Post by darksong on 2007-04-02
Hehe - might aswell get the DVD. I already have most of the Distrowatch top 100 avalible to me.

---

