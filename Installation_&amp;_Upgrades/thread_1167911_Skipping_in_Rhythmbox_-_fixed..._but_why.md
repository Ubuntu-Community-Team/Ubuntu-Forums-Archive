---
title: "Skipping in Rhythmbox - fixed... but why?"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by IainPurdie on 2009-05-23
Recently I found that I was having random pauses when playing music in Rhythmbox - streaming audio and MP3s. I had a think and the only thing I'd changed was to enable my swap partition. For some reason, it had never been enabled as swap despite being created when I installed Ubuntu.

I popped to the command line, ran a "sudo swapoff" and... the skipping stopped. I also seem to have stopped having issues whereby my hard drive would go mental and effectively lock up the laptop.

I'm now going to disable the swap partition in /etc/fstab so that's not re-enabled when I boot up in future. What I'd like to know is if there are any known issues with swap on 9.04 which would have caused this?

A rough spec of my system (what I reckon is relevant at least) is this:

One main ext3 Ubuntu partition plus a 1.5Gb swap partition
RAM: 1280Mb (1Gb plus 256Mb)
Ubuntu 9.04 upgraded from 8.10

In honesty, I didn't notice any real performance gain when I enabled the swap anyway. But it does strike me as strange that it should have such a detrimental effect!

---

### Post by cariboo on 2009-05-23
You won't notice a performance increase when enabling swap, as it isn't used until all of your ram is exhausted. Unless you're running vm's, the only real need for a swap aprtition is for using the suspend function, where the contents of ram are transfered to swap at shutdown.

---

### Post by IainPurdie on 2009-05-23
Well, there's the thing. I've re-enabled it as a test and got System Monitor running. It's telling me that despite my RAM usage only being around 49.5%, my swap usage stands at 26.5%. It's been gradually creeping up over the last couple of hours.

I've found after a length of time, the swap use hits 100% which is madness unless I've got something seriously leaking memory somewhere. However, I don't get any issues if I don't have swap enabled. Is it possible that the swap management itself is what's at fault?

I also wasn't aware of the swap space being used only for suspend use. Are you sure about this? If that's the case then it would be impossible to suspend if the swap space itself were being used when the system was suspended...

---

