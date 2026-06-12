---
title: "USB Microphone not working in Skype"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by alstroph on 2008-02-08
Hello, I'm completely new to Ubuntu. I installed 7.10 last night and I'm over whelmed. I have a Samson CO1U USB microphone that is plugged in and I'm trying to use Skype to make a call. I tried my internal sigmatel mic first and had no luck... but I was able to make a call out and hear the other person. When I select either Samson C01U HW: default, 0 or Samson plughw: default, 0 I can't make a call out at all. 

The only place my usb mic is working is in Audacity. This is a total bummer... Skype is my only phone and I need to call a friend before it gets too late so I don't miss this concert... :(

I thought I would add that no mics are working in sound recorder... and under system>preferemces>sound when I change the input device I get weird errors.

---

### Post by OoooMatron on 2008-02-08
install gnome alsa mixer and make sure its not muted.

---

### Post by Sabot on 2008-02-08
Try going under System > Preferences > Sound and set everything to USB audio.  There are some tests there you can try to see if you get any audio.

---

### Post by Sabot on 2008-02-09
Try this

Open a terminal and enter:

```
asoundconf list
```

This gave me the name of my sound card.  In my case it was default.  In the same terminal I entered:

```
asoundconf set-default-card default
```

Then restart your computer.

This command is key because without it I was unable to hear startup sounds and flash in firefox would not play audio through my usb headset. This command also makes skype work correctly.

---

### Post by xc3RnbFO8P on 2008-02-09
> **alstroph said:**
> Hello, I'm completely new to Ubuntu. I installed 7.10 last night and I'm over whelmed. I have a Samson CO1U USB microphone that is plugged in and I'm trying to use Skype to make a call. I tried my internal sigmatel mic first and had no luck... but I was able to make a call out and hear the other person. When I select either Samson C01U HW: default, 0 or Samson plughw: default, 0 I can't make a call out at all. 

The only place my usb mic is working is in Audacity. This is a total bummer... Skype is my only phone and I need to call a friend before it gets too late so I don't miss this concert... :(

I thought I would add that no mics are working in sound recorder... and under system>preferemces>sound when I change the input device I get weird errors.

I got the same problem, I think it is a bug.

Maybe last update.

---

### Post by aonegodman on 2008-02-13
> **Sabot said:**
> Try going under System > Preferences > Sound and set everything to USB audio.  There are some tests there you can try to see if you get any audio.

```

Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

```

When running test under sound capture I get the above error. Does anyone understand this?  :confused:

---

