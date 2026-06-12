---
title: "audio card nightmare!!"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by audiocurry on 2005-06-12
Hi folks! I have a tough, intriguing one for you: 
MY SYSTEM:
P4 3.0 GHz HT
Intel 915GAV motherboard
1 GB RAM
200 GB SATA
250 GB NCQ SATA
Win XP SP2

THE PROBLEM:
	I'm basically doing audio and video editing, using apps like Pinnacle, Sonar, etc., using DXi and VSTi softsynths. I have 2 professional multi I/O soundcards, one is Gina (20 bit) by Echo Audio, and the other is a USB-based MIDI controller plus audio interface (24-bit) called Neon.
I recently got the above system, and when I tried to use my USB interface (Neon) in Sonar, I started getting a very loud crackling noise. I checked the audio buffer settings in Sonar, which can sometimes cause such problems, but I was using ASIO drivers for the Neon, which shouldn't cause these problems normally. I tried the Gina, but the card wouldn't work at all. I downloaded the latest drivers in each case, and still it wouldn't go away.
	Then I took the Gina out of my system and removed all the drivers and tried again. The crackling sound continued.
	 I tried rebooting a few times and running audio through the Neon. What I noticed is - for about 8-10 secs the audio would play fine, and then it would disintegrate again into the crackling sound. I became convinced it was a driver problem.
	I USE THE NEON ALL THE TIME WITH MY LAPTOP, WITHOUT ANY PROBLEMS, SO IT IS NOT A HARDWARE PROBLEM - at least not with the audio hardware. I WAS USING THE GINA IN MY PREVIOUS SYSTEM WITH NO PROBLEMS WHATSOEVER (WIN XP).
	I still feel it's a software problem - something to do with drivers and/or Windows itself. Then I thought that perhaps the problem is with the SP2, but I couldn't remove it, since my legal copy of Win XP Pro came bundled with SP2. (My laptop doesn't have the SP2 installed). So I contacted MS support, and they sent me a way to uninstall by removing "spuninst.exe" from the "Run" command. I tried that, and something got removed, but SP2 still remains. 
	Then one of my friends (an audio engineer) told me that the Intel 915 motherboard has some audio issues. So I contacted Intel and they suggested I download the latest audio drivers for the onboard Realtek High Definition soundcard, as well as the latest BIOS. I did that, and hoped the problem would go away, but the problem continues to haunt me. 
	I realise I have the option to use another drive and reload Windows XP on it without SP2. The only thing is: I'm in the middle of a tight deadline project, so I decided to go with the onboard Realtek (lower quality) soundcard for now and just do my work till I absolutely have to stop and fix the problems. I do want to try this option, however, because I have a sneaking feeling that SP2 is messing things up.
	Is this a problem with the 915 motherboard? Echo support told me that audio cards can have problems with HT. I don't know much about this, but I've tried disabling it and still there's no difference. The ESI support said that the 915 causes problems for USB audio interfaces, so suggested a PCI USB2.0 card and use that instead of the onboard USB slots.

	What I want to be able to do is:
1.	Use the Neon (USB interface and MIDI controller) without any noises.
2.	Use the Gina in the system too. I have used multiple sound cards before. I realise you can't do that yet if you're using ASIO drivers in an 		application, but other than that, I want to have that option available to me.
3.	Stop losing hair and not grow old so quickly.
4.	Have good sleep at night and not have so many computer-related nightmares.

So if anyone out there has the solutions I would be EXTREMELY GRATEFUL for your help. Thanks so much!

---

### Post by kleeman on 2005-06-12
Wow this post is truly amazing! First I should say that I last used Windows seriously 3 years ago so I can't help (genuinely sorry). Why are you seeking help on a linux board? Are the winblows boards that bad? I guess linux has better community support but this is ridiculous - sorry for my reaction I am just amazed!

---

### Post by www.rzr.online.fr on 2006-05-29
I have a ESI neon device too ... and it is not fully usable on my laptop too ... 

Something makes me think there is some stuff we need to figure out about usb :
check :
[http://www.esiforum.com/show.asp?db=esi&t=esi1&mode=0&msg=2962](http://www.esiforum.com/show.asp?db=esi&t=esi1&mode=0&msg=2962)


Find me online ...

---

### Post by andou on 2006-11-25
I also have an ESI NeON I was using it with my PowerBook and GarageBand. That's quite easy to figure out and I'm just getting started with MIDI and Recording, so easy suits me just fine.

Anyway, I sold my Powerbook and now I have a PC. I regret my decision everyday, except when I watch movies on my 30" screen :D.

Interestingly enough, as I was looking for an easy to use replacement for GarageBand, I stumbled across Ardour and decided to give it a try. I needed to run Linux or OS X to use it. The distro of Linux I chose happened to be Ubuntu. Anyway, I can't get any sound and I'm not really sure how to configure it properly.

I don't know that much about music, and the tutorials I've tried to find seem to assume a lot of knowledge about either using Linux or other music programs. With GarageBand, all I had to do was plug in my Neon and click record. I'd like things to be that simple, but I'm willing to spend the time to learn something. If anyone's got some advice on a program I can use, please let me know.

Also, since this post was already here about a NeON and it's in the Ubuntu forums, let's try to get a Ubuntu Neon user's group going. At least, let's try to help each other get setup with Ubuntu and NeON and ardour, or whatever else might be out there.

Looking forward to hearing some ideas. I'll try to make post my progress (if I make any).

*note: I found what looks like a good startup tutorial on O'Rielly forums, so I decided to try out Ableton Live on Windows. (I'd like to get away from Windows... but I seem to keep coming back. Need help) [Here]("http://digitalmedia.oreilly.com/2005/02/16/ableton_intro.html")'s the link.

---

