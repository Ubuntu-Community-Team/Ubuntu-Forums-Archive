---
title: "ATI Radeon 4850 Fan Tweak for Linux to prevent overheating?"
date: 2008-07-16
forum: General Help
---

### Post by shmoe010 on 2008-07-16
I recently purchased a radeon 4850 and installed it in my system. I followed the directions on the wiki and on forums here to get the drivers properly installed, and I have ATI's watered down catalyst for linux. Everything is functioning okay.

The problem though is that these cards are extremely hot because the firmware doesn't ever spin up the fan (I mean they idle at about 75C and can approach 100C under load.) If you google for '4850 fan fix', as I did, you find a solution (for winblows of course) that involves editing the profile's .xml file. I tried this on my winblows partition and it dropped my idle temp from 75C to 38C lol.

But I hate windows and want to cool it off in ubuntu, so if anyone has any idea where to start, or another program that can mod the fans, anything, I would be greatly appreciative. It pains me to boot into windows but it pains me even worse to watch my graphics card melt. :(

Thanks in advance for the insight!

---

### Post by shmoe010 on 2008-07-16
/bump

---

### Post by tuxxy on 2008-07-16
Thats rather hot, I just upgraded from ATI to nVidia and am so happy I did, the drivers are so much better and also performance.  Card idles at 58 degrees also, runs flawlessly unlike my ATI card which wouldnt run 3D !

---

### Post by shmoe010 on 2008-07-16
> **tuxxy said:**
> Thats rather hot, I just upgraded from ATI to nVidia and am so happy I did, the drivers are so much better and also performance.  Card idles at 58 degrees also, runs flawlessly unlike my ATI card which wouldnt run 3D !

I actually just switched to ati. In windows the card idles at about 38C, the problem is that the firmware is messed up and the driver doesn't tell the thing to cool off. There's a tweak in windows but i can't figure out one on here.

Anyone with linux and this card or the 4870 is likely having the same problem...

---

### Post by Viper666 on 2008-07-17
hmmm not really a "tweak" but it resolved the problem of a friend of mine. He got a 3pin-to-molex connector and the fan was ON all the time... as i said it's a bit offtopic (and probably louder too) but it worked... :)

---

### Post by soxs on 2008-07-17
> **tuxxy said:**
> Thats rather hot, I just upgraded from ATI to nVidia and am so happy I did, the drivers are so much better and also performance.  Card idles at 58 degrees also, runs flawlessly unlike my ATI card which wouldnt run 3D !
Well, I would say nvidia sucks 2D wise, just try KDE 4.1 pre and just for politcal responsibilty as an opensource user I just "had" to buy ati/amd products (and you should too).

For the cooling thingy, you should consider flashing your bios with a modified bios (don't ask me howto do that, I am using 3870 OC and idles at 41°C)
You might wait for fglrx 8.7 later this month, which may or may not fix it, bios flash can be evil and kill your card. So .. do it at your own risk of wasting ~200$

---

### Post by shmoe010 on 2008-07-17
> **soxs said:**
> Well, I would say nvidia sucks 2D wise, just try KDE 4.1 pre and just for politcal responsibilty as an opensource user I just "had" to buy ati/amd products (and you should too).

For the cooling thingy, you should consider flashing your bios with a modified bios (don't ask me howto do that, I am using 3870 OC and idles at 41°C)
You might wait for fglrx 8.7 later this month, which may or may not fix it, bios flash can be evil and kill your card. So .. do it at your own risk of wasting ~200$

Hehe, that's why I got it at best buy up the street. It was actually cheaper than newegg/zipzoomfly for whatever reason, and I've got 30 days to return it =)

---

### Post by Bateluer on 2008-07-25
I'm in the same boat with my 4870. Its a thing called the Early Adopter Tax. The first crop of 4850s and 4870s had a minor bug in their bios firmware that prevents the fan from spinning up properly and PowerPlay from working correctly. Later revisions resolved these issues.

But, the first of us who bought the cards get stuck dealing with the issue. Under windows, its an easy work around editting an XML profile file to manually control fan speeds. 

I'm curious as to how it will work under Linux, as I certainly don't want my 4870 idling at 78C. I've thought about putting an after market cooler on, but the model I want isn't available yet, plus there's the whole thing with voiding the warranty and such. 

Does anyone know how to do the fan tweak under Linux, or if works essentially the same way? I haven't installed Ubuntu on this box since I got the 4870 installed and reconfigured my partitions.

---

### Post by grigio on 2008-07-29
Does the latest driver (8.7) works better?
[http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ)

---

### Post by soxs on 2008-07-30
> **grigio said:**
> Does the latest driver (8.7) works better?
[http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ](http://www.phoronix.com/scan.php?page=news_item&px=NjYwNQ)
8.7 broke all my games, though running glxgears just fine and stating 3d acceration being availiable. 
You will hve to give it a shot, I heard some voices telling me, the driver fixed _A_LOT_ for them.
Though it's the first driver officially supporting 4000 series
Btw. no plural s ;-)

---

### Post by grigio on 2008-07-31
OT: what's happen by default when I boot from a Livecd Hardy 8.04 or Intrepid?

I've booked a pc with this card and I'd like to test it in the shop a bit

---

### Post by soxs on 2008-08-01
> **grigio said:**
> OT: what's happen by default when I boot from a Livecd Hardy 8.04 or Intrepid?

I've booked a pc with this card and I'd like to test it in the shop a bit

Stop hijacking threads, create your own, but the aswer is: As long as you don't install ubuntu to some hardware (usbstick, harddisk) you won't be able to install ubuntu und thus not be able to test the fglrx driver.

It may work, if you use a 4GiB(preferably 8GB) usbstick and install ubuntu onto that (Don't ask me wether you have to do this at the targeted PC or if you can setup it at home, which I "think" should be possible)

---

### Post by pinoytechie on 2008-08-07
I flashed my BIOS. no more xml file tweak. be it in MS or Ubuntu

---

### Post by soxs on 2008-08-07
> **pinoytechie said:**
> I flashed my BIOS. no more xml file tweak. be it in MS or Ubuntu

Which bios version + link...

---

### Post by pinoytechie on 2008-08-07
> **soxs said:**
> Which bios version + link...

I'm using a Sapphire 4850 (vanilla). A co-forumer from a local site got a Sapphire Toxic 4850. I asked him to send his BIOS, so that I could copy his FAN settings. I extracted my 4850's original BIOS. And edited it's fan settings. Patterned it using 4850 Toxic BIOS. Flashed my 4850 BIOS. Problem solved.

**Tools Used:**
[LIST]
[*][Radeon BIOS Editor]("http://www.techpowerup.com/downloads/1131/TechPowerUp_Radeon_Bios_Editor_v1.12.html") - for editing BIOS
[*][GPU-Z]("http://www.techpowerup.com/gpuz") - to extract current BIOS
[*][ATI Flash]("http://www.techpowerup.com/downloads/1123/ATIFlash_3.60.html") - for Radeon BIOS flashing
[/LIST]

---

### Post by soxs on 2008-08-08
I don't have windows running anymore, ar there any equivalent linux versions or did you run them with wine?

---

### Post by pinoytechie on 2008-08-10
Native.

well, you need only w1nd0ze for BIOS editing. If you can download a pre-fixed BIOS, you can flash it in DOS, using ATIFlash.

What exactly is your video card?

---

### Post by rafaellg on 2008-09-08
I did this hack using the tools posted above and it works fine.
Just in case someone wants to know how to see the card temperature, if you installed Catalyst run this command:

```

aticonfig --adapter=0 --od-gettemperature

```

This command isn't for crossfire.

Mine is reaching 57°C :) (much better than the 80°C before)

---

### Post by diobrando on 2008-09-11
Using the latest catalyst driver you can set the fan speed with aticonfig.

```
aticonfig --pplib-cmd "set fanspeed 0 65"
```

You can change the 65 to whatever you'd like. My 4850 was idling at 72C before I ran the above command, now:
> Adapter 0 - ATI Radeon HD 4800 Series
            Sensor 0: Temperature - 39.00 C

---

### Post by Rotarychainsaw on 2008-09-18
Is there a way to set the fan permanently? or just add it to the session?

---

### Post by NullHead on 2008-10-01
> **diobrando said:**
> Using the latest catalyst driver you can set the fan speed with aticonfig.

```
aticonfig --pplib-cmd "set fanspeed 0 65"
```

You can change the 65 to whatever you'd like. My 4850 was idling at 72C before I ran the above command, now:

Thanks! That's exactly what I was looking for! 

The whole editing the bios thing is just plain freaky to me ... I'm way to cautious to do such a thing. I'd rather spend 250$ to water cool it than to edit the bios ... it sound totally perverted, but I duno .. that seems safer than editing a bios.

---

### Post by porchrat on 2008-10-07
> **diobrando said:**
> Using the latest catalyst driver you can set the fan speed with aticonfig.

```
aticonfig --pplib-cmd "set fanspeed 0 65"
```

You can change the 65 to whatever you'd like. My 4850 was idling at 72C before I ran the above command, now:

I'm so glad I checked this thread...I had a 4850 idling at 81C...now it is down to a more comfortable temperature thanks to you guys.  It now sounds like there is a freight train living in my PC case, but at least the card is safe.

I was afraid of flashing the BIOS on the card, this is a much more comfortable workaround for me.  Will run like this until ATI can sort this problem out in a more official manner.

---

### Post by hobo89 on 2008-10-07
I was just searching the forums for 4850 as I've got a couple of problems, came across this thread and was having a look through. Turns out my card was also idling at 80 degrees. I'd never even thought about the temperature beforehand. Thanks for this.

---

### Post by NullHead on 2008-10-07
I'm curious .. how are you guys checking the temperature of your cards? I can check mine in windows, but I can't seem to figure out how to do this in Ubuntu.

---

### Post by hobo89 on 2008-10-07
> **NullHead said:**
> I'm curious .. how are you guys checking the temperature of your cards? I can check mine in windows, but I can't seem to figure out how to do this in Ubuntu.

In the terminal:
```
aticonfig --adapter=0 --od-gettemperature
```
It was posted on a previous page.

---

### Post by porchrat on 2008-10-08
As an update, my card now idles at around 44 degrees celcius...woohoo!  I really think this thread should be made a sticky.  At least for a while until this issue is resolved more permanently.

Lets face it there are probably a lot of people out there right now with overheating 4800 series ATI cards and I would hate to see their cards damaged as a result of that.

---

### Post by NullHead on 2008-10-08
Good idea. I agree, let this thread be stickified.

---

### Post by oblidor on 2008-11-13
> **NullHead said:**
> Thanks! That's exactly what I was looking for! 

The whole editing the bios thing is just plain freaky to me ... I'm way to cautious to do such a thing. I'd rather spend 250$ to water cool it than to edit the bios ... it sound totally perverted, but I duno .. that seems safer than editing a bios.

There is absolutely no need to run the fan at 65%. That is just wasting power and hearing. I flashed my card to do about 24% at idle/desktop work and 31 while gaming. Works nicely and almost no sound to be heard. Temperature is 50-60C. No need to go lower. So try with 0 24 or 0 31 depending your system and desire

---

### Post by porchrat on 2008-11-13
> **oblidor said:**
> There is absolutely no need to run the fan at 65%. That is just wasting power and hearing. I flashed my card to do about 24% at idle/desktop work and 31 while gaming. Works nicely and almost no sound to be heard. Temperature is 50-60C. No need to go lower. So try with 0 24 or 0 31 depending your system and desire

Unfortunately for me if I go lower the temperature rises rapidly.  I chose 65 after playing around with the speeds at increments of 5%.  My PC is in a corner so it doesn't really get awesome ventilation to begin with.  I agree with you though that not everyone should crank it up to 65%.  Personally I hate the noise and wish I could bring it as low as 31%, but that would mean having my card sitting at 70 degrees or more. :(

---

### Post by NullHead on 2008-11-13
My computer is in a corner as well and my case doesn't exactly have the best airflow either. I just finished altering my BIOS and it now will turn up the fan as needed. I have to set so it runs at 47% and it now idles at 60C which is good enough for me. Depending on how it does under load, I'll probably be happy with it as it is. 

I use mine for gaming in windows, so using the tools said earlier wasn't a problem for me. I feel better now that I don't have to worry when I'm running a live CD or installing things before I can get catalyst installed. 

:KS

---

### Post by porchrat on 2008-11-13
> **NullHead said:**
> My computer is in a corner as well and my case doesn't exactly have the best airflow either. I just finished altering my BIOS and it now will turn up the fan as needed. I have to set so it runs at 47% and it now idles at 60C which is good enough for me. Depending on how it does under load, I'll probably be happy with it as it is. 

I use mine for gaming in windows, so using the tools said earlier wasn't a problem for me. I feel better now that I don't have to worry when I'm running a live CD or installing things before I can get catalyst installed. 

:KS

You mean you altered the BIOS on the card?  Let me know how you did that as right now I just set that fan speed command to run on startup, and while it is working fine I would like to have the fan spinning up the way ATI intended.

---

### Post by NullHead on 2008-11-13
> **pinoytechie said:**
> I'm using a Sapphire 4850 (vanilla). A co-forumer from a local site got a Sapphire Toxic 4850. I asked him to send his BIOS, so that I could copy his FAN settings. I extracted my 4850's original BIOS. And edited it's fan settings. Patterned it using 4850 Toxic BIOS. Flashed my 4850 BIOS. Problem solved.

**Tools Used:**
[LIST]
[*][Radeon BIOS Editor]("http://www.techpowerup.com/downloads/1131/TechPowerUp_Radeon_Bios_Editor_v1.12.html") - for editing BIOS
[*][GPU-Z]("http://www.techpowerup.com/gpuz") - to extract current BIOS
[*][ATI Flash]("http://www.techpowerup.com/downloads/1123/ATIFlash_3.60.html") - for Radeon BIOS flashing
[/LIST]

That is where these tools are said. They need a working Windows OS to work, but if you already have one of those, I can walk you through it if you want. I used winflash instead of atiflash to upload the bios back to the card.

---

### Post by porchrat on 2008-11-13
> **NullHead said:**
> That is where these tools are said. They need a working Windows OS to work, but if you already have one of those, I can walk you through it if you want. I used winflash instead of atiflash to upload the bios back to the card.

I don't have a working windows OS on this machine.  Perhaps I'll try a boot disk to get the BIOS out, make the changes in ubuntu and the flash it using freeDOS.  Thanks anyway though I will give you a shout when I build up the courage to give it a go. :)

EDIT:  Perhaps at a later stage I'll attach a HDD from one of my other machines running XP and do it that way.

---

### Post by NullHead on 2008-11-13
> **porchrat said:**
> I don't have a working windows OS on this machine.  Perhaps I'll try a boot disk to get the BIOS out, make the changes in ubuntu and the flash it using freeDOS.  Thanks anyway though I will give you a shout when I build up the courage to give it a go. :)

EDIT:  Perhaps at a later stage I'll attach a HDD from one of my other machines running XP and do it that way.

I was very morbid during the process, but to my surprise it actually worked better than I thought it would. Now I'm wondering if I've voided my warranty ... Honestly, I wouldn't trust wine to do any of the things that need be done. 

As far as I know, there is no native linux tools to do the work, but I don know windows will get the job done. You can just format that hdd after you're done using it to patch the BIOS.

---

### Post by binbash on 2008-11-13
[http://forums.extremeoverclocking.com/t303889.html](http://forums.extremeoverclocking.com/t303889.html)

---

### Post by Bateluer on 2008-12-04
Guys, I'm having some trouble with this. 

I have a 4870, not the 4850. Neither the temp command nor the fan speed commands detailed in this thread function for me, generating errors. This was with the fglrx drivers that Ubuntu 8.10 installed from the repository, I'd post the version it installed, but I've hit an impasse below.

I then decided to download and install the fglrx drivers from ATI's site manually, as I've done with Gutsy and Hardy in the past. However, even following the [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") it fails to load the fglrx driver on startup. I'm left in a low res GUI with a handful of trouble shooting options that get me no where. I can load back into Gnome if I let it reset to the Mesa drivers, but then I'm back in the same predicament before. 

I experienced no issues installing the ATI fglrx drivers on 7.10 or 8.04, the documentation on the ubuntu site always worked without a hitch. However, I've been hesitant to leave the system booted into Ubuntu for low because of the fan speed issue. The 4870 will idle at 80+ Celsius. 

Any chance we'll see manual fan speed adjustments added to the fglrx 8.12 drivers next week or in the near future? Also, what am I doing wrong with installing these drivers on Intrepid? 

I'm considering wiping that drive and installing 8.04.1 and going from there.

---

### Post by NullHead on 2008-12-05
> **Bateluer said:**
> Guys, I'm having some trouble with this. 

I have a 4870, not the 4850. Neither the temp command nor the fan speed commands detailed in this thread function for me, generating errors. This was with the fglrx drivers that Ubuntu 8.10 installed from the repository, I'd post the version it installed, but I've hit an impasse below.

I then decided to download and install the fglrx drivers from ATI's site manually, as I've done with Gutsy and Hardy in the past. However, even following the [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") it fails to load the fglrx driver on startup. I'm left in a low res GUI with a handful of trouble shooting options that get me no where. I can load back into Gnome if I let it reset to the Mesa drivers, but then I'm back in the same predicament before. 

I experienced no issues installing the ATI fglrx drivers on 7.10 or 8.04, the documentation on the ubuntu site always worked without a hitch. However, I've been hesitant to leave the system booted into Ubuntu for low because of the fan speed issue. The 4870 will idle at 80+ Celsius. 

Any chance we'll see manual fan speed adjustments added to the fglrx 8.12 drivers next week or in the near future? Also, what am I doing wrong with installing these drivers on Intrepid? 

I'm considering wiping that drive and installing 8.04.1 and going from there.

Just re-install the driver from the ubuntu repository, and then install the catalyst control center. *Then* run the temperature commands and the fan command.

---

### Post by Bateluer on 2008-12-05
Thanks, that seems to have worked.

---

### Post by bmwiedemann on 2008-12-07
hi fellow Linuxers,

I wanted some more automated fan control as I did not feel comfortable running my fan at 5% all the time (which proved to cool it well for me)
but I didnt want to flash my card's BIOS to not loose my warranty.

So I coded myself a perl script to regulary check temperature and adapt fan speed accordingly.


```
#!/usr/bin/perl -w
# 2008 by Bernhard M. Wiedemann <bernhard lsmod.de>
# Licensed under GNU GPL v2 or later

use strict;

# those below default settings mean:
# spin fan at 80% at 80+ C
# spin fan at 8% at 56- C
my %options=qw(
hightemp 80
lowtemp 56
highfan 80
lowfan 8
debug 0
);

sub diag($)
{ print(@_,"\n") if $options{debug} }


sub setfan($)
{
	my($percent)=@_;
	system("aticonfig", "--pplib-cmd", "set fanspeed 0 $percent");
}

sub mydie($)
{
	setfan($options{highfan});
	print (caller(),@_);
	exit 1;
}



sub gettemp()
{
	$_=`aticonfig --adapter=0 --od-gettemperature`;
	if(m/Sensor 0: Temperature - (\d+\.\d+) C/) {

	} else {mydie "bad temp read: $_"}
	return $1
}

$SIG{INT}=$SIG{TERM}=sub{setfan($options{highfan}); exit 2;};

open(STDIN, "</dev/null");
if(!$options{debug}) {
	open(STDOUT, ">/dev/null");
	open(STDERR, ">/dev/null");
	if(fork()>0) {exit 0} # background
	if(fork()>0) {exit 0} # background
}

my $trange=$options{hightemp}-$options{lowtemp};
my $frange=$options{highfan}-$options{lowfan};
while(1) {
	my $t=gettemp();
	my $x=($t-$options{lowtemp})/$trange; # number between 0 and 1
	if($x<0) {$x=0}
	if($x>1) {$x=1}
	my $fan=int($x*$frange+$options{lowfan});
	diag "setting fan to $fan";
	setfan($fan);
	sleep 15;
}

```

I added this script into
/etc/X11/xdm/Xsetup
but on gnome you might want to put it into the /etc/gdm/Init/Default or so

If you like it or hate it, please tell me. Feedback welcome.

Ciao
Bernhard M.

---

### Post by ditane on 2009-01-12
That script worked great for me. Like you, I didn't want to mess with the bios just for the fan speed, especially since when I boot to Win it has a utility that takes care of it for me. At the same time I wasn't too happy with it running at 81C all the time either. Like I said your script worked great, so thank you very much for that. I may fiddle around with it a bit, but not much since I don't know perl very well at all.

To run on startup I found it easiest to add it to System>Preferences>Sessions 
I'm using Gnome in Intrepid.

---

### Post by bmwiedemann on 2009-01-15
hello ditane.
thanks for your feedback.
you can adjust the default setting in the top after
```
my %options=qw(
```

but the other part should just work as is.
maybe the sleep 15 at the end could need adjustment to change fan speed update interval... which is best done by moving it into the options part :)
improved version follows:

```

#!/usr/bin/perl -w
# 2008 by Bernhard M. Wiedemann <bernhard lsmod.de>
# Licensed under GNU GPL v2 or later

use strict;

# those below default settings mean:
# spin fan at 80% at 80+ C
# spin fan at 8% at 56- C
my %options=qw(
hightemp 80
lowtemp 48
highfan 85
lowfan 8
updateinterval 15
debug 0
);

$ENV{LD_PRELOAD}="libXinerama.so.1";

sub diag($)
{ print(@_,"\n") if $options{debug} }


sub setfan($)
{
	my($percent)=@_;
	system("aticonfig", "--pplib-cmd", "set fanspeed 0 $percent");
}

sub mydie($)
{
	setfan($options{highfan});
	print (caller(),@_);
	exit 1;
}



sub gettemp()
{
	$_=`aticonfig --adapter=0 --od-gettemperature`;
	if(m/Sensor 0: Temperature - (\d+\.\d+) C/) {

	} else {mydie "bad temp read: $_"}
	return $1
}

$SIG{INT}=$SIG{TERM}=sub{setfan($options{highfan}) ; exit 2;};

open(STDIN, "</dev/null");
if(!$options{debug}) {
open(STDOUT, ">/dev/null");
open(STDERR, ">/dev/null");
if(fork()>0) {exit 0} # background
if(fork()>0) {exit 0} # background
}

my $trange=$options{hightemp}-$options{lowtemp};
my $frange=$options{highfan}-$options{lowfan};
while(1) {
	my $t=gettemp();
	my $x=($t-$options{lowtemp})/$trange; # number between 0 and 1
	if($x<0) {$x=0}
	if($x>1) {$x=1}
	my $fan=int($x*$frange+$options{lowfan});
	diag "setting fan to $fan";
	setfan($fan);
	sleep $options{updateinterval};
}

```

---

### Post by NullHead on 2009-01-15
Good work there, bmwiedemann. I wish I still had my sock cooler on there to try this ;) 

I put a Zalman cooler on mine.

---

### Post by marcgh on 2009-01-15
I got the same problem on my HD4850 radeon.

Try the advice on this thread : 
[http://ubuntuforums.org/showthread.php?t=1039548](http://ubuntuforums.org/showthread.php?t=1039548)

Hope it will work for you

---

### Post by goodrench on 2009-02-02
If your ati driver is working correctly you could use a script that I wrote.
I use this on my htpc and it is a little hard using the command line with my remote.
[http://mybrainrunslinux.com/radeon](http://mybrainrunslinux.com/radeon)

---

### Post by SrBungle on 2009-02-27
aticonfig --pplib-cmd "set fanspeed 0 30" only works at active sesion, when i restart i need do it again
is posible automatic this?


ps: sorry for my very bad english

---

### Post by NullHead on 2009-02-27
> **SrBungle said:**
> aticonfig --pplib-cmd "set fanspeed 0 30" only works at active sesion, when i restart i need do it again
is posible automatic this?


ps: sorry for my very bad english

You can add that command to your rc.local or add it to your programs that load with your session. I suggest using rc.local.

---

### Post by nicobeukes on 2009-03-02
Here is what i found to fix the ati fanspeed,
I have a 4870x2 and i loaded ubuntu 8.10 64bit with the 9.2 cc installed it runs at 82 degrees - way to hot but this console command fixed my problem

aticonfig --pplib-cmd "set fanspeed 0 50

this sets my fan to 50 % and my gpu is now running at 41 degress, the only problem is that you need to do this everytime x starts up,

is there anyone who knows how to run this console command automaticaly at statup

regards
nico

---

### Post by SrBungle on 2009-03-02
thanks NullHead!

---

### Post by bmwiedemann on 2009-03-03
> **NullHead said:**
> You can add that command to your rc.local or add it to your programs that load with your session. I suggest using rc.local.

I think, rc.local does not work, because the aticonfig tool needs an X11 session with the DISPLAY variable set.

On opensuse I would add it to /etc/X11/xdm/Xstartup but on ubuntu, it would probably be in the /etc/gdm/Xsession or so and kubuntu probably having yet another place.

Ciao
Bernhard M.

---

### Post by ophion on 2009-12-16
Is there a way to monitor temperature and control fan speed without using the proprietary driver?

---

### Post by Draknof on 2010-01-10
It's funny because I have the opposite problem, my ATI 4850 fan is always at full speed and I can't cantrol it.

the commands returns it worked...

```
aticonfig --pplib-cmd "set fanspeed 0 30"
PPLIB command execution is Successful!
```


but it doesn't, the noise is still the same, as well as for the temperature (about 40°C)


Please help me, my compouter is so noisy !

---

### Post by NullHead on 2010-01-10
> **Draknof said:**
> It's funny because I have the opposite problem, my ATI 4850 fan is always at full speed and I can't cantrol it.

the commands returns it worked...

```
aticonfig --pplib-cmd "set fanspeed 0 30"
PPLIB command execution is Successful!
```


but it doesn't, the noise is still the same, as well as for the temperature (about 40°C)


Please help me, my compouter is so noisy !

Make sure you have the ATI Catalyst driver installed, and not a FOSS derivative.

---

### Post by Draknof on 2010-01-10
I just re installed drivers from AMD-ATI website then rebooted, and it's exactly the same.

---

### Post by NullHead on 2010-01-11
Can you link to the manufacturer's product page? I'm wondering if the fan on yours is special. 

I got a first gen card, so the fan hardly worked until I gave it some encouragement ... at least yours does something.

---

### Post by Draknof on 2010-01-11
Here is it : [http://www.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=137&prod_no=1686](http://www.msi.com/index.php?func=proddesc&maincat_no=130&cat2_no=137&prod_no=1686)

[http://www.sabmegastore.com/images/articles/c/CGMS-P-RHD4850-1.jpg](http://www.sabmegastore.com/images/articles/c/CGMS-P-RHD4850-1.jpg)

there is even the manual pdf

---

### Post by NullHead on 2010-01-11
It looks to me like that card has a two pin fan connector. Have you tried controlling the fan from windows? There's a setting in CCC for that. 

My Diamond 4850 has a 3 pin fan connector as seen here: 

(This picture is after I removed the heatsink to install a new [Zalman GV-1000]("http://zalman.co.kr/ENG/product/Product_Read.asp?idx=283"))
[http://stashbox.org/765347/PC050292.jpg](http://stashbox.org/765347/PC050292.jpg)

[http://stashbox.org/765344/ATICCC_win7.jpg](http://stashbox.org/765344/ATICCC_win7.jpg)

Note: I have overclocking features turned on for my card in windows. DO NOT change the overclock settings unless you know what you're doing.

---

### Post by Draknof on 2010-01-12
I'll tell you if the fanspeed control works on windows when I'll install it.

---

### Post by Draknof on 2010-01-31
I installed windows and the fan control doesn't work either. I've tried Rivatuner, catalyst center and ATi tools. 
So I've decided to flash my card to set up the fan speed according to the temperature. The flash was sucessful except that the fan speed is stil at 100% !

Is this video card disfunctionning or what ?

And back on Ubuntu, the system freeze after 2-3 mn. I figures the origin of the bug, it was because of the ATI driver. So I disabled them, and I'm currently using the free driver.

---

### Post by noveevon on 2010-03-19
ah what a mess, ive got the same problem with a really noisy fan going at 63% and driving me crazy...

i did use the ati catalyst drivers for a while, but it messes up my system everytime and this is the second reinstall ive had to do due to the problems i get see this thread: [http://kubuntuforums.net/forums/index.php?topic=3110567.0](http://kubuntuforums.net/forums/index.php?topic=3110567.0)

i found the solution or atleast i think i did here: 
[http://ubuntuforums.org/showthread.php?t=1313828](http://ubuntuforums.org/showthread.php?t=1313828)


but now i am unable to control the fan as that requires the fglrx drivers which gave me the problem in the first place....

so, if anyone knows how to control the drivers using another method then ati catalyst based scripts i would really be happy and would probably do a victory little dance in my living room...


i am using kubuntu 9.10 and have a HD 4850 card with a psycho fan...and my motherbord is asus p45q pro and has no options for gpu fan control..



created a thread here:
[http://ubuntuforums.org/showthread.php?p=8992963#post8992963](http://ubuntuforums.org/showthread.php?p=8992963#post8992963)

---

### Post by ZarathustraDK on 2010-04-22
I know this post is all about fan-problems on the ATI 4850 and so on, but I'll throw it out there anyway in case people are checking out this thread trying to decide whether or not to go for a 4850: Gigabyte (probably others too), have made a fanless version of the 4850 that, obviously, bypasses the problems mentioned in this thread. It could (according to the tests) run Crysis with no active airflow (as in "not even chassis-, cpu- and psu-fans close to it") with cooling-ribs at a 100 degrees for hours on end.

If memory serves me right, it was a Gigabyte GV R485MC.

---

