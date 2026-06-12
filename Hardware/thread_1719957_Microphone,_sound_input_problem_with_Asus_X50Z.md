---
title: "Microphone, sound input problem with Asus X50Z"
date: 2011-04-02
forum: Hardware
---

### Post by mattasus on 2011-04-02
I just re-installed ubuntu 10.10 on my laptop so I want to have a fresh start at resolving this microphone problem that I even had before I re-formatted. I tried too many different things that it corrupted other applications which is why I decided to start fresh.

My sound card is  Realtec ALC662 rev1.

If there is anyone who is genius with Ubuntu that wants to help with this? And I'll take the advise step by step. I'm not going to do the problem solving on my own, I realize I'm not qualified to do so yet. By the way my sound input is unmuted in the sound preferences.
Thank you in advance

---

### Post by lidex on 2011-04-02
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by mattasus on 2011-04-02
Thanks for offering to help. I tried that, it gave asus mode 3. But it didn't change anything. I first checked in the input levels under sound preferences as a speak and as a second test I did a skype test call.

This is my second time writing this as before I wrote my typing cursor jumped back a few lines and then my mouse jammed. I was able to move the mouse around, it was highlighting what is was on but the clicking didn't do anything. I had to use ctrl alt del to reboot. 
That has happened to me several times already. I had that problem before, but by doing all the microphone troubleshooting I accidentally got rid of that bug. That's the other bug from ubuntu that is being in issue. Would you know anything about that?

---

### Post by lidex on 2011-04-02
That should work with that model. Let's look under the hood.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mattasus on 2011-04-03
Ok I did that and this is what I got:

```
Your ALSA information is located at http://www.alsa-project.org/db/?f=89e01595f3ce0bc369c4105a8afe1c25cef6aa9b

Please inform the person helping you.
```

I'll check out the link now
Thanks again

---

### Post by mattasus on 2011-04-03
Ok, something has happened, I just checked the input levels under sound preferences-input and as I spoke the rectangles got filled up accordingly. Then I did the skype test call and no sound was recognized, then I went back to sound preferences and the input levels were dead.

It seems to be partially working. I just installed skype before creating this thread. and I did not make any changes other than what is on here and installing automatic updates.

---

### Post by mattasus on 2011-04-03
After this I just rebooted the laptop and there is no response under sound preferences-sound input. I did not set skype to start when I reboot, that I have to do manually. So it is back to not working at all.

---

### Post by lidex on 2011-04-03
Remember with skype to disable the option to allow it to control your audio levels. That model is not working. 
Leave it in there for now but comment it out - we may need to edit it later. Put a # and space in front of that line.
Try updating your alsa-modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by mattasus on 2011-04-03
Before I did anything, I went to check my sound preferences and the sound input levels were working. Then I was excited to hear my voice and I tried to record something using the sound recorder that come with ubuntu and nothing happened. Then I when back to sound preferences-input level and it was no longer active. ???

Then I typed in the commands you gave me and this is what it did:

```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-alsa-driver-modules-2.6.35-28-generic
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 1,909kB of archives.
After this operation, 9,081kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main linux-alsa-driver-modules-2.6.35-28-generic amd64 2.6.35-28.201104031604 [1,909kB]
Fetched 1,909kB in 7s (243kB/s)                                                
Selecting previously deselected package linux-alsa-driver-modules-2.6.35-28-generic.
(Reading database ... 148792 files and directories currently installed.)
Unpacking linux-alsa-driver-modules-2.6.35-28-generic (from .../linux-alsa-driver-modules-2.6.35-28-generic_2.6.35-28.201104031604_amd64.deb) ...
Setting up linux-alsa-driver-modules-2.6.35-28-generic (2.6.35-28.201104031604) ...
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
```


Back to sound preferences-sound input and still not reading anything. But I haven't rebooted.
So I don't know what to think. All I did today was basic online surfing, listened to a radio program (coast2coast) and used open office writer. I don't understand how it went from not working to working then back to not working without any reboot during all that time.

---

### Post by lidex on 2011-04-03
**Remember with skype to disable the option to allow it to control your audio levels.**

---

### Post by mattasus on 2011-04-03
I missed the part where you told me to reboot so I just did that. The sound input level was working, then just opening the sound recorder application without doing anything else stopped it from working. My hardware is set at analog stereo duplex, I tried every other one being; analog output, analog input, digital stereo duplex. Out of all these only the analog output or analog stereo duplex work, so I'll leave it at the Duplex.

So it seems to work until I open sound recorder and maybe skype would jam it as soon as I opened it.

---

### Post by mattasus on 2011-04-04
I just unchecked the box that allows skype to adjust my mixer levels, I also noticed that once skype is opened and I do a test call it shows up under sound preferences-applications until I hang up.

---

### Post by mattasus on 2011-04-04
I decided to go back and check out my sound preferences and I noticed that my sound input device was unselected because I played around with the different hardwares as mentioned above. So I checked the orange circle, and it was back to working, then I decided to open skype and do a test call and it finally worked! Thank you

Just for fun I opened the sound recorder application and it jammed the sound input again. Then I played around with the hardware and re-checking that circle, closing and re-opening sound preferences. It is back to not working!
With my brief experience with this I bet that the sound input bar is going to read again in about 30 minutes for my unknown reason. This device has a mind of its own.
I'm telling you this for your own learning, I don't need sound recorder, Skype is all for now. So at this point I don't think I need your help but it would be nice if you can comment on this weird bug.
Thanks again!

---

### Post by mattasus on 2011-04-04
One last thing, the sound came back because I closed the laptop and re-opened it without shutting it down. I didn't take that into account because I didn't think it did anything. When I re-open it asks me to log back in, then I go back where I left off and of course sound input gets a reading.

---

### Post by windozh8ter on 2011-04-04
Lidex, I looked into this thread as you suggested and went through the steps. Still ran into the same problems. I also tried Mattasus's idea to close the lid and reopen it, and that did seem to "release" the microphone for use again without having to go through a full reboot.

As I did a bit more testing, I noticed if I tested my video in Skype, then immediately tested my microphone (with the webcam still on), the mic check didn't work. So I settled in on the idea that video keeps killing the microphone some how.

I ran another test: perform the test call in Skype, then in the middle of that call, test the web cam via the Skype settings. That test showed the microphone didn't die. So I wondered if maybe the microphone/sound card needed a few moments to get a full grip, so-to-speak, on the sound before any other process disrupted it.

The final test was to uncheck the video setting "Start my video automatically when I'm on a call" in Skype, and then to do a video call. I made a test call and made sure to speak a few sentences with the other party to make sure the sound was holding and not just cutting off at "hello". The sound held, so I then started my video. Voila! It worked!!

Honestly, I'm not sure what step actually fixed it. But I am SOOO glad this seems to be resolved. (At least it has worked once!)

I cannot thank you enough, Lidex. And Mattasus, thank you, too. Lidex, do you have a PayPal beer fund or something I could contribute to? You've helped me so much (through at least four different threads), I'd be more than pleased if you could enjoy a nice drink on me. Let me know.

---

### Post by windozh8ter on 2011-04-15
Lidex, I come seeking your advice again. I keep getting up update notice for the following:

[LIST]
[*]Ubuntu-supplied Linux modules for version 2.6.35-28-generic ALSA snapshots
linux-alsa-driver-modules-2.6.35-28-generic (Size: 1.0MB)
[/LIST]
I've been ignoring the update notice hoping not to break my (finally) functioning system. However, it's also getting a little annoying always seeing the update.

My question: should I stay away from the update, or should I go ahead and apply it? Your advice will be very much appreciated. Thank you!

---

### Post by lidex on 2011-04-17
> **windozh8ter said:**
> Lidex, I come seeking your advice again. I keep getting up update notice for the following:

[LIST]
[*]Ubuntu-supplied Linux modules for version 2.6.35-28-generic ALSA snapshots
linux-alsa-driver-modules-2.6.35-28-generic (Size: 1.0MB)
[/LIST]
I've been ignoring the update notice hoping not to break my (finally) functioning system. However, it's also getting a little annoying always seeing the update.

My question: should I stay away from the update, or should I go ahead and apply it? Your advice will be very much appreciated. Thank you!
That shouldn't cause any issues unless there's a regression. If you just don't want to see it anymore, uncheck the PPA for audio-dev in software sources and refresh your repositories.
```
software-properties-gtk
```
The 'Other Software' tab.

---

