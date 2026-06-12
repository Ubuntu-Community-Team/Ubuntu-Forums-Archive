---
title: "Best way to partition an Eee PC"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by funky_uncle on 2009-04-13
I've decided to install [http://crunchbanglinux.org]("CrunchBang Linux") (which is based on Ubuntu) on my Eee 901. I figured it's wise to have a separate /home partition. Trouble is, I don't know how big the / partition should be. For regular Ubuntu I see suggestions for everything from 5 to 30 GB. My HD is 16GB and I have 1GB of RAM.

I probably won't install a lot of huge programs on the PC. Can the root partition be resized later?

---

### Post by snowpine on 2009-04-13
Hi there, I am a CrunchBang user as well, on the Dell Mini 9 (with 8gb hard drive).

Crunchbang is just over 2gb installed. I would recommend 4gb (maybe 5gb if you plan to install openoffice or other large apps) for /, and the rest for /home. 

Yes, you can resize partitions at a future date by booting with a Live CD or USB and using the Gparted partition editor (System->Disk Partitioner in Crunchbang).

Many SSD drive owners (including myself) choose not to install a swap partition. You will get a warning from the installer if you don't create swap, which you can safely ignore. The only reason to create swap is if you plan to hibernate, in which case swap should be greater than your ram.

#! is a great distro. Ask (here or over at the #! forums) if you have any questions. :)

---

### Post by funky_uncle on 2009-04-13
Wow, only 2 gb!

Will I not be able to hibernate the PC unless I have a swap partition? I haven't gotten to test how fast it'll boot once it's installed, but if it's anything like Eeebuntu, I'd rather hibernate it than reboot. But if I'm not mistaken, I can always add a swap partition later, right?

---

### Post by snowpine on 2009-04-13
Swap is required for hibernate-to-disk (but not for suspend-to-ram). Wake up from suspend takes a few seconds, but wake up from hibernate takes almost as long as a full boot (maybe 10 seconds less). The advantage of hibernate over a full boot is not so much the time savings as the convenience of saving your full session (open applications and documents) from last time, so you can pick up right where you left off. You can also set the power manager to automatically hibernate when battery is critical, saving your work, which I think is a cool feature.

If hibernate is a useful feature to you, it's easier to create a swap partition from the get-go rather than add it later. 

I personally do not use a swap partition on my Mini 9, because my drive is only 8gb and I need it all.

---

### Post by funky_uncle on 2009-04-13
I think I can spare a portion of my HD for a swap. Does the old rule about the swap size being twice as big as the RAM still apply?

---

### Post by snowpine on 2009-04-13
> **funky_uncle said:**
> I think I can spare a portion of my HD for a swap. Does the old rule about the swap size being twice as big as the RAM still apply?

I am not sure (since I don't have swap personally)... can anyone else help???

I know it must be larger than your ram to hibernate (since the contents of ram are copied to swap) but whether it needs to be 2x I really can't say.

---

