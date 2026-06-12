---
title: "ALSA support"
date: 2005-01-06
forum: Hardware &amp; Laptops
---

### Post by freemanda on 2005-01-06
First, I would like to say this is a great forum which supports a great distro. Being new to linux  I was really scared at first coming from windows but things are going good so far.  I am starting to realise that the command line is your friend and it gives you a sense of accomplishment once you use it. I played with Mandrake for about a month and it is good also but there seems to be something different about ubuntu that makes me want to stick with it. The only problem so far is the sound. I have two linux boxes and one has full sound with all the programs and the other only has partial sound. When you first login the drums are there but there is no soothing sound or system sound once you open and close folders. XMMS,XINE,RYTHMBOX all work with sound but Gaim sounds are none exsistent. I have noticed that that in the volume control there are full controls for asla but only one slide, which is the mic, for oss. the sound card is intergrated on an intel 810 chipset/ dell optiplex 260. Any help on this would be greatly appreciated.

                                 thnx
      
                                 freemanda

---

### Post by freemanda on 2005-01-07
Any help would be appreciated  8)

---

### Post by hardcandy on 2005-01-07
Under Computer-->Desktop Preferences-->Sound, is the Start Sound Server box checked?
In the mixer, does it show the name of the sound card module at the top?

---

### Post by freemanda on 2005-01-07
Yes the sound server is enabled at startup but there is no particular name at the top of the window. It just simply says "sound preferences"

---

### Post by freemanda on 2005-01-08
sometimes i just don't understand , but that is the beauty of linux . the gaim sound has returned but the system sound isn't there. i haven't done anything with te sound preferences but it came back. now i have to figure out what is up with the other sounds

---

### Post by telmo on 2005-01-08
YEAH! What a beauty...  :-({|=

---

### Post by freemanda on 2005-01-11
anymore help would be appreciated

---

### Post by LongTooth on 2005-02-07
I'l like to revive this post. I've had this same 'partial sound' problem for about a week. I've racked my brain trying to figure what I did to cause it. I just don't know. Here's what I've got...or don't have:

Like the original poster, the drums at the logon screen but no music after that (on system start-up). No system sounds as when closing/opening apps. No GIAM sound. But oddly enough XMMS will play sounds (internet radio) with some stations. With others it's garbled. The CD plays with no problems. Realplayer is another no sound. I see that it connected and buffering but no sound.

Partial sounds. I've checked all I know. Where do I go from here? Any assistance will be greatly appreciated. Thanks.

---

### Post by froust on 2005-02-07
I'm having some sound issues too. I get all sounds in ESD (OSS won't work), but when I try to go with alsa (Desktop -> Preferences -> Multimedia Systems Selector), I get a "failure to construct test pipeline" error... I'm using the onboard sound on an Asus K8N-E Deluxe.

---

### Post by LongTooth on 2005-02-07
Help anyone? Please? Pretty please. Pretty please with sugar on top?

---

### Post by dtudosie on 2005-02-19
Hi,

This is just another post for complaining about alsa in ubuntu....
Ofcourse I have the same error for "failed to construct test pipeline for alsa"...
This (from what I understand) is related to the alsa plugin for gstreamer which is not quite supported...

But I noticed other issue: aplay itself won't play correct through a custom defined device that does a simple virtual surround: (note that I use via82xx)
if I play a .wav file through this deivce only the front speakers are used...
aplay -D VirtualSurround <some wav file>

Did anyone managed to get alsa work correctly in ubuntu ?

VirtualSurround {
        type plug
        slave {
                pcm {
                        type hw
                        card 0
                        device 1
                }
                channels 6
        }
        ttable.0.0 1
        ttable.0.2 1
        ttable.0.4 0.5
        ttable.0.5 0.5
        ttable.1.1 1
        ttable.1.3 1
        ttable.1.4 0.5
        ttable.1.5 0.5
}

---

### Post by dtudosie on 2005-02-19
Hi,

I just solved the virtual surround issue: it was related to the alsamixer options ("line in as surround" and "mic as center" were note selected and some channels were muted)

Just installed gnome-alsamixer and set them right... now it works..

However, there is the interaction between alsa and gstreamer that still has issues...
and I cannot use rhythmbox...


Regards,
Daniel

---

### Post by hkctr on 2005-02-22
Try this: select Custom as the Default Sink in System->Preferences->Multimedia Systems Selector and input [alsasink device=hw:0] as the Pipeline. This worked for me YMMV.

---

