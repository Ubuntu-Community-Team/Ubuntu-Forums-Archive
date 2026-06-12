---
title: "hda intel input troubles (sigmatel chipset)"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by morgengenuss on 2007-02-13
hi.

i'm using xubuntu since dapper and i'm quite satisfied with edgy, only one thing really bothering me. my sound-card really doesn't work properly (i think it even worked better under dapper than in edgy).

my problem:
- output: works fine, but "lfe"(internal laptop subwoofer) is always muted on bootup, which i hate, because i have to unmute it everytime i start my laptop.
- input: this is the real troublemaker. just like "lfe" it's always muted on startup but furthermore i cannot unmute "capture", i can only unmute "capture mux" and that doesn't give me any recording functionality. the xfce-mixer-panel-applet just puts back the volume bar for "capture" immediately if i try to raise it and alsamixer and the like don't even show a "capture", only "capture mux". the only mixer that seems to be working is the gnome-alsa-mixer, but lately even that doesn't make me successful anymore. (btw: of course i have to unmute the "capture" channel each time i bootup, because these darn mixers don't seem to remember anything).

my setup:
- alsa 1.0.14rc2 (tried the edgy-standard stable as well and 1.0.13 but without big differences, except for "lfe" only working in 1.0.14rc2)
- gnome-alsa-mixer, xfce-mixer, alsamixer (console), alsamixer-gui;
- laptop: dell inspiron 9400, dualcore 1,8ghz; 2gb ram 666mhz; 100gb hdd; ati x1400; hda intel soundcard (sigmatel stac92000);


ok, hope someone was experiencing the same and has come up with a solution (or at least a workaround) for this annoying problem.
(or do i really have to wait for a newer alsa-version that might solve the problem?)

thanks anyway,
morgengenuss

---

### Post by treesurf on 2007-02-24
I am having a similar problem.  Sound output is fine, but input barely works.  Any sound input from the mic jack is severely muted.  There is no volume control slider for the mic in alsamixer, and I'm at a loss for what to do.

This is a Gateway NX570X, hda intel soundcard, sigmatel chipset

Any suggestions would be appreciated!

---

### Post by morgengenuss on 2007-02-26
you can try to install gnome-alsamixer via synaptic or apt and see whether it shows the input-channel for you as well.
it should work, the only annoying thing is you have to unmute it manually on startup...

---

### Post by treesurf on 2007-02-27
I used the instructions on another thread to install alsa 1.0.14rc2.  Previous to this alsamixer only showed master and pcm.  Now I have several capture options as well.  The Sound Capture test function under System>Preferences>Sound still crashes when I try to use it.  Sound Recorder also crashes when I try to use it.  I'm not sure how else to test the mic right now.

I am also a little unclear about some of the on/off switches in alsamixer: Line in as output, Mic as output, input source, and off hook.  What do these mean and should I have them checked or not?

Thanks!

---

### Post by morgengenuss on 2007-02-27
difficult to say what to do with these checkboxes... actually i assume that they don't change anything, at least they didn't for me.
before updating to 1.0.14rc2 i had a checkbox called "lfe", now i have a channel called lfe (which is the internal subwoofer) and can use it. before there was nothing.

what exactly happens (i mean error-wise) when e.g. sound-recorder crashes? or is it that you just don't have any signal from your mic?

---

### Post by treesurf on 2007-02-28
Sound recorder just freezes when I try to use it, and I have to force quit.  This happens when I click on the record button.  The Test Sound funtion for Capture in the System>Preferences>Sound panel gives me the following error before freezing:

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'


Did updating ALSA solve the mic problem for you?

---

### Post by morgengenuss on 2007-02-28
never had this error, but generally updating to alsa1.0.14rc2 helped. intel hda is generally not so well supported by alsa, but seems they're working on it. at least within the last few versions of alsa many things have changed for better.

since it's an easy thing to do i would recommend upgrading to 1.0.14rc2.

---

### Post by dimeotane on 2007-03-08
I'm experiencing problems getting my headset microphone to work on my Dell XPS M1210.  I plug it into the line/mic in but can't record from the microphone on anything.  I've tried setting the sound capture  to alsa, and using asla mixer turning the capture mode on.   but no luck.

---

### Post by treesurf on 2007-03-09
Yup, I've pretty much given up on it for now.  I ordered a cheapo USB sound card of off ebay that I'm told should work out of the box.  Hopefully it will be good enough for VoIP at least.

---

### Post by ianfp on 2007-03-31
Hey, let us know if your USB sound card works.  I'm considering the same solution (workaround?) myself.

---

### Post by treesurf on 2007-04-01
I did get the cheapo USB sound card, but I have not had any luck getting it to work unfortunately.  When I go to the sound preferences panel it does not give my an option to choose USB sound.  Audacity does not give me the option either.

---

### Post by morgengenuss on 2007-04-02
just one thing that one might easily be overlooked: your alsamixer does not show you all the options if you just run "alsamixer"; if you want to see all the channels use the " -V all" switch. i only saw capture mux before, that's why my headset wouldn't record.

i would say: upgrade to 1.0.14rc3 and then look into your alsamixer, there should be all the input channels, unmute them, set capture to recorded channel (by pressing space) and then see whether you can record.

---

### Post by zabzoo on 2008-07-05
I've got exactly the same problem ....

lspci
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
...

when the analogue loopback is enabled, I am able to hear myself speak over the microphone, but not skype nor any other recording software actually records any audio.  I ran 

alsamixer -V all
Enabled L  R CAPUR on the Capture Device
Input Source is on MIC (I dont hear anythig on the loopback if this is disabled)

Mux is also enabled (without this too; no loopback sound is heard)

I know the mic works; using it on another machine.

Runny Hardy Heron (Kubuntu 8.04 with Kernel 2.6.24-19-generic [KDE4)

I had the same problem with Ubuntu Gutsy (7.04)

Is there any help for me; I'd really like to use Skype, Ventrillo etc. on my linux box and not on windows.

Thanks

---

