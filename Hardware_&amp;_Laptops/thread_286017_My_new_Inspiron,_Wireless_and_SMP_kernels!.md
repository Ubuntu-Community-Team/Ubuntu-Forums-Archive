---
title: "My new Inspiron, Wireless and SMP kernels!"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by Taigrr on 2006-10-27
Just got my Inspiron e1505, and I like it!

But Ubuntu doesn't. I fresh download of dapper, burnt, and isntalled jsut fine. Have ethernet! Obviously, will need to configure the radeon and stuff. But i'm working on the wireless right now.

Intel PRO/Wireless 3945a/g -
I've been reading that it should just work. But that's not the case. I sudo apt-get install linux-686-smp, because of the core duo, which is supposedly supposed to get the wireless to work too, because of the restricted stuff.

But it doesn't. It's not even read. It see's there's a wireless there, but has no idea what it is. And, the wireless light on the laptop itself is blinking.

Does anyone know what's going on?

iwconfig shows as follows -

joe@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:169   Missed beacon:0

sit0      no wireless extensions.


I'd be most greatful to any help =D

---

### Post by thila on 2006-10-27
Why are you installing Drake? why not try Edgey?

---

### Post by Taigrr on 2006-10-27
When I tried Edgy,  couldn't get a theme to install properly. I took it as a quick meaning that it was still far too beta. But, I have a fresh copy of the alternate ISO, so I guess i'll try it now.

Any other suggestions?

---

### Post by Taigrr on 2006-10-27
What in the world. 

I just installed Ubuntu Edgy, and it was a miserable failure. I did happen to catch, while booting into recovery, that it found my wireless card.

But the screen is absolutely horrid. It's like, twisted. As you move hte mouse "down", it slides down at an angle over and over, disapearing from the left side of the screen, and popping up on the right. Like it would be going down a screw. I can't see anything, just lots of brown.

Anyonw know what's going on? Might be just a super high resolution, I guess. How do I change it from command line?

---

