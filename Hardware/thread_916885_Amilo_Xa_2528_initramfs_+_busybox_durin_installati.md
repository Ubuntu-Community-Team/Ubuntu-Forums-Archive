---
title: "Amilo Xa 2528: initramfs + busybox durin installation"
date: 2008-09-11
forum: Hardware
---

### Post by grispa on 2008-09-11
Hi!
Let me apologize in advance if I'm posting about a problem already known and solved. I indeed found something at launchpad but nothing that actually solved my problem.

So here it is: I have an Amilo Xa 2528 (specs: [http://sp.fujitsu-siemens.com/dmsp/docs/ds_amilo_xa_2528_29.pdf](http://sp.fujitsu-siemens.com/dmsp/docs/ds_amilo_xa_2528_29.pdf) )and a problem.
The problem: I cannot install ANY Linux distro. I tried all the major, including Gentoo (it hanged before I could face the configuration problems, thanks God..).

The problem: launching the liveCd (or the direct installation), after few lines I get the following lines:

[xx.xxxxxx] ata1.00: status: { DRDY }
[xx.xxxxxx] ata1: soft resetting link
[xx.xxxxxx] ata1.00: configured for PIO3
[xx.xxxxxx] ata1: EH complete
[xx.xxxxxx] ata1.00: exception Emask 0x0 SErr 0x0 action 0x2 frozen
[xx.xxxxxx] ata1.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
                     cbd 12 00 00 00 24 00 00 00  00 00 00 00 00 00 00 00
                     res 40/0000000000/0000000000/00 Emask 0x4 (timeout)

This screen keeps repeating on and on.

I tried with ubuntu 7.10, 8.04, 8.04.1, 8.10 Alpha 5. All of them both x32 and x64.

I figured it is a problem with the nForce 4 SATA. I tried all_generic_ide and noapic, with no success.
So, I hope you can see better than I do.. I certainly am sick ov Vista..

Thank you!

---

### Post by phidia on 2008-09-11
As you said there does appear to be a [bug reported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/163637") for this problem.
From what I skimmed there it seems like the testing release, now in alpha 5, might be worth a shot.
I'm using [it]("http://cdimage.ubuntu.com/releases/intrepid/alpha-5/") on my desktop without any problems.

---

### Post by grispa on 2008-09-13
So, here I am again..
I tried with Intrepid Ibex alpha 5, and it SEEMS to work. But another problem came up, this time with the cpu's clock management.
I reported this problem on launchpad but I had no answer yet.

So, for the moment, I'd like to keep bugging you ( :) ) about this problem.

I hope you can come up with a solution.. Vista is REALLY deteriorating my nerves...

Cheers!

---

### Post by utklasad on 2008-09-23
Dohe, it would be nice if next Ubuntu release will work! I've been waiting for like a half year for a working dist to Amilo XA 2528..

I've manage to install many dists, but some dists give no sound, and some no dvd, ubuntu 8.04 gives slow processor etc. But this new release of Ubuntu seems to fix some problems! Can't wait!

---

### Post by marksken on 2009-04-14
Any luck to install a full working distro on Amilo Xa 2528

---

### Post by gedesby on 2009-05-15
i got the dvd to work after i downloaded 9.04 from a french ditso.

here is the adress
[http://74.125.79.132/translate_c?hl=da&langpair=auto%7Cda&u=http://www.neufgiga.com/n/50-17/share/LNK711849f2dacf0e171/&rurl=translate.google.com&usg=ALkJrhivDqVTy7d_nNDKG4AR2AINZfbq2w](http://74.125.79.132/translate_c?hl=da&langpair=auto%7Cda&u=http://www.neufgiga.com/n/50-17/share/LNK711849f2dacf0e171/&rurl=translate.google.com&usg=ALkJrhivDqVTy7d_nNDKG4AR2AINZfbq2w)

still to fix:
sound and
webcam

---

### Post by marksken on 2009-06-06
i found a config file for kernel 2.6.29.1 that makes the dvd-drive work but because i'm new in linux i dont know how to use it, maybe someone could compile a kernel with that config a send it to me ? For the moment i'm using ubuntu 9.04 everything works except for dvd-drive and webcam and remote

thanx Mark

ps remove the .doc extension from attachment (forum would not take .config file so i renamed it by adding .doc)

good luck

---

### Post by Jannick on 2009-08-18
I have the same laptop (Amilo xA2528) and the same problem... Currently I'm downloading the 2.6.29.1 kernel, and i will try the config file in a few days ;-)

---

### Post by Suhbas on 2010-04-07
Hi there, 

My English isn't so good, sorry about that, I'm from Netherlands.

This is a standard problem for the Amilo Xa 2528 series, I had it too. 
Also everybody who tried to install Ubuntu on this type Notebook, runs into that problem. 

I've finally got it running, and it's very easy to fix. (when you know it although)

By the way - The DVD Drive is the problem, the driver for the device isn't matchable. 
It means that whatever version of Ubuntu you install on your Amilo Xa2528, it just wont run after the boot/setup menu. 
You get the Busy box problem.
It's some kind of odd DVD dual layer drive thing. 
Don't know exactly:P

This are Solutions, Solution 1 is: To create a Bootable [[COLOR="Blue"]USBFlashDRIVE[/COLOR]]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/").
That worked fine for me, used Unetbootin to.

I think older versions of Ubuntu have integrated Live USB.
So if you've another PC with ubuntu installed on it, it can create A live boot able USBstick, or whatever you're wishing to boot from. 
(Other wise you can USE Unetbootin, no matter what OS.)
This is explained on the second Solution [[COLOR="Blue"]LINK[/COLOR]]("http://news.softpedia.com/news/Alternative-Installation-Methods-for-Hardy-86977.shtml") 

The other way, is to make a LAN boot [[COLOR="Blue"]LINK[/COLOR]]("http://news.softpedia.com/news/Alternative-Installation-Methods-for-Hardy-86977.shtml")

[B][U]Just 1 thing You maybe got to know, to not get confused:
 I Used Unetbootin under Windows (xp) and created/formatted a FAT (no 32) Bootable USB disk,
 Containing Ubuntu 9.10 Karmic Koala Live.
 
I run it live from a 1gb USB stick, and installed it with Ubuntu started(live)[/U][/B]

I hope my English is understandable:P

If something is not clear, let me know

Greetz

---

### Post by peterrey on 2011-01-14
Hail to the forum, sorry my english (I'm Italian), after several tests I managed to install Ubuntu on Amilo Xa 2528 (thanks fujitsu:evil: ...) the problem now is that I can not mount the cd / dvd, I have heard of set the kernel, etc. ... but I am new to linux, can someone kindly help me
 thanks

---

