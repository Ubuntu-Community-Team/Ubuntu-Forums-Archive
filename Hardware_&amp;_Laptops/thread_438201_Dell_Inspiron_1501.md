---
title: "Dell Inspiron 1501"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Caligula on 2007-05-09
I'm just copying a post I've made in the Dell forums, I don't think they're very active, sorry for cross posting.

Hello all.
I've just yesterday placed an order for the Inspiron 1501. 
The first thing I'm planning to do is install linux on it (probably ubuntu/some other debian distro).
I've stumbled across this post - [http://ubuntu1501.blogspot.com/2007/04/cant-get-feisty-to-install.html](http://ubuntu1501.blogspot.com/2007/04/cant-get-feisty-to-install.html)

Now I don't know if I'll be able to install Fiesty. My inspiron comes with windows vista, so most likely it will have the newest bios, right?
If it does, how can I install linux on it without flashing the bios? I REALLY don't want to flash it, I'm not confident enough to take the risk.

Now I'm afraid I'll be stuck with Vista. If anyone has any information about linux on this Bios, it'll be much appreciated. 


Thanks, 

Josh:)

---

### Post by gerdt on 2007-05-09
Hi, I'm about to buy an Inspiron 1501 as well.
I was wondering, are there any reports about problems installing edgy on the Dell Inspiron 1501?
I was planning to install edgy instead of Feisty.

In any case, if you are able to install edgy, you might be able upgrade to feisty from edgy, in that case you might be able to bypass the feisty-installation-problems.

---

### Post by misfitpierce on 2007-05-09
Just do as the guide says on a sunny day where there is no chance of power going out while flashing BIOS or else you could be screwed. You should be fine.

---

### Post by WinterWeaver on 2007-05-09
Gerdt, you may want to wait a wee bit.

Dell is releasing a range of Desktops and Notebooks with Ubuntu (Feisty) pre-installed, rather than vista.

Just a thought.

WW

---

### Post by gerdt on 2007-05-09
I know, but I heard that their will be no price difference, so in that case I like the idea of having Vista, because my girlfriend doesn't use (and probably will never use...) Linux...
I even heard that the ubuntu-dells will probably be more expensive...

---

### Post by Caligula on 2007-05-09
> **misfitpierce said:**
> Just do as the guide says on a sunny day where there is no chance of power going out while flashing BIOS or else you could be screwed. You should be fine.

Yes... but is that really the ONLY way to do it? I really prefer not to take the risk (brand new laptop and all...).

What about actually installing Edgy and upgrading, as suggested above?

What is the chances of screwing something up by flashing?

---

### Post by henkeC on 2007-05-10
Have installed Feisty on an Inspiron 1501 with no problems whatsoever! (Wasn´t my laptop so I felt I could risk it...;) )
Only thing that didn´t work right out of the box is suspend /hibernate

Cheers!

---

### Post by Caligula on 2007-05-10
guys, guys.
Thanks for the replies, but the question was if it'll work on the 2.1/2.4 Bios, those of you who have succeeded in installing Fiesty/anything else, what Bios version do you have?

---

### Post by dashnak on 2007-05-11
Anyone gotten hibernate to work? I've only gotten suspend

---

### Post by mickbw on 2007-05-12
Hi,

I got my Inspiron 1501 last week and got rid of the Vista virus replacing it with Feisty Fawn 32 bit.  I did have an issue with wireless at first but otherwise everything was recognized.  The Ubuntu on 1501 blog that was listed in the original post was my guide to fixing the wireless issue as well as other ways to optimize my laptop.  

In particular, if you are not an experienced touchpad user, look for the post about qsynaptic to tweak the touchpad settings.   

I can say that I haven't tried setting up beryl yet but there is a post on the 1501 blog that should lead the way to set it up in an easy to understand description.

My specs:
Inspiron 1501
BIOS version 2.30
1 GB RAM

Best of Luck,

Michael:)

---

### Post by twright on 2007-10-30
hi,
i run a 1501 happily on gutsy (bios 2.3) 

the brightness doesn't work :(, i know i could get it working if i flashed the bios down but my drive is setup  with encrypted LVM (no chance of resizing partitions) and the bios flasher is too big to fit on a floppy image for the freeDOS method so unless anyone has any ideas i'll just have to wait till i next feel inclined to flash my bios i'm stuck (oh well, doesn't matter much anyway).

for suspend and hibernate all you need to do is download the linux kernel (as long as you have the right bios)

i've actually written a small program for setting up a 1501, it's available here if anyone's interested:
[http://malwaresupport.10.forumer.com/viewtopic.php?p=238#238](http://malwaresupport.10.forumer.com/viewtopic.php?p=238#238)

---

### Post by gerdt on 2007-10-30
if you're having the same problem as I did, this was my solution:

The brightness keys (arrows up and down in combination with Fn-key).

I thought they didn't work, but after pressing them a few times somehow (don't ask me how) I can make the screen bright again. This only works when connected to the adapter, not while you're on battery.

Hope this helps...

---

### Post by twright on 2007-11-01
the only way i can get it to work is manually with sudo su and:

echo -n 100 > /proc/acpi/video/VGA/LCD/brightness
to goto full brightness

and 

echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
to goto half brightness

that works for these values:
37 12 25 37 50 62 75 87 100

---

### Post by tagno25 on 2007-12-08
has anyone found/made a fix to this so you do not have to set it on the CLI?

---

### Post by cgm12mgc on 2008-02-29
i just got a 1501, it came with bios version 2.6.3  i attempted to down grade to 1.7, this caused my video card to die...  i was lucky enough to have downloaded the 2.6.3 to my desktop and managed to just re-load it

is there a way to run ubuntu with my current version of bios?

---

### Post by cgm12mgc on 2008-03-01
the problem im having is i put in my amd64 bit cd and click install, it goes through the entire process however stops before actualy loading into the boot screen...  any ideas?

---

### Post by twright on 2008-03-02
you could try installing the server version and then sudo aptitude install ubuntu-desktop

---

### Post by RM19 on 2008-03-02
i recently downloaded Ubuntu 7.04 because of all the hype around it but i'm not too sure about it since everything is incompatible. i'm trying to get the modem working...my computer is an inspiron 1501 with an athlon 64 dual core processor and a conexant HDA  D110 MDC V.92 modem. after looking everywhere for the modem i finally found it for the dell inspiron 1505n i think it was i installed it and now it dials but doesnt connect adn i dont see anything while it doest this and i dont know what to do since dial up is my only way to connect HELP!!!

---

### Post by twright on 2008-03-03
do you mean ubuntu 7.10?
 
there is a tutorial to install the modem driver here:
[http://www.ubuntu1501.com/2007/12/conexant-modem-driver-for-gutsy.html](http://www.ubuntu1501.com/2007/12/conexant-modem-driver-for-gutsy.html)

---

