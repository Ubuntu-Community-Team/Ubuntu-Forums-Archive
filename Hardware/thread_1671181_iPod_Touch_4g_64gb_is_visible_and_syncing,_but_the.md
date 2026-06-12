---
title: "iPod Touch 4g 64gb is visible and syncing, but the files won't show up"
date: 2011-01-19
forum: Hardware
---

### Post by RafaelL on 2011-01-19
Hi!

The problem I'm having is summarized in to the topic, but to be more precise:

I just recently bought a 64gb iPod Touch 4th gen (not jailbraked). After I got it activated on a friends win7 and iTunes, I returned hopefully to my Ubuntu 10.10 - but alas, the device still wasn't syncing properly. Since I have added the Paul McEnery repository (installed libimobiledevice1, iFuse, ipheth-utils, libgpod4 and libusbmuxd1), the device shows up correctly, the folders are showed, and it even shows up both in Rhythmbox and gtkpod. 
Then , when I move some music over to the iPod it syncs normally and the pod even lights up saying, "sync in progress". However, after I disconnect and look into the music library on the iPod, there is nothing!
My own theory is that the hash file doesn't update even though the files are copied over to the device. 
There is another thing I'm not sure of: after saving, gtkpod says, "unsupported checksum type" or something of sorts.

Now, after combing the Ubuntuforums and not finding an answer, I turn to you, dear community. What might be the matter with the transfer?

Best regards,
Rafael

Ps. I am a fairly new user to Ubuntu, so please give detailed instructions on how to perform whatever I might have to perform. :)

---

### Post by amarumayo on 2011-02-04
I am having the same problem with the 8gb 4th gen. ipod touch.

---

### Post by ngativ on 2011-02-08
same problem here

---

### Post by stad on 2011-02-22
Same, and we are no alone. However, I don't even know how to go about figuring this out. So until one of the guys who made the guide can get on and tell us why it's no longer working, then we much wait.

---

### Post by falsedichotomies on 2011-03-11
I am having a similar issue with a 64GB 3rd gen iPod touch. It will mount, show up in Banshee, and I can even drag files onto it so that the program itself says "adding files." However, the files simply don't stay. If I check the inside of my iPod, or close out of Banshee and reopen it, they have vanished (Rhythmbox does the same).

One small difference though: when files are being added to it, the iPod itself doesn't say "syncing" like yours does. It just sits on the unlock screen. 

It actually used to work perfectly, then, a couple days ago, on a friend's computer, I restored it and updated its iOS to the new 4.3, so I'm thinking that iOS 4 might be part of the problem.

---

### Post by Joe_Dice on 2011-03-21
I also have this problem. Sucks because I have a lot of songs that I would like to put on my ipod. I'm happy to know that it's not just because I'm a noob.

---

### Post by alessandro0blanco on 2011-05-22
I got my two iPod Touch 4G (32 and 64 gb) with iOS 4.3.1 to sync with banshee in ubuntu 10.10!
The steps to follow are these:

[LIST]
[*]Follow [this]("http://cogizio.org/operating-systems/ubuntu/3089") guide
[*]Install the latest version of libimobiledevice: 1.1.0 (to do this you should add the _natty_ pmcenery ppa to your repositories)
[*]Install the 0.7.95 version of libgpod (select package libgpod4, the  go to packages >> force version and select this version. Do this  for libgpod-common too)
[/LIST]
I tried with ubuntu 11.04 but I couldn't install the 0.7.95 version  of libgpod, so I failed with natty. But someone could teach me too how  to do this.

Ask for more details!

---

