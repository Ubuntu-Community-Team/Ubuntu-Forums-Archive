---
title: "Sabrent Philips7130 PCI TV Tuner/Video capture card"
date: 2008-09-22
forum: General Help
---

### Post by carl99fan on 2008-09-22
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

I have read a few threads I followed the instruction in the following thread but since the person that started it is no longer a member I started a new thread cause I have purchased one and I want it to work on my Ubuntu computer.

Please help me get this card working.

I have followed the instructions found here: [http://ubuntuforums.org/showthread.php?p=4506840#post4506840](http://ubuntuforums.org/showthread.php?p=4506840#post4506840)

ERROR: Module saa7134 does not exist in /proc/modules

---

### Post by cariboo on 2008-09-22
I had a look a the thread you linked to and the is an error in the first step:

> tep 1:

sudo nano /etc/modprobe.d/saa1734 and hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor type in the following lines pressing enter at the end of each one.

alias chr-major-81 videodev
alias chr-major-81-0 saa7134
options saa7134 card=42 tuner=43 oss=1

now press the control key (ctrl) and the "x" key at the same time, you will be asked if you want to save file: saa1734 say yes by pressing "y" key on the keyboard.

In the first line it should be saa7134 instead of saa1734. I have an MSI TV@nywhere that has the same chip set this is what my ssa7134 script looks like:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

I don't have to specify a tuner as it is detected on boot up:

```
dmesg | grep tuner
[   14.928091] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   15.009018] tda829x 2-004b: setting tuner address to 61
```

Check here:

[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

To see if your card is listed, if it is you should be able to find the card and tuner numbers.

Jim

---

### Post by carl99fan on 2008-09-22
Thanks I will start over.
this is a bit advanced for me but I need to get this card working I bought 2 of them.

---

### Post by lovinglinux on 2008-09-22
I have suffered a little bit to install my saa7134 card too, mostly because of so many "recipes".

My TV card model is not the same as yours, but since both are saa7134 I'm pretty sure this will work for you.

First install TVTime. You can find it in the Add/Remove manager or run the following command on a terminal.

```
sudo apt-get tvtime
```

Then you need to edit /etc/modprobe.d/options

Run the following command to open it with the text editor:

```
sudo gedit /etc/modprobe.d/options
```

In the editor, add the following line to the end of the file

```
options saa7134 card=42 tuner=43 alsa=1
```

Back to the terminal run: 

```
sudo modprobe saa7134 card=42 tuner=43
```

Reboot. Open TVTime through the Applications menu or by running this command:

```
tvtime
```

Configure TVTime with the OSD menu.Some important settings:

Input Configuration > Change video source: Television
Input Configuration > Television standard: NTSC, PAL-M....
Channel Management > Change Frequency table: Cable

Then do a channel scan:

Channel Management > Scan channels for signal

This should be enough to make TVTime tune some channels.

Good luck.

---

### Post by carl99fan on 2008-09-22
OK I have my security camera working and I am getting channel 2 of my cable tv.

I can not find the channel scan option at all Thanks for the help so far I am off to a good start.
is there a terminal command for channel searching?

---

### Post by lovinglinux on 2008-09-22
> **carl99fan said:**
> is there a terminal command for channel searching?

```
tvtime-scanner
```

You can type "man tvtime-scanner" for other options.

---

### Post by carl99fan on 2008-09-22
@display-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/display/.tvtime/tvtime.xml
Scanning using TV standard NTSC.
/home/display/.tvtime/stationlist.xml: No existing NTSC station list "Custom".

    No tuner found on input 1.  If you have a tuner, please
    select a different input using --input=<num>.

display@display-desktop:~$ 

???

---

### Post by carl99fan on 2008-09-22
I figured it out!!!
Wooo Hooooo Thank you!

May I ask how to capture video now?

I will read your guides as I wait.

---

### Post by lovinglinux on 2008-09-22
> **carl99fan said:**
> I figured it out!!!
Wooo Hooooo Thank you!

May I ask how to capture video now?

I will read your guides as I wait.

Oh yes, with the tutorials on my sig you will be able to record, play, pause, go to the bathroom, make some :popcorn:, than come back and resume the TV... :)

I do recommend starting with Simple PVR and Simple TV Recorder tutorials, then if you like the idea of using Fireox as media center go for it, but it isn't necessary to just record/pause/resume TV.

---

### Post by joni8.10 on 2008-12-01
I have this same video capture card, except it is the usb2 version of it. Just wondering if there was some work around similar to the one posted here, except for USB2 connection, instead of video card.
I'm sure it's the same product, just a different way of connecting it to the computer.:?:

---

### Post by joni8.10 on 2010-03-27
> **lovinglinux said:**
> Oh yes, with the tutorials on my sig you will be able to record, play, pause, go to the bathroom, make some :popcorn:, than come back and resume the TV... :)

I do recommend starting with Simple PVR and Simple TV Recorder tutorials, then if you like the idea of using Fireox as media center go for it, but it isn't necessary to just record/pause/resume TV.

Could you tell me how to get this thing to record please, or provide a link to where I can learn how? I am currently using ubuntu dapper. Thanks.

---

### Post by pdlethbridge on 2010-05-08
I have tried both 9.10 and 10.04 but I could not get my TV card to work on either one. I followed the directions here and it works with 9.04. Any ideas? TIA Paul

---

### Post by pdlethbridge on 2010-05-18
bump

---

### Post by buster3 on 2010-06-07
BUMP

I too am using Lucid! The Sabrent 7134 card was working fine in intrepid BUT will NOT work in LUCID!
can anyone help us?!?

---

