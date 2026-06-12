---
title: "No sound on Dell XPS M1710"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by MickSulley on 2007-10-06
Hi,  I have installed Feisty on my Dell XPS M1710 and I cannot get the sound to work.  I have found lots of hits on various forums but non have fixed the problem.  I think that is is a very basic problem and the system just does not see the sound card.  From some of the hits I have found I have tried - 

mick@mick-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
mick@mick-laptop:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
mick@mick-laptop:~$ 

So it seems to think that there is no sound card there, however if I boot from a Edgy live CD the sound works fine.  Also the beep still works, but I think that is separate. 

Can anyone give me any pointers on how to fix this please.  

Anyone know if it should work in Gutsy?  That is due in a few days so that may be an option.

Can you please keep any suggestions at the absolute beginner level please, I am very new to Linux.

Thanks

Mick

---

### Post by omegamormegil on 2007-10-07
Try this page first: 

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)  

It has a section on manually configuring your sound card, but start from the top.  It has you use the terminal some, but it's easy to follow and very thorough.  This page is usually recommended as the first place to start.  It should give you a better idea of where the problem originates.

Sad to say, I wouldn't hold your breath for sound working in Gutsy, if you have a Dell Laptop with an hda_intel sound card.  I have sound in Feisty working fine on my Dell Inspiron 1300, but not at all in Gutsy, and I don't think it's going to be fixed in time for the release.  However, I'm sure that very soon after release, someone in the forums will come up with an easy solution, and then I can install Gutsy on my laptop. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133)

---

### Post by MickSulley on 2007-10-07
I have looked at that page but fail right at the start.  My sound icon has a red cross and the volume control was not on the menu.  I have added the volume control as per instructions, but if I try to open it from the menu or the icon I get the message 'No volume control GStreamer plugins and/or devices found.'

I have lots of gstreamer packages installed but I don't know if I have the correct one, or is the problem that it does not see the device?

Any idea what I can do next?

---

### Post by ljonesj on 2007-10-07
i have that exact sound card in my acer you just have to turn some more volume controls on in sound perfernces

---

### Post by MickSulley on 2007-10-07
Sorry to be dense but I don't understand how to do that.  If I go to Sound Preferences all the devices are set to Autodetect.  If I change any of them and hit Test I get an error message - 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

I cannot see any volume controls to turn on.

---

### Post by ljonesj on 2007-10-08
double click on the sound icon in the task bar and go to edit and perferences and you will see check boxes. that will let you add more sound control slides

---

### Post by MickSulley on 2007-10-08
I assume that the sound icon is the loudspeaker symbol.  If I double click on that I get an error message 

No volume control GStreamer plugins and/or devices found

---

### Post by ljonesj on 2007-10-09
ok try this 
options snd-hda-intel model=auto

at the bottom of:

Code:

sudo nano /etc/modprobe.d/alsa-base

---

### Post by MickSulley on 2007-10-10
Tried that and it has made no difference, still get the same error message.
Any other ideas?

---

### Post by MickSulley on 2007-11-13
I have updated to Gutsy Gibbin and while trying to sort out something else I disable all but the generic kernel.  As if by magic I now have sound!

Mick

---

