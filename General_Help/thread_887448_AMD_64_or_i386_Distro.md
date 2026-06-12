---
title: "AMD 64 or i386 Distro"
date: 2008-08-12
forum: General Help
---

### Post by Hitnfly on 2008-08-12
i have some interesting question.. it is better to install i386 on AMD 64 or its wise to use AMD 64 only? cause i had lot of experiement lately and i noticed i386 work better than AMD 64 any reason why? the reason why i made this new thread so i can have better relationship with this community and as well help out my friends thanks..

---

### Post by hyper_ch on 2008-08-12
what worked better?

AMD64 --> 64bit support
i386 --> 32bit support

64bit runs almost perfectly. For some stuff there is still legacy mode... but I don't really see much reason nowadays to not use 64bit on linux.

---

### Post by Hitnfly on 2008-08-12
true but the odd is im running linux mint and ubuntu both of them are 32 bit n run on 64 bit its run flawless.. can anyone tell me why? and it is possible to combine 32 bit n 64 bit to run any pc? if it can be done then linux wouldnt have to worry about 32 bit or 64 bit? let me know thanks guysss

---

### Post by hyper_ch on 2008-08-12
a 32bit os can run on 64bit plattform... but not vice-versa.

---

### Post by Mgiacchetti on 2008-08-12
ok.  this seems like a common question. so here goes.

Unless the following facts are true, you are better off with 32 bit;

You have 4 gigs of ram or more.
You have a program that requires a 64 bit os.


The reason is this, YOU WILL NOT BE ABLE TO INSTALL ALL THE PROGRAMS AVAILABLE TO A 32 BIT OS ON 64.

With 32 bit you will have more support, as more people are actually using 32 bit as opposed to 64 bit.

I have an AMD Athlon 64 and find ABSOLUTELY NO REASON to use 64 bit.

---

### Post by Joeb454 on 2008-08-12
Actually you'll find that most of the app's in the Ubuntu repo's are available for both 32 bit **and** 64 bit installs.

I have a 64 bit system (I have done since Gutsy was released) and it works flawlessly, Flash support works fine as of 8.04 so I don't see a reason to use 32 bit.

Chances are if there's no 64 bit version in the repo's, then you can compile it yourself.

---

### Post by Mgiacchetti on 2008-08-12
noted, however if you decide to install a program that IS NOT IN THE REPO'S you will NOT BE ABLE TO FIND A DEB FOR IT and most likely have to compile it yourself.

again this is another reason NOT to use 64 aside from the fact that unless you have 4 gigs of ram, THERE IS NO REASON TO INSTALL 64 BIT

---

### Post by tribaal on 2008-08-12
The old "32 bits has more applications available" argument is pure FUD.

Every single package from the repositories is available to amd64, 99% of which are native 64bits appliactions.
The only couple of packages which are still 32-bits only will install the necessary 32bits libraries when you install them.

If you use Skype or other proprietary program without 64bits, simply make sure you install general 32bits libs first, and it'll work just as well.

I use only 64 bits, as I like to use an OS that fits my hardware (and I do lots of scientific computing / image processing, I can use the slight increase in speed for floating-point processing). And yes, I can do everything I would do with a 32bits OS.

Why stay behind?

- Trib'

---

### Post by hufferd on 2008-08-12
> **Joeb454 said:**
> Actually you'll find that most of the app's in the Ubuntu repo's are available for both 32 bit **and** 64 bit installs.

I have a 64 bit system (I have done since Gutsy was released) and it works flawlessly, Flash support works fine as of 8.04 so I don't see a reason to use 32 bit.

Chances are if there's no 64 bit version in the repo's, then you can compile it yourself.

Hmmmmmm I have had nothing but issues with trying to keep things running on a AMD 64 platform with the 64 bit os

I can name many apps that are only in 32 bit vers.

---

### Post by tribaal on 2008-08-12
Would you please provide a few examples?
**Edit:**... of repositories applications which are 32bits only.

If there are, then they need to be packaged properly.

- Trib'

---

### Post by Mgiacchetti on 2008-08-12
why stay behind?  Because there is no reason for me to switch to 64 bit.

I have no use for an os that doesnt support the programs i want to use on it.

and yes there are programs in the repos that DO NOT HAVE A 64 BIT INSTALL

dont ask me what they are, I ditched 64 bit months ago

---

### Post by tribaal on 2008-08-12
Well, fine, use your machine as you please :)

I'm just being curious what those packages are, nobody could ever point me to a specific problem... which I'd be more than willing to fix.

Anyway, I'm sure you can find plenty of good threads on the age old 32bits vs 64bits debate, it's been discussed *ad nauseam* since theses formus exist :)
The best place to look is probably [this sticky]("http://ubuntuforums.org/showthread.php?t=765428"), for a start.

Cheers :)

- Trib'

---

### Post by Mgiacchetti on 2008-08-12
gyache gyachi etc

---

### Post by Krupski on 2008-08-12
> **Hitnfly said:**
> i have some interesting question.. it is better to install i386 on AMD 64 or its wise to use AMD 64 only? cause i had lot of experiement lately and i noticed i386 work better than AMD 64 any reason why? the reason why i made this new thread so i can have better relationship with this community and as well help out my friends thanks..

If you have an AMD 64 bit processor or an Intel EMT64 capable processor, you should run 64 bit Ubuntu.

And, if you have 4GB or more of ram, you MUST use 64 bit OS or else you won't "see" all the memory.

Lastly, I've experimented with both i386 and AMD64 versions. Both seem to run equally well... I've noticed no difference between them (other than the fact that 32 bit doesn't use all of my 8GB of ram!).

For what it's worth...

-- Roger

---

### Post by Krupski on 2008-08-12
> **Mgiacchetti said:**
> noted, however if you decide to install a program that IS NOT IN THE REPO'S you will NOT BE ABLE TO FIND A DEB FOR IT and most likely have to compile it yourself.

again this is another reason NOT to use 64 aside from the fact that unless you have 4 gigs of ram, THERE IS NO REASON TO INSTALL 64 BIT

I *assume* (could be wrong) that there is a "32 bit emulator" for Ubuntu 64 bit... because when Java is installed, I see one of the dependencies is something like "IA32LIBS" which I'm guessing is a 64 to 32 bit "layer".

If this is true, then (again I assume) any 32 bit app will run in 64.

Anyone know for sure?

---

### Post by hufferd on 2008-08-12
I posted [here]("http://ubuntuforums.org/showthread.php?t=886875") about this very issue I have also posted about having to force install some software [here]("http://ubuntuforums.org/showthread.php?t=886875")

---

### Post by Mgiacchetti on 2008-08-12
You will not (noticably) ride any faster with your bike even if the highway is twice as broad as it was before.
In one cpu-cycle you can transport twice the amount of data. But that only applies if you have applications that actually _use_ the broader highway. You need 64-bit apps. Encoding DVDs is one of those, since it is a very cpu-intensive work. Additionally, 64-bit allows you to have more RAM in your machine. 32-bit was able to adress 2^32 = 4 GB of RAM. On the other hand, 64-bit allows you to use 2^64 = 16 ExaByte. (Every additional bit in the exponent doubles the amount of data you can use!)
 The downside of 64-bit is, of course, that it is not yet 100% compatible.
The more people ask for better support of 64-bit, the better it will become.

---

### Post by tuxxy on 2008-08-12
32 bit apps run in 64, most 64 apps are supported now, only one I can think of is the 32bit web flash plugin

---

### Post by Mgiacchetti on 2008-08-12
> **Krupski said:**
> I *assume* (could be wrong) that there is a "32 bit emulator" for Ubuntu 64 bit... because when Java is installed, I see one of the dependencies is something like "IA32LIBS" which I'm guessing is a 64 to 32 bit "layer".

If this is true, then (again I assume) any 32 bit app will run in 64.

Anyone know for sure?

ok so youre saying that in order for me to run a 32 bit app in 64, i must install a 32 bit vm and go from there?

Naah, too much hassle, ill just use 32 bit because again THERE IS NO REASON TO SWITCH BACK.

---

### Post by tuxxy on 2008-08-12
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by Mgiacchetti on 2008-08-12
tried that, it wouldnt install .

---

### Post by tribaal on 2008-08-12
> **Mgiacchetti said:**
> gyache gyachi etc

Ah come on, that's not even in the repos in the first place :)

Here's how I installed it on amd64 - granted, it's an extra command-line away:

```
sudo aptitude install imagemagik # required lib
sudo dpkg -i --force-architecture gyachi_1.1.0-1_i386_gutsy.deb
```

- Trib'

---

### Post by Mgiacchetti on 2008-08-12
this talk is like a religion

"you should do this and that"  when there is no need to

what possibly could you benefit from using 64 bit
the support for 64 bit can not compare to 32 bit,
yes, some 32 bit apps STILL DO NOT WORK in 64 bit

and 
IF THEY DO NOT HAVE > 4 GIG ram or have a program that crunches a lot of numbers,   it is USELESS to install an os that THE ONLY BENEFIT(S) are increased math processing and increased ram recognition.

---

### Post by hufferd on 2008-08-12
> **tribaal said:**
> Ah come on, that's not even in the repos in the first place :)

- Trib'



its not in the repos but it is Linux software ?? is it not???

---

### Post by Mgiacchetti on 2008-08-12
> **tribaal said:**
> Ah come on, that's not even in the repos in the first place :)

- Trib'
  your point?

mine?  it dont work on 64 
"any 32 bit app should work?"  nope this one don't

---

### Post by tribaal on 2008-08-12
See my edited post...

Works fine. Nice program by the way, didn't know about it yet :) Thanks

- Trib'

---

### Post by Mgiacchetti on 2008-08-12
think of it this way.
You run a 64 bit os.
you NEED to install program x

you find out that program x will ONLY install in a 32 bit os, and there is no source to the deb.

howto time

```

go here, change this,
 install this, run that, 
wait this long, 
then go here change this, type this, add these w, y, z, 
compile this, 
wait more time, 
then run this, MAKE SURE NOT TO TYPE THIS, 
do that, go here, type this, 
hit enter, wait some more, 
then you *should* have a deb file that will install on your system. 
if not, oh well, go install something else

```it makes you feel accomplished if you do finally succeed, but its shortlived, because you will probably run into another program x that doesnt like 64 bit. (although you will probably become a master at this procedure)


BTW  for gyachI gyachE  cant remember which one, but the sound drivers are written in 32 bit and DO NOT WORK in 64 bit... :)

---

### Post by Mgiacchetti on 2008-08-12
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

> The unfortunate thing is that it is actually a little tricky converting some programs from 32-bit to 64-bit and therefore some programs cannot run in native 64-bit mode. They can run in an emulated mode but this will be a little slower.

> One might still recommend staying with 32-bit software because the 32-bit software has more support

> Within 10 years one would expect most computers to be 64-bit

---

### Post by hyper_ch on 2008-08-12
> **Krupski said:**
> If you have an AMD 64 bit processor or an Intel EMT64 capable processor, you should run 64 bit Ubuntu.

And, if you have 4GB or more of ram, you MUST use 64 bit OS or else you won't "see" all the memory.

Not quite true. If the processor supports PAE then you can use more than 4 GB ram. Either install the server kernel or recompile the generic (or whatever one) with PAE enabled.

I installed the notebook of one of my boss a little while ago and chose Ubuntu 64bit. Everything works like a charm. Flash, Skype, Java, ....

---

### Post by dai_vernon on 2008-08-12
> **Mgiacchetti said:**
> think of it this way.
You run a 64 bit os.
you NEED to install program x

you find out that program x will ONLY install in a 32 bit os, and there is no source to the deb.

howto time

```

go here, change this,
 install this, run that, 
wait this long, 
then go here change this, type this, add these w, y, z, 
compile this, 
wait more time, 
then run this, MAKE SURE NOT TO TYPE THIS, 
do that, go here, type this, 
hit enter, wait some more, 
then you *should* have a deb file that will install on your system. 
if not, oh well, go install something else

```it makes you feel accomplished if you do finally succeed, but its shortlived, because you will probably run into another program x that doesnt like 64 bit. (although you will probably become a master at this procedure)


BTW  for gyachI gyachE  cant remember which one, but the sound drivers are written in 32 bit and DO NOT WORK in 64 bit... :)
I don't see why you'd rail against 64bit OSs; even if there's no benefit now, which isn't true, for everyday users, what direction is the software world moving?  Towards 64bit.  Not necessarilly away from 32, but 64 bit support is only growing, so I'd advise to stop trolling.  For the everyday user it's a matter of preference at this point, and eventually it will be more clearly a benefit.

---

### Post by Mgiacchetti on 2008-08-12
so if someone doesnt have 4 gigs or more, and has no need for a 64 bit os, they *should* still install the 64 bit os, just because?  

I'm not trolling, im using past experiences with 64 bit in my opinion about this subject.  read the documents on the issue, they say the same thing.

Yes in 10 years most computers will be 64 bit, but until then (a long ways away) it is recommended to go with 32 bit because of the lack of support for 64 bit.

everyday users (like me for instance) have No Need for a 64 bit environment.

---

### Post by Mgiacchetti on 2008-08-12
and for those who actually do know what they are doing, and know the tradeoffs for using a 64 bit vs 32 bit and can figure things out without the mass of support, go ahead and use it.   but to the n00bs, use 32   its easier.

---

### Post by babylon2233 on 2008-08-12
getdeb.net provide 64-bit .deb package.So,  I don't really have to worry about unable to run certain software as long as it is open source(some of open source software don't even have a .deb package). I never really have any problem using 64-bit Linux.

---

### Post by hyper_ch on 2008-08-12
> **Mgiacchetti said:**
> Yes in 10 years most computers will be 64 bit, but until then (a long ways away) it is recommended to go with 32 bit because of the lack of support for 64 bit.
Maybe on windows... linux servers have been running on 64bit for a long time already and also there's no reason to stick with 32bit on desktops....

I still have to find an application that does not run on 64bit using linux.

---

### Post by babylon2233 on 2008-08-12
I don't think n00bs will have problem using 64-bit Linux unless they never know how to use any of Linux before. One more, once people start to take advantage of 64-bit, there is no more room for 32-bit OS.  

> **Mgiacchetti said:**
> 
You have 4 gigs of ram or more.



This is completely wrong as you can recompile your kernel to support up to 64GB RAM

This is example of program which take advantage of 64-bit:


> 
As 64-bit processors grow in popularity, the developers have begun work on the utilization of the 64-bit extensions of these processors to potentially increase speed in PCSX2.[2] 64-bit versions of Linux can currently take advantage of this, and 64-bit versions of Windows, such as Windows XP Professional x64 Edition or Windows Vista x64, will be used in a future release.


From PCSX2 Wikipedia article

---

### Post by Hitnfly on 2008-08-12
interesting so technically its doesn't matter what bit you run on linux compare to other. I can see that 32 bit n 64 bit is doable to combine for future Linux user? i hope so and i believe its can be done on one CD with "compatible program" that will set up for you n etc..

MAC and Microsoft is based on what you have 32 or 64 only?

---

### Post by hufferd on 2008-08-12
> **Hitnfly said:**
> interesting so technically its doesn't matter what bit you run on linux compare to other. I can see that 32 bit n 64 bit is doable to combine for future Linux user? i hope so and i believe its can be done on one CD with "compatible program" that will set up for you n etc..

MAC and Microsoft is based on what you have 32 or 64 only?

Haha hitnfly 

I just had to comment I love the "sudo apt-get install bowl."  in your tag line :lolflag:

---

### Post by Mgiacchetti on 2008-08-13
> **babylon2233 said:**
> 
This is completely wrong as you can recompile your kernel to support up to 64GB RAM


OK so your telling me.

32 bit can see > 4 gig ram

which means

another reason to NOT HAVE to use 64 bit.

"why stick with 32 bit"?  cuz I have no need for 64 bit.
AND I have seen, when people come into the IRC for support, someone guides them through a fix, only to find out it didnt work because of the 64 bit thing.

---

### Post by hyper_ch on 2008-08-13
> **Mgiacchetti said:**
> another reason to NOT HAVE to use 64 bit.
Stick with whatever you want but do not exaggerate and say that 64bit is totally useless and nothing works...

---

### Post by Mgiacchetti on 2008-08-13
im just saying that if someone has 32 bit installed, there is no reason to scrap it to install 64 just because you think that there is no reason to keep 32 bit.

That being said, i suppose the opposite is true as well.

However, when I ran 64 on my amd athlon 64  i had nothing but problems.  Couldnt install the programs I wanted without compiling their source (something I know nothing about)  then when that got finished, it turns out that the guts of the program don't work for 64 bit.

hah, kinda wierd huh?

[http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575](http://sourceforge.net/project/showfiles.php?group_id=158490&package_id=177556&release_id=551575)

as you can see, the source is independant, (duh) however the codecs needed for voice ARE I386 SPECIFIC.
along with everything else there.

---

### Post by hufferd on 2008-08-13
> **Mgiacchetti said:**
> However, when I ran 64 on my amd athlon 64  i had nothing but problems.  Couldnt install the programs I wanted without compiling their source (something I know nothing about)  then when that got finished, it turns out that the guts of the program don't work for 64 bit.

hah, kinda wierd huh 

Well I see we all have our own very strong opinions don't we 

I am just glad to see I am not the ONLY PERSON that is having issues with the 64 bit OS. As I have said [here]("http://ubuntuforums.org/showthread.php?p=5580384#post5580384")

Bottom line is both work well for some correct? - lets drop this and move on :)

Have a great day!
D

---

### Post by hyper_ch on 2008-08-13
> **Mgiacchetti said:**
> However, when I ran 64 on my amd athlon 64  i had nothing but problems.  Couldnt install the programs I wanted without compiling their source (something I know nothing about)  then when that got finished, it turns out that the guts of the program don't work for 64 bit.

And when was that?

---

### Post by tuxxy on 2008-08-13
> **Mgiacchetti said:**
> think of it this way.
You run a 64 bit os.
you NEED to install program x

you find out that program x will ONLY install in a 32 bit os, and there is no source to the deb.


Which programs are you reffering to here as I have yet to find one..

> **Mgiacchetti said:**
> Yes in 10 years most computers will be 64 bit, but until then (a long ways away) it is recommended to go with 32 bit because of the lack of support for 64 bit.

everyday users (like me for instance) have No Need for a 64 bit environment.


What lack of support is this you mention, is this the same as the apps you said dont work on 64bit but didnt list any names?

Also 10 years! do you not think thats a bit of an overstatement, I mean do you even think you could walk in a store and buy a computer today and leave without buying a 64 bit system?

> **Mgiacchetti said:**
> and for those who actually do know what they are doing, and know the tradeoffs for using a 64 bit vs 32 bit and can figure things out without the mass of support, go ahead and use it. but to the n00bs, use 32 its easier.

Why do you assume it would be easier for a new user to install 32bit? are you basing this on your orginal assumption again that there are incompatible programs? 

I have a fried who never used linux in his life, I advised him to go for Hardy 64bit and hes not had one single problem, he loves it.

> **Mgiacchetti said:**
> im just saying that if someone has 32 bit installed, there is no reason to scrap it to install 64 just because you think that there is no reason to keep 32 bit.

hah, kinda wierd huh?

64bit has come on a long way in the laast few years, I think you may be reffering to a period when there was lack of programs support etc

Also yes I would scrap the 32bit install if i had 64bit hardware, why would I want to limit my system to 32bit OS anyway

---

### Post by SeanBlader on 2008-08-13
I'm running 64 bit on my AMD Turion64, haven't had any issues yet. I'm mostly a newbie, don't yet have as a good handle on Ubuntu as I did on Windows. 

On the one hand I'd agree with Mgiacchetti in that I wouldn't rebuild my system if I was running 32 bit, but on the other hand, I wouldn't install 32 bit if I had a system capable of 64. The software and driver support is all there, and personally I'd like to get what I paid for. I'd hate to be considered a luddite too.

---

