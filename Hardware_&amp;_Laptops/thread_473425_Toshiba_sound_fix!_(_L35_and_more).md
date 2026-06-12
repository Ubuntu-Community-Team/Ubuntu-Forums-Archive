---
title: "Toshiba sound fix! ( L35 and more?)"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Unreal223linux on 2007-06-14
I have a toshiba l35-S2161 and had been through absolute hell trying to get sound working and I have finally done it! I have sound coming out of both speakers and my headphones.

Maybe someone can refine this process but it worked perfectly for me. I'm a complete linux noob but this isn't hard to do.(it was hard to figure out though. :P) Going through this myself I know how hard it can be for complete newbies to follow the seemingly easiest instructions. So I will try to explain this as simply as possible. 

Here it goes.

Step one is you need the newest version of the alsa sound drivers. To do that cut and paste each line of the below code box into the terminal one at a time. Wait untill one function is done before pasting in the next.  The terminal is located in applications> accessories>terminal.

```

sudo apt-get install build-essential linux-headers-$(uname -r)
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install 

```

Once through all of the commands reboot your computer.

-------------------

Once the computer is back up go back into the terminal and enter this:

```

sudo gedit /etc/modprobe.conf

```

You will be prompted for your user account password. When you type it will look like nothing is happening but thats just a security feature.

In the text file that pops up enter this and save it:

```

options snd-hda-intel model=6stack-digout

```

Once saved reboot your computer

---------------------

Once your computer is back up go back into the terminal and enter
```

alsamixer
```

Use the arrow keys to move around on this screen. On anything you see double MM on press the M key and maximize the volume. Do this to anything with the double MM.

Once you do your headphones should be working! Go to the volume control panel and go to edit>preferences> and enable surround. From what I have seen that is the one that adjusts your headphones.

I hope this helps some people out there! I will probably wake up tomorrow and see how badly written this gude is and I appologize for that but its 2:30 AM here. I just wanted to get this up to help those with this problem.

A big thank you to dannyboy79 for sticking with me and my noob questions about installing alsa.

---

### Post by matheuu on 2007-06-14
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
This card doesn't seem to work with the fix

---

### Post by DagMan on 2007-06-14
try putting it at the end of the file in /etc/modprobe.d/alsa-base instead of /etc/modprobe.conf
and also if those particular options don't work

options snd-hda-intel model=auto
or 
options snd-hda-intel model=3stack
might also work.

I was lucky enough to be able to do it without having to update the alsa driver on a differnat toshiba model.

---

### Post by Unreal223linux on 2007-06-14
Awe I was hoping this would work for the other toshiba users too. :(
I know how bad not having sound sucks.(I kept using xp because of it. I HAVE to have headphone sound.)

---

### Post by fingolfin07 on 2007-06-15
Hallelujah!!
Using a few of the other suggested workarounds I was able to get the speakers working on my L35, but not the headphones.
Being a linux noob, all I could really do was search the internet and forums for fixes to this probelm.

This worked for me, and now I am SOOO excited to be using ubuntu =D

Thank you so much

---

### Post by Unreal223linux on 2007-06-16
Glad it worked for you too! :D
I was really miserable without sound but now I'm actually really liking linux.(this coming from a 10+ year windows vet who knows lots about windows and nothing about linux. :P) Its kinda fun learning a new OS. (especially once you can listen to music while doing so.)

---

### Post by mad_dog on 2007-06-17
i don't have modprobe.conf in etc directory... where i can find this? whith search command i have fouded some modprobe but no one in etc...

---

### Post by Unreal223linux on 2007-06-17
Had you been trying other sound fixes? Maybe one of them messed something up..
I did this fix on ubuntu, kubuntu, and Mint and it worked fine on all three and they all had that file. :(

Like I said I don't really know much about linux. :P

---

### Post by Mrsongs on 2007-06-19
Another satisfied customer--I got speaker sound working on my Toshiba A135-S2386 by compiling the latest  alsa drivers, and headphones working by following this thread.:)  Haven't figured out how to mute the speakers while the headphones are playing--the volume control mute doesn't seem to work on them. But I'm not quibbling, believe me. Thanks for dogging this one down.

---

### Post by killux on 2007-06-29
Thank you for this! I want to confirm that this fix works on the Toshiba Satellite L35-S2174. Everything is working!

---

### Post by rolfa on 2007-06-30
Thanks!! 
it worked just after reinstalling alsa
Sattellite A200

---

### Post by sockerbit on 2007-07-04
i'm pumped, it worked for me. thanks a ton :)

---

### Post by Maverynthia on 2007-07-05
modprobe.conf could not be found.... :(

---

### Post by naxmul on 2007-07-10
> **Maverynthia said:**
> modprobe.conf could not be found.... :(

yeh, it doesn't originaly exist. doing sudo gedit /etc/modprobe.conf creates the file once u save it. make sure u have sudo in there.

---

### Post by santoxyz on 2007-07-13
there are chances that my post helps with headphones:

[http://ubuntuforums.org/showthread.php?t=500274](http://ubuntuforums.org/showthread.php?t=500274)


good luck!

---

### Post by silviasichigo on 2007-07-14
Thanks for the Crack I also have the Toshiba LT and now that I have the sound going along with you graphics I am having a great time exploring my Ubuntu!!

---

### Post by Pixie716 on 2007-07-16
Thanks Unreal...I'm an Ubuntu newbie myself and you made it nice and easy to fix my problem.

---

### Post by ktwbug on 2007-07-31
Unreal is Unreal!!!!  You Freaking ROCK!!!  This worked for my Toshiba Satellite after trying many, many, other attempts!!!  Thank you, Thank you.........  ):P

---

### Post by 98octane on 2007-08-16
Thanks Unreal!
I successfully made sound working on a Toshiba Satellite A135-4527, with that steps you quoted. I'm still working on that Headphone/Speaker issue.

---

### Post by Wickednix on 2007-08-20
All I have to say is thank you so much for this fix. I have all my channels working. Now to get my packet loss fixed and get my mouse buttons working, but thats a search away from being fixed.

---

### Post by Wickednix on 2007-08-20
All I have to say is thank you so much for this fix. I have all my channels working. Now to get my packet loss fixed and get my mouse buttons working, but thats a search away from bing fixed.

---

### Post by Blaster95 on 2007-08-20
Thank you sooo much. That worked and you just made my day :)

---

### Post by fumoffu on 2007-08-21
> **DagMan said:**
> try putting it at the end of the file in /etc/modprobe.d/alsa-base instead of /etc/modprobe.conf
and also if those particular options don't work

options snd-hda-intel model=auto
or 
options snd-hda-intel model=3stack
might also work.

I was lucky enough to be able to do it without having to update the alsa driver on a differnat toshiba model.
Ah! I'm using a Toshiba a105 S2051 and this managed to fix my sound problem. At the end of /etc/modprobe.d/alsa-base I put **options snd-hda-intel model=auto**   Thanks DagMan :)

---

### Post by sockerbit on 2007-09-12
worked for me, thanks a ton!

---

### Post by clmcdanne on 2007-09-22
fixed Toshiba Satellite A135-S2276 external sound, thanks for your time & efforts!

---

### Post by %hMa@?b&lt;C on 2007-09-24
thanks so much! confirmed to work on my brother's new Toshiba Satellite A135-S4656 (he is a brand new linux convert, and he chooses it over vista!)

---

### Post by lawrencewmooreJ on 2007-09-30
Hi all,

I've been tring to get my sound to work on Ubuntu Studio for a week now.  I'm going around to forums all over the place and am trying everything I'm just about to give up.  Since I'm a computer music composer, the use of sound is very important.


I installed the latest alsa drivers, compiled them and installed them.

I used these lines in the alsa-base file....

options snd-hda-intel model=6stack-digout
options snd-hda-intel model=3stach
options snd-hda-intel model=auto
options snd-hda-intel model=laptop

The volumes are up and unmuted in alsa-mixer.


I have a Toshiba Sattelite p100/p105 series

Here is the soundcard info....


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


After all this work the past week, I'm just about out of things to try and I don't know what to do.

Sorry to sound depressed, but I am.

Larry

---

### Post by olega on 2007-10-05
:))) You are perfect and Big thank you for that instruction! 
That works and I got sound on my Toshiba L30 notebook! Wow!

---

### Post by shpang on 2007-10-09
> **lawrencewmooreJ said:**
> Hi all,

I've been tring to get my sound to work on Ubuntu Studio for a week now.  I'm going around to forums all over the place and am trying everything I'm just about to give up.  Since I'm a computer music composer, the use of sound is very important.


I installed the latest alsa drivers, compiled them and installed them.

I used these lines in the alsa-base file....

options snd-hda-intel model=6stack-digout
options snd-hda-intel model=3stach
options snd-hda-intel model=auto
options snd-hda-intel model=laptop

The volumes are up and unmuted in alsa-mixer.


I have a Toshiba Sattelite p100/p105 series

Here is the soundcard info....


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


After all this work the past week, I'm just about out of things to try and I don't know what to do.

Sorry to sound depressed, but I am.

Larry

Hey Larry, my comp is a p105-s9722, and I also tried all the things possible through package managers nad manual editing, all the mixers and sound controls are present and set-up but still I have no sound, it just does not work :( perhaps the sound  driver itself is not the proper one ....

---

### Post by pierrot on 2007-10-10
:popcorn:
10x a lot! I'm Ubuntu new user too, and your post was very helpful and everything goes perfect.
It works perfect in Toshiba Satellite L30 after replacing the Vista with Ubuntu.

---

### Post by crazyforpurple on 2007-10-10
hello,I have followed your instructions right down to the end  on my Toshiba Satellite A135-S7404 but when i get down to the last command i get this:

mommy@mommy-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
mommy@mommy-laptop:~$ 


can anyone help me with this or shall i assume that this doesnt work for my latop and try something else?

thanks in advance xx

lucy x

---

### Post by MatthewPlanchard on 2007-10-12
Thanks for this excellent fix!
It worked for me on my Satellite A135-S2246, headphones and internal speakers both!

---

### Post by mbaker1965 on 2007-10-13
I have a P105 and I have been looking around for a fix for my sound now for weeks. So far nothing. Geeze I tried all this already .. 

I have the hda-intel sound card also and still I have no results. I am so frustrated and annoyed that I am almost to the breaking point.

I was told too disable my touch pag in bios and still nothing. 

Anyone have details on how to fix me up?

Mel

Thanks

---

### Post by clooch on 2007-10-17
> **Unreal223linux said:**
> I have a toshiba l35-S2161 and had been through absolute hell trying to get sound working and I have finally done it! I have sound coming out of both speakers and my headphones.

Maybe someone can refine this process but it worked perfectly for me. I'm a complete linux noob but this isn't hard to do.(it was hard to figure out though. :P) Going through this myself I know how hard it can be for complete newbies to follow the seemingly easiest instructions. So I will try to explain this as simply as possible. 

Here it goes.

Step one is you need the newest version of the alsa sound drivers. To do that cut and paste each line of the below code box into the terminal one at a time. Wait untill one function is done before pasting in the next.  The terminal is located in applications> accessories>terminal.

```

sudo apt-get install build-essential linux-headers-$(uname -r)
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
sudo make
sudo make install 

```

Once through all of the commands reboot your computer.

-------------------

Once the computer is back up go back into the terminal and enter this:

```

sudo gedit /etc/modprobe.conf

```

You will be prompted for your user account password. When you type it will look like nothing is happening but thats just a security feature.

In the text file that pops up enter this and save it:

```

options snd-hda-intel model=6stack-digout

```

Once saved reboot your computer

---------------------

Once your computer is back up go back into the terminal and enter
```

alsamixer
```

Use the arrow keys to move around on this screen. On anything you see double MM on press the M key and maximize the volume. Do this to anything with the double MM.

Once you do your headphones should be working! Go to the volume control panel and go to edit>preferences> and enable surround. From what I have seen that is the one that adjusts your headphones.

I hope this helps some people out there! I will probably wake up tomorrow and see how badly written this gude is and I appologize for that but its 2:30 AM here. I just wanted to get this up to help those with this problem.

A big thank you to dannyboy79 for sticking with me and my noob questions about installing alsa.

I would like to add that on my model L45-s4687  that using the "options snd-hda-intel model=6stack-digout" gave me headphones it also gave me only the right side, i modified the line in /etc/modprobe.conf to be  

[code]
options snd-hda-intel model=3stack 
[code]

All is happy I now have both speakers working  as well as headphones woo hoot.

this seems to only work in the /etc/modprobe.conf.   It seems that the /etc/modprobe.d/alsa-base is not affected by adding  this change. 

I hope this helps.

cheers

---

### Post by mikeypw on 2007-10-18
Just wanted t thank everyone on this thread. I too have an A135-S4656 and the only thing that did not work with 7.10 was the sound card. I was excited last night when I found this post, but when I followed the first set of directions still no sound. However after reading the entire thread and making modifications to the instructions per some posts....Bingo!!!! Thank you again. I too am a Windows  user and am trying to convert to Linux. With you guys I am on my way...Thanks again

---

### Post by crazyforpurple on 2007-10-19
i have been googling and following varios threads on the ALSA and i thought i had installed it etc... but i still have no sound. when i follow your steps here and then type the comand 

alsamixer after rebooting i get this:

mommy@mommy-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
mommy@mommy-laptop:~$ 


does this mean i havent got it installed as i thought i had? i went through all the make install things etc from this thread:

[http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463)

so i thought it was installed. can anyone help me  please??? i am a noob and getting very frustrated with living in a silent world!!

love lucy xx

---

### Post by crazyforpurple on 2007-10-24
Today I got my sound working!! 
thank you toe veryone who has helped me in doing this xxx

below is a list of what i did, I actually got the info from this link:

[http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)

but below is specificatlly what I did:

hope this helps someone else  xxx

love lucy xxx


1. after installing ubuntu gutsy i had no sound and no sound cards were detected.
2. when i tried the command "cat /proc/asound/cards" it would just say no soundcards installed
3. i couldnt even find these files....
"Remove ~/.asoundrc and ~/.asoundrc.asoundconf."

let alone remove them! so i went on to the next step:

4. i then went onto your next step:
"Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot."

to do this i did the following:

go to system, administration, synaptic package manager,
type in your password
in synaptic package manager, go to settings, repositories

under the "ubuntu software" tab I checked on each entry under "downloadable from the internet" and unchecked the cd/dvd option.

then under the "updates" tab I checked everything including the gutsy backports.
close the repositories box and then click reload in the synaptic package manager.

5. I don't think its necessary at this time but I restarted my laptop for good measure at this point.

6. I then went back into the synaptic package manager and ran a search for backports

7. I also went to applications, accessories, terminal and ran the following command
uname -r to find the details of my kernal.

it came back with 2.6.22-14-generic

8. In the synaptic package manager I had many options from my search and I wasnt sure which one I should use... I narrowed it down to

linux-backports-modules (which in the info said "Generic Linux backported drivers.")
and
linux-backports-modules-gene-2.6.22.14.21 (which in the info said "Backported drivers for generic kernel image")

I'm not quite sure why, but I clicked on the latter on and marked it for install. I then clicked "apply" and once it was all done I restarted the laptop and on restart I had sound!!!!!!


This may not be worth noting but when I use the term "restart" I actually shut down and then start up the laptop as using the "restart" option on mine means that it hangs before the log in screen.

---

### Post by skooge on 2007-10-24
Thank you! It worked on an Toshiba Satellite A135-S4656

---

### Post by Amblargh on 2007-10-25
First off, let me say that I'm a first time Linux user, and pretty much a noob with any sort of terminal and command prompt. (What can I say, Windows spoiled me until I realized it sucked.)

I'm running on a A105-S2001 and this pretty much did it for me, using the *[COLOR="Red"]options snd-hda-intel model=auto[/COLOR]* in the gedit modprobe.conf file. 

Thank you so much! Fixing this on my own made me feel so accomplished, especially considering my PC-tech-linux-loving-geek of a boyfriend couldn't figure out how to make it work =P

---

### Post by matt1 on 2007-10-27
headphones work, but the speakers won't mute when I plug headphones in.
has anyone found a fix for this. otherwise, this worked great. thanks.
i have a toshiba a135-s4527.

---

### Post by Major Crash on 2007-10-27
I was able to use options snd-hda-intel model=auto to get my headphones working, but now I have the same problem as matt1.

toshiba A135-S2386

---

### Post by Tribble on 2007-10-28
Thank you so much!! I followed the original post, and it worked for me! I've tried many other things and nothing worked, and this finally fixed my sound so it works through my headphones!

---

### Post by Unreal223linux on 2007-11-05
If you use the latest version of ubuntu(or derivatives, I'm using mint xfce right now). You no longer need to update alsa. You can skip those steps(which makes the process MUCH quicker).

If your on xfce replace gedit with mousepad.

---

### Post by nutz on 2007-11-06
This worked for me. Toshiba A105-S4284...

```
sudo gedit /etc/modprobe.conf
```

Paste this into the file...

```
options snd-hda-intel model=auto
```

Save and reboot!...

---

### Post by Stanley Krute on 2007-11-06
Thanks so much. That brought sound back for me. (I had it in 7.04, but lost it with the upgrade to 7.10). My machine's a Toshiba Satellite A-105 S2031

---

### Post by Stanley Krute on 2007-11-06
Just realized my post was ambiguous as to what worked. Nutz's post, #44, was the one:

> **nutz said:**
> This worked for me. Toshiba A105-S4284...

```
sudo gedit /etc/modprobe.conf
```

Paste this into the file...

```
options snd-hda-intel model=auto
```

Save and reboot!...

---

### Post by brosch91 on 2007-11-07
thanks for the help:) i have a toshiba satellite l35 s2174 and this works great thanks man! didnt think i'd ever get the left speaker working!

---

### Post by ejonestexas on 2007-11-11
The Steps above worked for my Toshiba Satellite laptop.  However I only get sound from the left speaker and not the right one.  Also when I connect headphones is only left.  When headphones are connected the laptop speakers dont turn off.

Im thinking it might be a setting under alsamixer?  I played with the settings and dont remember the dafault now

EJ

---

### Post by JunCTionS on 2007-11-17
it worked on Feisty for my Toshiba Satellite A135-S4677.
Not so much for Gutsy.

system appears not to recognize my soundcards.
anyone found a fix for this?

---

### Post by JunCTionS on 2007-11-17
oh well... gave on ALSA (didn't even know it was an option before) and welcomed the OSS.
worked for my Satellite A135-S4677 with Gutsy
here's the walkthrough
[http://ubuntuforums.org/showthread.php?p=3768914#post3768914](http://ubuntuforums.org/showthread.php?p=3768914#post3768914)

---

### Post by Laidbacklux on 2007-11-22
So, I have a Toshiba A135-4527, it sounds like people have gotten sound working on similar models, but I think I have tried so many things at this point that this fix isn't working for me...any suggestions on getting my laptop back to a place where this fix might work...besides fresh install?

---

### Post by andrewj100 on 2007-11-28
I've tried everything here, after following the instructions at the begining my speeker now has a no entry sign over it and if I click it I get 
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Any ideas?

Everything in Gutsy works great except sound.

---

### Post by JunCTionS on 2007-11-30
I still suggest switching to OSS (instead of ALSA). I worked for my Toshiba Satellite A135-S4677. Except for Skype and Kopete apparently still trying to use ALSA so no sound from them (and Skype sometimes doesn't open demanding sound to work and sometimes opening without sound).
what's your computer model?
I'm currently sort of busy, but I'll soon try hard to fix Skype and Kopete (and probably other KDE apps that aren't using sound properly but I haven't noticed).

---

### Post by stanton816 on 2007-12-01
Thanks so much!!! i was so tired of trying to fix this!!:guitar:

---

### Post by marquee moon on 2007-12-05
This works fine on my Toshiba L30. 
Thanks!

---

### Post by Spirotot on 2007-12-05
HAHA! Yes! Thanks! This actually worked... I've been trying for days (with ALSA, and OSS, PulseAdudio...), and could not get my sound to work properly... But this took like 5 minutes. And it works perfectly (even the little external volume knob works now!). Thanks! :D

edit: I forgot to tell you guys my computer model... It's a Toshiba Satellite A135-S4527. Thanks again.

---

### Post by Ur of Persia on 2007-12-21
> **Unreal223linux said:**
> 
```

sudo gedit /etc/modprobe.conf

```

You will be prompted for your user account password. When you type it will look like nothing is happening but thats just a security feature.

In the text file that pops up enter this and save it:

```

options snd-hda-intel model=6stack-digout

```

Once saved reboot your computer
.


Hi there, second day with Ubuntu. I am using Toshiba L30 and installed 7.10

Sound works except for my headphones. When I plug in my headphones the speakers  get mute but no sound from headphones. I tried your above fix and and it works. In my case the Headphone sounds were tied to the PCM, unmuting them and increasing the volume solved the issue.

Thanks.

---

### Post by gail on 2007-12-22
I have a P105 and I have been looking around for a fix for my sound now for weeks. So far nothing. Geeze I tried all this already .. 

I have the hda-intel sound card also and still I have no results. I am so frustrated and annoyed that I am almost to the breaking point.

I was told too disable my touch pag in bios and still nothing. 

Anyone have details on how to fix me up?

Mel

The only way I could get any sound out of the P105 was with Mandriva 2008 Live CD.  I am not sure how they do it but I think if they can........Ubuntu can!!

---

### Post by techgeek_us on 2008-01-01
> **jeffc313 said:**
> thanks so much! confirmed to work on my brother's new Toshiba Satellite A135-S4656 (he is a brand new linux convert, and he chooses it over vista!)

I have this same model and have not been able to get things working.  Can you please be a bit more specific about which options in the thread worked for you?  Did you have to create /etc/modprobe.conf?  What did you put in for the model of sound card?  What version of the alsa driver did you use?  Thanks in advance.

---

### Post by techgeek_us on 2008-01-20
> **techgeek_us said:**
> I have this same model and have not been able to get things working.  Can you please be a bit more specific about which options in the thread worked for you?  Did you have to create /etc/modprobe.conf?  What did you put in for the model of sound card?  What version of the alsa driver did you use?  Thanks in advance.

I fixed this using information in this thread: [http://ubuntuforums.org/showthread.php?p=3475485](http://ubuntuforums.org/showthread.php?p=3475485)

Specifically, post #235 seems to have done the trick.

---

### Post by Mal5494 on 2008-01-25
> **gail said:**
> I have a P105 and I have been looking around for a fix for my sound now for weeks. So far nothing. Geeze I tried all this already .. 

I have the hda-intel sound card also and still I have no results. I am so frustrated and annoyed that I am almost to the breaking point.

I was told too disable my touch pag in bios and still nothing. 

Anyone have details on how to fix me up?

Mel

The only way I could get any sound out of the P105 was with Mandriva 2008 Live CD.  I am not sure how they do it but I think if they can........Ubuntu can!!

Hi Mel,
This is my first post and I am a newbee to Linux. I too have a P105 and the sound does not work.  I tried the code at the beginning of this thread but the result was:

alsamixer: function snd_ctl_open failed for default: No such device

Like you it is becoming rather frustrating.

Have you had any response?

Mal

---

### Post by joe-the-indian on 2008-02-06
Now I hear! Works for my Toshiba Satellite L30-113 - Many thanks! :)

---

### Post by ser_enity on 2008-02-10
Thank you so much for this, you are the best!! I was about to play some laptop frisbee down the hall...

---

### Post by wrgarrett on 2008-02-11
I and at least one previous poster encountered this error:

alsamixer: function snd_ctl_open failed for default: No such device

Can anyone help us out here?

---

### Post by wrgarrett on 2008-02-11
Problem solved!

This worked for me and was simple, easy and quick!

[http://ubuntuforums.org/showpost.php?p=3619736&postcount=71](http://ubuntuforums.org/showpost.php?p=3619736&postcount=71)

---

### Post by Mal5494 on 2008-02-11
> **wrgarrett said:**
> Problem solved!

This worked for me and was simple, easy and quick!

[http://ubuntuforums.org/showpost.php?p=3619736&postcount=71](http://ubuntuforums.org/showpost.php?p=3619736&postcount=71)
Yes, it worked for me also.  But guess what - still no sound!

---

### Post by wrgarrett on 2008-02-12
duplicate post

---

### Post by uBrendon on 2008-02-22
This is what I get on the last step any help would be great.

```
brendon@brendonslaptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by uBrendon on 2008-02-23
Anyone? I would love to keep using ubuntu, but with no sound I'm going to be forced back to using XP. :(

---

### Post by neoroses on 2008-04-01
you my friend are a F****NG genius i love you been struggling with this on my packard bell for so long!!!!!

---

### Post by zackymcharvest on 2008-04-08
the method made me get this error when doing alsamixer
"alsamixer: function snd_ctl_open failed for default: No such device"

and when i click the vloume button i get this "No volume control GStreamer plugins found and/or devices found."

what do i do!!!

---

### Post by ikebowen on 2008-04-16
I actually had a similar problem; a friend found that while the issue is fixed in Gutsy, the fix can be applied in Feisty with the following:

```
sudo apt-get install linux-backports-modules
```

Worked for me. Happy little African drum sounds upon reboot. Good luck -

---

### Post by lostit on 2008-04-26
hi, i'm a newb to linux and thought i'd give it a shot, in particular HARDY HERON, however i'm suffering with similar prob with sound, i have used original fix and although it did give me sound i also have prob with background static all the time which is very loud. is there anything i can do to fix this

using a Toshiba L30

---

### Post by natetheinfamous on 2008-05-05
you... are... a... GENIUS!!!!

I've been trying to get this to work on my Satellite L35-S1054 for years, I'd just about given up on it. Yay!! no more rebooting to windows to watch movies!!!!

---

### Post by Tomsolomon on 2008-05-05
I could kiss you man........
This also works on the L30-134 ( PSL-33e )
Pure genius, thanks.

---

### Post by Newbee_KK on 2008-05-17
After searching through the forums for one complete day, solution I found was 

sudo /etc/init.d/alsa-utils reset

--------------------------------------------------------------------------
Toshiba Satellite R25
Kubuntu 8.04

---

### Post by n8makar on 2008-05-21
wow out of EVERYTHING i have tried across google this is the only thing that worked for my toshiba satellite l35-s1054. huge props to you thanks a billion times over. headphones and speakers work perfectly.:)

---

### Post by rigoberto27 on 2008-05-27
hi!

i'm using a Toshiba Tecra A9, and Kubuntu 8.04. Sound worked out of the box, but speakers doesn't mute when i plug in headphones. I tried every recipe in this thread, but it doesn't solve the problem. Then, i read <https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaTecraA9>, which states:

Current Issues
1. Plugging in speakers to the headphone jack does not mute the laptop speakers

afterwards, i read the same page, but for the A8 model, and there the solution was:
sudo echo "options snd-hda-intel model=hippo" >> /etc/modprobe.d/alsa-base

now i can use my headphones! It was my only issue with this laptop...


thanks,
Rigoberto

---

### Post by hidinginthemountains on 2008-06-14
I have a Toshiba A100-VA1 that this *basically* worked for. I'm running 8.04 Hardy, and sound was working, then I interupted an install of somethings in Synaptic today and broke all sorts of things. A less noobish user probably knows a way to revert whatever changes were just made, but I don't.

When I rebooted a while after the aborted install I had a "whitescreen where my desktop should be (sound was working). I reinstalled fglrx and other such things, rebooted, and had a proper desktop again. But now I had no sound.

I tried a few things none of which worked, then came across this thread.

First attempt failed during "make" mentioning something about CFLAGS ...I did a little googleing and figured this failure may be because I wasn't getting the newest version.

The only change I had to make to get it to work was to grab

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)

instead. I only had to do the first set of instructions (up to and including the reboot) and sound works again now.

Since going to 8.04 from 7.10 I've had some sound issues notably with Neverwinter Nights (NWN), which I have to force to use ALSA to get any sound. The sound still chugged and popped at some points in the game, I'm looking forward to seeing if this might fix that "by accident".

Thanks Unreal223linux for the original post!

---

### Post by pbenway on 2008-07-12
> **ikebowen said:**
> I actually had a similar problem; a friend found that while the issue is fixed in Gutsy, the fix can be applied in Feisty with the following:

```
sudo apt-get install linux-backports-modules
```

Worked for me. Happy little African drum sounds upon reboot. Good luck -
After all I've been through to get my sound back... this little line of code solved it all! ikebowen, you're my hero of the day! THANX!

---

