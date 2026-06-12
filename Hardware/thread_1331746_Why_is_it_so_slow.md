---
title: "Why is it so slow?"
date: 2009-11-19
forum: Hardware
---

### Post by headshotaof on 2009-11-19
Hello,

I have two questions.

1. I upgraded to 9.10 and it takes longer to load the operating system. And it takes a really long to to open applications and at least 15 seconds to browse between web pages that are not related to each other. For example if I am on here and i click forums---->general help. It loads instantly. But if i am on here and i type in youtube.com or google.com or microsoft's website ...etc...it will take at least 15-25 seconds

What i did. I put back in my 9.04 disk and zapped the 9.10 off the HDD. I am back on jaunty now. It had nothing to do with my internet speed because it was shown as excelent connection. Right now i am on "good" connection which is slower than excelent and it is loading everything instantly there is no wait time period.

2. On 9.04 i am unable to play any type of flash game or a game that takes any type of graphics output. I am using an older card , ATI X1600 Pro Series. I am able to play just about any game on windows with it. But no games whatsoever on here. I am able to use compiz fusion and run animations and what not. I did not download any drivers at all everything on that end is default. I just did a fresh install. It was working last time though. It is to my undestanding that there is no support for the ATI X series on linux anymore but that still should not prevent me from playing a simple flash game.

Thanx for the help.

---

### Post by wojox on 2009-11-19
Since wear zapping, why don't we zap a fresh install of 9.10?

---

### Post by doas777 on 2009-11-19
> **headshotaof said:**
> Hello,

I have two questions.

1. I upgraded to 9.10 and it takes longer to load the operating system. And it takes a really long to to open applications and at least 15 seconds to browse between web pages that are not related to each other. For example if I am on here and i click forums---->general help. It loads instantly. But if i am on here and i type in youtube.com or google.com or microsoft's website ...etc...it will take at least 15-25 seconds

What i did. I put back in my 9.04 disk and zapped the 9.10 off the HDD. I am back on jaunty now. It had nothing to do with my internet speed because it was shown as excelent connection. Right now i am on "good" connection which is slower than excelent and it is loading everything instantly there is no wait time period.

2. On 9.04 i am unable to play any type of flash game or a game that takes any type of graphics output. I am using an older card , ATI X1600 Pro Series. I am able to play just about any game on windows with it. But no games whatsoever on here. I am able to use compiz fusion and run animations and what not. I did not download any drivers at all everything on that end is default. I just did a fresh install. It was working last time though. It is to my undestanding that there is no support for the ATI X series on linux anymore but that still should not prevent me from playing a simple flash game.

Thanx for the help.

have you reinstalled flash and codecs?
the first thingsi do on a build are enable the medibuntu repos, and install the ubuntu-restricted-extras package.

---

### Post by headshotaof on 2009-11-19
Yes my mistake i missed that part. When i had 9.04 and wanted to get 9.10 i installed it from the update box. That is the first way i installed it. It was succesfull the only error was  usual mscorefonts error which i see almost everyone got. But i did not think that would hurt anything so i did not bother with it. 

I then took my disk and tried to install ubuntu 9.10 from the disk but it would just go to the install screen and i click install and it just goes to a black screen with a blinking __ command line. That does not let me type anything. It does this on disk error check and also on the live cd.

I will download it to disk again and see if it works one more time.

FLASH: Yes i have flash installed and no i do not have the extras installed i will start that now. Lets see if that helps.

---

### Post by headshotaof on 2009-11-19
Well, i have gnome codecs installed, i have flash installed, and the extras installed. Flash player for game is still lagging horribly. 

I also tried hulu and the video does not even show up

On youtube i try to play the video and it says it needs to search for the right plugins and it searches and says it comes up with nothing it needs an mpeg aac converter. 

Man ubuntu was easy to use last time i dont know what i am missing this time.

$ sudo apt-get remove --purge flashplugin-*
$ sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
$ sudo apt-get install flashplugin-nonfree

Ok so i tried this, it is now letting me view youtube BUT it is lagging just like the flash games. So now i can access the video i just cant watch it.

---

