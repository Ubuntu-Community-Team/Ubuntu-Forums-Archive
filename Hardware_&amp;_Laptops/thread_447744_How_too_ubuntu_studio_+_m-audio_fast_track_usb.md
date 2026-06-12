---
title: "How too ubuntu studio + m-audio fast track usb"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by barbe-et-hache on 2007-05-18
This will explain how I did to make my m-audio fast track usb work with my built in sound card on ubuntu studio.

My sound cards are : 
[LIST]
[*]hda-intel with conexant chip
[*]m-audio fast track usb
[/LIST]

[COLOR="Red"]
I have a built in sound card that use the driver **hda-intel** from alsa, the module is called **snd-hda-intel.** Please replace those names by the correct one for your sound card.
The commands *lspci* *lsmod | grep snd* and the [_alsa web_ ]("http://www.alsa-project.org")site may help you.

If you are a feisty user, to use your sound card with the best results (for recording), please install the low latency kernel.

[/COLOR]

To see if your card is recognized by your alsa version, try the command 
**$ cat /proc/asound/cards**
it will return the recognized sound card. If your usb device is not in the list, you may have to build alsa from sources, else proceed to **configuring jack**.

[FONT="Arial Black"]ALSA[/FONT]
In my case, I had to build alsa from source because the conexant chip is better supported with the last version. Download 
[LIST]
[*]alsa-driver
[*]alsa-lib
[*]alsa-utils
[/LIST]
from the [_alsa website_]("http://www.alsa-project.org").
untar them with the command 
**$ tax -xf alsa-driver-*version* && tax -xf alsa-lib-*version* && tax -xf alsa-utils-*version* **
Build the driver : 
**$ sudo apt-get install build-essential**
**$ cd alsa-driver***
**$ ./configure --with-cards=hda-intel,usb-audio --with-sequencer=yes**
**$ make**
**$ sudo make install**
Build the lib
**$ cd ../alsa-lib***
**$ ./configure && make && sudo make install**
Build the utilis
**$ cd ../alsa-utils***
**$ ./configure && make && sudo make install**
reboot and check if your both sound cards are recognized by your system
**$ cat /proc/asound/cards**

[FONT="Arial Black"]Configuring Jack[/FONT]
Right now you have your laptop sound card as the default sound card. We will see in the next section how to correct this. Lets check if everything is alright.
Launch jack 
**$ qjackctl **
or select JACK control in the *sound & video* menu.
launch the setup in jack and configure jack : 
[LIST]
[*]select **Realtime**
[*]**Frames/Period** 128
[*]**Interface** Fast Track
[*]**intput device** Fast track
[/LIST]
Launch the server and open the *Messages* window. If everything works fine (no xrun), you can test the output with hydrogen for instance, and the input by recording you favorite instrument with ardour. 

Everything okay? Let's make this sound card the default sound card.

[FONT="Arial Black"]Fast Track as default[/FONT]

open the texte file /etc/modprobe.d/alsa-base
**$ sudo gedit  /etc/modprobe.d/alsa-base**
and replace the line 
**options snd-usb-audio index=-2**
with 
**#options snd-usb-audio index=-2**

create a file called /etc/modprobe.d/sound
**$ sudo gedit /etc/modprobe.d/sound**
and put the following lines in it
**options snd-usb-audio index=0**
**options snd-hda-intel index=1**


Lets play :guitar:!!

---

### Post by kangol69 on 2007-05-20
Thanks Again.

---

### Post by Drophere on 2007-05-20
> **barbe-et-hache said:**
> Launch the server and open the *Messages* window. If everything works fine (no xrun), you can test the output with hydrogen for instance, and the input by recording you favorite instrument with ardour.

Thanks for posting these details on how you got things working on your system.

I followed your instructions and my card is recognised, but I can't find a Qjackctl combination that gets rid of xruns. Do you have any suggestions on how to get rid of xruns?

Cheers,

Malcolm.

---

### Post by barbe-et-hache on 2007-05-21
Could you tell me more about your configuration (sound card, cpu, and kernel) ? I could help you to get the lowest latency possible.  I will also post a How to get the lowest latency with ubuntu feisty, I could test it on you first :).

Basicaly, to get ride of xruns, you need to increase the *Frames/Period* until there is no more xruns. If your sound card is not well supported, you may continu to get xruns wathever the jack config you use. I had the problem with an Audiophile usb from m-audio.

---

### Post by Drophere on 2007-05-21
> **barbe-et-hache said:**
> Could you tell me more about your configuration (sound card, cpu, and kernel) ? I could help you to get the lowest latency possible.  I will also post a How to get the lowest latency with ubuntu feisty, I could test it on you first :)

OK. :)

Here's the output of **$ cat /proc/asound/cards**:

 0 [V8235          ]: VIA8233 - VIA 8235
                               VIA 8235 with ALC650D at 0xd400, irq 19
 1 [Speedio        ]: USB-Audio - Speedio
                                Novation EMS Speedio at usb-0000:00:10.2-2, full speed

It's the Novation that I'd like to get to work with Qjackctl.

The Novation is not on the list of supported cards at alsa-project, but it gets identified correctly by the OS. If I go to **System > Preferences > Sound **I can see "USB Audio" as an option for "Sound Events" and the other preferences, but it does not appear as a device under "Default Mixer Tracks". If I try the "Test" button with USB Audio selected, audio gets sent to the Novation but it sounds like it's playing back at the wrong sample rate. The pitch is about half what it is when I "Test" using the VIA.

In Qjackctl I see both "hw 1: Speedio" and "hw 1,0: USB Audio".

If I select USB Audio as the playback device in Audacity, the program terminates as soon as I press play. 

I'm not sure if this device can be made to work with Ubuntu Studio, but I'm happy to test things if there's a possibility.

Cheers,

Malcolm.

---

### Post by barbe-et-hache on 2007-05-22
Hi Drophere,

I still don't now if you are using a low latency kernel. Are you using Ubuntu studio?
Tell me which version of ubuntu you are using.

---

### Post by Drophere on 2007-05-22
Ubuntu Studio.

---

### Post by barbe-et-hache on 2007-05-23
Guys from Ubuntu Studio prepared a new kernel (a real time kernel). I tried it yesterday and it solved all my problems with xruns and Jack Server. I suggest you give it a try. You can find information and the kernel on [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=441366") thread.

---

