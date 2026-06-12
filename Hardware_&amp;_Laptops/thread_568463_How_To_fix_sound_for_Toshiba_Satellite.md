---
title: "How To fix sound for Toshiba Satellite"
date: 2007-10-05
forum: Hardware &amp; Laptops
---

### Post by squirage on 2007-10-05
How I solved my sound issues for my Toshiba A135-S4477.

Background:

	I started with Edgy a few weeks ago and started having sound problems as I received updates. At first I had sound, then it was every other time I booted, until finally I had none. I flailed around, following different guides and trying different things until I had wiped out any recognition of my sound card/chip.

What I Did:

	First I upgraded to Feisty. Next I finally had the epiphany that I should search for Toshiba sound on the forums. I will just say here that googling for info about configuring Linux on Toshiba laptops was fairly discouraging. All of the info is very old, or not for the exact model, or a different distro etc.

	The thread that helped me is [http://ubuntuforums.org/showthread.php?t=473422](http://ubuntuforums.org/showthread.php?t=473422) and the procedure for fixing the sound for hda-intel works nicely. Find it at HdaIntelSoundHowto - Community Ubuntu Documentation

Although this is basically just a regurgitation of these other threads, I'm going to repeat it here. You really don't have to be a programmer to do this. If I can do it, you can too.

1.Install required tools

		```
sudo apt-get install build-essential ncurses-dev gettext
```

		*Note: You also need libncuses5-dev to be able to compile alsa-utils.
			
		```
sudo apt-get install libncurses5-dev
```

		if you don't have it.

		*Also julian.coccia posted that you needed to run

		```
sudo apt-get install build-essential gettext ja-trans
```

		The point he is making is important. If you haven't yet manually compiled and installed anything yourself, you probably don't have the tools you need. You need build-essential and gettext for sure. I did not get ja-trans and everything installed okay for me. Mostly though I just wasn't paying attention when I compiled or I would have followed his advice. I can also corroborate that you will have problems if you do not have libncurses5-dev.

2.Install kernel headers

**EDIT

This one is wrong:
		```
sudo apt-get  install linux-headers-'uname -r'
```

This should read:
        ```
sudo apt-get  install linux-headers-`uname -r`
```

The left slant apostrophe apparently makes a big difference.  END EDIT&#65290;&#65290;

3.Download from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) the most current drivers. In this case the 15rc# series. On a personal note I had shied away from the developmental versions. So release your inhibitions and download them.

		I downloaded Driver, Firmware, Library, and Utilities. We shall see if not using the plugins becomes a problem. When you download with Firefox it downloads to the Desktop by default so my instructions will use that path.

4.Make installation directory

		```
sudo mkdir -p /usr/src/alsa
		cd /usr/src/alsa
		sudo cp ~/Desktop/alsa* .
		sudo tar xjf alsa-driver*.bz2
		sudo tar xjf alsa-lib*.bz2
		sudo tar xjf alsa-utils*.bz2
		sudo tar xjf alsa-firmware*.bz2
```

		It may seem self evident but I'll say it anyway. Make sure you are in the directory that you want to be in. At one point I was not paying attention and unpacking everything into my /home directory. Also you may want to specify the actual version number if, like me, you have downloaded multiple versions.

5.Compile and install alsa-driver. Here I'll use the version numbers that worked for me.

		```
cd alsa-driver-1.0.15rc3
		sudo ./configure
		sudo make
		sudo make install
``` 

		If for some reason you forget what the last command you input was, you can cycle through your previous commands by hitting the up arrow key. I found my self wondering at several junctures whether I had just typed sudo make or sudo make install?

6.Compile and install alsa-lib.

		```
cd ../alsa-lib-1.0.15rc3
		sudo ./configure
		sudo make
		sudo make install
``` 

		The two dots are just taking you up one directory, since all of your various programs are in the /usr/src/alsa. I'm just trying to be extra explicit because in my case it's hard to say if I was really paying attention to these somewhat obvious things when I failed in repeated attempts to fix my problem.

7.Compile and install alsa-utils.

		```
cd ../alsa-utils-1.0.15rc1
		sudo ./configure
		sudo make
		sudo make install 
```

		The rc1 is not a typo, as of now that is the only number available. And that is the numeral one, and not an L.

8.Compile and install alsa-firmware.

		```
cd ../alsa-firmware-1.0.15rc1
		sudo ./configure
		sudo make
		sudo make install 
```

		I personally questioned whether I really needed to install this. Upon reflection I considered the fact that I had failed at all prior attempts to fix my sound. So if someone recommended it, I should do it.

At this point the HdaIntelSoundHowto - Community Ubuntu Documentation thread tells you to reboot. You may want to hold off on that and add one more tweek before you do. More than likely you will also need to complete the instructions from the &#8220;Manually Specify Module Parameters&#8221; section.

1.Determine your model of sound card/chip

		```
cat /proc/asound/card0/codec#* | grep Codec
```

           or

		```
cat /proc/asound/card0/codec\#*
```

           or

		```
cat /proc/asound/*
```

		These are just three different ways of doing the same thing, more or less. The first two are both recommended in the HdaIntelSoundHowto - Community Ubuntu Documentation thread and the third one is by bvmou from the  [http://ubuntuforums.org/showthread.php?t=473422](http://ubuntuforums.org/showthread.php?t=473422) thread. 

	For me cat /proc/asound/card0/codec#* | grep Codec is best because it just returns what you are really looking for. The others return much more information that you may find hard to sort through. 

2.Determine model settings for your sound card/chip type

	Now that you know what the computer thinks is the sound card you need to look up that card in the ALSA-Configuration.txt file.

	Coming from windows I find it easier to navigate through the filesystem via the GUI instead of the terminal. Even though I read the instructions several times, I had difficulty locating that file. It is located inside your alsa-driver directory. In my case the full path was /usr/src/alsa/alsa-driver-1.0.15rc3/alsa-kernel/Documentation/ALSA-Configuration.txt.

	It's a long file and you need to scroll through it to find your sound card/chip. In my case about a third of the way down I find mine.
```

ALC861VD/660VD

	  3stack	3-jack

	  3stack-dig	3-jack with SPDIF OUT

	  6stack-dig	6-jack with SPDIF OUT

	  3stack-660	3-jack (for ALC660VD)

	  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)[

	  lenovo	Lenovo 3000 C200

	  dallas	Dallas laptops

	  hp		HP TX1000

	  auto		auto-config reading BIOS (default)
```

3.Edit /etc/modprobe.d/alsa-base

	```
sudo nano /etc/modprobe.d/alsa-base
```

	Scroll down to the bottom using the down arrow key and add

	```
options snd-hda-intel model=
```

	This is where that output from the previous step comes in handy. After the equals sign you want to type one of the things that seems to best fit your setup, i.e. if you have a Dallas laptop it should read

	options snd-hda-intel model=dallas

*Note- Since I have a Toshiba laptop I noticed that the entry above mine (ALC861/660) had a toshiba entry so I put that in. It did not fix the issue I still have with my headphones not working.

	Hit Ctrl-x to exit and it will ask you if you want to save. Hit y.

Now you should reboot, and you should have sound when you come back.

	For me there are only a few things that are unresolved:

1.No drums or sound of any kind when I log on
2.No muting of speakers or sound of any kind coming from the headphones.
3.alsamixer has completely vanished from my computer. I don't know if that matters or not?

	It is possible that I need to look at the bug information even though these alsa versions were supposed to obviate the need for any kind of patch.

	Thanks to mattheu for starting this thread, bvmou for pointing out these alsa packages, and julian.coccia for procedural tips.

Sorry if I made this too simple or stated the obvious. I just wanted to help others avoid the anxiety that I felt until I finally followed this exact procedure.

---

### Post by squirage on 2007-10-05
Head phone issue fixed with CalvinK's suggestion

options snd-hda-intel position_fix=1 model=lenovo

Added to the end of /etc/modprobe.d/alsa-base

---

### Post by crazyforpurple on 2007-10-10
hello, 

thank you for your "how to" i am currently working through it on my Toshiba Satellite A135-S7404 but when i get down to step 4 i get the following..............

mommy@mommy-laptop:~$ sudo apt-get install build-essential gettext ja-trans
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
gettext is already the newest version.
The following NEW packages will be installed:
  ja-trans
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.6kB of archives.
After unpacking 90.1kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe ja-trans 0.8-2 [16.6kB]
Fetched 16.6kB in 0s (24.4kB/s)
Selecting previously deselected package ja-trans.
(Reading database ... 126069 files and directories currently installed.)
Unpacking ja-trans (from .../ja-trans_0.8-2_all.deb) ...
Setting up ja-trans (0.8-2) ...
mommy@mommy-laptop:~$ sudo apt-get  install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
mommy@mommy-laptop:~$ sudo mkdir -p /usr/src/alsa
mommy@mommy-laptop:~$ cd /usr/src/alsa
mommy@mommy-laptop:/usr/src/alsa$ sudo cp ~/Desktop/alsa* 
cp: target `/home/mommy/Desktop/alsa-utils-1.0.15rc1.tar.bz2' is not a directory
mommy@mommy-laptop:/usr/src/alsa$ 


can anyone help me with what i am doing wrong here?

thanks, 

love lucy xx

---

### Post by squirage on 2007-10-11
Hi Crazyforpurple,

   I'm sorry that my directions didn't seem to work for you.

   The first thing off the bat that I noticed is that you are running Gutsy (7.10?), I did all this under Feisty(7.04). So it can be almost assured that there will be some new work arounds.

  The next thing is:
> mommy@mommy-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-headers-uname -r

I'm not sure what the problem is here. My assumption was that 'uname -r' was just the generic way to look at what kernel version you are using and get back the appropriate header file. I suppose one way to approach that would be to change:

```
sudo apt-get install linux-headers-'uname -r'
```

to

```
sudo apt-get install linux-headers-[actual kernel version]
```

where you keep the #.#.# format. I honestly can't remember my kernel version right now, for the sake of argument let's say it is 2.6.17 so I would write

```
sudo apt-get install linux-headers-2.6.17
```

Again, maybe there is something significantly different in Gutsy that I am not aware of.

And the last thing is this

```
mommy@mommy-laptop:/usr/src/alsa$ sudo cp ~/Desktop/alsa*
cp: target `/home/mommy/Desktop/alsa-utils-1.0.15rc1.tar.bz2' is not a directory
```

at the end of your command you should have

```
mommy@mommy-laptop:/usr/src/alsa$ sudo cp ~/Desktop/alsa* .
```

It is quite possible that the '.' missing at the end might be one issue.

As to why it would specifically single out the alsa-utils tarball, I am a little perplexed. If the file really is there you might try to unpack it and the copy those files instead of the compressed file.

I'm sorry my work around didn't do the trick for you. I'm sure there is a solution out there.

Let me know what you find out.

Good Luck.

---

### Post by Codix121 on 2007-10-12
squirage, I love you!

lol.

(Figure of speech of course)

man, you are awesome, you fixed my sound!!

I was amazed when i heard sound from my PC.
I was like, WOAH!

anyways,
aww man, i really appreciate it.
thanks bro!!


w00t w00t, codix has sound!
(im over excited for a noob, never been so excited
to hear sound from a pc).

anyways, ok im done glowing.
thanks man =]

---

### Post by mwero001 on 2007-10-12
Thanks man. That worked like magic. However, when i plug headphones onto the machine, the speakers still output sound. Am guesiing i've some tweaking to do.

---

### Post by squirage on 2007-10-12
Hi people,

  No problem. Like I said, this is the kind of post I was looking for and finally found by those other people I mentioned. I just tried to make it as simple and step by step as possible since I had failed so many times.

My how to is not really any different, just a little more specific to the problems of toshiba users.

Codix121,

   You're welcome. I felt the same way when I could finally get sound out of my laptop.

mwero001,

   Did you try this:

> Head phone issue fixed with CalvinK's suggestion

options snd-hda-intel position_fix=1 model=lenovo

Added to the end of /etc/modprobe.d/alsa-base

I probably should have gone back and edited my initial post. I'm not sure if the position_fix=1 or the model=lenovo did the trick, but my headphones worked like they are supposed to after that.

If you tried that then play around with the model settings to see if another works for you.

Good Luck.

---

### Post by aaronshaf on 2007-10-17
This worked great... thank you!

---

### Post by richwa4sxz on 2007-10-18
Just to add to the info, the linux-headers are installed in Gusty in the /usr/src directory.  I just put them in the path & compiled the alsa-*-1.0.15 release packages.

To cut down on the time in the driver re-compile, there is a 'with_cards' option that will only make the drivers for the specified cards.  I used hda-intel and emu10k1 to support the pcmcia audigy2 zs that has not worked completely until the 1.0.15 release came out.

It's amazing how much I've learned just reading the forums for a couple of weeks...:)

---

### Post by hsuwb on 2007-10-19
Hey thanks for posting this fix. I can't believe I finally got my sound working on my Toshiba A205-S4587 with Gusty (7.10) :D. I followed the exact procedure except for step two where I replaced 'uname -r' with the version number in the name of the folder in /usr/src as suggested by richwa4sxz.

And for anyone else in the same situation, the line I added for the last step was:
 options snd-hda-intel model=toshiba

---

### Post by crazyforpurple on 2007-10-19
hello, 

thank you for your previous help..... that little . makes all the difference! 

its taken me a while to reply as i have been trying different things and was also hoping that the latest release would just fix it but not so :( but with your help i  have now been speeding through the installation of all the alsa components but when i get down to the bit where you have to identify your sound card i get this:
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/card0/codec\#*
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/*
--- no soundcards ---
  1:        : sequencer
 33:        : timer
cat: /proc/asound/oss: Is a directory
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Oct 10 2007 for kernel 2.6.22-14-generic (SMP).
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ 

only the third of the 3 commands you gave gives me any kind of reply and it seems that the reply says i have no soundcard??? should i perhaps have rebooted my laptop before i ran these commands? what do you think? :confused:

thanks again xxx

love lucy xx

---

### Post by crazyforpurple on 2007-10-19
I NEED HELP!!!! ](*,)

i am going crazy with no sound please help!!!! i have tried all the steps on your tutorial but i still ahve no sound... because i couldnt find my chip/card type i guessed and tried just typing toshiba in that last command but it didnt work... now i tried "auto" and agian it doesnt work... it seems that ubuntu cannot even see my sound card????

please anyone have any ideas????

thanks in advance xxx

love lucy xxx

---

### Post by iwatts on 2007-10-19
Thanks for the help squirage!  This was driving me nuts since 7.04.  The strange thing is that sound worked just fine with 6.10 (wireless is another story).

All is well, even drums at login.  I also needed to use "dallas" rather than "toshiba".

My input sound from the microphone failed though with the following warning.

"Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'"

Guess it's some more searching to resolve that.

---

### Post by jmuzz on 2007-10-22
> **squirage said:**
> 
I'm not sure what the problem is here. My assumption was that 'uname -r' was just the generic way to look at what kernel version you are using and get back the appropriate header file. I suppose one way to approach that would be to change:

```
sudo apt-get install linux-headers-'uname -r'
```

to


I think the problem here is the **'** thingys around uname -r, they should be **`**
Correct way is
```
sudo apt-get install linux-headers-`uname -r`
```
They look very similar.

Gets past that step on mine (7.10), now to get through the rest :)
It says latest drivers anyway so step might not even matter at current time.

---

### Post by jmuzz on 2007-10-22
I have sound now (Toshiba A200 Gutsy 7.10) so dont have to return to Vista. :)

Only got through half the steps before another problem so I gave up, rebooted and theres sound so guess it was far enough.

Installing alsa-utils step failed because version of libasound is too old or something, so I didnt bother trying to fix that and rebooted from there. Didnt need to do the config changes luckily.

There is a slight pop from the speakers on shutdown.
On first reboot the drums and music were 100% volume, really loud. Once desktop had started the volume knob worked and I turned it down, was ok next reboot.
Headphones mute main speakers fine.

Display dimming with the FN keys still isn't working, it just thinks I am pressing the normal F6/F7 keys. But thats not really the sound, though probably related through the hda-intel drivers.

---

### Post by squirage on 2007-10-22
Hi All,

  Sorry to have been away, relatives are visiting and so I have been off of the computer.

Thanks to richwa4sxz and hsuwb for their input. I think what I did was create the alsa directory in /usr/src you may just have it in /usr/src and thats okay. The main thing is that you know where it is. It's also nice to know that for the A205-S4587 with Gusty (7.10) all you need is the command options snd-hda-intel model=toshiba.

crazyforpurple,

   I am sorry you are still having problems. I know exactly how you feel, for me things got alot worse before they got better. You posted this return:
```
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/card0/codec\#*
cat: /proc/asound/card0/codec#*: No such file or directory
mommy@mommy-laptop:/usr/src/alsa/alsa-firmware-1.0.15rc1$ cat /proc/asound/*
--- no soundcards ---
1: : sequencer
33: : timer
cat: /proc/asound/oss: Is a directory
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Oct 10 2007 for kernel 2.6.22-14-generic (SMP).
```

One thing that stands out to me is the ALSA version at the second to last line. Obviously this is probably due to the fact that you haven't rebooted.

I am also wondering if you need to be in ~/ before you run cat /proc/sound etc. I am not in linux right now and don't seem to have the long term memory to remember what I did at the moment.

If you test a few things and find that you don't have a sound card you may have to re-install ubuntu. This is exactly what happened to me when I was trying to fix my sound under edgy, upgrading to Feisty and then trying this fix is what worked for me.

jmuzz,

  Thanks for the update. I was not paying attention to the marks. I should probably edit the post.

```
sudo apt-get install linux-headers-`uname -r`
```

Is probably right.

That is weird about the Loud boot sound. I still to this day do not get any drum (or sound of any kind) while booting. But I don't care since sound seems to work. I don't know about the function keys, I hardly use them in windows so I haven't checked them in linux.

iwatts,

  That's weird about the mic, I haven't checked that out either.

If anyone has any thoughts/ advice on how to make this better, or knowledge of where the pitfalls that wipe out recognition of your sound card out, please share.

I wish I had all the answers but I just muddled through until it worked. If you get hopelessly lost try to go back to a clean slate. To this day ALSA mixer is totally gone from my computer and I don't know if that is something I should have or not.

Good luck all, thanks for posting and I'll try to check back more frequently.

Sean.

---

### Post by crazyforpurple on 2007-10-22
sean, 

thank you for taking the time to read this thread and respond to us all xxx

i am going to do some more research and also re-install the newsest release of ubuntu and hope that this might help too. i currently have the beta version that i guess updated when the newest version was released although i havent had many updates... i also have a few funky things going on with openoffice in this installation so i think its time to reinstall. i will let you know how i get on xx xI(keep your fingers crossed thati can replicate what i did the first time to get my wireless working again in the new install!)

love lucy xx

---

### Post by squirage on 2007-10-22
Hi crazyforpurple,

  No problem. I'm just trying to do my part as part of the community. Let us know how it goes. I'm still resisting upgrading to gutsy until I can get a few more things tweeked.

  I also double checked and it makes no difference where you are when you input:

```
cat /proc/asound/card0/codec#* | grep Codec
```

So it looks like you did what I initially did, zapped the sound card settings somehow.

Let us know how the re-install goes. I'm also going to edit the post to update some things in the procedure.

Good Luck.

Sean.

---

### Post by meburke on 2007-10-22
Well, this has been an interesting thread. However, I still don't have sound and don't really know what to do. I have a Toshiba Satellite A45-s150. I dual boot Windows XP and Kubuntu, and the sound works fine in Windows, so it must be my configuration. My chip is Intel 82801DB, but I didn't see it in the ALSA-base file, although the parameters came up fine during the compile. I did see a warning that "...is off by default..." but the message passed by so fast I didn't get a chance to read it all. I'm rusty at compiling in UNIX/Linux...Is there someplace to read the compile messages? I think the message said I was supposed to run ALSAGui or Alsaplayer or some thing to set the device to on. Now I need a step-by-step testing procedure to find out what is failing.

All-in-all the help in this thread have been very good. I had no problems or major warnings during the compile. Thanks for the help.

Mike

---

### Post by meburke on 2007-10-22
sorry, I should add that I have changed the last line in the -base file to different configurations and rebooted, and none of them give me sound. cat /dev/urandom > /dev/dsp gives me no sound, and I do have DSP type="alsaoss".

Thanks again.

---

### Post by squirage on 2007-10-23
Hi meburke,

  > I did see a warning that "...is off by default..." 

  This is a message telling you that ALSA is muted by default. So right click on your speaker icon and open Volume Control and double check that all the faders are up and the mute buttons are off.

> My chip is Intel 82801DB, but I didn't see it in the ALSA-base file

  When you run ```
cat /proc/asound/card0/codec#* | grep Codec
``` it will show you what card you have (unless you have wiped it) but that in and of itself will not get you sound.

  You need to go into the /usr/src/alsa/alsa-driver-1.0.15rc3/alsa-kernel/Documentation/ALSA-Configuration.txt. file. (I created the dir alsa in my /usr/src, your location may be different.

  One thing just occurred to me you say your chip is> Intel 82801DB but I recall that I knew what my chip was but that had nothing to do with the number that ```
cat /proc/asound/card0/codec#* | grep Codec
``` revealed to me as my sound card/ chip.

Also you say> cat /dev/urandom > /dev/dsp gives me no sound, and I do have DSP type="alsaoss".
 and you have totally lost me here.

So first thing is find your sound codec and look for it in the ALSA-Configuration.txt file in your alsa driver folder.

Good Luck

Sean.

---

### Post by broisaac on 2007-10-23
This is how I got the sound to work on my Toshiba Satellite running Ubuntu 7.10 Gutsy.

I encountered the same problems as 'crazyforpurple'.  I did everything they said to do on here, then Terminal informed me "--- no soundcards ---" !!!

So I reinstalled Ubuntu and then did only five of the original steps.

1. installed required tools -
```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install build-essential gettext ja-trans
```

2. Downloaded current drivers from [http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download") 

3. Made installation directory
```
sudo mkdir -p /usr/src/alsa
		cd /usr/src/alsa
		sudo cp ~/Desktop/alsa* .
		sudo tar xjf alsa-driver*.bz2
		sudo tar xjf alsa-lib*.bz2
		sudo tar xjf alsa-utils*.bz2
		sudo tar xjf alsa-firmware*.bz2
```

4. Compiled and installed the alsa-driver
```
cd alsa-driver-1.0.15
		sudo ./configure
		sudo make
		sudo make install
```

5. Compiled and installed alsa-lib
```
cd ../alsa-lib-1.0.15
		sudo ./configure
		sudo make
		sudo make install
```

then I restarted, and the sound worked fine... drums and all.

This may not work for others, but it's worth a try.

---

### Post by jcwill on 2007-10-23
Thanks for that broisaac. That was the trick I needed for my Toshiba A135-S4427. 

I had no sound card detected and now I have everything working, including the drums. I am now pulling all of my MP3s down so that i can have my music too!!

Between Squirage and you, I am now on my way! 

Have a good day! You just made mine!

---

### Post by Lleims on 2007-10-23
I have the same problem with the sound my laptop is a toshiba p105-s9337 with a sound card hd by intel. I have tried all the tutotials i have found and nothing seems to work in 7.10. Please help

---

### Post by squirage on 2007-10-23
Thanks broisaac,

  The first thing of note is that 1.0.15 is now the version, there are no developmental ones. It is interesting to see now how the alsa website lists these as being out since June 11th.

Then this is also the key if checking your codec reveals no sound card
 
> So _I reinstalled Ubuntu_ and then did only five of the original steps.


I'm glad you got it to work with only drivers and lib. I thought I might be gilding the lily, but since it worked for me I wasn't going to leave it out.

It is also probably unecessary to have ja-trans unless you need japanese. At least that is what bvmou had said might be going on with that one.

I hope crazyforpurple sees your post and tries it out.

Lleims,

Post the output of
```
cat /proc/asound/card0/codec#* | grep Codec
```
Or tell us if you get anything. Stick with it, you can figure it out.

Sean.

---

### Post by HannahK on 2007-10-23
Hi squirage, et al.

Ubuntu giveth and it taketh away!  I have a toshiba a200, of which I managed to get sound up and running about a month ago by patching the alsa driver.  I was then running Feisty.  I recently upgraded to Gutsy and the sound died again.  I decided to do a clean install, mainly because I had been playing around with alsa.  I still had no sound, found this thread, followed the instructions in post #1 and now I can't even access volume control.  I'm getting this error:

"No volume control GStreamer plugins and/or devices found."

cat /proc/asound/card0/codec#* | grep Codec gives me this:

cat: /proc/asound/card0/codec#*: No such file or directory


Any pointers??

HannahK

---

### Post by HannahK on 2007-10-23
broisaac, 

Which model of toshiba satellite do you have?  I tried your method but I still have no sound card apparently.  However I did not reinstall ubuntu first.   Looks like that has to be the next step.

---

### Post by SubZero_AK on 2007-10-23
Just another shortcut to make compiling your own modules easy.  I just get the module-assistant package, run it, and choose prepare my system for compiling.  In the terminal use the following:

sudo apt-get install module-assistant
sudo m-a

This will open up a curses version of the module assistant.  Select the PREPARE and let it run.  When it's all finished your system will be ready to compile whatever modules you need.

Cheers, 
Mark

---

### Post by broisaac on 2007-10-23
> broisaac,

Which model of toshiba satellite do you have? I tried your method but I still have no sound card apparently. However I did not reinstall ubuntu first. Looks like that has to be the next step.

My laptop is model A105-S2001. And you re definitely going to have to reinstall...I think what happen on mine was that the alsa-utilities kinda screwed up the Sound Controls and Mixers, apparently removing the other drivers and versions.

---

### Post by JaceMan on 2007-10-23
Excellent tutorial... unfortunately no sound for me on my Toshiba A105-S2081.  I can't really understand it.  In the past I had installed 7.04 and Linux Mint on this machine.  In both cases, sound was stubborn but I eventually got it to go.  Not so with 7.10.  This thing refuses to budge.

-Edited-

If sound is still "invisible vapor" after following the excellent tutorial provided here, try this:

```
sudo aptitude install ubuntu-restricted-extras
```

It worked for me!  

Note:  You will need access to the restricted packages in your source.list file.  If you don't want to mess with the command line, the easiest way to check it is to click on Application > System > Software Sources.
Under the "Ubuntu Software" tab make sure that the fourth option "software restricted by copyright..." is checked before running the command above in the terminal.

---

### Post by MMosley on 2007-10-24
Thank you, the steps in the original post worked for me.

---

### Post by RandyNose on 2007-10-24
Damn, I just killed a message to ya.. oh well.. It works. It seems to me that I had done a 

options snd-hda-intel model=

in the /etc/modprobe.d/alsa-base file  last time, when I tried this with Fiesty... oh well.. I went through the hoops and have a fresher version of the Alsa lib's for now...  :) 

Anyhow... It's WOORKINNNGGG! 

Thanks... 

Oh and this was on a Toshiba Satellite A135 S4656

Thanks...

---

### Post by crazyforpurple on 2007-10-24
hello squirage  

i want to thank you for all your help!! i am pleased to say that i reinstalled gusty on my toshiba satellite A135-s7404 and i have sound!!!! I did have to do some tweaking and thanks to jim sending me a link to this:

[http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)

I did it! I ahve posted in the above thread exactly what I did if anyone has the same laptop but i thank you all for all your help xxx

love lucy xxx

---

### Post by squirage on 2007-10-24
Hi All,

   It looks like those of you who have already moved on to Gutsy should take crazyforpurple's advice and look here

[http://ubuntuforums.org/showthread.php?t=530374](http://ubuntuforums.org/showthread.php?t=530374)

SubZero_AK and JaceMan,

  Thanks for the input ```
sudo aptitude install ubuntu-restricted-extras
``` and or```

sudo apt-get install module-assistant
sudo m-a
```

JaceMan, I think you saud this worked for you in Gutsy. SubZero_AK was yours also under Gutsy?

HannahK, 

   I think broissac already stated it but I'll say it again. If you are getting messages that say you have no sound card the only way I know to fix it is to re-install the OS. Also try JaceMan's fix or steps from the post recommended by crazyforpurple.

meburke,

  I don't know if you are still reading this post but some of these might work for you as well.

Later People.

Sean.

---

### Post by HannahK on 2007-10-26
crazyforpurple:

Thank you for your post - my sound works [again] now!  And I didn't need to reinstall thank goodness.  My mic is yet to work - a bit more tweaking needed, but I'm not complaining...!


HannahK

---

### Post by blop on 2007-10-26
Hi guys i have a Toshiba  p200 with the Intel Corp. 82801G (ICH7 Family) sound card,  intially on Feisty the addition of:

options snd-hda-intel model=3stack

in /etc/modprobe.d/alsa-base 

got sound working.

But now in Gutsy that is fixed...but there is still the issue with having no speaker mute when headphones are inserted...


I tried this...

> **squirage said:**
> Head phone issue fixed with CalvinK's suggestion

options snd-hda-intel position_fix=1 model=lenovo

Added to the end of /etc/modprobe.d/alsa-base

but no go...

any other ideas?

---

### Post by squirage on 2007-10-26
Hi blop,

  My suggestion would be to try and add the position_fix=1 and see what that does. So yours would read:

```
options snd-hda-intel position_fix=1 model=3stack
```

although Gutsy seems to be a little different in how it configures.

It's worth a shot.

---

### Post by blop on 2007-10-29
Thanks for the suggestion....but sadly it did not work.

---

### Post by gene6482 on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				sadly, i've switched to mandriva for the time being.  I definitely like Ubuntu better, but sound is a deal-breaker for me.  I tried to wipe the machine and go back to feisty, but I forgot how I got the sound working the first time, and couldn't get it back to where i had sound.  Hopefully the bug gets fixed and i can come back.

Bye for now.

---

### Post by squirage on 2007-10-29
Hi blop,

  It's too bad that the speaker mute with headphones doesn't work. It couldn't hurt to play around with more options. I have a habit of changing a bunch of things at once, so I am never really sure what is responsible for what. The P series may have something else going on.

Hi gene6482,

  Sorry to hear you gave up on ubuntu, but at least you found something to work with. I did not fully understand that bug report, but at least that is a reason.

One thing I will say is that I failed many times before actually fixing these problems. Most recently it took me about three tries to fix flash video sound which I detailed in this post [http://ubuntuforums.org/showthread.php?t=591486](http://ubuntuforums.org/showthread.php?t=591486)

Time is money, and there is a point at which it is not worth it to be noodling around with stuff instead of being productive.

Good luck with whatever you choose.

---

### Post by _mali_ on 2007-10-30
> **blop said:**
> Thanks for the suggestion....but sadly it did not work.

Same problem with Satellite A200 (PSAEC) :(. 

I tried many settings in alsa-base file.

---

### Post by blop on 2007-10-31
do you know if there is a list of settings that we can work through to determine the problem?

It could be that all is necessary is a simple but time consuming go at trial and error. Im willing to do that i really want to get all the hardwork for this laptop supported.

I really have impressed myslef with how much i have switched my work to an Ubuntu platfom..

---

### Post by squirage on 2007-11-01
Hi _mali_ and blop,

  I did do a cursory search for that sort of thing and did not come up with anything that jumped out at me. This is something that might be buried in the Comprehensive sound guide, but I have not had the time to wade through the 76 pages for an answer.

  I'm sure there is an answer out there, it's just a matter of whether or not one has the patience to find it.

Good Luck.

---

### Post by squirage on 2007-11-05
Hi All,

  I finally upgraded to Gutsy and found a few things. It asked me if I wanted to preserve my old alsa-base and I answered no because there seemed to be some new stuff in there. As I expected Ubuntu did not see my soundcard. I put my options back in the alsa-base and sound came back. Except I have now lost the loading music again.

  Now on to figuring out why Rhythmbox and totem don't work right anymore. And of course Kdenlive still doesn't have sound.

Sorry about off topic info. And this is without alsa 1.0.15, I'm still using the developmental ones.

So sound still works using this method under gutsy. Just thought I'd share.

---

### Post by mimagabooks on 2007-11-06
Smile  Toshiba a135-s4727 or 4527
Gutsy Seems to have broken this fix for Toshiba a135-s4727. I have worked on two of this model and two of the 4527 as well as a 2234. But so far only the models ending in 27 have broken.

But after allot of searching I finally found a solution download and install the realtek High Def Driver for linux.


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x which ever you like)

2. Run the first update with your package manager do not install other software. (except a compiler if needed)

3. install the Realtek High Def Driver (or as realtek calls it "codec")

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.

Note: If you have already done the driver install steps above and it didn't work in gutsy I will say the only way this realtek driver has work for us is a fresh install.

If there is another way that makes every thing work in gutsy please let me know.

---

### Post by flehnerz on 2007-11-06
I get the following error when trying to use sudo tar xjf alsa-driver*.bz2
the download locations are on the desktop and I do have the latest drivers ile.


frank@frank-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver-1.0.9rc4a.tar.bz2: Not found in archive
tar: Error exit delayed from previous errors
frank@frank-laptop:/usr/src/alsa$ 

what's going on?

---

### Post by squirage on 2007-11-07
Hi flehnerz,

   I'm not exactly sure what is going on from your description, but it sounds like it is not finding the files you are looking to unpack. You said> the download locations are on the desktop and I do have the latest drivers ile
and the the code you supplied shows that you are in```
/usr/src/alsa
```so my guess is when you run the tarball command in that directory it is looking for the files in that directory.
So the first solution is to copy them there, so in /usr/src/alsa```
sudo cp ~/Desktop/alsa* .
``` and don't leave out that period "." or perhaps a different tack might be```
sudo tar xjf ~/Desktop/alsa-driver*.bz2
```in the aforementioned directory.

The fact that you get > tar: alsa-driver-1.0.9rc4a.tar.bz2: Not found in archiveis weird but perhaps that was just the last driver that you had.

The fail safe method is just to type the full name of each file out that you want to unpack or do whatever with. I like the "*." method because I'm not so swift on the keyboard and make a lot of typing errors.

When I was having problems I started copying my terminal sessions to a word processing program so that I could go over the steps and see if there was something I had done wrong in the process. There are a lot of steps and a lot of typing and one wrong keystroke can mess the whole thing up.

Try some of this out and see what happens, let me know how it goes.

---

### Post by flehnerz on 2007-11-07
One problem....I used 

		```
cat /proc/asound/card0/codec#* | grep Codec
```

like you said and got

                ```
Codec: Realtek ID 268
Codec: Generic 11c1 Si3054
```

And I cannot find these in the configuration file. I do see this:
```
 Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ICH7), ATI SB450,
	       VIA VT8251/VT8237A

    model	- force the model name
    position_fix - Fix DMA pointer (0 = FIFO size, 1 = none, 2 = POSBUF)

    Module supports up to 8 cards.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

	  Model name	Description
	  ----------    -----------
	ALC880
	  3stack	3-jack in back and a headphone out
	  3stack-digout	3-jack in back, a HP out and a SPDIF out
	  5stack	5-jack in back, 2-jack in front
	  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
	  w810		3-jack
	  z71v		3-jack (HP shared SPDIF)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out

    Note 2: If you get click noises on output, try the module option
	    position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
	    register value without FIFO size correction as the current
	    DMA pointer.  position_fix=2 will make the driver to use
	    the position buffer instead of reading SD_LPIB register.
	    (Usually SD_LPLIB register is more accurate than the
	    position buffer.)

  Module snd-hdsp
  ---------------

    Module for RME Hammerfall DSP audio interface(s)

    Module supports up to 8 cards.

    Note: The firmware data can be automatically loaded via hotplug
          when CONFIG_FW_LOADER is set.  Otherwise, you need to load
          the firmware via hdsploader utility included in alsa-tools
          package.
          The firmware data is found in alsa-firmware package.

    Note: snd-page-alloc module does the job which snd-hammerfall-mem
          module did formerly.  It will allocate the buffers in advance
          when any HDSP cards are found.  To make the buffer
          allocation sure, load snd-page-alloc module in the early
          stage of boot sequence.

```

I am in the ALSA-Configuration.txt but I do not se anything similar to what you have. 
This is getting annoying. I just wish they would include these drivers compiled inthe next kernal or make some kind of easy installation...

---

### Post by squirage on 2007-11-07
Hi flehnerz,

  Amen to that.

Did you just give what you thought were the relevant portions of your configuration file? Because your right the info that you have does not give much help. I'm sure you have tried 3-stack etc. in the options file.

You could try what mimagabooks said

> download and install the realtek High Def Driver for linux.


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

However the only way I and several others have made this work is as follows.

1. Start with a fresh install of Gutsy (k,u,x which ever you like)

2. Run the first update with your package manager do not install other software. (except a compiler if needed)

3. install the Realtek High Def Driver (or as realtek calls it "codec")

This will install the alsa drivers (1.0.14), your sound wheel will seem to work (1-100%).
Each program will control its own volume level.


I also found this:

> After 3 days looking around and trying different settings... the following fixed my problem:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
Reboot and setup your sound settings

BTW, m-a re-installed alsa version 14 instead of the newer one 15 and it worked 

from delmir at this thread [http://ubuntuforums.org/showthread.php?t=596556](http://ubuntuforums.org/showthread.php?t=596556)

If what I posted hasn't worked for you, it's worth a shot.

Good Luck.

---

### Post by Michalxo on 2007-11-10
Hello ya all!

I have gutsy running on  toshiba A200 1gs (PSAECE). I had this similar problem with headphones too but thanks to this thread I managed to work it out :) THX 

For my notebook type worked adding these line to the end of /etc/modprobe.d/alsa-base file:
```
options snd-hda-intel model=lenovo
``` 
after many tries with others models.. few of them didnt worked (sometimes even headphones were deaf /dallas/hp). Finally lenovo (my last try) worked, so Iam happy as little kid ! :)

THX all folks again
   cheers Michalxo

---

### Post by originalsurfmex on 2007-11-17
hell all,

i just installed 7.10 yesterday, and only my sound has been giving me problems.  ive done the guides, including the guides on this page...and ive been particularly having the "no soundcards" problem.  i'm hoping to avoid a reinstall, but i'm also having another problem,
during bootup i get this message regarding alsa-base:
```

"ignoring bad line starting with 'opti'
```

i checked and rechecked the options line i added at the end of the alsa-base file, but its exactly the same as the suggestions:

```
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel position_fix=1 model=lenovo
```


my computer is a stock dell m2010, and i've tried several different forms of the "options" trick, including "model=dell"  my soundcard is a sigmatel HDA

im very new at linux and actually have been reading forums for what seem to be endless hours - a whole lot of learning going on here!  hopefully someone has fixed a similar problem with the 'ignoring bad line...'

---

### Post by originalsurfmex on 2007-11-17
by the way..i also get this message after i click the speaker icon in the upper right hand corner

```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

...gulp...

---

### Post by squirage on 2007-11-19
Hi Originalsurfmex,

  Just wanted to get back to you quick, I have been out of town and away from computers. The volume control message is related to the fact that it does not detect your sound card. Since I have upgraded to Gutsy myself I am back in the same situation.

  The first thing I would do is back up anything important. I wish I had. The next thing may be a clean install of gutsy. This seems to be what needs to happen when it won't see your card.

  The next thing is you need to find a recognizable sound card number with the grep | Codec command or which ever one you choose. You need this specific number and then to find it in the documentation to narrow down your choice of settings.

  I'm sorry I can't be more specific right now but I'm in the middle of another issue that I'm trying to resolve before the Thanksgiving Holiday.

Good Luck.

---

### Post by Schadenfroh on 2007-11-19
Any word if this (or if there is any fix) for the Conexant Waikiki no sound issue for the Toshiba P105 line?  If it does fix the problems with the Waikiki, I will put Ubuntu back on my notebook... no sound is the only thing keeping me from using it:(

---

### Post by squirage on 2007-11-19
Hi Schadenfroh,

  No clue about the Waikiki. Follow the instructions for listing your codec and then finding the options for that in the Documentation. Because knowing that I have ICH7 sound chip and the fact that the computer sees it as a Realtek ALC861VD is where it made all the difference.

  If you can get that kind of info then you have a starting point for this method.

Sean.

---

### Post by originalsurfmex on 2007-11-21
thanks for the feedback.

well i tried to update my alsa as per the instructions three times, each time it killed all recognition of any kind of sound hardware and i would get the "no soundcard" message.

so i have reinstall ubuntu along with alsa and everything else, and here is the output of the sound card query: 
```

Codec: SigmaTel STAC9221 A1
Codec: Conexant HSF

```
i added all the different "options" sugguestions, including those for my particular codec (dell, 3stack, etc) and still no dice.

i only have sound on my headphone jack, i still have no sound or microphone support anywhere else.

i did some more digging and according to this website my computer, the dell xps m2010 has 'partial' sound under linux (i guess thats all distros?)
[http://www.linlap.com/wiki/Dell+XPS+M2010](http://www.linlap.com/wiki/Dell+XPS+M2010)

i really truly love this laptop, and is really sad that i cannot use the 8 speaker plus subwoofer sound it has, and ubuntu is great...does anyone else have any other solutions/ideas?? i'll try anything, im only 1 month into linux, but im not too scared of the command line at the moment.

<as a side note, i am forced to use dial up as i am in a remote part of mexico for now, this means that i have been connecting using the linuxant softmodem driver...could this be what causes my alsa and all sound recognition on my computer to go nuts when i install the updated versions from source?>

---

### Post by DJazzy on 2007-11-28
first, BIG thanx for the help! :)

i had that problem (no sound) in Feisty and i had similar problem in Gutsy.

i have Toshiba Satellite L30-113 (Realtek ALC861-VD) and solved the sound problem by adding this
**options snd-hda-intel model=6stack-digout**

at the end of the alsa-base file.

nothing worked except that little thing (for both, Feisty and Gutsy) :)

i guess, it's important to be 6stack-**digOUT** because it wouldn't work for me with just 6stack-dig.

well, those were my 2 cents :) i hope i helped.

peace!

---

### Post by originalsurfmex on 2007-11-28
thanks so much for your 2 cents jazzy...buuut it didnt work on my laptop either.

i really appreciate everyone giving what they can to the community.  someday when i actually have knowledge to share ill follow your examples and post away.

in the meantime - im still searching for a solution to the linux/dell xps m2010 problem.

---

### Post by mandeepsmagh on 2007-12-02
Hi, guys

                It feels very encouraging to see toshiba users solving sound problems. My question is did someone try this on Toshiba P100 with conexant waikiki sound chip. All of my hardware information and steps I have gone through is listed here. [http://ubuntuforums.org/showthread.php?t=562835]("http://ubuntuforums.org/showthread.php?t=562835").

 I would really like to appreciate everyone's contribution, especially Squirage. Keep it up mate. Just beacuse of sound I had to leave wonderful world of Ubuntu.  Pls help me out !

---

### Post by squirage on 2007-12-03
Hi mandeepsmagh,

  originalsurfmex is the only other person who has mentioned conextant and I do not believe that he has been able to fix sound. Since I switched to Gutsy I have not been able to restore sound, and in fact I am in the process of getting ready to wipe my drive and do a fresh install. This is because ubuntu does not now see my sound card and I know of no other way to get it back.

  What lost me the sound card recognition was trying the backports fix. You can compile the alsa stuff yourself, one of the posters suggested getting the driver directly from Realtek and their version is 1.0.14, not the release candidates or 1.0.15.

  My other solution is to try some other distros as well to see if I can get them working better. I like ubuntu a lot but have had real problems with sound and video, the whole reason for trying out the OS, and in the interim have bunged up my bootloader to the point of Toshiba Recovery disks not working.

  I wouldn't worry about it for you though, that problem was caused by trying to recover partitions which has hopelessly confused Grub.

  If you are still wondering about alsa-base you just need to add those options at the end of the file. So just go to the last line, insert a new line after it, and copy or type in your line. Basically you are just adding another thing for linux to look for, in this case some specific info about your sound card/chip.

  Remeber that you need to find your specific model of card in the alsa-configuration.txt file and try the various options. Even then it might not work. The chipset and ICH numbers are not the ones you need to find but the actual manufacturer designation.

  Don't give up yet, but make sure you backup anything you absolutely need if you have the slightest concern about the commands you are running. Although I don't believe that any of these sound commands are dangerous.

  Good Luck and let everyone know what happens, good, bad or indifferent.

---

### Post by prog101 on 2007-12-07
SOLVED

Enable gutsy backports - this will detect sound-card and enable sound. 

If you have sound from both internal speakers and headphones at the same time, use the following fix. It works on my Toshiba A135-S7404.

1. Remove volume control icon from the top panel.

2. Edit file alsa-base: sudo nano /etc/modprobe.d/alsa-base
Add/edit the following line:
options snd-hda-intel model=lenovo

3. Remove sound module
sudo modprobe -r snd-hda-intel

4. Add sound module
sudo modprobe snd-hda-intel

Sound should work from internal speakers and get muted when headphones are used (headphone jack sense)

5. You may add the volume control icon again back to the top panel.

cheers!

---

### Post by originalsurfmex on 2007-12-07
for those using conexant, im not sure what the on-board sound driver thing from linuxant does, but here is what happened to me after three tries,

if i installed linuxant drivers and then updated my alsa, i would lose all sound card recogition and have to reinstall.

if i only updated alsa from source, and never messed with linuxant (i ended up buying a zoom modem, man i hate dialup) - then alsa would update just fine.

...however i still dont have sound either way, but im not givin up!

---

### Post by squirage on 2007-12-07
Hi prog101,

  Thanks for the help with the headphones thing, I know that is bugging a lot of people.

originalsurfmex,

  Keep plugging away. I am linuxless as of this moment. But mainly due to the fact that grub got completely squirrelly and I had to completely wipe my drive to use the recovery discs. There must be a solution somewhere.

---

### Post by sidcypher on 2007-12-08
squirage :

I am having the same problem with my Toshiba135-S4427.

I have tried most of this entire thread so far, and fresh installed twice.
once, my aircard wouldn't work, but printed out enough to try some fixes...
now my second, and trying the restricted packages route...

we will see...
The live cd, or either install hasn't ever detected the soundcard with 
```
cat /proc/asound/card0/codec#* | grep Codec
```

or even the
```
cat /proc/asound/*
```

now a am very much a newbie to linux, however i have messed with it in the past and understand some of what i am doing (with copy and pastes).

But this is killing me, since most tutorials needed a reboot getting it working with live cd (like i did with aircard) didn't seem to be a option...

now no Vista...no movies....no music....

if you get yours working...let me know! also what model laptop are you on?

thx
Cypher

---

### Post by squirage on 2007-12-08
Hey sidcypher,

  That is a major bummer. I am running an A135-4477. I got sound to work in Feisty but never in Gutsy. Then the flash video bug came back as well. Right now I have shifted my priorities back to actually working with the computer, rather than on the computer, but I will have some time once the pre-holiday frenzy subsides.

  Unfortunately when the OS won't even see your card, I don't know what to do other than a complete re-install. One thing I am looking into is the separate /home partition so that one can keep some of the settings intact. The main thing I don't understand is where the OS gets its basic information about the hardware and how it gets broken when you try to fix sound issues.

  As for Vista, did you jettison it yourself? Or did it just become unreadable? I had a major melt down but was able to recover the important stuff and then reformat the HD's and use the recovery disks to get back to something functioning.

  I truly believe that there is a solution out there, I haven't found it yet for Gutsy.

Keep me posted and I'll get back to you soon with what I find.

Good Luck,

Sean.

---

### Post by sidcypher on 2007-12-08
squirage -

yeah I dumped Vista myself, but not before I made a ghost image of it...So I can reinstall if need be, tho I would rather get the sound working...

broisaac -

I tried using your method, seeing as jcwill, has the same make and model of toshiba and it worked for them. No luck for some reason...

anyone know if a aircard could be causing a confilct....if i am not connected when I install it causes bad things that i don't know enough about linux to fix...

so this time i installed then rebooted to hd....did ```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install build-essential gettext ja-trans
```

then rebooted again (w/o aircard plugged in) seeing as i have the rest already downloaded to ext hd.

and did the rest of broisaac's suggestion...no luck...so i am here again...

This is a paste of what dmesg gave me concerning the sound

```
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   13.260000] snd_hda_intel: Unknown symbol snd_ctl_add
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_new
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   13.260000] snd_hda_intel: Unknown symbol snd_card_register
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   13.260000] snd_hda_intel: Unknown symbol snd_card_free
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   13.260000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   13.260000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   13.260000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   13.260000] snd_hda_intel: Unknown symbol snd_component_add
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   13.260000] snd_hda_intel: Unknown symbol snd_card_new
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   13.260000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   13.260000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   13.260000] snd_hda_intel: Unknown symbol snd_device_new
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   13.260000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   13.260000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   13.260000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   13.576000] lp: driver loaded but no devices found

```

Also here is my result from ```
james@Satellite:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
```

and of course ```
james@Satellite:~$ cat /proc/asound/*
--- no soundcards ---
  1:        : sequencer
 33:        : timer
cat: /proc/asound/oss: Is a directory
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Dec  8 2007 for kernel 2.6.22-14-generic (SMP).
```

This is also a fresh install, again. I have decided since I lost all my customization the first time, been reinstalling before each tutorial so I know the last one didn't mess it up.

Need to know anything else just ask.
Cypher

---

### Post by sidcypher on 2007-12-08
I GOT IT WORKING!!!

too bad the only real mp3's i have is audiobooks...never been SO happy to be bored..
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
I followed this to get it working....

No headphone...haven't tried mic yet...any suggestions?
really don't want this to break again...

options = levneo or whatever worked for headphones...i love 7.10!! 

l8r
Cypher
^ walks off listening to the footsteps!:)

---

### Post by Tedificator on 2007-12-13
Yay!

thanks Prog101, the headphone/speaker fix worked for my A135-7403 too.

---

### Post by alnp1987 on 2008-01-02
Hi all.
I have a Toshiba satellite A135-s7403. I'm new with ubuntu. i managed the wireless and the sound working following the next threads: 
wireless: [http://ubuntuforums.org/showthread.php?t=590093&highlight=atheros](http://ubuntuforums.org/showthread.php?t=590093&highlight=atheros)
sound: [http://ubuntuforums.org/showthread.php?t=539595&highlight=toshiba+audio](http://ubuntuforums.org/showthread.php?t=539595&highlight=toshiba+audio)
My problem is that i can use my headphones but when i change the volume either from the volume control or the wheel in the laptop the speakers unmute. if i reconnect the headphones the speakers mute back. if somebody can help me solving this I'll appreciate it.

---

### Post by jpilcov on 2008-02-04
hi everybody i have a problem downloading the necessary alsa archives, please if someone can send me this files i'll be really pleased, thanks

---

### Post by johnmcpot on 2008-03-17
Thanks man! 
Linux firs timer, and you all are making it really easy! Converting my Toshiba U305 to Linux, had a bit of a problem with the sound and the wifi card, but it's all solved now.

Thanks again!

---

### Post by browny254 on 2008-03-18
Cheers for the tutorial...finally got it working...kinda.

my volume control doesnt work, the volume wheel on the front of the laptop and the slider in the system tray only control the volume for the headphones, while the main speakers volume is controlled by something called PCM accessed in KMix.

Is there anyway I can get it so the volume wheel and system tray can control whichever speaker is in use (headphones or speakers)?


just something that may interst some ppl, i have just switched over to kubuntu and have experienced these problems. I was previously using Ubuntu and managed to get sound without having to do all of this. I cant remember exactly what I did because it was the first time I had ever used Linux, but I know it definatly wasnt this difficult. Funny thing also is that in Ubuntu my webcam didnt work, in Kubuntu it worked right away...

---

### Post by Tonsil Romancer on 2008-03-19
To make it work, I replaced "...15rc3" with "16" and removed the rc3.  I don't know what rc3 is or if I need it but I just got rid of it and now my sound seems to work.  *shrug*

---

### Post by kevinmoire on 2008-04-08
Okay so I'm TOTALLY frustrated. I've followed all of these instructions to a T.

I get to step 7.And nothing.

It's been a hot minute since I've installed ubuntu, and I'm running Ubuntu Studio if that helps.. Please someone with some expertise guide me a little bit.

Thanks...

kevin:KS

---

