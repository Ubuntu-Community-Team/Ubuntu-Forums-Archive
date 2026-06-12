---
title: "Everything lags (sound, mouse, graphics) every now and then"
date: 2008-10-29
forum: Hardware
---

### Post by Izek on 2008-10-29
When using compiz-fusion sometimes, the effects will lag. That's not all, the sound will also lag at times whether or not I am using an effect (IE: just scrolling a webpage may cayse a systemwide lag.)

Is there any way to fix this? It's annoying when I have sound playing and everything lags (including the mouse.)

---

### Post by Kobalt on 2008-10-29
What grapchics card do you have? This problem could come from its driver.

---

### Post by Izek on 2008-10-29
> **Kobalt said:**
> What grapchics card do you have? This problem could come from its driver.

ATI Radeon HD 3200 with 256 MB Graphics RAM, NOT compatible with ATI Overdrive.

I used the driver found in the Synaptics Package Manager (xorg-driver-fglrx), since I can't install with any of the ATI Catalyst drivers from their website at the moment.

---

### Post by JMorg on 2008-10-29
Do you have any processes running in the background that are sucking up a lot of your system resources. Generally system-wide lag is caused from a spike in processing, essentially due to a process bottle-necking other processes currently running. 

```

In terminal run "top"

```

Monitor the system usage and see when a certain process spikes  to around 40-50% CPU. If the process is something that you don't know about feel free to post it and someone can tell you what it entails. If it is a process that you know isn't necessary and you're comfortable ending it then just use the kill command and drop the process to see if that resolves the system latency.

```

kill -9 PID

```

PID = Process ID

I hope this helps you out!

---

### Post by Izek on 2008-10-29
Firefox seems to be the one causing the issue.

When every I scroll something in firefox, xorg gets pushed all the way up to 77 CPU or more, and firefox goes up to 20 CPU. (opera, the web browser, does a similar thing.)

This may be due to compiz in the end.

---

### Post by JMorg on 2008-10-29
> **Izek said:**
> Firefox seems to be the one causing the issue.

When every I scroll something in firefox, xorg gets pushed all the way up to 77 CPU or more, and firefox goes up to 20 CPU. (opera, the web browser, does a similar thing.)

This may be due to compiz in the end.


Both "Pulse Audio" and "Totem" are taking up a decent chunk as well. Do you need both of those programs running at the same time constantly? I know you may be listening to music, but by only running one instance of an audio player you could lessen some CPU usage. But compiz very well may be the issue in the end, yes. Have you turned off 3D desktop and all of that from within compiz-config?

---

### Post by Izek on 2008-10-29
And how do I turn all that off?

pulseaudio and totem I believe need to both run in my case (Having HD Audio is a real pain, and gives unwanted static when idle.)

unless I can turn off pulseaudio somehow without quitting totem while running an MP3. (I loop MP3s over and over again for many an hour.)

By the way, "VideoOverlay" does not affect current session.

---

### Post by JMorg on 2008-10-30
Well to turn off totem and pulseaudio use the command 
```
kill -9 PID
```

The PID = Process ID and to find the process of ID of a certain item use
```
ps
```

If you don't want to use terminal to end the process go to the Administration tab and select System Monitor and kill the programs manually in there!

I would recommend using, I'm on a separate PC right now so the program name might be off, but I think it is called "Rhythmbox." It is what I have been using for a while and I constantly loop music as well :). Let me know if the new program fixes your issue.

---

### Post by Izek on 2008-10-30
Is there a way to turn off playlists in Rhythmbox? Because, I don't want to add files to a playlist, I want to overwrite the playlist every time I open a file so that only one music is on the playlist at any given time.

By the way, killing pulseaudio crashes totem.

---

### Post by Izek on 2008-10-30
I installed Xubuntu, but it does the exact same thing (with compiz installed). *sighs* Guess I really do have to wait for a new driver and see if it works. But that may take forever at this rate. I should have never bought this computer, and gone with my intuition on a computer with NVIDIA. Oh, I'm so dumb.

In fact, it seems to lag worse on Xubuntu. o_O Though it's not without the lags from Ubuntu.

Lags even occur when simply loading a page, or when DOM events trigger.

---

### Post by E4tH on 2008-10-31
I have the same exact video card and I too have the same problem. Everything looks wasted out and when I try to play a video it flickers.

---

### Post by Izek on 2008-10-31
> **E4tH said:**
> I have the same exact video card and I too have the same problem. Everything looks wasted out and when I try to play a video it flickers.

It won't flicker if you disable compiz though, I believe. It also may be dependant on which codec you used. Either from the X/ubuntu restricted extras (which I use) or from the codec search from in totem.

Check this out too: _[Click Here](http://forum.compiz-fusion.org/showthread.php?t=10199)_

I hope these things are resolved in the 8.11 Catalyst (doubtful.)

---

### Post by Izek on 2008-11-10
>> Delete Post - Will Reply Later <<

---

### Post by Izek on 2008-11-11
So I reported this as a bug, you can see its status here:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/296497](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/296497)

---

### Post by Izek on 2008-11-14
This still happens even with the drivers from ati.com (Catalyst 8.11) in intrepid, but not hardy.

---

