---
title: "Hibernation doesn't work on MSI GX700 laptop"
date: 2008-12-30
forum: Hardware
---

### Post by baloocis on 2008-12-30
Hello everyone!
I have been using Ubuntu 8.10 64bit for a while now, but I can't get either the 'suspend' or the 'hibernate' function to work, despite the fact that [https://wiki.ubuntu.com/LaptopTestingTeam/MSIMegabookGX700](https://wiki.ubuntu.com/LaptopTestingTeam/MSIMegabookGX700) says that 'hibernate' should be working.

My laptop is not the exact same type, as it's a Hungarian subtype (GX700PX-258HU), but I guess it's mainly the same :). I am not sure what system details would be useful in this matter so I'll only post a swapon -s:

Filename				Type		Size	Used	Priority
/dev/sda7                               partition	5156824	0	-1

What it does when I try to hibernate is that it quits everything, then I get a blank, empty screen, with nothing on it except the prompt.

I realise this is a tricky subject (hibernation on linux) but it's kind of important for me, so I would really appreciate any help :). Also, I've read it somewhere that it's easier to get hibernate working than suspend, so that's why I asked for that, but if there's a solution for suspend too, that'd be just great...

---

### Post by baloocis on 2008-12-30
Oh my god! After I posted this thread, it actually started working! What magic power does this forum have?

The only thing I am curious about is if it's normal to start from Grub? Because when I press the wake-up button it displays the setup screen, then Grub, and if I start booting in, after a while, it just switches to login screen. Is that normal?

---

### Post by dadozgb on 2009-01-04
> **baloocis said:**
> 
The only thing I am curious about is if it's normal to start from Grub? Because when I press the wake-up button it displays the setup screen, then Grub, and if I start booting in, after a while, it just switches to login screen. Is that normal?

I belive it is as the hibernation process store system image on a disc from which it restore running apps.In hibernation power consumption sholud be 0% as the laptop is turned off. If you compare it to windows they acctually don't hibernate, they have suspend to ram which they call hibernate.

---

### Post by baloocis on 2009-01-07
Well,
I believe Windows has both functions, maybe they're just named somewhat different. Anyway, I don't care what Windows does, but what I do care about is that my hibernation doesn't work again.

Same symptoms: blank screen, only a blinking '_'. Sometimes, it eventually shuts down after like 10 minutes, but then it just reboots the computer when I try to wake it. It is a damn big issue, so again, any help would be appreciated.

---

### Post by dadozgb on 2009-01-07
> **baloocis said:**
> 
Same symptoms: blank screen, only a blinking '_'. Sometimes, it eventually shuts down after like 10 minutes, but then it just reboots the computer when I try to wake it. It is a damn big issue, so again, any help would be appreciated.

On my laptop msi ex700 with nvidia geforce 8400m hibernation is working. I installed package hibernate and uswsups. I'm running kernel 2.6.27-9-generic with lates stable nvidia driver. Try install these packages and do s2disk.I belive that pm-utils is broken on some laptops like msi.

---

### Post by baloocis on 2009-01-10
OK,
thanks, I'll try that. I'm going to be back with the results later :)

---

