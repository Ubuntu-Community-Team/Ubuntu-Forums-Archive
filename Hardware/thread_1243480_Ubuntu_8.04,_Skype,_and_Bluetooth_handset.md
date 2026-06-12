---
title: "Ubuntu 8.04, Skype, and Bluetooth handset"
date: 2009-08-18
forum: Hardware
---

### Post by Horomancer on 2009-08-18
Ok, I'm running Ubuntu 8.04, and i just recently got a handset from ThinkGeek.com to make using skype easier.
Trouble is i can't get the drn thing to work. I've browsed the forums and have tried some of the solutions listed and I am now at this point
1. My handset is Bonded and and shows up in Bluetooth Manager> Preferences> Services> Audio services
2. There are now BT Headset (hw:Headset,0) and BT Headset (plugin:Headset,0) options available in Skype> Options> Sound Devices. Niether of these options produce sound and I get the error 'Problem with Audio Playback' if I try to use them.
3. I have yet to make any applicatoin play sound through or pick sound up from my handset.

Nothing is working for me. What do i do now? I only need this handset to work with skype, nothing else

---

### Post by Horomancer on 2009-08-18
Update:
I reboot my computer and the BT options in Skype disappeared.


EDIT:
I tried starting over from scratch using the walkthrough i found here - [http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010)

i'm at step 23 but instead of getting the headset to pair up and make a sound i just get

jackmo@Time Control:~$ aplay -D btheadset -f s16_le /usr/share/sounds/login.wavPlaying WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:906: Channels count non available

why dos this have to be sooo difficult?

---

### Post by Horomancer on 2009-08-18
Ok so i found out that by running hcitool scan while the headset is in pairing mode will trigger the pairing request and let me enter in the '0000' passkey
this has paired my handset back with Ubuntu and Skype now has teh BT Headset option.
However selecting BT Headset still gives me an error message and is not usable
I tried this command

$ aplay -D btheadset -f s16_le /usr/share/sounds/login.wav

to try and get a response from teh head set but i only got this error

Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:906: Channels count non available

any i'm basically back to square one

sorry for all the selfbumps

---

### Post by Horomancer on 2009-08-18
After rebooting I can succesfully pair the headset with Ubuntu, and now Skype has 'btheadset' as an option for sound devices rather than
BT (Headset,0) BT (plugin:Headset,0)
Which was a big step forward!
I made a test call with sound in and sound out set to btheadset. The echo message came loud and clear through my head peice, but no audio was picked up from the mic. I did not get an audio pick up error like before.
After making a test call Skype froze up. I could open and close windows, play with options, and simular but could not make any calls, receive incoming calls, or close the program completely without bringing up System monitor and killing the app.
So a step forward but still not what i need -_-

Edit:
I typed in 
sudo cat /proc/asound/cards
to see what the headset was designated as so i could run alsamixer -cX where X is the number of the card.
It doesn't show up at all. I don't know what that means

EDIT AGAIN:
Ok, I found out that by running
sudo modprobe snd_bt_sco
sudo modprobe sco
I can make the bluetooth headset show up when i run 
sudo cat /proc/asound/cards
and can adjust the mic volume (it was set to 0 )
However, going back to skype I see that the btheadset option is gone and replaced with the old options and the old problems of not running
what the hell are modprobes?

---

### Post by Horomancer on 2009-08-24
bumpinate

---

