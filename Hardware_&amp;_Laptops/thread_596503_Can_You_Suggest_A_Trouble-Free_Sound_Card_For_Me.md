---
title: "Can You Suggest A Trouble-Free Sound Card For Me?"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by discmaster on 2007-10-29
Hello! I am looking for a "known good" sound card that will work well with ubuntu "out of the box", no muss, no fuss. Please give me your ideas, cards that you have used or are using with good results, especially with sound capturing. I am a noob at this & not able to troubleshoot a lengthy problem, compile, etc. I am using an ASUS A8V-VM SE mainboard with onboard sound that is very problematic. 

What I need is a sound card that will easily do capturing for me, such as streaming audio, mic/line inputs, etc. Doesn't need to be a real high end card, lower entry level, middle level would be fine. I just need one that is known to work well with this OS. Also, please be aware that this mainboard has the VT8237A South Bridge, which is known to cause problems with some sound cards, the ECHO audio cards, for example. I know about the hardware compatibility lists, but I am looking for actual user experiences. Thanks to all for your suggestions.

Regards,
discmaster :)          :popcorn:

---

### Post by henklaak on 2007-10-29
Are you sure you do not want to fix the onboard sound?

I recently solved some sound issues on my Asus A7U, using this very good howto: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

You might want to check it out, learn a bit and save some money in the process.

Regards, Henk.

---

### Post by discmaster on 2007-10-29
> Are you sure you do not want to fix the onboard sound?lol! You obviously haven't checked out my other threads on here! :D If it is in anyway possible, sure, I would like to fix it. I will check out the link you provided. It is just that I am at my wits end with this problem.

---

### Post by henklaak on 2007-10-29
Oh sh*t, you too? I have been like that for 3 days, but in the end al my hard work, cursing and despair paid off!

The bigger the effort, the bigger the feeling of accomplishment. Just sit back, have your little moment of Zen and approach the beast again from yet another angle, haha!

Gr. Henk.

---

### Post by DoorGunner on 2007-10-29
the VT8237A South Bridge has a tendency to take over on your sound card. The hole trick to it is to blacklist the module so it wont start. Then any sound card will work fine afterwords.
In your /etc/modprobe.d/blacklist add the following lines

# Alsa problems
blacklist snd-via8237
blacklist snd-via82xx

 I had that happen with my Audigy and now it works great

---

### Post by discmaster on 2007-10-29
Ok, started to do the process; however, being a noob, I got stuck here.
>     *

      Setup installation directories

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz

Don't know what to do with that info. :confused:

Tried what i thought was right & got -
> tr@tr:~$ sudo mkdir -p /usr/src/alsa
tr@tr:~$ cd /usr/src/alsa
tr@tr:/usr/src/alsa$ 
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: cannot stat `/home/tr/downloads/alsa*': No such file or directory
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa*
cp: missing destination file operand after `/home/tr/downloads/alsa*'
Try `cp --help' for more information.
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa
cp: missing destination file operand after `/home/tr/downloads/alsa'
Try `cp --help' for more information.
tr@tr:/usr/src/alsa$ 


Assistance please?

---

### Post by henklaak on 2007-10-29
The instruction tells you to download the three archives:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

In your home directory (~), you should make a subdir "downloads" and put these three files in there.

Your system says: "cp: cannot stat `/home/tr/downloads/alsa*': No such file or directory"

Obviously, the directory "downloads" was not created, or you didn't put the three archives in there.

Just read the instructions carefully (especially the text between the command line instructions), they are really very good and should give you no problems.

Gr. Henk.

---

### Post by discmaster on 2007-10-29
> the VT8237A South Bridge has a tendency to take over on your sound card. The hole trick to it is to blacklist the module so it wont start. Then any sound card will work fine afterwords.
In your /etc/modprobe.d/blacklist add the following lines

# Alsa problems
blacklist snd-via8237
blacklist snd-via82xx

I had that happen with my Audigy and now it works great Okay, I was busy doing this & hadn't seen your later posts. After blacklisting, I am now able to record 1 channel of very scratchy streaming audio in audacity. :lolflag:

---

### Post by discmaster on 2007-10-29
Well, Gr. Henk; I have done this; 
> Just read the instructions carefully (especially the text between the command line instructions), they are really very good and should give you no problems. They seem  good, but when I try to follow them, it doesn't work for me, I just end up getting errors in the terminal. :(

I have the 3 downloads in my home directory, in a folder named "downloads", but I still can't make it work. > tr@tr:~$ sudo mkdir -p /usr/src/alsa
[sudo] password for tr:
tr@tr:~$ cd /usr/src/alsa
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: cannot stat `/home/tr/downloads/alsa*': No such file or directory
tr@tr:/usr/src/alsa$ 
I know this seems easy for you guys, but sorry, I just don't understand. I thought that changing the name from **alsa*** to the filename in that directory would do it, but I was wrong...Sorry guys, I am trying! :(

---

### Post by DoorGunner on 2007-10-29
Hey no problem.....everyone has to learn some time.... :)

> tr@tr:~$ sudo mkdir -p /usr/src/alsa
[sudo] password for tr:
tr@tr:~$ cd /usr/src/alsa
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: cannot stat `/home/tr/downloads/alsa*': No such file or directory
tr@tr:/usr/src/alsa$ 

mkdir is make directory
cd is change directory
cp is copy
the ~(tilda) is the same as saying /home/tr/ or in otherwords a shortcut

cp: cannot stat `/home/tr/downloads/alsa*': No such file or directory means that it cannot find the file. So it could be a spelling error or wrong file name.... ie downloads could be down load...etc

can you check to see if is actually there. Or you can use your menu gui ..... 

try using the ls command that means list

> ls /home/tr/downloads/

Sometimes cp works better with current location and Location to be copied to. ie sudo cp /current/location /final/location .... Just a suggestion. It will help to formalize in your mind what is actually happening with the codes. "man cp' in terminal will give a synopsis of what the cp or anycode for that mater is trying to do and it is an interesting tool if you become stuck with what codes actually do.

for some reason if all else fails you can just sudo aptitude install alsa-base. That should install every thing correctly. Aptitude takes care of dependancies better than apt-get.

---

### Post by discmaster on 2007-10-29
Good Grief!!! I was dumb! I had made a folder - **D**ownloads, not **d**ownloads!

So yes, the 3 downloads are in the "downloads" folder, but here again, I am running into snag when trying to complete the next steps. I did get this far;
> tr@tr:~$ ls /home/tr/downloads/
alsa-driver-1.0.15rc3.tar.bz2  alsa-utils-1.0.15.tar.bz2
alsa-lib-1.0.15rc3.tar.bz2
tr@tr:~$ sudo mkdir -p /usr/src/alsa
tr@tr:~$ cd /usr/src/alsa
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tr@tr:/usr/src/alsa$ cd alsa-driver-1.0.15rc3.tar.bz2
bash: cd: alsa-driver-1.0.15rc3.tar.bz2: Not a directory
tr@tr:/usr/src/alsa$ 


---

### Post by DoorGunner on 2007-10-29
hey no prob :) now it should look better for you. 

It's right cd means change directory. .tar.bz2 is a form of compression like a zip file. They are commonly refered to as tarballs. They collect a lot of info. .

It isnt really a folder so you cant change directory into it. when you gave the command sudo tar xjf alsa-driver*.bz2 it unroles the tarball (tar.bz2) into a folder. Try the cd like this

> cd alsa-driver-1.0.15rc3

and see what happens

---

### Post by discmaster on 2007-10-29
> tr@tr:~$ ls /home/tr/downloads/
alsa-driver-1.0.15rc3.tar.bz2 alsa-utils-1.0.15.tar.bz2
alsa-lib-1.0.15rc3.tar.bz2
tr@tr:~$ sudo mkdir -p /usr/src/alsa
tr@tr:~$ cd /usr/src/alsa
tr@tr:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tr@tr:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tr@tr:/usr/src/alsa$ cd alsa-driver-1.0.15rc3.tar.bz2
**bash: cd: alsa-driver-1.0.15rc3.tar.bz2: Not a directory**
tr@tr:/usr/src/alsa$
What about this?

---

### Post by DoorGunner on 2007-10-29
try it like this

cd alsa-driver-1.0.15rc

---

### Post by discmaster on 2007-10-29
Ok, looks like everything installed well, followed the rest of the instructions without a hitch. Rebooted, tried recording again...same situation. :( 1 channel records in audacity, weak & "crackly". I appreciate all your help, but I just don't know if it is meant to be with this soundcard/mainboard setup...

---

### Post by DoorGunner on 2007-10-29
Ok..... i used audacity before as well. Sometimes you have to play with the settings abit to get rid of the crackliness. I hate that too. 

Go to terminal again and type > alsamixer

right arrow across to mic and ensure that it is all the way up. (use the up arrow)

right arrow across a couple more and ensure mic boost says 00 not m. 

Now hit tab..... do the same for mic volume again.

esc to exit

------------------------------------------------------

In Audacity make sure your mic volume is all the way up too. 

Hopefully that helps too. Sometimes the quality of the mic and your sound card will make a difference in the output. Audacity for me is very sensitive to back ground sound and pics a lot up giving it a very unclean sound. But that I think is my crappy mic or tape recorders etc.

One last thing..... you might be able to go into your prefferences and change your quality settings and some filters to help get rid of the unwanted sounds. I havent really looked into that part but you might find something that helps.

---

### Post by discmaster on 2007-10-29
> right arrow across a couple more and ensure mic boost says 00 not m.  Don't have mic boost in my mixer.

> Now hit tab..... do the same for mic volume again.
don't have that either. Unfortunately, I have been all over these settings, by clicking on the vol. icon mute/unmute everything, played w/ vol. levels.All different settings in audacity. I just can't imagine that it is this difficult! :lolflag:

So you see, by my thread title, I am in the market for a sound card that is hassle free! :D

Been working at this sooooo many times since April, nothing has worked out. :(

---

### Post by DoorGunner on 2007-10-29
I feel your pain :lolflag:

Mine actually says mic boos.....not mic boost..... but i think you get that anyways....LOL

There is another program you might try..... I found it in a copy of Linux Magazine. I havnt tried it so i am not really sure if it will be any better. It is called LMMS media studio. It is in adept or synaptic if you want to try it.

It looks like a better quality product than Audacity. More buttons and whistles.

---

### Post by discmaster on 2007-10-29
> There is another program you might try..... I found it in a copy of Linux Magazine. I havnt tried it so i am not really sure if it will be any better. It is called LMMS media studio. It is in adept or synaptic if you want to try it.

It looks like a better quality product than Audacity. More buttons and whistles.I should have mentioned, I am not really sure the problem lies totally w/ audacity; I can't get any pgm. to record, not even sound recorder. I liked the looks of GNUSound, I was hoping that would work, but no go...

I guess I have deeper problems, of which I have yet to uncover. Again,  I do appreciate your assistance & suggestions. All has not been bad, I have learned some things from this thread! :)

---

### Post by discmaster on 2007-10-30
Well, for sound card recommendations; 

I was looking at the Creative Sound Blaster, but I came across this;

> **I recommend to use a different card because Creative Labs Soundblaster LIVE! does in fact changes bus registers on the fly, so chances of data corruption are increase. **

**Turtle Beach Santa Cruz is the easiest to setup and has very good duplexing. Its 5.1 output is a lot better than the LIVE card.**

Any Turtle Beach users here? can anyone confirm this? Would The Turtle Beach be a better choice? Also, will this card work with the VIA VT8237A Southbridge, that seems to be so problematic?

---

### Post by discmaster on 2007-11-01
My local O-Max had the Diamond Xtreme 7.1 in stock. It is supposed to work with linux, but I still get no capture from stream. audio. I am overlooking something? Anything? Is there anything at all I can do to make this pc cooperate with me?

---

