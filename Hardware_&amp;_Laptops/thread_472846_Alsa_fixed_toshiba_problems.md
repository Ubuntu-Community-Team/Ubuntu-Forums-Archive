---
title: "Alsa fixed toshiba problems?"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by Unreal223linux on 2007-06-13
Apparently a new version of alsa was released and they are claiming it fixes all the toshiba issues:
[http://www.alsa-project.org/changes/v1-0-13--v1-0-14.txt](http://www.alsa-project.org/changes/v1-0-13--v1-0-14.txt)

Has anyone updated to see if everything works? I would really like to update and try it out but I'm too dumb with linux and don't know how.
[http://ubuntuforums.org/showthread.php?p=2836918#post2836918](http://ubuntuforums.org/showthread.php?p=2836918#post2836918)

---

### Post by dannyboy79 on 2007-06-13
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install 
OR 
sudo checkinstall
NOTE: BUT you need checkinstall installed first, this will create a .deb that you can install/uninstall with the package manager instead of having to leave the directory there in case you need to remove it which I don't know how to remove stuff you installed using sudo make install that's why I use checkinstall but sometimes checkinstall does NOT work. not sure why.

Then REBOOT. 

that should be it.

---

### Post by Unreal223linux on 2007-06-13
Thank you but I wasn't kidding when I said I didn't know anything about linux what so ever.
I'm willing to spend the time to learn but for me to do that I need at least all of my hardware working. :( (sound especially so I can listen to music while I read up on how stuff works)

Anyway.. to do the steps you listed I just copy and past exactly what you wrote into the command line?
Do I do it one line at a time or all at once? Is there anything I'm supposed to change specifically to my computer? Or is that exactly what I type?

Oh and thanks a lot!

---

### Post by Thomar on 2007-06-13
From my experience, kernel 7.04 (the most recent version of Ubuntu) fixed most of the problems the Toshiba Satellite had.  That version apparently includes working drivers, so I don't think you need to install the Alsa package.

Unfortunately, I have experienced numerous lockups (the sound gets "stuck", stuttering endlessly on the same bit), but it's better than no sound at all.  I've found that only using one sound-based program at a time (i.e., don't run your music player while watching a flash video in Firefox) keeps this from happening, but it's still a little touchy.

Of course, this all may be due to my numerous attempts to get sound working on the last rev of Ubuntu, I did try the Alsa drivers but they didn't work.

---

### Post by dannyboy79 on 2007-06-13
> **Unreal223linux said:**
> Thank you but I wasn't kidding when I said I didn't know anything about linux what so ever.
I'm willing to spend the time to learn but for me to do that I need at least all of my hardware working. :( (sound especially so I can listen to music while I read up on how stuff works)

Anyway.. to do the steps you listed I just copy and past exactly what you wrote into the command line?
Do I do it one line at a time or all at once? Is there anything I'm supposed to change specifically to my computer? Or is that exactly what I type?

Oh and thanks a lot!
yes, all you would have to do is copy 1 line at a time, paste it into the terminal and hit enter. compiling alsa takes awhile so be patient.

As far as getting your card working without compiling alsa, have you read the comprehensive sound guide? it's here: 

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive)

---

### Post by Unreal223linux on 2007-06-13
> **Thomar said:**
> From my experience, kernel 7.04 (the most recent version of Ubuntu) fixed most of the problems the Toshiba Satellite had.  That version apparently includes working drivers, so I don't think you need to install the Alsa package.

Unfortunately, I have experienced numerous lockups (the sound gets "stuck", stuttering endlessly on the same bit), but it's better than no sound at all.  I've found that only using one sound-based program at a time (i.e., don't run your music player while watching a flash video in Firefox) keeps this from happening, but it's still a little touchy.

Of course, this all may be due to my numerous attempts to get sound working on the last rev of Ubuntu, I did try the Alsa drivers but they didn't work.
I don't currently have ubuntu installed on my laptop(currently running xp) but I did install ubuntu about a week ago and tried tons of stuff. Out of the box ubuntu would play sound out of only the right speaker and nothing out of the headphones. The previous version of ubuntu would play sound out of both speakers but still no headphones(which is very important since I use skype all the time and cant listen to loud music while sitting on the couch in the hall way at college. :P)


> **dannyboy79 said:**
> yes, all you would have to do is copy 1 line at a time, paste it into the terminal and hit enter. compiling alsa takes awhile so be patient.

As far as getting your card working without compiling alsa, have you read the comprehensive sound guide? it's here: 

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive)

I've tried just about everything except updating alsa. Some people were reporting success by adding some line in a file called modprobe or something like that but it never worked for me. The alsa 1.4 link says they have fixed the problems with the ati sb something card which is what I believe my computer has. Also that linux laptop link here is reporting that toshiba l35's work with alsa 1.4:
[http://www.linlap.com/wiki/Toshiba+Satellite+L35](http://www.linlap.com/wiki/Toshiba+Satellite+L35)

Thanks for all the help I'm about to install ubuntu, update everything, and then update alsa. If it doesn't work I may just have to give up on linux. I really like the idea of using an all free, virus free, customizable OS but I just cant justify moving away from an OS where everything just works(winxp) to one that only supports half my hardware. :( I really really don't want to stay with xp though.

Thanks for all the help and I'll post back in a few hours if it worked or not. :)

---

### Post by Unreal223linux on 2007-06-13
Ok I have a fully updated ubuntu laptop now.
I havent updated alsa yet though because the first command isn't working.. I don't think. :(

I got this:

name@name-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
--19:43:37--  [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
           => `drive...1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.14.tar.bz2 ... 
No such file `drive...1.0.14.tar.bz2'.
(I changed the thing to say name instead of my name..)


Also what is the difference in the make install and check install steps?
If check install is better how do I download what I need to do it? 

Sorry I'm so lost. :(
I haven't had this much trouble with computers since my windows 3.1 days. :(
All help is greatly appreciated.

Is there not anything on linux thats like .exe on windows? Where I could just download and click next and it does it on its own?

---

### Post by dannyboy79 on 2007-06-13
> **Unreal223linux said:**
> Ok I have a fully updated ubuntu laptop now.
I havent updated alsa yet though because the first command isn't working.. I don't think. :(

I got this:

name@name-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
--19:43:37--  [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
           => `drive...1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.14.tar.bz2 ... 
No such file `drive...1.0.14.tar.bz2'.
(I changed the thing to say name instead of my name..)


Also what is the difference in the make install and check install steps?
If check install is better how do I download what I need to do it? 

Sorry I'm so lost. :(
I haven't had this much trouble with computers since my windows 3.1 days. :(
All help is greatly appreciated.

Is there not anything on linux thats like .exe on windows? Where I could just download and click next and it does it on its own?
sorry about that, it had put a bunch of periods instead of the complete link path, so it couldn't find it since it had............. in it, try this:
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)

the rest is still the same

---

### Post by Unreal223linux on 2007-06-13
oh got it. 
Thanks again. I'll let you know if it works. :)

---

### Post by Unreal223linux on 2007-06-13
name@name-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
--23:06:35--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
           => `alsa-driver-1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> PASV ... done.    ==> RETR alsa-driver-1.0.14.tar.bz2 ... done.
Length: 2,600,096 (2.5M) (unauthoritative)

100%[====================================>] 2,600,096     63.29K/s    ETA 00:00

23:07:37 (47.77 KB/s) - `alsa-driver-1.0.14.tar.bz2' saved [2600096]

name@name-laptop:~$ tar -xjf alsa-driver-1.0.14.tar.bz2
name@name-laptop:~$ ./configure
bash: ./configure: No such file or directory 

I got another error. :(

---

### Post by Unreal223linux on 2007-06-13
ok I'm an idiot. I just figured out I skipped a step, but I did get another error. :(
There really needs to be graphical ways to do this for dummys like me. :(

ryan@ryan-laptop:~$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
--23:46:59--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
           => `alsa-driver-1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> PASV ... done.    ==> RETR alsa-driver-1.0.14.tar.bz2 ... done.
Length: 2,600,096 (2.5M) (unauthoritative)

100%[====================================>] 2,600,096     47.71K/s    ETA 00:00

23:47:58 (49.12 KB/s) - `alsa-driver-1.0.14.tar.bz2' saved [2600096]

ryan@ryan-laptop:~$ tar -xjf alsa-driver-1.0.14.tar.bz2
ryan@ryan-laptop:~$ cd alsa-driver-1.0.14
ryan@ryan-laptop:~/alsa-driver-1.0.14$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
ryan@ryan-laptop:~/alsa-driver-1.0.14$ 


What did I do wrong now? Some kind of compliler error?
Am I missing a tool I need or something?

---

### Post by Unreal223linux on 2007-06-14
Ok I'm getting closer!
I figured out what was wrong with the alsa install and now I have it working. 

I now have sound in both speakers but no headphone sound. But I found an article that said I needed to enter this:

options snd-hda-intel model=6stack-digout

Into this file:
 /etc/modprobe.conf

I saw how to open a file by entering gedit  /etc/modprobe.conf 
But when I try to save it says I don't have admin usage rights or something like that. I feel like i'm almost there but there is always something holding me back. :( How do I get admin rights to edit that file?

---

### Post by Unreal223linux on 2007-06-14
YES!!!!!!!!!!!
I GOT SOUND!!!!!!!!!!!!!!!!!!!!!!!

I'm so happy. bye bye windows. :)

To all of those with toshiba l35 computer here is how you get headphones and speakers to work.

1. Update alsa 1.4
2. Input:  "options snd-hda-intel model=6stack-digout" (no quotes)
Into this file:
/etc/modprobe.conf

use "sudo gedit /etc/modprobe.conf" to be allowed to save the edit.
Reboot after this step

3. go to terminal and enter "alsamixer". Make sure nothing is muted and turn the volume things all the way up and you should be good to go!

It even autodetects when my headphones are plugged in. I just have to figure out which sliders I need now in the audio panel.(I have litterally 12 or so of them visible. :P)

---

### Post by dannyboy79 on 2007-06-14
i am glad you got it working, this is good to know for others and proabably not just for your laptop. Sound has been one of those unfortunates with linux and a little spotty so this is obviously a step in the right direction for Linux and sound. They just need to get wireless working a little better, more hardware etc etc. you're welcome for telling you how to upgrade to the latest alsa.

---

### Post by Fliipn on 2007-06-14
> **Unreal223linux said:**
> YES!!!!!!!!!!!
I GOT SOUND!!!!!!!!!!!!!!!!!!!!!!!

I'm so happy. bye bye windows. :)

To all of those with toshiba l35 computer here is how you get headphones and speakers to work.

1. Update alsa 1.4
2. Input:  "options snd-hda-intel model=6stack-digout" (no quotes)
Into this file:
/etc/modprobe.conf

use "sudo gedit /etc/modprobe.conf" to be allowed to save the edit.
Reboot after this step

3. go to terminal and enter "alsamixer". Make sure nothing is muted and turn the volume things all the way up and you should be good to go!

It even autodetects when my headphones are plugged in. I just have to figure out which sliders I need now in the audio panel.(I have litterally 12 or so of them visible. :P)


I got the same error when I compiled the alsa file.. im also a linux n00b.. what did u do to finish the compile?

---

### Post by dannyboy79 on 2007-06-14
> **Fliipn said:**
> I got the same error when I compiled the alsa file.. im also a linux n00b.. what did u do to finish the compile?

huh?? what error??  he didn't compile, you quoted what he did. if you're referring the post way at the top, than I am guessing it's because you don't have the developer tools installed. do this
sudo aptitude install build-essential
and then try to configure it, IF you really need to but as you can see by above, he never did compile it, he got the Feisty version of Alsa working. (Well at least that's how I am reading it but I suppose I could be wrong)

---

### Post by Unreal223linux on 2007-06-14
I wrote up exactly what I did a little better here:
[http://ubuntuforums.org/showthread.php?t=473425](http://ubuntuforums.org/showthread.php?t=473425)

You probably need to run this:

sudo apt-get install build-essential linux-headers-$(uname -r)

---

### Post by sci-fi guy on 2007-06-16
You seem to have forgotten to include the line "cd alsa-driver-1.0.14" before the "./configure."  Open a new terminal, and enter that line now and continue with the ./configure, make, and make install lines.  No need to bother with the preceding lines, as they just downloaded and unzipped the driver, and the files are still there (unless you deleted them).  Good luck, because this did not work on my A205.  For anybody reading this post who might be able to tell me how to fix this, Hardware Information on my computer says that my sound is a "82801G (ICH7 Family) High Definition Audio Controller" from Intel.

---

### Post by Unreal223linux on 2007-06-16
I put up exact directions for what I did here:
[http://ubuntuforums.org/showthread.php?t=473425](http://ubuntuforums.org/showthread.php?t=473425)

Sorry it didnt work for you. :(

---

### Post by reset3x on 2007-06-16
I have a Satellite A45-S120 with a fresh install of 7.04.... Everything works fine... Even the function keys.....

---

### Post by sci-fi guy on 2007-06-16
> **Unreal223linux said:**
> I put up exact directions for what I did here:
[http://ubuntuforums.org/showthread.php?t=473425](http://ubuntuforums.org/showthread.php?t=473425)

Sorry it didnt work for you. :(

Tried that before. No dice. :(

---

### Post by pbhill on 2007-06-16
I've been following this thread to resolve my lack of sound on my dual boot Acer 5670. I  can't seem to get anywhere with the link dannyboy79 has posted. I get this:

pbhill@Acer:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
--22:10:43--  [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
           => `drive...1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.14.tar.bz2 ... 
No such file `drive...1.0.14.tar.bz2'.



Does it work for anyone else?
Love to get some sound out of this box. Works fine in WinXP.

---

### Post by Unreal223linux on 2007-06-16
> **pbhill said:**
> I've been following this thread to resolve my lack of sound on my dual boot Acer 5670. I  can't seem to get anywhere with the link dannyboy79 has posted. I get this:

pbhill@Acer:~$ wget [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
--22:10:43--  [ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
           => `drive...1.0.14.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub ... done.
==> PASV ... done.    ==> RETR drive...1.0.14.tar.bz2 ... 
No such file `drive...1.0.14.tar.bz2'.



Does it work for anyone else?
Love to get some sound out of this box. Works fine in WinXP.


Its because the forum software is messing up your download destination with the .... in the URL.

Here is step by step how to update alsa:

```

sudo apt-get install build-essential linux-headers-$(uname -r)
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install

```

If you use the code tags it wont happen.

---

