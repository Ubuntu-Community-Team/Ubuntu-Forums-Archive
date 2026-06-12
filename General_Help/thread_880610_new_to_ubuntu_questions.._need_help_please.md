---
title: "new to ubuntu questions.. need help please?"
date: 2008-08-05
forum: General Help
---

### Post by jakedubai on 2008-08-05
hi
how are you
so i installed ubuntu8.4.1 from wubi installer 
i had windows xp
everything is great but
i installed wine and when i wana open with ( wine ) most of the programs and games dont work .. how to fix that? or if there is a better way to run windows stuff in ubuntu? without re installind windows ! 
bcuz i tried to do it with win4lin so it was demo for 15 days and it didnt launch my own xp it asked me to put xp cd to re install it!
anyone know best way to run my own xp stuff in ubuntu without re installing?

another question

is there any online games for ubuntu? like the way in xp u know WOW this stuff??  if there is can you give me the link?  it would be better to have free online games :D

and where can i download real ubuntu games 
like games having amazing graphics and this stuff?

thnx in advance

---

### Post by jakedubai on 2008-08-05
oh i forgot 1 thing 

can i have a link to know most of the things in ubuntu?

you know to know how to work with everything? for starters?

---

### Post by /////// on 2008-08-05
WINE right now is probably the best way of running windows applications in Ubuntu. If the games/applications your trying to run don't require D3d, then you will most likely be able to get them to work in a Virtual Machine. Try VMWare Workstation or VirtualBox. If you have a game that WINE doesn't support and that requires Direct X 3D acceleration, then you won't be able to run it in Ubuntu unless you use Cedega which is a software which you'll have to pay for.

---

### Post by jakedubai on 2008-08-05
aha
thnx
ok so i tried normal game which was created on 2001 or 2002  using wine
no colors! only black and white!

and 
what is the best updates i should have them in my ubuntu?

and yeah sometimes i get error about insertin drive for amd64 somethin like that its an error while updating 
how to fix that?

thnx in advance

---

### Post by WRDN on 2008-08-05
> **jakedubai said:**
> aha
thnx
ok so i tried normal game which was created on 2001 or 2002  using wine
no colors! only black and white!

and 
what is the best updates i should have them in my ubuntu?

and yeah sometimes i get error about insertin drive for amd64 somethin like that its an error while updating 
how to fix that?

thnx in advance

What game are you referring to?

Also, what do you mean by "what is the best updates". You should use the latest version of Wine, which is available in the repositories. Unless you downloaded and installed from a website, its likely you have the latest version.

As for the last request, what is the exact error message, as people can't help much without it. If you are running a 64bit OS, you may have more issues than if using a 32bit OS.

---

### Post by jakedubai on 2008-08-05
i mean best updates for the ubuntu

and yes i have the latest version of wine

the problem is 

Please insert the disk labeled:
Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)
in drive /cdrom/

how can  i fix that?

how can i know if i have 64bit or 32bit?



ok and now i got new problem

i plugged my gamepad for playing games
but its not working.. ubuntu did recognize the device? and my gamepad if i plugged in it ( the light in it will turn on for few seconds ) but nothing

how to fix that?

---

### Post by WRDN on 2008-08-05
For Ubuntu, just install all updates from the Update Manager, you shouldn't have many/ any problems.
As for the error message, put the LiveCD in the disk drive, and click Continue/ the appropriate button. After viewing the message, the 32bit/ 64bit issues should no longer be relevant. As the error message says "amd64" it appears you have the 64bit edition of Ubuntu. To find what version you have, type the following command in the Terminal:

```
uname -a
```

> Linux Desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 **i686** GNU/Linux


The above is the result when I enter the command. The **bold** part tells you what architecture you are running on. "i686" and "x86" is a 32bit architecture, whilst "x86-64" is a 64bit architecture.

---

### Post by jakedubai on 2008-08-05
> **WRDN said:**
> For Ubuntu, just install all updates from the Update Manager, you shouldn't have many/ any problems.
As for the error message, put the LiveCD in the disk drive, and click Continue/ the appropriate button. After viewing the message, the 32bit/ 64bit issues should no longer be relevant. As the error message says "amd64" it appears you have the 64bit edition of Ubuntu. To find what version you have, type the following command in the Terminal:

```
uname -a
```



The above is the result when I enter the command. The **bold** part tells you what architecture you are running on. "i686" and "x86" is a 32bit architecture, whilst "x86-64" is a 64bit architecture.


ok 
thanks :D

i got this msg which im using 64bit i think

Linux-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux


so how can i fix the usb stuff?

---

### Post by linux_tech on 2008-08-05
Can you clarify what issue your having with  usb?

To find out the Kernel version of the Ubuntu release 
try using this command: 
 uname -r

Hardy Guide-  [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)
Troubleshoot USB issues - [https://help.ubuntu.com/community/Mount/USB?highlight=%28issues%29%7C%28usb%29%7C%28troubleshoot%29](https://help.ubuntu.com/community/Mount/USB?highlight=%28issues%29%7C%28usb%29%7C%28troubleshoot%29)
[https://help.ubuntu.com/community/UbuntuLTSP/TroubleShooting](https://help.ubuntu.com/community/UbuntuLTSP/TroubleShooting)

---

### Post by hyper_ch on 2008-08-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by Mgiacchetti on 2008-08-05
well seeing as how you have the 64 bit os.   i would like to tell you the only advantage to using a 64 bit os is the ability to use more than 4 gigs of ram

so unless your pc is a powerhouse, i would go with 32 bit ubuntu.

and just because you have a 64 bit processor, doesnt mean you cant use a 32 bit os.  windows xp was 32 bit unless it specifically said 64 bit edition.

now..
after you go to the 32 bit version of ubuntu

go to [wine HQ](http://www.winehq.org/site/download-deb) and make sure you are running the latest.  

you can also use [http://www.winehq.org](http://www.winehq.org) to see if whatever program you wish to use will work in wine, and how to if applicable.

---

### Post by jakedubai on 2008-08-05
aha

thnx 

so can i change my ubuntu from 64 to 32 without re installing?


and how can i run the xpenguins? 

i installed and installed the xpenguins-applet

how to make it work?

---

### Post by Mgiacchetti on 2008-08-05
me thinks you might have to go through setup. (reinstall)

if you have seperate partitons for  / and /home you should be in the clear.

---

### Post by jakedubai on 2008-08-05
so i have to re install ? :( 

ok ... thnx :D im downloading the 32bit right now :D

but how can i fix the usb? for gamepad? it doesnt recognize it:(

thnx for your help

---

