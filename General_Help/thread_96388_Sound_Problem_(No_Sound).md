---
title: "Sound Problem (No Sound)"
date: 2005-11-28
forum: General Help
---

### Post by qbproger on 2005-11-28
I installed ubuntu a few weeks ago, and before I can really take it too too seriously everything has to work.  Sound was working for a while with Hoary, but then it stopped and hasn't returned even with the installation of breezy, so i'm not sure what went wrong.

Here are the specs of my sound card (via alsamixer in the terminal)

Card: Ensoniq AudioPCI
Chipset: Cirrus Logic CS4297A rev 4

if anymore information is needed let me know, I'll be happy to provide anything neccesary to get this working.

Any help is appreciated.

---

### Post by Dr. Nick on 2005-11-28
Ive read some on your soundcard and it seems its supported by default in other distros but is muted by default run alsamixer from a terminal and make sure your master volume is turned up.

If that doesnt work, run this from a terminal
lspci -v | grep -i audio

That will tell you the chipset, make sure it comapres to yours. I looked on this site [http://www.alsa-project.org/alsa-doc/]("http://www.alsa-project.org/alsa-doc/") and was unable to find your card mentioned

If the lspci output matches your result run this from a terminal\
 [SIZE=-1]**sudo modprobe** cs46xx 
and then see if that works, IF  the modprobe fixes it then edit /etc/modules.conf by adding cs46xx to it to start on boot

Good luck
[/SIZE]

---

### Post by qbproger on 2005-11-28
when i run
lspci -v | grep -i audio

I get this:
0000:00:09.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128

The modprobe gave a warning than an error.  Not sure what it means, but here is it:
WARNING: Error inserting ac97_codec (/lib/modules/2.6.12-10-686/kernel/sound/oss/ac97_codec.ko): Operation not permitted
FATAL: Error inserting cs46xx (/lib/modules/2.6.12-10-686/kernel/sound/oss/cs46xx.ko): Operation not permitted

---

### Post by Dr. Nick on 2005-11-28
Opps I screwed up, Run "sudo [SIZE=-1]**modprobe** cs46xx" If alsamixer didnt fix it

I am editing my first post aswell
[/SIZE]

---

### Post by qbproger on 2005-11-28
ens1371 <--- that looks familiar (I saw that on the alsa page)  I installed suse a long time ago (8.2 when it was new, and got everything working on it).  I think that might be what I have, if that is any help.

---

### Post by Dr. Nick on 2005-11-28
If the **sudo modprobe cs46xx** didnt help you can subsitute ens1371 instead and just type [B]
sudo modprobe snd-ens1371

[/B]After you run those commands though check each time to make sure your volume isnt muted

---

### Post by qbproger on 2005-11-28
FATAL: Module ens1371 not found.

that might have something to do with this...

BTW, thanks for all the help so far

---

### Post by Dr. Nick on 2005-11-28
Bah, Im in to big a hurry, I need to try these out before posting :)
give this one a shot [B]sudo modprobe snd-ens1371

[/B]Your Welcome, Hopefully this one will solve it

---

### Post by qbproger on 2005-11-28
is it supposed to work instantly after that command?

Don't hear anything yet, not giving up though :-D

---

### Post by Dr. Nick on 2005-11-28
It should work instantly aslong as the master volume is turned up. After loading it run alsamixer in a terminal and check the sound levels, master and pcm should be turned up somewhat, navigate the program using your arrow keys

---

### Post by qbproger on 2005-11-28
i don't hear anything yet :(

in alsamixer I have 2: 3d Contr's and 1: capture

---

### Post by Dr. Nick on 2005-11-28
I dont quite follow you last post, When you start alsamixer look at the very top at the **Card:** and **Chip:** items, Do they seem to correctly identify your card? If so then turn the Master volume up to 80ish and also raise the PCM to 50 something.

Also what kind of speakers do you have. Surround sound or just regular stereo with 2 speakers, Just to be safe are you sure they are plugged into the right jack? ;)

---

### Post by qbproger on 2005-11-29
[QUOTE=Dr. Nick]I dont quite follow you last post, When you start alsamixer look at the very top at the **Card:** and **Chip:** items, Do they seem to correctly identify your card? If so then turn the Master volume up to 80ish and also raise the PCM to 50 something.

Also what kind of speakers do you have. Surround sound or just regular stereo with 2 speakers, Just to be safe are you sure they are plugged into the right jack? ;)[/QUOTE]

I dual boot the machine, and booted into windows. Testing the sound card now, here is the info in the drivers.

Creative AudioPCI (ES1371,ES1373) (WDM)

that's what it says in the device manager.
Yea it definitely works.  I hear the music.

There are no master or pcm faders.

---

### Post by Dr. Nick on 2005-11-29
Well windows telling you that your card is a ES1371,ES1373 would make me think that **sudo modprobe snd-ens1371 **would be the correct command.

If you do a fresh reboot and run **lsmod | grep 1371** from a terminal before trying to load anything what does it show? If it shows sound related stuff then it means it sees your card but something is misconfigured. If you post that result here along with the output of **lsmod **it may help some.

After running modprobe you may have to run  **sudo /etc/init.d/alsa-utils restart **from a termina**l** to restart the sound system, not sure if its needed but it seems logical that It might be, I had never though about that before. 
Just looking online it seems to be well supported so it seems like it would be a simple fix.

---

### Post by crazyness003 on 2005-11-29
Hey, everyon. I'm having the same problem w/ my soundcard. I have an eMachines Laptop. When i do the ```
lspci -v
``` it shows:
> 0000:00:07.0 ISA Brigde: ALi Corp. M1533 PCI to ISA brigde 
and
0000:00:08.0 Mustimedia audio Controller: ALi Corp. M5451 PCI AC-Link
and other gibberish (no idea what they mean)

If anyone can help me out aswell. Sorry **qbproger **to interfere with your post. I just need some help.

Thanx

---

### Post by Dr. Nick on 2005-11-29
[quote=crazyness003]Hey, everyon. I'm having the same problem w/ my soundcard. I have an eMachines Laptop. When i do the ```
lspci -v
``` it shows:

and other gibberish (no idea what they mean)

If anyone can help me out aswell. Sorry **qbproger **to interfere with your post. I just need some help.

Thanx[/quote]

You can try the majority of whats been posted.
[LEFT]Just subsitute snd-ali5451 instead of the others
[/LEFT]

---

### Post by qbproger on 2005-11-29
lsmod | grep 1371 is this:
snd_ens1371            23680  1
gameport               14824  1 snd_ens1371
snd_rawmidi            24704  1 snd_ens1371
snd_ac97_codec         83932  1 snd_ens1371
snd_pcm                88840  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd                    54884  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

just lsmod:
Module                  Size  Used by
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  6
af_packet              21768  2
floppy                 59124  0
pcspkr                  3396  0
rtc                    12344  0
snd_ens1371            23680  1
gameport               14824  1 snd_ens1371
snd_rawmidi            24704  1 snd_ens1371
snd_seq_device          8460  1 snd_rawmidi
snd_ac97_codec         83932  1 snd_ens1371
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  1 snd_pcm
i2c_piix4               8592  0
i2c_core               21200  2 i2c_acpi_ec,i2c_piix4
pci_hotplug            27508  0
intel_agp              23164  1
dm_mod                 57692  1
tsdev                   7776  0
evdev                   9664  0
nvidia               3710980  12
agpgart                34792  2 intel_agp,nvidia
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
tulip                  50080  0
uhci_hcd               31184  0
usbcore               118044  2 uhci_hcd
ide_cd                 41572  0
cdrom                  39616  1 ide_cd
ide_disk               18464  3
ide_generic             1376  0
piix                   10372  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,piix
unix                   26896  619
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


I tried restarting alsa after doing the sudo modprobe snd-ens1371

Still didn't work :(

---

### Post by phrogman35 on 2005-11-29
I had the same problem with a Compaq deskpro. Couldn't get the sound to work at all. Gave up with it.

---

### Post by crazyness003 on 2005-11-29
So, after i type in ```
sudo modprobe snd-xxxnnn
xxxnnn-refering to a soundcard
```
what is supposed to happen? Wen i do it, it just dosnt do anything. I see nothing there. like
```
crazyness003@lappy:~$ sudo modprobe snd-ali5451
crazyness003@lappy~$
```
Nothing happened. I'm confused...

I did see the alsamixer and i set all the levels to mas and turned everything on. Is this good or bad?

---

### Post by Dr. Nick on 2005-11-30
Nothing will happen, I am not sure what to do after that, I had to set it up manually on mine awhile back but forgot what all I changed :( I will look for the guide I used and see what all I had to do

---

### Post by Dr. Nick on 2005-11-30
Well I couldnt find the guide, but if i recall all I had to do was modprobe the driver. 

Check under System-Prefrences-Sound and see what all sound cards are listed their, also make sure both checkboxes are checked.

Check under system-prefrences-multimedia selector and try changing some of those options and then hitting "test"

Hopefully one of those will help some. I havent had much trouble with sound except once so I am not the best at troubleshooting some of it.

---

### Post by kelean on 2005-11-30
Try looking in your /etc/modules and see if the correct sound card is listed.  On my computer I have to insert my sound card in the file before my sound works.

---

### Post by qbproger on 2005-12-03
this is what's in my modules file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
nvidia

---

### Post by Dr. Nick on 2005-12-03
[quote=qbproger]this is what's in my modules file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
nvidia[/quote]

use **sudo gedit /etc/modules** so you can edit and save it, add **snd-ens1371 **at the bottom and save then restart and see what happens

---

### Post by starfire1983 on 2005-12-04
I've been having sound problems with my Intel chipset sound. I'm on a I'm on a Gateway 7322GZ laptop, fyi. The lspci output for the card is:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

I've followed some of the steps in the thread with no luck. Did modprobes with no errors, put snd-intel8x0 into /etc/modules, i've checked alsamixer tons of times and nothing is muted. To my knowledge ALSA is installed fine. 

Only snag is I tried to do the Multimedia Systems Selector test and it "Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'". I've checked all info and it -seems- everything is technically fine but I'm recieving no audio output. No errors visible, except the one above, just no output.

The lspci | grep 8x0 readout is as follows:

snd_intel8x0           34240  1
snd_ac97_codec         84508  1 snd_intel8x0
snd_pcm                92900  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    57764  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10824  2 snd_intel8x0,snd_pcm

Any help would be appreciated. I really like Ubuntu but if I can't get the sound working I'm gonna have to migrate either back to Windows or another distro of Linux :(

---

### Post by qbproger on 2005-12-04
still nothing even with that change.  Anything else you want me to try?

---

### Post by Dr. Nick on 2005-12-05
I would think one of those would solve it, but if not I am out of ideas :( sorry
Hopefully someone else can help

---

### Post by qbproger on 2005-12-09
anyone else have any ideas?

---

### Post by denisesballs on 2006-01-05
I have this chipset on an Asus k8u-x MB. If anyone gets the sound working, please let me know.

---

