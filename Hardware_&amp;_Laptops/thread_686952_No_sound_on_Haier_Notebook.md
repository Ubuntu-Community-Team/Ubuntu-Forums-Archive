---
title: "No sound on Haier Notebook"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by wubsieonline on 2008-02-03
Hi,

I have looked around on this forum but i couldn't find any good help and tips. Recently i have installed Ubuntu 7.10 on a Haier Notebook (H51 to be exact). This notebook first ran on Windows XP but i got tired of it so i switched to Ubuntu.
Now there's a problem with my sound driver.
I can't hear any sound at all, and i don't get any error messages. If someone knows what the driver is called for my notebook, where i can find it, and how to install it, i would really appreciate it.

Thanks, Robert 

p.s. I'm from The Netherlands..so please don't criticize my English ;)

---

### Post by Yellow Pasque on 2008-02-03
I'm not familiar with Haier notebooks, so you need to runs some quick commands to see what kind of sound hardware you have. Please run:
```
sudo update-pciids; lspci
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by wubsieonline on 2008-02-04
Thanks.. the first command line worked: my audio driver seems to be SiS AC'97 Sound Controller...the second command lines feedback was: directory not found..

Can you give me advice or help with downloading and installing my drivers??
Many thanks!

---

### Post by Yellow Pasque on 2008-02-04
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)

---

### Post by oldsoundguy on 2008-02-04
Just hope the Haier Notebook is not like their appliances.  I bought a dishwasher that arrived broken and not completely assembled and it took over 6 months and four visits by the repairman to get it JURY RIGGED fixed (they never DID fix it completely the way it SHOULD have been fixed .. it is held together with clamps we bought at Ace Hardware in order to get it to function.  But glad to see that there was someone HERE to help!!

---

### Post by wubsieonline on 2008-02-05
Hmm i tried that site earlier..didn't work.. I had a guy check my laptop and he said: "Sir, you have a f****d up chipset. The audio driver is the same as my modem...ubuntu says the driver is running, and the audio works, but it just doesn't. So i guess i have to go back to windows. :(

---

### Post by kesman on 2008-02-05
The solution may be even simplier than you thought.
Open up terminal and run alsamixer. Then hit tab twice to select "all" channels to be shown. Then browse trough every one and if they have "MM" below them, that means they are muted. Hit M to unmute them. Unmute all, and maybe you'll get your sound. After this, hit ESC to exit the mixer setup.

Some update muted my PCM once, and I wasted a lot of time reactivating modules for my soundcard :F

---

### Post by wubsieonline on 2008-02-05
Sorry i already tried that too. I even set every channels to 100% but it didn't work. If you wanna take a close look you can pm me and get my ssh info so you can take a look yourself..... If it doesn't work i'm going back to Windows.......

---

