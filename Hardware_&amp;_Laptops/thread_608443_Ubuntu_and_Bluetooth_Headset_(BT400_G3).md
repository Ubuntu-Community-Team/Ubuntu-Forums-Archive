---
title: "Ubuntu and Bluetooth Headset (BT400 G3)"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by endura29 on 2007-11-10
Hello,

I'm attempting to get my BT400 G3 running using Gutsy Gibbon.

Here is what I try:


[Screenie #0:]("http://soldierreturn.org/Screenshot-0.png")
~ I plug in my USB bluetooth adapter.. it blinkies.
~ I turn on my BT400 G3, it blinkies. Then I press a button and it pairs.
~ Ubuntu finds my device via the upper right corner.
~ Your program doesn't find it... any ideas?

[Screenie #1]("http://soldierreturn.org/Screenshot-1.png") & [2:]("http://soldierreturn.org/Screenshot-2.png")
~ Enter Passkey: 0000...
~ Try to refresh devices on gbtsco but no good (oh and I'm running gbtsco as root)

[Screenie #3:]("http://soldierreturn.org/Screenshot-3.png")
~ Ubuntu verifies, gbtsco still doesn't see it, I press Check Devices again...
~ gbtsco still doesn't find it.

[Screenie #4:]("http://soldierreturn.org/Screenshot-4.png")
~ Ubuntu says "hey this is a headset"
~ I say sure is w00t!

[Screenie #5:]("http://soldierreturn.org/Screenshot-5.png")
~ I go into sound preferences... ooh noes! its not there!
~ It seems you can't take a screenie when holding down a menu option... shoulda used the Gimp, etc.

Now I've tried many of the terminal commands that the other threads:
[http://ubuntuforums.org/showthread.php?t=48889](http://ubuntuforums.org/showthread.php?t=48889)
[http://ubuntuforums.org/showthread.php?t=35105](http://ubuntuforums.org/showthread.php?t=35105)
[http://ubuntuforums.org/showthread.php?t=52296](http://ubuntuforums.org/showthread.php?t=52296)

and I'm not sure what info they give, or honestly how to use it.

```
 sudo hciconfig hci0 revisionhci0:   
        Type: USB
        BD Address: 00:0A:3A:55:7E:22 ACL MTU: 192:8 SCO MTU: 64:8
        HCI 16.4
        Chip version: BlueCore02-External
        Max key size: 56 bit
        SCO mapping:  HCI

```


Also, the directions here: [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html) don't seem to work either.

I am running Ubuntu 7.10 on a Live CD on a Sony Vaio. I've also tried on a Dell 5150 with Gutsy installed, same thing.

Anyone have any ideas? Much appreciated!

---

### Post by dodona on 2007-11-12
It appears gnome-bluetooth needs to depend on gnome-vfs-obexftp. Installing that fixed the initial error.
[https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/138356](https://bugs.launchpad.net/ubuntu/+source/bluez-gnome/+bug/138356)

---

### Post by endura29 on 2008-01-13
Ok I made a little bit of progress.

1) I tried the above and it seems a no go. No change.

2) I also wrote the authors of gbtsco and got this response (thanks Stephane!): 
"
It's certainly a problem with python-bluetooth or something locking the
bluetooth scanning feature.

You may also try loading your BT headset by hand :

sudo rmmod snd-bt-sco
sudo modprobe snd-bt-sco
btsco -rv XX:XX:XX:XX:XX:XX
"

I tried that a few times and had to try:
sudo rmmod sun_bt_sco
sudo modprobe snd_bt_sco

and now the btsco -rv command gives me the following:
~~

btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 1 connected
Using interface hci0
speaker volume: 12 mic volume: 0
i/o needed: connecting sco...
connected SCO channel
Done setting sco fd
recieved AT+VGS=15
Sending up speaker change 15
speaker volume: 15 mic volume: 1
driver is not in use
disconnected SCO channel

~~

SO! 

Then I used alacarte to add the Multimedia Systems Selector to Preferences and in there I FINALLY! get an option for Device: BT SCO PCM

I press Test and I get this: 
"Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

SO!
I turn off my MP3s and try again (just in case) but no go.

SO! (its 4am and I'm amused writing this all)
I search for that error and get these posts:
[http://ubuntuforums.org/showthread.php?t=330069](http://ubuntuforums.org/showthread.php?t=330069)
[http://ubuntuforums.org/showthread.php?t=149315](http://ubuntuforums.org/showthread.php?t=149315)

I tried the command (from the second one):
gst-launch-0.10 alsasrc ! alsasink

which gives me:

Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstAudioSrcClock

Then gstreamer-properties crashes when I press Test again.

Any more ideas?

---

