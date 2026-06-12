---
title: "No headphone sound on Toshiba  Satellite A135"
date: 2009-03-09
forum: Hardware
---

### Post by jerrynewt on 2009-03-09
My son just came over from the dark side a couple weeks ago and so far no problems with his Hardy install other than no headphones. The sound works fine with the laptop's built in speakers, but no sound with the headphones or any external speakers (worked ok with XP). lspcv -l shows Intel Corp 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Any help would be appreciated.

---

### Post by albandy on 2009-03-09
search in sound options for jack sense

double click in the speaker icon
the mixer will appear
then click preferences
search for Line Jack Sense, enable it

now a new tab will appear in the mixer
search for headphone jack sense and select it

---

### Post by jerrynewt on 2009-03-11
Ok double clicked the speaker icon and no selection for Line Jack Sense. There is one for headphones and it is already checked. Still no joy.

---

### Post by Anthem on 2009-05-18
Same laptop, same problem.  It's had this difficulty for since Hardy, which is annoying since it worked before that.  Now I've got to re-figure out how to fix it, since the gutsy fix no longer works.

It's a stock vanilla Intel chipset, you'd think it would be easy.

---

### Post by PRDS on 2009-06-14
There is a solution to this.. there is a similar fix to Sony laptop owners. I have gotten it to work in the past. It also makes the side buttons work [Play, Stop, Track Advance]. Unfortunately, I will need to figure out how to do it again. I will see if I can find it and post the solution.

---

### Post by coltcannon on 2009-08-05
I am using a a135-s7403 and have the same issue. There is no sound at all from the headphone jack. The internal speakers dont mute, and I have enabled and changed all the sound options availibe. I havent found anything close to a fix newer that Hardy releases and that fix was recompiling the alsa drivers. I actually cant remember if the headphones worked with Intrepid. Right now I need this laptop to play music out of the headphones for use in my business. It would be a shame to have to change OS.

---

### Post by wford002 on 2009-08-09
I forget where I originally saw this but I have to input this every time I do a fresh install. I have a toshiba A135-S4467 and this completely fixes the headphone issue.

1) open terminal:

     Applications > Accessories > Terminal

2) in terminal enter command:

     sudo gedit /etc/modprobe.d/alsa-base.conf

     enter password when prompted.

3) this will open a file, scroll to the end of the file and paste in:

     options snd-hda-intel model=lenovo
     
     save and close this file

4) Restart computer, sound should work through the headphones now.

Hope this helps.

---

### Post by DonnieP on 2009-08-23
> **wford002 said:**
> I have a toshiba A135-S4467 and this completely fixes the headphone issue.
---
     options snd-hda-intel model=lenovo

OMG!  Thank you.  I have the same model laptop and never was able before to get the speakers to mute when the headphone was plugged in.  Can't believe even the media keys work.

---

### Post by DRankovic on 2009-08-23
> **DonnieP said:**
>  to get the speakers to mute when the headphone was plugged in 

I can't get the built in speakers to mute on FSC Amilo Pro, I get sound from both external and internal speakers. Is there any way to solve this? Thanks

---

### Post by DonnieP on 2009-08-30
> **DRankovic said:**
> I can't get the built in speakers to mute on FSC Amilo Pro, I get sound from both external and internal speakers. Is there any way to solve this? Thanks
Check out this thread at LinuxQuestions:
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ubuntu-headphone-599930/]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ubuntu-headphone-599930/")
It's basically a crap shoot.  Try some of the tweaks toward the end of that thread for your /etc/modprobe.d/alsa-base.conf.

---

### Post by Angel169 on 2009-09-15
[FONT=Arial Narrow][SIZE=3]I have been having the same problem with the headphone sound my laptop is a toshiba satellite A135-S2426. Any solutions?[/SIZE][/FONT]

---

### Post by Hallic7 on 2010-08-12
Hi! I have the same problem with my Toshiba Satellite A665-S6056. My speakers work nice, but the jack does not! I have tried the solutions before with no luck...

Help please!!!

---

### Post by king james II on 2011-02-11
same problem toshiba satellite T135D-S1324 RT. Please help!:confused:

---

### Post by Chaz Griffin on 2012-12-10
I also have a Toshiba Satellite running Zorin OS 6 (64 bit) and could not for the life of me get the headphone jack to work.
Then I found "wford002"'s reply as follows.....

1) open terminal:

Applications > Accessories > Terminal

2) in terminal enter command:

sudo gedit /etc/modprobe.d/alsa-base.conf

enter password when prompted.

3) this will open a file, scroll to the end of the file and paste in:

options snd-hda-intel model=lenovo

save and close this file

4) Restart computer, sound should work through the headphones now.

BRILLIANT FIX!!!! Worked like a proverbial charm!
Thanks wford002 !!!!!!!!!!!

---

