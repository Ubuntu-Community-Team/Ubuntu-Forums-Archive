---
title: "Gentoo vs. Sabayon"
date: 2007-08-30
forum: Gentoo and derivatives
---

### Post by Chymera on 2007-08-30
what is your opinion?

---

### Post by fuscia on 2007-08-30
i've never used gentoo, but it's my unfair wild guess that sabayon is to gentoo what osx is to freebsd, or maybe what ubuntu is to debian.

---

### Post by igknighted on 2007-08-30
> **fuscia said:**
> i've never used gentoo, but it's my unfair wild guess that sabayon is to gentoo what osx is to freebsd, or maybe what ubuntu is to debian.

The BSD doesn't really hold as OSX really isn't BSD.  Some of the userspace was indeed borrowed, but the kernel is a Mach microkernel.

The Debian/Ubuntu analogy is closer, but Sabayon and Gentoo are at the same time far more different than Ubuntu/Debian and also much more the same.

Sabayon uses the Gentoo (portage) repositories.  So in that sense, with enough messing around you would be running pure Gentoo.  This obviously isn't possible with Ubuntu/Debian, so in a certain sense Sabayon IS Gentoo (sort of a Mint/Ubuntu deal).  However, at the same time, Sabayon has so much stuff not in Gentoo (entropy for example), and the difference in the philosophies of the two almost makes them FEEL more different than Debian/Ubuntu.

Overall, you cannot say which is better.  Sabayon is certainly easier.  Gentoo is certainly better for performance.  I personally give the nod to Gentoo due to the buggyness of Sabayon, but both are very good.

---

### Post by Chymera on 2007-08-30
I approve of the fact that sabayon is easier... but what do you mean by performance when stating that gentoo is better for performance?

Are you hinting at the fact that it is a lot more lightweight, in terms of preinstalled apps, and thus has fewer processes hogging the resources?
Because if that is the case it's not a problem of performance but rather of how much stuff you actually want to have on your comp....

---

### Post by igknighted on 2007-08-30
> **Chymera said:**
> I approve of the fact that sabayon is easier... but what do you mean by performance when stating that gentoo is better for performance?

Are you hinting at the fact that it is a lot more lightweight, in terms of preinstalled apps, and thus has fewer processes hogging the resources?
Because if that is the case it's not a problem of performance but rather of how much stuff you actually want to have on your comp....

Nope, nothing to do with how many apps installed.  It has everything to do with (1) Gentoo is compiled with optimizations specific for your system, while Sabayon cannot be (unless you recompile everything... which pretty much makes you running Gentoo), and (2) Sabayon has a lot of services enabled by default that are rather unnecessary for most users.  Sure you could disable them all, but again, you might as well run true Gentoo if you want to go through that.

I'm not ripping Sabayon, I love the distro.  It got me into Gentoo when I otherwise would not have tried it.  But Sabayon gave me a taste of what Gentoo could be, and I moved on to the real thing.  Try updating world on a Sabayon install.  Sure, it can be done.  But it is not easy.  If you want to do that then you should run true Gentoo, its easier in the end.  Plus if Sabayon has a package you want, just add their overlay.

---

### Post by justin whitaker on 2007-08-30
Sabayon is certainly easier to get up and running....but you end up emerging from Gentoo, and breaking things, and then you are back to the handbook and the mercy of the Gentoo Community Forums. 

In other words, just run Gentoo. :)

---

### Post by Chymera on 2007-08-30
why do you end up braking things?

---

### Post by mips on 2007-08-30
> **Chymera said:**
> why do you end up braking things?

Probably because of the Sabayon overlays.

---

### Post by rsambuca on 2007-08-30
I have them both installed on my rig and prefer gentoo over Sabayon.  Sabayon looks pretty slick, but is somewhat buggy on my pc. 

I agree with igknighted here, in my eyes gentoo is all about customizing it for your rig, while Sabayon just installs everything.  Just a preference of ease of installation vs customization.

---

### Post by SunnyRabbiera on 2007-08-30
Gentoo what can I say, its better then it was... no more two day installations, thank goodness for live CD's!
but I can say Sabayon is better, at least in its installer as Gentoos live leaves a lot to be desired.

---

### Post by mips on 2007-08-30
> **SunnyRabbiera said:**
> Gentoo what can I say, its better then it was... no more two day installations, thank goodness for live CD's!


My undetanding is that the live CD installs precompiled binaries and does not compile from source. Is my understanding correct ?

---

### Post by EndPerform on 2007-08-30
> **mips said:**
> My undetanding is that the live CD installs precompiled binaries and does not compile from source. Is my understanding correct ?

Yes, it does by default, which is pretty nice.

---

### Post by rsambuca on 2007-08-30
I think they are precompiled yes.  That is why I did the stage3 tarball installation via a chroot from ubuntu.

---

### Post by Chymera on 2007-08-31
> **mips said:**
> My undetanding is that the live CD installs precompiled binaries and does not compile from source. Is my understanding correct ?

Uhm.... how does that translate into english?

---

### Post by mips on 2007-08-31
> **Chymera said:**
> Uhm.... how does that translate into english?

Uhm, what part don't you understand ?

> Originally Posted by mips
My undetanding is that the live CD installs precompiled binaries and does not compile from source. Is my understanding correct ?

The stuff on the LiveCD has been compiled and the reulting binary files were put on the CD as opposed to the Source being put on the livecd and compiled on your local machine when booted up. (Not that I can see it all fitting on the cd though)

---

### Post by Foxmike on 2007-08-31
Here's my 2 cents: I personnaly try to get the best of two worlds: for pre-compiled packages, I use Ubuntu which is just awsome IMHO.  I am using Gentoo to try something else, completly different than Ubuntu and I quite love it!  I have read about Sabayon, almost downloaded the DVD, but each time I retract for if I need a system up'n running in no time, I know Ubuntu does the job flawlessly.

To me, Sabayon looks like building a system from source using apt-get build-dep and apt-get source ...   I'm pretty sure Sabayon guys (and gals) are doing a superb job, but it just not fit my needs.

---

### Post by zaratustra on 2007-09-03
Here is what I think...

There is no basis for comparing these two distros. They aim at different group of users and point of Sabayon is to make make Gentoo easier. As main point of Gentoo is customization, Sabayon gives you no customization at all. So, I use Gentoo because I am one of those 'die hard' users but I think Sabayon is the one who should compete with Ubuntu and SUSE and other gay distros. (No flame, just kiddin). Also, enthropy may become quite nice Pack Man when it is get done and it would be nice to have in Gentoo when you have no time to compile stuff.

Happy h4x0ring...

---

### Post by Cannaregio on 2007-09-04
> **Foxmike said:**
> Here's my 2 cents: I personnaly try to get the best of two worlds: for pre-compiled packages, I use Ubuntu which is just awsome IMHO.  I am using Gentoo to try something else, completly different than Ubuntu and I quite love it!  


I agree totally.
Ubuntu rocks, and Sabayon is almost equally wondrous. 
I run both.

Of course "real" debian and "real" gentoo can deliver more power. But why the hassle? 
Of course you have more power at your fingertips when you leave a GUI environment.
So what?
The point with both Ubuntu and Sabayon is that you have MORE power and choices (not less).

If you want *that* barebone real power, you can immediately have it, of course, *behind* both Ubuntu and Sabayon GUI environments. 

Please don't be silly: behind Ubuntu is a full-fledged debian and behind Sabayon is a full-fledged gentoo.
'Ts not a reduction of GNU-inux, in both cases is an EXPANSION. 

Hence there's no need to choose a poorer barebone version when you can have it toghether with  both power AND whistles AND frills :-)

Just my 000.2 eurocents. I might be wrong. Yet don't touch my Ubuntu and my Sabayon.

---

### Post by Foxmike on 2007-09-04
> **Cannaregio said:**
> I agree totally.
Ubuntu rocks, and Sabayon is almost equally wondrous. 
I run both.

Of course "real" debian and "real" gentoo can deliver more power. But why the hassle? 
Of course you have more power at your fingertips when you leave a GUI environment.
So what?
The point with both Ubuntu and Sabayon is that you have MORE power and choices (not less).

If you want *that* barebone real power, you can immediately have it, of course, *behind* both Ubuntu and Sabayon GUI environments. 

Please don't be silly: behind Ubuntu is a full-fledged debian and behind Sabayon is a full-fledged gentoo.
'Ts not a reduction of GNU-inux, in both cases is an EXPANSION. 

Hence there's no need to choose a poorer barebone version when you can have it toghether with  both power AND whistles AND frills :-)

Just my 000.2 eurocents. I might be wrong. Yet don't touch my Ubuntu and my Sabayon.
Something is really true IMHO, is that more Linux flavours there is, better it is.  I have not tried Sabayon yet, but for me Gentoo acomplished it's goal flawlessly, is to bring something I have to build by hands.  So to me Sabayon looks too "finished".  But at this point is more a personnal opinion than a fact of course!:D

---

### Post by cotcot on 2007-09-28
I had them both of them installed, deleted sabayon and kept gentoo. Sabayon was much slower and a little bit buggy.  Though I still keep an eye on its development.

---

### Post by handy on 2007-10-12
Beagle has been slowing down Sabayon, I've just done the xdelta thing & made a 3.4f DVD, apparently beagle only works when called now, at the moment in my 3.4a it can be using 80+% of cpu power, & I never use it!

It was easier to do the upgrade than for me to uninstall beagle, as it has connections.

To the topic, Sabayon suits me, I've gone past wanting to customise everything, the few bugs don't bother me, the speed is fine & about to become much better (fingers crossed), their community is small compared to Ubuntu, but it is quite friendly with a helpful forum.

The graphics display is superior to any OS I have ever seen, I don't know why but boy is it crisp.

The Sabayon dev's will have to do something dramatically wrong for it to come off my #1 machine.  then again, someone else may do something that especially suits me & win me over.  

It's great having so many choices.

---

### Post by handy on 2007-10-15
I'm currently in the loooong process of installing Gentoo, & no other O.S. has taught me so much during the installation. :lolflag:

I expect I'll be through tomorrow, so it will have taken me about 3 days!

---

### Post by yabbadabbadont on 2007-10-15
That is usually how long it takes me to get my Gentoo system fully configured.  It doesn't help that there have been both gcc and glibc updates since the stage files were last built.  (I wish they would update the stage files whenever that happens...)  I'm waiting for them to be rebuilt in November before I put Gentoo back on this machine.

---

### Post by handy on 2007-10-15
It looks like I've gone from the sublime to the ridiculous when it comes to customisation!

On various distro's & PC-BSD, I have been happily only customising my fonts to suit 1280x1024 or higher res, changing the desktop wallpaper, fiddling with the panels & menu's & adding removing a few app's, customising Firefox a little, that's about it for the last couple of years.

Now I have discovered ***USE=" "*** & kernel compilation, amongst other things, oh boy!

Looks like its back to the old days of make 'em just how you want 'em, & nothing has ever given me the control that Gentoo has...  

Therefore 3 days, though I expect I'll take longer than that being my first time through.  Then I'll start playing around with the kernel more... :-)

I do understand why Sabayon exists, it is a really easy quick install, with everything on the DVD.  Most users don't want to spend days installing their OS.  Most don't have the time to start with.

---

### Post by handy on 2007-10-17
I have spent about a day (day #2 in the Gentoo install process so far) trying to get X installed on Gentoo; during the process I have built multiple kernels, unmerged my initial modular X, installed monolithic X, provided the prescribed USE=" " flags, read lots of the great  Gentoo documentation, read some of the good X.org documentation, & it still will not work!

Having posted on the Gentoo forum I have received a reply saying that it is not actually X's fault but the 2.6.23's kernel's, & that I must build the nvidia-drivers module using a sandbox parameter to get past this problem:

***FEATURES="-sandbox" emerge nvidia-drivers***

I have not tried this as yet as I have decided to have a whole day of not trying to install Gentoo, so that I may continue to enjoy the process... :lolflag:  That's not tongue in cheek, I am actually enjoying the process.  

I am learning so much about Linux; I certainly would not recommend Gentoo to anyone who wasn't at least somewhere in the intermediate stage of familiarity with Linux. I'm only just there myself, but I come from a history of supplying professional support to the windows world, which probably helps, I am also determined :-:-)-: which I believe is a computer tech' support dude's initial prerequisite qualification :-) everything else follows after that.

So, by the time I get Gentoo installed, which should be sometime this year ;-) my Linux knowledge base will have grown dramatically from what it was before I downloaded the 54Mb Gentoo install .iso.

*The bottom line is:-*  Anyone who wants to have a look (beyond the ever so easy Sabayon) at Gentoo, should be prepared to spend at least 3 big days, (that's an all going well scenario) & be prepared to learn an enormous amount about the Linux kernel based OS's, (that's of course if you don't already know it), & know that you ***_will_*** get a Linux kernel based OS that is customised to have not much more in it than what you put there.  

A caveat on that:-  Because the Gnome, & (especially) the KDE meta-packages have such huge amounts of software included, you have to make a choice to spend the time (as I will) to sort through & manually install only that which you require (or at least as best we can in that regard).

Due to my simple computing requirements I have been basically a Gnome user who appreciates that KDE is (at the least) a far more configurable desktop than Gnome;- having learned this from my experience with PC-BSD & PCLOS.  

Due to the aforementioned, I am using the Gentoo ***/etc/make.conf*** file with the ***USE="-gnome -gtk2"*** parameters, including other appropriate calls (which I've forgotten at the moment), (all calls under the "**-**" prefix are ma***_s_***ked in program compilation, therefore playing a major part in creating programs with or without the chosen dependencies. Gentoo has  even more control than this regarding masking, but I have not learned about it yet.  

The above, is for my personal learning experience as much as anything else, I really don't need any more speed for what I do; by the time I have successfully installed Gentoo I will have gained another stripe on my belt re. IT;  please don't get me wrong, that was not an ego statement, its just a reflection of the fact that some processes enforce intense learning & installing Gentoo certainly can (under certain circumstances) be one of them. :-)

---

### Post by zapcojake on 2008-02-28
> **rsambuca said:**
> I think they are precompiled yes.  That is why I did the stage3 tarball installation via a chroot from ubuntu.

Is there a howto for this?  I would be very interested.  Thanks

---

### Post by mips on 2008-02-28
> **zapcojake said:**
> Is there a howto for this?  I would be very interested.  Thanks

Did you even bother looking at the installation handbook?

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap6](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap6)
or
[http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml)

There really is no difference whether booting from a livecd or an existing linux installation of any sorts.

---

### Post by zapcojake on 2008-02-28
> **mips said:**
> Did you even bother looking at the installation handbook?

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap6](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#book_part1_chap6)
or
[http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86-quickinstall.xml)

There really is no difference whether booting from a livecd or an existing linux installation of any sorts.

yup, I have installed Gentoo a couple of times from the cd.  Thanks for getting snippy though.  What I wanted to know is there any Ubuntu specific things I needed to know.

---

### Post by rsambuca on 2008-02-28
I am not sure what you mean by "Ubuntu specific things".  When it comes to installing via chroot, you are just using a terminal, so it doesn't really matter if you are doing it from Ubuntu, Kubuntu, Arch, Foresight, etc.

---

### Post by mips on 2008-02-28
At the expense of sounding snippy again.

> **mips said:**
> 
There really is **[COLOR="red"]no difference[/COLOR]** whether booting from a livecd or an **[COLOR="Red"]existing linux installation of any sorts[/COLOR]**.

---

### Post by zapcojake on 2008-02-28
I was doing some reading about Linux from Scratch and there are apparantly a some of issues with the Ubuntu  and LFS  I didn't know if there would be similar trouble with Gentoo.

---

### Post by zapcojake on 2008-02-28
> **mips said:**
> At the expense of sounding snippy again.

You could have just said that in the first place.

---

### Post by mips on 2008-02-28
> **zapcojake said:**
> You could have just said that in the first place.

But I did, in Post#27.

First I referenced two Gentoo docs and then I told you there is no difference wrt livecd or distribution booted from.

I give up, have a nice day.

Edit: Updated ignore list.

---

### Post by zapcojake on 2008-02-28
> **mips said:**
> But I did, in Post#27.

First I referenced two Gentoo docs and then I told you there is no difference wrt livecd or distribution booted from.

I give up, have a nice day.

Actually, the first thing you said was "Did you even bother to look at the handbook?"  Which seems a little snippy for an answer to perfectly good question.

---

### Post by angryfirelord on 2008-03-13
Currently I'm using Sabayon as a stepping stone in order to jump to gentoo later. At first, I was turned off by the source compiling, but now I'm really starting to like it. I emerged the latest firefox from source and I notice it's snappier than the one Ubuntu provides.

But in terms of Gentoo vs. Sabayon, you really can't compare the two in that manner since Sabayon is gentoo (with some settings chosen and binary packages).

---

### Post by Siljrath on 2008-09-26
sabayon is lovely.
gentoo is lovely.

to each as per their needs.


my needs are best met with sabayon.

OOTB & KISS.

!!!  and thats that!

OOTB as they call it in their philosophy, i prefer to call it by what they call their DVD versions.   Full.  and yep.. it really just about is.  you'll b doing less installing of other software after installing sabayon is finished, as it includes so much.  loads of very clever little touches (like the irc sabayon help icon, the nvidia setup icon making twin view easier than ever before), metisse, compviz, Out Of The Box.

i just got back from, catastrophic hardware failures (musta got lightninged), installed 3.5full on my system.  happy as larry, one day after install, my desktop looks as cool as it did before i lost those hardrives.  (and i do alot of moddings to kde)  (alot!!)

still seems to run pretty damn stable n sweet...  fingers crossed though should i go for any updates.  hehe.  will be sticking with portato, having tried spritz... not fun.. who knows, it might get better, but yes, its getting much further from the ideals of gentoo with that i'm sure.

havn't come across anything i can't customise yet.  ...oh, havnt got around to getting three monitors to work yet..  always something else on the go.  will get it done soon... just that its not like the 5 clicks required to get twinview working.  :D

i've seen over 100 distros.

i use sabayon by choice.

not because its the one i happen to be using at time of writing.

because it's the one that's sticking around.

...there must be some reason... right?

to choose it over even ubuntu!?  right?

...

...there must be some reason... 

*fades into the shaddows among the trees...  and then was gone*









:lolflag:

---

### Post by ippokratis on 2008-10-11
I love Gentoo and I love Sabayon!  I see no big difference as they are "twin brothers"!  Sabayon is easier to install it, has a lot of stuff (it reminds me of Ubuntu Ultimate Edition - one of my favorite distros, but in a Gentoo base instead of UUE) and with a perfect interface.
Gentoo is something else!  Nice, fast but a little pain in the @ss for its new users!  But it's OK!  We are in Linux because we like the hard way! \\:D/

---

