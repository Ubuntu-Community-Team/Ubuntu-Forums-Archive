---
title: "Intel audio drivers, constant reboots"
date: 2008-06-10
forum: Hardware
---

### Post by Synival on 2008-06-10
Hi all,
   I have a Gateway laptop, model MT6728, and it looks like I'm using 'snd_hda_intel' for my audio.  I don't know much about the linux sound architecture, so hopefully somebody can help me out :(
   Typically nowadays, I'm running Pidgin and occasionally looking at YouTube videos.  After a certain amount of time, audio stops working in all applications.  (Also, audio in Pidgin tends to "stack up" before actually playing, and will play all at once sometime later.)  Worse yet, applications start crashing, or not loading altogether.  Firefox refuses to start, and the gnome-terminal window APPEARS, but hangs before displaying the command prompt.
   At this point, a ctrl+alt+backspace will restart X, but it will hang and require a full reboot from the console.  (Occasionally, ctrl+alt+backspace will completely reboot instead of restart X, but that could be an unrelated issue.)
   Here's output from lspci and lsmod:

lspci:
------
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

lsmod | grep snd:
-----------------
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

   Anything else I need to post?  Short of preventing the problem, is there any way I can at least FIX the audio problems instead of rebooting completely?  Is this problem already documented?

Thanks in advance!

---

### Post by cetheriel on 2008-08-07
happens to me also. i thought it was related to XULrunner, since sometimes sound plays on Rhythmbox but not on Songbird. might be unrelated as well. onc it happens again i will study further.

---

### Post by millerl on 2008-09-15
Same thing here.  I've tried killing/restarting several services.  Haven't been able to track it down.  Doesn't happen to often and I can't reproduce this intentionally, so it makes troubleshooting a pain.

Rebooting is the only thing that "fixes" it.

Sound stops, programs start locking, same thing with gnome-terminal not displaying a prompt...

I'll throw in more the next time this happens.

---

