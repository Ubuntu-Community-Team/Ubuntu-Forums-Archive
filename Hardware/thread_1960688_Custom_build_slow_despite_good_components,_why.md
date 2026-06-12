---
title: "Custom build slow despite good components, why?"
date: 2012-04-17
forum: Hardware
---

### Post by mmuldoor on 2012-04-17
Sorry-- I'm a semi-newb.  I recently bought a custom built PC desktop at a thrift store for like $60 and I thought it was a great deal because of the specs--3ghz dual processors, 2 gb ram 160 gb bard drive etcetera etcetera. However, it it pretty slow, can't really handle the unity interface, audio stutters and is out of sync with the video. Sometimes when I try to do more than 2 things while audio is playing, it will get stuck and repeat a smalll 2 second segment loop ad infinitum. Flash video is Choppy.  So what's going on? Did the guy who build this mess up somewhere? Did he use a cheap graphics card or something ? Is the graphics card incompatible? I think its called a "gallium" or something like that.

---

### Post by ahallubuntu on 2012-04-18
Maybe it's got an ancient Pentium D CPU, probably the worst dual core CPU ever?  (A Pentium D is really just two Pentium 4 chips in one package.)  And yes, it might also have a crappy video card, one reason it probably can't run Unity.

A 3GHZ Pentium D (if that's what you have) is like a 1.6GHZ Core 2 Duo system.  Different CPUs used different architectures, FYI, so you can't simply compare GHZ to compare performance.  If you tell us more about this box, we can help you judge the specs for real instead of just guessing.

---

### Post by Mark Phelps on 2012-04-18
To find out the make and model video chipset being used, open a terminal, enter "lspci" and look for the line containing "VGA".  Post that info back here.

And, think about this -- if that PC was working great, why would someone have sold it for as little as $60?  Maybe the original owner was unable to get decent performance out of it and just wanted to be rid of it.

---

### Post by sudodus on 2012-04-18
Please run ***lshw*** to list your hardware to the file ***lshw.txt*** with the following command
```
sudo lshw > lshw.txt
```
and attach that file to a reply. It will help us understand, what can be done with your computer :-)

---

### Post by amaz1ng on 2012-04-18
I have NEVER had perfect internet video playback in any of my Ubuntu machines, going back to 6.whatever.

For the record, to save you some looking through for the line that says "VGA" you can type the following command:

```
lspci | grep "VGA"
```

And you can post that output here, just like Mark suggested.

---

### Post by MonkeyPaw on 2012-04-18
Graphics card is probably a DX9-only card if it's a Pentium D. The best cards from that era were like nVidia 7900GTXs and ATI x1950s (I think). That, or we're talking Intel GMA graphics--which were never considered decent.

You are probably fortunate enough to have a PCIe slot though, which leaves a chance for an upgrade.

---

### Post by ahallubuntu on 2012-04-18
We don't know what the CPU is yet; I was just presenting an example where a "dual-core CPU" like the Pentium D could still be pretty slow even if running at 3GHZ.  Some people see "3GHZ" and think, "Wow, that sounds really fast!"

---

### Post by mastablasta on 2012-04-19
> **ahallubuntu said:**
> Some people see "3GHZ" and think, "Wow, that sounds really fast!"
 
well for years and years industry worked like that. the advertising and all... it was preety easy to say that 486-100Mhz is faster than 486-66Mhz. nowadays it's preety hard to tell from the name which one is faster and i think they really should do something with the naming so that people don't get confused. and they should drop the Ghz form the name as it seems to be nothing but false advertising...
 
 
now back to the OP problem - old motherboard.... it seems to me the problem is in the GPU. check what kind of port you have AGP or PCI and get a working used GPU. movies will work then. if you don't want to spend money you could try Xubuntu or Lubunt first to see if there is any performance improvement.
 
additonally check the BIOS settings a bit. i have an old mobo at home that i took out and replace because it had a 1.6 Ghz single core on it and it worked as 800Mhz. motherboard simply didn't support higher working CPU. 
 
on the side note the 16 MB Ati rage a really old graphic card worked perfectly in linux :-).

---

### Post by mmuldoor on 2012-11-02
Lol... sorry guys, I gave up on that piece of junk for a while. I tried every distro, all the lightweights,  puppy linux, bodhi, lubuntu. Still, the fans came on, even when i was barely doing anything. I haven't even bothered to take it apart much yet, probably just gonna use it as a kind of server/storage unit. I found a really great working Core2Duo Dell with a 250GB HD (actually, 2 250 GB, set up in a RAID I think, I'm still a newb to RAID) for $32 with a coupon. Only thing wrong with it was that the dvd drive button was smashed in and you can't eject the drive with the button (but can by typing eject in terminal) I've got a dual-boot Fedora 17/Ubuntu 12.10 on it...so I'm good. If i ever take that junker apart in my spare time, and need help, I'll start another thread. Thanks for the comments though. I've learned a lot in the last few months just scouring forums.

---

