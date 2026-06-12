---
title: "Playing music over the network"
date: 2008-07-24
forum: General Help
---

### Post by agaudio on 2008-07-24
Hello,

I have searched the threads for something similar to this, but I haven't really found anything. I was wondering if anyone had any advice for how to use my desktop Ubuntu computer which contains all my music together with some other device on the network to play this music. In the Windows world, I probably would have bought a Roku Soundbridge and set it up over the network, but this only seems to work with Windows and Mac. Does anyone have any alternative suggestions?

Thanks!

---

### Post by Dylock on 2008-07-24
What kind of devices are going to be playing the music?

If its for computers, look into mpd

---

### Post by agaudio on 2008-07-24
I suppose I could set up another computer to play back the music, but I was hoping for something a little more small scale, something like a Soundbridge for example.

---

### Post by mcduck on 2008-07-24
I'm not familiar withthe Soundbridge, so could you tell which one you want to acchieve, keeping the files on one machine and playing them on a remote machine, or keeping the files on the same machine that will play them, but control it from a remote machine?

---

### Post by flytripper on 2008-07-24
if it is windows media connect compatible you should be able to use [twonky]("http://www.twonkyvision.de/") media server to stream... its a free download and as far as i'm aware, the license does not expire(though they say it does)

---

### Post by agaudio on 2008-07-24
I'm looking to have the music on my desktop and play it remotely elsewhere in the apartment.

---

### Post by imon9 on 2008-07-24
ever thought of using samba to share your musci folder and the other computer can play it?

or do u mean, u want to remotely control your current computer to play certain song? if that is the case, try MPD with a web client:
[http://www.musicpd.org/clients.shtml](http://www.musicpd.org/clients.shtml)

---

### Post by jocko on 2008-07-24
You can use pulseaudio to send a sound stream to another computer.
Just make sure you have pulseaudio on both computers (it should even be possible to run pulseaudio on windows, the installer can be found [here]("http://www.cendio.com/pulseaudio")).
[This page]("http://pulseaudio.org/") may be helpful on setting things up, especially have a look at the [FAQ]("http://pulseaudio.org/wiki/FAQ")s to find answers to most of your questions.
[Here's a good thread]("http://ubuntuforums.org/showthread.php?p=4928900"), maybe not for sending audio over the network, but to set up pulseaudio to work the way it's intended to work on ubuntu.

EDIT: Didn't realize you wanted to stream the sound to something else than a computer... Aren't there wireless usb sound cards that can do what you want?

---

### Post by cszikszoy on 2008-07-24
You actually should be able to use the Soundbridge from Roku.  And, you actually have a couple of options.  After looking at the specifications of the Soundbridge ([http://www.roku.com/products_soundbridge_specs.php](http://www.roku.com/products_soundbridge_specs.php)) I see that it uses windows media connect (which is basically just a UPnP media sharing server).  I stream audio and video from my linux computer to my xbox360 (which sort of uses the same protocol).

Someone sugested twonky, which might work.  Or there's Fuppes which is another UPnP media streaming server, and I believe rythmbox even has a UPnP plugin too ([https://coherence.beebits.net/wiki/RhythmBox](https://coherence.beebits.net/wiki/RhythmBox)).

I'm not saying that the soundbridge will work 100% for sure, but there's a good chance that it will.

If all of the above don't work, you can always run iTunes inside of a VM.  It seems the soundbridge also supports iTunes sharing.


**edit**

Actually, after further reading the rythmbox page I linked to, it specifically states that he has it working with the Roku Soundbridge.

---

### Post by inkrypted on 2008-07-24
I was just gonna suggest the same thing. I use Fuppes to stream from my Xbox 360 and my PS3 the setup is a little rough but after that it works like a champ and might work with Soundbridge.

---

### Post by cszikszoy on 2008-07-24
> **inkrypted said:**
> I was just gonna suggest the same thing. I use Fuppes to stream from my Xbox 360 and my PS3 the setup is a little rough but after that it works like a champ and might work with Soundbridge.

Did you install Fuppes with transcoding of video for the 360?  I could never really get fuppes to work with the 360.  I didn't really spent a lot of time trying to fix it though.  The setup is quite rough for Fuppes.

It would be nice if someone could make a precompiled version, already setup with transcoding for easy sharing with the 360.  Or at least some kind of installer to help configure ffmpeg to work proplerly for transcoding with fuppes.

---

### Post by Endolith on 2008-11-10
I would love to be able to play music over the network natively, as PulseAudio claims to do (but probably doesn't work in Ubuntu without lots of manual labor).  Currently I just run Rhythmbox on the other machine using ssh (I have a launcher for **ssh -fXC remotehostname rhythmbox**) and then I can control it from this computer.   I have music files on both machines, and have the files on this computer mounted on the other through sshfsmount.  Works pretty well.

[http://ubuntuforums.org/showthread.php?p=5352993#59](http://ubuntuforums.org/showthread.php?p=5352993#59)

If I can just have one music player that can choose which speakers to output to, that would be ideal.

---

### Post by Endolith on 2008-11-16
I actually got the PulseAudio working from another machine, but decided I prefer running Rhythmbox remotely instead.  With remote PulseAudio, it has to send raw uncompressed audio streams for each application over the network, which swamps your connection.  With remote Rhythmbox, it only sends the control information, which is much lower bandwidth, and maybe a compressed mp3 file if you have it stored on your local machine, which is still much less bandwidth than uncompressed audio.  There are fewer dropouts and problems, yet the interface is just as responsive.

---

