---
title: "Looking for an Jammy Jellyfish and beyond 5.1 compatible sound system."
date: 2024-08-26
forum: Hardware
---

### Post by falloutboy2 on 2024-08-26
I am looking for a 5.1 Sound card or USB DAC which is known to be fully compatible with Ubuntu 24.04 and beyond.

It needs to be actual 5.1 with 3 audio jacks along the lines of what the old Creative cards used to do and not do any
of this running speakers over microphone tomfoolery.

I would be grateful for any recommendations be it a PCIe card or a USB DAC system.

EDIT: Just realized i'm running Noble Numbat and that is what I am looking for compatibility with and beyond DOH!

---

### Post by Shibblet on 2024-08-26
> **falloutboy2 said:**
> I am looking for a 5.1 Sound card or USB DAC which is known to be fully compatible with Ubuntu 24.04 and beyond.

It needs to be actual 5.1 with 3 audio jacks along the lines of what the old Creative cards used to do and not do any
of this running speakers over microphone tomfoolery.

You don't want to run an HDMI, OPT(SPDIF), or Coax(RCA) jack into an Amplifier to power your speakers, correct?  This would be the best way to accomplish 5.1/7.1 (etc), because the amplifier not only powers the speakers, but the receiver unit decodes the digital audio data.

However, if you are looking for a "non-powered/non-amplified" device, check this out, Star Tech:
[https://www.amazon.com/StarTech-com-7-1-USB-Sound-Card/dp/B002LM0U2S/ref=sr_1_6_sspa?crid=28N7LO8WMX2NX&dib=eyJ2IjoiMSJ9.133ykvUUODOsoJfXMpX13Z3P8gZTMKawHH8eXSoLV85ZPt1Rzxl8jjJjPXhHtZDC_e88_5YpGQMsF9ROq_R8bw.zUu63Q_klTiVbwDG_MDIkIzGNbH7pJyjLLvE7iheGmU&dib_tag=se&keywords=star+tech+7.1&qid=1724703084&sprefix=star+tech+7.%2Caps%2C236&sr=8-6-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9idGY&psc=1]("https://www.amazon.com/StarTech-com-7-1-USB-Sound-Card/dp/B002LM0U2S/ref=sr_1_6_sspa?crid=28N7LO8WMX2NX&dib=eyJ2IjoiMSJ9.133ykvUUODOsoJfXMpX13Z3P8gZTMKawHH8eXSoLV85ZPt1Rzxl8jjJjPXhHtZDC_e88_5YpGQMsF9ROq_R8bw.zUu63Q_klTiVbwDG_MDIkIzGNbH7pJyjLLvE7iheGmU&dib_tag=se&keywords=star+tech+7.1&qid=1724703084&sprefix=star+tech+7.%2Caps%2C236&sr=8-6-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9idGY&psc=1")

---

### Post by falloutboy2 on 2024-08-26
Thanks for the reply, something like that would be exactly what I am looking for, do you use one of these under ubuntu 24.04?

---

### Post by Shibblet on 2024-08-26
I do not, but the reviews state that it is Ubuntu compatible.

---

### Post by TheFu on 2024-08-26
> **falloutboy2 said:**
> Thanks for the reply, something like that would be exactly what I am looking for, do you use one of these under ubuntu 24.04?

So, I don't have any 5.1 capable systems with 24.04, but I did test, just now, a number of different test files that I found here on my 20.04 system using on-board audio to 5.1 speakers.  The speakers plug into the back of the B450 motherboard using at least 3, perhaps 5 little colored jacks, just like they did with my SB Live 5.1 cards 20 yrs ago.  I didn't do anything special, except turn off the speaker's built in "matrix mode" which better handles stereo audio. The "Matrix mode" is a toggle ON the center speaker control along with the power button, treble, bass. It doesn't have any digital connection to any computer at all. Purely audio with self-powered speakers.

Anyway, here are the test files: [https://drive.google.com/drive/folders/1JxmeedtAtgmoafXv9rroiDOS2vEX7N4b](https://drive.google.com/drive/folders/1JxmeedtAtgmoafXv9rroiDOS2vEX7N4b) google found those on a redit.

I pulled these down, and got the following results:
[LIST]
[*]AAC_5.1.mp4  - Worked as expected. All channels were where expected.
[*]Dolby_Digital_AC-3_5.1.mp4     - Worked as expected. All channels were where expected.
[*]Dolby_Atmos_E-AC-3_5.1.2.mp4  - Worked as expected. All channels were where expected. The duck flying around the room with the location matching what my ears here was great.  They simulated left and right ceiling speakers using the front/rear speakers together. That worked well too.
[*]DTS_5.1.wav     - Worked as expected. All channels were where expected.
[*]FLAC_5.1.flac   - Worked as expected. All channels were where expected.
[/LIST]

Just to be clear, the subwoofer worked each time as well.

For playback, I used **mpv** from a terminal. That's how I roll. ;)
There were many other test files available. I was happy to verify that my 5.1 surround sound was working.  The speakers are from around 2000 - they came THX certified, though I think without a THX Certified tech setting everything up, that doesn't mean so much. I had more money than brains back then, it seems.

Here's the hardware information, if it matters:
```
$ inxi -Axx
Audio:     Device-1: AMD vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 0a:00.1  chip ID: 1002:1637 
           **Device-2: AMD Family 17h HD Audio** vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 0a:00.6 chip ID: 1022:15e3 
           Sound Server: ALSA v: k5.15.0-119-generic 
```
It is the built-in audio hardware from an Asus B450 motherboard.  If any of my systems had normal PCI slots anymore, I'd probably still be using those SB Live 5.1 cards.  They were great, standard and "just worked" with everything.  I probably have 2 of them around here somewhere.  Think I paid about $25 for each.

For movie playback, I use a raspberry pi v4 connected to an old receiver going through an HDMI -to- TOSLINK converter.  That does 5.1 too.  When I transcode the source media, I grab all the audio tracks and convert them into vorbis audio with the same number of channels. Also grab all the subtitles/captions, then put everything into MKV containers.  I'm saddened by how many great movies only have stereo audio in their DVDs.  I need to remember that 2001 was the first movie that used Stereo audio in 1968. It wasn't all that popular until the mid-1970s.  These days, the audio can be 50% of the movie for movies that aren't just talking.

I'd bet it will work with 24.04 if I ever move to that OS.  I do have a laptop with Mint 22 on it (based on 24.04), but it only has 5.1 capability over HDMI and I haven't ever connected any HDMI screen to it. The laptop is very new to me and doesn't meet your needs for having those 4+ colored audio jacks anyway.

Hopefully, the test files will be useful to you at least.

---

### Post by falloutboy2 on 2024-08-26
> **TheFu said:**
> So, I don't have any 5.1 capable systems with 24.04, but I did test, just now, a number of different test files that I found here on my 20.04 system using on-board audio to 5.1 speakers.  The speakers plug into the back of the B450 motherboard using at least 3, perhaps 5 little colored jacks, just like they did with my SB Live 5.1 cards 20 yrs ago.  I didn't do anything special, except turn off the speaker's built in "matrix mode" which better handles stereo audio. The "Matrix mode" is a toggle ON the center speaker control along with the power button, treble, bass. It doesn't have any digital connection to any computer at all. Purely audio with self-powered speakers.


Yup that is all good but my board is a Supermicro H12SSL-i running an Epic 7c13, this board has no on board audio chip because it was originally made to be a data center server and they just don't require sound. I've been able to give it plenty of USB from USB 2 up to 3.1 Rev 2 and USBC but at the moment sound is something I don't have and is sort of a requirement for video editing, I tend to edit all my stuff in 5.1 so that I can play it back on my HT system.

Thanks for the response though.

---

### Post by bobunderwood99 on 2024-08-28
Try posting your query at [https://linuxmusicians.com/](https://linuxmusicians.com/) 

Look at either the Focusrite Scarlett 4i4
[https://us.focusrite.com/products/scarlett-4i4-3rd-gen](https://us.focusrite.com/products/scarlett-4i4-3rd-gen) 
[https://github.com/geoffreybennett](https://github.com/geoffreybennett) 

or the Behringer UMC204HD
[https://www.behringer.com/product.html?modelCode=0805-AAS](https://www.behringer.com/product.html?modelCode=0805-AAS) 
[https://community.musictribe.com/kba/article/KA-02974/Behringer](https://community.musictribe.com/kba/article/KA-02974/Behringer) 

I own neither of these devices.

---

