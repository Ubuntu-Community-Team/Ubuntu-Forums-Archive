---
title: "&quot;no soundcards found&quot; as usr, but root can find!"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by johnpipe on 2006-11-02
Hi,

I'm having trouble with sound.  As a user:

ajohnpipe@linus:~$ aplay -l
aplay: device_list:222: no soundcards found...
johnpipe@linus:~$ 

But, if I login as root, I get a complete listing of the sound card resources.  However, I can't get sound to play, even as root.  The card is SB Live emu10k1; all drivers are loaded, tried the un-install/re-install of sound, gdm, etc from the "Comprehensive Guide" but no sound, and no user access to sound resources, which suggests some permission problem may be part of the trouble.

Any suggestions what to try next? The card is OK, checked out with KNOPPIX 4.0.2, where I could get it working with just 'sudo modprobe emu10k1'.

Thanks in advance

Johnpipe

---

### Post by woedend on 2006-11-02
could be a group issue i suppose, what is the output of the command "groups"...does it show audio?

---

### Post by johnpipe on 2006-11-03
Hi, I had "fixed" the group issue with gpasswd, added myself to "audio"; but, I had not logged out/logged back in afterward, so it wasn't activated when I posted last (those things trip me up almost every time).  So I can access sound services now, but still no sound; apps "think" they are playing, but no sound out.  I'm wondering where to look next.

Thanks, Johnpipe

---

### Post by johnpipe on 2006-11-03
I went back to double check the soundcard with Knoppix, made sure it's connected correct and working OK. Then rebooted into Ubuntu edgy. Everything looks OK except for an odd-looking property in Device Manager:

Key                   type        Value

info.linux.driver     strlist     EMU10k1_Audigy # 

.....
pci.product           strilst     SB Live! EMU10k1

.....

pci.subsys_product    strlist     CT4832 SBLive! Value

.....

Still can't get sound to work, though everything seems to be configured Ok, except maybe that odd property, don't know what that's about.

I don't know what this means, or if it's having an effect, but the card does not have an Audigy chip as far as I know, and the card itself is correctly identified as may be seen above.

Johnpipe

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by eilker1917 on 2006-11-11
could anyone help pls, i have same problem...



01. eilker@eilker:~$ aplay --list-devices
02. aplay: device_list:221: couldnt be found audio card...
03. eilker@eilker:~$ su
04. Password:
05. root@eilker:/home/eilker# aplay --list-devices
06. **** PLAYBACK hardware devices list ****&#8629;
07. kart 0: ICH5 [Intel ICH5], cihaz 0: Intel ICH [Intel ICH5]&#8629;
08.   subdevices: 1/1&#8629;
09.   subdevice #0: subdevice #0&#8629;
10. kart 0: ICH5 [Intel ICH5], cihaz 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]&#8629;
11.   subdevices: 1/1&#8629;
12.   subdevice #0: subdevice #0&#8629;
13. root@eilker:/home/eilker# groups
14. root eilker
15. root@eilker:/home/eilker# exit
16. eilker@eilker:~$ groups
17. eilker admin
18. eilker@eilker:~$
19.

---

### Post by eilker1917 on 2006-11-12
solved
it was group mistake.
i added audio to my account, and it is solved.

---

