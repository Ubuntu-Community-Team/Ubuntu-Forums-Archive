---
title: "no voice"
date: 2009-02-12
forum: Hardware
---

### Post by shaygen on 2009-02-12
I have a dell vostro and I dont hear  no voice.
this are the detaiks
```
dell-desktop             
    description: Portable Computer
    product: Vostro A860
    vendor: Dell Inc.
    serial: 77NY6H1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3700-104E-8059-B7C04F364831
  *-core
       description: Motherboard
       product: 0Y487G
       vendor: Dell Inc.
       physical id: 0
       serial: .77NY6H1.CN486438B72674.
```

when i try ti di something with the voice the coputer says

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.
```

the answer for lspci | grep Audio is

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

what shell i do

---

### Post by donkyhotay on 2009-02-12
What do you mean by 'no voice'? Do you not have any sound at all or do you just not hear someone elses voice in a VOIP program such as skype?

---

### Post by shaygen on 2009-02-12
I dont have any voice at all

---

### Post by shaygen on 2009-02-12
In the dell sute they told me to install a bios driver naming a860a02.bin
how do I do this?

---

### Post by donkyhotay on 2009-02-12
> **shaygen said:**
> I dont have any voice at all

Umm... so do you mean you have no sound then? This really needs clarification before I can help. I don't know if english is your primary language or not but there is a big difference between 'no voice' (which doesn't make much sense in regards to computers) and 'no sound' (which does make sense). All voices are sounds but not all sounds are voices. A voice is a sound a person makes while talking, a sound is simply something someone hears. While a computer often makes sounds it very rarely is considered to have a 'voice' except in cases of a program that transmits or produces audible speech.

---

### Post by shaygen on 2009-02-13
English is not my primary language' and I dont have a sound. I cant hear anything.
what can i do?
how can I install a bios driver?

---

