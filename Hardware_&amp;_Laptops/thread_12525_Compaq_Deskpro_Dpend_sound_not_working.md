---
title: "Compaq Deskpro Dpend sound not working"
date: 2005-01-25
forum: Hardware &amp; Laptops
---

### Post by 4ebees on 2005-01-25
Hi,

My pc is a Compaq Deskpro Depend

PII 
350MHZ CPU
128M RAM

I've shown a list of the things I have done to resolve this (taken from other posts on site and suggestions made there - I didn't work out ANY of this myself :))


The soundcard is built-in. I've checked the BIOS and it tells me it's irq 5, so I added

acpi_irq_isa=5

to #kopt

in the  

/boot/grub/menu.lst


The tech manual says that the built-in sound card is a 

"...Compaq Premier Sound system. The system board includes an embedded 16-bit full-duplex subsystem based on the ES1869..."


and so I edited

/etc/modules file to include

snd-es1869


Now, the following commands give me no response:

[COLOR=DarkRed]Alsamixer[/COLOR] – nothing
[COLOR=DarkRed]alsaconf[/COLOR] – nothing

The speaker icon on the top right of the screen does not allow me to change anything. It refuses to move. It will not allow me to make an configuration changes.

I have tried: 

[COLOR=DarkRed]lsmod|grep snd[/COLOR] (read this on another post) – nothing. There is no output at all.

On boot, I was getting a “Modprobe Error”. After going through the Unofficial Starter Guide, this appears to have been resolved.

On boot, I have noticed an error saying: 
[COLOR=DarkRed]
pci address space collision in region 7 of 0000 00 14.3 [f800:f83f][/COLOR]

and:

[COLOR=DarkRed]alsacnt[/COLOR] (I think this is the correct term) [COLOR=DarkRed]state 1134 No soundcard. [/COLOR]

I get no sound on boot, I get no sound from the CD player (cable is in place) and I get no sound when viewing the news online.


I've got no idea where to go to from here. I still cannot get sound and still cannot activate alsamixer or alsaconf and the sound icon will not let me change the setting.


Any assistance is, as always, most appreciated.

---

### Post by molio on 2005-01-31
Well I can't be of any assistance yet, but wanted to let you know you're not the only one with this problem. I also have a Compaq deskpro with ES1869 onboard sound and am looking into making it work, 

I have tried the same things you posted above without any luck, but as soon as I make any progress I'll be sure to post it here! ;) I'm also gettin the same errors as you on bootup btw no matter how I configure things in bios.

---

### Post by molio on 2005-01-31
[ESS18xx Alsa support](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx) 

There should be support for the ESS18xx series in also according to the link above, but I'm pretty new to linux and I'm not sure how to go about installing that yet :) But I'll give it a try.

---

### Post by 4ebees on 2005-05-17
Hi all,

I've installed 5.04 

See new post:

[http://www.ubuntuforums.org/showthread.php?t=35147](http://www.ubuntuforums.org/showthread.php?t=35147)

Thanks to everyone.

---

### Post by SickTwist on 2005-05-21
I'm running Hoary on a Compaq Deskpro Dpend.  I also had trouble getting sound to work until I found this solution:

[list]
[*] Save the following lines in the file /etc/modprobe.d/soundcard

```
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0


```

[*]sudo modprobe snd-es18xx
[*]sudo /etc/init.d/alsa restart
[/list]
Voila!  I'm not sure if this will work on Warty or not but I thought I should post it just in case somebody else has the same problem.

---

### Post by suripens on 2005-05-30
Thanks! That worked for me. Should have read your post first! - Suri

[QUOTE=SickTwist]I'm running Hoary on a Compaq Deskpro Dpend.  I also had trouble getting sound to work until I found this solution:

[list]
[*] Save the following lines in the file /etc/modprobe.d/soundcard

```
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0


```

[*]sudo modprobe snd-es18xx
[*]sudo /etc/init.d/alsa restart
[/list]
Voila!  I'm not sure if this will work on Warty or not but I thought I should post it just in case somebody else has the same problem.[/QUOTE]

---

### Post by suripens on 2005-05-31
It didn't last that long. 

I was able to listen to the radio (used Rythmbox) and then got a bit greedy and wanted to listen to MP3s. So, I installed gsstreamer0.8 using apt and then I lost the sound for good. 

Now it plays (I see the bar moving), but, there is no output from the speakers.

What else can I do? Please suggest.

Thanks,
Suri

[QUOTE=suripens]Thanks! That worked for me. Should have read your post first! - Suri[/QUOTE]

---

### Post by suripens on 2005-06-02
[QUOTE=suripens]It didn't last that long. 

I was able to listen to the radio (used Rythmbox) and then got a bit greedy and wanted to listen to MP3s. So, I installed gsstreamer0.8 using apt and then I lost the sound for good. 

Now it plays (I see the bar moving), but, there is no output from the speakers.

What else can I do? Please suggest.

Thanks,
Suri[/QUOTE]
 okay this worked....I removed the options part in the third line i.e., I basically added the following in /etc/modprobe.d/soundcard

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1

then did this - 
# sudo modprobe snd-es18xx
# sudo /etc/init.d/alsa restart

and it worked. Hope it stays this way!

---

### Post by florizs on 2005-06-19
I also have a Compaq Deskpro with an es-1869 soundcard.
There appears to be no sound in Gnome, but I followed the instructions on this post.

after creating /etc/modprobe.d/soundcard and changing it to:

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es1869
options snd-es1869 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=9 dma1=1 dma2=0


when I run:
sudo modprobe snd-es18xx

I get:
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko): No such device
FATAL: Error running install command for snd_es18xx

What is the matter? am I missing a kernel  module? how can I correct this?

thanks in Advance,

---

### Post by hoshi18 on 2005-06-24
[QUOTE=florizs]I also have a Compaq Deskpro with an es-1869 soundcard.
There appears to be no sound in Gnome, but I followed the instructions on this post.

after creating /etc/modprobe.d/soundcard and changing it to:

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es1869
options snd-es1869 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=9 dma1=1 dma2=0


when I run:
sudo modprobe snd-es18xx

I get:
FATAL: Error inserting snd_es18xx (/lib/modules/2.6.10-5-386/kernel/sound/isa/snd-es18xx.ko): No such device
FATAL: Error running install command for snd_es18xx

What is the matter? am I missing a kernel  module? how can I correct this?

thanks in Advance,[/QUOTE]
 I have the same than above...

When /etc/init.d/alsa restart : ESS Audiodrive ES18xx sound card not found or device busy
Ans Error inserting sne-es18xx.... no such device

I have a question indeed....

Should I have something like isapnp running on init.d?

---

### Post by hoshi18 on 2005-06-24
I have a Compaq deskpro where I change Processor to PII 400 and ram to 192M
I installed a savage 4 Video card on AGP instead of Original ATI
+ a 10MB Network card and and Pinnacle Tuner TV with audio input/output!!!
In the BIOS, I choose to disable all in PCI option, remove floppy and serial/printer port
So I can Choose to allocate IRQ 3 / 4 / 5 / 9 / 10 / 11 to any of those card
?? Should I ?? I mean, should I say "network IRQ 11" since in disabled mode it work with ubuntu

Same questions with onboard option from bios
Should I activate the card, or let linux detect and choose DMA/IRQ by itself



So, In gnome, Only BT related (eg Pinnacle TV card) is found

try all above, but cannont access to es1869 pnp onboard card
I try modinfo to check and snd-es18xx is OK...
but cannot see config (Where can I set it, if it is possible?)


May I dream to be able to activate both cards or should I concentrate on TV and forget audio from the es18xx???

Help :)))
New to linux/ubuntu, and not sure of what I'm asking !!!

---

### Post by wvslkr on 2005-06-25
I am not familiar with your TV card, but I do use the 1869.  The only thing I have ever had  to do to get it to work is add to /etc/modules > snd-es18xx isapnp=0. Do not know if your other card will interfere, but I have used this on at least a half dozen debian based distros, plus slack and clones of.

From what I understand from your post, modprobe accepts the card.  You will then  have to enable it under alsa,esd,oss,using your sound config tools in your menu.  if it is working you should be able to play around with the various setups to get sound.  The entry to /etc/modules just makes it permanent so you don't have to modprobe every time you reboot.

GL Hope it helps. :)

---

### Post by hoshi18 on 2005-06-26
Ok,

I had another pb (which was a DVD+R which wasn't reconized for ubuntu install, which I fix) and then I clear CMOS+reconfigure bios+reinstall ubuntu and... it work (with just add lines to modprobe.d)
Still have things make it not perfect (sound quality + pb with TV tuner) but, still sound card work now....
And video4linux is working too... (with only 1 TV software + test for choosing multimedia environement in ubuntu -- don't know why)

 next step -> clustering !!! (arg, they are not anymore supported with 5.04... but there is unoficial CVS for openmosix which I compile for linux image 2.6.11-386....
next in another thread...

---

### Post by Philippe Worontzoff on 2005-10-16
[QUOTE=SickTwist]I'm running Hoary on a Compaq Deskpro Dpend.  I also had trouble getting sound to work until I found this solution:

[list]
[*] Save the following lines in the file /etc/modprobe.d/soundcard

```
alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0


```

[*]sudo modprobe snd-es18xx
[*]sudo /etc/init.d/alsa restart
[/list]
Voila!  I'm not sure if this will work on Warty or not but I thought I should post it just in case somebody else has the same problem.[/QUOTE]

Hi, I have a Compaq Deskpro EN Series (I guess it's the same). I'm on ubuntu 5.10 and there are no /etc/modprobe.d/soundcard file here is the content of /etc/modprobe.d directory:
aliases  alsa-base  arch  arch-aliases  bluez  ibm_acpi.modprobe  isapnp  nvidia-kernel-nkc  toshiba_acpi.modprobe

Do I have to create a soundcard file or to change another file ?

---

### Post by az on 2005-10-16
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28OldSoundCard%29](https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28OldSoundCard%29)

---

### Post by Nedder on 2005-11-27
I had the same issue... here is what worked for me: 

first we want to test the to make sure it's gonna work before we it permanent: 

open a terminal window and get ready to type!!!
start a "root" terminal session: 

[COLOR="DarkRed"]# sudo -s [/COLOR]

Enter yor password then type the following to create then jump to a new directory:

[COLOR="DarkRed"]# mkdir /etc/modprobe.d/soundcard
# cd /etc/modprobe.d/soundcard[/COLOR]

Now create a new file called snd-es18xx and edit it:

[COLOR="DarkRed"]# gedit snd-es18xx[/COLOR]

Add the following to the newly created file: 

[COLOR="DarkRed"]alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0[/COLOR]

NOTE:  if you are unsure of your soundcards setting they should be listed in your bios!

Save and exit the file.

ok... let's test it! Type:
 
[COLOR="DarkRed"]# modprobe snd-es18xx
# /etc/init.d/alsa-utils -restart[/COLOR]

Now open your volume control - if you have the gui loaded double click the little speaker beside the time. 

It should open now (if there was no sound device loaded it would spit out an error). 

ok... play a wav or something.    Got sound?... if so Great!(don't go anywhere)... if not don't worry.   On the volume control make sure you are not muted(default). Still no sound?  ok  lets try the OSS driver. 

On the Volume Control goto [COLOR="DarkRed"]File[/COLOR] then [COLOR="DarkRed"]Change Device[/COLOR] and choose [COLOR="DarkRed"]Ess AudioDrive ES1869 (OSS Mixer)[/COLOR]

make sure it's not muted and turn the volume up.  Now you should have sound. 

If you reboot your system now the module we added will no longer be loaded with the kernel and you will have no sound.  To make it permanent type:

[COLOR="DarkRed"]# gedit /etc/modules[/COLOR]

Add the following string to the end of the file:

[COLOR="DarkRed"]snd-es18xx[/COLOR]

Save and Exit... reboot your system and you will have sound!

Hope this works.  Worked for me.  

Nedder ;)

---

### Post by markiisi on 2005-12-10
[QUOTE=Nedder]
Hope this works.  Worked for me.  

Nedder ;)[/QUOTE]
Yay! I just followed those steps exactly, in a fresh install of Kubuntu 5.10, and it .. just worked for me also. Thanks! Painless tweaking. ;)

---

### Post by FliesLikeABrick on 2005-12-25
I just installed kubuntu 5.10 on my father's 400mhz compake Deskpro dpend and followed those instructions 2 posts above... worked perfectly :P

now onto the printer and scanner...

---

### Post by Nameeater on 2006-01-01
Nedder's directions worked awsome for me and 5.10/Breezy, thanks :)

---

### Post by 4ebees on 2006-01-05
Hey Nedder,

Thanks for the information. It /seems/ to have worked on a Compaq Armada 1598dt that I've been playing with. Alsamixer starts up and lets me make changes, the sound icon appears and lets me change the volume setting. The present problem, if you're able to help out, is that after installing the requisite codecs, when I try to play an MP3 sound file (one that I know works and have copied from another machine) in XMMS, I get a message:

"Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard"

I've tried various options in XMMS but to no avail.

I've tried using the OSS option (as opposed to ALSA) but that doesn't help.

I'm not sure what else to try.

Any ideas (anyone)?

Any assistance will be most appreciated.

---

### Post by mweston on 2006-02-03
I followed the instructions - created the soundcard folder and the etc/modprobe.d/soundcard/snd-es1879 file, but my 7400 still doesn't detect any sound hardware.
I get "FATAL: Module snd_es1879 not found."

Not sure why it displays an underscore instead of a dash in the file name....
Any other ideas? 

I'm trying to migrate from Windows, so my knowledge of Linux is very limited.....go easy on me.

Thanks

---

### Post by mweston on 2006-02-03
fixed snd-es1879 to read snd-es18xx.
Now it works.

tks,

---

### Post by mweston on 2006-03-12
Nedders instructions worked great for Breezy.
 I just installed Dapper, and I have the problem again. I can get sound - but I can't make it permanent - there is no /etc/modules folder under Dapper.

Where did the modules folder go to ?

Armada 7400 333 mhz - ESS1879 sound.

---

### Post by mweston on 2006-03-13
Nevermind - looks like "modules" isn't a folder - just a file.
Hooray - I have sound again.....now on to my wireless problem.

---

### Post by zo0o0ot on 2006-07-04
> **Nedder]I had the same issue... here is what worked for me: 
.......

ok... let's test it! Type:
 
[COLOR="DarkRed"]# modprobe snd-es18xx
# /etc/init.d/alsa-utils -restart[/COLOR]

Now open your volume control - if you have the gui loaded double click the little speaker beside the time. 

It should open now (if there was no sound device loaded it would spit out an error). 
......

Save and Exit... reboot your system and you will have sound!

Hope this works.  Worked for me.  

Nedder  said:**
> 

FYI, I also have a compaq Armada 7400 and I am doing an install of Kubuntu 6.06-

I had to type in your command slightly differently to get it to work.

[QUOTE]sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                 [ ok ]
 * Setting up ALSA...                                                    [ ok ]

Apparently , it's now "restart" instead of "-restart".
I did sudo operations instead of using the root shel, and l used kate instead of gedit.
Kmix was already up, so I had to restart it in order to get the soundcard to be recognized.
Without the help of this thread, I would have been completely lost.  Thank you to all.
I am going to restart and see if the sound has been permanently installed.

---

### Post by zo0o0ot on 2006-07-04
It does work.  Good deal.

---

### Post by frisket on 2007-01-29
> **suripens said:**
> Thanks! That worked for me. Should have read your post first! - Suri

Perfect...did it for me too, many thanks.
Why this doesn't get detected at install time baffles me.

---

### Post by Woodsy on 2007-02-23
> **Nedder said:**
> I had the same issue... here is what worked for me: 

first we want to test the to make sure it's gonna work before we it permanent: 

open a terminal window and get ready to type!!!
start a "root" terminal session: 

[COLOR="DarkRed"]# sudo -s [/COLOR]

Enter yor password then type the following to create then jump to a new directory:

[COLOR="DarkRed"]# mkdir /etc/modprobe.d/soundcard
# cd /etc/modprobe.d/soundcard[/COLOR]

Now create a new file called snd-es18xx and edit it:

[COLOR="DarkRed"]# gedit snd-es18xx[/COLOR]

Add the following to the newly created file: 

[COLOR="DarkRed"]alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0[/COLOR]

NOTE:  if you are unsure of your soundcards setting they should be listed in your bios!

Save and exit the file.

ok... let's test it! Type:
 
[COLOR="DarkRed"]# modprobe snd-es18xx
# /etc/init.d/alsa-utils -restart[/COLOR]

Now open your volume control - if you have the gui loaded double click the little speaker beside the time. 

It should open now (if there was no sound device loaded it would spit out an error). 

ok... play a wav or something.    Got sound?... if so Great!(don't go anywhere)... if not don't worry.   On the volume control make sure you are not muted(default). Still no sound?  ok  lets try the OSS driver. 

On the Volume Control goto [COLOR="DarkRed"]File[/COLOR] then [COLOR="DarkRed"]Change Device[/COLOR] and choose [COLOR="DarkRed"]Ess AudioDrive ES1869 (OSS Mixer)[/COLOR]

make sure it's not muted and turn the volume up.  Now you should have sound. 

If you reboot your system now the module we added will no longer be loaded with the kernel and you will have no sound.  To make it permanent type:

[COLOR="DarkRed"]# gedit /etc/modules[/COLOR]

Add the following string to the end of the file:

[COLOR="DarkRed"]snd-es18xx[/COLOR]

Save and Exit... reboot your system and you will have sound!

Hope this works.  Worked for me.  

Nedder ;)

This worked perfect for my Compaq AP400 although at first I was replacing the "18xx" with my sound model "1869" doh!  Thanks Nedder!

---

