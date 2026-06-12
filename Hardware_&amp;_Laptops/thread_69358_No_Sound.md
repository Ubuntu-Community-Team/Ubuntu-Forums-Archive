---
title: "No Sound"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by gabhla on 2005-09-26
I'm new, and eventually will get Unbuntu to work as I like.  Actually, I'm very pleased, the installation and configuration went very well exept no sound.  I've read and reread in the forum everything regarding sound, or lack thereof, alsa, configuration, etc., and still...no sound.  My sound card is recognized and when I run the live cd, sond is fine.  I tried to run alsamixer, alsaconfig but recieve back an error that alsa doesn't exist...(it does, even uninstalled then reinstalled it).

I've got hoary 5.04, P4, dual boot w/Windows, 80g, 512 ram.

Any ideas?

Thanks.

---

### Post by mlomker on 2005-09-26
What kind of sound card?

```

lspci | grep audio
lsmod | grep snd

```

Once you know that you can then look through **dmesg | more** and look for any possible error messages regarding the driver/audio.

---

### Post by GhostDawg on 2005-09-27
I have a friend who installed Warty version using cd disc and he told me that his Realtek AC'97 sound works with warty but when he upgrades to Hoary, he doesn't get sound once its upgraded.

Any ideas/suggestions?

Thnx.

---

### Post by gabhla on 2005-09-27
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)  

Above, soundcard...I also ran the other commands, didn't "see" any errors..but, honestly don't know what to look for....but did notice...

ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.

No clue what any of this means....

Really appreciate any help...thanks.

---

### Post by mlomker on 2005-09-27
> Really appreciate any help...thanks.

Please post the output of **lsmod | grep snd** and we'll make sure the drivers are loaded.  After that you can run through some of the [troubleshooting guides.]("http://linux.iuplog.com/default.asp?item=94639")

---

### Post by canadianwriterman on 2005-09-27
I know this is not a popular opinion and, believe me, I do enjoy lots of tweaking to "get things just right," but...

[LIST]
[*]When I installed Windows, Media Player was "just worked" with no problems.
[*]Windows automatically searched the Web for my printer driver and installed it when I hooked up my printer and then it "just worked" with no problems.
[/LIST]

With Ubuntu, some media players produce sound (like Totem) and others don't (like XMMS), even after spending hours seeking out plugins, codecs and what ever else people recommended trying. I still don't have sound with XMMS!

Ubuntu recognized my Canon S300 printer, but there is no driver. Foomatic SAYS it will support the printer, but it doesn't. So, I still can't print within Ubuntu.

In my opinion, when something is "packaged" for installation, such as XMMS, Foomatic and amaroK, everything should work after installation. None of those programs work for me and I've spent ages on the Forums, tweaking, and downloading to try to get them to work.

Just my opinion.

---

### Post by mlomker on 2005-09-27
> None of those programs work for me and I've spent ages on the Forums, tweaking, and downloading to try to get them to work.


That's easy to do when one company writes everything (Microsoft).  Linux is mostly a collection of unpaid programmers who write whatever they want to, however they want to, and then it is all thrown together.  Distribution creators, such as Ubuntu, try to piece them together the best that they can but there are limits because they have no control over the programmers.

The primary problem and the primary value of linux is that it is free.  There are limits to what you can do when you don't have the money to hire people.

---

### Post by canadianwriterman on 2005-09-27
I do understand. However, why WOULDN'T someone who develops a Media Player (like amaroK, for example) ensure that it can play common media, like commercial music CDs? If all the required pligin, codecs, dependencies and setting changes are known and available, why wouldn't the package include those? I still can't get amaroK to play ordinary CDs. From an ignorant layman's perspective, it would seem logical that a Media Player should be able to play common media.

---

### Post by mlomker on 2005-09-27
> why wouldn't the package include those? I still can't get amaroK to play ordinary CDs.

That has to do with copyright laws.  Other distributions, such as Linspire and Xandros don't do that to you.  Then again, they pay royalties to the proper people for those codecs and obtain written permission from Real, Macromedia, and whoever to include their 'free' but non-gpl licensed code.

---

### Post by canadianwriterman on 2005-09-27
Makes sense, sort of. I wasn't ware that you needed a licence to play standard music CDs on a Media Player. I thought that only related to MP3s. Anyway, you're right, it was two commercial Linux versions (Xandros and Linspire) that I was using prior to Ubuntu. The only reason I'm whining is that I'm 100% behind Ubuntu and much prefer it to Xandros or Linspire. Perhaps the solution is to present downloads of programs like amaroK differently. It would be better to say: "Download and install the base program here. If you need to play music CDs, download and install this. If you need to play MP3s, download this..." etc.

I think what makes it confusing and frustrating for us ex-Windoze users, it that things like plug-ins and additional dependencies are very "fuzzy." One is never clear on what needs to be installed to make things work. Forums like this are a wonderful help but, even here there are many differing pieces of advice on what needs to be installed, tweaked or adjusted.

Alas, though... perhaps that's simply the small price to pay for living in and enjoying the world of free Linux!

---

### Post by linuxgrrl on 2005-09-27
[QUOTE=GhostDawg]I have a friend who installed Warty version using cd disc and he told me that his Realtek AC'97 sound works with warty but when he upgrades to Hoary, he doesn't get sound once its upgraded.

Any ideas/suggestions?

Thnx.[/QUOTE]

I had a similar problem on a fresh install of hoary - the answer was found here - 
[http://www.ubuntuforums.org/showthread.php?t=25980&highlight=ac97+mute+alsamixer](http://www.ubuntuforums.org/showthread.php?t=25980&highlight=ac97+mute+alsamixer)

---

### Post by gabhla on 2005-09-28
[QUOTE=mlomker]That has to do with copyright laws.  Other distributions, such as Linspire and Xandros don't do that to you.  Then again, they pay royalties to the proper people for those codecs and obtain written permission from Real, Macromedia, and whoever to include their 'free' but non-gpl licensed code.[/QUOTE]
steven@ubuntu:~$ lsmod | grep snd
snd_intel8x0           29984  0
snd_ac97_codec         64608  1 snd_intel8x0
snd_usb_audio          60224  2
snd_pcm_oss            47652  0
snd_mixer_oss          16768  3 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
snd_usb_lib            11776  1 snd_usb_audio
snd_rawmidi            22944  1 snd_usb_lib
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  9 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
usbcore               107384  6 snd_usb_audio,snd_usb_lib,ehci_hcd,usbhid,uhci_hcd

Thanks...I appreciate any help.

---

### Post by mlomker on 2005-09-28
> Thanks...I appreciate any help.

It looks like the driver is loaded.  Have you looked [here]("http://www.ubuntuguide.org/#configuresoundproperly") or used one of the [troubleshooting guides]("http://linux.iuplog.com/default.asp?item=94639") yet?

---

### Post by gabhla on 2005-09-28
Yes...and no....I'll revisit both and let you know.  Thanks.

---

### Post by gabhla on 2005-09-28
Hello....Well, tried the first remedy...didn't work.  Honestly, a large part of the problem is my own ignorance.  Suspect I've got something wrong and will revisit this later, as I've run out of time this morning (have to work).  Haven't tackled the troubleshooting guides; however, I have read them and, to my mind, appear intimidating, (but so?  I can learn).

Otherwise, this is great.  I'm very impressed.

---

### Post by mlomker on 2005-09-28
> to my mind, appear intimidating, (but so?  I can learn).


If you plan to stick with linux then that's a good attitude to have.  It is always changing and there is a steep learning curve if you come from a Windows-only background.

---

### Post by gabhla on 2005-09-29
Indeed, very steep learning curve...but, that's one of the reasons I'm doing this.  I have Windows...got that down pat.  I enjoy linux..but I'm taking one simple thing at time, such as no sound.  I really don't need the sound, don't listen to all that much music...besides, I have a radio, tv etc (although I do enjoy listening to internet radio and that'll be my next great challange).  

Will take another pass and update, just don't have the time late in the week due to my work schedule.  

Thanks for your help.

---

### Post by Gezzer on 2005-09-29
have u tried reinstalling alsa
i found that sometimes that works ...

---

### Post by gabhla on 2005-09-30
Yup.  Tried that already.  Waiting for the weekend, then I'll have some time to redo some of the troubleshooting steps.  Stay tuned.  Thanks.

---

### Post by gabhla on 2005-10-01
Hello.  revisited "How to configure sound to work properly in GNOME"... issued the very first command...and this is what I get :

root@ubuntu:/home/steven # sudo killall esd
esd: no process killed
root@ubuntu:/home/steven # sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
root@ubuntu:/home/steven # sudo gedit /etc/esound/esd.conf

(gedit:9572): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Unknown option pcm.card0 {.
Unknown option type hw.
Unknown option card 0.
Unknown option }.
Unknown option pcm.!default {.
Unknown option type plug.
Unknown option slave.pcm "dmixer".
Unknown option }.
Unknown option pcm.dmixer {.
Unknown option type dmix.
Unknown option ipc_key 1025.
Unknown option slave {.
Unknown option pcm "hw:0,0".
Unknown option period_time 0.
Unknown option period_size 2048.
Unknown option buffer_size 32768.
Unknown option rate 48000.
Unknown option }.
Unknown option bindings {.
Unknown option 0 0.
Unknown option 1 1.
Unknown option }.
Unknown option }.
Unknown option pcm.card0 {.
Unknown option type hw.
Unknown option card 0.
Unknown option }.
Unknown option pcm.!default {.
Unknown option type plug.
Unknown option slave.pcm "dmixer".
Unknown option }.
Unknown option pcm.dmixer {.
Unknown option type dmix.
Unknown option ipc_key 1025.
Unknown option slave {.
Unknown option pcm "hw:0,0".
Unknown option period_time 0.
Unknown option period_size 2048.
Unknown option buffer_size 32768.
Unknown option rate 48000.
Unknown option }.
Unknown option bindings {.
Unknown option 0 0.
Unknown option 1 1.
Unknown option }.
Unknown option }.
- using device default
- using device default

In the terminal the cursor just stops.  Note the "Warning",  I've no idea what that indicates.

Absent no sound whatsoever, everything else is great.

---

### Post by gabhla on 2005-10-01
Hello - Been into the lack-of-sound problem, off and on, most of the day.  Tried everything, and have nothing to show for the effort.  Read, then reread, every post related to "No sound" or sound issues, did the trouble-shooting steps, tried the "How To's"...and, while I did no harm, I have no sound.:confused: :-({|= 
Then I remembered, prior to the hard drive installation of Ubunto I had downloaded and burned the 5.04 live CD iso and it had sound.  In fact, everything worked just great, which is why I decided to do a hard drive install.  So, I tried it...and ...voila...sound!
The difference from the hard-drive....on the live CD, under System>Preferences>Sound is there's sound options for "events" and "System"..but on the hard drive only for a game called "nibbles".
What can I do?  I'd hate just give up, but this just won't work without sound.

---

### Post by gabhla on 2005-10-02
Got it!  Sound on Hoary 5.04.  Took some doing, but - in spite of myself, I have sound. :D 
Here's what I did....installed 5.10 Breezy on a seperate partition of the hard drive, more out of desperation, (never booted into it after installation, instead when right back to Hoary), and - for the first time - SOUND.  I read somewhere on this forum someone else had a similar experience...so I figured, why not? 
Obviously, due the the number of sound issues there's a sound problem w/Hoary, which apparently has been addressed in 5.10.

---

### Post by roberto.pierpaoli on 2005-10-05
[QUOTE=canadianwriterman]Alas, though... perhaps that's simply the small price to pay for living in and enjoying the world of free Linux![/QUOTE]

Hi!
Well, two things:
1) I have really appreciated the lines quoted above, that really means to join the spirit of the community! I've initiated lot of friends to Linux (on their request, of course) and so many times I've heard something like "well, nice ... but windows is easier and I can get for free anyway" ... really disappointing.
Yours is a great aproach, go on like that!
2) I've  ecountered some problems with sound under Ubuntu, I don't know if the origins are the same of yours, but maybe the point is in the choice of the engine: in my case XMMS and amaroK only work fine "upon" the 'arts' sound server. Xine engine also gave some results, but nothing definitive.
So, what I suggest is that you download ALL the output plugin for XMMS and ALL the engines for amaroK (remember to include the EXTRA repository in Synaptic) and the "mad" library (libmad, dealing with mp3). Than try all of them one by one (for both the programs), maybe you will have to kill the processes few times, but MAYBE, in the end, you'll hear some lovely sounds.
One more thing: XMMS has some known problems with the NVIDIA graphic driver, if you have got an NVIDIA card and you have installed the driver, take a look at the Unofficial Ubuntu Guide (installing NVIDIA driver) to know the proper workaround.
I hope I've been a little bit useful ;)

---

### Post by mlomker on 2005-10-05
> engines for amaroK (remember to include the EXTRA repository in Synaptic) and the 

I've had my share of problems with plugins as well.  Right now I have it using gstreamer and it is working a lot better than xine did.

---

