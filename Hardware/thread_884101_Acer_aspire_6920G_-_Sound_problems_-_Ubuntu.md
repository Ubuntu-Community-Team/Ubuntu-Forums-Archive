---
title: "Acer aspire 6920G - Sound problems - Ubuntu"
date: 2008-08-08
forum: Hardware
---

### Post by olol on 2008-08-08
Hi. I am using ubuntu on my laptop, which is a Acer Aspire 6920G, and I really like the OS. But there is of course a problem. The sound won't work. It worked on my desktop. But now it just wont work.. Have looked here at the forum and searched on Google, but I just can't find a solution.
  
the command cat /proc/asound/card0/codec#* | grep Codec gives me:

Codec: Realtek ALC889
Codec: Generic 11c1 ID 1040


//Olol

---

### Post by silkstone on 2008-08-08
It's a long shot, but right-click on the volume control icon, select Preferences and try selecting something other than Master to control.

I had a laptop where Master did nothing, but one of the other selections worked - can't remember which, but it may have been Headphones.

---

### Post by olol on 2008-08-08
> **silkstone said:**
> It's a long shot, but right-click on the volume control icon, select Preferences and try selecting something other than Master to control.

I had a laptop where Master did nothing, but one of the other selections worked - can't remember which, but it may have been Headphones.

Thank you for the answer, unfortunately it didn't work.. So any other help is welcome..

Maby it is a driver problem? How to know what driver I need? And how to update it?

---

### Post by no0ne on 2008-10-06
I got my alc889 on a Acer Aspire 6920G by using the [hda-verb]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2") utility (which I originally found [here]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007653.html")). I found the info as bits and pieces at the time, but [this post]("http://ph.ubuntuforums.com/showpost.php?p=5490997&postcount=12") describes quite well what needs to be done. 

You can use [OSS4]("http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4") as last resort, since ICH8 is listed as supported and apparently it worked for [someone with the same hardware in this thread ]("http://ubuntuforums.org/showthread.php?p=5131350").

---

### Post by plunder on 2008-11-19
I just got OSS4 running on my acer 6920G... you have to manually tell every program to output sound to OSS4 which is a pain, and the quality isn't too great, especially for the hardware that comes with our laptop... I really would like a better solutions to this problem using ALSA

-p

---

### Post by plunder on 2008-11-19
> **no0ne said:**
> I got my alc889 on a Acer Aspire 6920G by using the [hda-verb]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2") utility (which I originally found [here]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007653.html")). I found the info as bits and pieces at the time, but [this post]("http://ph.ubuntuforums.com/showpost.php?p=5490997&postcount=12") describes quite well what needs to be done. 

You can use [OSS4]("http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4") as last resort, since ICH8 is listed as supported and apparently it worked for [someone with the same hardware in this thread ]("http://ubuntuforums.org/showthread.php?p=5131350").


** REQUEST **
I couldn't find a newbie friendly guide for getting this ALSA driver working, I did read a little on hda-verb and tried to get that going, I had to edit a few files but I am unfamiliar with ubuntu and am not sure how to keep root authorization in GUI mode and I'm not an experienced enough linux user to know how to do it strictly in command prompt.

If you could help me out too with this and give a newbie friendly step by step to get ALSA working with an Acer Aspire 6920G, not only would I love you forever, but I'll rub your belly and give you a scooby snack... thanks

-plunder

---

### Post by no0ne on 2008-11-22
> **plunder said:**
> ** REQUEST **
I couldn't find a newbie friendly guide for getting this ALSA driver working, I did read a little on hda-verb and tried to get that going, I had to edit a few files but I am unfamiliar with ubuntu and am not sure how to keep root authorization in GUI mode and I'm not an experienced enough linux user to know how to do it strictly in command prompt.

If you could help me out too with this and give a newbie friendly step by step to get ALSA working with an Acer Aspire 6920G, not only would I love you forever, but I'll rub your belly and give you a scooby snack... thanks
-plunder

Well, jansaells guide linked in my last post is quite simple, but I'll try to simplify the process futher, though there's no way to avoid using quite a few commands: (remove all quotes, they're just there to show you what exactly needs to be typed)

1. Open a terminal window and type "sudo nano /etc/modprobe.d/alsa-base" and add the following line to the end of the file

"options snd-hda-intel model=acer-aspire"

2. Download the hda-verb file and save it in your home directory.

3. Open a terminal window again and type "tar jxvf hda-verb-0.2.tar.bz2"
to unpack the hda-verb file.

4. go into the hda-verb direcgtory in the termninal window by typing "cd hda-verb"

6. Complile it by typing "make"

7. Copy it to /usr/local/bin by typing "sudo cp hda-verb /usr/local/bin"

8. Type "sudo nano /etc/rc.local" and add the followind line to the file berfore the exit 0 line:

"/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2"

9. Restart your computer, sound should be working.

To use headphones and disable the speakers just simply mute your headphones from kmix, seems to work for no apparent reason. 
Note that the above solution only works on Hardy Heron and seems to be broken by different recognition of hardware in Intrepid Ibex. I'm trying to figure out how to continue using ALSA in order to avoid switching to OSS in Intrepid, but no luck so far.

Edit: There is a [new version of hda-verb]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz") available and the previous version is no longer available.

---

### Post by plunder on 2008-11-23
omg sound thank you

---

