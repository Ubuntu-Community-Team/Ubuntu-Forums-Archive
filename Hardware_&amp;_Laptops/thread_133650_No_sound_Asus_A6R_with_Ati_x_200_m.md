---
title: "No sound Asus A6R with Ati x 200 m"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by fernando_lopes_jr on 2006-02-20
Well I've managed to get the grafix card to work with the help of same threads in this forum but no luck with the sound.Can anyone help with this.I'am sure their more ppl with this problem could sameone with experiance write a how to on this matter please

---

### Post by ixius on 2006-02-26
i have the same problem with my a6r laptop. i can only hear extremely distorted sound on my headset and no sound on laptop speakers at all. unfortunately i found no solutions for this...

---

### Post by dhalgren on 2006-02-27
hi, I had a similar problem with as asus a5ec. I found the answer in a posting by kbuel in a thread on no sound from headphone jack:  [http://ubuntuforums.org/showthread.php?t=76307]("http://ubuntuforums.org/showthread.php?t=76307") 

I had no sound at all, but after following kbuel's instructions *to the letter*, I have sound through the inbuilt speakers and headphone jack. This makes it worth a try for you both.

Make sure the sound card is a realtek and that the offending module is snd-hda-intel !

Good luck!

---

### Post by Chanon on 2006-03-07
A6R has ATI Radeon Express 200M chipset and according to Windows the sound chip is one from Soundmax. Ubuntu 5.10 detects the sound as ATI IXP. Anyone have any further ideas how to get the sound working on this kind of machine?

In case this helps, here is the output of my lscpi:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:02:01.1 0805: Ricoh Co Ltd: Unknown device 0822 (rev 17)
0000:02:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0592 (rev 08)
0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

and here is the relevant output of lsmod (lsmod | grep snd)

snd_atiixp             19040  1
snd_ac97_codec         71420  1 snd_atiixp
snd_pcm_oss            46240  0
snd_mixer_oss          16256  1 snd_pcm_oss
snd_pcm                78344  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    49540  8 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc          9604  2 snd_atiixp,snd_pcm


I download the latest alsa drivers, libraries and utilities and compiled those myself. Nothing changed after that.

---

### Post by fernando_lopes_jr on 2006-03-30
Well I like Ubuntu a lot but the driver support is terible I really think its not much to ask for same audio support for my card seams no one can anser my question this post was been online for quite a while and still no luck.I had same problems with the gfx card but managed to make it work, I just hope that the next version os Ubuntu was support cause I think there must be a lot of people with this chipset.

---

### Post by arkangel on 2006-04-01
[http://fr.wikibooks.org/wiki/Tout_sur_le_portable_Asus_A6VA](http://fr.wikibooks.org/wiki/Tout_sur_le_portable_Asus_A6VA)

i have thsi computer and i follow all the instructions and works well 
give it a try (if you understand french )

---

### Post by bishop1981 on 2006-04-05
I have the same laptop and same problem, no sound at all.
I listed some information about my problem: [http://paste.ubuntu-nl.org/11478]("http://paste.ubuntu-nl.org/11478")
I've tried everything but nothing seems to work, this hardware is a piece of shit. I e-mailed to asus about drivers or somekind support with linux, but I didn't have an answer. Sounds would be fun to have :-k

---

### Post by rantak on 2006-04-14
Any luck with getting the sound on A6R? I just bought this computer two days ago, íf I'd read this thread I would have left it at the store. I also get the slight scrambled sound on the headphone jack when playing some sound on Ubuntu. 

I'm using Dapper Kubuntu btw.

---

### Post by rantak on 2006-04-14
I got it working! 

I was sure there was some hardware/driver issue. After two hours of trying to blacklist modules, alsamixer etc. The problem was resolved:

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=160397](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=160397)

Check the last comment. In KMix go to the switches tab and enable the external amplifier. Or fiddle with the buttons go on and back the switches tab until you get it working. There's still some issues, master sound is not working (the master surround is).

---

### Post by leoneri on 2006-04-15
Hi, I also have this laptop. I'm using ubuntu dapper 6.06. I enable the external amplifier but all is still the same... no sound from either my builtin speaker and my headphone... Is there any previous step(s) that need to be done before enabling the external amplifier? Please tell in more detail.

Thanks.

---

### Post by rantak on 2006-04-16
I think not. I didn't recompile anything, I tried to blacklist some modules (atiixp_sound_modem) but I removed those. 

There's definetely something weird about the sound still.
If I look at my KMix now, the external amplifier is actually off (all the buttons are dark). If I press it few times the sound might go off and doesn't come back. Eventually after pressing the buttons on and off and going back to the
output tab works. 

For example now when I pressed the external amplifier button (on) the sound went off. When I pressed it again (off) the sound didn't come back. But when I pressed the headphone jack sense and line in sense buttons on the sound came back (note that all the buttons were off in the beginning). It seems almost random. Also I didn't get the sound on when I tried with alsamixer, only with KMix

Do you get the small distorted sound in the headphones when playing something at full volume?

Btw, I'm having issues with external usb mouse, it just stops working after few minutes. Have you tried a external mouse? I've tried with the one included with the laptop and one another, it's the same.

---

### Post by leoneri on 2006-04-17
No, I hear nothing on my headphones. 

Btw, can you tell me how to blacklist module?

External USB mouse, yes, sometimes --not always-- it suddenly stop working. It happens when I use Breezy 5.10. But now after install Dapper 6.06 I never --or not yet-- experience it again..  :) Even when I plug out the mouse and plug it in again on different usb port, it still go back to works, while the situation is different when I still using Breezy.

Oh yea, do you also have other hardware issue such as camera, modem, or directdraw? I have it, so I'm pretty sure that all who using A6R will face the same issue. :) What kind of hardware problems that you have solved? Maybe you can share. Thx.

---

### Post by rantak on 2006-04-18
The USB issues are so bad that I had to install another distro for the moment (Kanotix). The mouse sometimes worked only for 10 seconds, and there was no way to get it back, and when it happened no other USB devices worked either.  The USB seems to work well with other distro's though, so its not the A6R. 

Sound started to work in Kanotix when I (in KMix again) pressed the Master Surround button on (it has a icon of 1/2 inch headphone plug), the main master volume doesn't work here either. Same was with Knoppix when I tried it. With Damn Small Linux the sound worked right at the start.

Blacklisting modules, sorry I followed some guide from the net when I was trying that. It's some file you have to edit. /etc/modprobe.d/blacklist is for plug-in usb devices but I can't remember what the file was for the modules that kernel loads. Google/forums I'm sure you can find some guide.

The webcam doesn't have any drivers for linux, but there's development going on. The same is for the Ricoh Card reader.
I created a Laptop Testing Team entry for A6R. Check it out 
at [http://wiki.ubuntu.com/LaptopTestingTeam/AsusA6R]("http://wiki.ubuntu.com/LaptopTestingTeam/AsusA6R")
and edit it yourself if your experience was different.

---

### Post by rantak on 2006-04-22
I now think that the usb problems occur only with the fglrx driver, because the problem started in Kanotix too after I had installed the fglrx driver. In 6.06 Beta Ubuntu it works ok with the "ati" driver. And if you still don't have sound check out the wiki page, I put the exact things I did with a clean Ubuntu 6.06 Beta install to get the sound working there.

---

### Post by ghostdog78 on 2006-04-23
hi!
please:
i need some help step by step, how can i make a sound on my a6r after clean ubuntu drapper beta install (gnome)
i tried some trick what i found here, but not worked
maybe i did wrong way
thanx

(sorry for the poor english)

---

### Post by rantak on 2006-04-23
[QUOTE=ghostdog78]hi!
please:
i need some help step by step, how can i make a sound on my a6r after clean ubuntu drapper beta install (gnome)
[/QUOTE]

Quote from the wiki page 

People are having problems with the ATI IXP sound so this is how I got the sound working in Ubuntu 6.06 Dapper Beta clean install: 

start alsamixer in terminal -> mute the external amplifier (press M) -> increase the master surround sound(if needed) -> quit the alsamixer (Escape) -> sound working.

If this doesn't work, sorry I can't really help more. Different mixer options should work.

---

### Post by ghostdog78 on 2006-04-23
tnx!

nothing changed..
is there any hope when the stable 6.06 will come out?
the developers know about us problem?

---

### Post by ewoox on 2006-05-01
well my a6r seems ok with sound, after muting external amplifier and increasing master surround, but built-in microphone doesn't work at all. :rolleyes:

---

### Post by uggeli on 2006-05-01
I have used ubuntu for a while now, but I'm still totally newbie when it comes this kind of situations. Anyway I was wondering could same kind solution work here, as in MSI Megabook, look sound section here:
[http://craig.copi.org/computers/ms-1013/](http://craig.copi.org/computers/ms-1013/)

I know it's Breezy in that example, but it's atiixp in Megabook also. Result there seems to be installing snd_atiixp module from a newer alsa. Could that method be used with A6R & Dapper aswell (but where to get newer alsa than in dapper?)? I'm not sure is the soundproblem samekind in A6R as in Megabook, cause I don't have machine myself, just intrested of it.

If this message is foolish, just say and I edit this away when I happen to read this next time. Just remember, I'm still newbie and just wanted to know the possibility of this. :)

---

### Post by leoneri on 2006-06-06
[quote="rantak"]I now think that the usb problems occur only with the fglrx driver, because the problem started in Kanotix too after I had installed the fglrx driver. In 6.06 Beta Ubuntu it works ok with the "ati" driver.[/quote]
hmm, it seems you right.
[quote="rantak"]And if you still don't have sound check out the wiki page, I put the exact things I did with a clean Ubuntu 6.06 Beta install to get the sound working there.[/quote]
nope still not work... I currently waiting for the ubuntu 6.06 LTS and kubuntu 6.06. I've just order thru free ship-it. Just can't wait to get my hand on it :)

---

### Post by bishop1981 on 2006-06-29
Cool finally I got the sound working... YES!
I just intalled new version of Ubuntu and did that alsamixer tweak. :rolleyes:

---

### Post by leoneri on 2006-07-13
me too... both with kubuntu and ubuntu :D  but dial-up modem died in kubuntu, so I switch back to ubuntu.

---

### Post by fernando_lopes_jr on 2006-08-27
I had gived up having any sound in Ubuntu but finally I got the sound working with that alsamixer tweak.
Thanks very much for the help :D

---

### Post by Fugazii on 2006-09-08
Read this. That can Help You to get sound on a6r->

[http://ubuntuforums.org/showthread.php?t=251383&highlight=a6r](http://ubuntuforums.org/showthread.php?t=251383&highlight=a6r)

---

