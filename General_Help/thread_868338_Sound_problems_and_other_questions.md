---
title: "Sound problems and other questions"
date: 2008-07-23
forum: General Help
---

### Post by aomlives on 2008-07-23
Hi all, 

This is the current situation for a kind of old laptop (Sempron 2600+, 224 Mb RAM) I use from time to time. It has an older version of Xubuntu 7.10, which has been "forgotten" on one partition after I installed XP on the other because I needed some specific Windows programs. Today I thought I give Wubi a shot and installed the new Xubuntu 8.04. In any case I really need Xubuntu because XP Service Pack 2 is already having serious problems running Firefox along with OpenOffice.org and some other programs because of the low RAM. 

After Xubuntu 8.04 was installed correctly I saw I could - of course :) - access my old Xubuntu 7.10 installation again. However I first wanted to test the new one and came up with these problems.

Overall, the Xubuntu 8.04 is performing (even) less than XP, especially when connecting to the internet (using a Dlink external wifi adapter). Downloading via apt-get seems to almost lock up the computer to the point where nothing else can be done during downloading. Even surfing in Firefox or Epiphany is laggy. So I thought I'd install Fluxbox to make things better but this didn't seem to help one little bit.  :(. 

The worst part is when I switched to "old" Xubuntu I noticed no such problems, on the contrary this Xubuntu worked - as I'd hoped - way better and faster than XP. I wonder why this Wubi Xubuntu is so slow/laggy, could this possibly have anything to do with Wubi itself, or can someone think of other reasons?

Anyway I decided to use the Xubuntu Gutsy then but noticed I had no sound. This was the case in the Wubi install too. I read a lot on the forums about Xubuntu sound problems and the issue with many people was a muted alsamixer. However this is not the case here, I set it all on max (PCM, master,...) and 

```
aplay -l
```gives me

```
aomlives@aomlives-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [SiS SI7013 Modem], device 0: Intel ICH - Modem [SiS SI7013 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```so I think my sound card is installed correctly. The problem in both Xubuntus is I don't get anything from my speakers, although al mediaplayers are playing the things I ask them to: whether DVD, mp3 etc... just no sound. I really don't what to do anymore... :confused:

One last question concerning the Xubuntu Gutsy. It seems my screen resolution is slightly wrong detected because on some postions of my screen, across the whole length all tokens are somehow disfigured vertically. The explanation may be difficult :) but I think I just need to refresh/reset my resolution somewhere. The problem is when I go to Settings > Display Preferences it only has three options which don't apply for me. Anyone know where I can find/set these settings plz?

Thanx a lot in advance for any help, I would be very grateful!

---

### Post by caljohnsmith on 2008-07-23
Just to get another clue to your sound problems, how about trying to play a sound directly to your sound card and see if you can hear anything:
```
aplay --device=hw:0,0 /usr/share/sounds/login.wav 
```
I'm not sure if Xubuntu comes with that login.wav file as I don't use Xubuntu, but you can substitute any other .wav file for that one if you need to.

---

### Post by aomlives on 2008-07-24
I get 

```
Playing WAVE '/home/aomlives/Desktop/test.wav' : Unsigned 8 bit, Rate 22050 Hz, Mono
aplay: set_params:900: Sample format non available
```and still no sound...

What do I do now?

Thanks for helping.

---

### Post by caljohnsmith on 2008-07-24
> **aomlives said:**
> Playing WAVE '/home/aomlives/Desktop/test.wav' : Unsigned 8 bit, Rate 22050 Hz, Mono
aplay: set_params:900: Sample format non available
That means your sound card's DAC (digital to analog converter) does not support a 22.05 kHz sampling rate, so try a .wav file that is the standard 44.1 kHz (audio CD standard) or 48 kHz which is used by many sound cards. 

In other words, you can go into the /usr/share/sounds directory and find out which .wav files are 44.1 kHz:
```
cd /usr/share/sounds
file *.wav 
```
Pick one that's 44.1 kHz and try playing it with that aplay command I gave before. If aplay still complains about sample rate, go into the /usr/share/sounds/alsa directory, pick a .wav file that is 48 kHz sampling rate, and try playing that. Let me know how it goes.

---

### Post by aomlives on 2008-07-24
It seems to be playing (there are no 44,1 kHz standard wave files in Xubuntu apparently, so I had to find another one)

```
Playing WAVE '/home/aomlives/pidgin/test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

``` but it's the same as with the normal media players, it looks like it's working, only I can't hear a thing. I also triple checked alsamixer and everything is (almost) on maximum. 

Btw it's probably not relevant anymore but I also tried a 48 kHz file and it gave me this:
```

aomlives@aomlives-laptop:/$ aplay --device=hw:0,0 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:905: Channels count non available
```Any other things I can do? 

Thx for your help.

---

### Post by caljohnsmith on 2008-07-24
Just to clarify, is sound still working when you use Windows? 

I'm not sure about your problem, your best bet will be to experiment as much as possible to get more clues. For instance, instead of using ALSA, maybe try OSS under your system sound settings. Have you tried any Live CDs? That could give some valuable clues--boot up any Live CDs you have and try playing sounds. It would be good if you can use a Live CD other than Xubuntu to help narrow down whether Xubuntu is the problem.

---

### Post by aomlives on 2008-07-24
Posting from Windows and sound is still working here. I will now start testing some LiveCDs like you suggest. 

By any chance do you know how to change ALSA to OSS in Xubuntu because I didn't see any such options in the control panel.

I'll be back when I know more, thanks for staying with me :D

---

### Post by caljohnsmith on 2008-07-24
I had a few other ideas to help us get some more clues about your problems--please post the output of the following commands:
```

lsmod | grep snd
cat /proc/asound/modules

```

---

### Post by aomlives on 2008-07-24
```
aomlives@aomlives-laptop:~$ lsmod | grep snd
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                3200  1aomlives@aomlives-laptop:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_intel8x0m
 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm

```and
```
aomlives@aomlives-laptop:~$ cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_intel8x0m

```Does this help anything?

---

### Post by Taxman415a on 2008-07-24
Just a note. I didn't know the answers to any of your questions, but to get the best help you'll probably want to split your question into one per post. Otherwise it gets hard to help and discourages responses.

---

### Post by caljohnsmith on 2008-07-24
Well, it appears at first glance that Xubuntu is using the snd_intel8x0 driver for your SiS sound card, which is what it should be using. :) Did you try the Live CD for Xubuntu? And do you have any other Live CDs you can try? Let me know the results if you can use sound or not with those.

Also, I think we need to dive in a little deeper to get more clues, so please download the following shell script:
```
http://hg.alsa-project.org/alsa/raw-file/tip/alsa-info.sh
```
Then you'll need to run the program as root:
```
[navigate to the folder with alsa-info.sh]
chmod +x alsa-info.sh
sudo ./alsa-info.sh

```
The program will automatically pastebin the results, so just provide the link. Or if you prefer you can always copy and paste the results manually. :)

---

### Post by aomlives on 2008-07-24
> *Just a note. I didn't know the answers to any of your questions, but to get the best help you'll probably want to split your question into one per post. Otherwise it gets hard to help and discourages responses.*Yeah sorry about that, it's my first thread here and I'm still a little uncomfortable with the amount of information I should provide...

I'll certainly change this in the future though, thanks for your feedback.

---

### Post by aomlives on 2008-07-24
Here's the link:

[http://pastebin.ca/1082067](http://pastebin.ca/1082067)

Looks like it might help me, although I don't know how :D

I will now test my sound on a LiveCD like you asked.

grtz

---

### Post by aomlives on 2008-07-24
I don't know whether this simplifies things or not, but I just tested a Kubuntu 8.04 LiveCD and sound doesn't work there either. My sound card was detected though, as in the Xubuntu versions, and I set volume at max via KMixer. However nothing through my speakers. :(

I hope this information helps. 

grtz

---

### Post by caljohnsmith on 2008-07-24
Try unloading the snd_intel8x0m module, because if I remember correctly, you shouldn't need that and the snd_intel8x0 at the same time:
```
sudo modprobe -r snd_intel8x0m
```
That might fix things, but if it doesn't, I suspect your real problem is with this particular arcane parameter you need to specify for that module relating to your specific sound card:
```
sudo nano /etc/modprobe.d/alsa-base
```
Note you can use any editor you like if you don't like nano, but just make sure you open that alsa-base file as root. Then add a line near the bottom with:
```
options snd-intel8x0 ac97_quirk=3
```
To see whether that works, you can reboot, or I believe the following will be enough to load the changes:
```
sudo modprobe -r snd_intel8x0
sudo modprobe snd_intel8x0
sudo /etc/init.d/alsa-utils restart
```
And if that doesn't work, you can try 1, 2 or 4 instead of 3 for that ac97_quirk variable, but 3 should work.

Let me know how it goes. :)

---

### Post by aomlives on 2008-07-24
I'm trying the other things now, but when I execute the first line of your code I get this error:

> FATAL: Module snd_intel8x0m is in use.


How can I circumvent this?

I'll report back in a minute with the other results :)

---

### Post by aomlives on 2008-07-24
I've done all you said but I stil get the same error as above every time I try to unload the snd_intel8x0 and snd_intel8x0m modules using 
```
sudo modprobe -r
```So far still no sound with the part of the code that I could execute, but I guess I need everything for it to work. :)

How do I unload these modules while they're in use?

grtz and thx

---

### Post by caljohnsmith on 2008-07-24
My mistake, I shouldn't have assumed ALSA would let us unload the module. You definitely need to unload that snd_intel8x0m module though, so do the following instead:
```
sudo nano /etc/modprobe.d/blacklist
```
and then add the following line:
```
blacklist snd_intel8x0m
```
After that, reboot. Then do:
```
lsmod | grep snd_intel8x0m
```
And it should not return anything, meaning that module is no longer loaded.

If that doesn't fix the sound, then definitely try the alsa-base file modification I gave earlier, and once again, reboot.

---

### Post by aomlives on 2008-07-24
When I added snd_intel8x0m to the blacklist and rebooted the module's still loaded because ```
lsmod | grep snd_intel8x0m
``` returned stuff.

Then I checked /etc/modprobe.d/blacklist again and I saw that snd_intel8x0m was already blacklisted, so I simply re-blacklisted it before my reboot...

 I don't know if I'm doing anything wrong here. Thx for helping me.

---

### Post by caljohnsmith on 2008-07-24
Hmmmmm, if blacklisting the module does not prevent it from being loaded, I'm wondering if you have problems more significant than I originally thought. You could do the following "brute force" method to prevent that snd_intel8x0m module from loading: 
```
cd /lib/modules/`uname -r`/ubuntu/sound/alsa-driver/pci
sudo mv snd_intel8x0m.ko snd_intel8x0m_backup
```
Again, reboot, do "lsmod | grep intel8x0m", and if you get anything, be sure to post the results back here.

---

### Post by aomlives on 2008-07-24
The brute force method worked and I was able to unload snd_intel8x0m.

Then I continued with your instructions from a few posts back. I edited the alsa-base file with root privileges and added the line you said. After that I did a reboot as you suggested. I couldn't use your quick method because when I tried to unload snd_intel8x0 I had another "in use" error. 

I did this with ac97_quirk=3 and the other values you said but none of them had any result so far :( 

I hope this is actually a possibility and that we didn't run out of options completely. Thx for trying anyway. I'm open to other suggestions/methods of course, I really appreciate what you're doing.

---

### Post by caljohnsmith on 2008-07-24
> **aomlives said:**
> 
I hope this is actually a possibility and that we didn't run out of options completely. Thx for trying anyway. I'm open to other suggestions/methods of course, I really appreciate what you're doing.
Glad to help when I have the time to do it. :) I'll give it some more thought and let you know if I come up with more ideas, but in the meantime, I would recommend upgrading your kernel as that might be the culprit. Unfortunately I can't access that [http://www.pastebin.ca/1082067](http://www.pastebin.ca/1082067) page you posted right now for some reason as it seems their server is having problems, but if I remember correctly, you were using an older kernel. Try installing a newer one:
```
sudo apt-get install linux-headers-2.6.24-19-generic linux-image-2.6.24.19-generic linux-restricted-modules-2.6.24-19-generic linux-ubuntu-modules-2.6.24-19-generic
```
I would set the alsa-base file back to using "options snd-intel8x0 ac97_quirk=3", and again, if that doesn't work you can try the other values. When you reboot, make sure you choose the newer kernel in your Grub screen. Also, make sure the snd_intel8x0m module is not being loaded (lsmod | grep snd_intel8x0m), otherwise you'll need to repeat the "brute force" method to remove it since the newer kernel will have a different directory for that module. Let me know how it goes. :)

---

### Post by Taxman415a on 2008-07-25
> **aomlives said:**
> Yeah sorry about that, it's my first thread here and I'm still a little uncomfortable with the amount of information I should provide...

I'll certainly change this in the future though, thanks for your feedback.

No worries, it was basically just a suggestion so you get better help. Feel free to open other threads when you have time to tackle those. :)

Also here's a good link with more ideas for how to get good help:
[http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

---

### Post by aomlives on 2008-07-27
It seems I can't do a kernel upgrade. When I execute your code it says:

```
E: Kon pakket linux-headers-2.6.24-19-generic niet vinden

``` (that's could not find ~ in English :p)

When I try to install headers manually, I get these options:

```
aomlives@aomlives-laptop:~$ sudo apt-get install linux-headers
linux-headers                    linux-headers-2.6.22-15-rt
linux-headers-2.6                linux-headers-2.6.22-15-seraomlives@aomlives-laptop:~$ sudo apt-get install linux-headers
linux-headers                    linux-headers-2.6.22-15-rt
linux-headers-2.6                linux-headers-2.6.22-15-server
linux-headers-2.6.22-14          linux-headers-2.6.22-15-ume
linux-headers-2.6.22-14-386      linux-headers-2.6.22-15-virtual
linux-headers-2.6.22-14-generic  linux-headers-2.6.22-15-xen
linux-headers-2.6.22-14-rt       linux-headers-386
linux-headers-2.6.22-14-server   linux-headers-generic
linux-headers-2.6.22-14-ume      linux-headers-rt
linux-headers-2.6.22-14-virtual  linux-headers-server
linux-headers-2.6.22-14-xen      linux-headers-ume
linux-headers-2.6.22-15          linux-headers-virtual
linux-headers-2.6.22-15-386      linux-headers-xen
linux-headers-2.6.22-15-generic  ver
linux-headers-2.6.22-14          linux-headers-2.6.22-15-ume
linux-headers-2.6.22-14-386      linux-headers-2.6.22-15-virtual
linux-headers-2.6.22-14-generic  linux-headers-2.6.22-15-xen
linux-headers-2.6.22-14-rt       linux-headers-386
linux-headers-2.6.22-14-server   linux-headers-generic
linux-headers-2.6.22-14-ume      linux-headers-rt
linux-headers-2.6.22-14-virtual  linux-headers-server
linux-headers-2.6.22-14-xen      linux-headers-ume
linux-headers-2.6.22-15          linux-headers-virtual
linux-headers-2.6.22-15-386      linux-headers-xen
linux-headers-2.6.22-15-generic  
```What can I do?

My kernel release atm is still 

```
aomlives@aomlives-laptop:~$ uname -r
2.6.22-14-generic
```In case you would need it, I've copied the pastebin info [here]("http://aomlives.googlepages.com/pastebin").

sry for the delay and thx

---

### Post by caljohnsmith on 2008-07-27
My gosh, there is no end to your troubles with Xubuntu, is there? :) Be sure all your repositories are enabled, and then you'll have to update your packages list; I'm not sure how to do that exactly in Xubuntu, but if you can get into Synaptic Package Manager (do they have that in Xubuntu?), go under Settings > Repositories, and enable everything. Then hit the "Reload" button in Synaptic. You should be able to find those newer kernels then and install them. Make sure you get all four packages I mentioned before.

---

### Post by aomlives on 2008-07-28
I've done an upgrade to Xubuntu 8.04.1 and somehow I managed to finally upgrade my kernel too to version 2.6.24-19-generic.

Then I repeated all of the above instructions you gave me, but it still doesn't seem to help, I'm sorry :(

I also ran that script again and posted the output [here]("http://aomlives.googlepages.com/pastebin2").

---

