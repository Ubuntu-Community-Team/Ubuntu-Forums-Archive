---
title: "Alsa/USB Audio: M-Audio Transit USB"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by SethD on 2005-10-22
Hello forum,

I'm a current Gentoo Linux user and am thinking about switching to Ubuntu. I'm running on a Dell Inspiron 600m and the only things keeping me from switching is I'm not sure if I'll be able to get my modem (intel-8x0m/slmodem) and USB soundcard (M-Audio Transit USB) working. I think I've found information on getting the modem working, but I haven't seen anybody say anything about the Transit USB.

In Gentoo I have it working using the madfuload scripts provided at [http://www.theory.physics.ubc.ca/transit.html](http://www.theory.physics.ubc.ca/transit.html). I can make Alsa reload the modules and register the sound card quite easily. Unfortunately I'm not familiar with Ubuntu's method of doing the same thing so I'm not sure how I would get it to work there. It seems to me like Ubuntu loads everything dynamically, so I'm not quite sure how I'd get it to re-register the card. I've booted into a LiveCD and worked around with that but haven't had much luck.

I guess the simple version of my question is this: Is anybody using the Transit USB in Ubuntu? Was it difficult to set up? Are there any problems with it?

Thanks for your time and I look forward to your reply.
Seth

---

### Post by fdimmling on 2005-10-22
I suppose that your USB audio adapter should work out of the box in Breezy. It should be possible to test this with an Live Breezy CD system. You just go to System->Preferences->Audio->Default sound card and check if your USB sound card is selectable.
I have the iMic USB sound card and it works perfectly. Some time ago I asked the m-audio people on behalf of another USB sound adapter for guitar+voice. They told me that their USB sound adapters comply with standard USB interfaces and should therefore work with Linux too though it was not tested for the sound card in question.

Good luck

Friedrich

---

### Post by SethD on 2005-10-22
Friedrich,

Thanks for your reply. I'll have to check in to the iMic. Do you like it? How is the sound quality? Is it hot-pluggable in Ubuntu? Sounds cool.

If you read the link I supplied you'll see that the m-audio doesn't quite work "out of the box." You have to load the appropriate firmware for it. It's kind of a pain but I guess that's the way M-Audio decided to do it.

If anyone else out there has tried a good USB soundcard with Ubuntu, let me know!

Thanks again, Seth

---

### Post by mpvano on 2005-10-23
I've been using the transit on Macintosh OS-9, OSX, Windows 98SE, Redhat 9, Ubuntu 5.04 and now Ubuntu 5.10 with excellent results.

It's a very nice soundcard - I use it for live recording of concerts for subsequent radio broadcast. The quality is excellent for most purposes, but it does have a few quirks:

- no hardware record monitoring (but I usually use it with a mixer or receiver that provides monitoring)
- low voltage DC present on the line input jack to allow it's use with cheap "PC" and some mini-disc/cassette recorder microphones. This is usually not a problem when connected to most sources, but I HAVE seen it drive the VU metering crazy on some Mackie mixers if the device is connected to the tape outputs. It also can be a problem if you connect to a board with transformer outputs, but they're pretty rare nowadays.
- The linux driver doesn't support the trick the windows driver does of boosting the input gain in software so that you can use a microphone with it. The interface is quiet enough so that this works for low quality use, but it's too noisy for serious use anyway. I've had good luck, however using ladspa plugins and jack rack to cobble together a preamp for some uses. This has made it work well with a microphone for some simple uses - beware the voltage on the line input, however. It makes dynamic microphones act strange unless you use a cable with a blocking capacitor or a transformer rated to handle the current without saturating.
- It seems to generate a lot more rfi (probably because of it's more advanced cpu) than some of my other interfaces. It occasionally interferes with radio reception when used to record very weak FM radio stations if it's too close to the radio antenna.

INSTALLATION

The transit is, in fact, usb class audio compliant enough to work well with alsa. The problem is that whenever the device is plugged in, it has no firmware installed and you need to install USB firmware loading software to make it into an audio interface before it can be used.

There is a standard package called madfu-firmware for doing this, available from a project on sourceforge. It works well, but you must know how to install things from source to use it. It does NOT require a kernel build, but it does require access to the M-Audio windows driver files to extract the firmware module from them.

I DID have some trouble installing  madfu-firmware-0.7 under Ubuntu, however. It incorrectly installed two files that need to go into /etc/hotplug/usb into /usr/local/hotplug/usb instead and (as root) I had to manually copy them into the right place. I have noticed that there is now a version 0.9 release of madfu-firmware available and the release notes claim to have fixed this problem - I have not tried that version however.

USB Firmware loading is now a fact of life for many devices because it lets the vendor update the firmware to fix bugs easily.Nearly all M-Audio products require it. Unfortunately linus support for it is not always automatically installed.

I've got quite a few USB interfaces and use them on a lot of platforms and the Transit is definitely one of my favorites. Another plus is that it directly supports most common sampling rates, so it's less confusing to use. Cards that require software resampling by the ALSA driver or application can work very well, but they can be VERY confusing to use since it's hard to predict whether they will work with a given application or to troubleshoot why they don't.

My experience with the iMic has been very erratic. I've owned three of them and each one worked differently. Some of them seem to be excellent, reliable, quiet devices, others are flakey and noisy. I think they've made some running design changes to them and it's hard to tell what you'll get in advance. At the moment, ALSA doesn't directly support the iMic mixer properly, so it's behavior is also very confusing.

Hope this helps....

Mario

---

### Post by fdimmling on 2005-10-23
Hi Seth,

I bought the iMic to make Cds from my old favorite vinyl records and to make recordings from my playing guitar. It has excellent sound quality for both purposes though I am not sure if it would match professional standards. I like it very much. You just plug it into your computer and - in Breezy - you select it in the Gnome audio settings as default device. In Hoary you have to start the computer with iMic plugged in to make it the default device.

Friedrich

---

### Post by JaySteel on 2006-04-26
Ok I'm going to sound really stupid but......
After reading this post, I have to say that I don't understand a word you guys are talking about! It's all way over my head! lol

I'm looking for some help though. I wish to transfer my minidisc recordings onto my PC. I'll be using the optical output on the minidisc player and I want to use the USB port on my PC. Is this possible? What exactly do I need?
This 'M-Audio Transit High Resolution Mobile Audio Interface (Transit USB)' seams to do the job but I might be completely wrong! My PC is using windows XP. I have no idea what sound card I'm using. Does this matter? If so, what else would I need to purchase?

Thanks for any help or advice that anyone can offer me.
Please feel free to patronise me and teach me in a condesending manor if you believe this will help me to understand!! lol 

Jay

---

### Post by mpvano on 2006-04-26
Jay:

Are you sure your player has optical output? Most recorders only have optical input now due to sony's excessive paranoia about copyright theft. You're lucky if you have one of the old ones that do digital output.

The M-Audio Transit works very well for me, but it DOES require an extra installation step as described above in this thread. Most simple usb audio cards need no special software installation because they use "class" drivers which are generic drivers built into all modern versions of operating systems.

The Transit, however, like most M-audio interfaces, and like many other newer devices of all sorts, has an additional problem - it's missing the code inside it that makes it into an audio interface!

The device shows up as a generic USB device at every startup and the operating system must load the manufacturer's software INTO THE DEVICE that makes it into a usb audio interface. 

There is a standard package called madfu-firmware for loading M-Audio firmware into their interfaces, available from a project on sourceforge. It works well, but you must know how to install things from source to use it.

It does NOT require a kernel build, but it does require knowledge on your part about how to build drivers and it needs access to the M-Audio windows driver files to extract the firmware module from them.

The process can be confusing for a beginner. Reread my notes earlier in this thread about what's got to be done, then find and download the madfu package and read its documentation carefully. If you don't understand the process, don't try it. There are other cards available that work with no driver added.

I'd stay away from the iMic however - I have had three of them and they're good value for the price, but they seem very inconsistent in quality - some of mine are very quiet and reliable, others are noisy and flakey and crash at the drop of a hat. Their mixer interface is a little confusing as well when used on Linux.

Note however, that In my opinion, there's very little benefit to using the optical interface on MD players that support one, since the audio is so highly compressed and it's ALWAYS resampled on playback in the player. (Except of course when playing raw pcm encoded files on the new HD players - but they don't have an optical output!).

I do a lot of transfers and the quality is usually as good as it's going to get by coming out of the line or headphone jack into a decent 16 bit analog audio interface if you get the cabling and levels right.

hope this gives you more information to work with,

Mario

---

### Post by conortodd on 2006-09-21
Hi everyone.

I'm considering getting a Transit for a MythTV frontend which I'm building.  Due to the small form factor of the machine, I'm out of PCI slots and so I'm looking for a USB audio solution which will give me the ability to play at least 7.1 channels via a SPDIF output (either optical or RCA).  The Transit seems like it has the ability to do this, but I'm not sure if ALSA can work with it to that extent yet.

Has anyone been successful in setting up a Transit to play out 7.1 channels via it's SPDIF output under Linux?

Thanks!

---

### Post by aka.robbie on 2008-03-16
I'm having the same problem with my system, so my question is:
Is anyone here that can post how to make it work step by step ?

I have followed some posts and now neighter my transit usb works or my normal sound card...so no sound for me :(

---

