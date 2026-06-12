---
title: "Elantech touchpad not detected in 17.04"
date: 2017-10-05
forum: Hardware
---

### Post by warpspeedscp on 2017-10-05
I installed the latest lubuntu on my ideapad yesterday.

The touchpad didn't work in the installer, as expected, but now I notice that even after installation it still doesn't work! It's an Elan touchpad, and windows detects it just fine. I tried arch out before this, and the touchpad worked there too. It's only on lubuntu that this is occuring. xinput doesn't list it. Any ideas what I could do to fix it, beyond, say, trying out a newer kernel version?

---

### Post by mörgæs on 2017-10-06
Hi, welcome to the fora.

Yes, a newer kernel is an easy test. Is there any differnce in a live boot of 17.10 (beta)?

---

### Post by warpspeedscp on 2017-10-06
Actually, I tried out the 4.13 kernel from the artful ppa, and that seems to have fixed the issues. One thing though, is that wifi has gone completely bonkers in 4.13. If I log out once and log back in, wifi stops. I try getting it back up using iw, ip and the rest and they just become unresponsive-can't even ctrl-c out of them. They just freezer, and stop the system from shutting down properly because systemd keeps waiting for them to "finish".

Any thoughts on that?

---

### Post by mörgæs on 2017-10-07
So far, so good. Now it's just waiting until the network bug get fixed. 

An intermediate low-tech solution: Don't log out. Do a real shut down when you are finished.

I suggest that you try 17.10 in a live boot now and then to see when wifi works reliably. If you can live with using only wired internet access you can also install it today.

---

### Post by warpspeedscp on 2017-10-07
Well, as of now my wifi is completely broken, and won't turn on no matter what. Guess I'll have to reinstall.

So, nowI am faced with a choice: 

Do I want a working trackpad or do I want a working internet connection?


I think I'll use a usb mouse instead. Thank you for the help!

---

### Post by mörgæs on 2017-10-07
When you reinstall 17.04 you could create space for a dual boot so you can run 17.10 (beta) in parallel. I prefer running the clean versions to adding PPA's. 

This way you can try 17.10 from time to time, if needed with a wired internet connection, to see how the progress is. At least we know that the trackpad works here.

---

