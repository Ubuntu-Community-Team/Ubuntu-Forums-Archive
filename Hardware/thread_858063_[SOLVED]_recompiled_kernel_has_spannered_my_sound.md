---
title: "[SOLVED] recompiled kernel has spannered my sound"
date: 2008-07-13
forum: Hardware
---

### Post by larryfroot on 2008-07-13
Hello everyone and whoops.

I have just recompiled my kernel from vanilla to 2.6.25.10 and its killed the sound on my Dell latitude D600.

I used the latest kernelcheck (hopestar) to do the deed as it has made an excellent job of things in the past. 

Testing sound playback through sound preferences brought error messages for pulse audio, oss, alsa and, naturally enough, autodetect. 

The volume control on the panel did not find any elements and/or devices to control. to quote it "This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured".

"No volume control GStreamer plugins and/or devices found"

A quick look in synaptic revealed gstreamer plugins present and correct. As a just in case I reinstalled ubuntu-restricted-extras. Still no sound.

As I am on Dell latitude laptop (D600) the soundcard/chip is (according to one sound geek out there):

Card: Intel 82801DB-ICH4
Chip: SigmaTel STAC9750/51

As an aside...there doesn't appear to be any thing that lists the hardware on the system in either preferences or administration...if I am wrong or ignorant of a particular tool that will help me to find out what kit is inside my boxes, I would be very happy to be informed. would save Googling around and also guarantee accuracy as laptop internals can vary within the same model...

If anyone can help me with this I would be well chuffed. especially as I was bragging about my spanky new kernel to my mate and then found that the sound was spannered. As was my reputation in his eyes, at any rate. There is always an audience for these moments! Grrr. 

Thanks for any help rendered.****

---

### Post by matt$2 on 2008-07-13
Yes ok.  Firstly how about ;
bring up a console., enter

sudo lspci

and this will list your hardware you're interested in.

then how about

sudo lsmod

and this will list all the kernel modul;es loaded in the system.

You say you re-compiled the kernel.  Well that's good, so I suspect the finding of the above mentioned will inform you of your hardware and indicate the presence or not of your required sound drivers.

There are the alsa drivers and the sound card driver that you need.

Post the outcome.
I suspect you'll be going back to /usr/src/newkernel-version
bringing up 
sudo make menuconfig
and getting your kernel configuration correct.

I had a very similar outcome the last time I compiled a new kernel, in gentoo

---

### Post by master_kernel on 2008-07-13
I think I know your solution (shown in the attachment).

Enable Intel HD Audio in ALSA PCI Devices in your kernel configuration.

---

### Post by sdennie on 2008-07-13
As master_kernel said, the HDA Intel sound cards are not built if you use the default Ubuntu kernel config (neither are the iwl drivers I don't think).  You can either rebuild the kernel with HDA Intel enabled or you could probably just download the alsa drivers from [here]("http://www.alsa-project.org/main/index.php/Main_Page") and simply build and install them into the new kernel.  The process is very straightforward.

---

### Post by larryfroot on 2008-07-15
Thank you all very much indeed for your help and advice - all of it good advice as well! Matt, I have taken careful note of lspci and lsmod. They have gone into my text file of useful penguin things. 

Master_kernel! The man himself! I did as you said - with apologies to the other participants in the thread, but when the developer of an app you have a problem with contacts you personally it would be rude to ignore him! I am constantly amazed by this community, and sometimes feel at a loss in giving back all the help that I have recieved, Still, with slender means the heart can be expressed,,,I recompiled as per your instruction and am rewarded with a) sound and b) the 2.26 kernel...bang on cue! Cool or what?

And vor....quite right...I am about to do just as you advise because I installed virtualbox...and before the vbox module was compiled into the kernel, I had sound. And after it had compiled into the kernel I had no sound! This is so bizarre. But at any rate, I am now fully equipped to deal with the situation.

Once again, many thanks for all your ubuntu.

---

