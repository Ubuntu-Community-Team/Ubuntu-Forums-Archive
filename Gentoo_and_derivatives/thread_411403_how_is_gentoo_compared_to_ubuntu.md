---
title: "how is gentoo compared to ubuntu"
date: 2007-04-16
forum: Gentoo and derivatives
---

### Post by izizzle on 2007-04-16
hello.

I was wonder how gentoo is compared to ubuntu. although ubuntu picked up all my hardware flawlesly, I am wondering if gentoo can do a better job. how efficient is it? is it easy to set up? newbie friendle?

please reply,

thanks in advance,

-Imran

---

### Post by jdong on 2007-04-16
Gentoo is not as user-friendly as Ubuntu... It will pick up less hardware out of the box (but you can compile drivers by hand or through Portage to support more hardware, but it won't support much more than Ubuntu)

It uses a rolling-versions release cycle, meaning that new versions of software is added to the repositories as soon as they are available, as opposed to all-at-once every 6 months with Ubuntu. You may or may not like that release style better. It's good in the sense that you always get fresh new toys to play with, but bad in the sense that things are more likely to break unpredictably after a routine update.

Setup/installation takes patience and dedication on the user's side.

I would encourage you to read the Gentoo documentation on installation, or snoop around the Gentoo forums, or even try installing and using the distribution. Open Source is all about finding what YOU like, not what others force you to use :)


(I used to be an avid Gentoo user before Ubuntu)

---

### Post by NeoLithium on 2007-04-16
Well, at the risk of getting flamed; gentoo is not a newbie friendly distro.  Ubuntu is easy on the installation for a great many people; but gentoo can be fairly daunting.  But also keep in mind, it is efficient and a great distro on it's own, just different than ubuntu.

I haven't tried their newer GUI Installation, their last release (2006.1) it was broken and didn't do things right; and the command line install...WHOAH. Brew some coffee and get ready to use links with their forums searching; for the most part.  That being said, I might consider trying their new release.  As well, emerge is one outstanding creation that is probably the best package manager around.

I think they have a live CD that you can try though, to take a peek around without having to install over your current setup.

EDIT- Perhaps a moderator might want to move this to the Gentoo forum.

---

### Post by chakkaradeep on 2007-04-16
Gentoo - Long journey in making Linux your best mate :D 

Ubuntu - The Easiest way to make your Linux your best mate :guitar:

---

### Post by wuzzerd on 2007-04-16
Imran:

In Gentoo you have to build your own kernel and configure it yourself.  It is a great experience if you want to learn a lot about linux and are not afraid of the command line.  It can take quite a few days for a new user to get everything he wants installed. It is a good idea to read the handbook [http://www.gentoo.org/doc/en/handbook](http://www.gentoo.org/doc/en/handbook) before you try to install.  Everything is compiled on your machine which takes quite a bit longer than installing a binary distribution like Ubuntu.

If you are new to Linux, I would suggest learning your way around Ubuntu first, then when you think you want to try Gentoo you can build it in a separate partition, keeping your Ubuntu install which can come in handy if you have to fix something.

Check out the forums [http://forums.gentoo.org](http://forums.gentoo.org) 

Hope this helps.

---

### Post by tchoklat on 2007-04-16
interesting comments. I am unable to install any version of Ubuntu on my system. Sabayon Linux (Gentoo based) installed easily and detected everything. I also have windows XP on it and it wont detect my ethernet adapter.

Gentoo is good for me!

---

### Post by stmiller on 2007-04-16
I've used Gentoo in the past. It is quite nice, especially portage. But yes, you have to make your own configuration files. And compile your own kernel. So if you don't particularly know how to make an /etc/fstab and /etc/make.conf and so forth, it's probably not for you.

But there are excellent gentoo docs to walk you through an install on their site. I learned a lot by using Gentoo. And they have a very open/free etc philosophy which is great.

---

### Post by jdhore on 2007-04-17
this is kind of one of those situations where: "if you need to ask, you should not be using Gentoo", but here we go:
1. Gentoo detects less hardware out of the box and you're close to screwed if you need specific hardware to follow the steps for install. (ex: wifi to download a stage3 image, a portage image or to update portage).
2. The install is quite a bit more difficult than the Install for Ubuntu.
3. The install takes a while (if you know what you're going to be doing, 2-4 hours for a base install (no GUI))...add another 8 hours for Gnome or KDE and tack another 2 hours on top of that if you don't really know what you're doing.
4. It takes at least 2-3 times longer to install any package than it does on Ubuntu
5. one of the 2 huge advantages to Gentoo: FAST...on the same system i have Ubuntu on, Gnome opens in 1/4 the time on Gentoo and Firefox opens instantly as opposed to taking a few seconds on Ubuntu.
6. the other advantage to Gentoo: customizable...if you want a module/feature or don't want a module/feature from some package you can always add/remove it with USE flags.

Gentoo's great if you want to learn a lot about linux and have a sense of accomplishment. but if you're impatient, lazy, or not too good with the command-line, you'll be hating life with Gentoo. I thought i knew quite a bit about linux...but i learned easily 40 or 50 new things while installing Gentoo.

---

### Post by wuzzerd on 2007-04-17
Well Izzle's tagline says it all.  When I was 13 you could heat the nieghborhood with a machine that couldn't run Donkey Kong, not even Fortran which came later. :lol:

---

### Post by izizzle on 2007-04-17
thank you sooooo much guys, youre a great help.

I believe i will give gentoo a shot, just to see how its like.....for myself  ;)

Thanks in advance,

- Imran

---

### Post by mips on 2007-04-18
> **izizzle said:**
> thank you sooooo much guys, youre a great help.

I believe i will give gentoo a shot, just to see how its like.....for myself  ;)


You might want to consider Sabayon Linux as an intro to Gentoo. This way you get a fast install and you can play around with emerge/portage, use flags etc. Sabayon is basically precompiled Gentoo.

Once you are comfortable with the above you could try your own Gentoo install.

---

### Post by jdong on 2007-04-18
On the downside though, Sabayon is several overlays over Portage, and I've had many cases where something in a Sabayon overlay causes another program in Portage to fail to emerge.

---

### Post by coplan on 2007-04-23
As a long time Gentoo user who is very new to Ubuntu, I thought I should offer some of my wisdom.  

Gentoo is a great system, and it really is a great way to learn linux.  You see everything from the ground up, so you learn a lot about how your system works inside and out.  It's not newbie friendly...but that's more of an intimidation factor.  If you're patient and you are willing to learn (a lot), then it is, in my opinion, the best way to learn about linux.  

However...there are a lot of things that are quirky and less-refined from some people's perspective.  I like to think that a lot of things are a series of hacks.  For example, on my laptop, I have media keys at the top.  To get them to work, there's a number of hacks that I could use, and it was some tinkering but I got them to work exactly the way I wanted.  In contrast, Ubuntu seems to pick them up without question and they work out-of-the-box.  The behavior isn't exactly what I want, in Ubuntu, but I havn't yet tried to tweak that -- so I don't know how easy that is to fix.  

So of course the question is this:  Why am I using Ubuntu now?  Well, I use both.  My laptop uses Ubuntu.  There's a lot of odd hardware on there, and Ubuntu is best and picking that stuff up.  Quite frankly, I don't really have time to be figuring out every detail and aspect of the laptop.  Especially since I didn't build the laptop so I don't know the hardware as well.  I also use the laptop for my field photography, so I like to have a lot of free space -- and the portage tree (the source files for updating your system) gets really large in Gentoo.  But I use Gentoo on my desktop where resources are nearly unlimited, the hardware isn't anything special and I really want performance maxed out.  Don't believe the naysayers...I can get a much faster system out of Gentoo than I can in Ubuntu...but it is at a cost of a lot of tinkering.  

My advice to newcomers to Linux -- go with a simple setup like Ubuntu or SUSE.  If you decide you like Linux a lot and you have "the bug" (commonly called an obsession), you'll end up in a distro like Gentoo or Slackware anyhow -- especially if you're a tweaker.  You just can't beat the USE flag system that Gentoo has for tweaking.

---

### Post by coplan on 2007-04-23
> **mips said:**
> You might want to consider Sabayon Linux as an intro to Gentoo. This way you get a fast install and you can play around with emerge/portage, use flags etc. Sabayon is basically precompiled Gentoo.


I would highly recommend against that.  Sabayon is really a great system, don't get me wrong.  But it has so many overlays on the portage tree that it acts wierd at times.  It's on its way to being the Ubuntu of the Gentoo world (as Ubuntu is to Debian), but it's still not mature yet.  I think you'll get really confused if you start with Sabayon.

---

### Post by Ateo on 2007-05-14
Gentoo is not easy to set up and it's not newbie friendly.

If Ubuntu can do it, so can Gentoo. It's just with Gentoo, YOU have to do it.

---

### Post by NumPy on 2007-05-22
> **Ateo said:**
> It's just with Gentoo, YOU have to do it.

Which is a great thing IMO. 

Something that sticks out to me when reading opinions of a distro, is the need to use the term "user-friendly". Lets be honest, user-friendly is entirely relative to what you want to achieve with your trip down LINUX road. I think that Gentoo is great for beginning users, you LEARN the OS. Its really not entirely different of the original MS 95/NT installs, where you had to figure things out. (that is vauge and interpolated, but hey:)) Anyhow I would NOT be where I am today with the OS on the whole if I did not start with a barebone distro. Slackware, Debian, RH, Mandrake(driva) all in the beginning where hideous on the setup, but you learned how to make your OS work. Its nice to see that there are distros' out there that still hold on to the idea that its your responsibility to know what your doing, how your doing it, and push you to educate yourself on the LINUX kernel, use, and FS structure.. 

and thats my 0.2

---

### Post by blacksadness on 2007-05-29
Well after almost 3 years experimenting, i can say gentoo is the best distro out there.. it gives you great experience and gets you really familiar with your system, the only downside is the long compile time and well if you're nto paying attention you could simply replace a critical file.. and actually the only reason i switched to ubuntu is that i don't have to wait much for what i need.. i'm at a stage where i need every second i can get.. so gentoo at this time is not for me.. later though i could come back.. or have a dual boot system.. good luck with your experience.. and make sure you read every step in the handbook also don't do the easy install do a stage 3 that way you will get to know your way arround.

---

### Post by mozetti on 2007-05-29
> **izizzle said:**
> although ubuntu picked up all my hardware flawlesly, I am wondering if gentoo can do a better job.

How do you do a better job than "flawlessly"?

---

### Post by cferthorney on 2007-05-30
I find it amusing that there are so many users on the Gentoo forums (Including myself) who are experimenting with *buntu and I come on here and find a forum section dedicated to Gentoo!

Gentoo has many things I love, some of which are easy to achieve (For instance a different colour prompt for root to standard user), others not so easy (Portage)  The compile times are insane sometime (It took nearly 24 hours to compile KDE on a 2.6 GHz with 2G of RAM.  Admittedly this was all of KDE bar the educational package though)  Another thing I really like is a software tool called webapps which keeps track of which popular webapps are installed on VHosts etc.  I am going to try and create .debs for this.  Just need to find out how...

Personally I now use Gentoo on my servers (With a few CentOS 5 thrown into the mix for Xen testing etc) and I have gone to Kubuntu for my desktop/laptop due to the better hardware support and me not wanting to have to spend ages watching stuff compile to ensure I have updated.  Gentoo is stable (As long as you don't use ~x86 - their mark for unstable/preview) and due to its rolling update policy ideal in my opinion for servers.  Updates will always come in and you can pick or choose what you use.  For desktops however *buntu is perfect.  APT is an exceptional update tool and with debian as a base you know what you are going to get :-)

Gentoo for servers, *buntu for desktops from now on.

---

