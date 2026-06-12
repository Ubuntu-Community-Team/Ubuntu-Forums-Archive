---
title: "xubuntu install with unetbootin, stuck"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-08-23
hello all
i'm in japan for a couple of weeks, and bought a second hand mini pc, a kohjinsha with an AMD geode processor and 512mb of ram. but i've been struggling with the xubuntu 9.04 install. the computer doesn't have a cd drive, and it's hard to get it online where i am

however i do have access to another computer with internet access, and a pen drive.
so i downloaded both the xubuntu desktop install and the alternate install, and tried to install a version from the pen drive, using unetbootin

the alternate version gets stuck on the CD drive issue, it cannot find one even if i suggest dev/sdb , no go. after some browsing i've read that the desktop version should be used.
tried this, and things went differently, i got a xubuntu loadingbar and then nothing.
the display went black and stayed that way.

is there anything i could or should try ? i also tried pendrive linux but the drive's letter wasn't recognized, probably due to the fact that both computers are running a japanese windows xp.

thanks in advance for your help

ben

---

### Post by dk06 on 2009-08-23
> **bjaz said:**
> hello all
i'm in japan for a couple of weeks, and bought a second hand mini pc, a kohjinsha with an AMD geode processor and 512mb of ram. but i've been struggling with the xubuntu 9.04 install. the computer doesn't have a cd drive, and it's hard to get it to connect where i am

howeverm i do have access to another computer with internet access, and a pen drive.
so i downloaded both the xubuntu desktop install and the alternate install, and tried to install a version from the pen drive, using unetbootin

the alternate version gets stuck on the CD drive issue, it cannot find one even if i suggest dev/sdb , no go. after some browsing i've read that the desktop version should be used.
tried this, and things went differently, i got a xubuntu loadingbar and then nothing.
the display went black and stayed that way.

is there anything i could or should try ? i also tried pendrive linux but the drive's letter wasn't recognized, probably due to the fact that both computers are running a japanese windows xp.

thanks in advance for your help

ben

If you haven't already, try checking the integrity of your download and CD/USB. 

If the Alternate disk gets stuck, I'm guessing either you have a bad burn or a bad download.

You can check the MD5 when you download it easily with a Firefox extension called DownThemAll ...you just put in the checksum at the time you tell it to download and it checks it for you

Hope this helps,

Don

____________________________
edit: adding

DownThemAll also speeds up your download a lot... makes downloading ISOs not such a big deal when you can get 700mb in 15minutes (also depends on connection speed)

________________________________
I'm not sure what to tell you on the rest of the issues but maybe this will help:
[http://ubuntuforums.org/showthread.php?t=203732](http://ubuntuforums.org/showthread.php?t=203732)
[http://www.ubuntulinux.jp/](http://www.ubuntulinux.jp/)

&
You may be able to pick up an inexpensive USB Wifi dongle for surfing while you're over there, I know they use a different frequency.

---

### Post by bjaz on 2009-08-23
thanks for your answer.
i don't have a cd, just downloaded the iso files using bittorrent.
i'll try to see how i can check the iso's, this is a japanese windows running pc, not the easiest.

the main issue was that it was geting stuck looking for a cd drive, when i'm trying to install from a usb live made with unetbootin

i can't get past the "no common cd rom drive was detected". 

should i be focusing on the desktop iso or the alternate iso to make the usb live cd ? 

i'm trying again using the desktop version.
i get to pointer which bounces back and forth, then slowly, then the display goes black...the little light on the pen drive stops blinking

thanks



b

---

### Post by apparle on 2009-08-23
I have heard that alternate install via USB in very difficult.
Stick with the Desktop CD ISO.
To check the md5 sum from ISO image
you can use [http://www.nullriver.com/downloads/Install-winMd5Sum.exe](http://www.nullriver.com/downloads/Install-winMd5Sum.exe)

---

### Post by bjaz on 2009-08-23
thanks.
i did a checksum, redowloaded the desktop version, checked that and used unetbootin to make a usb live.
got the same point, the xubuntu logo with the pointer bouncing, then nothing, black screen.

anything i could try ?

---

### Post by apparle on 2009-08-23
You can try the safe graphics mode by pressing F4 on the boot menu (just after the unetbootin menu) (see the attachment)
Though I am not sure if you get the normal boot menu because of unetbootin.

Maybe its because graphics card in your PC may not be supported.
ATI cards give a lot of trouble.

And you can try Ubuntu Desktop version also.
Because I have heard that Ubuntu runs usually where Xubuntu runs.

And I myself have used Ubuntu on 512MB RAM for about an year.
I suggest you try ubuntu.........it will run fine (personal experience). Just disable the desktop effects

---

### Post by bjaz on 2009-08-30
thanks, i'm back home now, with a USB cd drive and a live cd
yet the screen still goes black.
the maching is a kohjinsha SAF100,
 [http://www.biztoolbelt.com/2006/12/kohjinsha_sa1f00_umpc.html](http://www.biztoolbelt.com/2006/12/kohjinsha_sa1f00_umpc.html)

i'm starting to wonder if i'll be able to install xubuntu on this machine or if i'm doomed to use the japanese windows XP....
b

---

### Post by bjaz on 2009-09-01
> **apparle said:**
> You can try the safe graphics mode by pressing F4 on the boot menu (just after the unetbootin menu) (see the attachment)
Though I am not sure if you get the normal boot menu because of unetbootin.

Maybe its because graphics card in your PC may not be supported.
ATI cards give a lot of trouble.

And you can try Ubuntu Desktop version also.
Because I have heard that Ubuntu runs usually where Xubuntu runs.

And I myself have used Ubuntu on 512MB RAM for about an year.
I suggest you try ubuntu.........it will run fine (personal experience). Just disable the desktop effects


i'm trying with ubuntu in safe graphic mode but the screen stil goes black after the ubutu loading bar. i opened up an other thread and am not getting any answers. windows won't boot anymore, and japanese pc's don't come with cds to reinstall apparently, simply a user licence code...pretty stuck here...

---

### Post by jackng on 2009-10-25
I was able to install Ubuntu 8.01 on the Kohjinsha SAF001 previously and the display is fine. 

I have just tried Ubuntu 9.04 Desktop edition and encountered the blank screen problem, same as you. However, I'm able to boot up the same CD from a Dell laptop from which I'm posting this. I stumbeld upon this forum while researching the SAF100 screen display problem.

I'm not familiar with Ubuntu or Linux to solve this myself but obviously Ubuntu 8.01 came with the right display driver for the Kohjinsha SAF100 so you may wish to follow up from there. 

Do post your soluion if you manage to solve this because I'm interested to get Ubuntu 9.04 on my Kohjinsha.

Cheers

---

