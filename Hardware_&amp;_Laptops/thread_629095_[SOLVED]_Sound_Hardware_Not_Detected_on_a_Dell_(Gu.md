---
title: "[SOLVED] Sound Hardware Not Detected on a Dell (Gutsy)"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by TuxLove on 2007-12-02
[SIZE=3]Target Laptop: Dell Latitude D531

**lspci -v** tells me (among other things):[/SIZE]  

[FONT=Courier New][SIZE=2]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 0206
        Flags: slow devsel, IRQ 17
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2[/SIZE][/FONT] 

Yet **aplay -l** says:
[FONT=Courier New][SIZE=1]
[SIZE=2] aplay: device_list:204: no soundcards found...[/SIZE][/SIZE][/FONT]


And here's the snd- bits from **lsmod**...
[FONT=Courier New][SIZE=1]
[SIZE=2] snd_hda_intel         263712  0
snd_pcm_oss            44672  0
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pc[/SIZE][/SIZE][/FONT] 

More clues?[LIST]
[*]Sound *appears* to work okay booting a Knoppix 5.1.1 DVD -- but no sound is audible. (Yes, the volume is at 100%)[/LIST][LIST]
[*]Booting a Mepis 6.5 CD actually produces sound, but it locks and repeats continuously after the first half-second or so. (Killing the app doesn't stop the sound. The only way to do that is to force-reload alsa!)[/LIST]Any suggestions...?

---

### Post by TuxLove on 2007-12-19
[U][B][COLOR=Black]Fixed it!

[/COLOR][/B][/U]Here's how:

I followed the *"Update to the Latest Version of ALSA"* instructions here...
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

(Note that the latest version of ALSA is now 1.0.15. You'll find all the downloads here [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) )

After the installation and reboot, I ran [FONT=Lucida Console]**sudo alsaconf**[/FONT] and followed the instructions My card was correctly detected and I now have sound.

---

### Post by konungursvia on 2007-12-25
Do you have multiple source multiple channel mixing, or just one device at a time? Just curious as I'm finding I have sound but not from more than one app at a time.

---

### Post by TuxLove on 2007-12-30
Yeah, I do get sound from multiple apps running at the same at the same time.

---

