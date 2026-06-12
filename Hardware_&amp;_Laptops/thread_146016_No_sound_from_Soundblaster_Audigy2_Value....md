---
title: "No sound from Soundblaster Audigy2 Value..."
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by ubuntu-mike022465 on 2006-03-17
After mucking about with the sound setup on my desktop, which has onboard nvidia nforce2 chipset, and an Audigy2 value soundcard added (which is my primary soundcard) I when about making modifications to my setup based on this link [http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound]("http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound"), now I have no sound at all.  :confused: 
I have esd turned off, I have alsa selected in the multimedia setup, and I have my default soundcard as Audigy 2 Value [SB0400] (AlsaMixer).

I get no sound from xmms, rhythmbox, muine or any other sound apps.

Can someone give me a hand straightening this out, because I really don't want to reinstall the system all over again... mine you it might solve my problem with no being able to boot into FC4 on another hd... but that's another thread :-D

M.

---

### Post by Shampyon on 2006-03-17
I have the same card, and I'me having the same difficulties.
I tried the tute from this thread: [http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)
And got some crackly, sdistorted sound.
I thought using the tute mentioned in your post would help, but I lost sound entirely. I have no idea how to backtrack and undo the changes I've made, either.

---

### Post by ubuntu-mike022465 on 2006-03-18
Bump.

---

### Post by ubuntu-mike022465 on 2006-03-18
Here's my esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=50
# default options are used in spawned and non-spawned mode
default_options=

Here's my asound.conf

pcm.card1 {
type hw
card 1
}

pcm.!default {
type plug
slave.pcm "output"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048	#1024
buffer_size 32768	#4096
			#periods 128
rate 48000		#44100
}
bindings {
0 0
1 1
}
}

Here's my ~/.asoundrc

### BEGIN set-default-soundcard
# If the "### BEGIN..." and "### END..." comments are intact, then you
# can change your default soundcard with "set-default-soundcard(1)."
# Remove these comments if you want to maintain a custom configuration
# that should not be changed automatically.

# Default soundcard
defaults.pcm.card 1

pcm.!default {
 type plug
 slave.pcm "dmix"
}

### END set-default-soundcard

And lastly, here's my modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

powernow_k8
cpufreq_userspace
cpufreq_conservative
cpufreq_powersave
cpufreq_stats
cpufreq_ondemand
cpufreq_stats


evdev

nvidia-agp
nvidia

tun
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq


Any thoughts would be greatly appreciated.

M.

---

### Post by ubuntu-mike022465 on 2006-03-19
Bump.

---

### Post by ubuntu-mike022465 on 2006-03-20
Bumpity Bump Bump.

---

### Post by ubuntu-mike022465 on 2006-03-20
Helllloooooooooooo :D

---

### Post by Shampyon on 2006-03-20
I just backed up all my files and did a whole fresh install. Installed my ATI drivers, ran update. Once that was all done, I re-ran Automatix, choosing the Gnome Sound fix. Just like I did last time, but with one exception:
The first timew around, I tried a bunch of the manual fixes I found on these boards and on wikis *before* I installed and ran Automatix. This time, i didn't try to mess with anything, just installed the Automatix sound fix.

So, yay for me.

---

### Post by exkalibur on 2006-03-29
Open the volume control and selected Edit | Preferences and select Audigy Analog/Digital Output Jack. Go back to mixer and check the box on the switch tab...That  did it for me...

---

