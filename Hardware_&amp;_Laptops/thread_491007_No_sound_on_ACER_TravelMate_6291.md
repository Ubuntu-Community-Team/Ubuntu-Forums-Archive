---
title: "No sound on ACER TravelMate 6291"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by qrwe on 2007-07-03
Hello,

As referred by the heading, I've just purchased an ACER TravelMate 6291 laptop. 
First of all a little glorifying of Ubuntu: It came with a Windows Vista installation, which I quickly wiped from the drive to install Windows XP instead. However, it also came with a SATA harddrive. No problem: just download the separate driver from the homepage. After purchasing a floppy drive to have a chance of using this driver at all *sigh*, I realized that it didn't work. OK, back to Vista again: it wanted me to provide a separate SATA driver, which was not available for Vista (wait a minute..), so I tried with the Windows XP driver again. Nope, bad luck also..
Finally, I went on with Ubuntu. A few clicks later, the computer was ready for use. TA-DA! :)

..almost. The sound card doesn't work. I tried to switch from 'Auto detect' to 'ALSA' in the sound configuration GUI and so on, but nothing haqppened. Is there any TravelMate users out there having the same problem? Please reply if you want other specifications.

Kind regards!

---

### Post by DaveB05 on 2007-07-03
I do not think it is your computer.  i have the same problem on my new toshiba.  i have tried several forums and lots of people are having the same 'no sound' problems.  Unfortunately all the lines of help die out with no solutions.  If I find anything I will let you know.

Dave

---

### Post by DaveB05 on 2007-07-03
I just found this but have not tried it yet - giveit a go and see what happens.

Someone else just got his sound card working and this is what he wrote:

I found the solution here:  [https://bugtrack.alsa-project.org/al...ew.php?id=3165](https://bugtrack.alsa-project.org/al...ew.php?id=3165) .  Just sign in as guest to view the forum.

Kentrosaurus gives his solution and links to where he found it...download the newest alsa driver, utils and library (I used 1.0.14rc4), replace hda_proc.c and patch_realtek.c from realtek10.tar.gz (on the page Kentrosaurus linked to pshou explains how to do this).

Insert the line "options snd-hda-intel model=toshiba" on the end of /etc/modprobe.d/alsa-base.  Finally, compile the driver using the directions here:  [https://help.ubuntu.com/community.HdaIntelSoundHowto](https://help.ubuntu.com/community.HdaIntelSoundHowto)  .

I have not tried this yet myself but I thought you would like to know.

Good luck!!

Dave

---

### Post by ppm1949 on 2007-07-03
those two links do not work

---

### Post by jlh68 on 2007-07-03
I found on my Acer TravelMate 2480 that If I go to the sound panel and unmute and push up the "Surround" slide that I now have sound.

---

### Post by jlh68 on 2007-07-03
BTW I am using 7.04 Ubuntu.

---

### Post by ugm6hr on 2007-07-04
> **jlh68 said:**
> I found on my Acer TravelMate 2480 that If I go to the sound panel and unmute and push up the "Surround" slide that I now have sound.
Acer Aspire 5150 Laptop is the same: headphones are "centre" speaker and main speakers are "surround".  Also, the kernel update (from 2.6.20-15 to 2.6.20-16) broke alsamixer for me, so I went back to the older kernel (although there is a workaround, apparently).

---

### Post by l5110 on 2007-07-04
it's not travelmate's problem, i am using tm3272 now , the sound problem is from the ubuntu system , you can open the sound properties, and cancel the surroud ‘s mute, then ok ..

---

### Post by qrwe on 2007-07-09
Haven't had the time to test this the latest days, but I wil.
Thank you for all the replies!

---

### Post by Kingskid on 2007-07-09
> **l5110 said:**
> it's not travelmate's problem, i am using tm3272 now , the sound problem is from the ubuntu system , you can open the sound properties, and cancel the surroud ‘s mute, then ok ..

I was trying to use your hint but I had to do it little different. This is my way to sound :) :

Right click in top right corner of your screen on the icon of speaker > select *Open volume control* (or whatever you have there in English - I use Czech version) > in the opened window choose the second option (from three on the tab which opens option Settings > mark the box by *[I]Side,*[/I] it will add it to the opened window > activate it and set the volume.

That's it. Just now I enjoy King Diamond :popcorn:

Sorry for not so precise instructions as I had to guess the English terms becasue I'm in Czech environment & didn't find so quick how to change language. But I'm sure this will help at least in some way.

---

### Post by xvi99 on 2007-11-11
I am a complete newbie in ubuntu and linux. i just install ubuntu 7.10 on my acer 6291 laptop. the sound doesnt work. does anyone know how to fix this. a step by step guide would be appreciated

---

### Post by dlbrando on 2007-11-11
yea, I cant get 7.10 to play sound on my e-machines laptop either.  The other options in this  thread didnt do anything for me

---

### Post by Alte on 2007-11-15
My ACER Travelmate 6291 does not play sounds either. I also have some problem with my wireless network card. The connection jumps up and down making surfing very frustrating. I am a total n00b at this and an easy step by step guide would be much appreciated because I really hope to be able to ditch Microsoft completely.  Thanks in advance and the winner gets a bucket of :popcorn:

Cheers!

---

### Post by Alte on 2007-11-15
Solved my network problem! Go to this place for solution [http://ubuntuforums.org/showthread.php?t=595060:KS](http://ubuntuforums.org/showthread.php?t=595060:KS)

---

### Post by Alte on 2007-11-17
Solution found!
(From the Swedish Ubuntu forum)

1) sudo apt-get install build-essential ncurses-dev gettext libncurses5-dev linux-headers-`uname -r`

2) download lsa-driver, alsa-lib och alsa-utils from alsa-project.org

3)     ```
sudo mkdir -p /usr/src/alsa

    cd /usr/src/alsa

    sudo cp ~/alsa-src /usr/src/alsa

    sudo tar xjf alsa-driver-1.0.15.tar.bz2

    sudo tar xjf alsa-lib-1.0.15.tar.bz2

    sudo tar xjf alsa-utils-1.0.15.tar.bz2
```

4)   ```
cd alsa-driver-1.0.15

      sudo ./configure --with-cards=hda-intel --with-oss=yes

      sudo make

      sudo make install
```

5)   ```
cd ../alsa-lib-1.0.15rc1

    sudo ./configure

    sudo make

    sudo make install
```

6) ```
 cd ../alsa-utils-1.0.15rc1

     sudo ./configure

     sudo make

     sudo make install
```

7)  edit the file etc/modprobe.d/alsa-base and add options snd-hda-intel model=acer at the bottom. 

8) Restart and you got sound :guitar:

---

### Post by xvi99 on 2007-11-17
I would love to try the sound problem solution, but I can't right now since I can't get into the ALSA project webpage. I will try it as soon as I have the time and the webpage is up

---

### Post by xvi99 on 2007-11-19
I have tried, but it still not working. anybody has got it right?

---

### Post by qrwe on 2008-01-08
> **xvi99 said:**
> I have tried, but it still not working. anybody has got it right?

Apparently, Alte did.

---

### Post by jeppe99 on 2008-01-11
> xvi99 	
Re: No sound on ACER TravelMate 6291
I have tried, but it still not working. anybody has got it right?

Im running ubuntu 7.10 on my Acer travelmate 6291 and my sound didn't work from the installation.
I've tried Altes tips from this thread with  no results.:(
Then i found this: [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

Solved the problem for me :-({|=

---

