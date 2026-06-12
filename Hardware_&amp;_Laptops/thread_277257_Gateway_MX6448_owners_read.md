---
title: "Gateway MX6448 owners read"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by DavidGX on 2006-10-14
I just wanted to know if ANYONE who has a gateway (laptop) MX6448 (1gig ram, amd turion X2, radeom xpress 1150) has gotten sound to work with dapper.

---

### Post by American Techpusher on 2006-10-23
I am having the same exact problem. Do you have wireless working? 

Keith

---

### Post by michaelgulak on 2006-10-23
I am running the latest beta of Ubuntu on this laptop (typing on it from the wireless at school right now).  I got the wireless to work using the latest version of ndiswrapper.  I've heard stories of the Broadcom 4311 chipset working without ndis, but that was using an experimental reverse-engineered (I think) set of drivers that are included with the 2.6.10 kernel by default (I THINK).  I hope this helps a bit.

And as for the sound, no, I'm still looking into that.

---

### Post by American Techpusher on 2006-10-28
Can you point in the right direction for wireless drivers? I have ndiswrapper installed but I don't know where to locate the drivers.

---

### Post by towanda on 2006-11-16
Did you learn anything about getting sound to work yet?  I'm still trying to turn off the touchpad's hover-to-click feature, too.

---

### Post by DavidGX on 2006-11-27
Anyone with this laptop gotten sound to work yet?

---

### Post by usergentoo on 2006-12-19
Maybe file a bug report cause I have the same laptop with no sound.

---

### Post by GeoPirate on 2007-01-12
can anyone tell me wich version they installed on this laptop?  I have tried the regular and alternate 186 version of edgy and I havn't been able to get either to install successfully

---

### Post by usergentoo on 2007-01-12
Ive got the x64 version and now since sound is working I couldnt be happier.

---

### Post by zvandiver on 2007-01-12
> **usergentoo said:**
> Ive got the x64 version and now since sound is working I couldnt be happier.
Did you use the 64-bit version of Edgy?  I have the 32-bit version of Kubuntu on my 6447 with no sound.
How did you get the sound to work?
Zane

---

### Post by zvandiver on 2007-01-16
Alsa has posted version 1.0.14rc2 as of today.  The documentation specifically mentions the SigmaTel chips and Gateway laptops.
Quote:   Module snd-hda-intel
            STAC9202/9250/9251
	       ref		Reference board, base config
	       m2-2		Some Gateway MX series laptops
	       m6		Some Gateway NX series laptops

I will post results after installing.
Zane

---

### Post by zvandiver on 2007-01-16
I compiled the new alsa drivers/libs/firmware/plugins/utils and modified the /etc/modprobe.d/alsa-base file to identify the laptop model.
The new alsamixer showed the options for surround sound and front speakers that I didn't have before, but I still do not get any sound.  Also, when I rebooted, alsamixer would not start giving an error message "function snd-mixer-load failed: Invalid argument".
I had hoped this new release would work since it listed options for Gateway laptops.
I guess I will have to wait for the next alsa update.
Zane

---

### Post by Donn on 2007-01-16
Zane --

You may need to add this to your /etc/modprobe.d/alsa-base file at the end.

> alias snd-card-0 snd-hda-intel
options snd-hda-intel model=test enable-msi=1 probe-mask=1


Donn

---

### Post by zvandiver on 2007-01-16
> **Donn said:**
> Zane --

You may need to add this to your /etc/modprobe.d/alsa-base file at the end.




Donn
THANK YOU!!!!!
That worked.  My joy is complete.
Zane

---

### Post by Donn on 2007-01-16
Zane --

You got it.  Hopefully this works for lots of other folks too!  

Donn

---

### Post by ygolohcysp on 2007-01-30
Hello.  I'm extremely new to Linux, so I apologize first off for the simplicity of my questions.  I am currently looking at a post describing how to compile the alsa drivers, but I can't find the identifier of this particular sound card.  Is it STAC9250, or one of the other ones?  Also, the other post I'm reading just describes the compiling of the drivers.  Do I need to compile the libs, firmware, plugins, and utils as well?

As a side note, since I have the very same Gateway MX6448, I've noticed in the device manager that many things seem listed as unknown, such as the USB even though they seem to work.  Are other drivers needed for this particular chipset, or something?  Sorry for the novice-like questions.  I'm doing my best to make the switch.  Thank you in advance.

---

### Post by Donn on 2007-01-30
I think you typically just need to compile and install the drivers, unless there is functionality you're missing somplace else.  Check out this thread for directions on getting and compiling 1.0.14 rc2.

[http://ubuntuforums.org/showthread.php?t=276343&page=4](http://ubuntuforums.org/showthread.php?t=276343&page=4)

Also, try this to get the 'unknown' things known

sudo update-pciids
sudo update-usbids

Donn

---

### Post by ygolohcysp on 2007-01-30
Thank you for the reply, Donn.

I finally figured out the doc system on the alsa site, and found my soundcard on it.  Knowing it was a Sigmatel Chip, and the driver module having "intel" in it, I didn't know to look under ATI.  It suggested installing the drivers, libs, and utils.

In trying to do that, I found I didn't have the c compiler I needed.  Another thread on these forums helped out with that.  In trying to compile and install the utils, I found I didn't have the right ncurse libraries.  Again, another forum helped out with that.  So then I did the modprobes, added those two lines in, restarted, and the speakers work great!  Well, as great as any laptop speakers can work anyway.

My mic jack, however, still doesn't work.  I normally don't use it, but have a friend across the world at the moment that would like to use Skype.  I do have this setup for dual-boot with XP Pro, so I'll use that till I can do it with Ubuntu.  I've already found out that Skype in XP causes memory leaks serious enough to need restarting every so often.  It's the only program that does that for me.  Ironically enough, the forum that helped me out with the ncurse libraries was about getting mics to work with the hda-intel sound module, so I'll try there.

As to the other things, I tried those commands.  It may have helped, but there are still things that are "unknown".  I figure I'll go back into XP, and write down everything that's listed in the device manager, then compare with Ubuntu, and find what's missing that way.

Again, thank you for the help. :) 

ygolohcysp

---

### Post by t3hj3ff on 2007-04-16
Does anyone know the sound problem will be fixed in 7.04?? btw I have a MX3417 :(

---

### Post by scarab on 2007-04-17
I have a mx6447... under dapper I had no sound until I compiled ALSA drivers manually (sorry, I do not remember how, I followed some googled how-to)... however, only output works, no microphone... now I have edgy (upgraded via update manager), and this problem persists... however, under dapper, I had no wireless, that now appears to work well under edgy.
one thing is that with edgy I simply loose the Fn-arrow funcion to control display bright (I had it working well in dapper...)....
so, for having output sound, compile alsa drivers (google - alsa-drivers, dapper, gateway - and you´ll found some howto)...
for having microphone, I would aprreciate any ideas...

also for display brightness, that would be great!

hope that helped....

---

### Post by GeoPirate on 2007-04-20
I had the sound working fine on a mx6448 in edgy, until like a week ago (headphone jack and all), and there was an update, like a week ago but it broke my sound, I tried reinstalling alsa but it did nothing, still no sound at all now.

---

### Post by zvandiver on 2007-04-20
> **GeoPirate said:**
> I had the sound working fine on a mx6448 in edgy, until like a week ago (headphone jack and all), and there was an update, like a week ago but it broke my sound, I tried reinstalling alsa but it did nothing, still no sound at all now.
Did you reinstall from source?  I have had two kernel updates since I got sound working on my 6447, and I had to recompile and install alsa to get sound back each time.
Zane

---

### Post by scarab on 2007-04-20
I have a 6447, and no way for microphone to work...
take a look at the complete problem here: [http://ubuntuforums.org/showthread.php?p=2494237#post2494237](http://ubuntuforums.org/showthread.php?p=2494237#post2494237)

any help will be great!

---

### Post by JustLookingToHelp on 2007-06-23
Well I hope all these issues get solved soon. I just bought a Gateway MX6448 and wanted to put Ubuntu on it. I noticed that before I updated the sound worked but after the update... NOTHING. I looked and looked for about 7 or 8 hours and this is what I found for the sound card. I am running Ubuntu Feisty Fawn and sound works now. I found the answer on this web site... followed all the directions and was up and running within 15 min. Hopefully this helps.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Let me know if this works.

Now all I have to do is get the wireless to work.

---

### Post by yknott on 2007-07-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				gateway MX6448
purchased from tigerdirect

gnu/linux (kubuntu 7.04)
have had both 32bit and 64bit

uname -a
Linux 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

wireless? yes
bcm43xx

sound? yes
appended to /etc/modprobe.d/alsa-base
#       hda_codec: invalid dep_range_val 0:7fff
#       hda_codec: num_steps = 0 for NID=0x3
options snd_hda_intel probe_mask=8 model=auto

video? yes
"ati" - yes 
also "fglrx" - yes

restart/reboot? yes

shutdown? no
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868)

i let it unload as much as possible then hold the power button until the machine powers off; upon start up the reiserfs (3.6) file systems need to be checked and their journals replayed

---

### Post by derald on 2007-10-13
> **Donn said:**
> Zane --

You may need to add this to your /etc/modprobe.d/alsa-base file at the end.




Donn

Donn,

You rock, I tried for 6 months to figure this out and stumbled across your solution after a year. Now I finally have sound.

Thanks,

Derald

---

### Post by Selcal on 2007-10-21
did anyone get the wireless to work.  i found the instructions on this particular card but it just goes into a long drawn out Dell thing.  If i could at least get the .inf file i could install it but i can't find that file

---

