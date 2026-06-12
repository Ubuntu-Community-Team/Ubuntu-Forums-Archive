---
title: "fakeraid problems with jaunty"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by pradtf on 2009-05-26
we have a supermicro 1.26G server with 4 scsi hd and a dac960 raid card
it's worked great on freebsd for about a year, but we want to switch to
ubuntu.

i'm exploring:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

we have managed to get the livecd to work and tried to follow the above
document's steps with our DAC960 card (these steps were tested on Intel
ICH9R array):

# $ sudo modprobe dm-raid4-5
# $ sudo apt-get install -y dmraid
# $ sudo swapoff -a 
# $ sudo dmraid -ay 

the first 3 steps go just fine, but when we try the 4th we get 
"no block devices found"

so this seems to suggest that ubuntu can't see our raid5 array?

---

### Post by ronparent on 2009-05-26
You might enter the following in a terminal - **sudo dmraid -l** - to see if your raid card is supported. If not, you might have better success using a software raid (mddam). I'm guessing you don't need to dual boot with windows so that might be a superior solution. If you decide to go in that direction you might want to run **dmraid -E** before uninstalling it to insure any leftover raid metadata is removed from your drives (you will probably get the same "no block devices found" which only means this last step was unnecessary).

---

### Post by pradtf on 2009-05-26
i wouldn't mind trying mddam, but the problem seems to be i can't disable the dac960. if i do, the system doesn't detect the 4 scsis. if i pull the card and plug the cable into the motherboard there is no recognition of the scsis either.

it's almost as though the system works around the dac960, which imho is really weird.

right now we're trying to figure out how to get into the motherboard bios. (it's easy to get into the dac bios, but as explained disabling it there doesn't seem to be an option).

---

### Post by ronparent on 2009-05-26
Fake raid is actually sortware raid in disguse. Often the only thing the raid bios does is write metadata to the disks so that they may be identified by the system and used in the proper raid by the drivers. The metadata is persistent and i've encountered cases where it interfears with the use of the disks in a non raid environment. That is why I've suggested using ****dmraid -E[B] to erase any existing data.

Disabling the raid is probably in the mb bios (it is on my mb's).

---

### Post by pradtf on 2009-05-26
i'm starting to think that this isn't fakeraid. i read a thread about non-fakeraid controllers and the dac960 was in there. so may be we need to take a different approach. thx for your suggestions ron.

---

