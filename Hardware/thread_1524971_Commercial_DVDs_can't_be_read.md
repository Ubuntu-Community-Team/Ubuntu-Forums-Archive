---
title: "Commercial DVDs can't be read"
date: 2010-07-06
forum: Hardware
---

### Post by brizzenden on 2010-07-06
I can't get any commercial DVDs to work.  I'm not sure when it stopped working, but it could do it several months back (the last time I tried one). 

Data discs and standard CDs work fine. 

Someone suggested I download VLC, which I did, but it didn't help.  Does anyone else have any advice?

---

### Post by Yarui on 2010-07-06
Do you have ubuntu-restricted-extras installed?

---

### Post by brizzenden on 2010-07-06
> **Yarui said:**
> Do you have ubuntu-restricted-extras installed?

I just downloaded it.  Do I have to do more with it? Because it still doesn't seem to be working.

---

### Post by lancest on 2010-07-06
I think you still need libdvdcss2 to play DVD's.
[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by brizzenden on 2010-07-06
> **lancest said:**
> I think you still need libdvdcss2 to play DVD's.
[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

I just tried that and still nothing.

---

### Post by lancest on 2010-07-06
Honestly on certain occasions (after real long sessions) I've had to reboot to get a DVD playing. Also try another DVD to verify if it's a good copy. 
 In the past I've noticed some DVD RW players work better than others in Linux. (it's why I ditched ASUS for Samsung)

---

### Post by ac7ss on 2010-07-06
> **brizzenden said:**
> I just tried that and still nothing.

What player are you using?

---

### Post by brizzenden on 2010-07-06
I've been using VLC and Movie Player.  But even when I go into places and look under computer, the drive doesn't even show a disc in it.  And I've reset several times already.

---

### Post by efflandt on 2010-07-06
Did you read the description for ubuntu-restricted-extras to go to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) which tells how to install libdvdread4?

---

### Post by brizzenden on 2010-07-06
> **efflandt said:**
> Did you read the description for ubuntu-restricted-extras to go to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) which tells how to install libdvdread4?

I have libdvdread4.

---

### Post by Yarui on 2010-07-06
Kind of a silly questions but I noticed in your opening post you said that data CDs work fine, but not commercial DVDs.  Is the problem, perhaps, that your drive can't read DVDs?  By that, I mean is it a CD drive, rather than a CD/DVD drive?  I'm sure this isn't the problem, but I thought I should probably ask.

---

### Post by brizzenden on 2010-07-06
> **Yarui said:**
> Kind of a silly questions but I noticed in your opening post you said that data CDs work fine, but not commercial DVDs.  Is the problem, perhaps, that your drive can't read DVDs?  By that, I mean is it a CD drive, rather than a CD/DVD drive?  I'm sure this isn't the problem, but I thought I should probably ask.

Oh no, sorry, I should have clarified.  They are Data DVD's.  Like old files I copied off another computer and even the disc I used to install 10.04 was on a DVD-R/W.  It just seems to be DVD movies that it won't detect.

EDIT: I just tried a DVD-R/W and it worked fine.

---

### Post by fx_viallon on 2010-07-11
Hello,

i face the same problem: i am unable to read correctly protected dvds. i followed the instructions on [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) step by step, even the troubleshooting part on DMA and Decryption errors (it seemed to fit to the trouble i was encountering), but without resolving the problem.

To describe the problem more precisely, the menu of the dvd shows up, but after clicking on "play", when the movie is supposed to start, there is first only chopped sound, then only a black screen instead of the video. the length of movie appears correctly though.

I am using VLC, lucid with the newest updates, my dvd drive is a MATSHITADVD-RAM UJ862AC and my computer in general quiet recent (Lenovo t400s).

I forgot to mention that the region code is correctly set.

Any help appreciated.

fx

---

### Post by Eddison on 2010-12-25
I have the same problem- Audio cd works fine. The optical drive will recognise the commercial film, and everything looks sweet. Then you try to play the film (commercial) and nothing !
Tried to copy files from DVD to hard drive, and Ubuntu offers this, but when you click 'copy' - again nothing happens. I did notice a buffer issue at one stage though ??
A bit annoying 'cause I just got s laptop for the new wife for Christmas, and I cant play a movie for her...



eddison

---

### Post by lancest on 2010-12-25
libdvdcss must be installed.

Try ripping the DVD with AcidRip or other.

Try another movie DVD, or another DVD drive for comparison purposes.

Problem could be specific to the DVD or the drive itself.

By the way just Google "Windows media player won't play DVD" and you'll see this is not uncommon. 

I don't run into this too much. 
(My ASUS DVD drives used to have problems so I changed them)

---

### Post by Eddison on 2010-12-27
Lancest- thanks for the reply.

Tried to install libdvdcss in the synaptic package manager, but couldn't find it, so I installed ubuntu restricted drivers, which installed libdvdcss automatically. 
The laptop I have (ok wifey owns it) is a samsung rv510 in case anyone else runs into this problem. After installing libdvdcss I can now play several older type dvd's no problem.
But we have the new Avatar commercial dvd (i know i should have got it with transmission lol!) and it will not play. something to do with security or new format or something. Lets hope there is a fix for this in the future?
Ubuntu says 'could not read from source media' I tried CSI miami and it does not work either/ Both of these dvd's will work on normal dvd players.



eddison

---

### Post by Eddison on 2010-12-27
This problem with Samsung laptop dvd drive could be region specific? I noticed the commercial DVD's that do not work have region 2 (Europe) on them.
DVD's that play no problem, are not region specific, and can play in any region, and on the samsung..


eddison

---

### Post by lancest on 2010-12-27
> **Eddison said:**
> This problem with Samsung laptop dvd drive could be region specific? I noticed the commercial DVD's that do not work have region 2 (Europe) on them.
DVD's that play no problem, are not region specific, and can play in any region, and on the samsung..

eddison

This is what I think is the problem.
I'm not forced to purchase commercial DVD's though so not much basis for comparison.

---

### Post by lancest on 2010-12-27
> **Eddison said:**
> This problem with Samsung laptop dvd drive could be region specific? I noticed the commercial DVD's that do not work have region 2 (Europe) on them.
DVD's that play no problem, are not region specific, and can play in any region, and on the samsung..

eddison

This is what I think is the problem.
I'm not forced to use commercial DVD's though so not much basis for comparison.

---

### Post by Eddison on 2010-12-27
Its weird though, files on the DVD will not even show up ???

If there was a workaround, it would be great like copy an image to hard drive or something, but this does not work either :(


eddison

---

### Post by Eddison on 2010-12-28
Problem seems to be getting weirder ??
When VLC is installed, I click on 'Home' or any folder, and VLC starts up. I then removed VLC, completely, rebooted then the home folder etc all work normally.
When I install VLC again, and try to open Home folder, VLC starts to run again ?? 
This is getting pretty frustrating.


eddison

---

### Post by Eddison on 2011-01-01
Hi Guys,
These solutions worked for me:
Make sure multiverse is selected in system/administration/settings/repositories/ and under the tab ''ubuntu software'' at the end of different lines it says universe, multiverse etc.

Install VLC in synaptic
Install ubuntu-restricted-extras also in synaptic

install  libdvdread4 or just use terminal- 
code: sudo apt-get install libdvdread4

You must also have 
Code: sudo /usr/share/doc/libdvdread4/install-css.sh

The above does not seem to be in the repositories, so I just ran it from terminal instead.


The laptop I have is a Samsung rv510 and the  problem was with the optical drive or TS-L633 which is a toshiba dvd  drive. 


 



eddison

---

### Post by meandshadow on 2011-01-01
here's the link to someone that not only tell you how but gives you the proper codecs for it .... Just copy & paste the first one in your terminal window then click enter you'll have to enter whatever password you have set for administrative tasks and then wait for the computer to load this command then copy & paste the second command & voila ! it'takes a little while to execute all that but you should be set...
Oh ! the link... 
[http://kellepcharles.blogspot.com/2009/07/enabling-dvd-playback-in-ubuntu-904.html](http://kellepcharles.blogspot.com/2009/07/enabling-dvd-playback-in-ubuntu-904.html)

---

### Post by POWMS on 2011-01-03
This solution worked for me too.

---

### Post by cain071546 on 2011-03-12
THANK YOU! meandshadow  
worked great

---

