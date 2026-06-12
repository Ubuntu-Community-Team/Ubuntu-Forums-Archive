---
title: "Sound Mixing on external sound card"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by jeremija on 2007-06-03
Hello!
I couldn't find the solution to my problem, I am sorry if this has been discussed before.
I have a laptop with two sound cards, one is the Intel's built-in soundcard, and the other is a USB Creative Labs Sound Blaster MP3+.  I have managed to set the MP3 card default by typing this line in the terminal: 
```
sudo asoundconf set-default-card MP3
```

(this is the only thing that i have done to make programs like Amarok use the external card, rather than the internal one.)

But i have one problem:
Sound mixing doesn't work on SB MP3+. I can hear only one stream at the time. This doesn't happen when I use the internal sound card.

My question is this: Why can I mix more sound streams on the internal card, and play only one stream at the time on the external card?

Thanks!

---

### Post by crimsun on 2007-06-03
> **jeremija said:**
> Why can I mix more sound streams on the internal card, and play only one stream at the time on the external card?!

This is the case because the usb-audio alsa-lib configuration does not have dmix enabled by default.  See LP #104130 for a workaround.

---

### Post by norberto on 2007-06-04
Ok, two problems on the same step. First make the MP3+ the default card (select it as default via sound config). Then create a new alsa mixer for that card.

# create a asound.conf file in /etc folder
sudo gedit /etc/asound.conf

# Paste the following text

# /etc/asound.conf
########################################################################

pcm.playbackcard {
	type			hw
	card			default # the selected card
}

ctl.playbackcard {
	type			hw
	card			default # the selected card
}

pcm.mymixer {
	type			dmix
	ipc_key			1024	# must be unique for all dmix plugins!

	# ipc_key_add_uid	false	# Let multiple users share.
	# ipc_perm		0666	# IPC permissions for multi-user
					# sharing (octal, default 0600)
	slave {
		pcm		playbackcard
		channels	2
		periods		3
		period_time	0
		period_size	1024
		buffer_size	8192
		rate		48000
	}
 
	bindings {
		0		0
		1		1
	}
}

pcm.!default {
	type			plug
	slave.pcm		mymixer # my new software mixer
}

ctl.!default {
	type			plug
	slave.pcm		mymixer
}

########################################################################

# close and save the file
# and restart alsa

sudo /etc/init.d/alsa-utils restart

---

### Post by jeremija on 2007-06-04
thank you for your replies!

**@crimsun**
 i found the bug on google: [https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/104130](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/104130) and i don't have a USB-Audio.conf file in /usr/share/alsa/cards so i don't know which file to replace

**@norberto**
i did as you wrote, i made the mp3+ the default card in system>preferences>sound: Default mixer tracks device (other combo boxes in that window are set on ALSA), made the /etc/asound.conf and pasted the text, but i had problems:
Amarok wouldn't play music on MP3+, just on internal card, and I couldn't select ALSA in Amarok audio settings (it would only play on autodetect, i didn't try other options) because i got the message: "xine can't initialize audio drivers" or something like that...
VLC played on internal soundcard when default device is selected, when I select mp3+ it plays...
Totem Movie Player signals error on start: "Could not open resource for writing" and Rhytmbox won't play audio files.

And of course, sound mixing still doesn't work :(

When I delete the /etc/asound.conf file and restart ALSA everything works, except the sound mixing

Help :)

---

