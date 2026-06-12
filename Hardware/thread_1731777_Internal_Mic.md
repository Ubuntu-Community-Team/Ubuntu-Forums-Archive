---
title: "Internal Mic"
date: 2011-04-17
forum: Hardware
---

### Post by dhaitham on 2011-04-17
Hello,
I've decided to start using Ubuntu. So far everything runs smoothly except with Skype - my Internal mic isn't working with Skype and maybe further on won't work with other voice-chat softwares but it seems to work on Sound Recorder. 

On Skype Sound-Options I get PulseAudio server (local) for all sound devices and no other options. 

-I have Acer Aspire 5553G Laptop.
-Installed Ubuntu 10.10

Thanks in advance.

---

### Post by lidex on 2011-04-17
What version of skype? From ubuntu documentation:
> Selecting Microphone (input device)

Most netbooks/laptops have two input devices, one built into the casing and another one for plugging in an external microphone. In Ubuntu 10.04 (Lucid Lynx) and Skype 2.0+ you might have problems selecting the right input device. The following instructions should solve this issue:

1. Install pavucontrol, a program with with you can select audio devices

[Click here to install the pavucontrol package]("apt:pavucontrol?section=universe")

Synaptic

    Go to Applications &#8594; Add/Remove...

    Set Show: to All available applications

    Search for pavucontrol and install it. 

Or open the Terminal, and execute the following command:

    sudo apt-get install pavucontrol

2. Start Skype and initiate a test call (you can use echo123 Skype testing service).

3. Start pavucontrol while the test call is running: Press Alt-F2 and type pavucontrol, hit return

4. In pavucontrol there is a tab called Recording where you can select the input device for the application Skype

Note: Skype has to be running and Skype needs to use (i.e. make a call) Pulseaudio while you change settings with pavucontrol.



---

### Post by dhaitham on 2011-04-18
Hello,

Installed pavucontrol and tried all settings while a call was active on Skype, still no luck.

btw, my Skype's 2.2 Beta.

Thanks

---

### Post by NewToThis2011 on 2011-04-25
Hi,

same here. I removed Skype 2.2 and reinstalled 2.1, only in the latter does the trick with pavucontrol work for me.

Good luck

---

