---
title: "no sound ever is driving me nuts"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by blakamin on 2005-08-05
OK... I have no sound ever (and cant c&p the terminal) on my 3rd install
I have searched the forums for hours (about 16 today)


it shows up in lspci as a cs4281,
if i run alsamixer, I get a pretty picture of all the volumes
I have no "/etc/asound" files at all

what am i doing wrong???

I will ditch other OS's on this machine if I can get audio!!
I run another laptop (hp ze series) that runs knoppix with audio... ASC version.
but I want an everyday machine so I can get rid of xp

it is a dell l400 with 256ram, 40g HDD blah blah blah...

I'm not a total linux n00b (been off and on for 10 years), Ubuntu noob tho, I've just tried every ubuntu trick I can find and still cant find sound...

---

### Post by heimo on 2005-08-05
So, is correct sound module loaded?

---

### Post by blakamin on 2005-08-05
i wish i knew... brain is fading

how can I tell??? what would you like to know?
It says its it's the cirrus logic cs 4281 alsa in the volume preferences and in the system->prefs->multimedia

---

### Post by blakamin on 2005-08-05
Now you mention it

lsmod says

```
pcmcia_core            53568  3 orinoco_cs,pcmcia,yenta_socket
snd_cs4281             20576  1
snd_rawmidi            22944  1 snd_cs4281
snd_ac97_codec         64608  1 snd_cs4281
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9604  1 snd_pcm
gameport                4608  1 snd_cs4281
snd_opl3_lib           10112  1 snd_cs4281
snd_seq_device          8332  2 snd_rawmidi,snd_opl3_lib
snd_timer              23300  2 snd_pcm,snd_opl3_lib
snd_hwdep               9220  1 snd_opl3_lib
snd                    50276  12 snd_cs4281,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq_device,snd_timer,snd_hwdep
soundcore               9824  1 snd
```


so how can I change that in ubuntu?

---

### Post by heimo on 2005-08-05
Hmm.. ok, you probably have the correct module (wouldn't show up as a device otherwise). You can open some player and play music files? (but no sound) Is this the case?

There's somewhere in the upper menus multimedia selector or similar, which has "default sink" settings, Alsa, ESD, OSS... and a test button which gives a steady test tone. Try changing those and check that in the alsamixer you don't have any channels muted (toggle with m key). Also change other settings in alsa, and ... check the cables. Yes, you've done that - but sometimes it's just a combination of two or three minor problems which cause you to do hours and hours of work before you get all those things fixed at the same time.

Oh. To check which sound modules you have loaded - *lsmod | grep snd *

I won't be on these forums for next 24-36 hours. Others... please - continue debugging. ;) And you too, have a nice weekend, don't burn yourself on this problem, it's definitely something that can be solved and won't be so hard next time.

---

### Post by blakamin on 2005-08-05
[QUOTE=heimo]Hmm.. ok, you probably have the correct module (wouldn't show up as a device otherwise). You can open some player and play music files? (but no sound) Is this the case?[/quote]
yep
[QUOTE=heimo]
There's somewhere in the upper menus multimedia selector or similar, which has "default sink" settings, Alsa, ESD, OSS... and a test button which gives a steady test tone. Try changing those and check that in the alsamixer you don't have any channels muted (toggle with m key). [/quote]
I dont even get a tone evn tho it says "testing"
[QUOTE=heimo]
Oh. To check which sound modules you have loaded - *lsmod | grep snd *[/quote]
will try that and report
[QUOTE=heimo]
I won't be on these forums for next 24-36 hours. Others... please - continue debugging. ;) And you too, have a nice weekend, don't burn yourself on this problem, it's definitely something that can be solved and won't be so hard next time.[/QUOTE]

Thank you for your help.. and you're right... sleep would help, but i promised myself I wouldnt leave this laptop until I could kill XP :-P  ](*,)


you have a good weekend too!

---

### Post by s_p_a_r_k_y on 2005-08-05
the best way I have found to test sound is by killing any and all sound servers.
```
sudo pkill -9 esd
``` 
will go ahead and kill that pest. Then check alsamixer

Make sure you don't have any things with MM. that is muted. Unmute via selecting it and pressing m. I have my master turned up all the way, and PCM all the way (right now).

Once you have done that try playing a song with XMMS or something. In XMMS right click and go to options->preferences and make sure your output plugin is ALSA or OSS (whichever you are using). then try playing a song.

Cheers

---

### Post by blakamin on 2005-08-05
hmm... did that and nothing has changed... nothing is muted in any controls (that I can find, alsamixer, etc) I am well and truly confused!!!

---

### Post by varunus on 2005-08-05
Have you tried the configure sound properly section of the Ubuntu Guide?  ([http://www.ubuntuguide.org](http://www.ubuntuguide.org))

Also, can you post the full output of lspci and lsmod?

---

### Post by s_p_a_r_k_y on 2005-08-05
does ```
cat /dev/urandom > /dev/dsp 
``` give you a nice, lovely, homely sound? Or nothing?

Check the bios and turn off plug and play support...I know I had a problem once with that.

---

### Post by blakamin on 2005-08-05
After re-installing mozilla because I thought it wasnt working (just to find I couldn't connect to the forums on my other PC either).... :-# 

the bottom of ubuntuguide.org has nothing in the boxes... can read some text ...

lsmod and lspci
```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:00:10.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

```
```

Module                  Size  Used by
speedstep_lib           4228  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  2
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229504  9
3c59x                  37160  0
yenta_socket           19584  0
pcmcia_core            53568  2 pcmcia,yenta_socket
snd_cs4281             20576  2
snd_rawmidi            22944  1 snd_cs4281
snd_ac97_codec         64608  1 snd_cs4281
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_cs4281,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9604  1 snd_pcm
gameport                4608  1 snd_cs4281
snd_opl3_lib           10112  1 snd_cs4281
snd_seq_device          8332  2 snd_rawmidi,snd_opl3_lib
snd_timer              23300  2 snd_pcm,snd_opl3_lib
snd_hwdep               9220  1 snd_opl3_lib
snd                    50276  13 snd_cs4281,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq_device,snd_timer,snd_hwdep
soundcore               9824  1 snd
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
intel_agp              20636  1
agpgart                31784  1 intel_agp
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
nls_utf8                2176  1
ntfs                   97136  1
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
joydev                  9408  0
tsdev                   7488  0
evdev                   9088  1
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  902
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb
```

and s_p_a_r_k_y, It did nothing! :?

---

### Post by varunus on 2005-08-06
Sorry you're having so many problems with audio.  The cs series of cards sometimes get crazy on ALSA...

Can you post a screenshot of your alsamixer?  I've heard some CS cards need a certain thing muted to get it to work (maybe digital audio out, maybe digital audio in, something like that).

You may want to try breezy if you feel lucky; it has much better sound card support apparently.  Other than that, try google out...

---

### Post by blakamin on 2005-08-06
cheers, varunus

---

### Post by wvslkr on 2005-08-06
You might want to look at this [http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=cs4281](http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=cs4281).

Hope it helps :)

---

### Post by varunus on 2005-08-06
Try unmuting aux and the 4-speaker stereo ones and see if that works...Also try plugging your speakers into the lineout jack (if you have one) instead of the regular jack.  If you haven't been using headphones/speakers, try a pair of headphones and see if you get sound through those; i've seen a laptop that did that before.

---

### Post by blakamin on 2005-08-06
Cheers, guys,. tried all that.... i'm thinking of living in silence...lol

---

### Post by bearbigears on 2005-08-07
for what it's worth, i seemed to have the same problem with my 8200 inspiron, i got very frustrated and just reinstalled ubuntu and followed the unofficial ubuntu guide, i had done this previously but not to the letter. i found the fifth time i had reinstalled that i had missed details in going thru it. lo and behold i had audio and it has been running smoothly ever since. i may be a shot in the dark. well that is my two cents. 
good luck

 :grin:

---

### Post by blakamin on 2005-08-07
might try again then... cheers

---

### Post by blakamin on 2005-08-08
Well, I'm installing again now... 
a mate gave me some fedora core 4 discs... what a horrible distro... 4 hours to install, killed my windoze partition, had sound but it didn't like any of my wireless cards... I cant belive they dont support prism chipsets!

back to ubuntu (I never really wanted anything else)

That will teach me!!! :-P

---

### Post by varunus on 2005-08-08
When you had fedora installed, did you type in lsmod | grep snd?  Or alsamixer?  This way, you could have known what fedora was doing with your config to makes sound and just done the same in Ubuntu...

Sorry if its too late for that...

---

### Post by blakamin on 2005-08-08
[QUOTE=varunus]When you had fedora installed, did you type in lsmod | grep snd?  Or alsamixer?  This way, you could have known what fedora was doing with your config to makes sound and just done the same in Ubuntu...

Sorry if its too late for that...[/QUOTE]
HA... I didn't even think of that coz i hated it so much.... ooops ](*,) 


Oh well... i'll get it oneday, prolly when breezy becomes stable!!

---

### Post by DancingSword on 2005-08-08
[QUOTE=blakamin]Cheers, guys,. tried all that.... i'm thinking of living in silence...lol[/QUOTE]
 this swiped from another thread, and I did an equiv to it using vigr, 'cause I didn't 'get' usermod ( I looked at the group* commands, not the user* commands to do it )

sudo usermod -G audio blakamin

should add you to group audio
and that'll get KDE working, but not amaroK ( which can't find ANY soundsystem, even though KDE makes noise fine. Bleah. )

---

### Post by blakamin on 2005-08-08
I dont think it even matters anymore... the fan died during install and I couldn't hear it over the cd-rom.... cooked the graphics chip...  ](*,)

---

### Post by blakamin on 2005-12-07
A small update... 

my cousin (more like a brother), who I bought this laptop off, died 2 months ago (31, heart attack from diabetes complications). 

I Hadn't turned it on since about a week before he died...and it was still; broken.


Last week I decided to turn it on to see how bad it was so I could maybe sell it for parts and, voila, IT WORKS AGAIN!!!!

No idea why, no idea how....

anyway, I've installed breezy, run through everything again.... AND STILL NO SOUND:cry: 

everything is showing up and i'm confused again.... did a forum search and tried all the tricks...

has anything developed to solve dell problems that I might of missed while it hasn't been working???

---

### Post by coderasm on 2005-12-08
Take a look at this thread and try to follow the advice. Hope it helps
```
          http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4
```

---

### Post by blakamin on 2005-12-08
[QUOTE=coderasm]Take a look at this thread and try to follow the advice. Hope it helps
```
          http://www.ubuntuforums.org/showthread.php?t=87849&highlight=ich4
```[/QUOTE]
Unfortunately, it wasn't enabled....:(

---

