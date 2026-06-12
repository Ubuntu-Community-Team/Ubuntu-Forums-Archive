---
title: "Intel 536EP dial up modem"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by fairdoes on 2006-01-27
Having spent 30 hours failing to get a modem to work, I've uninstalled Ubuntu linux, re-installed Windows 98-SE and have to ask the same question again (again).

 For the 95% of the world that don't have more than one PC, and don't have broadband, and aren't software engineers, how do we perform the most obviously necessary task - installing a dial up modem?

 If this was moderately easy to do, 50% of the world would soon be using Ubuntu linux and the ethical, financial and freedom-generating consequences would be enormous.

 As things stand, an awesome and complete alternative to the immoral cartels that control internet use and software monopoly  has a social and political clout on a par with trainspotting.

 Where can I find non-geek, English instructions for getting the world's most common contemporary dial up modem to work on Ubuntu linux, please?

 In case it's not clear, a non-geek newbie that has just installed Ubuntu linux sees a desktop with a few links. Their only courses of action are to use a mouse or a keyboard.

 'Help' messages mid-way through the process that say 'to install your modem, visit this webpage' are not helpful.[-o<

---

### Post by az on 2006-01-27
There are two issues with dial-up modems.

1.  Their drivers are proprietary.  The ones that work are provided by the manufacturers and do not always run on the newsest kernels.  If there were free-libre drivers that worked, their integration into the kernel would assure that they always worked. 

2.  There are not enough people who use linux who are interested in developing their use.  For example, better dial-up support was a goal for Dapper.  This has been announced for months.  No one seems to be running with it.

It may very well be a chicken and the egg problem - software-modem users do not use linux because they have no working drivers.  Since they do not use it, there are not a lot of people who can hack existing problems...


In general, to compile a driver for your modem try:  (please understand that I do not own your hardware, so I don't yet know if this will work for you)

install build-essential from the cd.  You will also nee gcc-3.4 which is not on the cd.  This was an oversight.  The three packages are gcc-3.4 gcc-3.4-base and cpp-3.4.

You also need the linux-headers-2.6.12-9-386 package, which is on the cd.

You need to untar the source package you got from intel

tar xvzf intel*
cd intel*
sudo make
sudo make install


You can also try to use the sl-modem drivers - these often work for intel chipsets.

There is a prepackaged sl-modem-source deb in multiverse.

Please let me know if that worked.

---

### Post by mtron on 2006-01-27
detailed instructions: [http://www.ubuntuforums.org/showthread.php?t=82443](http://www.ubuntuforums.org/showthread.php?t=82443)

---

### Post by fairdoes on 2006-01-27
The 'detailed instructions' don't appear to be detailed instructions. unless i am supposed to commence installation by typing ** i am trued** which seems rather unlikely.

azz - thanks for the coherent reply. I'm sure i have the correct intel drivers, but the instructions with them are hopeless (and fail).

do you mean - install all 3 parts of **build essential**, if so,
a). where are they?
b). how do i install them?

where is ** multiverse** please.

---

### Post by ddtmsa on 2006-01-27
[QUOTE=fairdoes]The 'detailed instructions' don't appear to be detailed instructions. unless i am supposed to commence installation by typing ** i am trued** which seems rather unlikely.

azz - thanks for the coherent reply. I'm sure i have the correct intel drivers, but the instructions with them are hopeless (and fail).

do you mean - install all 3 parts of **build essential**, if so,
a). where are they?
b). how do i install them?

where is ** multiverse** please.[/QUOTE]

Fairdoes,
you've posted to other threads in the Desktop Support forum, please look at the replies posted there.

In reply to your questions

(a) The build-essential and linux-headers files are on the Ubuntu CD
(b) Open a Terminal window and type

sudo apt-get install build-essential

Together with the comparable command for the linux-headers file for your computer. For an Intel processor this should be

sudo apt-get install linux-headers2.6.12-9-386 

In particular, you will need to use the commands I suggested in the Desktop Support thread entitled 'Help with modem install please'  (which you have already contributed to) to load the necessary files to compile your own drivers.

---

### Post by fairdoes on 2006-01-30
Another 15 hours work. Every command followed to the T. Result = 'permission denied'.

Delete ubuntu, reinstall 98-SE etc.

On behalf of the 99.7% - Goodbye

---

### Post by ddtmsa on 2006-01-30
Sorry that you've given up trying. If you ever get broadband, please try again. From what I can discern, broadband internet access is usually fully automatically configured.

---

### Post by az on 2006-01-30
[QUOTE=fairdoes]Another 15 hours work. Every command followed to the T. Result = 'permission denied'.

Delete ubuntu, reinstall 98-SE etc.

On behalf of the 99.7% - Goodbye[/QUOTE]
It would be great if only a few more dialup modem users filed bugs....
[https://launchpad.net/malone/distros/ubuntu?field.searchtext=modem&search=Search&orderby=-priority%2C-severity](https://launchpad.net/malone/distros/ubuntu?field.searchtext=modem&search=Search&orderby=-priority%2C-severity)

---

### Post by towsonu2003 on 2006-01-30
not trying to flame and things like that. I truly understand the frustration. I just wanted to say 3 things:
1. run scanmodem tool and read modemdata.txt (I don't know what you did before, give link to your most recent and relevant modem question around here pls, or open up a new one and link here, or -better yet- attach your modemdata.txt here) for scanmodem, see 2nd link in my signature. 
2. dual boot (so you will boot to windows, download stuff, boot to ubuntu, run stuff, test connection, boot to windows, get more stuff etc. I don't think you can deal with a winmodem on a one-boot linux installation without alternative net connection)
3. I up your 30+15 hours to 3 months + ~6 distros during those 3 months (and my winmodem only works in ubuntu, no other distro at all)... I'd say you are lucky if you manage to get it to work in 1 week... 
[quote=azz]It would be great if only a few more dialup modem users filed bugs[/quote]
it's just too hard to post a bug report and follow it up for a system that cannot connect to net, and the frustration it creates really gets you worked up and angry for the whole thing...

PS. I gotta find a way to stick that bug search link to my signature... Edit: done.

---

### Post by az on 2006-01-30
[QUOTE=towsonu2003]
it's just too hard to post a bug report and follow it up for a system that cannot connect to net, and the frustration it creates really gets you worked up and angry for the whole thing...
.[/QUOTE]

It's a catch-22.  You need some success to further explore linux.  In this situation,  you tend to give up.  You wouldn't really know where to file a bug or care to.  I wasn't trying to be funny - people actually need to do this.

Many of these people find their way here.

The reality is that there is nobody intersted enough to do this work.  There was a push to find people to solve dialup issues before Hoary released and again before Breezy release.  The wiki pages are there, unassigned.  Nobody took it and ran with it.

How can we motivate some people with the neccessary skills to do something about it?

Example: the lucent modem was included in Hoary and sorta worked.  It is hopelessly broken in Breezy.

The original source for the ltmodem comes with scanmodem as well as a bunch of other tools.  That was stripped and is not shipped with ubuntu.  Someone needs to package it seperately from linux-restricted-modules.  It is a fair amount of work, but it does not seem to be rocket-science.

The multiverse repository and the linux-restricted-modules do away with most of the licencing issues, since many versions of these drivers are shippable, although not free-libre software.

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=azz]
How can we motivate some people with the neccessary skills to do something about it?
[/QUOTE]
agree with your post. 
pushes seems not to work, hence the general silence for/in the first link in my signature... May be the bug link will work? not too hopeful though...
As I say in that thread, ubuntu gotta "cont(**r**)act" linmodem people if it is possible.  that would solve a lot of dial up issues. ubuntu can say "we support linmodems" and linmodem people can just say "get ubuntu, apt-get this, it's solved". other distros will eventualy follow. 
Or we gotta find a developer who has a dial up modem and sees the importance. we won't have users from poorer countries / areas if this is not fixed. From a political point of view, this also makes ubuntu / linux problematic in issues of discrimination (race, ethnicity, nationality). 

Any news from the O(riginal)P(oster)?

---

### Post by carlmccall on 2006-01-30
I tried to Follow the SetUPModemWiki: and I think I got gcc 3.4 installed but when I got to Compile Modem Driver I got "Error 1" and "Please Install Kernal Source"

How do I do that?

Thank you

---

### Post by towsonu2003 on 2006-01-30
copy paste 
```
sudo apt-get install linux-headers-`uname -r`
``` should fix that. if it doesn't, do this as well ```
sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
``` after that, ```
ls /usr/src/linux
``` should show you some files / output. 

what you are doing is: 
1. get the linux headers (sort of kernel source, but not really the source itself) using apt-get so that driver can use them to compile
2. if the driver cannot find the source of kernel (headers in this case), link /usr/src(source)/linux with /usr/src/linux-headers-blabla so that it can find it easier. 

you can use ```
uname -r
``` to see which kerel you are using (just a note).

PS. I don't know the setupmodemwiki... can you give me a link (I'm curious)? check out the second link (dial up modem wiki) in my signature too if you'd like to...

---

### Post by fairdoes on 2006-02-02
> Any news from the O(riginal)P(oster)?

Yes! Some people have succesfully compiled and installed the intel536EP modem. For the whole world to gain internet access on Linux, we require one of these people to write the list of commands, and where they are typed, in layperson's language.

Question (from an ignorant non-techy!) - Does everyone need to compile the driver? Or can it be compiled once and installed by everyone that is using the same version of Ubuntu and the same modem? I only ask because I've installed a windows modem driver dozens of times, but never had to compile it (thank God/Godess/deity-of-choice-&-gender).:twisted: :confused: :D :KS 

P.S. The order of smilies is intended to be prophetic, but it's not in my hands ...

---

### Post by carlmccall on 2006-02-02
Thanks!

By the way: that second Link IS the Page I've been working from!

I'll try over again. (uname is a Command and not the variable for "Insert your username here", Right?)

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=fairdoes]
Question (from an ignorant non-techy!) - Does everyone need to compile the driver? Or can it be compiled once and installed by everyone that is using the same version of Ubuntu and the same modem? I only ask because I've installed a windows modem driver dozens of times, but never had to compile it (thank God/Godess/deity-of-choice-&-gender).:twisted: :confused: :D :KS 
[/QUOTE]
That should be possible. It is possible for packages, soit should be possible for drivers as well. your kernel version (see belov, uname -r) and distro (same filesystem, dependencies ok etc) should match afaik. the problem would arise from modem chips that differ even for the same model & make of the modem (can be checked by scanmodem tool). these commands compile and build a deb to install ```
./configure
make
sudo make checkinstall
``` you'll have to apt-get checkinstall bf this, which should be in the install cd (offline). 
[quote=carlmccall]uname is a Command and not the variable for "Insert your username here", Right?[/quote] uname is a command and uname -r shows your kernel version. you can check man uname (two words toghether as a command which will show you the man-ual- page of uname) for more info. 

when you use uname as the following ```
sudo apt-get install linux-headers-`uname -r`
``` apt-get will get the linux-headers that are built for your kernel version. 
so for example, **my** uname -r is the following:
> 2.6.12-10-686

so the linux headers package appropriate for **my** kernel is > linux-headers-2.6.12-10-686


Oh I almost forgot:
[quote=carlmccall]that second Link IS the Page I've been working from![/quote]
heheh lol :)

---

### Post by ddtmsa on 2006-02-02
[QUOTE=fairdoes]Question (from an ignorant non-techy!) - Does everyone need to compile the driver? Or can it be compiled once and installed by everyone that is using the same version of Ubuntu and the same modem? I only ask because I've installed a windows modem driver dozens of times, but never had to compile it
[/QUOTE]

I'm sure that you could download a compiled driver for an Intel 536EP modem for your particular kernal e.g. 2.6.12-9-386. However I have an Intel 537EP modem and use the 2.6.12-10-386 kernal. When you think of all the combinations of kernals and modems (with all the different manufacturers), then we are heading for a large list of options, which becomes obsolete everytime a kernal update is provided. 

But then it gets difficult, in that you will then have to copy it and link to the /dev/modem file, not that this is especially difficult. But if you are not an ubuntu guru (and I'm certainly not one of those, who got online with my winmodem) it is much easier to follow a faq and compile your own driver in the right place following Intel's directions.

ps The problem is that winmodems require software built into windows to work (for the paranoid, this is all part of Bill Gate's plan to take over the world ... think of Pinky and the Brain cartoons :-) ) mainly because the modem manufacturers didn't consider the possibility that users would want to run any other operating system

---

### Post by fairdoes on 2006-02-03
Thanks for all the feedback.

 I have voted for the modem support to be included.
 
 I'll print all this advice and aim to suceed over the next year or two (!).

 It seems to me there is money to be made if someone manufactures a dial up modem for linux ...

 > ps The problem is that winmodems require software built into windows to work (for the paranoid, this is all part of Bill Gate's plan to take over the world...) 

 I don't think this is a paranoid view! Re-inventing slavery is very popular, and always has been. I'm just disappointed that it's still apparently legal.

 Is there a non-MicroLimp dialup modem I can use - PCI, USB, stick on with blutack or whatever, 'cos the MicroLimp empire of Gill Bates is P'ing me off. I'm trying to bear in mind the dozens of excellent applications that ubuntu includes that I'll be able to recommend to everyone once the modem issue is sorted.

---

### Post by fairdoes on 2006-02-06
>
>
>
>IMPORTANT - I've found all the mistakes in the modem Howto - it now takes 15 minutes to install a 536ep modem, and the world's forums are full of people spending months of frustration failing to do so. I've tested the install on FIVE neighbours' computers and it worked first time, every time, and took 15 minutes.

The crucial errors are the guide to a terminal (it's under accessories)

and there are four typing errors in the 3 lines that quote what the user should type to install the modem - the underscore character is replaced by a space.

Please can someone correct this then everyone can use their 536ep dial up modems.

 thank you.

---

### Post by newuser111 on 2006-02-06
intel has been pretty supportive of linux that being said even the intel site says your modem works in linux

[http://www.intel.com/design/modems/products/536ep.htm](http://www.intel.com/design/modems/products/536ep.htm)

"Supports Windows 95, 98, ME, NT4.0, 2000, XP and Linux*"

---

### Post by fairdoes on 2006-02-06
Yes, the modem does work - the ubuntulinux.org dialupmodemHowto needs correcting.

I've sent them an email, but haven't heard back yet.;)

Thanks again for previous help. I hope to join in on the helping side, as soon as I understand anything ... ;)

---

### Post by towsonu2003 on 2006-02-06
[QUOTE=fairdoes]Yes, the modem does work - the ubuntulinux.org dialupmodemHowto needs correcting.

I've sent them an email, but haven't heard back yet.;)

Thanks again for previous help. I hope to join in on the helping side, as soon as I understand anything ... ;)[/QUOTE]
You can just register and correct it yourself (this is the ubuntu wiki page, right? 2nd link in my signature? if yes, just register and correct the mistake ;) ).

---

### Post by fairdoes on 2006-02-07
Thanks for the link - will do.:KS

---

