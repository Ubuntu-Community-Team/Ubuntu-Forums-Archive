---
title: "Extension .ape"
date: 2008-08-29
forum: General Help
---

### Post by NeoAndersen on 2008-08-29
How to install a program or plugins to play my .ape music?

---

### Post by jerome1232 on 2008-08-29
Wow, something it looks like vlc can't handle, the only thing I've found is this, [http://www.monkeysaudio.com/download.html](http://www.monkeysaudio.com/download.html) windows only so you'd have to try your luck with wine

---

### Post by Vivaldi Gloria on 2008-08-29
I deal with ape all the time. Audacious and gnome-mplayer play it without a problem.

I suggest you transform apes to flacs. Flacs are more widespread, everything can read it, and they need less cpu resources for both encoding and decoding. Even my cowon D2 can play them without a problem.

I prefer foobar2000 in wine to convert ape to flac. It's by far the best conversion tool. Actually, it's the only app which can do all of the following:

1. Open ape+cue
2. Download tags from internet.
3. Edit those tags.
4. Convert to individual flac files.
5. Do this conversion multi-threaded, that is, different tracks are encoded by different cpus at the same time.

Unfortunetely foobar2000 is closed source software.

---

### Post by NeoAndersen on 2008-08-29
Hello!!

I installed Audacious and now I am listening my .ape music without any problem!!

Thank you very much Vivaldi!!

---

### Post by Vivaldi Gloria on 2008-08-29
> **NeoAndersen said:**
> Hello!!

I installed Audacious and now I am listening my .ape music without any problem!!

Thank you very much Vivaldi!!

You're welcome.

---

### Post by logos34 on 2008-08-30
> **Vivaldi Gloria said:**
> I deal with ape all the time. Audacious and gnome-mplayer play it without a problem.

I suggest you transform apes to flacs. Flacs are more widespread, everything can read it, and they need less cpu resources for both encoding and decoding. Even my cowon D2 can play them without a problem.

I prefer foobar2000 in wine to convert ape to flac. It's by far the best conversion tool. Actually, it's the only app which can do all of the following:

1. Open ape+cue
2. Download tags from internet.
3. Edit those tags.
4. Convert to individual flac files.
5. Do this conversion multi-threaded, that is, different tracks are encoded by different cpus at the same time.

Unfortunetely foobar2000 is closed source software.

I seem to lose fast-forward / reverse capability in the resulting flacs in amarok -- the track progress slider just snaps back.  But as long as I decompress the wav and then encode to flac everything is fine.  K3b, foobar2000 (0.9.5.5), dBpoweramp, even calling mac-3.99 directly doesn't work.  Wonder why.

---

### Post by Vivaldi Gloria on 2008-08-30
> **logos34 said:**
> I seem to lose fast-forward / reverse capability in the resulting flacs in amarok -- the track progress slider just snaps back.  But as long as I decompress the wav and then encode to flac everything is fine.  K3b, foobar2000 (0.9.5.5), dBpoweramp, even calling mac-3.99 directly doesn't work.  Wonder why.

Sorry mate, I have no idea why it doesn't work for you. I have never used amarok in my life.

---

### Post by logos34 on 2008-08-30
> **Vivaldi Gloria said:**
> Sorry mate, I have no idea why it doesn't work for you. I have never used amarok in my life.

I tried different players, and it seems audacious and VLC can ff/rr, but not amarok or totem.  (I uninstalled rhythmbox so not sure about it).

So maybe it's just a fluke in certain players...it doesn't necessarily appear to be related to the flac conversion settings in K3b:

> [COLOR=Blue]flac -8 -o %f --force-raw-format --endian=big --channels=2 --sample-rate=44100 --sign=signed --bps=16 [/COLOR]-T ARTIST=%a -T TITLE=%t -T TRACKNUMBER=%n -T DATE=%y -T ALBUM=%m -

But I noticed when I convert wavs to flac from command line, even though the exact same flac version is being used, it adds 'seek points', whereas any other way (foobar, k3b, dBpoweramp, etc.) does not:

1) split and convert .ape (cue) directly to .flac with any of the above apps:

> 
$ metaflac --list 01\ -\ Symphonie\ No.6\,\ Pastorale\,\ op.68\ _\ 4.\ Gewitter.\ Sturm\:\ Allegro.flac 
METADATA block #0
  type: 0 (STREAMINFO)
  is last: false
  length: 34
  minimum blocksize: 4096 samples
  maximum blocksize: 4096 samples
  minimum framesize: 16 bytes
  maximum framesize: 12009 bytes
  sample_rate: 44100 Hz
  channels: 2
  bits-per-sample: 16
  total samples: 9756684
  MD5 signature: af3b4b1b102e8d4a8ee9bd5a7e14ce6b
METADATA block #1
  type: 4 (VORBIS_COMMENT)
  is last: false
  length: 253
  vendor string: reference libFLAC 1.2.1 20070917
  comments: 5
    comment[0]: ARTIST=Beethoven Ludwig van
    comment[1]: TITLE=Symphonie No.6, Pastorale, op.68 _ 4. Gewitter. Sturm: Allegro
    comment[2]: TRACKNUMBER=01
    comment[3]: DATE=0
    comment[4]: ALBUM=Symphonies - Orchestre Revolutionnaire et Romantique John Eliot Gardiner
METADATA block #2
  type: 1 (PADDING)
  is last: true
  length: 8192


2) split .ape (.cue) --> .wav (using above apps)

.wav --> .flac (CLI):

> $ metaflac --list 01\ -\ Symphonie\ No.6\,\ Pastorale\,\ op.68\ _\ 4.\ Gewitter.\ Sturm\:\ Allegro2.flac
METADATA block #0
  type: 0 (STREAMINFO)
  is last: false
  length: 34
  minimum blocksize: 4096 samples
  maximum blocksize: 4096 samples
  minimum framesize: 16 bytes
  maximum framesize: 12009 bytes
  sample_rate: 44100 Hz
  channels: 2
  bits-per-sample: 16
  total samples: 9756684
  MD5 signature: af3b4b1b102e8d4a8ee9bd5a7e14ce6b
METADATA block #1
  type: 3 (SEEKTABLE)
  is last: false
  length: 414
  [COLOR=Blue]seek points: 23
    point 0: sample_number=0, stream_offset=0, frame_samples=4096
    point 1: sample_number=438272, stream_offset=491169, frame_samples=4096
    point 2: sample_number=880640, stream_offset=981897, frame_samples=4096
    point 3: sample_number=1318912, stream_offset=1831282, frame_samples=4096
    point 4: sample_number=1761280, stream_offset=2954955, frame_samples=4096
    point 5: sample_number=2203648, stream_offset=3962244, frame_samples=4096
    point 6: sample_number=2641920, stream_offset=4760437, frame_samples=4096
    point 7: sample_number=3084288, stream_offset=5472521, frame_samples=4096
    point 8: sample_number=3526656, stream_offset=6282455, frame_samples=4096
    point 9: sample_number=3964928, stream_offset=6824650, frame_samples=4096
    point 10: sample_number=4407296, stream_offset=7478098, frame_samples=4096
    point 11: sample_number=4849664, stream_offset=8498847, frame_samples=4096
    point 12: sample_number=5287936, stream_offset=9570177, frame_samples=4096
    point 13: sample_number=5730304, stream_offset=10594909, frame_samples=4096
    point 14: sample_number=6172672, stream_offset=11492342, frame_samples=4096
    point 15: sample_number=6610944, stream_offset=12585418, frame_samples=4096
    point 16: sample_number=7053312, stream_offset=13669225, frame_samples=4096
    point 17: sample_number=7495680, stream_offset=14555706, frame_samples=4096
    point 18: sample_number=7933952, stream_offset=15266823, frame_samples=4096
    point 19: sample_number=8376320, stream_offset=15922456, frame_samples=4096
    point 20: sample_number=8818688, stream_offset=16515012, frame_samples=4096
    point 21: sample_number=9256960, stream_offset=17084949, frame_samples=4096
    point 22: sample_number=9699328, stream_offset=17635071, frame_samples=4096[/COLOR]
METADATA block #2
  type: 4 (VORBIS_COMMENT)
  is last: false
  length: 40
  vendor string: reference libFLAC 1.2.1 20070917
  comments: 0
METADATA block #3
  type: 1 (PADDING)
  is last: true
  length: 8192


Wish I could make sense of this.

---

### Post by Vivaldi Gloria on 2008-08-31
logos34,

I always transcode to flac using the default options of foobar2000 or sound juicer (for cds). I checked today and none of my flacs have seek points. I've never realized this until today because it doesn't create problems with my players (MOC - Music On Console & Cowon D2). They seek forward and back in little jumps but it never bothered me. 

I also checked with totem, quod libet, vlc, audacious. You need to hold the progress button and scroll it yourself in totem, ql, vlc. Otherwise either it jumps a lot or it doesn't move at all (totem). Only in audacious you can click an arbitrary point in the progress bar and the button goes there. 

I didn't check rhythmbox or amarok because I don't have them.

---

### Post by logos34 on 2008-08-31
> **Vivaldi Gloria said:**
> You need to hold the progress button and scroll it yourself in totem, ql, vlc. Otherwise either it jumps a lot or it doesn't move at all (totem). Only in audacious you can click an arbitrary point in the progress bar and the button goes there. 


yeah, I can confirm that (except for quodlibet).

Oh well, it's not a deal breaker--as I said I can just do it manually with extra step...I lose tag info but that's not a big loss as I redo everything in easytag or amarok anyway .

But amarok is my music organizer/jukebox of choice, and it's irritating that ff feature does not work properly in this case.

---

### Post by Vivaldi Gloria on 2008-08-31
> **logos34 said:**
> But amarok is my music organizer/jukebox of choice, and it's irritating that ff feature does not work properly in this case.

I feel your pain. ;)

---

### Post by misterspider on 2008-08-31
I've been having this problem for ages, most flac files misbehave in any audio player that uses xine as the engine.

---

### Post by logos34 on 2008-08-31
> **misterspider said:**
> most flac files misbehave in any audio player that uses xine as the engine.

+1

that's my experience too.  I use the xine back end for amarok (like most people), and I still have periodic problems with gapless playback on tracks ripped to flac or ogg format--just shouldn't be happening at all

---

### Post by paker on 2008-08-31
> **Vivaldi Gloria said:**
> I deal with ape all the time. Audacious and gnome-mplayer play it without a problem.

I suggest you transform apes to flacs. Flacs are more widespread, everything can read it, and they need less cpu resources for both encoding and decoding. Even my cowon D2 can play them without a problem.

I prefer foobar2000 in wine to convert ape to flac. It's by far the best conversion tool. Actually, it's the only app which can do all of the following:

1. Open ape+cue
2. Download tags from internet.
3. Edit those tags.
4. Convert to individual flac files.
5. Do this conversion multi-threaded, that is, different tracks are encoded by different cpus at the same time.

Unfortunetely foobar2000 is closed source software.

Congrats, OP, for solving your problem.

Vivaldi,
I need your help one more time. How did you install ape to foobar2k? I downloaded foo-input-monkey.zip and unzipped it to a folder. What's next?
Thanks.

---

### Post by Vivaldi Gloria on 2008-08-31
> **paker said:**
> Congrats, OP, for solving your problem.

Vivaldi,
I need your help one more time. How did you install ape to foobar2k? I downloaded foo-input-monkey.zip and unzipped it to a folder. What's next?
Thanks.

You put the dll file in foobar2000/components folder.

---

### Post by paker on 2008-09-01
That easy? Thanks. I am totally impressed by foobar running so well in wine.

---

### Post by Vivaldi Gloria on 2008-09-01
> **paker said:**
> That easy? Thanks. I am totally impressed by foobar running so well in wine.

You're welcome. It also impresses me. But it's pretty much the only non-FOSS software I use. I wish there was an equivalent one in FOSS world.


For future reference, if you ever need wma support in foobar2000 then install Windows Media Lite in wine:

[http://www.free-codecs.com/download/Windows_Media_Lite.htm](http://www.free-codecs.com/download/Windows_Media_Lite.htm)


For ogg encoding download oggenc2 from here:

[http://www.rarewares.org/ogg-oggenc.php](http://www.rarewares.org/ogg-oggenc.php)

unzip it and rename "oggenc2.exe" to "oggenc.exe" and put it in your foobar folder.


Also, ColumnsUI work OK:

[http://yuo.be/columns.php](http://yuo.be/columns.php)


Cheers.

---

### Post by paker on 2008-09-01
Thanks. I will save this thread for future wma need.

---

### Post by pokipoki08 on 2008-09-02
Try aqualung, it's available from the repos.
[http://aqualung.factorial.hu/screenshots.html](http://aqualung.factorial.hu/screenshots.html)

> # Almost all sample-based, uncompressed formats (e.g. WAV, AIFF, AU etc.) are supported. For the full list of these formats, visit the libsndfile  homepage.
# Files encoded with **FLAC** (the Free Lossless Audio Codec) are supported.
# Ogg Vorbis and Ogg Speex audio files are supported.
# MPEG Audio files are supported. This includes MPEG 1-2-2.5, Layer I-II-III encoded audio, including the infamous MPEG-1 Layer III format also known as MP3. For tracks containing the appropriate LAME headers, the MPEG encoder delay and padding is eliminated by Aqualung, resulting in truly gapless playback. Aqualung also supports VBR (variable bitrate) and UBR (unspecified bitrate) MPEG files.
# MOD audio files (MOD, S3M, XM, IT, etc.) are supported via the high quality libmodplug library.
# Musepack (a.k.a. MPEG Plus) files are supported.
# Files encoded with **Monkey's Audio Codec** are supported.
# WavPack files are supported via a native decoder.
# Numerous formats and codecs are supported via the FFmpeg project, including AC3, AAC, WMA, WavPack and the soundtrack of many video formats.

---

### Post by Halbarad on 2008-09-02
@Vivaldi Gloria: Thank you, thank you SO much for mentioning Audacious! I had lost all hope to listen to many of my musical files without having to mess around with conversions etc. -- the quality of the files would surely not increase. And now, I am listening my Dowland directly, thanks to this powerful, little and extremely elegant tool (at first sight, it is much like the old Winamp, in its aspect and functionality).
(By the way: a general question, even if a naive one: are ape and flac lossless formats? For, in this case, the conversion would not frighten me so much.)

---

### Post by Vivaldi Gloria on 2008-09-02
> **Halbarad said:**
> @Vivaldi Gloria: Thank you, 

You're welcome.

> (By the way: a general question, even if a naive one: are ape and flac lossless formats? For, in this case, the conversion would not frighten me so much.)

Yes, both are lossless. I prefer flac over ape - more widespread, open source, needs less cpu to encode & decode.

EDIT: For more on lossless formats see:

[http://wiki.hydrogenaudio.org/index.php?title=Lossless_comparison](http://wiki.hydrogenaudio.org/index.php?title=Lossless_comparison)

---

### Post by hugmenot on 2008-09-06
This is my procedure:

- Get shntools from official Ubuntu repos
- Get monkey's audio from rarewares.org

```
shnsplit -oflac -f CDImage.cue -t "%n. %t" CDImage.ape
exfalso .
```

Then get tracks from FreeDB and edit these tags for correctness. Then replaygain them with Exfalso plugin. Then rename by tags, which moves the single flacs neatly into my music folder. Finish by moving cover art over too.

---

### Post by logos34 on 2008-09-06
> **hugmenot said:**
> This is my procedure:

- Get shntools from official Ubuntu repos
- Get monkey's audio from rarewares.org

```
shnsplit -oflac -f CDImage.cue -t "%n. %t" CDImage.ape
exfalso .
```Then get tracks from FreeDB and edit these tags for correctness. Then replaygain them with Exfalso plugin. Then rename by tags, which moves the single flacs neatly into my music folder. Finish by moving cover art over too.

Yes, but I found out that just '-o flac' encodes at default '-5' level compression.  Here's how to get '--best' (what I prefer):
> 
shnsplit -o "flac flac -s -8 -o %f -" -f CDImage.cue CDImage.apeBut all this has got me wondering why on earth there isn't a way to split large .ape cdimages AND preserve the tags--FROM THE CLI.  I'd prefer a native linux, non-gui way.

shnsplit splits and converts  but doesn't preserve the tags.  (And the dev says he doesn't plan on adding that support since the focus is strictly on audio encoding).  

Scripts like ['convtoflac.sh']("http://www.gomellow.com/?p=24") (by [Jared Breeland]("http://aidanjm.wordpress.com/2007/02/04/converting-monkey%e2%80%99s-audio-ape-files-to-flac-in-ubuntu/#comment-3092")) preserve the ape tags but don't split. 

I wish someone would figure out how to combine the latter with shnsplit.

---

### Post by Vivaldi Gloria on 2008-09-06
> **hugmenot said:**
> Get monkey's audio from rarewares.org

I downloaded 

libmac2_3.99+update4+build5+shntool-0rarewares1_i386.deb
monkeys-audio_3.99+update4+build5+shntool-0rarewares1_i386.deb

from [[COLOR="Sienna"]rarewares[/COLOR]]("http://www.rarewares.org/debian/packages/unstable/")

Thanks. I wasn't able to find mac since [http://sourceforge.net/projects/mac-port/](http://sourceforge.net/projects/mac-port/) dissappeared. 

Your command worked. For some reason vlc didn't play the resulting flac files but I don't use vlc anyway. 

For the time being I'll continue using foobar2000 because it preserves tags, it's multithreaded and it's convenient to do everything in a single app. 

I wish there was a decent FOSS gui converter for gnome.

---

### Post by hugmenot on 2008-09-07
> **logos34 said:**
> Yes, but I found out that just '-o flac' encodes at default '-5' level compression.  Here's how to get '--best' (what I prefer):

Hmm. Fair enough. For me, the default is good enough.
> But all this has got me wondering why on earth there isn't a way to split large .ape cdimages AND preserve the tags--FROM THE CLI.  I'd prefer a native linux, non-gui way.
shnsplit splits and converts  but doesn't preserve the tags.  (And the dev says he doesn't plan on adding that support since the focus is strictly on audio encoding).
Well, usually the tags in the cue file are identical to what you get from FreeDB. When the CD is not available on FreeDB I have a script that converts the .cue file to a .tags file, which Exfalso can import; it's similar, only the syntax has to be rewritten.
And, I usually have to add a ton of extra tags anyway. Organisation is key, and I'm a german.

---

### Post by hugmenot on 2008-09-07
[might be interesting]("http://www.hydrogenaudio.org/forums/index.php?s=&showtopic=59183&view=findpost&p=531323")
[script here]("http://code.google.com/p/4nykey/source/browse/scripts/cueek.py")

---

### Post by paker on 2008-10-10
Vivaldi,
Another foobar2k question. How do I get flac support? When I select ape>flac, it prompts me to locate flac command.

---

### Post by Vivaldi Gloria on 2008-10-11
> **paker said:**
> Vivaldi,
Another foobar2k question. How do I get flac support? When I select ape>flac, it prompts me to locate flac command.

Download windows version of flac from [[COLOR="Sienna"]here[/COLOR]]("http://flac.sourceforge.net/") and install it with wine. Then direct foobar to flac.exe when foobar asks.

---

### Post by paker on 2008-10-11
Thanks. Though making foobar work is not straight, it's definitely worth the trouble. It does everything that I want so far.

---

### Post by Spike-X on 2008-11-16
> **Vivaldi Gloria said:**
> 
I prefer foobar2000 in wine to convert ape to flac. It's by far the best conversion tool. Actually, it's the only app which can do all of the following:

1. Open ape+cue
2. Download tags from internet.
3. Edit those tags.
4. Convert to individual flac files.
5. Do this conversion multi-threaded, that is, different tracks are encoded by different cpus at the same time.

Unfortunetely foobar2000 is closed source software.

After a lot of trial and error, I finally got this to work on Crossover. Thanks!

---

### Post by crgutierrez on 2008-11-24
foobar installed
how do i convert to flac?????

Thks

---

### Post by Spike-X on 2008-11-25
You need to install Flac for Windows ([get it here]("http://flac.sourceforge.net/download.html")) through Crossover or Wine (whichever one you'll be using to run Foobar), then tell Foobar where to find the flac codec once it's installed.

---

### Post by paker on 2008-11-26
> **crgutierrez said:**
> foobar installed
how do i convert to flac?????

ThksIf you do full install, flac is supported natively. But if you do selected install (as recommended in Hydrogenaudio), you have to add flac separately as posted above. I tried both methods and found full install easier and without a problem.

32 bit 8.04

---

### Post by jocheem67 on 2008-11-28
I tried foobar let's say a year ago with wine, didn't work nicely back then ( especially skin related )...I just tried it again a couple of days ago and am very impressed.
It's one of my few reasons to keep xp installed, but if and when I get foobar working to the fullest ( have to do more testing ), I'll be very pleased.
This thread is a helpful one rgarding the various codecs, so thenks for that.

By the way: what audio backend do you all use? I selected OSS/emulation in wine prefs. as I remember that to be the safe choice from my last attempt.

---

### Post by Spike-X on 2008-11-29
I don't use foobar as a player, just to convert and/or split when I need to.

---

### Post by paker on 2008-12-02
Vivaldi,
I have one more question. I downloaded Windows Media Lite and isntalled it under wine. Drive C > Program Files > Windows Media Lite > Backup. I found a bunch of DLL files there. Copied all of the files and pasted them in Drive C > Program Files > Foobar2000 > Components, where other DLL files are already sitting. Still Foobar does not convert wma to flac. Pop-up reads, "Could not load info (WMA support requires Windows Media runtime libraries installed)" What did I miss?
Thanks.

---

### Post by jocheem67 on 2008-12-04
I haven't tried, but my idea is that you need one or more additional *.dll's. Should be placed in the .wine/system32 folder....why , by the way, would you try to convert wma to flac??

I can confirm that ripping, tagging with freedb and file operations work. No caveats.
On top of that I've ripped a cd to mp3 with no problems. The lame.exe on a ntfs partition worked flawlessly.

This all makes foobar/wine imho better than the linux native rippers/players/encoders.

---

### Post by Corwin7 on 2008-12-09
> **logos34 said:**
> I seem to lose fast-forward / reverse capability in the resulting flacs in amarok -- the track progress slider just snaps back.  But as long as I decompress the wav and then encode to flac everything is fine.  K3b, foobar2000 (0.9.5.5), dBpoweramp, even calling mac-3.99 directly doesn't work.  Wonder why.

Amarok requires seek points in the flac file. Try comparing Amarok's limited cue file support to XMMS (with xmms-cue). On Amarok the song title changes only when it hits a seek point which is sometimes 30 seconds after the song changes. In your case it would probably never change. On XMMS the change sync is less than a second. Amarok is really a horrible player (albeit w/a pretty interface), use XMMS and this problem will only be a memory.

I think the best ape-flac converter is Convert to FLAC: [http://legroom.net/software/convtoflac](http://legroom.net/software/convtoflac)

---

