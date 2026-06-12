---
title: "[SOLVED] Unable to Disable System Beep when (un)pluggin AC Adapter"
date: 2008-08-18
forum: General Help
---

### Post by probain on 2008-08-18
First time poster. 

I'm using Hardy on an Acer TravelMate 5520 Laptop. And I'm having extreme difficulties finding how to disable the System Beep for when I (un)plug my AC Adapter. Note that this is NOT the common misspell-in-terminal or wake-up-from-hibernation beeps. The sound is identical, but the cause for it differs. 

The beep plays through the ordinary soundcard. Because if I've muted  my speakers the beep becomes "muted" too. Although that is in no way near a fix. 

As I'm using a laptop I (un)plug the AC Adapter quite often. Especially since my battery is decaying. And having a loud audible BEEP for whenever I do this is REALLY getting on my nerves. Most so when I'm using earplugs and the beep is making me fear for my hearing some day, since it is just so incredibly loud.

Here is what I've done/tried so far, without desired results:

[LIST]
[*]Removed and blacklisted the pcspkr module in "/etc/modprobe.d/blacklist"
[/LIST]

[LIST]
[*](re)Unchecked Everything "System Sound/Beep" related in Sound Preferences.
[/LIST]

[LIST]
[*](re)Unchecked "Use sound to notify in event of an error" in gnome-power-manager.
[/LIST]

[LIST]
[*]Removed gnome-power-manager... This proved that the issue is not with this app at all.
[/LIST]

[LIST]
[*]Checked "PulseAudio Preferences" for anything related without results.
[/LIST]

[LIST]
[*](edit) There is no option in BIOS for this either. The beep is of Ubuntu system origin since it is higher pitched than "standard" error beep.
[/LIST]
---------------------------------------
Hoping that some one knows which config file to edit or anything that can solve this issue. Any tips

---

### Post by sdennie on 2008-08-18
Sounds like you've tried everything but looking at the BIOS.  Both for an option that is causing it or a possible BIOS update.  A possible way to test if a BIOS update would help would be to but up but enter the grub menu and try unplugging/replugging in the machine.  If there is no sound that's not definitive proof that a BIOS upgrade wouldn't help.

Also, check /var/log/syslog and /var/log/acpid.log for possible information after getting the beep.

As a last resort, you could drop a script to mute the volume in /etc/pm/power.d and then unmute it a second later whenever the ac adapter state changes.  That may not prevent it if the sound happens before the script kicks in to mute it though.

---

### Post by probain on 2008-08-21
> **vor said:**
> Also, check /var/log/syslog and /var/log/acpid.log for possible information after getting the beep.


I tail -f both log files, and only /var/log/syslog had life.. /var/log/acpid said nothing. 
```
Aug 21 16:06:59 UNIX anacron[7977]: Anacron 2.3 started on 2008-08-21
Aug 21 16:06:59 UNIX anacron[7977]: Normal exit (0 jobs run)

```
However, this only apeared when I plugged the AC Adapter **into** the laptop again. 

Also to clarify a bit on my initial post. The beep is unaffected by volume (master, pcm and front alike), it is always maxed out. Only when the master channel is muted does the beep become inaudible.

Second: Sadly I wouldn't even know how to begin a script like you suggested since I don't know which app is causing the beep, or where to continue looking for it.

---

### Post by probain on 2008-08-25
*Bump*

---

### Post by probain on 2008-08-30
Re-Bump

---

### Post by probain on 2008-09-12
pity-Bump

---

### Post by Het Irv on 2008-09-12
Hun... thats weird... 
My laptop never beeps at me... which leads me to belive that it is a system/BIOS thing... but... you said that there is nothing there... and since the beep comes thought the speakers/headphone jack I would say check the Sound Dialog box, but you have done that...  

Have you tried turning off the System Beep and turning on the Visual Beep?  or Unchecking the box in the second tab that says "Play System sounds"?

---

### Post by EmanresuusernamE on 2008-09-12
Some of the newer laptops out there will always beep at you when you loose power, as if to say: "I'm on batteries and it would be best for you to save everything and shutdown, or give me power again."

If you kick the cord out from the laptop, or from the wall, it's a little notice for you to put it back as the lights would still be on and you probably wouldn't notice the lack of power to the laptop.

---

### Post by probain on 2008-09-12
Thx for replying Irv.

Yes I have tried, and re-tried, checking and unchecking all the options related in Sounds Preferences.

---

### Post by probain on 2008-09-12
Thx for replying EmanresuusernamE.

When I had XP and/or vista installed no such "kicking out the cord notices" where necessary. Or at least was able to shut it off. And the beep is the classic ubuntu/linux beep with a higher pitch than standard system beep.

And it bugs the heck out of me that it can't be turned off >_<

---

### Post by EmanresuusernamE on 2008-09-12
System > Preferences > Power Management.  General tab, then try unchecking Use sound to notify in event error.

---

### Post by probain on 2008-09-12
Tried and re-tried that too. Also tried purging the app gnome-power-managment, and even without the app installed the beep beeped. But it should prove that it has nothing to do with the app itself.

I've also tried KDE's variant (can't remember the name right now), And that too had no effect :(

---

### Post by Het Irv on 2008-09-12
You could try Vor's script Idea, unfortuneatly I don't know how to code that well.  But if you could write the script so that when the system would beep the system, would be muted first. or for that matter could that file be edited to remove the code for the beep... I have no idea. I am not sure if Vor is still subscribed to this...

---

### Post by probain on 2008-09-12
I would love to try that. How ever, I have little to no idea on even how to begin scripting a mute function. Also as I posted before, when I did a tail -f on the log files, an anacron event only occured when I plugged IN the cord. But having a script sollution would surely be better than no sollution at all :)

---

### Post by EmanresuusernamE on 2008-09-12
How about renaming the sound it's playing, and then point everything else to the new name?

---

### Post by Het Irv on 2008-09-12
if you could do that to a blank mp3 or oog that would work.

---

### Post by probain on 2008-09-12
Renaming the mystery sound kinda brings me back to my inital conundrum. I can't find any reference to where said beep is comming from. Even which device being used in /dev/ is eluding me. Maybe finding that out could make it possible to link it to /dev/null at least.

Any tips to where the system beep is being called from would be greatly appreciated. :)

---

### Post by EmanresuusernamE on 2008-09-12
You said it was making the system default sound, find that, and then rename it.

---

### Post by probain on 2008-09-13
OK... It turned out that I was horribly wrong, in a sence. What I thought was a linux/ubuntu system beep, acctually turned out to be a computer standard/BIOS related beep, since it beeps even before grub is loaded. But no option in BIOS can be found though. You can imagine my face turned red when I did the extra testing to find this out... However, since I have blacklisted the pcspkr module I still have no clue from where it's originating.

Here are my loaded modules, and if anyone can name the culprit then I would be very happy.

Or at least give some clues to a nother sollution other than blacklist.

*edit* Also, when issuing a system shutdown, the beep becomes disabled a short time after X has shut down, but before the network has shut down (or at least from what I can read in the very rapid succesion of lines). So something is keeping the beep alive whilst the system is up and running, be it an app or module or whatever.

```
Module                  Size  Used by
isofs                  39464  0 
af_packet              27272  2 
binfmt_misc            14860  1 
rfkill_input            6912  0 
b43                   159280  0 
rfkill                 10144  3 rfkill_input,b43
mac80211              192532  1 b43
cfg80211               17680  1 mac80211
input_polldev           6928  1 b43
b44                    33168  0 
ssb                    39428  2 b43,b44
mii                     7552  1 b44
ndiswrapper           243872  0 
ipv6                  311720  22 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  2 parport_pc,lp
joydev                 15488  0 
pcmcia                 45976  0 
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
snd_hda_intel         440536  7 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
uvcvideo               62212  0 
snd_rawmidi            29856  1 snd_seq_midi
compat_ioctl32         11136  1 uvcvideo
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
videodev               30720  1 uvcvideo
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
fglrx                1804800  20 
snd_timer              27912  2 snd_pcm,snd_seq
sdhci                  21508  0 
wl                   1081936  0 
ieee80211_crypt         8192  1 wl
ac                      8328  0 
battery                16776  0 
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   53892  0 
nsc_ircc               27472  0 
psmouse                46236  0 
container               6656  0 
video                  23444  0 
output                  5632  1 video
snd                    70856  24 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              11148  0 
irda                  222956  1 nsc_ircc
serio_raw               9092  0 
mmc_core               59272  1 sdhci
yenta_socket           30092  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic
acer_acpi              21720  0 
led_class               7176  2 b43,acer_acpi
button                 10912  0 
i2c_core               28544  1 i2c_piix4
crc_ccitt               3584  1 irda
evdev                  14976  9 
k8temp                  7680  0 
wmi_acer               11076  1 acer_acpi
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
atiixp                  6672  0 [permanent]
ide_core              136600  1 atiixp
pata_acpi               9856  0 
ata_generic             9988  0 
sg                     41880  0 
sd_mod                 33280  3 
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
pata_atiixp            10496  0 
ehci_hcd               41996  0 
ohci_hcd               28956  0 
ahci                   33284  2 
usbcore               170288  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd
libata                176432  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              178488  5 sbp2,sr_mod,sg,sd_mod,libata
thermal                19744  0 
processor              41832  1 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  1 
```

---

### Post by dlstyley on 2008-09-14
I have this exact problem on Acer Extensa 4420.   It's really obnoxious.  If you figure this out, I would love to know the solution.

---

### Post by grim4593 on 2008-09-14
I have the same exact problem on a Lenovo T60. It also makes the beep when I go into standby, which is really annoying in the dead of the night or if I am in a classroom. Yes, hitting the mute button works but sometimes I forget.

---

### Post by probain on 2008-09-15
I marked this thread as SOLVED. This due to a wonderfull upgrade to Intrepid Ibex. Where I was able to mute the beep by it self without muting the speakers..

Mind you though, on a completly differnt side not, as of yet fglrx (2008-09-16) is not compatible with X.org.. Just a heads up for anyone planning on upgrading to "fix" the "problem"

---

