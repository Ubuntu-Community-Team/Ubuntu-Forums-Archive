---
title: "HP HDX16 Thread"
date: 2009-04-28
forum: Hardware
---

### Post by pokogr on 2009-04-28
Hi all, 

  I thought to start this thread in order to exchange info/problems   for the owners of HP HDX laptops.

I installed Jaunty with success. Everything seems to be working except the Remote Control.

I also had to add > options snd-hda-intel model=hp-m4 in the /etc/init.d/alsa-base.conf file in order to have sound.

I also noticed that when rebooting/shutting down, before system restarts, the monitor fades to a light blue color.

Anyway,
  glad to hear your experience or the things you might have done to overcome the problems I mentioned before.

Regards

---

### Post by knife on 2009-04-28
I've been using Intrepid successfully for about 5 months.  The things that don't work are:

remote/ir - it appears that there's no driver for the ENE CIR ir receiver, and I can't find any project that is creating new ir drivers

fingerprint reader - it's on the list for the fprint project, but there's no driver yet

mute button led/hardware volume controls - the buttons work, but it gets the hardware and software volume out of sync. The bass and treble softkeys don't work at all.

suspend to ram/disk - it won't resume from s2r (it's a known problem, apparently in the sata driver and affects all distros).  I get errors when resuming from s2d, but it comes back and seems to work fine.

I haven't tried the tv tuner.

---

### Post by pokogr on 2009-05-15
For the record: I found out that Vista's driver for the ENE CIR kept something somewhere that was causing problems for linux. I logged in to Vista and I uninstalled the driver. I now have the remote working fine for linux but not for Vista (doesn't bother me at all).

---

### Post by jackgu1988 on 2009-06-07
well i just got my HDX16 yesterday and installed ubuntu. i also have all these problems (monitor turns into blue-green-red etc before shutdown completely, suspend problem, fingerprint problem) but my remote just works! i was wondering if these problems are going to be solved because it is a pretty good laptop and it is a shame that it doesn't fully support linux!

---

### Post by knife on 2009-06-10
The suspend problem is fixed with the latest bios update (f.23, I think).

---

### Post by exutable on 2009-07-11
I wonder why the windows driver would affect the remote of a completely different operating system on a completely different partition?

---

### Post by exutable on 2009-07-11
I definitely couldn't get the finger print scanner working or the remote, any tips on either?

by the way for the sound I added the following to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=hp-m4

I don't think /etc/init.d is where alsa-base.conf is located any longer....

---

### Post by allianux on 2009-07-13
You may be interested in this post: [http://h30434.www3.hp.com/psg/board/message?board.id=Hardware&thread.id=4928](http://h30434.www3.hp.com/psg/board/message?board.id=Hardware&thread.id=4928)

---

### Post by exutable on 2009-07-15
The webcam doesn't seem to work either.........

---

### Post by lilkidz on 2009-08-15
My webcam works. Problems I'm having is that there's no sound coming from the speakers. With headphones on it works. Another problem is the card reader. I stick in my Memory stick duo adapter and the pro card and doesn't work. Fingerprint not working, standby not working.  Any solutions to these? Model HDX16-1358CA. Thanks

---

### Post by hovrashko on 2009-08-16
hello everyone!

I have fixed the sound on my HDX16 and have a problem with microphone, it's just doesn't work, any solutions?

my other question - how did you get installed fingerprint reader and remote?

thank you,
 regards

---

### Post by exutable on 2009-08-21
Sorry,

My webcam does actually work.  As of now there is no driver for the fingerprint scanner. Some people said that the remote works but I haven't been able to get that result.

I am going to "try" to write a driver for the fingerprint scanner but don't trust me.  I'm not great at programming Java or C++.

-Dane

---

### Post by exutable on 2009-08-23
Oh and I am trying to get people together to create this driver for the fingerprint scanner, I think the fprint mailing list is down.

If you have any programming skills or experience with USB interfaces or just want to offer some kind of help please contact me at [email]dane@daneshea.com[/email]

-Dane

---

### Post by bobthemilkman on 2009-08-28
For those of you who say that your webcam is working, was it working out of the box or did you have to do something to make it work?

I am very interested in making this webcam work.  I have an HP HDX 16-1375DX.

I really enjoy this laptop (particularly the nvidia graphics card).  The issues with the video and audio during shutdown are annoying, but not terrible.

I do, however, have an issue with my laptop that no one else has mentioned so far:
Sometimes if I shutdown (not restart), the computer does not turn off.  It goes through the shutdown process, then gets to the part where the monitor changes to weird colors, and then that's it.  It just remains turned on with the strange video output.  This is not a 100% occurance, but it does happen sometimes.  I'm running the nvidia proprietary drivers 185.18.36, and kernel 2.6.30.5.

---

### Post by spazznie on 2009-08-29
Did your computers come with [COLOR=#333333][FONT=arial] Intel Next-Gen Wireless-N Mini-cards? If so, did you have to download a driver for them? My HP is getting worse connectivity and download speeds than my 4-year old dell running Ubuntu and connected to the same network. 

And my webcam worked as soon as I downloaded and opened cheese. It was the microphone that needed extra tweaking before I could record sound. 
[/FONT][/COLOR]

---

### Post by hovrashko on 2009-08-30
..What about that microphone tweaking? can you provide details?

:confused:

---

### Post by spazznie on 2009-08-30
Due to other errors, I had to completely reinstall jaunty and..well, this is where I am right now with the microphone.

[http://ubuntuforums.org/showthread.php?t=1253799](http://ubuntuforums.org/showthread.php?t=1253799)

It's kinda unfortunate that no one is replying, as I've seen tons of other threads that died on this issue.

---

### Post by exutable on 2009-09-01
Yes please.... The microphone? and no I didn't have to download a driver.

I have the PRO/Wireless 5100 AGN [Shiloh] Network Connection

---

### Post by warped6 on 2009-09-05
I just picked up one of these to replace my STOLEN Toshiba (still kicking myself for that). Bad day all around yesterday. Anyway...

Adding that line to the alsa conf file fixed my sound problems. Yeah!

My remote does work, although when playing with it I hit the power off button. It works! But when I hit it again it got all weird. Is this the suspend problem I saw mentioned?

Still fiddling with the DVD playback.

The volume controls seem to be working for me.

On a side note. I bought mine from Best Buy. OK 2 stories...

1. Went to the first Best Buy. Said I was looking for a laptop with an nVida card. One guy said "Well you could buy one of the others and upgrade the video card." I looked at him and said "No you can't." He looked all confused then.

2. Went to second Best Buy. Said I want that one, pointing at the box behind glass doors. The Geek Squad guy asked "Do you want that pre-optimized or optimized?" My turn to look confused. "We take it in back and unload all the crap they load on." Ahhh... never mind I'm gonna take it home are REALLY optimize it. :-)

---

### Post by spazznie on 2009-09-05
Hey guys,

I'm sorry but after I got the mic to work, ubuntu completely failed on me. I reinstalled it and...the mic stopped working. I tried everything to get it working again but gave up and went back to vista >_>. 

I made another thread where I figured out the combination of codes to get the mic to work, but it causes the sound to shut off. 

[http://ubuntuforums.org/showthread.php?t=1253799](http://ubuntuforums.org/showthread.php?t=1253799)

---

### Post by hovrashko on 2009-09-07
[B]weird, hah? =)
 did you try it with just changing Alsa file(thal all what you can do)? the point is the outside port for mic is working, dont do what is on that link. just get external mic, untill someone come up with smarter solution for HP HDX laptops. And dont go back to Vista, WVista - it's bad move![/B]
:popcorn:

---

### Post by Thystra on 2009-09-14
I recently bought a HP HDX 16, and had sound issues with jaunty.  Tried the Karmic release and sound works great out of the box (haven't test the mic yet but speakers work fine).  Need to trouble shoot the webcam and all should be well.

---

### Post by exutable on 2009-09-16
The webcam works with cheese on Jaunty, but that's awesome to hear that it works in Karmic right away.

I can't wait until October!

---

### Post by jims2321 on 2009-10-13
I recently purchased an HP HDX16.  I keep getting and SR0 error when it is trying to detect the hard drive trying to install Karmic release.  Any thoughts on how to fix this installation issue.

Jim

---

### Post by exutable on 2009-10-18
Have you tried Jaunty considering that Karmic is still in beta??

I have successfully installed the beta though.

---

### Post by Kakofonix on 2009-10-28
Hello ppl!
Thanx for opening the thread pokogr!
pls change

/etc/init.d/alsa-base.conf

to

/etc/modprobe.d/alsa-base.conf

as this other user suggests bellow your post.

oh, also hp-dv5 instead of hp-m4 works too.

for newbies:

type in a terminal

 sudo gedit /etc/modprobe.d/alsa-base.conf

and add to the end of this file

options snd-hda-intel model=hp-m4

then type

sudo /etc/init.d/alsa-utils restart to start having sound and enjoy!

Also again for ppl starting up with ubuntu:

For you webcam problems
1-goto system-administration-synaptics...
2-write "cheese"
3-Select cheese and mark for instalation
4- install it
5- goto a terminal and write "cheese"
6- see your face in the webcam.

Sorry if I repeat stuff but I think its nice to have quick and easy solutions.
I spent a lot of time with this issues myself.

Oh, and pokogr, it would be nice if you would accumulate the solutions and keep them in the first post too.

---

### Post by jims2321 on 2009-11-05
Yes, I tried Jaunty same error about detecting device SR0

Jim

---

### Post by lilkidz on 2009-11-30
I'm using Ubuntu 9.10 x64 and my memory stick duo isn't being recognised. SD card is doing fine. xD I don't know as I don't use any. Webcam, speakers, mic, works well. Just that problem.

Edit: I clicked on Places at the top and authenticate to mount the memory stick duo. But it seems like it stays there now.

---

