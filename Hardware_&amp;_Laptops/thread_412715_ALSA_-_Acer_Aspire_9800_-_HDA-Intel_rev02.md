---
title: "ALSA - Acer Aspire 9800 - HDA-Intel rev02"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by zeroXcool on 2007-04-18
Hi There all you masterminds and big-brains ;)
At first, my english is not the best but i hope you can understand my problem !

So...I have no Sound on my Acer Aspire 9800 it got an INTEL/REALTEK High Definition Audio (INTEL ICH7 HDA)
Details @ [http://samuel.benoit.online.fr/linux/kubuntu_linux_on_acer_aspire_9814_wkmi_9800_series.html](http://samuel.benoit.online.fr/linux/kubuntu_linux_on_acer_aspire_9814_wkmi_9800_series.html)

I tryed many Distributions with different Alsa Drivers 13 & 14 (compiled by source),
but only the standard-alsa of newest Debian and Suse give me Sound, but only over the SPDIF(shared with Headphone).
I need Sound from the Internal Laptop Speakers and i need it with UBUNTU ;)
So if anyone can help me or give a hint please post :)
If there are any aditional informationed needed just ask ;)
greeeeeetz z.c

---

### Post by Rospo Zoppo on 2007-04-18
[http://https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29]("http://https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29")

---

### Post by zeroXcool on 2007-04-19
thx for the hint but i've done this 100times ;) compiled all releases of alsa from 13 to 14 and checked all mixer settings....oh and i tryed many models from alsa configuration.txt

---

### Post by Rospo Zoppo on 2007-04-19
The problem is not the drivers but the configuration of /etc/modules and /etc/modprobe.d/alsabase (o something like that)...

---

### Post by unghione on 2007-04-22
I've the same problem, same laptop, and tried to compile configure set everithing in every forum...
PLEASE!!! if someone knows how to make this internal speaker working, let us now!!

just an hint, with the latest hg driver installed i found a mismatch in alsactrl on the headphone, but i don't know how to fix it! It could be it!

---

### Post by Rospo Zoppo on 2007-04-23
post alsamixer...

---

### Post by califalcon on 2007-06-28
I have the same ACER Aspire 9810 and no sound thru speakers only thru SPDIf/headphones, we really need a solution for this problem, can anyone out there tell us how to redirect the output channel from spdif to speakers?

Tried everything out there and no luck, I love Ubuntu however I am not happy with the lack of support for certain hardware, specially when so many people have the same problem.

Thanks.

---

### Post by matheuu on 2007-06-28
This is what I get in my alsamixer.  I have a toshiba a200 satellite. with no sound from anywhere!

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.13 (Press Escape to quit)
&#9474; Card: HDA Intel                                                              
&#9474; Chip: Realtek ID 268                                                         
&#9474; View: [Playback] Capture  All                                                
&#9474; Item: Master [dB gain=0.00, 0.00]                                            
&#9474;                                                                              
&#9474;           &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                                              
&#9474;           &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;            
&#9474;                                                                    &#9474;MM&#9474;             &#9474;MM&#9474;         
&#9474;                                                                     &#9492;&#9472;&#9472;&#9496;             &#9492;&#9472;&#9472;&#9496;            
&#9474;         100<>100         100<>100                                                          
&#9474;        < Master >          PCM                         Caller I         Off-hook           
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by matheuu on 2007-06-28
NO SOUND and have tried all the "fixes".

---

### Post by jwater7 on 2007-06-28
I have a Toshiba A205, this also has the Realtek 268 and no sound from speakers.  With the latest HG version of alsa, the sliders appear, but still no sound.  Have also tried the "3stack" option.

---

### Post by califalcon on 2007-06-28
Is anyone working on how to fix this problem?
It doesn't look like it.

---

### Post by brightsmile on 2007-06-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Realtek 268 doesn't seem to be supported yet.

-- check here:
[https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)

Let's all try to convince Chris Cheney there to work on a patch?  ;)

---

### Post by jwater7 on 2007-07-02
A bug was posted here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3165)
(log in as guest if you'd like)

The patch/comment mentioned yesterday fixed it for me.

---

### Post by zeroXcool on 2007-11-28
**Update: ** Hey there....so I still have my Aspire 9800 with WinXP because there is no sound with Alsa-Drivers....but I have some new informations for you...there is a guy named gruemaster or something like that and he seams to know what the problem is...he told me that the driver should work but there are problems with the wireing of the speakers in aspire 9800 because of this there is no sound coming out of the internal "3D-"Speakers ;) sadöy he couldn't fix the driver 4 me...but i think this is much work to do...

So if anyone finds a solution post post post ;)

---

### Post by Yife on 2007-12-11
Hi there,

You will not like to read this here on Ubuntu forums, but I am a happy Fedora user, on that same Acer Aspire 9810 laptop. And guess what, I have got the same bloody problem: no sound from the internal speakers...

But you did help me a lot allready as I did not know sound was working through the headphone (did not try that before). So finally I got some sound from my machine... If only those internal speakers would work...

The strange thing however is that sound was working for me using Fedora 7, but not anymore after upgrading to Fedora 8...

Maybe this information is of some help to somebody...

Yife

---

### Post by Yife on 2007-12-11
Hi again,

I did it! Sound from the internal speakers, and from the headphone, whenever I want too!

This thread gave me the solution: [http://ubuntuforums.org/showthread.php?t=616845&highlight=ad1981+solved](http://ubuntuforums.org/showthread.php?t=616845&highlight=ad1981+solved)

For my specific ( Fedora 8 ) case:
I had to add this line "options snd-hda-intel model=acer" to the /etc/modprobe.conf, and reboot the machine...

Hope it helps someone else!

Thanks a lot, as it helped me!

Yife

---

### Post by gfd_2 on 2007-12-11
This works! 

I've been trying for the last 3 weeks to get sound on my Acer 7720 laptop to work... nothing in Ubuntu, Mandriva, Puppy... had to reinstall after NUMEROUS suggested fixes FUBARed things up to the point of no return.... and I held my breath with this one.... but it works! Ripped some Stones after following the steps and viola! SOUND.

Link: [http://www.antonywilliams.com/](http://www.antonywilliams.com/) 
(scroll down to the bottom)

Here's the article: "Most of the laptops I've owned have had trouble with sound to some degree. The only solution is to compile the latest version of alsa manually, as most GNU/Linux distros have an out of date alsa (even the recently released Ubuntu 7.10 - Gutsy Gibbon)

This wouldn't be a big deal, but every time you get a kernel update, you have to compile alsa again. This can become a bit of a pain, so I wrote a bash script that would do it all for me.
First the script will download all alsa's dependencies. Then it will download:
alsa-driver-1.0.15.tar.bz2
alsa-lib-1.0.15.tar.bz2
alsa-utils-1.0.15.tar.bz2

it will then extract them (whilst deleting the .bz2), move them to /usr/src/alsa and compile them each.

just copy the first block of text to a text file and save as alsa_1.sh, and then the second block to alsa_2.sh and then cd to it in a terminal and type "sudo sh alsa_1.sh"
then reboot, and then type "sudo sh alsa_2.sh"
(make sure the scripts have execute privileges. (by typing "chmod a+x alsa_1.sh")

#!/bin/sh
#
#install necessary stuff
apt-get install build-essential ncurses-dev gettext
apt-get install linux-headers-`uname -r`

echo "downloading alsa packages..."
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)

echo "extracting alsa packages..."
tar -xjf alsa-driver*.tar.bz2
tar -xjf alsa-lib*.tar.bz2
tar -xjf alsa-utils*.tar.bz2
rm alsa*.tar.bz2

echo "setting up alsa for compilation"
mkdir -p /usr/src/alsa
mv alsa-* /usr/src/alsa

#alsa-driver
cd /usr/src/alsa/alsa-driver*
./configure --with-cards=hda-intel
make
make install

#alsa-lib
cd /usr/src/alsa/alsa-lib*
./configure
make
make install

#alsa-utils
cd /usr/src/alsa/alsa-utils*
./configure
make
make install

echo "now reboot your machine, and run alsa_2"
#end of alsa_1




#!/bin/sh
#for after reboot
cp -v /lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.22-*/kernel/sound/
depmod -a
#end of alsa_2


note, in its bare form, this will work in any distro, but my script installs the dependencies using APT (so this will only work for debian based distros - Debian, Ubuntu, LinuxMint, Mepis etc..)

also, alsa_2 is assuming kernel 2.6.22. If you have a different kernel, or several .22 kernels, you'll need to specify. Also, my script compiles the alsa-driver for intel-hda sound cards. This is the most common card for laptops (if you have an intel processor, chances are you have it). If not, replace with your sound cards name

"

NOTE:  I had to add a line about model=acer as per one of the comments

---

### Post by unghione on 2008-02-21
Finally, after months... problem solved by alsa team.
I tried the ubuntu beta 8.04 and it includes the alsa 16 drivers.
On the ALSA-Configuration.txt there is an option to put in "/etc/modprobe.d/alsa-base":
options snd-hda-intel model=acer-aspire

just doing that and rebooting or restarting the alsa-service will give you sound.
I tried in an acer 9804 model and in an acer 9814 model (my friend's) and it was indipendent from how i left windows (booting it first or not).
Hope this will help.

(Note that 8.04 is still beta and have a known bugs like f.e. nautilus doesn't read "network://".
So either you try that beta, stick with the bugs and wait for the final release or just install the alsa driver ver.16 and then post us if it's working that way. I think it will, though. :-))

---

