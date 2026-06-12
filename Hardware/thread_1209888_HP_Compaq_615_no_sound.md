---
title: "HP Compaq 615 no sound"
date: 2009-07-10
forum: Hardware
---

### Post by aphx on 2009-07-10
Hi
Bought this laptop today, installed Ubuntu 9.04 on it, everything works great, but I can't seem to get the sound to work. I had Ubuntu installed on my desk computer a while ago (dual boot with win xp), but I didn't use it that much or as serious as I plan to do now, so my knowledge of the system if fairly weak. Anyway, if someone could please help me, I would be greatful.

And another thing that I would like to know, the laptop has an integrated graphics card (Ati Radeon HD 3200), so I was wondering if that would maybe stop me from getting, let's say, transparent windows working, and stuff like that, all the kewl effects? ^^ 'Cause I've got the Konsole terminal and when I try to customize the profile and enable transparent windows it says that my background doesn't support that kind of stuff or something like that. And whan I try to enable the transparent windows in general in CCSM I can't find the tab (I saw it in some tutorial, but the tab isn't even there in my case)

Thanks in advance ):P

---

### Post by fisk0 on 2009-07-30
I bought that model a couple of days ago as well, and am having the same problem. I've looked around and it seems there is a common problem with the HDA ATI SB sound drivers used in most HP laptops, there are guides on how to fix it, but it seems you have to write different stuff in the alsa config for all the different laptop models, and I can't find the Compaq 615 on the list.
Seems most people (on those other laptop models) also only have problems with the internal speaker not working, but they still get sound from the headphones, but I can't get any sound from either.
It's not limited to Ubuntu though, I tried Mandriva Linux One 2009.1 too, and couldn't get sound there either.
Might be worth trying OpenSUSE or Novell SUSE Linux though, since it seems that's the distro HP sells some of their laptops with. I haven't tested SUSE on it yet though.

As for the Radeon HD3200, I think it should work with desktop effects. I haven't tried it myself yet, but I was looking around before I bought the computer and the HD3200 is supposed to be able to handle that kind of stuff.

---

### Post by point6 on 2009-09-14
Hello I had exacltly the same problem (found this thread while searching for a sollution, also one of the reasons why I am writing here).

The sollution for my HP615 is to add:

options snd-hda-intel model=hp-dv5

at the bottom in /etc/modprobe.d/alsa-base.conf

alsa-base.conf can be opened up with the text editor of your choice, but you need to be root or use sudo.

you can restart the sound with: sudo alsa reload (or use force-reload)

---

### Post by mr-pink on 2009-09-21
I was planning to buy just this laptop, so I was looking for infos about Ubuntu compatibility when I found this post. Can you tell me if everything works in Ubuntu (suspend, NIC, wifi-card, etc.)? Is there any kind of issue (apart from the sound problem which seems solved)?  Would you suggust me to buy it?

---

### Post by i_doc on 2009-09-21
Hi 
I have had this notebook about a week now and am very satisfied.  it came with Vista home basic which was quickly replaced by ubuntu. Everything works except the sound! I have tried the above but still no sound. Any other suggestions anyone??

---

### Post by mr-pink on 2009-09-22
> **i_doc said:**
> Hi 
I have had this notebook about a week now and am very satisfied.  it came with Vista home basic which was quickly replaced by ubuntu. Everything works except the sound! I have tried the above but still no sound. Any other suggestions anyone??

Have you tried this: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/61903](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/61903) ? Let us know if it works for you. What about suspend and hibernate?

---

### Post by i_doc on 2009-09-23
Thank you!! Initially it didn't work but then used the latest version update - 


alsa-driver-linuxant_1.0.20.3


 Have a look here:


 [http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php](http://www.linuxant.com/alsa-driver/downloads-ubuntu-x86_64.php)


_[U]Hiberate and suspend seems to work_[/U]. Once again Thank you

---

### Post by point6 on 2009-10-11
A part from the sound, I haven't come across any other problems with it. All do it is my GF that is using it. Only main annoyance is that the laptop comes with Vista, so my suggestion is trying to get one with W7 (if the price are the same). Never know if you are forced to use Windows for some obscure program...

The sound seems a bit strange, but my research showed that it is the same driver as "hp-dv5". Since there already exists drivers that work, I would be surprised if this problem isnt solved soon.

---

### Post by Yaba on 2009-10-17
Thanks a lot... I also managed to get it work with the newer driver version.

---

### Post by mr-pink on 2009-10-31
Is there anyone here who has upgraded to 9.10 and can say if everything is still working on this laptop with the new realese of Ubuntu?

---

### Post by force317 on 2009-11-21
Installing Ubuntu 9.10 is not working.

See my recent posting about.

For the moment I am using Linux Mint 7 Installed in Compatibility Mode.

If anybode knows how to get the latest Ubuntu/Kubuntu/Xubutu 9.10 running
on the HP Compaq 615, please post it here.

---

### Post by g3rn1 on 2009-12-01
after update from 9.04 to 9.10 i had no headphone sound, no mic input (internal as external)

first ive performed a alsa update from 1.0.20 to 1.0.21 without success

then point6' solution worked for me

> **point6 said:**
> Hello I had exacltly the same problem (found this thread while searching for a sollution, also one of the reasons why I am writing here).

The sollution for my HP615 is to add:

options snd-hda-intel model=hp-dv5

at the bottom in /etc/modprobe.d/alsa-base.conf

alsa-base.conf can be opened up with the text editor of your choice, but you need to be root or use sudo.

you can restart the sound with: sudo alsa reload (or use force-reload)

in my case i had to change

options snd-hda-intel model=hp-m4

to

options snd-hda-intel model=hp-dv5

at the bottom in /etc/modprobe.d/alsa-base.conf

(sudo alsa reload had no effect, but after restart all worked fine)

----------

2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10

Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec  1 2009 for kernel 2.6.31-14-generic (SMP).

---

### Post by foxy123 on 2010-02-07
I am considering to buy this laptop for my wife and I wonder if you guys still have any issues with it on Karmic/Lucid (if someone adventurous enough to install the latest alpha). Thanks a lot in advance. It is so tiresome and difficult to buy a laptop to use with Linux because of compatibility issues.

BTW, what wifi chip does it use and do you have a decent speed with it?

---

### Post by mohaned_nj on 2010-02-27
hi evey one
i am deciding to buy the same laptop, so call u tell me if it's good with linux or not and which is the best version of linux which support's every thing in it like, sound drive & graphic card

---

