---
title: "No sound from headphone jack"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by sammydlm on 2008-01-14
Hello, all.  I am trying Ubuntu for the first time by installing on my Everex Stepnote NC1502 laptop.  My laptop actually came with Vista, but Ubuntu 7.10 is running 10 times better on it.  I have gotten everything to work so far except the sound through my headphone jack.  My headphone jack works fine in Windows, so it has to be specific to Ubuntu.  I've been reading a lot of threads regarding headphone jacks for other types of laptops, but, being new at this, I'm not sure where to start or if the instructions are specific to the other sound cards.  I did read that by typing aplay -l in the terminal you can find out what sound device you have.  Here is my output:

sammy@sammy-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sammy@sammy-laptop:~$ 

Can someone please help me fix my headphone jack problem?  I love using Ubuntu, but hate not being able to use my headphone jack for music and Skype.  Please make your advice as plain as possible as I am very new to this.  Thanks in advance.

---

### Post by miceagol on 2008-01-14
The first thing you can do is go to a terminal and type alsamixer. What volume sliders do you see there? You can mute/unmute sliders with m, and change the volume with up/down key.

---

### Post by sammydlm on 2008-01-14
I see Master Front, PCM, Front, Front Mic, and finally Input Source (with no slider above it)  Input Source lets me cycle between Stereo Mixer and Front Mic.  Thanks for the quick reply!

---

### Post by Yellow Pasque on 2008-01-14
What codec/sound chip do you have. Please run:
```
grep Codec /proc/asound/card0/codec#*
```

---

### Post by sammydlm on 2008-01-14
Here's what I got:

sammy@sammy-laptop:~$ grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: VIA VIA VT1708
/proc/asound/card0/codec#1:Codec: Conexant ID 2bfa
sammy@sammy-laptop:~$

---

### Post by sammydlm on 2008-01-15
Is there anything else that I can try?

---

### Post by sammydlm on 2008-01-15
I found this thread where it seems someone solved it for someone else, but it is somewhat confusing for me since I'm not sure how to patch a file.  Can someone guide me through it?

[http://ubuntuforums.org/showthread.php?p=1517455](http://ubuntuforums.org/showthread.php?p=1517455)

---

### Post by Yellow Pasque on 2008-01-15
You can try playing with different options in your /etc/modprobe.d/alsa-base file. See:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

You can try some of the methods here:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

You can try a completely different sound system, OSS4. See link in my sig.

---

### Post by Yellow Pasque on 2008-01-15
> **sammydlm said:**
> I found this thread where it seems someone solved it for someone else, but it is somewhat confusing for me since I'm not sure how to patch a file.  Can someone guide me through it?

[http://ubuntuforums.org/showthread.php?p=1517455](http://ubuntuforums.org/showthread.php?p=1517455)

That's a pretty old thread. It refers to patching ALSA 1.0.12  If you're using Gutsy (7.10), you should have ALSA 1.0.14

---

### Post by sammydlm on 2008-01-15
I tried OSS4 from your link a little while ago, but my headphones didn't work still and my volume control on my laptop stopped working.  I was able to uninstall OSS4 and ALSA and get back to where I was before.  It took me a while to figure it out.  I will try your two other links, though.  Thanks for the help.

---

### Post by Yellow Pasque on 2008-01-15
Hey, np.

I'm curious for feedback's sake: Did you try the volume control patch when you did OSSv4? Also, when you ran ossxmix, did you have a separate volume slider for your headphones?

---

### Post by sammydlm on 2008-01-15
I appreciate your help, but it seems to be a bit over my head.  This is my first time trying Linux so I am not familiar at all with it.  I did not see anything that applied to my laptop.  The only thing I saw was that in the second link you posted the Dell Inspiron 1300 had the same Conexant 2bfa codec.  Other than that, I have no clue what to do.  Regardless, thanks for trying to help me.

---

### Post by sammydlm on 2008-01-15
I did not try the patch because I don't know how to apply them.  Also, I have never seen a volume control for headphones at all while using Ubuntu on this laptop.  I still like Ubuntu and it runs great on my laptop, but I don't know enough about Linux to fix it by myself.

---

### Post by lawr_rawr on 2008-01-15
Forgive me if this is too simple -- you've probably already tried this. I just wanted to throw it out there since it fixed my problem this weekend. (3 months of Gutsy before I tested the headphones!)

In the volume control, there's a set of sliders for front, pcm, etc. There's another tab that had a "headphone" checkbox. I had to check this box before I got any sound out of the headphones.

On Feisty I had a slider for Headphone; on Gutsy I only have the checkbox.

---

### Post by Syke on 2008-01-15
> **sammydlm said:**
> Hello, all.  I am trying Ubuntu for the first time by installing on my Everex Stepnote NC1502 laptop.

Can someone please help me fix my headphone jack problem?  I love using Ubuntu, but hate not being able to use my headphone jack for music and Skype.  Please make your advice as plain as possible as I am very new to this.  Thanks in advance.

The existing drivers won't work on this model (for the headphones). We're working on getting them fixed, but I don't know when that will be.

---

### Post by Yellow Pasque on 2008-01-15
Try OSS4 again. The volume control patch was already applied and built into an included library (libgstossaudio.so). The patch file itself is only included for reference. All you need to do is move that file to the /usr/lib/gstreamer-0.10/ directory and overwrite the old one. Follow the commands in the README file. As far as getting the mixer to work, all you should have to do is type ossxmix in a terminal.

---

### Post by sammydlm on 2008-01-16
Temüjin, I downloaded the OSS package again.  I saw that if I double-click the folder, it gives me the option to install the package.  Can I just do it that way vs. doing it from the command line?

---

### Post by Yellow Pasque on 2008-01-16
It's tempting, but the installer instructions tell you to use the command line, and I would suggest following the instructions. Besides, it's only a couple commands.

---

### Post by sammydlm on 2008-01-16
Ok, I did everything up until the point where I have to install the patch.  When I go to the terminal and I type gzip /usr/lib/gstreamer-0.10/libgstossaudio.so, it tells me that there is no such directory.  When I go to the gstreamer-0.10 directly to look inside of it, I can see the libgstossaudio.so.gz folder, but when I try to extract it by double-clicking it, it tells me permission denied.  So, I can't extract the file either way.  I also tried extracting it on my desktop, then copying the extracted file and it tells me that I don't have permission to write to that folder.  The same thing happens when I try to drag and drop it from the gstreamer folder.

I did manage to open the mixer to look at it, but I still have no audio from the headphones.  There is a checkbox with headphones in a drop down menu under the record section, but it does not do anything for the headphone audio whether it is checked or not.

Any suggestions on how to proceed?

---

### Post by Yellow Pasque on 2008-01-16
For the patch, simply download it, open it with the GUI and extract to your Desktop. You should now have a folder with 3 files. Go to a terminal and type: 
```
cd /usr/lib/gstreamer-0.10/
sudo mv libgstossaudio.so libgstossaudio.bak
sudo nautilus
```
That will backup the original file and bring up a file browser with root permissions. Now you can navigate to the gstreamer-0.10 dir in that window and drag/drop the new libgstossaudio.so file.

For the headphone problem, let's start by looking at your output from:
```
ossinfo -v
```

---

### Post by sammydlm on 2008-01-16
I got stuck at sudo mv...  Here is what it said:

sammy@sammy-laptop:~$ cd /usr/lib/gstreamer-0.10/
sammy@sammy-laptop:/usr/lib/gstreamer-0.10$ sudo mv libgstossaudio.so libgstossaudio.bak
[sudo] password for sammy:
mv: cannot stat `libgstossaudio.so': No such file or directory
sammy@sammy-laptop:/usr/lib/gstreamer-0.10$

---

### Post by sammydlm on 2008-01-16
I went at looked at the libgstossaudio.so by right-clicking and looking at properties, permissions and it said I was not the owner so I couldn't change permissions (all root).  Do you think it is a permissions problem?

---

### Post by sammydlm on 2008-01-16
Ok, I got the file to write into the folder.  I kept getting no such directory, so I looked at the file and it was libgstossaudio.so.gz, so I added the .gz at the end and I got no error, so I kept going and it opened the other file browser window.  I dragged and dropped and it worked.  To check it, I closed it out and reopened the folder and it was there.  Now that it is there, was does that accomplish?  (Pardon my ignorance)

When I ran ossinfo, this is what I got:

sammy@sammy-laptop:~$ ossinfo -v
Version info: OSS 4.0 (b1012/200801022350) (0x00040003) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (sammy-laptop)

Number of audio devices:        4
Number of audio engines:        12
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 VIA HD Audio interrupts=585 (585)
    HD Audio controller VIA HD Audio
    Vendor ID    0x11063288
    Subvendor ID 0x1e401509
     Codec  0: Unknown (0x11061708/0x15091e40)
     Codec  1: Unknown (0x14f12bfa)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: High Definition Audio 0x11061708 (Mixer 0 of device object 1)
    Device file /dev/oss/hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 

Audio devices
High Definition Audio pcm1        /dev/oss/hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: Available for use 
      Engine      2: Available for use 
      Engine      3: Available for use 
      Engine      4: Available for use 
      Engine      5: Available for use 
      Engine      6: Available for use 
      Engine      7: Available for use 
      Engine      8: Available for use 
      Engine      9: Available for use 
High Definition Audio pcm2        /dev/oss/hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: Available for use 
High Definition Audio pcm3        /dev/oss/hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: Available for use 
High Definition Audio rec         /dev/oss/hdaudio0/pcmin0  (device index 3)
    Legacy device /dev/dsp3
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: Available for use 
      Engine      2: Available for use 
      Engine      3: Available for use 
      Engine      4: Available for use 
      Engine      5: Available for use 
      Engine      6: Available for use 
      Engine      7: Available for use 
      Engine      8: Available for use 
      Engine      9: Available for use 
sammy@sammy-laptop:~$ 

So far, so good... (crossing fingers...)

---

### Post by Yellow Pasque on 2008-01-16
Plug your headphones in and run:
```
osstest
```
Warning: It plays loud music, so don't do it in public. osstest will test left, right, and stereo outputs on each device listed in ossinfo.

The volume control patch should allow you to control the volume with your media keys and/or mouse wheel if your laptop was set up to do that before. Also, the gnome volume control app shouldn't have an 'x' on it now, if you didn't already remove it for ossxmix.

---

### Post by sammydlm on 2008-01-16
I now see OSS Mixer in the default mixer tracks drop-down menu under System, Pref, Sound.  I also see Volume under the device, but I cannot control the volume with the media keys.  The only way I can control the volume is with the ossxmix -d0 sliders.

I tried osstest and it did play loud music over the speaker, but when I plugged the headphones in the music went away.

To summarize, I can't control the volume with my keys and I still have no audio from my headphones, however, I am willing to keep trying as long as someone is willing to help me.

---

### Post by sammydlm on 2008-01-16
I don't know why because I didn't do anything, but my volume control keys are working now.  Now my headphone jack is the only problem.

---

### Post by Yellow Pasque on 2008-01-16
> I tried osstest and it did play loud music over the speaker, but when I plugged the headphones in the music went away.

It exhibited this behavior for all 3 output devices?

---

### Post by sammydlm on 2008-01-16
Yes, for all three.  I plugged and unplugged the headphones every time it went to the next device during the test.

---

### Post by sammydlm on 2008-01-16
Why does the only thing that says headphones show up under record as "fp-headphones" with one slider in the ossxmixer -d0?  I don't understand why "headphones" is located under the record section of the mixer.

---

### Post by Yellow Pasque on 2008-01-16
I'm running out of ideas :(
What output does ossmix give you?

---

### Post by seawright on 2008-01-16
Sammy,
I Am trying to understand your gstreamer problem. Can you run the following command in a terminal and paste the result in your reply:

file /usr/lib/gstreamer-0.10/libgstossaudio.so*

regards,
Clive

---

### Post by sammydlm on 2008-01-17
Sure thing... here is what I got in the terminal:

sammy@sammy-laptop:~$ file /usr/lib/gstreamer-0.10/libgstossaudio.so*
/usr/lib/gstreamer-0.10/libgstossaudio.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), stripped
sammy@sammy-laptop:~$

---

### Post by sammydlm on 2008-01-17
Everyone, thanks for your help, but after I found out that Skype wouldn't work without ALSA, it became a moot point for me to fix my headphone jack.  Using Skype was the main reason I wanted to get the hp jack working, so I took OSS off and went back to ALSA.  I really appreciated your time, but I'll just live with no headphone jack unless someone knows how to fix it in ALSA.  Thanks!

---

### Post by Yellow Pasque on 2008-01-17
Skype for OSS
[http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)

---

