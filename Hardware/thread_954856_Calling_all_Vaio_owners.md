---
title: "Calling all Vaio owners"
date: 2008-10-21
forum: Hardware
---

### Post by jacalonzo on 2008-10-21
Here is the ACPI DSDT for:

SONY VAIO LAPTOP VGN-NR330FE (PCG-7132P)

Buyed in Monterrey, Mexico, on september, 2008

Thank you for your work!!

---

### Post by psymicha on 2009-01-09
Hallo,

i'm also a proud owner of a sony vaio VGN-CS11S

I'm really having trouble to activate all FN-keys.
Except the keys for sound control worked out of the box.
So following work fine: 
 * Mute 
 * VolDown
 * VolUp

The rest does not work at all:
 * Brightness down
 * Brightness up
 * Zoom out
 * Zoom in
 * Fn-12

Further there exists a keybar for multimedia playback and a special capture button for the camera.

Hopefully it will change ;)

greetz

---

### Post by niceguy123 on 2009-01-10
> **jacalonzo said:**
> Here is the ACPI DSDT for:

SONY VAIO LAPTOP VGN-NR330FE (PCG-7132P)

Buyed in Monterrey, Mexico, on september, 2008

Thank you for your work!!

Can you please explain what this is about. I am using Sony Vaio VGN-FW250J

---

### Post by marcos_zion on 2009-02-12
thanks

---

### Post by pablo_macbeth on 2009-02-22
Hello,

can you explain it? i've a vaoi VGN-SR21M


thanks

---

### Post by markoschlegel on 2009-04-19
This is my Sony Vaio SZ730E dsdt results:
filename:  VGN-SZ730E-R0121S5.dsdt.tar.gz

Mark

---

### Post by okan72 on 2009-04-29
[B]How do I access the BIOS ?
 [/B]

---

### Post by m1xx3r on 2009-05-02
If it is possible, could you help me find the ACPI DSDT for a Sony Vaio PCG-TR2MP? 

Thanks!

---

### Post by BlackRazor22 on 2009-06-02
VAIO VGN-CS21S: only the volume hotkeys work, brightness hotkeys don't work and I have instead to use smartdimmer.

---

### Post by thmonkey on 2009-06-05
hello everyone!

> **psymicha said:**
> Hallo,

i'm also a proud owner of a sony vaio VGN-CS11S

I'm really having trouble to activate all FN-keys.
Except the keys for sound control worked out of the box.
So following work fine: 
 * Mute 
 * VolDown
 * VolUp

The rest does not work at all:
 * Brightness down
 * Brightness up
 * Zoom out
 * Zoom in
 * Fn-12

Further there exists a keybar for multimedia playback and a special capture button for the camera.

Hopefully it will change ;)

greetz

apart from these issues, my cs11s has a problem with the MagicGate MSPro Card Reader. The SD Card Reader works fine though.

Ubuntu 8.10's drivers and my graphics card (NVIDIA GeForce 9300M) was not a good combination at all...in 8.04 no such issue exists, it works fine. Anyone noticed problems with ubuntu 9.04?

PS. what exactly are these dsdt files that all of you attach?

---

### Post by mister_playboy on 2009-06-06
What's going on in this thread?  Is this about the FN keys?  I'm interested since I have a Vaio VGN-NR430E.

---

### Post by MindGuerrillas on 2009-06-15
Here's mine

None of the Fn keys work.
Brightness is controllable from the Gnome Power Manager applet only.
Wifi works fine

After posting this info how does one go about getting these to work? Are we waiting for some updated driver?

---

### Post by geekygirl on 2009-06-15
> **MindGuerrillas said:**
> Here's mine

None of the Fn keys work.
Brightness is controllable from the Gnome Power Manager applet only.
Wifi works fine

After posting this info how does one go about getting these to work? Are we waiting for some updated driver?

Its a modification to the sony-laptop kernel module that is needed and these files provide the neccesary information to be able to do that.

You could try the upcoming 2.6.30 kernel which does have a new and improved sony-laptop module inlcuded. This was an issue that had also bugged me on the Vaio TT, but thanks to a few people in here and the internet in general a patch was made for the current kernel.

---

### Post by markoschlegel on 2009-06-16
> **thmonkey said:**
> hello everyone!

PS. what exactly are these dsdt files that all of you attach?

There was an older thread that ran for a long time and got disconnected from this one for some reason.  Go look it over to see what the dsdt files are in detail 

[http://ubuntuforums.org/showthread.php?p=2789021#post2789021](http://ubuntuforums.org/showthread.php?p=2789021#post2789021)

But basically the dsdt file contains detailed information about the hardware of the laptop so the coders can support more of the buttons and features on more models of laptop.

That earlier thread has a script 'snc-dsdt.sh' attached that makes it easy for the user to capture the dsdt file so it can be attached to the forum for the programmers.

---

### Post by coldmack on 2009-06-17
So, I am still kind of fairly new to ubuntu, and I have plans of purcahsing the Sony Vaio TT. Now is there like a specific version I can download designed for like Sony devices?

---

### Post by coldmack on 2009-06-19
Now here is a question I have. I ordred a Vaio TT, and have notice that UNR is for Atom devices, but the architecture it uses is for i386(not the Atom cpu and hence why I never put it on my HP). So, what I want to know is could UNR be a viable option for the TT(pending we do all the updates to get everything work right)?

---

### Post by sjLondon on 2009-12-01
Hello

Friend has Sony Viao Laptop but sound does not work. Cannot see external amplifier option in alsamixer so cannot try to disable it (as suggested in other thread).

Label says:  PCG-7V2M  but script says: VGN-FE48E

Sound does not work, tried all options such as:
#options snd-hda-intel model=vaio enable=1 index=0
#options snd-hda-intel model=vaio-ar position_fix=0
#options snd-hda-intel model=mobile enable=1 index=0
#options snd-hda-intel model=vaio position_fix=0
options snd-hda-intel model=sony-assamd enable=1 index=0

None of the above worked. Have also tried updating alsa by manual install.
This is on Ubuntu 9.10 ( 2.6.31-15 )

Thank you

---

### Post by BigMeanMikeRich on 2010-01-13
**VAIO VPC-CW14FX**

 Only Fn keys that work are Vol +/- and mute.  Brightness +/- seem to be detected correctly, but this model does not actually dim or brighten with either the Fn keys or Gnome brightness applet.

---

