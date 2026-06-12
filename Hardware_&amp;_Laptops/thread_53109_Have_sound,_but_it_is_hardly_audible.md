---
title: "Have sound, but it is hardly audible"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by aussieskin on 2005-07-30
Finally got my sound to work using this link [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)
very excited about that part...although...

It is super quiet I can hardly hear it...

in alsamixer I have MASTER and PCM on 100% and have been through every other option turning them up to see if it works...but it doesnt...

have also right clicked on my speaker icon -> open volume control and made sure nothing is muted in the playback tab. I also went into preferences and tiked every box. Still sound I can hardly hear.

Is there another sound section to check and adjust? And also what about Ubuntu sounds, like new mail, people loggin into kopete and sending me messages etc. I dont seem to be getting any of those sounds.

have done a few searches but not turned anything up...hope someone can help

Thanks guys..and girls of course

---

### Post by heimo on 2005-07-30
Well, only one thing comes to my mind: are you sure you haven't connected your speakers to line out (instead of speaker out)? Does the volume level have any effect on volume?

---

### Post by aussieskin on 2005-07-30
[QUOTE=heimo]Well, only one thing comes to my mind: are you sure you haven't connected your speakers to line out (instead of speaker out)? Does the volume level have any effect on volume?[/QUOTE]
 just tried the other plug and no....It seems to be in the right one....If I put it in the other plug there is no sound...

But yeah, when I try and alter the volume by clicking on the speaker it has no affect, alshtough in xmms when i turn it's volume right down there is no sound, but when i turn it up there is one volume..

---

### Post by heimo on 2005-07-30
This is a very long shot, but try System->Preferences->Multimedia System Selector, select different outputs and for each one, click Test button - you should here a continuous sine-wave kind of tone.

---

### Post by aussieskin on 2005-07-30
[QUOTE=heimo]This is a very long shot, but try System->Preferences->Multimedia System Selector, select different outputs and for each one, click Test button - you should here a continuous sine-wave kind of tone.[/QUOTE]
 okay did that....
tested esd and got the Beeeeeeeep
alsa and got the beeeeeeep
oss couldnt find the pipeline...

anyway...all the beeps were at the same level of beeep....

so i started xmms again and the sound is the same

loving all your quick replies though!

---

### Post by heimo on 2005-07-30
Ok... back to alsamixer. Check that no channel is muted. You can toggle state with m key - see that every bar is turned at least half way. Keep the alsamixer open, play something, toggle the channel selection (it's on far right, there are more options than show on one screen unless you have very big terminal window), change it using up/down arrows, mine says 2ch, 4ch, 6ch and so on.

My amplifier is connected to the light green round 3.5 minijack, but I can also get sound from light blue connector if something else than 2ch is selected. Maybe this has some effect on your system too?

---

### Post by aussieskin on 2005-07-30
[QUOTE=heimo]Ok... back to alsamixer. Check that no channel is muted. You can toggle state with m key - see that every bar is turned at least half way. Keep the alsamixer open, play something, toggle the channel selection (it's on far right, there are more options than show on one screen unless you have very big terminal window), change it using up/down arrows, mine says 2ch, 4ch, 6ch and so on.

My amplifier is connected to the light green round 3.5 minijack, but I can also get sound from light blue connector if something else than 2ch is selected. Maybe this has some effect on your system too?[/QUOTE]

done that...turned everything on and up....the only one i dont have on is the IEC958 cause that was on which was the problem...so i tunred that off and got sound...

oh and its not the speakers cause they work fine on the windows machine...

hehe...nothing is ever simple when it comes to things I do!

---

### Post by heimo on 2005-07-30
Great you found the solution! :D Enjoy the sounds.

For me, this night (it's 4pm local time), I'm going to listen Spacemusic hosted by TC (in Rotterdam, Holland) - when he gets his weekly podcast uploaded and servers back up.
[http://spacemusic.libsyn.com/](http://spacemusic.libsyn.com/)

---

### Post by aussieskin on 2005-07-30
no id dint find the solution though!

I have got sound but it is still really quiet

---

### Post by heimo on 2005-07-30
Oh! I misunderstood. You probably have gone though all the settings in alsamixer? I'd still bet that the connector is in wrong output... but I'm running out of ideas. This is weird problem.

This is again just a very faint idea, but have you tried turning IEC958 on and changing its value (one bar to the left) through PCM/Analog/IEC958. For me, those have no effect whatsoever.

Can you post output of lspci and lsmod  | grep snd?

Maybe you don't have mixer device loaded. Don't know. Never had that problem.

---

### Post by aussieskin on 2005-07-30
okay
lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
0000:00:0b.0 Communication controller: Lucent Microelectronics V.92 56K WinModem (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

lsmod | grep snd
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

And I tried turning the IEC958 on and chaning its value etc...no luck


and here is all my alsamixer settings....
Master=100 
  PCM =100    
Surround=100  
Center  =100
   LFE =100     
 Line   =100  
Line-In   = on (cannot give a value though)
  CD =     100
 Mic = 100    
Mic As C  = on (cannot give a value though)
Mic Boos = on (cannot give a value though) 
Mic Sele   = Micl
&#9474; IEC958 = on  (cannot give a value though) 
  IEC958 C= off (this is the one that if it is on gives me no sound at all)
 IEC958 C = on   (cannot give a value though) 
IEC958 P = on with one bar (33)
IEC958 P - analog
 PC = 100
Speak = 100
   Aux = mix
    Mono Out = mix
<External> = off

---

### Post by heimo on 2005-07-30
I'm quite lost. This one - snd_intel8x0 - looks like your sound module. There are couple lines which don't look too good (unknown device), but don't neccessarily have anything to do with sound. 

What does your: cat /proc/asound/cards say? I have a different chipset, but mine says:
 ```
0 [V8237		  ]: VIA8237 - VIA 8237
					 VIA 8237 with ALC655 at 0xbc00, irq 22
1 [UART		   ]: MPU-401 UART - MPU-401 UART
					 MPU-401 UART at 0x330, irq 10

``` 

You could try restarting hotplug, type
 ```
sudo /etc/init.d/hotplug restart

``` 

Then open /var/log/messages
 ```
less /var/log/messages

``` 
press shift+G to go to the end of the file and check couple dozen last lines for any errors and lines with snd / sound in them. Anything interesting? (q to quit)

---

### Post by aussieskin on 2005-07-30
cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with CMI9761 at 0xdc00, irq 18

means not a lot to me that one!
And I did the other bit but could find not lines in about the last 4 dozen lines that even had snd / sound in them!

hmm...I think it seems I may have to tolerate extremly quiet sound...:-(

---

### Post by aussieskin on 2005-07-30
oh and one thing....

My Ipod has just stopped mounting....

Is that because I restarted hotplug without unplugging it first? I kinda didnt think to do that.... I hope I can fix that. I have had to reformat the ipod already twice because of things going wrong

and i have to go to bed now....very tired and getting mad!

thank you soooo much for your help...I will be back tomorrow!

---

### Post by heimo on 2005-07-30
Hmm.. yes, that hotplug may have stopped your ipod autodetection, but it should not be permanent change. I don't normally recommend rebooting... I'd just try to start the hotplug - restart actually stops the service and then starts again, so it should be normal, but if that doesn't help, go ahead and reboot the system.

With the module name I found all kinds of threads about problems with sound, but couldn't find anything really useful - anything that would be exactly like your problem. Are you using passive or active loudspeaders? Can you use some other audio source to check cables and speakers?
[http://www.ubuntuforums.org/showthread.php?t=26567]("http://www.ubuntuforums.org/showthread.php?t=26567")
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+735.&chip=SI7012&module=intel8x0]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=SiS&card=SiS+735.&chip=SI7012&module=intel8x0")

The fact that you can hear any sound (even though very low volume) suggests that the card itself is ok, and so is the sound card "driver", but it may have somtething to do with mixer or hardware itself. Have you recently used that sound card (in Windows, perhaps) ?

:-/ Hopefully some other people with similar problem or any other ideas to this mystery will pop up and give their input. If there's not other way... there're always inexpensive soundcards... It's probably not worth couple days sweat to get this working, unless you enjoy debugging and solving mysteries. :)

---

### Post by aussieskin on 2005-07-31
Yeah its a strange one thats for sure.

I have been toying with linux on and off for a few years, but never actually got past playing with a knoppix live cd. Then I decided that the only way for me to actually put the time in to give linux a go was to totally get rid of Windows altogether, Which I did. We do have another windows computer, but I am sticking to ubuntu and ubuntu only. 
So in short, the sound card **was** used in Windows...

Unfortunatly there arent any other speakers I can try on this linux machine, as the others in the house all have to plug into monitors, and my monitor doesnt support that. But I did try pluggin my speakers into the windows computer, and they worked fine :-( . I think I might go and invest in some new speakers though anyway, as these are pretty old, and may very well be the problem...

I do like spending multiple hours trying to debug and get things working though! Which is why I like linux a helluva lot better, because you can get to the code..even though I dont totally understand the code yet! But fixing problems is how you learn!

But thanks a bunch for all your help and ideas. I have now learnt 100 times more on how sound works, ie. alsamixer, oss, esd etc... and other little tricks to see what is going on! So even though I still have very quiet sound I have some sound at least!

Thanks again!

If I get it working I will make sure I post my solution!

---

### Post by heimo on 2005-07-31
You have great attitude! :D

---

