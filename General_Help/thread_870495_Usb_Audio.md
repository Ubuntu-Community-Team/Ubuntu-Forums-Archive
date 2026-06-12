---
title: "Usb Audio"
date: 2008-07-25
forum: General Help
---

### Post by bfsilas on 2008-07-25
Properly going to hit myself because this is a newbiest question in the world

I've used Ubuntu in the past quite abit but i always gave up and went back to a win32 OS because it's really easy to use =(

I want to use ubuntu but i always run into a problem and i can't fix it

My problem is this:

I can't use my USB Audio, i use it all the time, it's my only audio device i have a planatronics headset which is picked up as "USB Audio Device" when i right click the sound icon and go to properties, though nothing comes out of the speakers :(

When i unplug the headset and plug it into a diffrent USB Slot it plays the welcome message so it is working but when i select it nothing plays, i'm playing stuff through almost every media player and nothing works i've been using VLC mostly because it has all the codecs

Why won't it work :( it's selected and it says PCM which i'm guessing is the main output thing so what am i doing wrong =( is it a hardware issue? am i doing it right? help would be so appreciated

Edit (printscreen):

[IMG]http://openservltd.com:7331/temp/Screenshot-Volume%20Control%20Preferences.png[/IMG]
[IMG]http://openservltd.com:7331/temp/usbaudio.png[/IMG]

---

### Post by Taxman415a on 2008-07-25
> **bfsilas said:**
> I've used Ubuntu in the past quite abit but i always gave up and went back to a win32 OS because it's really easy to use =(

I want to use ubuntu but i always run into a problem and i can't fix it
Nowdays this is unfortunately usually a case of hardware makers not releasing enough information about their devices so that free drivers can be written for them when the manufacturer doesn't release linux drivers.

> 
When i unplug the headset and plug it into a diffrent USB Slot it plays the welcome message so it is working but when i select it nothing plays, 
What welcome message do you get? The hardware's welcome message or Ubuntu's?

> 
Why won't it work :( it's selected and it says PCM which i'm guessing is the main output thing so what am i doing wrong =( is it a hardware issue? am i doing it right? help would be so appreciated
What that output looks like is the device is being recognized in a generic sense but may not have specific drivers for it.

Can you give us the specific model number for the hardware and the output of ```
lsusb
``` run on the command line? That way we/you can do a google search to find out if this specific device is supported under linux.

---

### Post by bfsilas on 2008-07-25
Thanks for quick reply, in answer to your questions it's the ubuntu's welcome message, when you login usually

> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 009: ID 047f:c001 Plantronics, Inc. 
Bus 001 Device 008: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 001 Device 007: ID 046d:c51a Logitech, Inc. 
Bus 001 Device 006: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 001 Device 001: ID 0000:0000 

I've done the prefrences - sound and set them all to usb-audio and the test button works, and also kills your ears if you're not expecting it :|


i guess the "ID 047f:c001 Plantronics, Inc. " is the case, i ran a google search, All in French unfortunately i don't speak it so i can't find the answer fromt here

---

### Post by bfsilas on 2008-07-25
bump =(

---

### Post by bfsilas on 2008-07-25
Sorted :D

needed the codecs, i though that VLC installed them obviously not =(

Edit:

Okay so sound works but not through alot of stuff, firefox doesn't output any sound, nor does ubuntu its self. not even amarok 

Works only on

Rthymbox and Movie player

All i want to do is get the sound to work but it has so much difficult getting it right :(

---

### Post by Taxman415a on 2008-07-26
Well that's good news, the hardware seems supported. I'm a bit confused at how you're trying to go about producing sound output. If all you needed was codecs, I don't get what isn't working. Have you read: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ?
If you've already done that, what specifically don't you get sound from?

Try opening the media files in the Examples subdirectory in your home directory in various programs. Those do have the codecs installed and if they work you know it's a codec problem.

As for identifying your sound device the ID 047f:c001 numerical id part isn't terribly useful finding info on the device. Doesn't it say anything more on it that will help find more info about it? If not, since from the output you gave above the device is bus 1 device 9, try this to see if it gives up any more useful info: ```
sudo lsusb -v -s 1:9
``` Adjust the numbers as needed if you moved the device.

---

### Post by mbsullivan on 2008-07-26
> Okay so sound works but not through alot of stuff, firefox doesn't output any sound, nor does ubuntu its self. not even amarok 

Perhaps another audio device is grabbing the highest priority, such that all of your applications are playing through it (even though no speakers, etc) are connected.

What are the contents of **/etc/modprobe.d/alsa-base** ???

Make sure that snd-usb-audio has an index of 0, and that it's the [COLOR="Red"]**only one**[/COLOR]. So, you should see a line towards the bottom of the file that looks like:

```
options snd-usb-audio index=0
```

Furthermore, all other indices should be negative (if you want it to be the highest priority device).

Mike

PS: Sorry for only using configuration files / command line commands... I don't have Ubuntu installed, per se (just server).

---

### Post by Bionic Apple on 2008-07-26
This is mostly a shot in the dark, but this might work.  I had a similar problem and there is two ways you can solve this.  However, if some common Gnome applications work and others don't, then this probably won't help you.

**Quick Number One**: Install *asoundconf-gtk* from Synaptic.  Go to System -> Preferences -> Default Sound Card.  Simply select USB Audio/Headset/Whatever.

**Good Number Two**:  Install full PulseAudio.  To do this, install *padevchooser* and every package that is required to come with it.  Go to Applications -> Sound & Video -> PulseAudio Device Chooser.  Now left-click on the cord in the top right of your screen.  Click on preferences and make sure it starts on login.  Go back to the menu for the cord, then click on C*onfigure Local Sound Server*.  Enable everything in *Network Access*, but the *Don't Require Authentication* option.  Now go back to the cord menu and check if it says *user*@*computer* under default server, then click the radio button if it does.  If it doesn't, then re-login or restart.  Now you must go to *Default Sink* (speakers) and *Default Source* (mic) and click on the device you want on default from the radio buttons.  

Now, your applications should play through your headset.  If a certain application doesn't, go to the cord menu and click on *Volume Control*.  Right-click on the application stream that isn't making sound, go to *Move Stream*, then click on the headset.


Hope that works for you!  I prefer the PulseAudio way because it is stable and can do custom things for all of your sounds.  I am surprised Ubuntu didn't come with full PulseAudio.  However, if number two is too daunting, then go ahead and do number one for a quick fix.

---

### Post by mbsullivan on 2008-07-26
I agree that PulseAudio may help your current situation.

> I am surprised Ubuntu didn't come with full PulseAudio

I think that's the way things are moving... PulseAudio is still experimental, but it seems solid. So long as OSS4 doesn't get a huge following, I'm hopeful that we'll keep seeing more of it in Ubuntu.

Mike

---

### Post by bfsilas on 2008-07-26
Okay sorry i was asleep and then at work i've returned and about to try everything

> Have you read: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ?
If you've already done that, what specifically don't you get sound from?

i ran it and got

```
ubuntu-restricted-extras is already the newest version.

```

So that's bad right i have it already so =(

> what specifically don't you get sound from?

Every Application Firefox, Frets on fire, everything except Rthymbox and Movie player

> Try opening the media files in the Examples subdirectory

If i hover over them they play which is a cool feature (thank you ubuntu) opening them in rythmbox and movie player works but nothing else... (though it played in amarok for about 1 second and then stopped -.-

> As for identifying your sound device the ID 047f:c001 numerical id part isn't terribly useful finding info on the device. Doesn't it say anything more on it that will help find more info about it? If not, since from the output you gave above the device is bus 1 device 9, try this to see if it gives up any more useful info:

I ran the code and got this, i don't know what to make out of it

```
Bus 001 Device 009: ID 047f:c001 Plantronics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x047f Plantronics, Inc.
  idProduct          0xc001 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          224
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0 
      iInterface              0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           71
        bInCollection           2
        baInterfaceNr( 0)       1
        baInterfaceNr( 1)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             2
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0001
          Left Front (L)
        iChannelNames           0 
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             6
        wTerminalType      0x0301 Speaker
        bAssocTerminal          0
        bSourceID               9
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             7
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID              10
        iTerminal               0 
      AudioControl Interface Descriptor:
        bLength                10
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 9
        bSourceID               1
        bControlSize            1
        bmaControls( 0)      0x01
          Mute
        bmaControls( 1)      0x02
          Volume
        bmaControls( 2)      0x02
          Volume
        iFeature                0 
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                10
        bSourceID               2
        bControlSize            1
        bmaControls( 0)      0x43
          Mute
          Volume
          Automatic Gain
        bmaControls( 1)      0x00
        iFeature                0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           1
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             2
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        48000
        tSamFreq[ 1]        44100
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            9
          Transfer Type            Isochronous
          Synch Type               Adaptive
          Usage Type               Data
        wMaxPacketSize     0x00c8  1x 200 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         1 Milliseconds
          wLockDelay              1 Milliseconds
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           7
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                14
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            2 Discrete
        tSamFreq[ 0]        48000
        tSamFreq[ 1]        44100
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0064  1x 100 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x01
            Sampling Frequency
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              32
Device Status:     0x0000
  (Bus Powered)

```

> What are the contents of /etc/modprobe.d/alsa-base ???

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

> Make sure that snd-usb-audio has an index of 0, and that it's the only one

Stated above it's not i've edited the file and i'm going to reboot after trying some more stuff in this thread

> 
Quick Number One: Install asoundconf-gtk from Synaptic. Go to System -> Preferences -> Default Sound Card. Simply select USB Audio/Headset/Whatever.

You sir win, it seems to be working i've only tried firefox so far though... WAIT!.... =( amarok didn't play the jazz ogg file... frets on fire sound works :D! VLC doesn't work either... what the ****? so most of the stuff is fixed but a small few still not -.-

> Good Number Two: Install full PulseAudio. To do this, install padevchooser and every package that is required to come with it. Go to Applications -> Sound & Video -> PulseAudio Device Chooser. Now left-click on the cord in the top right of your screen. Click on preferences and make sure it starts on login. Go back to the menu for the cord, then click on Configure Local Sound Server. Enable everything in Network Access, but the Don't Require Authentication option. Now go back to the cord menu and check if it says user@computer under default server, then click the radio button if it does. If it doesn't, then re-login or restart. Now you must go to Default Sink (speakers) and Default Source (mic) and click on the device you want on default from the radio buttons. 

It doesn't say user@computer or silas@silas-pc but i'll restart and check it out

Overall it's looking good i'll check it out in a sec


Edit:

Well alot of stuff now works but VLC and Amarok still arn't working which means other app's using the same setup for audio playback won't work so i guess it would be nice to resolve everything, i don't understand why it would do that

Rebooting all the noises that should be there are, firefox is now working and everything but vlc and amarok are not... The user@computer still says "No Network Device Found"

---

