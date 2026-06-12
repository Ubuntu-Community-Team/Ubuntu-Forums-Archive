---
title: "How to: Mono sound for Single Speaker Acer Laptops"
date: 2011-02-26
forum: Hardware
---

### Post by nolo on 2011-02-26
Hi all,

For everyone running ubuntu on a laptop with a stereo audio adapter but only one built-in speaker, like the Acer Aspire series, here's how you create a mono profile so you can hear both channels through the single built-in speaker:

In Terminal run:
```
$ pacmd

```at the prompt enter:
```
>>> list-sinks
```Note your main sink's name so you can inset it into the following code:
```
>>> load-module module-remap-sink sink_name=mono master=[YOUR MAIN SINK'S NAME] channels=2 channel_map=mono,mono
```If you have entered the command correctly, you should be returned to the >>> prompt. Do not exit at this time.

Open Sound Preferences and chose "Remapped Internal Analog Stereo* Mono*"

You may want to reduce the master volume to prevent audio clipping.

The Mono setting will last as long as pacmd is running in Terminal.  To make it permanent, add the command to the end of /etc/pulse/default.pa.

Hope this helps you enjoy ubuntu on your laptop.

nolo

---

### Post by codyv on 2011-02-27
can you please walk me through this step i cant seem to figure it out, i get ikt to work by running pacmd and everything but cant figure out how to edit that file an" :/

"The Mono setting will last as long as pacmd is running in Terminal.  To  make it permanent, add the command to the end of /etc/pulse/default.pa."

---

### Post by nolo on 2011-02-28
In Terminal enter:
```
$ sudo gedit /etc/pulse/default.pa
```

Position your cursor at the end of the file and add the command:
```
load-module module-remap-sink sink_name=mono master=[YOUR MAIN SINK'S NAME] channels=2 channel_map=mono,mono
```

Then save the file in gedit.

This will make the mono setting a permanent choice under Sound Preferences.

Good luck.

Nolo

---

### Post by codyv on 2011-02-28
It seems to have worked except for oen thing, if i turn my volume up even remotely high there is major cracking etc. i have to have the volume so low i can barely hear it. any way to fix this?:confused:

---

### Post by codyv on 2011-02-28
got never mind thanks so much

---

### Post by codyv on 2011-02-28
its happening again. any way to fix the crackling?

---

### Post by Sylos on 2011-12-07
Hello.

I have a packard bell with a similar set up - single speaker. 

I have tried following the guide above but it has had no effect on the sound - im still only getting one channel of audio.

Can anyone offer any guidance?


Cheers

 EDIT: Got it working but like others I have terrible crackling and popping. I guess nobody has a fix for that?

---

### Post by Lemagex on 2012-10-25
I know this is an old thread, but I've had this problem too. these instructions are still valid in 12.10 and as for the "crackling" people still have after using these settings, my solution is to switch back to the NON remapped stream in Gnome sound settings, turn the volume on that up to say 105% then switch back to the remapped stream and turn the volume up just a bit or lower, it allows you to have louder volume before it starts to crack. :)

---

### Post by wildmanne39 on 2012-10-25
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

