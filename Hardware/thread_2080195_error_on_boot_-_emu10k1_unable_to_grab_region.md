---
title: "error on boot - emu10k1 unable to grab region"
date: 2012-11-03
forum: Hardware
---

### Post by arch0njw on 2012-11-03
I had a strange error today booting my system.  I got past GRUB and it was loading Kubuntu.  It then stopped with an error message like this:

emu10k1 unable to grab region

There was some hex after it.

The only informative hits I've found so far are comments about sound cards and moving them to a different PCI slot.

I have made ZERO hardware changes to my computer in the last 24 hours.

Has anyone else seen this?  I'm hoping this isn't a sign of things failing.

---

### Post by imachavel on 2012-11-03
can you get to Ubuntu OS? If so please go to the terminal an enter these commands then look for any errors in the settings, it could be a configuration issue:

alsamixer

alsaconf

amixer

anything unusual? Now please enter these commands and post the output:

lsmod | grep '^snd' | column -t

ls -l /dev/snd

aplay -l

you might want to try re installing  reinstalling alsa-utils/alsa-oss/linux

Lol yes I found most of these trouble shooting solutions in another thread. But most of these would most likely address the problem if the error wasn't at boot but occured after the OS loaded, meaning it was an error message not a boot error message. If it was a software problem which it might be I'd trouble shoot the file system specifically the settings and file properties dealing with sound input/output, try running updates as well:

sudo apt-get install update

sudo apt-get install upgrade

but most likely I believe the cause of your problem is that you probably installed a new sound card no? Do you have a sound card installed in an expansion slot? Try moving it to another pci slot it'll most likely fix your problem. Best of luck

---

### Post by arch0njw on 2012-11-03
The only thing odd was that "alsaconf" didn't work -- apparently not installed.

I have sound.  I'm listening to an album right now (**** Dale -- Tribal Thunder... AWESOME!).

I'm completely up-to-date on 12.04.  No new software installed.

I did not install a new sound card.  This is the same one I've been using on this very same rig for years.

Oh well.  Perhaps just a fluke.  "Move to a new PCI slot" seems to be the universal answer.  Of course, "buy a new card" might be an answer too.  This card is only something like 10 years old.  So, it's ancient in computer terms.  I think the only thing older in my system is my 3.5" drive...

---

