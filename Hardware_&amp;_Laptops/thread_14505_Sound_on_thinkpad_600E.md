---
title: "Sound on thinkpad 600E"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by viuks on 2005-02-08
Hi!
I have realy big problems to get soundcard detected on my 600e. I get the sound working running mepislinux with 2.4 kernel by adding file called 'sound' in my modutils folder, but it seems not to work woth ubuntu.
Is there some 600e user, who can help me to find it out?
In ubuntu wiki supported laptops, it says, that i just need to change driver to cs4236... but where and how? Pls help!

---

### Post by michele on 2005-02-09
Hi

same thing here.
I had the same problem with Mandrake and I wasn't able to find a solution.
Only CD playing would work.

Try

[http://panopticon.csustan.edu/thood/tp600lnx.htm](http://panopticon.csustan.edu/thood/tp600lnx.htm) 

and 

[http://www-307.ibm.com/pc/support/site.wss/MIGR-4BP6Q6.html?selectarea=SUPPORT&brand=root](http://www-307.ibm.com/pc/support/site.wss/MIGR-4BP6Q6.html?selectarea=SUPPORT&brand=root)

let me know if you find a solution

---

### Post by viuks on 2005-02-09
I have tryed a lot and different ways. I sed, that it was easy on mepis, but it just does not work with ubuntu. And I don't know where is the problem. It has to be some way, becouse ubuntu says that it works..., but how???

---

### Post by michele on 2005-02-09
where does it say in ubuntu that it works?

I am still trying out things. I'll let you know if I find anything, but I wouldn't hope too much

M

---

### Post by grj on 2005-02-09
In a terminal windows type

sudo lsmod | grep 42
enter password when prompted

look for a module named something like snd-cs4232

if it is not there type

sudo modprobe snd-cs4232

if that fails type

sudo lsmod

and look for something relating to snd etc.

---

### Post by king20878 on 2005-02-10
After months of on-again off-again struggles trying to get this working, and trying just about every proposed solution, I FINALLY got this working last night.  \\:D/  I hope someone else may find this helpful.  I'm sure this explanation will not be complete and I've tried so many different configurations that some of my config files may be "special" so I hope other people will try this and if they have success, we can come up with a HOWTO.

1. Install **polypaudio**.  This is what finally did it for me.  Sound in all applications (so far) and multiple sounds at once.  I was blown away.  After installation you may have to launch this manually with "polypaudio -D" after you have loaded the modules.

2. I have a file in /etc/modutils/ called sound.  It contains:
[INDENT]alias char-major-14 cs4232
options cs4232 io=0x530 irq=5 dma=1 dma2=0[/INDENT]
These values are from Jeremy Zawodny's page.  Make sure you run: "sudo update-modules" after creating this file

3. "sudo modprobe cs4232"

4. "polypaudio -D"

5. Check your volume setting in Applications - Multimedia - Volume Control

6. Run "gstreamer-properties" and make sure it is set to output to ESD

7. Try playing something.

8.  Flame me if this didn't work. (j/k)

There is quite possibly something unique about my setup, so if this fails for you, let's try figuring it out.  I would like to put a final nail in the coffin of my 600E sound woes.

---

### Post by viuks on 2005-02-20
Following HOWTO I get sound on fresh warthy installation. But now, I'm realy idiot, but cant find out where to add modprobe, to load soundcard driver on boot. :-k

---

### Post by Kemotaha on 2005-03-01
Any one else getting and error when you modprobe the cs4232 module?  I am getting this error:

FATAL: Error inserting cs4232 (/lib/modules/2.6.10-4-686/kernel/sound/oss/cs4232 .ko): No such device


Any ideas?

Nathan

---

### Post by Kemotaha on 2005-03-01
I finally got the module loaded by going into the bios and disabling quick boot.  However I am unable to hear sound.  The only sound I hear is when I am typing in a terminal and I hit backspace too many times.

---

### Post by king20878 on 2005-03-01
[QUOTE=Kemotaha]I finally got the module loaded by going into the bios and disabling quick boot.  However I am unable to hear sound.  The only sound I hear is when I am typing in a terminal and I hit backspace too many times.[/QUOTE]

Have you checked the volume settings under the multimedia menu?  They often seem to reset themselves.   Also make sure the gstreamer properties are set to use the esd sink.

---

### Post by Kemotaha on 2005-03-01
Yeah,  I have checked the volume settings and no luck.  I am running hoary and that might be the problem.  I hope not.  I gave up on my sound a long time ago and I would love to have it.

Nathan

---

### Post by king20878 on 2005-03-02
[QUOTE=Kemotaha]Yeah,  I have checked the volume settings and no luck.  I am running hoary and that might be the problem.  I hope not.  I gave up on my sound a long time ago and I would love to have it.

Nathan[/QUOTE]

Hi Nathan,

All right.  Let's run down the check list.

1. If I run lsmod I find:

cs4232                  7364  3
ad1848                 33244  1 cs4232
uart401                11556  1 cs4232
sound                  81612  6 cs4232,ad1848,uart401
soundcore              10112  4 sound

2. ps -F | grep polypaudio show it running as a local user process i.e. under user "jeff" in my case .  I'm not sure if this matters.

3. gstreamer-properties is set to use esd as the default output sink.

4. If you launched polypaudio after starting gnome don't expect to hear the desktop sounds.  You have to open the Computer > Desktop > Sound app, uncheck the start sound server option, close it, open it again, check the start sound server option, then close it again for it to relaunch the server  (Note: I have gnome set to launch polypaudio -D at atartup, so it works as soon as I log in.)

5. If you are using something like XMMS to test the sound, make sure it is set to use esd output.

6. Make sure the hardware sound level is set high enough by hitting Fn-PgUp.  This sounds obvious I know, but if I had a nickel for everytime I forgot to do this, I could afford a new laptop.   :mrgreen: 

7.  I have alsa stopped.  Not sure if this matters.

That's all I can think of right now.  If you play an audio stream in XMMS, does it give an error message?  

I hope we can get this figured out for you.

- Jeffrey

---

### Post by spydrmn on 2005-03-02
I don't know if this will be of much help, but I got the sound working using this /etc/modules.conf

# --- BEGIN: Generated by ALSACONF, do not edit. ---
# --- ALSACONF verion 1.0.0rc2 ---
alias char-major-116 snd
alias char-major-14 soundcore
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss
alias snd-card-0 snd-cs4236
alias sound-slot-0 snd-cs4236
options snd-cs4236 port=0x530 cport=0x538 isapnp=0 dma1=1 dma2=0 irq=5
# --- END: Generated by ALSACONF, do not edit. ---


Using aumix I raised all the levels up and used the volume keys (Fn+ Pgup or PgDwn) to test it, then I tweaked it later. It worked for me once, but I haven't tried it again.

~keith

---

### Post by Kemotaha on 2005-03-02
[QUOTE=king20878]
--snip--

3. gstreamer-properties is set to use esd as the default output sink.
--snip --

That's all I can think of right now.  If you play an audio stream in XMMS, does it give an error message?  

I hope we can get this figured out for you.

- Jeffrey[/QUOTE]


I am running hoary so polyaudio is setup to run by default.  I have gone in the gstreamer-properties and set ESD as the default sink however When I try to test it, I get an error saying failed to construct test pipeline for 'ESD-Enlightenment Sound Daemon'


the only one that works is the OSS sink but it just gives me a flat tone coming out of the speakers.

I tried the other things that you said and no luck.

I tried playing a wave file in XMMS and it seems to be stuck at the first note or so and just repeating.  I ran it from the console and I am not seeing any error messages.

Nathan

---

### Post by wolfchri on 2005-03-13
[QUOTE=Kemotaha]Any one else getting and error when you modprobe the cs4232 module?  I am getting this error:

FATAL: Error inserting cs4232 (/lib/modules/2.6.10-4-686/kernel/sound/oss/cs4232 .ko): No such device
[/QUOTE]

Hello Nathan,

i am working since hours on the same issue (Thinkpad 600E, desperatlely trying to get the cs4236 drivers loaded on hoary. How the heck did you solve the problem? Here, it keeps saying "no such device" when I try a modprobe. 

I tried all the howtos, no success. Currentlly I am compiling a new kernel, however, that is real pain on a 600e :-) 

pls let me know how you succeeded.

Thank you a lot!

chris

---

### Post by Kemotaha on 2005-03-13
I never really got the sound going.  I use it mostly at school in class where I don't need the sound.  I did however get the CS4232 module loaded but never got it to output sound.  

I don't have my laptop with me so I am not 100% sure on this but I had to comment out all the sound devices that were trying to load so they didn't error.  I added a file called sound.conf( I think) that was in the /etc/alsa.d?? directory.  I also had do disable the quick boot option in the bios.  I think there was more but I can't remember off hand.

I will check tomorrow on my laptop. and can let you know the specifics.  I found most of it off a post that was here in the forums.  Do a search for 600E.  The sound is a very common problem for that model.  I have dealt with it ever since I switched it over to Linux.  But I can't complain too much.  I would only enjoy the sounds for games and such.  Not having it on my laptop probably makes me focus a little more at school :)

---

### Post by Kemotaha on 2005-03-15
I put a file called sound in /etc/modutils with this in it

alias char-major-14 cs4232
options cs4232 io=0x530 irq=5 dma=1 dma2=0


Hope that helps

---

