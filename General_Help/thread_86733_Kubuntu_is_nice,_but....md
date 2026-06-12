---
title: "Kubuntu is nice, but..."
date: 2005-11-06
forum: General Help
---

### Post by victorche on 2005-11-06
The whole Kubuntu idea has only one major problem.
It is on 1 CD only...
Well it is almost perfect... But the devs really should think about a second extraCD.
I have my own PC with good internet connection.
But I have a laptop, a PC at work, my girlfriend's PC ;)
I am a Slackware user and Slackware is something really stable. What Slackware does not have is that perfect and user-friendly package managment like the one here in Kubuntu. But!
There is one big BUT here...
I have 2 CDs of latest Slackware /10.2/... And one exctra CD with latest aplications that I use... A CD, made by myself.
With these 3 CDs I can install it, make it work perfect, even without an internet cable plugged in ;)
Not everyone has fast, unlimitted internet connection. Especially in countries like mine /Bulgaria/...
So what I can install is one perfect base of one future reliable linux system with all the features I want... Only this. Kubuntu will be a major success when there is an extra CD.

I have it on my PC now for testing and I really like it. Some of my friends also like it and they ask me to install it on their PCs... But most of them have a bad connection with monthly limit of 300 MBs
So they will use Slackware ;)
Just because the one-CD Kubuntu is the good base only. To make it useful and powerful, you need really fast internet conection.

So, think about it, devs. Really ;)

---

### Post by ofek on 2005-11-06
well i think 1 cd is kind of the main concepts many like about ubuntu.
most people wouldn't want to download a 4 cd distro if a 1 cd distro can be just as good.
in this 1 cd ubuntu gives anything ull need for office work and even alittle more.
if u need anything more u can just make a cd of softwares u like just as u do on slackware i realy can't see the problem here.
oh and for downloading slackware's 2 cds u need the fast connection as well there nothing u can do about it ull have to download the other softwares anyway.

i downloaded about 40 programs more than what ubuntu gives and thier total size is about 200mb i think thats better than downloading another cd (700mb) for the 200mb of programs i realy need from it, and chanses it won't give me all i need and ill still have to download extra stuff.

---

### Post by victorche on 2005-11-06
[QUOTE=ofek]....
if u need anything more u can just make a cd of softwares u like just as u do on slackware i realy can't see the problem here.[/QUOTE]
Well first of all the soft for Kubuntu /For downloading as .debs I mean/ is much more hard job to do.
I had a problem yesterday - I wanted the latest D4X /Download manager/... I saw that the latest version /2.5.6/ is in the repositories. I saw it when I browsed them manually with my browser. "That's nice!" I said to myself... But Adept and Synaptic keep telling me that the latest one is 2.5.0
I decided to download it manually like a .deb package... Well good, but not enough.
It depends on gcc 4.0.2
Mine is 4.0.1
In Slackware I can just download the .tgz and it works ;)
Well to use the latest and simple download manager, you have to upgrade the whole distro to "dapper"... Just to have gcc 4.0.2 and then to be able to use D4X 2.5.6
Debian /And Ubuntu/ developers like to use the words "package need testing"...
But what testing we have here just for one download manager?!
You can look on the D4X's main web site... It is said there that the latest version /2.5.6/ has many bug fixes... It can handle now files mor than 2 GBs etc...
So the devs of D4X did a lots of testing itself... And I should wait until the release of "Dapper" just to be able to use a bug-free version of one small download manager?

That sounds funny even after the favourite Debian's thought like: "This package needs a good testing and you can use it after 6 months"...

And what if I just follow your advice?
I will download so many .deb packages, burn them and if I try to use them I will meet the reality. For the single use of a simple download manager, I will have to do a dist-upgrade :???:
Dependancies are good, but only when they are smart... And D4X is only an example ;)
I can tell you (even if I am not a Debian/Ubuntu developer), that D4X works perfectly even with some older versions of gcc like 3.3.6
And D4X will work great but if it is the latest one. 2.5.0 is too old and full of bugs ;)
Which all we here can use after tons of upgrades /To "Dapper"/...

---

### Post by mlomker on 2005-11-06
Ubuntu is available on a DVD that includes Kubuntu and many other things.  It currently has to be downloaded, though.

---

### Post by victorche on 2005-11-06
[QUOTE=mlomker]Ubuntu is available on a DVD that includes Kubuntu and many other things.  It currently has to be downloaded, though.[/QUOTE]
I know that there is a DVD version, but if there are extra things... I think you should inform the users more clear ;)
Just because in the description it says that the DVD includes Install CD and Live CD...
Not even a word about extra packages ;) Just a combination of Install and Live :)

---

### Post by mlomker on 2005-11-06
> I think you should inform the users more clear

The forums are totally separate from Ubuntu.com.  We don't have any more input than you do.

There's a mention of the DVD in their [shipping FAQ.]("http://www.ubuntulinux.org/support/documentation/faq/shipit/")

---

### Post by shinygerbil on 2005-11-06
You could make a CD of all the files you have stored in your cache - every .deb you dowload and install through any package manager is saved in the cache. You could burn them all to CD and you would then have an extra offline repository of apps with all the correct dependencies.

Steve

---

### Post by mlomker on 2005-11-06
[QUOTE=shinygerbil]You could make a CD of all the files you have stored in your cache [/QUOTE]

That's a good point.  Configure one machine by downloading the files and then burn the contents of /var/cache/apt/archives to a CD and copy those files to the same directory on your other machines.  When you run Synaptic/apt-get it'll look there first.

---

### Post by victorche on 2005-11-06
The idea is perfect... Just one little question:
Why there are so many packages with almost the same names?
For example:
gcc-3.3-base_1%3a3.3.6-8ubuntu1_i386 /*I thought Kubuntu 5.10 is coming with gcc 4.0.1 by default... I have no idea what this 3.3.6 makes here*/;
gcc-4.0_4.0.1-4ubuntu9_i386;
gcc-4.0_4.0.2-3ubuntu1_i386;
gcc-4.0-base_4.0.2-3ubuntu1_i386;
gcc_4%3a4.0.1-3_i386;
gcc_4%3a4.0.2-1_i386

So 6 different .debs for gcc :???: And please don't tell me that I need all of them ;)

---

### Post by mlomker on 2005-11-06
> So 6 different .debs for gcc :???: And please don't tell me that I need all of them ;)

The first part is the package name and the second part is the version.  Each entry in Synaptic is a different package.

You should run **sudo apt-get autoclean**.  That command deletes the older packages that are no longer listed in the repositories.

---

### Post by peanut butter on 2005-11-06
[QUOTE=victorche]Well first of all the soft for Kubuntu /For downloading as .debs I mean/ is much more hard job to do.
I had a problem yesterday - I wanted the latest D4X /Download manager/... I saw that the latest version /2.5.6/ is in the repositories. I saw it when I browsed them manually with my browser. "That's nice!" I said to myself... But Adept and Synaptic keep telling me that the latest one is 2.5.0
I decided to download it manually like a .deb package... Well good, but not enough.
It depends on gcc 4.0.2
Mine is 4.0.1
In Slackware I can just download the .tgz and it works ;)
Well to use the latest and simple download manager, you have to upgrade the whole distro to "dapper"... Just to have gcc 4.0.2 and then to be able to use D4X 2.5.6
Debian /And Ubuntu/ developers like to use the words "package need testing"...
But what testing we have here just for one download manager?!
You can look on the D4X's main web site... It is said there that the latest version /2.5.6/ has many bug fixes... It can handle now files mor than 2 GBs etc...
So the devs of D4X did a lots of testing itself... And I should wait until the release of "Dapper" just to be able to use a bug-free version of one small download manager?

That sounds funny even after the favourite Debian's thought like: "This package needs a good testing and you can use it after 6 months"...

And what if I just follow your advice?
I will download so many .deb packages, burn them and if I try to use them I will meet the reality. For the single use of a simple download manager, I will have to do a dist-upgrade :???:
Dependancies are good, but only when they are smart... And D4X is only an example ;)
I can tell you (even if I am not a Debian/Ubuntu developer), that D4X works perfectly even with some older versions of gcc like 3.3.6
And D4X will work great but if it is the latest one. 2.5.0 is too old and full of bugs ;)
Which all we here can use after tons of upgrades /To "Dapper"/...[/QUOTE]
Yes i have had the same type of problem youhad.
at onepoint i was thinging of going back to SuSe because they actually update their packages.
K/ubuntu neends to address this problem.
anyone know shuttelworth's e-mail (just joking)?

---

### Post by shinygerbil on 2005-11-06
According to *man apt-get*, you can run: > sudo apt-get autoclean which will remove any cached packages which can no longer be downloaded - "This allows a cache to be maintained over a long period without it growing out of control."

My guess is that all the different versions you have downloaded/upgraded in the past are stored separately, but as the old versions can't be downloaded anymore (correct me if I'm wrong) autoclean will remove all but the latest packages.

You may want to backup your cache before you try anything, just in case... ;)

Steve


EDIT: Damn, beaten to it :P shouldn't be eating at the same time ;)

---

### Post by victorche on 2005-11-06
[QUOTE=shinygerbil]According to *man apt-get*, you can run:  which will remove any cached packages which can no longer be downloaded - "This allows a cache to be maintained over a long period without it growing out of control."

My guess is that all the different versions you have downloaded/upgraded in the past are stored separately, but as the old versions can't be downloaded anymore (correct me if I'm wrong) autoclean will remove all but the latest packages.

You may want to backup your cache before you try anything, just in case... ;)

Steve


EDIT: Damn, beaten to it :P shouldn't be eating at the same time ;)[/QUOTE]
I've just used "sudo apt-get autoclean" and... there are still 6 different gcc packages :)

---

### Post by mlomker on 2005-11-06
[QUOTE=victorche]I've just used "sudo apt-get autoclean" and... there are still 6 different gcc packages :)[/QUOTE]

Have you looked in Synaptic?  I have at least 6 installed.

---

### Post by Copter on 2005-11-06
> **victorche]I know that there is a DVD version, but if there are extra things... I think you should inform the users more clear  said:**
> yes, and another funny thing is that the DVD version of Hoary was (afair) about 2.5gb of data. there was lots of space left for some extra stuff.[QUOTE=mlomker]Configure one machine by downloading the files and then burn the contents of /var/cache/apt/archives to a CD and copy those files to the same directory on your other machines.  When you run Synaptic/apt-get it'll look there first.sounds nice indeed. i have to try that in the future

copter :]

---

### Post by shinygerbil on 2005-11-06
> **victorche]The idea is perfect... Just one little question:
Why there are so many packages with almost the same names?
For example:
gcc-3.3-base_1%3a3.3.6-8ubuntu1_i386 /*I thought Kubuntu 5.10 is coming with gcc 4.0.1 by default... I have no idea what this 3.3.6 makes here*/ said:**
> 

For certain programs, GCC 3.3 is required rather than GCC 4.0. Silly, but true. (although you have only the 'base' part installed - I'm not sure what that means.)

[QUOTE=victorche]gcc-4.0_4.0.1-4ubuntu9_i386;

This is the latest GCC 4.0 for (K)Ubuntu Breezy, as far as I know.

> **victorche]gcc-4.0_4.0.2-3ubuntu1_i386 said:**
> 

This doesn't appear in my repo, is it the Dapper version...?

[QUOTE=victorche]gcc_4%3a4.0.1-3_i386;
gcc_4%3a4.0.2-1_i386

I don't know about these - they're not in my repository. Unless you have repos that I don't which is quite likely, although they don't have ubuntu in the name, so a Debian repo maybe?.. I also can't help you any further, because I regularly clean out my cache (I have pathetically small amounts of space left on my drive...)

[QUOTE=victorche]So 6 different .debs for gcc :???: And please don't tell me that I need all of them ;)[/QUOTE]

I don't know about all of them, but at least a few of them are useful :) and they don't take up that much space either! ;)

Steve

---

### Post by victorche on 2005-11-06
Well, Steve...
1) I don't have gcc 3.3.6 installed on my machine according to Synaptic/Adept
2) I don't use some extra or debian repositories also... Just the default ones for Kubuntu.
3) gcc 4.0.2 is from dapper...
Well the idea of making dapper my choice was... not to be on the bleeding edge of Kubuntu. But to have the latest D4X 2.5.6 :)
I know it sounds funny, but that's the way Ubuntu/Kubuntu works.

And that's why I made this topic anyway. The devs have their own opinion of adding new packages. Need testing they say... Well with my long experience with Slackware I don't have such a problem.
D4X's devs say that 2.5.0 has a lots of bugs. The last one - 2.5.6 - has all these bugs fixed ;)
But to use it on my machine I need gcc 4.0.2.... Both D4X 2.5.6 and gcc 4.0.2 are available in the repositories, but for dapper only ;)
So I had to update more than 280 files in order to have one small but bug-free download manager :)

Strange way of making distros ;)

---

### Post by claydoh on 2005-11-06
Odd as I just compiled D4X 2.5.6 with gcc 4.01, and gcc4.02 was released 9/28/2005, only a month ago for that matter. Where does it say it requires 4.02?

D4X 2.5.6 was released only a week ago.
I wonder how many official releases of any distro has both these recent versions available?

> <Summary>---
      Configuration: release

   Host system type: i686-pc-linux-gnu
       C++ compiler: g++ (GCC) 4.0.2 20050808 (prerelease) (Ubuntu
                     4.0.1-4ubuntu9)
       Install path: /usr

         ESD output: enabled
         OSS output: enabled
       libao output: disabled

        SSL enabled: yes
And for that matter, look at the above and see what version gcc4 truly is.

[look here for gcc-3x]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=gcc-3&sourceid=mozilla-search")
They are all in main, no extra repositories needed.

Does slackware offer (good)dependency checking? does it download and install all the bits you need if they aren't there already? it's a different philosophy between debian/(k)ubuntu and slackware at least in terms of software packaging, thats what it all boils down to.

---

### Post by victorche on 2005-11-07
[QUOTE=claydoh]Odd as I just compiled D4X 2.5.6 with gcc 4.01, and gcc4.02 was released 9/28/2005, only a month ago for that matter. Where does it say it requires 4.02?

D4X 2.5.6 was released only a week ago.
I wonder how many official releases of any distro has both these recent versions available?


And for that matter, look at the above and see what version gcc4 truly is.

[look here for gcc-3x]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=gcc-3&sourceid=mozilla-search")
They are all in main, no extra repositories needed.

Does slackware offer (good)dependency checking? does it download and install all the bits you need if they aren't there already? it's a different philosophy between debian/(k)ubuntu and slackware at least in terms of software packaging, thats what it all boils down to.[/QUOTE]

No, no, no... You got me wrong ;)
I am not talking about compiling D4X from source ;)
I am talking about installing it via apt-get/Synaptic/Adept...
It is in universe repository. See here:
[http://archive.ubuntu.com/ubuntu/pool/universe/d/d4x/](http://archive.ubuntu.com/ubuntu/pool/universe/d/d4x/)

So here we have 2.5.6 but Synaptic/Adept continue telling me that the latest available in the repos is 2.5.0
So like a Kubuntu newbie I decided to download this file:
[http://archive.ubuntu.com/ubuntu/pool/universe/d/d4x/d4x_2.5.6-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/d4x/d4x_2.5.6-1_i386.deb)
And to install in manually with the good old dpkg -i

And then... It said that it needs gcc 4.0.2 ;)
This idea still sounds crazy to me... To use a bug-free download manager you'll have to make a dist-upgrade
We are not talking about compiling from source. As a Kubuntu newbie I am trying to understand the idea of how it works. And this looks strange for me ;)
That's all...

---

### Post by claydoh on 2005-11-07
Ok, sorry about that, I assumed you were trying to compile it as it is so new :smile:

But my thoughts still are relevent, as this version is so new you won't find it in a lot of distros just yet. Never having used d4x before, I cannot say how buggy Breezy's version really is.

I find kget (which is in Universe) to be a very bug free downloader, though it probably only has 95% of d4x's features. It does offer resume and multiple connections. Why a download manager is not included on the cd is a good question , though.

---

### Post by Eckhard on 2005-11-08
[QUOTE=shinygerbil]You could make a CD of all the files you have stored in your cache - every .deb you dowload and install through any package manager is saved in the cache. You could burn them all to CD and you would then have an extra offline repository of apps with all the correct dependencies.

Steve[/QUOTE]

Better use apt-proxy to setup a local repository. Your client's sources list would then look something like this:
deb [http://your.server:9999/ubuntu](http://your.server:9999/ubuntu) ....

Works perfectly for my 3 machines -- only one copy of each paket is downloaded. However, your.server has to be running while the clients update...

---

### Post by kairu0 on 2005-11-09
[QUOTE=victorche]The whole Kubuntu idea has only one major problem.
It is on 1 CD only...
Well it is almost perfect... But the devs really should think about a second extraCD.
[/QUOTE]

I see this as a feature, not a problem.

The 1-cd thing was one of my attractions to Ubuntu in the first place. Suse has several, Mandriva has several, and, well, a complete Debian set could cover the side of a barn.

I like knowing that I can download 1-cd and get a general variety of popular desktop software. If I need anything else, it's in the repos. No CD swapping, no extra torrents to download.

---

