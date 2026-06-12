---
title: "Soundblaster Audigy SE ( CA0106 ) -What I did to make it work."
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by gordong11 on 2006-04-01
OK, after a few hours of trial and error...I'll go through the step by step of how I got the SoundBalster Audigy SE PCI Card (CA0106 Device) to work.

This is off a fresh install of 5.10 breezy, 64bit. After I  installed breezy, I then installed all updates, rebooted, then enabled Multiverse's in the Synaptic Package Manager. Double clicked the sound icon on the top on gnome, and went into preferences and enabled all. I then Played around until I got static where I would normally near hear sound(probably don't have to do this). I had to select in "Multimedia systems Selector" Sink: ESD and the Source at OSS. I'm not sure about this, but it works for me!

Here is how I got it to work:

1. Open Terminal  and type:
Code:

sudo apt-get install build-essential gcc gcc-3.4

I rebooted

2.

wget [http://http.us.debian.org/debian/pool/main/a/alsa-driver/alsa-source_1.0.10+1.0.11rc3-1_all.deb](http://http.us.debian.org/debian/pool/main/a/alsa-driver/alsa-source_1.0.10+1.0.11rc3-1_all.deb)

3. 

sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant

4.

sudo dpkg -i alsa-source_1.0.10+1.0.11rc3-1_all.deb

if you get error(i did) then:

sudo apt-get -f install

NOW..VERY IMPORTANT. This did not work unless I did step 5!
5. 

sudo /etc/init.d/gdm stop

6.

login if needed-

sudo dpkg-reconfigure alsa-source

***READ THIS ALL FIRST****
this will bring you into a configure screen. FOR "PNP" press "NO, FOR DEBUG press :"yes".  on the next screen is just showing you the drivers, nothing to select just Press "ok"......now on the next selectable drivers screen press "spacebar" to de-select "All", and press "arrow" down until you see "CA0106". Then
Press the space bar again to select "CA0106", then " Tab".....then "enter" to OK. You will then exit.

7. Back in console type:

sudo module-assistant auto-install alsa-source


Thats it! you are done. type sudo /etc/init.d gdm start and your sound should be working!


Special thanks to the author of [https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28audigy%29%7C%28soundblaster%29](https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?highlight=%28audigy%29%7C%28soundblaster%29)

and others who helped me here.

There are a few changes that I needed to do, not listed at that Wiki page, so I decided to post this. Hope it helps

Gordo

---

### Post by Mustard on 2006-04-01
I'm sure some frustrated Audigy SE user is going to love you for this HOW TO. Good work putting it together. :)

---

### Post by tr333 on 2006-04-17
thanks for this!

it should also be posted in the HOW-TO forum (if it isn't already).

---

### Post by darkwarrior0404 on 2006-04-23
> Thats it! you are done. type sudo /etc/init.d gdm start and your sound should be working!

sudo /etc/init.d/gdm start           just a correction :) 

good how-to yet, my sound still not working :( thanks tho :(

---

### Post by darkwarrior0404 on 2006-04-23
Update:

well, there is sound now... but its really really really staticy? any ideas?

---

### Post by gordong11 on 2006-04-23
you know what is weird? I just built a new PC with an MSI K8n Diamond Motherboard, which has the CA0106 SoundBlaster SE onboard.....and it worked out of the box :confused: 


I can't explain that at all. And it sounds awesome!!!

I thought I was going to have to have to the steps in order to get it work. how weird!

---

### Post by darkwarrior0404 on 2006-04-23
[QUOTE=gordong11]you know what is weird? I just built a new PC with an MSI K8n Diamond Motherboard, which has the CA0106 SoundBlaster SE onboard.....and it worked out of the box :confused: 


I can't explain that at all. And it sounds awesome!!!

I thought I was going to have to have to the steps in order to get it work. how weird![/QUOTE]

:( not helpin lol can i have your motherboard? :):mrgreen: :p

---

### Post by darkwarrior0404 on 2006-04-23
Woo, installed Mandriva 2006, and the sound works perfect, didnt have to do anything :D

---

### Post by Mustard on 2006-04-23
[QUOTE=darkwarrior0404]Woo, installed Mandriva 2006, and the sound works perfect, didnt have to do anything :D[/QUOTE]

Heh..well, I'm glad you got linux going at least, even if its not Ubuntu. :)

---

### Post by darkwarrior0404 on 2006-04-24
[QUOTE=Mustard]Heh..well, I'm glad you got linux going at least, even if its not Ubuntu. :)[/QUOTE]

im going to stick it to the man :twisted:  and dual boot muahahha lol :twisted: wait... quadruple boot :D!!! 4 operating systems at once... every mans dreams... maybe a good idea for a future distro haha :p  thanks tho the tutorial was great, but I dont know why ubuntu wouldnt read it :(  I'll probably slap it on a small part of hard drive as far as web browsing and chatting and just playing around cause I really like it, it was my first Linux distro, and I'll probably always keep a copy of it on HD8)

---

### Post by gordong11 on 2006-04-28
I just installed the 32-bit i386 version of breezy...so now I have XP PRO Sp2, Breezy 32 +64 in a Tri-Boot sytem.....works great, but I'm actually gonna change this weekend.

I'm gonna use the 2 raptors from my old rig for Linux. SO The SATA II for windows, 1x Raptor for 32 bit breezy and one Raptor for the 64 bit( or maybe try a different Linux).

I honestly do not see the advantage to using the 64 bit version right now, the 32 bit runs just as well on my AMD X2 machine plus there is just so much more out there for 32 bit. I wish Ubuntu or even some other distro would step up to plate and beat microsoft to putting an OS , thats truly solid  and user friendlyfor a 64-bit architecture...such a good opportunity for Linux!!!! I know there is a lot involved, especially getting apps to work, but it needs to be done.

Just my thoughts.

---

### Post by jtaylor on 2006-05-09
Thanks a lot.  This worked for me.  To help googlers I have a Shuttle XPC computer.

lspci -v showed:
0000:02:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer: Unknown device 3038
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at ee00 [size=32]
        Capabilities: [dc] Power Management version 2

---

### Post by leif3d on 2006-10-05
Wow! I'll try this when I get home...this was driving me crazy....the weird thing is ...5 out of the 10 installs I've done on the same computer have recognized my sound card (Audigy SE) and 5 times it hasn't...I hate that about Ubuntu...that randomness...but oh well...it's free :D

---

### Post by jsundqui on 2006-12-05
Are there any modifications that anyone can think of for trying this on Dapper?  Use the same gcc version?  The .deb link is already broken but I would assume just go with the lastest version there (apparently 1.0.13-2).

Any help would be appreciated.  I thought my speakers would blow with the static pumped out through this cheap audigy with dapper!

---

### Post by SubWolf on 2006-12-09
Just plugged the card in running Edgy, worked with no changes or mods required.

However, just gotta get KMix to change it's default control when you single click, and wish the controls were a bit more varied.

---

### Post by remick182 on 2007-01-15
I ran this setup, but it didn't help.  I mean, everything already worked except for in-game sound.    I have an onboard sound card (AC '97) on an Intel m-board and I can't figure out how to get rid of it!  My Audigy SE that I recently installed works for system sounds, dvd's, bmp, internet, etc.  As soon as I load up a game, however, it won't work.  Whether it's Tux Racer, Neverwinter Nights, Unreal Tournament, I can't get my Audigy to pick up the sound.  As soon as I plug my speakers into the onboard line out port, in-game sounds and music work.

I've changed my System-->Preferences-->Sound to all Alsa settings.  No joy.  Any ideas on how to disable the onboard card?

---

### Post by remick182 on 2007-01-15
Whew!  I finally got it working.  I had to rummage around throught my BIOS to finally find the option to disable the onboard sound.  I wasn't sure if it would work because the way it was laid out, it just said "Audio" and from the place it was at in the BIOS I thought that it would only disable the system beeps.  I was wrong and I now have sound for my games in Linux!  

I just keep getting closer to a Linux only box!  Keep up the good work everyone!

---

### Post by Pablasso on 2007-01-24
this card is 7.1 right? do you know if it works well on a 5.1 home theater?

getting the right card to work with my simple 5.1 sorround system has been a pain :mad:

---

### Post by buzka on 2007-01-28
No, this card is 5.1. I have a little weird probs. I'm running alsamixer and there is no PCM. I'm installing latest drivers (source + base) and I'm still had same probs, alsamixer recognized my sound card.

lspci -v
0000:04:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs: Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 225
        I/O ports at a000 [size=32]

In alsamixer:
Card: CA0106 
Chip: none 

Ubuntu 6.06

sorry for my english :s

---

