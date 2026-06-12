---
title: "[SOLVED] Cannot activate NVIDIA driver!"
date: 2009-01-11
forum: Hardware
---

### Post by Drubie on 2009-01-11
Greetings.

I recently upgraded my other laptop to dualboot Mac OS X.4 and Ubuntu 8.10 (upgraded ubuntu from 8.04) and am having trouble activating a hardware driver.

Everything is as normal, I open up the hardware drivers thing in the administration menu, and select the driver (NVIDIA accelerated graphics driver v177) and hit activate.  however, the driver is not activated!  a window pops up saying "downloading and installing driver" and a progress bar at 0%, but then promply disappears and it is as if it never showed up...  

what is going on, or is there a way to manually do this?
Thanks in advance.

---

### Post by Drubie on 2009-01-11
Nevermind, I got it to work!

Thanks, Drubie!  Yay!

---

### Post by Drubie on 2009-01-11
Double post???

---

### Post by fsando on 2009-01-23
> **Drubie said:**
> Nevermind, I got it to work!

Thanks, Drubie!  Yay!

How did you do that?

---

### Post by ScAwN on 2009-02-25
> **Drubie said:**
> Nevermind, I got it to work!

Thanks, Drubie!  Yay!

I'm new to this scene but the first thing "most" forums want you to do is search for your problem before posting. I am having the exact same problem so I searched and found this thread. It's very disappointing that you didn't at least let people know how you fixed the problem. Would you mind letting us know so others who experience this problem can attempt your solution?

---

### Post by Wreckless Hype on 2009-02-25
Make sure you network works. Go to System > Admin > Software Sources and check download from (restricted). After this, you should be allowed to download the restricted drivers for your Nvidia chip. I just did this with my HP laptop to get my 8400M GS card to work. You'll need to reboot after the install and then just double check it's enabled.

---

### Post by ScAwN on 2009-02-26
> **Wreckless Hype said:**
> Make sure you network works.

I can see some people would overlook something so obvious as I have done it myself. However, I was posting from the exact same system I am trying to fix, so I already knew my network was working fine.

I did get things working however on my HP dv9540US laptop with the GeForce 8600M. I can't say for sure I know how I fixed it, but this is what I did:

First ran "sudo apt-get update"

Secondly ran "sudo apt-get upgrade"

After these were both done, I rebooted and attempted to activate the 177 driver. It was a delayed download process, but it eventually did go through and activated. I'm assumming that the update/upgrade procedure had something to do with it, but that's just a guess. Hopefully someone else can verify this is what made a difference, but I didn't do anything else. The only other thought is that the download link was not working previously and all of the sudden came back up.

---

### Post by andr0cles on 2009-03-22
Thanks for posting that. I had this problem too after a fresh install of 8.10. I did as you said: 'sudo apt-get update' followed by 'sudo apt-get upgrade' and rebooted. I'm not sure why that works but it does.

---

### Post by therevEJW on 2009-04-08
this isn't working for me :(

i need help bad!

---

### Post by freddybob on 2009-04-08
> **Wreckless Hype said:**
> Make sure you network works. Go to System > Admin > Software Sources and check download from (restricted). After this, you should be allowed to download the restricted drivers for your Nvidia chip.

Thank you, I was pulling my hair out trying to get the Hardware Drivers wizard to install the latest recommended driver.

---

