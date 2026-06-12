---
title: "ALSA + SoundBlaster"
date: 2005-01-30
forum: Hardware &amp; Laptops
---

### Post by detox on 2005-01-30
hi all.. i have installed Ubuntu but i don't have support for my sound card... the card is a Sound Blaster Live! 24-bits with the ca0106 chipset... my question is:
hhow can i support with the last alsa driver version my sound card? i have to recompile the kernel??? thanks!!!

---

### Post by sharkzf6 on 2005-02-01
I believe you have the same problem I did. The discount version of the Audigy (LS or SB 24 bit) does not use hardware mixing, it offloads to the CPU (that's why it's so cheap). This causes a problem with Linux (works fine in WinXP if you have a good processor). I don't believe there's a solution for this yet. I ended up putting my old SB Live! 16 bit back in my system and it works flawlessly with the EMU10k1 module. You'll either have to wait until this problem is resolved - if it's resolved – or get another sound card (real Audigy 2 or another 24 bit brand), there are several that work with Linux.

---

### Post by Jesterace on 2005-02-14
That is the best answer I've found about my SB Live 24bit, I wondered why it was so cheap. So i know it's junk and it only works in windows hehe shucks $30 wasted  ](*,)

---

### Post by aplsin on 2005-02-15
[QUOTE=Jesterace]That is the best answer I've found about my SB Live 24bit, I wondered why it was so cheap. So i know it's junk and it only works in windows hehe shucks $30 wasted  ](*,)[/QUOTE]
 I made the same mistake as you, i was SO angry when i noticed it was the wrong chipset! But i managed to trade it for a good old SB Live with the EMU10k1 chipset the same day, so then i was happy. :)

---

### Post by sharkzf6 on 2005-02-15
[QUOTE=aplsin]I made the same mistake as you, i was SO angry when i noticed it was the wrong chipset! But i managed to trade it for a good old SB Live with the EMU10k1 chipset the same day, so then i was happy. :)[/QUOTE]
I am also using my trusty old SB live with Linux. It seems to be the best card despite its age - or maybe because of it ;). Creative should be ashamed of themselves for making such a crappy card...(Audigy LS, SB live 24 bit).

---

### Post by Jesterace on 2005-02-16
Definitly I remember when Creative stood for quality and not cheap useless hardware.

---

### Post by sharkzf6 on 2005-02-16
I've done a lot of research on ALSA and the Audigy LS/SB live 24 since I originally posted this thread. I even subscribed to the ALSA mailing list so I get feedback from people all over the world constantly. Turns out, ALSA **does** support these cards with the latest release, ALSA version 1.0.8. Originally the support started in versions 1.0.6a and used a driver called *audigy ls*. This means if you use Warty, you don't have the support built-in as Warty uses ALSA 1.0.5. If you use Hoary the support is there (version 1.0.6), however, I was never able to get the Audigy LS to work with Hoary, despite this supposed fact (maybe there's a difference between 1.0.6 and 1.0.6a - not the same version?). With ALSA 1.0.8, the driver changed names, it's now called *ca0106* and is suppose to work for both cards. If you want to do your own research, I suggest you start here:

[http://www.alsa-project.org/](http://www.alsa-project.org/)

I have since switched to Debian Sarge and am using the SB live with it. Everything works great and sounds decent, that's good enough for me. I don't mind a challenge, but this Audigy LS thing was a bit much for me, especially when I found out what a piece of junk the card is...

Good luck!

Oh, BTW - keep in mind if you decide to use ALSA version 1.0.8, it's bleeding edge technology and may not actually "fully" support what the LS and SB 24 try to do since the real issues is hardware vs software mixing.

---

### Post by macewan on 2005-02-16
i had to upgrade to the latest source from the also-projects site

---

### Post by detox on 2005-02-21
hi, can i upgrade alsa-driver from apt-get repositories?... that is my problem...

---

### Post by drinky76 on 2005-02-25
*Annoyed*

I bought this card after checking compatibility, it appears that all Soundblaster Live cards are not equal and my source was incorrect...

I've been trying to record an Ubuntu jingle for [LUG Radio](http://www.lugradio.org/) for a few weeks now, hampered by my crap onboard sound card so I bought an SB Live on a recommendation.

Can anyone confirm that this card works in Hoary? I don't want to upgrade unless I have to. Equally I bought this card against the will of my bankmanager and can't afford to buy another card unless I really have to, although I have just found the 5.1 Live for 10 GB pounds...

Besides, I thought the world had decided that offloading hardware tasks to the CPU was a bad thing with Softmodems and softprinters...

---

### Post by gyaresu on 2005-02-26
[QUOTE=sharkzf6]I've done a lot of research on ALSA and the Audigy LS/SB live 24 since I originally posted this thread. I even subscribed to the ALSA mailing list so I get feedback from people all over the world constantly. Turns out, ALSA **does** support these cards with the latest release, ALSA version 1.0.8. Originally the support started in versions 1.0.6a and used a driver called *audigy ls*. This means if you use Warty, you don't have the support built-in as Warty uses ALSA 1.0.5. If you use Hoary the support is there (version 1.0.6), however, I was never able to get the Audigy LS to work with Hoary, despite this supposed fact (maybe there's a difference between 1.0.6 and 1.0.6a - not the same version?). With ALSA 1.0.8, the driver changed names, it's now called *ca0106* and is suppose to work for both cards. If you want to do your own research, I suggest you start here:

[http://www.alsa-project.org/](http://www.alsa-project.org/)

I have since switched to Debian Sarge and am using the SB live with it. Everything works great and sounds decent, that's good enough for me. I don't mind a challenge, but this Audigy LS thing was a bit much for me, especially when I found out what a piece of junk the card is...

Good luck!

Oh, BTW - keep in mind if you decide to use ALSA version 1.0.8, it's bleeding edge technology and may not actually "fully" support what the LS and SB 24 try to do since the real issues is hardware vs software mixing.[/QUOTE]

Thank you.
I install alsa >> doesn't work.
I get the latest kernel >> doesn't work. 
'lspci -v' >> "Creative Labs: Unknown device 1004"
I scratch my head >> head scratching 'A OK'.

Stupid WinBlaster.

I appreciate you recounting your experiences.
Off to swap pretend card for real one.

regards
gyaresu

---

### Post by Seatux on 2005-02-26
I have an even troublesome problem

I have an Asus A78NX-E, NForce2 based system. I had a Sound Blaster Live 5.1 installed too. Now the Gnome sound applet says there's no mixers detected, though i can use XMMS with a little tweaking. Even in XMMS, i can only use my NForce sounds only, not my Sound Blaster LIve. Any ideas? Running Warty...

---

### Post by drinky76 on 2005-02-27
[QUOTE=gyaresu]Thank you.
I install alsa >> doesn't work.
I get the latest kernel >> doesn't work. 
'lspci -v' >> "Creative Labs: Unknown device 1004"
I scratch my head >> head scratching 'A OK'.

Stupid WinBlaster.

I appreciate you recounting your experiences.
Off to swap pretend card for real one.
[/QUOTE]

I'm afraid I don't know much about these kind of problems, but did you get the ALSA version mentioned? (v1.06 minimum, 1.08 or above preferable).

Other than that I can't offer much help as I just bought an SB Live 5.1 instead. I think the 24bit 7.1 card will be supported by ALSA (and Ubuntu)  in the future, just not at the moment.

I filed a bug against the ALSA website as it doesn't differentiate between the 5.1 and 7.1. Thats why I bought one of these by mistake.

---

### Post by drinky76 on 2005-02-27
[QUOTE=Seatux]I have an even troublesome problem

I have an Asus A78NX-E, NForce2 based system. I had a Sound Blaster Live 5.1 installed too. Now the Gnome sound applet says there's no mixers detected, though i can use XMMS with a little tweaking. Even in XMMS, i can only use my NForce sounds only, not my Sound Blaster LIve. Any ideas? Running Warty...[/QUOTE]

Does that mean you have or had 2 soundcards installed (one onboard and one SB 5.1)? Is the 5.1 still in the machine? Which one are you using? If you are using onboard sound, what is it?

XMMS will play CD audio across the IDE bus if you tell it to (digital audio extraction) so you can do it without one of those little audio cables from your CD drive to your soundcard, this might be why XMMS works. This way it bypasses your soundcard. Thats how Windows Media Player works too.

The SB Live 5.1 uses the emu10k1 module. Have you tried running lsmod and looking to make sure the emu10k1 module is loaded?

lsmod | grep emu10k

if it's not loaded,

modprobe emu10k1

Have you (or Synaptic) accidentally removed ALSA or anything like that? Double-check it's still installed. Double check the permissions on /dev/dsp

ls -l /dev/dsp

It should be something like the following (the date and time will be different, but the permissions are essential)

crw-rw----    1 root     audio     14,   3 2005-02-27 14:13 /dev/dsp

If not:

sudo chmod 660 /dev/dsp

to make the permissions correct

sudo chown root /dev/dsp

to make it root owned and

sudo chgrp /dev/dsp

to make it owned by the audio group. These should all be ok anyway.

Make sure you are a member of the audio group. From the menu:

Computer > System Configuration > Users and Groups > select your user account > Properties > Other Groups.

Make sure Audio is in the User's Groups column, if not, add it. All of this should be set up ok anyway, I'm just saying it to make sure nothing obvious is at fault. I don't really know much about the sound system or ALSA.

If all of this is ok, then maybe come back and someone else will be able to help you, I'm at the limit of my knowledge here.

---

### Post by macewan on 2005-02-27
I took my soundblaster live back to the store

---

### Post by Seatux on 2005-02-28
root@ubuntuku:/home/meng # lsmod | grep emu10k
emu10k1_gp              3840  0
snd_emu10k1            80776  0
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9120  1 snd_emu10k1
snd_ac97_codec         59268  2 snd_emu10k1,snd_intel8x0
snd_pcm                85540  4 snd_emu10k1,snd_intel8x0,snd_pcm_oss
snd_page_alloc         11144  3 snd_emu10k1,snd_intel8x0,snd_pcm
snd_rawmidi            23232  2 snd_emu10k1,snd_mpu401_uart
snd_seq_device          7944  2 snd_emu10k1,snd_rawmidi
snd                    50660  17 snd_emu10k1,snd_util_mem,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
gameport                4736  3 emu10k1_gp,snd_intel8x0,analog
root@ubuntuku:/home/meng # modprobe emu10k1
root@ubuntuku:/home/meng # ls -l /dev/dsp
crw-rw----    1 root     audio     14,   3 2005-03-01 10:05 /dev/dsp

I just need to use the SB Live card, kinda obvious that i want to use the sb card isn't. I had gnome-alsamixer installed and played the volumes, but kinda useless. Anyway to disable the Nforce one and just use the SB card?

---

### Post by drinky76 on 2005-03-01
[QUOTE=Seatux]Anyway to disable the Nforce one and just use the SB card?[/QUOTE]
You should be able to disable onboard sound in the BIOS.

---

### Post by Seatux on 2005-03-01
But since the SB card isn't working now, won't i be rendred soundless?

In windows, i had the card disabled from device manager and defaulted the sb card. Anyway to do this in Ubuntu?

---

### Post by drinky76 on 2005-03-11
[QUOTE=Seatux]But since the SB card isn't working now, won't i be rendred soundless?

In windows, i had the card disabled from device manager and defaulted the sb card. Anyway to do this in Ubuntu?[/QUOTE]
Sorry for the delay, I hadn't realised there had been more posts on this thread.

As I said before, I'm not a sound expert, it was just a suggestion based on a loose idea that maybe your nForce onboard sound was confusing the issue as your 5.1 **should** work.

The BIOS information screen is pretty much the first thing you see when your turn your PC on, where it counts and checks your RAM, works out what disks are attached and so on. You can enter the BIOS setup normally by pressing Del, though sometimes it is F1 or F2. You should be able to see the message 'Press xxx to enter setup' somewhere (where xxx is the approprate key) unless there is a vendor splashscreen (Intel and a few other people do this).

Enter the BIOS setup by doing the appropriate action from above, then locate something like the PCI setup or similar and look for where you can turn onboard devices on or off. This is just a case of looking around and finding it, I can't help you with this as BIOSes are different, but it will probably be somewhere down a few submenus.

**BIG warning:** don't mess with anything you don't understand.

Just locate the item that allows you to enable or disable onboard sound and disable it. Save your settings and reboot.

With a bit of luck, you will reboot and have sound if my assumption is correct that the nForce sound is the default soundcard and is not supported/working under Linux atm.

Disabling onboard sound in the BIOS will also hide it from Windows too so you shouldn't need to bother with the Device Manager again.

If this action makes no difference, just re-enable onboard sound in the BIOS and you're back as you were. Unfortunately, this also means I'm s**t out of ideas ;)

If this doesn't work, maybe you have a flaky installation, though config shouldn't change unless you change it, or flaky hardware. In a worst case, try disabling onboard sound and attempt a reinstall? If you still have the problem consider that your card might be borked or that you just have a weird hardware combination that doesn't like Linux. Can you tell I'm clutching at straws now? ;)

Anyway, good luck but I'm out of ideas.

---

### Post by trigg on 2005-03-13
[QUOTE=detox]hi, can i upgrade alsa-driver from apt-get repositories?... that is my problem...[/QUOTE]
Make sure your repositories are up to date for apt-get (e.g. - hoary vice warty). 
Use this apt-get command:

apt-get install alsa-source
cd /usr/src
tar -xvjf alsa-driver.tar.gz
cd modules/alsa-driver
sudo ./configure --with-cards="whatever card you have"  (and also whatever other options you want)
sudo make
sudo make install

---

### Post by Jesterace on 2005-03-13
I had some guided help from crimsum last night and I made some instructions here on this forum for them.... Note these are for people running Hoary I haven't done it on warty.

 [How to get SBLive 24Bit ca0106 modules](http://www.ubuntuforums.org/showthread.php?t=19307)

---

### Post by psoulocybe on 2005-03-20
I posted in your thread, I tried it, but got hung up....

if you can help, it'd be great... i really want to listen to some tunes.

---

### Post by psoulocybe on 2005-03-20
Trigg, i did it just like that.... but i had to make sure i had the alsa headers and all that....   

but it's working!

Listening to Ghetto Boys - Damn It Feels Good To Be Gangster

---

### Post by veda_sticks on 2005-05-27
arg, an update for my kernel 2.6.10.5-k7 just downloaded and installed and now my sound is broken, ive tried running alsaconf to reconfigure the driver,  it detects my sound cards spot ot, but when it trys to initilise then it goes mental wwith lots of text on the screen and says no soundcards found this is what happens

Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
Invalid card number.
Usage: amixer <options> command
Available options:
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
Available commands:
  scontrols       show all mixer simple controls
  scontents       show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control
 * /etc/init.d/alsa: Warning: 'alsactl restore' failed with error message 'alsactl: load_state:1272: No soundcards found...'.                            [ ok ]

---

### Post by Mission 10 on 2005-12-19
Ok after much toil I cannot get this card working. At least I'm not alone in buggin out about this card.

---

