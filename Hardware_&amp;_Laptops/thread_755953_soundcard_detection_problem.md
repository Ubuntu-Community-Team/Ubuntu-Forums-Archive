---
title: "soundcard detection problem?"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by gab_707 on 2008-04-15
Hi all,
I recently installed Ubuntu studio and i'm trying to get my m-audio fast track pro to work with Ardour/Jack. I'm usin a Dell precision M65.
My problem seems to be that Jack only detects the midi channels but not the audio ones. So on Ardour i can't select the fast track's audio channels, and in Jack's connections menu all i get is the alsa clients.
Now when i run asoundconf it indicates that that both sound cards(fast track and internal) are available but there's no way to select the m-audio with alsamixer -c. now the best thing is /etc/asound.names is empty and /var/lib/alsa/asound.state has a whole list of controls for the internal intel soundcard whereas the list for the fast track is empty:
state.Pro {
	control {
	}
}
Am i just doin a silly newbie mistake or is there summin wrong? If so how could i fix it?
On the System>preferences>sound menu the test sounds work on the fast track.
Oh and the card works fine on windows with asio drivers.
Any help would be incredibly appreciated.

Gab

---

### Post by gab_707 on 2008-04-16
I finally found the problem:
All i needed to do was load the kernel module for the card:
modprobe snd-usb-audio

---

