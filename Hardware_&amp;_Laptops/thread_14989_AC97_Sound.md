---
title: "AC97 Sound"
date: 2005-02-11
forum: Hardware &amp; Laptops
---

### Post by skyde on 2005-02-11
MOVED! from the wrong topic.

Well I installed Ubuntu today but found out that I have zero sound. I can't hear anything. Asked some of my friends and they told me that something wrong with my mixer settings. Started up Alsamixer and put everything to full strength. Response was nothing.

I did do a few searches on the forums here, but I wasn't able find anything specific to my problem.
Sounds worked fine with winblows so I don't think there is nothing wrong with bios ie. not disabled.

An lsmod | grep snd_ brings out this. If this helps with the answer?

snd_via82xx 26660 3
snd_ac97_codec 59268 1 snd_via82xx
snd_pcm_oss 48168 0
snd_mixer_oss 16640 3 snd_pcm_oss
snd_pcm 85540 2 snd_via82xx,snd_pcm_oss
snd_timer 23172 1 snd_pcm
snd_page_alloc 11144 2 snd_via82xx,snd_pcm
snd_mpu401_uart 7296 1 snd_via82xx
snd_rawmidi 23232 1 snd_mpu401_uart
snd_seq_device 7944 1 snd_rawmidi
snd 50660 11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_o ss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,s nd_seq_device
gameport 4736 2 snd_via82xx,analog

If you need more info lemme know. I am fairly new to Linux so feel free to talk to me like I am an idiot

Best Regards
~skyde

---

### Post by r00 on 2005-02-28
you tried  going root in the terminal
and typing  "alsamixer"  ?

it might've been muted of something there.. i've been totally combing the whole forum for anything to get my soundblaster extigy usb card to play some sound..but not luck wif that..    i did, however, find a way to get my onboard ac97 card working thanks to that alsa mixer ..  hope it helps..

---

### Post by bored2k on 2005-02-28
[QUOTE=r00]you tried  going root in the terminal
and typing  "alsamixer"  ?

it might've been muted of something there.. i've been totally combing the whole forum for anything to get my soundblaster extigy usb card to play some sound..but not luck wif that..    i did, however, find a way to get my onboard ac97 card working thanks to that alsa mixer ..  hope it helps..[/QUOTE]

i hav an ac97 , an i currently support arts, oss, esd and alsa sound [gstreamer-properties / computer>sys config>sound]

alsamixer helps, artsbuilder does too

---

### Post by r00 on 2005-02-28
can you be slightly more specific?  i think you meant to go to the systems tools >> configuration editor.. but i could be wrong? ..and what is artsbuilder ?

also, does your ac97 play with all the speakers instead of just two?
thanks much

---

### Post by hard_i on 2005-02-28
[QUOTE=r00]can you be slightly more specific?  i think you meant to go to the systems tools >> configuration editor.. but i could be wrong? ..and what is artsbuilder ?

also, does your ac97 play with all the speakers instead of just two?
thanks much[/QUOTE]
 i've got ac97  , and i had problems with speakers too .. , to get all my 4 speakers to work i did:
Volume control > device > alsa mixer > switches > ticked "line in as surround" and " duplicate front" , and under > playback > raise the "surround" bar .

But for some reason it wont save the changes for me .. so i have to do it over again after reboot...

---

### Post by rdario on 2005-02-28
[QUOTE=skyde]MOVED! from the wrong topic.

Well I installed Ubuntu today but found out that I have zero sound. I can't hear anything. Asked some of my friends and they told me that something wrong with my mixer settings. Started up Alsamixer and put everything to full strength. Response was nothing.

I did do a few searches on the forums here, but I wasn't able find anything specific to my problem.
Sounds worked fine with winblows so I don't think there is nothing wrong with bios ie. not disabled.

An lsmod | grep snd_ brings out this. If this helps with the answer?

snd_via82xx 26660 3
snd_ac97_codec 59268 1 snd_via82xx
snd_pcm_oss 48168 0
snd_mixer_oss 16640 3 snd_pcm_oss
snd_pcm 85540 2 snd_via82xx,snd_pcm_oss
snd_timer 23172 1 snd_pcm
snd_page_alloc 11144 2 snd_via82xx,snd_pcm
snd_mpu401_uart 7296 1 snd_via82xx
snd_rawmidi 23232 1 snd_mpu401_uart
snd_seq_device 7944 1 snd_rawmidi
snd 50660 11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_o ss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,s nd_seq_device
gameport 4736 2 snd_via82xx,analog

If you need more info lemme know. I am fairly new to Linux so feel free to talk to me like I am an idiot

Best Regards
~skyde[/QUOTE]
 try this
add this line to kernel option in boot (grub)

acpi_irq_isa=7

rdario

---

### Post by skyde on 2005-03-06
Well tried adding the line into grub = no effect.
Used alsamixer  and unmuted everything... = no effect.

Well almost no effect.... if I put my ear against the speaker and put them to max I can hear the music... as a whisper...

Any other suggestions?

Best regards,
skyde

---

### Post by skyde on 2005-03-06
Update: I read from somewhere a solution where one should add

options snd-via82xx ac97_quirk=0  to modprobe.conf file.

Don't think that worked either. Did not even find modprobe.conf file anywhere and instead added it to one of the files (alsabase) in modprobe.d directory. Hope I did it right.

~skyde

---

### Post by skyde on 2005-03-06
SUCCESS!!!

I restarted my computer after doing the update-modules (I had thought it would take effect immediately) and 'lo and behold sounds work!

The ac97_quirk thing seems to have worked!

Thanks all for the responses!!!

~A -very- happy skyde  :mrgreen:

---

### Post by myotheralt on 2007-03-06
ok, so what exactly needs to be done? i have the same problem...

---

### Post by iamtherealwoody on 2007-03-06
Have the same problem too.  I have a Gateway M675ppp with Sigmatel ac97 82801EB chipset thing.  Ive tried everything imaginable, OSS ALSA, comprehensive sound guide.

I believe this is what you do, Ive tried it though with no results.
>     * webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by
      Code:

      sudo nano /etc/modprobe.d/alsa-base

      and adding this as the last line:
      Code:

      "options snd-intel8x0 ac97_quirk=3"



Straight from the Comprehensive Sound Problem Guide.  They say is 3 doesnt work, add 0,1,2, or 4.

---

### Post by wcampbell on 2007-03-18
I had what I thought was the exact same problem and have resolved it, so I thought I would share.   I my sound card was detected as '82801BA/BM AC'97 Audio'.  I'm pretty new to Linux, so this might be basic, but here goes...

open terminal.
type 'alsamixer' and press enter.
Make sure that 'Master', '3D Control' and 'PCM' have green '00' at the bottom and that under 'item' at the top it does not say (off) for any of these.  If they do, you can turn them on with the M key.

Thats all it was for me...

---

### Post by andy_tok on 2007-04-09
Sorry but it's the first time I've installed linux.
How do you add 
"options snd-via82xx ac97_quirk=3"?
I mean, in the terminal, I typed sudo nano /etc/modprobe.d/alsa-base and add "options snd-via82xx ac97_quirk=3" at the bottom of the file, but how to save it?
Thanks

---

### Post by WiseElben on 2007-04-09
> **andy_tok said:**
> Sorry but it's the first time I've installed linux.
How do you add 
"options snd-via82xx ac97_quirk=3"?
I mean, in the terminal, I typed sudo nano /etc/modprobe.d/alsa-base and add "options snd-via82xx ac97_quirk=3" at the bottom of the file, but how to save it?
Thanks

At the bottom, you will see the commands. "^" represents Ctrl, so if you want to save it, you would press Ctrl + O for "Write Out."

---

