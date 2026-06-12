---
title: "Headphone Jack Sense control missing"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by Manannon on 2006-09-17
Hi there. I have been trying to get my laptop's internal speakers to turn off when I plug in headphones. This isn't working. Most of the advice on the internet says to enable "headphone jack sense", however Alsa doesn't provide me with this option. Is there some configuration setting that will enable it, or otherwise allow me to control the headphone and internal speaker volumes separately?

Specs:
Laptop: HP Pavilion dv2000 series
Distro: Kubuntu 6.06
Kernel: Stock 2.6.15-23-386 (also tried with 2.6.17 from Edgy)
Alsa: Currently 1.0.13rc2 (also tried 1.0.12 and the stock 1.0.10)
Audio: Intel 82801G (ICH7 family)

Output of amixer contents:
numid=4,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=5,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=30,step=0
  : values=22,22
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=6,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=227,227
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=2,iface=MIXER,name='Line Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=14,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=1.50dB,mute=0
numid=3,iface=MIXER,name='Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=14,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=1.50dB,mute=0
numid=1,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Line'
  ; Item #1 'Mic'
  : values=0

Thanks in advance...

---

### Post by billflu on 2006-10-15
I am having the same problem with the same model laptop, although I don't think this problem is limited to this laptop.

---

### Post by Manannon on 2006-10-16
I eventually found that the chip is by Conexant Systems, who do not release specs, meaning that ALSA isn't able to support it properly. :|

To solve it I went and bought a small USB soundcard. Not quite ideal but it does the job.

---

### Post by billflu on 2006-10-16
Ok, thank you. I'll stop pouring hours into trying to fix this problem now.

What usb soundcard did you get? I was thinking about buying something like this and hopefully it will work.
[http://www.newegg.com/Product/Product.asp?Item=N82E16829612001](http://www.newegg.com/Product/Product.asp?Item=N82E16829612001)

**EDIT**: Ok, I just purchased one of the [ugly green usb audio adapters](http://search.ebay.com/usb-audio-green) off of ebay. (It was <$10 shipped and insured from Hong Kong) I saw that it worked with Linux in this article.
[http://devices.natetrue.com/musicap/](http://devices.natetrue.com/musicap/)

---

### Post by Manannon on 2006-10-17
I just bought a cheap one off eBay too - works great and is better looking than the one you linked to :p 

To make it the default card I edited /etc/modprobe.d/alsa-base and added

options snd-usb-audio index=0
options snd-hda-intel index=1

This has caused the slight problem that if the USB device isn't connected there is no default sound card, but it isn't annoying enough for me to bother fixing right now. 

Oh, and don't disconnect the device while you're using it to play music... some applications get rather upset ;)

---

### Post by ryanrockey on 2006-11-03
Buying a new sound card is not a particularly satisfying answer. Is there another place where this setting can be changed. It worked just fine before upgrading to 6.10. Is there another solution?

---

### Post by Manannon on 2006-11-04
If it worked previously for you, it's unlikely to be the same problem as I reported. There are various other threads around (I no longer have the links sorry) about similar issues with solutions - you might want to try those.

---

### Post by MHD on 2006-11-05
I'm totally baffled to...
I want to listen to music through my headphones without annoying everyone else in the room... I can not find out how to turn headphone sense on in either alsamixer or kmix...

Inspiron 6400
Edgy
 Card: HDA Intel                                                                                                                                                                    
&#9474; Chip: SigmaTel STAC9200

---

### Post by MHD on 2006-11-06
Ok.. now it works...

I added the 
line:
options snd-hda-intel model=z71v position_fix=1

to /etc/modprobe.d/alsa-base

And it didnt seem to work, even after a /etc/init.d/alsa restart

But, perhaps not at all related, after a restart headphone sense works...
oddness...

---

### Post by MHD on 2006-11-13
This is still annoying me... I seem to loose headphone sense whenever I suspend my lappy...
Surely some one else has had this problem?

---

### Post by MHD on 2006-11-26
Anyone?

---

### Post by Manannon on 2006-11-26
As this is a different issue, you're better off starting a new thread.

Have you tried restarting Alsa after resuming?

---

### Post by MHD on 2006-11-28
Just tried it then (alsa-utils) no luck
Will start a new thread

---

### Post by lexarrow on 2007-05-26
maybe [this]("http://ubuntuforums.org/showthread.php?t=455147") could help

---

### Post by LaPingvino on 2007-06-28
> **MHD said:**
> Ok.. now it works...

I added the 
line:
options snd-hda-intel model=z71v position_fix=1

to /etc/modprobe.d/alsa-base

And it didnt seem to work, even after a /etc/init.d/alsa restart

But, perhaps not at all related, after a restart headphone sense works...
oddness...

Thanks for this tip, it works for me :). I guess it's impossible to restart alsa while active, at least not this way, because you're referring to an init-command... That's why a reboot is doing the trick :).

LaPingvino

---

### Post by timsath on 2008-01-20
> **Manannon said:**
> I just bought a cheap one off eBay too - works great and is better looking than the one you linked to :p 

To make it the default card I edited /etc/modprobe.d/alsa-base and added

options snd-usb-audio index=0
options snd-hda-intel index=1

This has caused the slight problem that if the USB device isn't connected there is no default sound card, but it isn't annoying enough for me to bother fixing right now. 

Oh, and don't disconnect the device while you're using it to play music... some applications get rather upset ;)

Just did the same thing...4.09 shipped...whatever, as long as I can listen to music in the library, i don't care...haha.

---

### Post by cdtech on 2008-01-29
Could have a look [[COLOR="DarkRed"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=676917").
Hope this helps you......

---

