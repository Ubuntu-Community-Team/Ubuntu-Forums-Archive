---
title: "Can't Install a Dang Thing - Help or Windows Here I Come (Solved)"
date: 2005-11-13
forum: General Help
---

### Post by Wuhu on 2005-11-13
Ok, I am at my wits end with Ubuntu.  I am new to linux and have played with this thing for over 2 weeks now.  Every time I try to install ANYTHING (take your pick) Synaptic always tells me I can't because packages "are not installable."  We're talking basic things like:

Mplayer
Wireless drivers (I've tried to install ndiswrapper)
Plugins for media (MPEG, MP3, DVD, etc)

I mean everything fails; EVERYTHING!  I have not even been sucessful once.  If it isn't installed with the basic Ubuntu install then I don't have it.  I've enabled every repository I can find, tried to talk to people on IRC (very unhelpful), and read what I can find in the Wiki.  

I need someone to give me step by step (remember, I'm new to linux) to make things work.  I don't want to read another link, I don't want to get on IRC again, and I'm tired of digging through forums.  

I am seriously about a hair away of going back to Windows where at least basic things work.

---

### Post by az on 2005-11-13
For ndiswrapper, you need to install the ndiswrapper-utils package.  It is on the cd, so what error do you get when you ask it to install that?

Let's start with that.  I think your problem are related to the fact that you are using foreign repositories.  What repositories do you have on and where did you learn about them?

---

### Post by aysiu on 2005-11-13
[QUOTE=Wuhu]I've enabled every repository I can find[/quote] This sounds like the problem.

> I don't want to read another link I realize you're frustrated, but we're also all volunteers here. We post links because we don't want to keep typing out instructions over and over again. I promise the first link in my sig works (I wrote it myself) if you follow the directions exactly (which include posting **over** your entire /etc/apt/sources.list). Do not simply add repositories--they'll begin conflicting with one another.

By the way, what does you /etc/apt/sources.list look like right now?

---

### Post by kelsey23 on 2005-11-13
I personally do not recommend Ubuntu to you. I actually only use it because at this time I have no access to a CD burner, and Ubunutu gave out free CDs. Please remember that Ubunutu GNU/Linux is not all GNU/Linux, it is only one distrobution. One distrobution you might consider if you want GNU/Linux to be very simple to use, and you want multimedia plug-ins is [Linspire 5-0]("http://linspire.com/"). Linspire come pre-packaged with many multimedia plugins, due to liscensing fees you must pay. I also would recommend not using Synaptic, but instead apt-get. All you need to do is find out the name for the package you are using, and then type:

sudo apt-get install (package name)

And it may install that way. **But please, please don't let any bad experiances with Ubuntu make you think all GNU/Linux is not! Try a few other distros to and see what you like :-)**

---

### Post by aysiu on 2005-11-13
I agree with kelsey23. First of all, I think there's an easy fix, but if Ubuntu doesn't do it for you, and you don't have the patience to investigate a few links (you may be a busier person than I am), then Linspire may be a good choice for you. I'd also recommend Mepis and Blag.

That said, it just sounds as if you have too many repositories enabled.

---

### Post by nszabolcs on 2005-11-13
[QUOTE=Wuhu]
Plugins for media (MPEG, MP3, DVD, etc)
[/QUOTE]

these are illegal in the usa so these never will be included in a free operating system like ubuntu.

i guess you haven't tried automatix yet [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
this automates everything you want

---

### Post by Wuhu on 2005-11-13
Ok, it sounds like the opinion out there seems to be a problem with my repositories.  I found a HowTo in the Wiki for repositories and went with that.  Basically all the 5.10 and Breezy bin and source repositories to include universe and multiverse.

I figured if it needs a package to install (based on dependencies) then it could find it if I had all the repositories turned on.  I am not using any foreign repsositories, just the ones you can get to by default in Ubuntu.

I want to use Linux, but this is getting insane.  Thoughts?

---

### Post by Wuhu on 2005-11-13
Oh, and here is my sources.list:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by aysiu on 2005-11-13
Comment out (put a # in front of) the CD-ROM line and take all the *us* references out of there. Then ```
sudo apt-get update
```

If that doesn't work, I urge you to please use the instructions in my sig.

---

### Post by Wuhu on 2005-11-13
Ok, I commented out the CD-ROM line.  I don't know what you mean by the us line.  You mean the repositories that begin with us?  

And thanks for the help so far, much better than IRC (told me to "learn more" and "figure it out").

---

### Post by kelsey23 on 2005-11-13
It seems like you have all of the standard respotories installed, again though, I would recommend looking into another distro. Either that, or you could try manually installing the packages. Let's say you download a program called test. The file you downloaded was called test-i686-build-033.deb. Let's also assume you file test-i686-build-033.deb was downloaded to /home/your_username/Desktop   and that you didn't move the file after downloading it. To install it manually, you would type the following into the terminal:

$sudo dpkg -i /home/your_username/Desktop/test-i686-build-033.deb

That should install the package. But some packages do not have debs you can download. Sometimes, though you will be able to convert the package frome say, an RPM to a DEB, and it will install just fine. So now we will assume that Test only came in a RPM, and the file is named test-i686-build-033.rpm  and we will assume that it is in the /home/your_username/Desktop directory. Now, to convert that to a deb, type:

$sudo alien /home/your_username/Desktop/test-i686-build-033.rpm

Typing that will create a .deb called test-i686-build-033.deb in the directory /home/your_username  Then you should be able to install the .deb via dpkg

Hope that helps!

---

### Post by Wuhu on 2005-11-13
[QUOTE=kelsey23]It seems like you have all of the standard respotories installed [/QUOTE] Glad to know.  But tell me if my logic is correct.  If I install a package (through Synaptic or apt-get) and it requires other packages to function correctly, does Ubuntu automatically download those packages as well?

[QUOTE=kelsey23]Hope that helps![/QUOTE]

Getting there.  Thanks.

---

### Post by kelsey23 on 2005-11-13
[QUOTE=Wuhu]Glad to know.  But tell me if my logic is correct.  If I install a package (through Synaptic or apt-get) and it requires other packages to function correctly, does Ubuntu automatically download those packages as well?



Getting there.  Thanks.[/QUOTE]
Typically, it will install all other dependancies.

---

### Post by Drifter on 2005-11-13
I too am new to linux, I had a problem I couldn't solve, but I found out that it was because I did not do what I was shown to do by these very helpful people in here.  I have leaned by my mistakes and I had fun while doing it.  If this becomes a chore for u then u may be in the wrong distro.  When they give u a link to look at if you will go there and read it and follow it you will not only learn to fix your problem but will also learn more.  If you don't read you can;t find out anything.  I have all kinds of experience with computers, I build them for myself.  I stared out with Dos and could make a computer sing, but it took reading a lot of books about Dos.  If linux could use the Dos commands I would be one of the people helping out very much in here, but it is a different language.  You can get all the help u want in here if u will remember the fix is out there.  If I can help in anyway I will be glad to but I am as new as u.  Enjoy this or u will not like it.

---

### Post by kelsey23 on 2005-11-13
Take a look at other possbile distros for you to try (and easy to use)

[Linspire 5-0](http://linspire.com/)
[Mandrivia GNU/Linux](http://mandrivia.com/)
[Fedora (Free RedHat)](http://fedora.redhat.com/)
[Debian (what Ubuntu is based on)](http://debian.org)

---

### Post by Wuhu on 2005-11-13
Thanks, I'll look into it.  Going to give Ubuntu more time because it's pissing me off enough that I want to beat the thing.  Hopefully I win before I chuck this computer out the window.

---

### Post by az on 2005-11-13
Okay, I dissagree with everybody here.  What you are asking Ubuntu to do for you is something it should be able to do out-of-the-box.

Something other than the user is doing something wrong, here.  What is the link to the howto you used?


Also, just so see...
Open up a terminal and type

sudo apt-get -f install

Also, were there any problems with the instalation?

---

### Post by Roobert on 2005-11-13
[QUOTE=Wuhu]Thanks, I'll look into it.  Going to give Ubuntu more time because it's pissing me off enough that I want to beat the thing.  Hopefully I win before I chuck this computer out the window.[/QUOTE]

Yeah, hang in there, man. I am a new Ubunter as well. Installing Ubuntu off the CD was fine, and about 90% of the functionality I need (i.e., e-mail, internet, instant messaging, music, movies) worked right out of the box. But I've encountered a few frustrating tweaks that have been aggravating, but I'm slowly overcoming them as I'm learning about Linux. Right now I'm trying to figure out why the sound and video in Totem is really jerky and out-of sync with the movie (ideas, anyone?). But I have no doubts that the answer is either on this list, or will be provided by the excellent community support we have here (that's right...it's not TECH support, it's COMMUNITY support). 

As with a lot of things, what you get out of it is what you put into it. I think if you can overcome these initial hurdles, you will be able to reap the rewards of an excellent, full-featured OS that is absolutely FREE. But, as others have said, if you aren't the type to fiddle with tweaking your OS setup, then there are several other great Linux alternatives for you to try. It's all about finding what you are most comfortable with. But I still encourage you try to get your Ubuntu up and running, because I think it kicks ass.

Just some thoughts,

~ Roobert.

---

### Post by Wuhu on 2005-11-13
[QUOTE=azz]Okay, I dissagree with everybody here.  What you are asking Ubuntu to do for you is something it should be able to do out-of-the-box.[/QUOTE]

Thank you!!

[QUOTE=azz]Something other than the user is doing something wrong, here.  What is the link to the howto you used?[/QUOTE]

[https://wiki.ubuntu.com//AddingRepositoriesHowto](https://wiki.ubuntu.com//AddingRepositoriesHowto)

---

### Post by Wuhu on 2005-11-13
[QUOTE=Roobert]But I still encourage you try to get your Ubuntu up and running, because I think it kicks ass.

Just some thoughts,

~ Roobert.[/QUOTE]

Yeah, I think it CAN kick ass.  I just think they need to put in more "basic" functionality at the start.  Also, since everything and everyone has to enable more repositories before they can do anything, why not make it the default?

---

### Post by Wuhu on 2005-11-13
[QUOTE=aysiu] If that doesn't work, I urge you to please use the instructions in my sig.[/QUOTE]

Thanks aysiu.  Your repository listed seemed to help.  I was at least able to install Mplayer this time around :eek: .

---

### Post by rlange on 2005-11-13
I know your feelings on link help but if you never look at another link read this one:

 [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)


save the automatix  file to your home directory the click to open and click install.

---

### Post by aysiu on 2005-11-13
[QUOTE=Wuhu]Thanks aysiu.  Your repository listed seemed to help.  I was at least able to install Mplayer this time around :eek: .[/QUOTE] Awesome. I'm putting this as "solved," unless you state otherwise.

---

### Post by zmhs5 on 2005-11-13
I had the same initial problem, because I wasn't connected to the net when I installed.

For myself, it was solved by reinstallation with internet access.

---

### Post by az on 2005-11-13
[QUOTE=zmhs5]I had the same initial problem, because I wasn't connected to the net when I installed.

For myself, it was solved by reinstallation with internet access.[/QUOTE]

You could have set up internet access through the networking tool in the system menu.

---

