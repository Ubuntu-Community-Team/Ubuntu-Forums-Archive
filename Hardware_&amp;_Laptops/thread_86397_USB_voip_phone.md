---
title: "USB voip phone"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by Matchless on 2005-11-05
Hi,
   Can anyone point me in any direction. I have a USB voip phone that works well on Skype and for which no drivers are required on Windows, as they are built in. Skype is working on my Breezy and I would like to get this phone working. Is it possible?

---

### Post by Ruler on 2006-05-02
Hey, 

Was just wondering if you ever solved this one? I am trying to achieve the same with the Cyberphone K, and it is made by the company voipvoice.com

Any pointers in the right direction would be great.

Cheers

---

### Post by lonetree on 2006-05-12
Apparently there are still no solution for this, the driver is built for FC, and even the manufacturer is not developing new drivers, perhaps all should start writing to them andtell them we LINUX (UBUNTU) users are really in need for the drivers.

I hope this would work soon. Was just wondering why after so many years linux supports for devices are still uncommon, probably this is due to the way each distro watch which make them confuse. Let;s just hope that one day, all linux distro will have a common way of working, I believe by then, more people will be willing to accept LINUX.

---

### Post by Tony.Mercury on 2006-11-22
Well, I know this is an old thread, but..  I emailed the manufacturers of the Cyberphone-W, and they've told me they ain't going to develop drivers for linux, which I'm very disappointed to hear..

---

### Post by justin whitaker on 2006-11-22
Did you try alien to install the rpms (I assume that FC meant Fedora Core). That could work.

---

### Post by lonetree on 2006-11-22
no justin. that is not going to work.

thanks though

---

### Post by mr.thraz on 2007-07-02
turbolinux also supported the cyberphone k's dial pad, i suspect its just a h.i.d. string we would have to put into
xorg. 
any got an old copy of turbolinux or fc to see how there xorg is setup.

---

### Post by bobkat60 on 2007-07-03
Hi ,  dont know if this one wll help you , I'm trying to install @V Traveller Voip usb phone. the best so far I've got is  Synaptic Package 'ekiga' found under search- voip 
It's got the phone usable, but the buttons don't work on the phone I still have to double click on  'Contact ' in skype.. Good Luck. Bob

---

### Post by _Petya_ on 2007-07-16
Hi!

I'd like to use my UP-90 USB phone: [http://www.3-speech.com/UP90.html](http://www.3-speech.com/UP90.html)

with Ubuntu. lsusb says it's a

ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter

I can use it as a soudcard for Ekiga, but dialling doesn't work. Can I make it work under Ekiga or any other SIP client?

Can anyone help me?

Petya

---

### Post by SilverWave on 2007-08-30
Just in case anyone else is trying to set up a cyberphone w with skype this is how I did it:
Just the basic phone works I cant get the keypad working, just the phone's built in soundcard.

Go to skype  > Options  > Sound Devices
Sound In: VoIPVoice USB Phone (hw:Phone,0)
Sound Out: VoIPVoice USB Phone (hw:Phone,0)
Ringing: I left this at the default (in my case that was the pc speakers).

The following infomation is based on this post:
[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg12838.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg12838.html)
( I recommend you have a look at if so you can see the expected output of the following commands)

This next command will tell you if the usb phone is working:
cat /proc/bus/usb/devices

This next command reports the soundcard number in the usb phone (input):
arecord -l

This next command reports the soundcard number in the usb phone (output):
aplay -l

This next command lets you control the volume of the phone also its bass, treble etc.
(use the arrow Keys and tab etc.).
alsamixer -c 1

(This assumes that the previous commands indicated that the card in the usb phone was card1).

---

### Post by YannickDefais on 2007-09-01
Hi,

For Linux, we have this:
[http://wiki.ekiga.org/index.php/Controling_Ekiga_using_an_USB_phone](http://wiki.ekiga.org/index.php/Controling_Ekiga_using_an_USB_phone)

I don't know how far the development has gone.

Regards,
Yannick

---

### Post by bornagainpenguin on 2008-02-09
/BUMPing this back to the top of the page...

I'm downloading TurboLinux 10 Desktop now.  Planning to install the thing and see if it gets my Cyberphone K (voipvoice.com) working with dial pad and all in Skype.  If it finds everything appropriately, can anyone here tell me what to look for in order to get everything working back on Ubuntu?  Assuming there's an English installer, and I can figure the thing out...

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-02-13
/BUMP

I have the Fuji trial version of TurboLinux downloaded--the first one I found was an update cd which required the original (unavailable) discs to be inserted before continuing.  The Fuji version is newer but only lasts 30 days.  Could someone here please tell me what to look for so I can install it, grab the data output and we can add Cyberphone K support to Ubuntu?  Also, is this even the right section for this thread?

--bornagainpenguin

---

### Post by bornagainpenguin on 2008-02-21
/BU---ahhh whatever. :(

It seems like either A) I'm the only one with a Cyberphone K, B) No one cares, or C) No one has a clue...

Sad.  Maybe I should start a new thread?
 
--bornagainpenguin

---

### Post by MichaelSM on 2008-02-24
bornagainpenguin don't despair .

I don't know if this helps, but ..

From trawling and downloading all sorts of stuff I have a working (?) cordless voip handset insofar as it acts simply as a usb soundcard scenario ie. like a radio headset. So when I'm using Skype it works (badly) llke a headphone/mike setup.

Apparently most of the voip phones use a similar chipset ...hmmm

And a PC thinks the keypad on the phone is a usb keyboard ...

Sort of.

So there's one major issue.

Which is to get the usb handset to communicate with Skype on the PC not just as a sound gadget, but which interacts via its LCD screen as a linked device which parallels through its keypad the functions usually accessed by mouse clicks on the PC Skype window.

The bad news is that it can't be done at the moment.

The good news is that it will be do-able soon. Such is the tech world.

Just be patient.

I've spent many hours on this.

Mike.

---

### Post by imhavoc on 2008-02-24
I got in some of the US Robotics Mini USB handsets for some Windows machines at work. The first thing I did, of course, was plug one of them into my Linux notebook to see if (maybe, just maybe) it would work.... no joy.

The device showed up correctly with lsusb, but I was not able to send audio to it from the command line. I didn't have much time to mess with it. if the handsets work out for us, we'll deploying them throughout the organization, so I'll grab a spare to experiment with. The phone isn't much to write about, but it's functional, small and I picked them up for ~$20.00 each, so it's worth spending some time on.

---

