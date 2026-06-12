---
title: "icecast"
date: 2008-07-17
forum: General Help
---

### Post by wgato on 2008-07-17
i am struggling to figure out how to send a stream to icecast.  ideally, i'd like to do it from rhythmbox.  i've been googling around but am pretty lost.  anyone have any suggestions

---

### Post by Darkade on 2008-07-18
I've setup icecast before, and I also wanted to do it through rhythmbox but couldn't so I installed ices, Ices is an app that manages icecast streams, check it out
[http://www.icecast.org/ices.php](http://www.icecast.org/ices.php)

There's a little app called internet DJ console, it never worked really fine for me, but that could be for the limet resources of my laptop
check it [here]("http://www.onlymeok.nildram.co.uk/"), and you can install it from the repositories.

finally, [this]("http://www.yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html") was the way I did most of my icecast setup. hope it helps:D:D

---

### Post by wgato on 2008-07-19
Thanks for the suggestions.

i've got the icecast server up and running.  (i think.  i'm able to see [http://localhost:8000](http://localhost:8000) in the browser.)

I looked at iceS briefly before but I dont understand what it does and there doesn't seem to be any documentation.  Does it sit between the music player and the icecast server? Or is it the player itself? i'm kinda confused about its purpose and workings.
if iceS doesnt play the music and you werent play to using rhythmbox or the dj console (which looks like a really interesting program, but maybe not what i'm looking for atm), what is the music player you use?

---

### Post by Darkade on 2008-07-19
For my icecast was more of an experiment that a serious proyect, so I really never used a player (even though if I'm able to configure it for a player I'll be glad to take the proyect again hehe)
Ok about ices, yep there's not much documentation but [this]("http://www.icecast.org/docs/ices-2.0.0/") and it ain't that good, but it helps. Anyway ices is not a player, nor does it sits between a player and icecast. It's a streamer. I'll try to clarify: It encodes what you give to it and then gives it to icecast. So if you give a list of ogg files it icecast will stream and ogg file, that you will hear through localhost:8000 or ices can capture the input of your soundcard so you may stream your voice.

you can check some basic configs [here]("http://www.icecast.org/docs/ices-2.0.0/inputs.html") and you can start ices with ```
sudo ices routetoconfigfile
``` where configfile y the file you created with one of the configs from that page.

Well I said that I wanted to use a player too but I never was able, however I think it was due to limitations of my soundcard. So I'll give you my idea and PLEASE let me know if it worked for you.

ices can capture your soundcard through this module
> 	<module>alsa</module>
	<param name="rate">44100</param>
	<param name="channels">2</param>
	<param name="device">plughw:0,0</param>
	<param name="periods">2</param>
	<param name="buffer-time">500</param>
	<param name="metadata">1</param>
	<param name="metadatafilename">/home/ices/metadata</param>


this is an alsa device > <param name="device">plughw:0,0</param> the first 0 is the number of soundcard and the send 0 is the number of device of that soundcard. In my soundcard the input device and the output device are the same, the 0 device, but I think that if you can separate them or that if in your soundcard they are not mixed you MAY be able to capture the output of your soundcard instead of the input of you soundcard. Know what that means? That means that you could stream whatever you are listening in your PC, even voice if you un-mute your microphone. 

This are two threads I made back when I tried to setup this, about December or January. I don't think they will help much but they may

[http://ubuntuforums.org/showthread.php?t=650036](http://ubuntuforums.org/showthread.php?t=650036)
[http://ubuntuforums.org/showthread.php?t=651627](http://ubuntuforums.org/showthread.php?t=651627)

BTW you will find this command useful
```
cat /proc/asound/devices 
```
it lists your ALSA devices, if you have something like this
```
 16: [ 0- 0]: digital audio playback
 24: [ 0- 1]: digital audio capture

```then you are ready to go

just set
> <param name="device">plughw:0,1</param> or 2 or 3 or 0 or anything that is your playback device
but if you have something like this
```
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture

```
which is what I have you may need to do some tweeking, and that's where I couldn't do anything.

---

### Post by wgato on 2008-07-19
I do appreciate the help but unfortunately am still not understanding at all...
if ices takes what you give it and sends it to icecast
how do you give it things?

i would like to give it the music being played by rhythmbox. what should i use to give it things?

i used to stream under windows and used winamp to play music and the shoutcast plugin to send it.
what would be the ubuntu equalivant?

---

### Post by Darkade on 2008-07-19
First, There **are well supported ways to stream shoutcast in linux**.
Second, icecast is installed in your machine, if you want to stream to another server shoutcast is the choice


Ok probably I'm being too technical. I'll do my best to explain

To see some basic configurations of ices try this page [http://www.icecast.org/docs/ices-2.0.0/inputs.html](http://www.icecast.org/docs/ices-2.0.0/inputs.html)

Ok. now I'll try to explain, you give ices a source to stream via a config file, that you can create anywhere. The important part is what the file contains for example:

**Streaming your stdinpcm, ie your microphone**

> 
<module>stdinpcm</module>
<param name="rate">44100</param>
<param name="channels">2</param>
<param name="metadata">1</param>
<param name="metadatafilename">/home/ices/metadata</param>


Will stream you microphone, see that > <module>stdinpcm</module> it means that the configuration file will take stdinpcm, that is to say your microphone
> <param name="rate">44100</param>
is the coding rate, the lower the faster, and less resources it will take
> <param name="channels">2</param>
this means that you'll stream in stereo.
The last two lines are metadata, headers for the stream, nothing really important.

**Streaming a list of ogg files** (ices 2.0 only supports ogg format)
> 
<param name="type">basic</param>
<param name="file">/path/to/playlist</param>
<param name="random">0</param>
<param name="once">0</param>
<param name="restart-after-reread">1</param>

this config file will take the ogg files in a list and stream them, in the order the list is, unless stated otherwise
> <param name="file">/path/to/playlist</param>
this is the route to your playlist file for example /home/$USER/icesplaylist
> <param name="random">0</param>
<param name="once">0</param>
<param name="restart-after-reread">1</param> I think these three explain for themselves

Now, as far as I know there is no way, yet, to stream to icecast directly from rhythmbox but that's where this module gets in.

> 
<module>alsa</module>
<param name="rate">44100</param>
<param name="channels">2</param>
<param name="device">plughw:0,0</param>
<param name="periods">2</param>
<param name="buffer-time">500</param>
<param name="metadata">1</param>
<param name="metadatafilename">/home/ices/metadata</param>


This module captures your soundcard. Soundcard has basically 2 devices: playback and capture. Playback is anything that "is coming out of your speakers" and capture is your microphone.

Ok now, If you can stream what is coming out of your speakers it would be a way to stream what you are hearing in rhythmbox right? so that is *my* solution, to capture the output and stream it. now **how?**

This line > <param name="device">plughw:0,0</param>
and more accurate this plughw:0,0 is an ALSA device, and for ices what it means is that it will take the device 0 from the soundcard 0. Whatever is the 0 device, which can be your playback device or your capture device.

of course we want ices to capture playback so here is where ```
cat /proc/asound/devices
``` enters. That command lists your alsa devices in something like this
```

ivan@icarus-laptop:~$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer

```
Where the first 0 is the number of soundcard and the second 0 is the number of device. (For some reason, that for almost 8 months I haven't understood, my devices are all mixed in the 0 device) If your digital audio playback looks something like this
```

 16: [ 0- **2**]: digital audio playback

```
then all you have to do is set that in the config file
> <param name="device">plughw:**0,2<**/param>
and run ices

Here is my configfile for ices

[HTML]
<?xml version="1.0"?>
<ices>
    <!-- run in background -->
    <background>1</background>
    <!-- where logs, etc go. -->
    <logpath>/var/log/ices</logpath>
    <logfile>ices.log</logfile>
    <!-- 1=error,2=warn,3=info,4=debug -->
    <loglevel>4</loglevel>
    <!-- set this to 1 to log to the console instead of to the file above -->
    <consolelog>0</consolelog>

    <!-- optional filename to write process id to -->
    <!-- <pidfile>/home/ices/ices.pid</pidfile> -->

    <stream>
        <!-- metadata used for stream listing (not currently used) -->
        <metadata>
            <name>Arcade's lair Radio</name>
            <genre>Varios</genre>
            <description>La Radio de Arcade's Lair, un proyecto para desarrollar internet de usuarios con plataformas libres.</description>
        </metadata>

        <!-- input module

            The module used here is the playlist module - it has
            'submodules' for different types of playlist. There are
            two currently implemented, 'basic', which is a simple
            file-based playlist, and 'script' which invokes a command
            to returns a filename to start playing. -->

 
[B]
<input>
	<module>stdinpcm</module>
        <param name="rate">44100</param>
        <param name="channels">2</param>
</input>   [/B]

                <!-- Stream instance
            You may have one or more instances here. This allows you to
            send the same input data to one or more servers (or to different
            mountpoints on the same server). Each of them can have different
            parameters. This is primarily useful for a) relaying to multiple
            independent servers, and b) encoding/reencoding to multiple
            bitrates.
            If one instance fails (for example, the associated server goes
            down, etc), the others will continue to function correctly.
            This example defines two instances as two mountpoints on the
            same server.  -->
        <instance>
            <!-- Server details:
                You define hostname and port for the server here, along with
                the source password and mountpoint.  -->
            <hostname>localhost</hostname>
            <port>8000</port>
            <password></password>
            <mount>/arcadelair.ogg</mount>

            <!-- Reconnect parameters:
                When something goes wrong (e.g. the server crashes, or the
                network drops) and ices disconnects from the server, these
                control how often it tries to reconnect, and how many times
                it tries to reconnect. Delay is in seconds.
                If you set reconnectattempts to -1, it will continue
                indefinately. Suggest setting reconnectdelay to a large value
                if you do this.
            -->
            <reconnectdelay>15</reconnectdelay>
            <reconnectattempts>-1</reconnectattempts>

            <!-- maxqueuelength:
                This describes how long the internal data queues may be. This
                basically lets you control how much data gets buffered before
                ices decides it can't send to the server fast enough, and
                either shuts down or flushes the queue (dropping the data)
                and continues.
                For advanced users only.
            -->
            <maxqueuelength>80</maxqueuelength>

            <!-- Live encoding/reencoding:
                Currrently, the parameters given here for encoding MUST
                match the input data for channels and sample rate. That
                restriction will be relaxed in the future.
            -->
            <encode>
                <nominal-bitrate>64000</nominal-bitrate> <!-- bps. e.g. 64000 for 64 kbps -->
                <samplerate>44100</samplerate>
                <channels>2</channels>
            </encode>


        </instance>

        </stream>
</ices>
[/HTML]

in the area where the bold text is you may enter another input like the ones I explain above or some of this address
[http://www.icecast.org/docs/ices-2.0.0/inputs.html](http://www.icecast.org/docs/ices-2.0.0/inputs.html)

---

### Post by wgato on 2008-07-19
First, There are well supported ways to stream shoutcast in linux.

so there are others ways to do this that have instrutions?  what are they?  do they work with peercast?
i am under the impression that because i want to use peercast, i have to use icecast.  it would be excellent if this was not true since i do not understand these programs at all and it is frustrusting considering i know it takes 10 minutes or less in OSes that i am more familiar with.

you give ices a source to stream via a config file, that you can create anywhere. 

so there is a text file that tells ices what to stream? where do you put it? i dont want to stream my microphone or everything coming out of my soundcard or ogg files. just my music.
would i have to type up a list of all my mp3s and make that the config file and then not be able to listen?  i have an old laptop i could use to listen to the stream if the server actually doing the streaming is unable to play because of ices.

---

### Post by Darkade on 2008-07-19
For broadcasting via Shoutcast click [here]("http://www.shoutcast.com/support/docs/docs.phtml?filenumber=20&language=english&layout=normal&prevlayout=normal")
> you give ices a source to stream via a config file, that you can create anywhere. Yes you may create the file anywhere.
> Would i have to type up a list of all my mp3s and make that the config file and then not be able to listen?
Yes you can stream MP3 but you need ices0, available [here]("http://www.icecast.org/ices.php") I really don't know how to configure Ices0. The problem with ices2 is that it can only stream in ogg

For streaming with PeerCast Try installing Geekast
> 
 Geekast
GNOME interface to peercast - binaries 
Geekast is an alternative to the Web interface. Currently, it can perform audio (Ogg and MP3) or video (OGM) streaming through an external player like totem, or an internal player based on the Gstreamer multimedia framework. In the future, it should be possible to encode a Webcam or any input stream over the peercast network.
This package provides binaries for running geekast.

This application is provided by the Ubuntu community.


---

### Post by Darkade on 2008-07-19
In fact I'm gonna try myself geekast LOL

EDIT: Nope... I think it doesn't do what you want. try it out though

---

### Post by wgato on 2008-07-25
between your help and this site:
[http://www.howtoforge.com/linux_webradio_with_icecast2_ices2_p2](http://www.howtoforge.com/linux_webradio_with_icecast2_ices2_p2)
i seem to have a stream playing from one computer to another.  but there is no sound, its a stream of silence.

my audio is all through 0, like yours.

 cat /proc/asound/devices

  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer


so my ices file contains:

     <input>
            <module>alsa</module>
            <param name="rate">44100</param>
            <param name="channels">2</param>
            <param name="device">hw:0,0</param>
            <!-- Read metadata (from stdin by default, or -->
            <!-- filename defined below (if the latter, only on SIGUSR1) -->
            <param name="metadata">1</param>
            <param name="metadatafilename">test</param>
        </input>



i am reading reakteks site but i cant tell for sure if my soundcard, realtek662, will be able to do this.

---

### Post by whitethorn on 2008-07-25
I don't really understand why you want or have to use rhythmbox, there are some music players out there that support streaming to an icecast server.  You could try using mpd.  Here's a Howto to install MPD with Icecast on a Fedora 6, but the interesting stuff is what progs you need and the configuration so it shouldn't be all that different.  Instead of yum use sudo apt-get install ..  If you don't want to install the web interface for MPD you can always just ssh into your computer and change the playlist (if you have a client installed which runs in the terminal I suggest trying out ncmpc).

[http://news.softpedia.com/news/Streaming-Audio-Using-MPD-and-Icecast-52181.shtml](http://news.softpedia.com/news/Streaming-Audio-Using-MPD-and-Icecast-52181.shtml)

MPD is a Music Playr Daemon, you need clients to tell the player what to play, for example: the web interface explained in the howto, or from the console, mpc / ncmpc  or a really nice Gtk program Sonata. (the clients are all available through synaptip)

---

### Post by Darkade on 2008-07-25
Well with that config file and your ALSA device you should be able to stream from your microphone, I know it's not what you want but that's as far as I got with Ices :(:( I'm looking at MPD right now, I can't say much about it, yet.
Hehe, you know I've regained the interest over this project, I hope we can solve it ;):D

---

### Post by wgato on 2008-07-26
i looked at mpd when i first got started on this project.  i installed sonota as part of that but didnt understand either. i got a few songs to play from the command line with mpc before it stopped working but sontona has no play button and seemed to be lacking in options.  i'll go back and take another look though since i've got all these things installed. 

i also tried vlc which didnt have the options its docs said it had for streaming unless i recompiled for rebuilt or something the whole program.  i tried but it was over my head.

for various reasons, i dont want to install a webserver and i'd need one for pitchfork. so i went back to rhythmbox since it was the only ubuntu app i could get to actually play music at all and it has many of the options in a player i am looking for.

mpd isnt really clear about what it does.  i've read its site and wikipedia enty but it seems analagous to ices, something that sits between the 2 things you actually need (the thing playing the music and icecast).  i havent figured out what ices does either but aparently i got it working enough for icecast to stream silence. 

if i was using mpd, would i still need ices?

what are some other players that work with icecast?  i saw the list on the icecast site but most of those are obsolete.

---

### Post by produnis on 2010-02-07
> **Darkade said:**
> 
```
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture

```

Same is my hardware. How I solved it:

At the rear of my PC, I put a cable (which came with my monitor) from "Line Out" to "Mic".

So, the output signal is directly sent to my microphone-line...

Now it works...

ugly hack, but it works!

---

### Post by charles_shipp on 2010-05-02
i tink icecast has to be on

---

