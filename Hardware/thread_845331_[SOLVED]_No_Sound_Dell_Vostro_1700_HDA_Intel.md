---
title: "[SOLVED] No Sound Dell Vostro 1700 HDA Intel"
date: 2008-06-30
forum: Hardware
---

### Post by chip616 on 2008-06-30
Well, I'm stumped.  I've been through the forum many times and seen some reports of sound problems with this system, and others saying it worked out of the box.  My Vostro 1700 with Intel HDA sound card does not work -- no sound.  It works with Fedora 8.  KInfoCenter report on sound card detection attached.

Card seems to be detected.  This is a fresh install of Kubuntu 8.04 -- not an upgrade.  Any of the posts with regard to kernel issues are now out of date, as I am running 2.6.24-19-generic.

I checked KMix under Fedora 8 on this machine, then booted into Kubuntu 8.04 and checked KMix again, making settings in both identical.  No sound.

Tried alsamixer.  It works fine, but no sound.

Tried alsaconf and got 'command not found' and same with alsaconfig.

Don't know what to do anymore.  Any help appreciated.

Thanks.

Frank.

PS:  Just added the KInfoCenter report as shown by Fedora 8 on this same machine (or tried to add it).  Most is the same, but Fedora is using IRQ 21.

---

### Post by LuisGMarine on 2008-06-30
Before I can help you I'm going to need some more information about your current hardware.

Open up a Terminal window by going to **Applications > Accessories > Terminal**

once the terminal window is up, type this command into the prompt and hit <enter> aftwerwards:

```
sudo lshw -C multimedia
```

paste the output of it.  For me I was a lucky one that my sound card worked right out of the bux on Hardy 8.04.  However back in 7.10 I had to do some serious hacking of my system to get them to work properly.

Hopefully you have the same card I have and for 8.04 it is an easy fix.  Just changing a value in a file.

-xkill

---

### Post by chip616 on 2008-06-30
Here it is.  Thanks for the offer of help.

Frank.

```
frank@vostro:~$ sudo lshw -C multimedia
[sudo] password for root:
  *-multimedia
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
frank@vostro:~$

```

---

### Post by moore.bryan on 2008-06-30
perhaps the correct module isn't being loaded in the kernel?
what does ```
lsmod
``` give you?

---

### Post by chip616 on 2008-06-30
Bryan:

```
frank@vostro:~$ lsmod
Module                  Size  Used by
af_packet              23812  2
rfcomm                 41744  2
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0
ipv6                  267780  12
acpi_cpufreq           10796  2
cpufreq_ondemand        9740  1
cpufreq_userspace       5284  0
cpufreq_conservative     8712  0
cpufreq_stats           7104  0
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0
sbs                    15112  0
sbshc                   7680  1 sbs
dock                   11280  0
container               5632  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
mmc_block              14980  0
snd_hda_intel         344728  2
uvcvideo               58116  0
joydev                 13120  0
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
iwl3945                89844  0
sdhci                  19076  0
compat_ioctl32          2304  1 uvcvideo
iwlwifi_mac80211      219108  1 iwl3945
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
mmc_core               51460  2 mmc_block,sdhci
nvidia               7825536  26
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
sr_mod                 17956  0
cdrom                  37408  1 sr_mod
evdev                  13056  9
cfg80211               15112  1 iwlwifi_mac80211
i2c_core               24832  1 nvidia
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0
wmi_acer                9644  0
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq

```

---

### Post by moore.bryan on 2008-06-30
> **chip616 said:**
> 
```

snd_hda_intel         344728  2

```
i don't yet know if this has anything to do with your issue, but my snd_hda_intel is used by "1," not "2." let me look into it a bit...

---

### Post by moore.bryan on 2008-06-30
how about try ```
sudo modprobe snd_hda_intel
``` and post if there are any messages.

---

### Post by chip616 on 2008-06-30
Bryan:

Nothing shows.

```
frank@vostro:~$ sudo modprobe snd_hda_intel
[sudo] password for root:
frank@vostro:~$

```

Thanks for the help.

Frank.

---

### Post by moore.bryan on 2008-06-30
okay, let me get my head around this:
[LIST]
[*]lsmod shows snd_hda_intel IS loaded,
[*]alsamixergui shows everything is unmuted, and
[*]you still can't get any sound?[/list]

---

### Post by chip616 on 2008-06-30
Bryan:


>lsmod shows snd_hda_intel IS loaded,<

Near as I can tell from the response you made earlier.

>alsamixergui shows everything is unmuted,<

I think so.  Attached is a screenshot of alsamixer in a konsole.  The line in and analog sliders don't appear to move, unless I am not understanding how to make them move.  I can select either digital or analog input, but neither makes any difference.

>you still can't get any sound<

Not a peep.

Like I say, I really don't get it.

Frank.

---

### Post by moore.bryan on 2008-06-30
you're right, this IS bizarre. i had a hard time getting my sound to work with snd_hda_intel as well, but i can't seem to remember EXACTLY what i did... let me look around to see if i wrote-down my fix.

---

### Post by moore.bryan on 2008-06-30
okay, "last ditch" effort... what does ```
aplay -l
``` give you?

---

### Post by chip616 on 2008-06-30
Brian:

OK, appears to give what it should give.  :)

```
frank@vostro:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
frank@vostro:~$

```

Now what?

Don't I remember Pulse Audio being the default with 8.04?  Will this make a difference?

Frank.

---

### Post by moore.bryan on 2008-06-30
i've heard more problems with pulseaudio than its worth. in what program are you trying to get sound? just to foreshadow: the steps i had to take to get my sound working required compiling alsa from source.

---

### Post by chip616 on 2008-06-30
Brian:

Amarok does not work.  I get no sound on system startup either.

> the steps i had to take to get my sound working required compiling alsa from source.

It shouldn't require that.  This machine works fine with Fedora 8.  The Intel chipset it uses is no longer cutting edge, and other people with a machine like mine say 8.04 is working fine, in some cases right out of the box.

Something more obvious must be missing here.

However, with that said, I won't reject compiling from source if someone can guide me through it.  Just seems like swatting a fly with an atom bomb, however.

Frank.

---

### Post by moore.bryan on 2008-06-30
i completely agree the nuclear option on the fly, but in the past for me and others it seemed to be the only thing that actually got sound working. it was probably some very small, rather insignificant setting which could have easily been changed if it could have been found which was just "fixed" through the compiling. let's work through a couple of other things before we go there, though.

launch kcontrol and head down to "sound system;" does everything look to be in-place?

---

### Post by chip616 on 2008-06-30
OK, with regard to Kcontrol, here are screeshots.  Clicking the 'test sound' button yields no sound, but as I started kcontrol from a konsole, there was some output, as follows:

```
frank@vostro:~$ server status: running, will suspend in 38 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940

```

Frank.

---

### Post by moore.bryan on 2008-06-30
on the hardware tab, try selecting the "advanced linux sound architecture" choice instead of "autodetect."

---

### Post by chip616 on 2008-06-30
OK, tried that, again running kcontrol from a konsole.  No change to the sound system, but it did generate some output in the konsole when I clicked the 'apply' button in kcontrol to select the advanced sound system.  Output here below.

I'll try rebooting now as well and see if any difference is noted.

Frank.

```

frank@vostro:~$ okay
server status: suspended
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940
sound server terminated
unable to connect to sound server
unable to connect to sound server
server status: running, will suspend in 59 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940
server status: running, will suspend in 53 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940
server status: running, will suspend in 37 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940
sound server terminated
unable to connect to sound server
unable to connect to sound server
server status: running, will suspend in 59 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940
clear
frank@vostro:~$ server status: running, will suspend in 39 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940
sound server terminated
unable to connect to sound server
unable to connect to sound server
server status: running, will suspend in 59 s
real-time status: not real-time
server buffer time: 53.288 ms
buffer size multiplier: 1
minimum stream buffer time: 53.288 ms
auto suspend time: 60 s
audio method: alsa
sampling rate: 44100
channels: 2
sample size: 16 bits
duplex: half
device: default
fragments: 10
fragment size: 940

```

---

### Post by moore.bryan on 2008-06-30
hmm... interesting output. how'd the reboot go?

---

### Post by chip616 on 2008-06-30
No change after the reboot.

Frank.

---

### Post by moore.bryan on 2008-06-30
okay. try firing-up amarok, going to "settings" and "configure amarok." select "engine" on the left sidebar and let me know what "sound system" is selected.

---

### Post by chip616 on 2008-06-30
Brian:

Engine selected is Xine.  Screenshot attached.

The dropdown list for Output Plugin has autodetect selected, but can be switched to ALSA, Pulse Audio, oss or file.  However, selecting anything other than autodetect or also yields the complaint that "Xine was unable to initialize any audio drivers".  There is no selection for any engine other than Xine.

Frank.

---

### Post by moore.bryan on 2008-06-30
that would indicate none of the audio drivers were properly installed, but unless you did something bizarre, that doesn't make sense. why don't you reinstall your arts, alsa-base, alsa-firmware, and alsa-firmware-loaders in synaptic?

---

### Post by chip616 on 2008-06-30
I can do that, but Amarok/xine does NOT complain if alsa is selected.  It only complains if I try to select pulseaudio or oss.

Frank.

---

### Post by LuisGMarine on 2008-06-30
Awesome Frank, thanks for the quick reply.

Ok , lets get started.  First we are going to modify your */etc/modprobe.d/alsa-base*.  Here we are going to try a tweak, that I found works pretty well with toshiba laptops.  The good news everyone that did this tweak that I'm going to show you for a dell showed almost 90% success.  It's quite easy, your are going to laugh if this fixes it.

To begin, we are going to make a backup copy of your current */etc/modprobe.d/alsa-base*.  So go ahead and fire up a terminal and type in the following command followed by <enter> and of course type in your root password when it prompts you to:

```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak
```

Next, open it up to edit the file with your favorite text editor, for this example I'm going to use the text word editor , Gedit.

```
sudo gedit /etc/modprobe.d/alsa-base
```

Once the file is open look for a line that might look *similar* to this:

```
options snd-hda-intel model=toshiba
```

Now all you need to do is make that line look like this, keep in mind if you don't have that line, just add the line below to the bottom of the file:
```

options snd-hda-intel model=dell
```

As you can see all I did was change the value of "model" from *toshiba* to *dell*

Save the file and quit, and then restart your PC.

[SIZE="2"]*Note:  You can restart the sound module, but I don't know how to do it off the top of my head, so lets just play it safe and restart ;)*[/SIZE]

Let me know how it goes.

-xill

---

### Post by moore.bryan on 2008-06-30
sorry, i misunderstood. when you select alsa, can you test a media file?

---

### Post by LuisGMarine on 2008-06-30
Did you try what I said?

Let me know if it works, if it doesn't I'll give you the guide to get it to work.  It's a mulitiple post guide, I'll probably compile it into one so it will be easier for you to follow

---

### Post by chip616 on 2008-06-30
xkill:

No, it didn't work.  Still no sound.  I'm beginning to despair, and may blow away the whole install and try again....

However, if you have additional suggestions, then please make them.  :)



Brian:

> sorry, i misunderstood. when you select alsa, can you test a media file?

Now it is I that does not understand.  What do you mean test a media file?  The sound test button does not work in kcontrol no matter what I select.  Is that what you mean?

Thanks, guys, for your kind patience with this.

Frank.

---

### Post by LuisGMarine on 2008-06-30
Ok, it was worth a try.

I will sort through the post tomorrow and try to come up with a straight foward guide for you.  I would now but it's getting late and I have to PT tomorrow morning at 5:30AM.  

Don't worry I promise I will try my hardest to get this problem fixed for you.  Just be patient, that's all I ask for :)

As for the re-install.  DON'T DO IT.  Re-installing isn't going to fix your problem.  Like I said with Linux you have to be patient, and just fight it through.  There is an answer for everything, trust me.  Re-installing is not the way to do it, just hang in there!

-LuisGMarine

---

### Post by chip616 on 2008-07-01
Luis:

> There is an answer for everything, trust me. Re-installing is not the way to do it, just hang in there!

I prefer to do it by finding and fixing the problem, as you don't really learn anything otherwise.  However, as Brian pointed out, there may be something weird going on here.  I had one of my Kubuntu machines hang during an update, but I don't remember which one it was.  Interrupting an update in progress could leave any amount of trash lying around, and a guy could spend the rest of his days trying to fix everything that is broken.

As to being patient, I have no problem with that, as long as we are working at something analytically rather than 'just trying stuff' to see if it works.

Again, my thanks to both of you.

Frank.

---

### Post by moore.bryan on 2008-07-01
@luis: sometimes a reinstall fixes things in a much more timely way than fighting through piles of code to find one little entry which might be off, so SOMETIMES it is a good/the best choice.

@frank: why don't you try reinstalling arts and alsa-base... perhaps that will yield a clue.

---

### Post by LuisGMarine on 2008-07-01
Frank,

Here is what I was able to dig up from doing some research.  This if for a 1720.

I'm going to give you the link, and you can view for yourself.

[http://ubuntuforums.org/showthread.php?t=702003]("http://ubuntuforums.org/showthread.php?t=702003")

Check post #3

If that doesn't work I'm sorry but that is as far as I can help.  Sorry but leave for Iraq on Friday, and need to get my final preparations before my deployment.  

Wish you the best of luck.

:guitar:

---

### Post by chip616 on 2008-07-01
Luis:

Thanks for all your kind help, and I wish you well while you are away.  However, the link you gave me is for 7.10, not 8.04.  I enabled the backports repository for Hardy, but alsa 1.0.15 is not available.  I may look for another way to downgrade alsa if that is what it takes.  My Fedora 8 install on this machine uses alsa 1.0.15, and that works.  I may just try copying the binary over and see if anything breaks.


Brian:

I updated arts and alsa-base.  No change.  A full reinstall is looking better all the time.  May not resolve things, but surely I cannot be the only one in the world with this machine that does not have sound.  SOMETHING must be different about this install.

Frank.

---

### Post by chip616 on 2008-07-01
OK, was gonna blow this one away and reinstall from scratch.  However, in loading the liveCD, I see that there is no sound there either.  No point in reinstalling.

Any help still appreciated.  In the meantime, I'll start scouring the web.


Frank.

---

### Post by chip616 on 2008-07-01
Bryan and Luis:

Boy, is my face ever red now.

Note the screenshot in post # 10.  Anyone see anything there out of place?  It kills me to have to point out that the "Front" is muted.  Of all the dumb, newbie, stupid, (add expletives here) things to do....

I found it by searching the web, and a post in the Fedora forum showed me how to use the 'm' key in alsamixer to mute/unmute a column.  In checking that, I found that the front one was labelled 'mm'.

Guys, I am SO sorry to have put you through all of this.

Now I'm going to have to change my account here to hide my embarassment.

Please forgive me.

George.  :)

---

### Post by moore.bryan on 2008-07-01
i'm just glad it was something so simple, frank/george. ;-)

---

### Post by chip616 on 2008-07-01
Bryan:

You are such a gentleman.  Thanks again so much.

Frank.

---

### Post by moore.bryan on 2008-07-01
you're too kind...

---

### Post by LuisGMarine on 2008-07-01
I feel even dummer.  I was under the impresion that we already had opened up alsamixer from the command prompt ...

Eh, at least you fixed it!  Congrats .... lol

Thanks, and enjoy!

---

### Post by chip616 on 2008-07-01
Luis:

> I was under the impresion that we already had opened up alsamixer from the command prompt ...

I had.  Just missed that it was muted.  Can't believe I did that....

Frank.

---

### Post by moore.bryan on 2008-07-02
hey frank... you might want to mark this thread as "solved" using the thread tools at the top of the thread.
:-)

---

### Post by chip616 on 2008-07-02
Bryan:

I tried to yesterday, but am not familiar enough with this forum yet, I guess.  Now, when you pointed me to the 'thread tools' I found out what to do.

Thanks again.

Frank.

---

### Post by moore.bryan on 2008-07-03
no worries...

happy ubuntu-ing.

---

