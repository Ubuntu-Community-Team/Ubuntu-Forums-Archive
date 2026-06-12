---
title: "asus laptop f3sv and ubuntu (no sound)"
date: 2008-04-25
forum: Hardware
---

### Post by eraserpt on 2008-04-25
I bought this laptop about 2 months ago and waited for new ubuntu to come out. When i installed it today i had no sound at all :(
I installed ubuntu in some laptops and desktop machines never had a problem. Anyone with this model having no sound at all with ubuntu? 
I tried running with live cd and installing and no luck :(

Any help would be apreciated

---

### Post by ibs137 on 2008-04-25
sooo many ppl hav this problem. i hav it too. i dunno how to fix it.

can anyone help us?

---

### Post by eraserpt on 2008-04-25
You own the same laptop? Or ubuntu gives that many problems with sound cards? All the laptops and desktop machines i didnt have sound problems were realtek audio devices. For what i understand from the asus website, this asus has a intel audio device, might be the problem?

---

### Post by ibs137 on 2008-04-25
no i hav a lenovo 3000 n200 laptop. i think it has an intel audio as well

---

### Post by eraserpt on 2008-04-25
Can you rectify that you have a intel audio device? If so we have the exactly same problem :(

---

### Post by eraserpt on 2008-04-25
Never mind, the intel audio has a realtek chipset :O, ALC660 to be precise! And found tons of posts with alot of problems with sound from back 2006 :S
Anyone help?

Thanks

---

### Post by eraserpt on 2008-04-26
I have been digging around and found some interesting things

lspci gives this:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Seen posts that this issue could be solved as simply adding:
options snd-hda-intel model=asus

At the end of the file /etc/modprobe.d/alsa-base, it didnt work for me :S, Anyone on this forums with this laptop and running ubuntu with sound? there is got to be someone...
Any help will be appreciated 

Thanks

---

### Post by eraserpt on 2008-04-26
Just downloaded and installed the new alsa drivers (driver,libs and utils) 1.0.16 and compiled them. It didnt change anything, still no sound from speakers or headphones :confused:
In windows xp all works so it isnt the hardware! :(

---

### Post by ibs137 on 2008-04-26
we both hav exactly the same sound card and mine doesnt work either...

dont tell me i hav to go back to xp again!!!

---

### Post by eraserpt on 2008-04-26
ibs137 did you checked your thread? seems to be there a working solution for your lenovo laptop.

[quote=biggahed]The output should be:
"00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)"

If its the same, enabling the sound should be as easy as opening /etc/modprobe.d/alsa-base and adding some stuff

$sudo gedit /etc/modprobe.d/alsa-base

After that, find the line that says "options snd-hda-intel" and change it to "options snd-hda-intel model=lenovo"[/quote]

I hope this work for you, apparently this solution doesnt work for my asus :(

---

### Post by eraserpt on 2008-04-26
[quote=http://www.linlap.com/wiki/Asus+F3SV] Kernel versions older than 2.6.22 may not properly support the sound in the Asus F3SV. If that is the case for your setup then you will either need to upgrade to kernel 2.6.22 or to install the latest development ALSA drivers (at least version 1.0.15rc3). [/quote]

I have ubuntu 8.04 with kernel 2.6.24 and alsa drivers 1.0.16 :confused:

[quote=http://www.linlap.com/wiki/Asus+F3SV] The Asus F3SV works well with Linux as long as you use a distribution which is up to date. Currently Ubuntu 7.10, OpenSUSE 10.3 and Mandriva Linux 2008 work great. [/quote]

You got to be kidding :lolflag:

what the hell am I doing wrong? ](*,)

---

### Post by eraserpt on 2008-04-26
After so many digging i solved it :popcorn:

[quote=https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]
Method H: Straight forward for ASUS F3Sa and maybe others

    *

      does work: ASUS F3Sa
    *

      does not work

First install the latest version of Alsa 1.0.15 final (read this [WWW] howto for 1.0.14 as example!). After, you create a file in /etc/modutils called, for example, 'alsa' with this sequence of aliases and options:

 alias char-major-116 snd
 alias snd-card-0 snd-hda-intel
 # module options should go here
 options snd-hda-intel model=lenovo

 # OSS/Free
 alias char-major-14 soundcore
 alias sound-slot-0 snd-card-0

 # card #1
 alias sound-service-0-0 snd-mixer-oss
 alias sound-service-0-1 snd-seq-oss
 alias sound-service-0-3 snd-pcm-oss
 alias sound-service-0-8 snd-seq-oss
 alias sound-service-0-12 snd-pcm-oss

 options snd-hda-intel model=lenovo

For a secure success, add the last line to the file /etc/modprobe.d/alsa-base too If it doesn't exist, create!

After you must restart. Before you start to dancing, run 'alsamixer' and unmute all channel and set the volume.

This fix was found [[http://ubuntuforums.org/showthread.php?t=605990&highlight=82801H&page=2]](http://ubuntuforums.org/showthread.php?t=605990&highlight=82801H&page=2]) here. [/quote]

I have sound on speakers and headphones :D, this solution works for asus f3sa and now for the f3sv also :D :D :popcorn:

---

### Post by uconvert on 2008-04-26
I have an ASUS Z62FM and had the same problem when Gusty came out.

Create a text file on your desktop and name it sound. Then add this line:
"options snd-hda-intel position_fix=1 model=3stack" (no quotes)
Switch to root and copy this file to the /etc/modprobe.d directory. 

This was the only fix that worked for me.

I lost the thread, so if you find it thank the guy who suggested it back in the days of Gutsy  :)

---

### Post by Furka on 2008-09-20
Sound Problem solved:

append,

options snd-hda-intel model=lenovo

to the end of the file /etc/modprobe.d/alsa-base

worked for my F3sV

---

