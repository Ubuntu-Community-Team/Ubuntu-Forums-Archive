---
title: "Fujitsu Siemens 2428 compatibility"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by Kubunteando on 2007-11-17
There are not much info on how the new AMILO laptops are doing with Ubuntu.
I mean the Amilo Xi 2428 and Amilo Xi 2528. And cannot find also any reviews of those.
They seem to have ok specs, but none says any good or bad things about those.

I hope some of the Amilo Xi 2428 owners running Ubuntu will read this thread and can tell what works and what does not work in Ubuntu. And how they like the laptop.

I have only read that one guy could not make the webcam and microphones to work.

Thanks,

---

### Post by breaking on 2008-03-16
I got the Amilo xi 2428 a few days ago and installed ubuntu 7.10 the same day.

Generally I'm very happy with Ubuntu on the xi2428 because the battery lasts longer and the fan doesn't run all the time like it does with windows vista.

Theres a few things which aren't working properly, any advice of users who achieved to get them working would be appreciated.

**Not working:**
The Webcam.

Microphone is working, but signal strength is very low. There is no Microphone boost option   in the mixer (seems to be the case with that particular intel HDA sound driver) and I could get the volume up a bit by putting all Capture and the Digital slider to the max in gnome mixer.

The function keys in front of the display aren't working, too. This is not a big drawback since the Fn combination buttons are working properly and you can change the sound volume and display brightness with them.

suspend to ram and hibernate are not working either. The laptop will go to sleep but theres only a black display when you try to wake it up. Hibernation will cause the computer to lock up.

Inrared remote isn't working either.

[B]
Working:[/B]

card reader

bluetooth (although i wasn't able to browse my phone, i could at least pair it with the system)

wireless network

The Fn combination buttons

[B]
Unknown:[/B]

eSATA, HDMI

Since i don't have any devices that use eSATA or HDMI, I couldn't test these two.


All in all im happy with my purchase. If I find out how to solve any of the above problems i will post again.

---

### Post by Kubunteando on 2008-03-19
For the suspend issues I would check:

[http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)

I haven't tried myself, but that webpage is a good source of information.

---

### Post by MacheteMurderer on 2008-03-22
i also have the 2428 pretty much the same things are working for me but when i use headphones the built in speakers dont mute like on windows for instance ive tried using the sound manager, do you have the same problem or know to get around it?

---

### Post by Ouba on 2008-03-28
Hello,

I also have a fujitsu amilo xi 2428, everyhting is working fine (webcam, esata, hdmi, bluetooth with mouse and keyboard, wifi, nvidia glx ...) except the audio. I mean, the basic functionnality is fine, but as MacheteMurderer pointed it, when I plug an headphones, the builtin speakers still works ...

I've try some tricks with /etc/modules.d/alsa-sound, and especially some tries with model variable as explained in the file ALSA-Configuration.txt from the kernel sources.

For the webcam, you can use this tutorial : [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

If someone have a solution for the audio configuration, I will greatly appreciate !

Thanks in advance

Best regards

Denis Sacchet

---

### Post by MacheteMurderer on 2008-03-29
Hi,

I just installed the hardy beta and everything that seems to have worked before still does, although my screen resolution is fine in the screen resolution monitor window my screen is unknown not really a problem....
I don't know if anyone noticed or maybe its to do with hardy heron but my sound quick links work, the ones in front of the display - mute, increase volume and decrease volume to be more specific.

This leads me to believe it should be possible to use the other key, being able to use the next pause etc. would be very nice

And if anyone has ideas on the remote control.....:confused:

---

### Post by LingLing on 2008-03-31
Thanks Ouba for the webcam link.
I did all the steps to download, compile and install the latest UVC driver but still no webcam. I tried to activate it with Fn-F7 as in Vista. (The other Fn-Buttons all work fine)
Skype or Ekiga still cannot see any web cam devices.
What am I doing wrong?

---

### Post by Ouba on 2008-04-01
MacheteMurderer : good news, for the other keys, you can try to use the command "xev", it will give you the name of the key when you press it. You will then be able to associate them with action ...

LingLing : do you have more details, I follow the link I gave, and in skype 2.0, the webcam is working perfectly ...

Moreover, I got a hint for the sound card, I posted a bug in the BTS of alsa project, and they told me to try this drivers :

[ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20080323.tar.bz2](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20080323.tar.bz2)

and specify model=fujitsu-pi2515

I don't test it for the moment, but if you have enough time, you can try this howto :

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Denis

---

### Post by LingLing on 2008-04-01
I followed the link and downloaded and compiled the source code as in the instructions.
There where no error messages.
When I do 
*sudo modprobe uvcvideo*
There is no output which i guess is how it should be.

However Fn-F7 has no effect. Do you switch your cam on and off with Fn-F7? Is the red/green cam light working?
In skype 2.0.0.63 under video devices it says "no device found"
What else can i do?
:confused:

Edit:
When i press Fn-F7 and watch the kernel log, i can see the following lines:

[I]Apr  2 02:29:00 amilo kernel: [  208.364000] usb 2-3: new high speed USB device using ehci_hcd and address 8
Apr  2 02:29:00 amilo kernel: [  208.504000] usb 2-3: configuration #1 chosen from 1 choice[/I]

So it seems that the switching off and on works, but the cam isnt detected properly

---

### Post by Kevin_Jim on 2008-04-14
I have the same problem with the webcam ( and everything else that is). But I did everything by the how to of UVC still don't work. Any ideas ? I'll try something for the sound but I don't put my hopes to high.

PS: I have Ubuntu 8.04 Beta right now.

---

### Post by LordOfThePigs on 2008-05-03
I finally got the headphones and the speaker to work properly and mute properly when the headphones are plugged in. The problem was fixed in alsa at the beginning of march, so all we need to do is compile a newer version of the alsa drivers modules, and load it in the kernel.

1. Ubuntu likes to load its own modules first, so simply installing the alsa modules is not enough. First, go to your ubuntu kernel sound modules directory, and move alsa-driver to somewhere else (your home directory for example).

```

cd /lib/modules/2.6.24-16-generic/ubuntu/sound
sudo mv alsa-driver ~

```

this step is necessary to avoid the system loading the ubuntu modules before loading our new compiled alsa-module.

2. Download the following package [http://www.megaupload.com/?d=66VW79V4](http://www.megaupload.com/?d=66VW79V4) . This is a snapshot of alsa from the 5th of april 2008, compiled against the hardy kernel 2.6.24-16-generic. Now in the console navigate to the folder you downloaded the file to, and run

```
dpkg -i alsa-driver_hg20080502-1_i386.deb
```

if you don't want to install this package, or are using a different kernel version, you'll have to compile the alsa module yourself. Here are a few resources to get you started.
Alsa daily snapshots: [ftp://ftp.suse.com/pub/projects/alsa/snapshot/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/)
Intel HDA wiki page: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Sound troubleshooting wiki page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

3. Edit your /etc/modprobe.d/alsa-base file

```
sudo gedit /etc/modprobe.d/alsa-base
```

and paste the following line at the END of the file

```
options snd-hda-intel model=fujitsu-pi2515
```

4. reboot

your sound should now work as expected (it worked for me at least). 


**If something screws up:**
If something screws up at some point, you can fix it by running these 2 commands (your sound will be back to how it was before though):

```

dpkg -r alsa-driver
sudo apt-get --reinstall install linux-ubuntu-modules-`uname -r`

```

**Resources**
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3800](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3800)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3875](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3875)
[http://eriksdatadump.blogspot.com/2008/02/loading-custom-compiled-alsa-modules.html](http://eriksdatadump.blogspot.com/2008/02/loading-custom-compiled-alsa-modules.html)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by scorp123 on 2008-05-04
> **LordOfThePigs said:**
> I finally got the headphones and the speaker to work properly and mute properly when the headphones are plugged in. The problem was fixed in alsa at the beginning of march, so all we need to do is compile a newer version of the alsa drivers modules, and load it in the kernel.

1. Ubuntu likes to load its own modules first, so simply installing the alsa modules is not enough. First, go to your ubuntu kernel sound modules directory, and move alsa-driver to somewhere else (your home directory for example).

```

cd /lib/modules/2.6.24-16-generic/ubuntu/sound
sudo mv alsa-driver ~

```

this step is necessary to avoid the system loading the ubuntu modules before loading our new compiled alsa-module.  
Sorry, I did not understand the first part. Could you please explain in more details? I am asking because it seems the files you mention are not there. :confused:

---

### Post by Kevin_Jim on 2008-05-05
Does anyone know when the Alsa drivers and the webcam drivers will be on the Ubuntu repo. I don't have a problem to do stuff but when it comes to kernel modules I really prefer not to O:)

---

### Post by Hitrix on 2008-05-05
> 2. Download the following package [http://www.megaupload.com/?d=66VW79V4](http://www.megaupload.com/?d=66VW79V4) . This is a snapshot of alsa from the 5th of april 2008, compiled against the hardy kernel 2.6.24-16-generic. Now in the console navigate to the folder you downloaded the file to, and run

```
dpkg -i alsa-driver_hg20080502-1_i386.deb
```

are these drivers also avaible for amd64?

---

### Post by LordOfThePigs on 2008-05-06
> **Kevin_Jim said:**
> Does anyone know when the Alsa drivers and the webcam drivers will be on the Ubuntu repo. I don't have a problem to do stuff but when it comes to kernel modules I really prefer not to O:)

After playing around with that stuff a bit more, I've seen that the version of alsa that ubuntu uses is already supposed to contain the fix for the recent fujitsu siemens notebooks (ie: model=pi2515), but for some reason, it doesn't work. That is the source code of alsa for ubuntu already includes the patch, but fr some reason that patch doesn't work when applied to ubuntu's version of alsa, but works fine on the original alsa sources.

So the fix is actually already in the repo, but for some reason it doesn't work as it should.

[quote=scorp123]Sorry, I did not understand the first part. Could you please explain in more details? I am asking because it seems the files you mention are not there.[/quote]
As long as your ubuntu install was successful they should be there. Maybe you upgraded from Gutsy? I've read in several places that sometimes when upgrading from gutsy to hardy, the linux-ubuntu-modules package is not installed properly. Try to run the following command first and try my procedure again:
```
sudo apt-get install linux-ubuntu-modules-`uname -r`
```

[quote=Hitrix]are these drivers also avaible for amd64?[/quote]
No. I just compiled them on my machine for the generic kernel. I have no idea how I can cross-compile it for AMD64, so I'm afraid you will have to do it yourself. However, with the links in my original post, it shouldn't be too hard to figure out how to do it properly.

---

### Post by LordOfThePigs on 2008-05-06
For reference, there is already a bug filed for that particular problem (although with a slightly different fujitsu laptop model) at [https://bugs.launchpad.net/ubuntu/+bug/194866](https://bugs.launchpad.net/ubuntu/+bug/194866)

---

### Post by LordOfThePigs on 2008-05-06
after fiddling a bit more, it seems that using "model=lenovo-nb0763" instead of "model=fujitsu-pi2515" also works. And there is no need to recompile alsa.

---

### Post by Hitrix on 2008-05-06
> **LordOfThePigs said:**
> after fiddling a bit more, it seems that using "model=lenovo-nb0763" instead of "model=fujitsu-pi2515" also works. And there is no need to recompile alsa.

I tried this way... with a little sucess :)

everything worked fine expect of the mic. Everytime when I say something into it, the sound comes directly out of my headset. I tried to change the settings in the alsa mixer but that didnt fixed the problem...

can someone help me? :)

---

### Post by scorp123 on 2008-05-06
> **LordOfThePigs said:**
>  As long as your ubuntu install was successful they should be there. Maybe you upgraded from Gutsy? I've read in several places that sometimes when upgrading from gutsy to hardy, the linux-ubuntu-modules package is not installed properly. Try to run the following command first and try my procedure again:
```
sudo apt-get install linux-ubuntu-modules-`uname -r`
``` Ah OK, I see. Thanks for this hint.

---

### Post by Hitrix on 2008-05-08
can someone explain me how to get the webcam working or link me to a page where it is explained. :)

---

### Post by rafkt on 2008-05-12
I compiled alsa drivers and after that, i changed the model to "model=lenovo-nb0763", so everything worked fine :guitar: :guitar: ..(And the mic problem solved for me <<the sound comes directly out of my headset>>)..

What about webcam, is there a specific solution, to solve and this problem;;;

Also, is there any chance, for the remote control to work;;;Any ideas..

Thanks in advance..:)

---

### Post by Kevin_Jim on 2008-05-12
You only have to add "options snd-hda-intel model=lenovo-nb0763" at the end of the file. I did it with one command

```
echo "options snd-hda-intel model=lenovo-nb0763" >> | sudo tee -a /etc/modprobe.d/alsa-base
```

you can do it AND automatically reboot, I mean close everything because after the following command your PC will reboot.

```
echo "options snd-hda-intel model=lenovo-nb0763" >> | sudo tee -a /etc/modprobe.d/alsa-base | sudo reboot
```

Have fan!

PS: Please if there is someone with a hint for the webcam be welcome and share.

---

### Post by Tsab on 2008-05-13
Hi!

How about the remote controller? Anyone knows which driver should I use?

Thanks
Tsab

---

### Post by rvfh on 2008-05-18
The webcam does work. Just don't forget to activate it:
[Fn] + F7

I use Skype to place video calls and everything is fine using Kubuntu 8.04.

---

### Post by LingLing on 2008-05-23
Why doesn't it work for me then?? I'm using Ubuntu 8.04. It can't be the fact that you're using KDE instead of Gnome, can it?

Can you please tell me what your kernel log says when you're activating the cam with ALT-F7?

And also please tell me your skype version.

> **rvfh said:**
> The webcam does work. Just don't forget to activate it:
[Fn] + F7

I use Skype to place video calls and everything is fine using Kubuntu 8.04.

---

### Post by Nikos_M on 2008-06-24
> **LingLing said:**
> Why doesn't it work for me then?? I'm using Ubuntu 8.04. It can't be the fact that you're using KDE instead of Gnome, can it?

Can you please tell me what your kernel log says when you're activating the cam with ALT-F7?

And also please tell me your skype version.

At this point the web camera driver does NOT work. You ll have to wait and keep an eye on this project: [https://sourceforge.net/projects/m560x-driver/](https://sourceforge.net/projects/m560x-driver/)

You can try to compile your kernel module but the best thing that you ll accomplish at this point is to light up the camera led.

Stay tuned...

---

### Post by LingLing on 2008-06-25
Thanks Nikos
I already tried my luck earlier on with the m560x-driver but i couldn't even get the LED on. ](*,)

Guess I'll have to wait then. I just wonder why other people claim they had the cam working out of the box...

---

