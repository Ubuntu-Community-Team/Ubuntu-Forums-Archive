---
title: "No sound"
date: 2005-11-19
forum: General Help
---

### Post by Optiker on 2005-11-19
A couple of weeks ago I posted to the General forum on the Kubuntu site forums regarding no sound on my computer at work. I never resolved the problem, and now that I've installed 5.10 on my home computer, and having the same problem, I went back to the previous posts, and tried some of what I saw there, but no luck. I accessed the universal repositories as instructed, and in this case, was able to install gstreamer0.8-mad, but still noting.

I am trying to play MP3s as the type I'll most often play, and remember reading that Kubuntu doesn't support MP3s because of copyright issues, but I thought that installing gstreamer0.8-mad would resolve that.

In Amarok and Kaffeine, the visualization and progress bar show that something is being played, but no sound. The obvious things have been checked and are OK - like my speakers are plugged in and turned on, and volume at the speaker and in the app is up. The opening sound when Kubuntu starts up plays and is audible, so that's working.

It behaves just like it might in Windows if the sound is muted or some setting is not set right.

Suggestions?

Thanks!
Optiker

---

### Post by garciadc on 2005-11-19
I don't know what posts you looked at, but I would check your ALSA settings to see what is (or isn't) muted as well as what sound device is enabled. Go to volume control.  If that doesn't help I would go to multimedia systems selector under system>preferences, and make sure alsa is set to default sink.

---

### Post by Optiker on 2005-11-19
How do I check ALSA settings?

Right-click on volume in tray, then from KMix menu select Show Mixer Window. Mute is not activated.

Three tabs...

Output tab...
Master ad Mono active, slider at 100%; others not active
IntelICH5 slider at bottom at 75%

Input tab...
Line, CD, Mike active; sliders at about 75%; all others not active; red button on for Line; same Intel ICH5 at bottom

switches tab...
Mic boost yellow button
video - off
mix - red button
all others off

surround jack mode - shared
Mic select - mic 1
Channel Mode - 2 ch
downmix - off
That's it...Does any of it make any sense? I don't know what else to look at. 

You mention "multimedia systems selector under system>preferences" but I don't know where to find that. If I click on the System button in the bottom tool bar, then Settings, I get ten icons, one of which is Sound & Multimedia. When I click it, I get for more, Audio CDs, Sound System, System Bell nd System Notifications. Of those, only Sound System seems relevant, and if I click it, I get 2 tabs, General and Hardware.

Enable sound system - checked
Networked Sound - not checked
Skip Prevention - checked wit slider a little over 50%
Auto Suspend - checked with 60 seconds selected

The Hardware tab has autodetect for audio device. Nothing else checked, Quality at default.

Does that make any sense? See anything? What else do I look at to check on setup?

thanks!
Optiker

---

### Post by mlomker on 2005-11-19
[QUOTE=Optiker]How do I check ALSA settings?
[/QUOTE]

Run **alsamixer** in a terminal.  [link here]("http://linux.iuplog.com/default.asp?item=94639")

---

### Post by pabach on 2005-11-19
I've had a problem adjusting the volume of any sound - it's permanently at maximum (using kubuntu 5.10), and sounds are fuzzy in some players (kaffeine) but not others (beep). with alsamixer the master volume is stuck at zero
Having now read through many forum posts and tried the IRC channel with no luck, it's time to ask for advice.
Thanks :) 

CARD: Intel 82801DB-ICH4

CHIP: C-Media Electronics CMI9739

snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 saa7134,snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

---

### Post by johndoe080 on 2005-11-19
I've installed the Kubuntu 5.10 Breezy Badger and I went on this forum because I had
the same problems with the sound card. My sound card is Intel ICH5 and it is integrated
on the motherboard (My motherboard is an Asus P4P800-X)

I tried to editing modprobe.conf, reinstalling alsa driver, ... but I get still no sound.

Today I read the manual of my motherboard and I discovered that the motherboard
has two audio output, one is on the rear side of the case and one is located on
the motherboard.

On my motherboard there are 9 pin (10-1) nearly the rear mic-linein-lineout
jack connector and they are called on the manual "10-1 pin FP_AUDIO".

This second line out is used if you have a case with a front panel audio connectors
but this motherboard doesn't support two line out at the same time, so If you would
like to use the front panel audio connectors no sound can be produced by the
rear line out.

If you would like to activate the rear jack line out of the motherboard you have to
connect with jumper caps the LINE OUT_R (pin n'7 in the example below) with
BLINE_OUT_R (pin n'3 in the example below) and the LINE OUT_L (pin n'9 in the example below) with
BLINE_OUT_L (pin n'4 in the example below) 

```

 _________
|1|2|3| |4|
|-|-|-|-|-|
|5|6|7|8|9|
-----------

1=AGND
2=+5VA
3=BLINE_OUT_R
4=BLINE_OUT_L
5=MIC2
6=MICPWR
7=Line out_R
8=NC
9=Line out_L


```

Now I can hear 5.1 dolby surround music with my multimedia sound system
and my new distribution Kubuntu 5.10.
I hope this post can help you.

---

### Post by Optiker on 2005-11-20
Ah...my computer has the onboard sound, but I added the Soundblaster Live 24-bit, and it's what's set up to run in Windows. How do I force Kubuntu to use it instead of the onboard sound? Apparently it wsn't detected.

I think that the blog that mlomker linked probably answers that, unless somebody has a simpler solution. I'm not very experienced.

Thanks!
Optiker

---

### Post by t2kburl on 2005-11-20
If you have onboard sound and a sound card you should edit your BIOS to disable the onboard sound

then try the modprobe for your sound card

---

### Post by Optiker on 2005-11-20
t2kburl...I have disabled the onboard sound in BIOS - evidence that the SB is being used in WinXP.

As a Linux novice, I have no idea what modprobe is (I assume module probe), where to find it, or how to use it. Any more detailed instructions?

Thanks!
Optiker

---

### Post by Optiker on 2005-11-20
Per suggestion in the linked blog, I ran lspci and got the following line (in addition to a ton of other stuff that appears to relate to the onboard sound...
-------------------------
0000:02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
-------------------------
So, it is recognizing my SB card, just not selecting it.

NOTE...some posts as well as the blog refer to the selection path...

System > Administration > Device Manager  > Sound Controller

Either I'm very thick, or that's not accurate. I don't find that string anywhere in exactly that form.

One path I've followed is the System button in the default tool bar at the bottom-left, then Settings (no Administration) in sight at that point), then System Administration gets to a grooup of icons including System Services. That gives me a window that when I enter my password, lists all the services and their status. alsa is shown, but shown as not running. Is that relevant?

Another path is from Settings, select Sound and Multimedia, giving four icons: Audio CDs, Sound System, System Bell and System Notifications. Selecting Sound Systems gives a window with two tabs, General and Hardware. I think I summarized that content in a previous post, but it seems like maybe a relevant point is that in the Hardware tab, Autodetect is selected.

Yet another path (probably abbreviated as yap in app naming style!) was the volume control in the tray, to get KMix, select show mixer window, has a selection menu which I presume is the device, that has selected Intel ICH5, but the other option is CA0106 -is that my SB Live card? Is that _C_reative Labs _A_udigy...?Should I select it? Maybe I will just do it and see what happens!  :)

More help please...Thanks!
Optiker

---

### Post by Optiker on 2005-11-20
In KMix, tried to select CA0106, then shutdown and restarted. When I opened KMix, it had reverted to the ICH5 selection. In the System Services report, alsa is still shown as not running...I made no changes there since I don't really undrstand what that's all about. I do see that there is a selection to start a process at boot.

Bummer...had hoped I'd stumbled on the solution, but maybe it's close enough that somebody can tell me what to do to select my SB caard instead of the onboard at boot.

Thanks!
Optiker

---

### Post by Optiker on 2005-11-21
Since my lsat post on this isue, tried selecting ALSA from the dropdown list of sound options, and also running it from the services list. Neither made a difference, nor "stuck" and the whole reverted to the onboard sound, no ALSA when I rebooted.

Can anybody tell me what to do to automatically select my SB card as default instead of the onboard at boot?

Thanks!

Optiker

---

### Post by mlomker on 2005-11-21
Are the drivers loading for the on-board sound?  **lspci** should give you an idea of what kind of card it is.  **lsmod | less** will allow you to page through the loaded modules and look for likely suspects.  If it is a driver that is loading then it may be possible to use /etc/hotplug/blacklist to prevent it from loading.

---

### Post by Optiker on 2005-11-22
mlonker...first off, thanks very much for staying with me. This is getting very frustrating, and if it wasn't for your continued efforts, I'd probably have given up on Linux yet again - for the ...I've forgotten how many times I've started down this road and gave up for things like this  or for exactly this, ie, no sound.

Here's two lines from running lspci, selected because each references either the Intel (onboard) sound "card" or the Soundblaster.
------------------------
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC   '97 Audio Controller (rev 02)

0000:02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
------------------------
Given that, what next? I know nothing about this blacklist thing, but having opened it and browsed, I think I can do that, but need to know what I enter in the blacklist. The lspci listing for the Intel sound has nothing in it that looks like the syntax of any of those already there. Specific directions please?

Thanks!
Optiker

---

### Post by zukakog on 2005-11-22
I've got the same problems aparently.  I've got a SB Live! 24-bit card.  lspci gives the following:
```
0000:04:01.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

Here's my modprobe.  Scroll the box to see the bolded parts that I thought would be relevent.
```
Module                  Size  Used by
af_packet              21768  2
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
nfsd                  218560  9
exportfs                5760  1 nfsd
lockd                  63784  2 nfsd
sunrpc                137796  12 nfsd,lockd
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251200  8
tsdev                   7776  0
floppy                 59124  0
rtc                    12344  0
pcspkr                  3396  0
[B]snd_ca0106             30916  1
snd_ac97_codec         83932  1 snd_ca0106
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_ca0106,snd_pcm[/B]
tpm_nsc                 6656  0
tpm                     9888  1 tpm_nsc
pci_hotplug            27508  0
intel_agp              23164  1
agpgart                34792  1 intel_agp
nls_cp437               5664  1
ntfs                  108144  1
ext2                   66824  1
dm_mod                 57692  1
evdev                   9664  0
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  2 ext2,ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
usbhid                 35264  0
tg3                    96772  0
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               117884  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 19120  5
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_generic             1376  0
ata_piix               10052  8
libata                 53764  1 ata_piix
scsi_mod              135688  2 sd_mod,libata
piix                   10372  1
ide_core              138772  3 ide_cd,ide_generic,piix
unix                   26896  648
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

```
I've got to reimage a room of 30 computers today, and was hoping to have sound before then, so that I didn't have to reimage.  Oh poo!

---

### Post by mlomker on 2005-11-22
[QUOTE=zukakog]I've got the same problems aparently.  I've got a SB Live! 24-bit card.  lspci gives the following:
```
0000:04:01.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

Here's my modprobe.  Scroll the box to see the bolded parts that I thought would be relevent.
[/QUOTE]

Your list looks the same as mine, other than the driver name.  I don't think there's anything 'extra' in there.  

This post is [interesting]("http://www.ubuntuforums.org/showthread.php?t=92671") and [here.]("http://www.ubuntuforums.org/showthread.php?t=79383")  It sounds like you need to use ALSA and the default mixer settings don't work.

---

### Post by Optiker on 2005-11-23
mlomker...I checked the two posts you linked, and tried to follow. In the second one, markdrago says... 
------------
Click on System >> Preferences >> Multimedia Systems Selector.
Change the Default Sink to 'ALSA'
------------
I keep seeing directions like this, but when I try to do it, don't find anything that matches...for example, when I click either the System icon in the toolbar at the bottom or the System item in the start menu from the "K" icon in the lower-left corner, I don't see anything that says Preferences. I see Settings in the menu from the System icon, but from the System in the start menu, nothing close. If I go to Settings from the System icon in the toolbar, there is an icon for Sound & Multimedia - nothing that says Media Systems Selector. Under Sound & Multimedia, there is an icon for Sound System. Clicking it gives a window that is titled Configure - KDE Control Module, which has 2 tabs, one General and one Hardware. The hardware tab has a "Select the Audio Device", and drop-down menu containing a group of selections, none of which are familiar to me, but Advanced Linux Sound Architecture looks like it might be ALSA, so I selected it.

Is it possible that the reference by markdrago and others that give similar directions are referring to either a different version of KDE, or Gnome under Ubuntu? If not, where am I missing the boat? I'm running Kubuntu 5.10 with whatever version of KDE came with it.

I am trying to find an FTP client on the Linux system so I can upload a screen capture of the information shown in the Sound section of KInfoCenter so that you can see what my system is telling me - maybe that will help. I've added a couple of ftp packages, but they don't show up anyplace in the start menu, nor desktop icons. I suppose that they may be command line apps - one definitely is. They incllude ftp, lftp (command line), ncftp2, and wu-ftpd. Command line is out - I'm not that skilled. Any suggestions on where I might find the others, or an alternate to install?

Thanks!

Thanks!
Optiker

---

### Post by mlomker on 2005-11-23
[QUOTE=Optiker]Advanced Linux Sound Architecture looks like it might be ALSA, so I selected it.[/quote]

Yup, that's the one.

> Is it possible that the reference by markdrago and others that give similar directions are referring to either a different version of KDE, or Gnome under Ubuntu? 

It's undoubtedly for gnome.  Most people use gnome, so we often have to find an equivalent in those situations.  You might want to post on the [Kubuntu Forums ]("http://kubuntuforums.net/")as well...if you haven't already.

I'm not sure why you'd need an FTP program.  You can simply attach JPG files to posts on here using the Manage Attachments button.

---

### Post by Optiker on 2005-11-23
mlomker....thanks for the reply.

So, I've selected ALSA, but still no sound..

I am posting to the Kubuntu forums as well, but I thought this one is supposed to be Kubuntu as well, even though it's one on the Ubuntu forum group. This one is more active, and frankly, I haven't gotten a single reply to my "no sound" post over there. I've also posted to my local Linux users' group, but no replies yet from them yet either.

I didn't realize I could attach files here...most forums seem to require just a url to link to a file.

That said, I'll try to attach the jpeg of the KInfoCenter information on the sound system and see if there's anything there that rings a bell. OK...I've attached...I don't see any evidence of it in the preview, but we'll see if I've done it right. Filename is snapshot2.jpg.

Thanks!
Optiker

---

### Post by mlomker on 2005-11-23
[QUOTE=Optiker]I am posting to the Kubuntu forums as well, but I thought this one is supposed to be Kubuntu as well, even though it's one on the Ubuntu forum group. [/QUOTE]

It is, but I don't have any answers so thought I'd suggest the option.

---

### Post by Optiker on 2005-11-30
One more time...Since it has been almost a week and this has drifted down to page 3 without any new replies, I thought I'd give it one more try and see if another day on page 1 gets some help.

I am still at the same point as when I posted my last reply, which included the screen shot of the KInfoCenter output. With the exception that I have now posted to LinuxQuestions.org, my local Linux users' group, and GRC's grc.techtalk.linux - all without replies.

Any fresh ideas? If not, I will probably wipe it off and try reinstalling.

Thanks!
Optiker

---

### Post by zukakog on 2005-11-30
My sound is working now!

I had to select ALSA, but then I just had to turn up the 'Analog Front' volume.  For some reason, the sliders on my toolbar was set to 'Analog Center/LFE'.

---

### Post by linuxfanatic1024 on 2005-11-30
> The opening sound when Kubuntu starts up plays and is audible, so that's working.

If that's still true after all that messing around with ALSA, check this out:

[http://www.kubuntu.org/faq.php#mp3s](http://www.kubuntu.org/faq.php#mp3s)

I think this might fix your problem. Good luck.

---

### Post by Optiker on 2005-12-05
fanatic...some things have changed.

Embarassingly, I discovered that the onboard sound was not disabled. Can't understand how it changed since I disabled it last spring when I installed the SB, and the one app that motivated the SB that didn't work with the onboard, has worked since I put the SB in. Something changed...guess it doesn't matter because now I've disabled onboard sound for sure.

I was also mistakenly confusing my problems at home with my problems at work. At work, the startup sound plays, but no mp3s, and trying to fix that, I seemed to have broken Adept...workin on that. At home, no startup sounds.

However, that didn't affect the result.

I will try zukalog's suggestion - as I recall, mine is set to "center". I will also try k3b-mp3 as suggested in the link you provided.

Thanks!
Optiker

---

### Post by Optiker on 2005-12-08
Just for the record, so others might see it and it might help them as well. I went back to the old reliable GRC groups and posted to grc.techtalk.linux, and after a fairly long time of no activity, one person replied and stayed with it asking questions and me giving answers until he spotted something that led to the right answer. I'm reposting here for others that might find it useful.
------------------------------
Try looking at this web page:

[http://www.linuxquestions.org/questions/showthread.php?t=337513]("http://www.linuxquestions.org/questions/showthread.php?t=337513")

The relevant lines seem to be these, but there is more explanation there:

"well here I am again found the solution. For some reason it changed itself to digital from analog, here is how to change it back.

open terminal type alsamixer

a panel will open up it looks like there are about 2 little boxes with mm in them and 5 sliders but if you keep pushing the arrow key right till you find the little boxes with mm in it for analog and I also had to switch the oss one said sigtel I believe was almost all the way over put the focus on the little boxes and hit m that will trip the switch and turn it on. hit escape to close.

When you reboot you will loose it unless you save it

sudo alsactl store

is the save command i believe...good luck"
----------------------------------

I guess this thead can be closed now.

Thanks to all who posted to this thread and the previous one to try to help.

Optiker!

---

### Post by mlomker on 2005-12-09
:cool: 

If this happens on a clean install then hopefully someone has filed a bug report so that they make that the default setting for that sound card.

---

