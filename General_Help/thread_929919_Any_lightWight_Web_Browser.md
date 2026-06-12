---
title: "Any lightWight Web Browser"
date: 2008-09-25
forum: General Help
---

### Post by zohaib on 2008-09-25
Helo Friendz.., I've been using firefox from the day I Installed Ubuntu.,
and I'm facing many problems., one of them is that it plays youtube or any other videos From the Internet very slowly [That's major problem I'm facing] So I wanna get rid of all this., I just want to know a name of any browser which is user friendly n very light enough to play videos without being hanged second after second..,
and also I need Link

Thanks.

---

### Post by Cifra on 2008-09-25
Try Opera or Konqueror. They retain many features, but are a little bit lighter on resources.

---

### Post by Ryadt on 2008-09-25
Give Seamonkey a try.

---

### Post by zohaib on 2008-09-25
yea i tried opera but it doesnt install the flash player by itself.,
thats the problem

so no flash player no videos :(

never heard about konqueror

let me try it

but thanks for giving ur precious time

---

### Post by zohaib on 2008-09-25
> **Ryadt said:**
> Give Seamonkey a try.

yea will also try that one

thanks:)

any link do u have of this browser from where i can download it?

---

### Post by EvilRobotDrew on 2008-09-25
open terminal, type:

sudo apt-get install seamonkey

and that should do it

---

### Post by Ryadt on 2008-09-25
> **zohaib said:**
> yea will also try that one

thanks:)

any link do u have of this browser from where i can download it?

It's in the repos.```
sudo apt-get install seamonkey
```Or go in add/remove and look for seamonkey.

---

### Post by zohaib on 2008-09-25
> **EvilRobotDrew said:**
> open terminal, type:

sudo apt-get install seamonkey

and that should do it

yea i tried that in terminal it says the package is not avialable., so any other way..

or can i install konqueror in that way?

thanks:)

---

### Post by Dr Small on 2008-09-25
Dillo, anyone?

---

### Post by Sycron on 2008-09-25
Yes, you can. ```
sudo apt-get install konqueror
``` Also make sure that you have the latest video drivers and in the case that is still sluggish deactivate compiz fusion.

> Dillo, anyone?
Hey, I use that on my 486. So fast...

---

### Post by zohaib on 2008-09-25
> **Sycron said:**
> Yes, you can. ```
sudo apt-get install konqueror
``` Also make sure that you have the latest video drivers and in the case that is still sluggish deactivate compiz fusion.


Hey, I use that on my 486. So fast...

ok let me try it

---

### Post by zohaib on 2008-09-25
> **Ryadt said:**
> It's in the repos.```
sudo apt-get install seamonkey
```Or go in add/remove and look for seamonkey.

yes i searched it on add/remove seamoneky isn't avialable there either

konqueror is in progress., hope it will work for me

---

### Post by Nepherte on 2008-09-25
Epiphany, Kazehakase, Midori (can all be used with webkit).

---

### Post by Ryadt on 2008-09-25
Have you got universe enabled in the repos. Check in Software sources.

---

### Post by zohaib on 2008-09-25
yea konqeror has been installed succsefully

now im donwloading flash player it ask that select the version to download.,
3 versions are avialable

tar.gz

yum

rpm


which one do i have to select



thanks everyone for the support

---

### Post by snowpine on 2008-09-25
> **zohaib said:**
> yea konqeror has been installed succsefully

now im donwloading flash player it ask that select the version to download.,
3 versions are avialable

tar.gz

yum

rpm


which one do i have to select



thanks everyone for the support

None of the above. Open a terminal (Applications->Accessories) and type:

```
sudo apt-get install flashplugin-nonfree
```

Perhaps that is part of the problem in the first place. :)

---

### Post by zohaib on 2008-09-25
> **Ryadt said:**
> Have you got universe enabled in the repos. Check in Software sources.

yes universe is checked in software sources

i searched seamonkey in synaptic manager., it doesn't exist there either

any other way to install seamonkey?

---

### Post by zohaib on 2008-09-25
> **snowpine said:**
> None of the above. Open a terminal (Applications->Accessories) and type:

```
sudo apt-get install flashplugin-nonfree
```

Perhaps that is part of the problem in the first place. :)

thank u very much friend
im sure thats really gonna help me out of this problem.,

---

### Post by zohaib on 2008-09-25
> **snowpine said:**
> None of the above. Open a terminal (Applications->Accessories) and type:

```
sudo apt-get install flashplugin-nonfree
```

Perhaps that is part of the problem in the first place. :)

yes i tried that now in terminal it says "Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
flashplugin-nonfree set to manual installed.
The following packages were automatically installed and are no longer required:
  libgtk-jni libcairo-java libglib-java python-wxversion imlib-base
  libswt3.2-gtk-jni libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

nothing else happens., wat does that mean?

---

### Post by oldsoundguy on 2008-09-25
As an aside on this topic .. could be that FF is not the issue.  I updated Flash to the 10 beta and lots of problems went away in FF as far as the streaming stuff from YouTube and similar.

---

### Post by snowpine on 2008-09-25
> **zohaib said:**
> yes i tried that now in terminal it says "Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
flashplugin-nonfree set to manual installed.
The following packages were automatically installed and are no longer required:
  libgtk-jni libcairo-java libglib-java python-wxversion imlib-base
  libswt3.2-gtk-jni libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

nothing else happens., wat does that mean?

That is good news, you already have Flash. :)
I'm sorry but I've never used Konqueror, so I don't know why it is asking you to download Flash when you already have it installed. :(

---

### Post by zohaib on 2008-09-25
> **snowpine said:**
> That is good news, you already have Flash. :)
I'm sorry but I've never used Konqueror, so I don't know why it is asking you to download Flash when you already have it installed. :(

yea it also asked for flash in opera.,i think this flash only supports firefox.,

any other solution?

---

### Post by zohaib on 2008-09-25
> **oldsoundguy said:**
> As an aside on this topic .. could be that FF is not the issue.  I updated Flash to the 10 beta and lots of problems went away in FF as far as the streaming stuff from YouTube and similar.

hmmm that sounds kool.,, but hey how can i update my flash.,
but the flash im using is dumb., it only supports firefox:(

how can i get good flash player which can support all browsers

---

### Post by zohaib on 2008-09-25
helo

so wat do u think guyz wats the problem with flash player im using?

---

### Post by Cifra on 2008-09-25
> **zohaib said:**
> helo

so wat do u think guyz wats the problem with flash player im using?

Try copyying the file flashplugin (or something like that).so from Mozilla's plugin folder to Oper'as or Konqueror's plugin folder.

---

### Post by zohaib on 2008-09-25
> **Cifra said:**
> Try copyying the file flashplugin (or something like that).so from Mozilla's plugin folder to Oper'as or Konqueror's plugin folder.

ok but where can i find that plugin folder?

---

### Post by kerry_s on 2008-09-25
> **zohaib said:**
> Helo Friendz.., I've been using firefox from the day I Installed Ubuntu.,
and I'm facing many problems., one of them is that it plays youtube or any other videos From the Internet very slowly [That's major problem I'm facing] So I wanna get rid of all this., I just want to know a name of any browser which is user friendly n very light enough to play videos without being hanged second after second..,
and also I need Link

Thanks.


okay, since nobody's asked yet.

what are your system specs?
what kind of internet connection do you have?

---

### Post by Cifra on 2008-09-25
> **zohaib said:**
> ok but where can i find that plugin folder?

should be

/usr/lib/mozilla/plugins/

Here is more info for Opera:
[I]
You can go to Tools/Preferences/Advanced in Opera and highlight

applicationx/shockwave....swf

and click edit and change the path to

user/lib/flashplugin-nonfree

This will work for both i386 and amd64 versions of Opera. If you direct the search to firefox-addons in amd64 it will link to npwrapper.flashplayer.so and Opera9.50 does not need the wrapper to use flash on amd64 so it should be linked directly.

You can get flash10b from the adobe website and unpack the download and put libflashplayer.so the directory mentioned above. The installer will try to put it in the wrong place for Ubuntu and complicate any future updates.[/I]
[http://ubuntuforums.org/showthread.php?p=5282541](http://ubuntuforums.org/showthread.php?p=5282541)

---

### Post by zohaib on 2008-09-25
> **Cifra said:**
> should be

/usr/lib/mozilla/plugins/

Here is more info for Opera:
[I]
You can go to Tools/Preferences/Advanced in Opera and highlight

applicationx/shockwave....swf

and click edit and change the path to

user/lib/flashplugin-nonfree

This will work for both i386 and amd64 versions of Opera. If you direct the search to firefox-addons in amd64 it will link to npwrapper.flashplayer.so and Opera9.50 does not need the wrapper to use flash on amd64 so it should be linked directly.

You can get flash10b from the adobe website and unpack the download and put libflashplayer.so the directory mentioned above. The installer will try to put it in the wrong place for Ubuntu and complicate any future updates.[/I]
[http://ubuntuforums.org/showthread.php?p=5282541](http://ubuntuforums.org/showthread.php?p=5282541)

let me explain some more about it., today I've downloaded n Installed opera 9.52 and i also downloaded flash player 10 from here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) 

But when I copy this file libflashplayer.so which is located in flash player folder n try to paste it in this location usr/lib/flashplugin-nonfree., when i right click to paste it., it doesn't paste it., in opera i clicked on tools n then preferences n then went to advance, But in advance menu i cant see anything like  applicationx/shockwave....swf. n how can i change the plugins option in firefox so that it re-download all the plugins to this location usr/lib/flashplugin-nonfree.

thanks everyone any type of help will be appriciated  I've been trying to fix this problem from yesterday but now it feels like I did everything for nothing:(

---

### Post by Sycron on 2008-09-26
Anyone tried Dillo ?

---

### Post by kevinmchapman on 2008-09-26
Yes, I love Dillo, especially the i18 version with tabs. It doesn't really work with a lot of sites, though, so you would need another browser for flash and frames. Where it does work, however, it is in another league in terms of speed.

---

### Post by Sycron on 2008-09-26
Hmm. Dillo support Javascript ? I wonder if I can use it to post on ubuntuforums.org.

---

### Post by Sycron on 2008-09-26
Well, it doesn't work.

---

### Post by zohaib on 2008-09-26
yea dillo cant be installed from terminal[:(
don't know wats wrong
any other solution sir?

---

### Post by Sycron on 2008-09-26
```
sudo apt-get install dillo
``` That's how I installed dillo, lol .

---

### Post by zohaib on 2008-09-26
> **Sycron said:**
> ```
sudo apt-get install dillo
``` That's how I installed dillo, lol .

yea i tried that in terminal it says "Reading package lists... Done
Building dependency tree       
Reading state information... Done
dillo is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtk-jni libcairo-java libglib-java python-wxversion imlib-base
  libswt3.2-gtk-jni libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

but i never installed dillo so why it says that??

---

### Post by Sycron on 2008-09-26
Type in a terminal: ```
dillo
```.

---

### Post by zohaib on 2008-09-26
> **Sycron said:**
> Type in a terminal: ```
dillo
```.



yea i did that in terminal another window appears., its name is "splash screen for dillo"

wats that

sorry for the late reply i waz bit bizy.

---

### Post by Sycron on 2008-09-26
Run these command in the order they apear.
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get remove dillo
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dillo
```

---

### Post by zohaib on 2008-09-26
> **Sycron said:**
> Run these command in the order they apear.
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get remove dillo
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dillo
```

yea i did that respectively., now wats the next step?

---

### Post by snowpine on 2008-09-26
> **zohaib said:**
> yea i did that respectively., now wats the next step?

type ```
dillo
```

:)

---

### Post by zohaib on 2008-09-26
> **snowpine said:**
> type ```
dillo
```

:)

yea i already did that ., again did that another window appears.. name is splash screen for dillo

---

### Post by Sycron on 2008-09-26
It's very strange. My dillo installation worked out of the box.

---

### Post by zohaib on 2008-09-26
hey surprisingly n fortunately my firefox works fine today., it plays videos without being hanged or slow as compared to yesterday.:)

so i guess no need install another browser now

---

### Post by zohaib on 2008-09-26
thanks for the response u gave guyz,., highly appreciated.,

whoever contributed in this thread i just wanna say thank u all from the bottom of my heart.,

my problem have been solved., now i fugure out wat was the problem not so sure about it

now this is wat i did., i have been trying new browsers n new softwares from yesterday to fix this problem., accidently I opened google n searched for latest flash player i downloaded flash player 10 n ran it with terminal installation completed successfuly., i didnt know that up untill now., but moments ago i opened youtube n played a video it played it so clearly as it used to play on intrernet explorer when I was using windows.,

so If u want to play youtube videos very clearly or from somewhere else on the net You should have the latest version of Flash player., no matter what browser are u using., latest flash player is the key

thats what i think the solution is.,:guitar:

---

### Post by Sycron on 2008-09-26
I have the latest flash player on my eeepc and it's wacky.

---

### Post by Cifra on 2008-09-28
> **Sycron said:**
> Anyone tried Dillo ?

I hear DIllo doesn't handle advanced CSS very well :(

I use Kazehakase at the moment

---

