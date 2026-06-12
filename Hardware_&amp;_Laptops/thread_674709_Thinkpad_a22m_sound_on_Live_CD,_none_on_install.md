---
title: "Thinkpad a22m sound on Live CD, none on install"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by nethbar on 2008-01-22
I've had this Thinkpad for awhile and the sound has worked at one point in the past.  After some updates and an attempt to slim the auto-loading modules, I can't get the sound to work.  I have 7.10 installed.

I've booted off of the 7.10 Live CD and the sound works great.  What should I look at to see what is working there and isn't here?  

(Note: I've checked alsamixer levels and alsa-utils is running.)

Thanks!

EDIT:
I've done a comparison of loaded modules between the live CD and the installation and all sound related modules are loaded the same

---

### Post by nethbar on 2008-01-24
Bump

I've been trying most help guides I can find with no luck.  Here's some additional info:

I ran
a@a:/usr/share/sounds$ aplay -D default startup.wav
Playing WAVE 'startup.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: pcm_write:1265: write error: Input/output error

When I unmute my PCM channel and turn it all the way up, I get static out of my speakers

**aadebug:**

```
ALSA Audio Debug v0.1.0 - Thu Jan 24 00:18:55 CST 2008
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux tartarus 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_cs46xx             85096  1 
snd_ac97_codec        100644  1 snd_cs46xx
snd_pcm_oss            44672  0 
snd_pcm                80388  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  2 snd_cs46xx,snd_pcm

Modprobe Conf ---------------------------------------------

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xf4122000/0xf4000000, irq 11
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: raw midi
  5: [ 0- 2]: digital audio playback
  6: [ 0- 1]: digital audio playback
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0]   : control
cat: /proc/asound/hwdep: No such file or directory
00-02: CS46xx - IEC958 : CS46xx - IEC958 : playback 1
00-01: CS46xx - Rear : CS46xx - Rear : playback 31
00-00: CS46xx : CS46xx : playback 31 : capture 1
Client info
  cur  clients : 4
  peak clients : 4
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1
Client  16 : "Sound Fusion CS46xx" [Kernel]
  Port   0 : "CS46XX" (RWeX)

Dev Snd ---------------------------------------------------
controlC0  midiC0D0  pcmC0D0c  pcmC0D0p  pcmC0D1p  pcmC0D2p  seq  timer

CPU -------------------------------------------------------
model name	: Pentium III (Coppermine)
cpu MHz		: 697.449

RAM -------------------------------------------------------
MemTotal:       255940 kB
SwapTotal:      746980 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

```

---

### Post by Benanov on 2008-01-30
I have this exact model and sound *is* working for me.  PM me and i'll send you any log you wish. :)

---

### Post by Yellow Pasque on 2008-01-30
[http://www.alsa-project.org/main/index.php/Matrix:Module-cs46xx](http://www.alsa-project.org/main/index.php/Matrix:Module-cs46xx)

---

### Post by nethbar on 2008-02-05
FIXED (?):
I think the sequence of events went something like this:
- Made system changes, hibernated system
- Powered system back on, discovered sound no longer worked, assumed system changes the cause
- Tried to troubleshoot sound problems myself, stuck
- Posted here, received excellent help here and on other related post
[http://ubuntuforums.org/showthread.php?t=676678](http://ubuntuforums.org/showthread.php?t=676678)
- Read over solutions, got busy
- Finally rebooted to start fixing and discovered sound works fine on a full reboot

So I guess I'm facing an APM/ACPI issue?  It's never worked quite right; I can manually hibernate or standby but letting the laptop do it on its own causes problems.  I'll bring it back up, the login screen comes up but within seconds the laptop powers off.  When I power it back on, Ubuntu loads just like I was coming out of hibernation only there's no login screen and poof, there's all my open work.

When I hibernate, there's a sound related error I've caught:

**cs46xx: failure waiting for FIFO command to complete**

but I don't know where to look for a complete log.  Searching elsewhere hasn't turned up anything helpful.

Trying to come out of standby or hibernate is impossible with a my PCMCIA wireless card plugged in (Linksys job using ndiswrapper).  It will either hang or... hang I guess.  It doesn't seem to matter if I powered down with the card in or not.

Any recommendations?  Should I move my post?

BENANOV: If you've had to debug power management on your Thinkpad, your advice would be invaluable

---

### Post by Benanov on 2008-02-05
Haven't had sound work after hibernating / suspending.

If you want me to look I can try, but I don't know how much help I'll be.

---

### Post by nethbar on 2008-02-06
Well, I'll be sure to let you know if I find a fix.  I sure like this laptop.

---

### Post by Ulysses361 on 2008-04-08
Hi,

I recently had the exact same problem on my Thinkpad A20m running Antix (antiX-M7.2-preview1). The master volume level was high in alsamixer, but I still had no sound in Firefox or the vlc player.

I also got the error - cs46xx: failure waiting for FIFO command to complete - during each boot of the pc, according to the dmesg output.

All this debugging info is actually irrelevant. The real problem on my pc was the volume setting in aumix. The volume was set to 0 in aumix and apparently that aumix volume setting has priority over alsamixer.... After increasing the volume in aumix, the sound was working again on my laptop.

If this does not help, you might need to create the file .asoundrc in your home directory. It should contain the following config settings:

pcm.!default {
   type hw
   card 0
   }

ctl.!default {
   type hw           
   card 0
        }

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"
    #   period_time 0 # set to 0 lets period size and buffer size do everything
             period_time 2 # this is the general standard even though often is set to 0
         #   period_time 84000
         #   period_size 512
             period_size 1024 # oss period frames this is the one shown as hardware for me
         #   period_size 128
    #   period_size 2048
         #   period_size 4096 # not great to go over this
         #   buffer_time 340000
    #   buffer_size 16384 # this is the one shown as hardware but causes huge mess
         #   buffer_size 8192
         #   buffer_size 4096
             buffer_size 2052 # this is the one i use
             rate 44100 # can let card decide this on it's own this one is what hardware says
    #   rate 48000

   }
   bindings {
       0 0
       1 1
   }
    }

    ctl.dmixer {
   type hw
   card 0
    }


Hope this helps someone.

Regards,

Mark Rijckenberg

---

