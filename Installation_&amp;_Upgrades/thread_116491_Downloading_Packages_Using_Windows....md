---
title: "Downloading Packages Using Windows..."
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by hk_2999 on 2006-01-12
I have no internet connection, and I download from a netcafe and burn cds and put them there. The cafe uses windows ( 98 ). 

And im tired of clicking THOUSANDS of things in packages.ubuntu.com that sometimes my system already has that package but I still download it just to be sure! 

Can anyone advice me on how to do this easier. eg. aptitude/synaptic for windows that'll just fetch the package for me(and maybe check if i already have it using a file i'll put) or maybe someone could just put dates on the packages on the website, so i wont waste time having to download packages i already have.

---

### Post by rykel on 2006-01-12
[QUOTE=hk_2999]I have no internet connection, and I download from a netcafe and burn cds and put them there. The cafe uses windows ( 98 ). 

And im tired of clicking THOUSANDS of things in packages.ubuntu.com that sometimes my system already has that package but I still download it just to be sure! [/QUOTE]


I used to have the same problem, and still do, but have found a way to resolve it...
[INDENT]
1. Use **autopackages**! (see [http://www.autopackage.org](http://www.autopackage.org)) You do not have to bother with downloading essential programs such as Gaim, AbiWord, Scribus, GIMP etc. from ubuntu.com since their self-contained autopackages are available.

2. Get hold of someone with a Ubuntu system, and download all the programs you want through Synaptic. Ensure that the downloaded packages are kept in the Synaptic cache. (go through the Options menu to enable this feature)

Thereafter, copy all the downloaded debs from /etc/cache/apt/archive (this address might be wrong! just do a search for the folder where all the debs were stored) onto ur cd/dvd and there u have them![/INDENT]

hope that helps.

---

### Post by hk_2999 on 2006-01-13
Thank for the reply, but actually, the problem isn't downloading big packages one by one, it's *dependencies*. I mean, the world of open-source changes so rapidly, when I want to download a game or program, I almost always find out that my libraries are old.

And none of my friends who have a net connection have ubuntu installed. 

Also I have tried autopackage before, but same thing. The dependencies are settled using a net connection. So I still have to fetch them when I miss something. And since in Linux dependencies codepend so much in each other i'll download like 10 files before i get the apps to work. And if I miss some deps again, i'll fill my room with cds more then.

My theoretical solution is that to build a synaptic/aptitude/apt-get thing in windows/dos to ease this, but i'm checking for other ideas before I start planning to program this kind of stuff. Also, a date updated function in the ubuntu packages website (packages.ubuntu.com) could ease things up if I'l download em manually, or maybe they should just include a download w/ dependencies button - much easier to implement but might make a small load in the server.

---

### Post by sterling on 2006-01-13
I agree and have the same problem having a dead slow internet connection at home and able to download larger files only in the office where I cannot install Ubuntu. The first impression I had of Ubuntu was extremely positive - hot plugs USB, relatively easy to install, free etc. and Ubuntu being an African word I thought this might finally be the distro suitable for here (Zimbabwe). But the need for a fast internet connection to update or install new software is making the use impossible. Mirroring the entire repository of several GB as described in the forum is not a possibility and trying to distribute as is with Totem crashing with even mpeg files and the modem dial up hidden in root administrative issues does not seem to be a feasible option. 
Any suggestion for a solution would be appreciated.

Thomas

---

### Post by hk_2999 on 2006-01-16
Nice to know there are other people with these similar problems.

Ok, i'll start planning a program that'll ease downloading packages from windows. Don't know how long it will be before I can release it, anyway, if you've got similar problems or solutions, please post here, i need some inspiration someway...

---

### Post by mental_noise on 2006-02-27
i have the same problems too. i have a very slow internet connection at home and it is running windows os. i have always wanted to download debs and it's dependencies and then i find out that the dependencies also have dependencies. it's too tiring to download them one-by-one.

it would be a relief if you had a web-based, one-click downloading tool that can get the main package, it's dependencies, it's dependencies' dependencies and etc.

---

