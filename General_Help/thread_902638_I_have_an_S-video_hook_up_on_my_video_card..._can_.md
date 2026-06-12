---
title: "I have an S-video hook up on my video card... can I plug a tv to it?"
date: 2008-08-27
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-27
I have an old TV (For now) so hooking up via dvi or hdmi is not possible.

I have a little converter box on the tv, for video, L&R audio, and I'm 99% sure I also have a s-video IN port on this converter box too.

So can I plus an S-video cable into this video card and get a feed?

Does audio travel through S-video?

---

### Post by fooman on 2008-08-27
yeah,  so long as you have an input for s-vid...then it should work.  

no,  there is no audio carried through the s-video cable.

i have my s-video going from my 8800gt to my toshiba 35" analog t.v..  it works great!  lucky for me,  my t.v. and home theatre setup is located right next to my desk...so i can run the s-vid to the tv set for the video and the s/pdif output from my motherboard to my home theatre receiver for the audio.

---

### Post by PsychedelicWonders on 2008-08-27
How do I activate the s-video for the tv to work like a monitor?

Do I have to unplug the cable? (cable tv, not wire)

Or can i set it to come on on a particular channel?

What I have is an HTPC, I currently have a Sony Home Theater System, but there doesnt seem to be any "input" for any other devices.

I am going to sell this home theater setup and buy a new really sweet speaker and subwoofer setup.

I wont need a receiver any longer will since I am going to buy a kit that will plug right into my audio card will i?

Any suggestiosn on a speaker/sub-woofer set up that is small and compact liek bose and gives off the same quality?

---

### Post by fooman on 2008-08-27
well if you have an nvidia card you would have to configure the X screen to use either "separate x-screen" or "twinview"(i use separate x-screen) in the "nvidia-settings" program.  there is a similar control panel for ati, if you have one of their cards.  

as for the t.v.....mine has different choices in the menu for video1, video2, aux, s-video etc..  i just have to change that setting....doesn't matter what channel it is set to.

btw...the t.v. sucks for use as a monitor.  fonts are practically impossible to make out.   i only use for watching videos from my computer.  and it works *very* well at that. :)

---

### Post by PsychedelicWonders on 2008-08-27
yeah im just going to use it to watch videos for now.  No reading.

I have an Nvidia card, so where do i find the Nvida settings file?

What is the difference between "separate x-screen" or "twinview"?

---

### Post by fooman on 2008-08-27
if you have your nvidia drivers installed,  the nvidia-settings may already be installed.  look in applications > system tools (if you installed them manually from the nvidia site) or, either under system > preferences or system > administration if you installed the drivers from the repo's or envyng.

if you don't find them there and your drivers *are *installed,  then install the nvidia-settings package from synaptic or in a terminal:

```
sudo apt-get install nvidia-settings
```

separate x-sceen will give you just that...2 separate screens, each with their own resolutions, panels and such.

twinview will give you one long screen, spanning across both monitor(s)/t.v..  with both sharing the same resolution (i think) and panels.  i guess twinview would work best with 2 same size monitors.

with twinview, you can drag items from one screen to the other....with separate x-screen you cannot.

---

