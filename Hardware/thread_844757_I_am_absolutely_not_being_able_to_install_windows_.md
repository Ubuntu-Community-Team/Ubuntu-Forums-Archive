---
title: "I am absolutely not being able to install windows after i installed ubuntu?"
date: 2008-06-29
forum: Hardware
---

### Post by ledzeppelin on 2008-06-29
Ubuntu is my only operating system and i want to download windows again because there are some .exe files that run way to choppy on ubuntu. I have Sony Viao 2003. I have tried booting from the C.D. but whenever i do so it freezes up and stays on that one blue screen. I am not being able to boot from startup because it wont give me the option. What can i do? I will not use virtual box or anything like that unless it is my absolute last option. if more detail is needed i will reply with it

---

### Post by starcannon on 2008-06-29
well you could resize your hdd using gparted live cd, install windows to the new partition, then reboot with ubuntu livecd and restore grub, but virtual box would be so much easier and trouble free in my experience, though if its gaming your after VB isn't the solution, dual booting, or becoming a wine or cedega master is. 

Oh, make sure your windows CD is clean and free of scratches... or that its image is clean and disease free... outside of that I don't have much to add.

---

### Post by ledzeppelin on 2008-06-29
My computer is not allowing me to write gparted to a c.d. and im not being able to resize anything. is there a way i could install from computer startup

---

### Post by starcannon on 2008-06-30
You can install gparted from the ubuntu desktop if your able to get that far, if not you can run gparted from the Ubuntu Livecd as well if you have one.

---

### Post by ledzeppelin on 2008-06-30
I Was able to get that far, but im not being able to resize anything, even if i put in the ubuntu live c.d.

---

### Post by kessaris on 2008-06-30
As crazy as it may sound, I was having a similar issue booting off a windows CD.  After installing ubuntu, the only operating system that my computer accepts is Linux.  Booting off the windows CD it just freezes at a black screen.  

I didn't really give it a second thought, but it's strange to hear that it's happening to someone else too!

---

### Post by bored_shiva on 2008-06-30
First I'd have to echo the vitualBox comment: it is way easier, and it actually will run some games well, depending on the game and your hardware (I play AOE II on it, for example)

Secondly, if you got resize your drive: Don't forget to backup your entire partition first. ANY time play around with the partitions, you're running a risk.

That said, GParted is readily available by using the Synaptic package manager, and you should have no trouble using it from the hard drive. It should be able to resize the partition for you. Although I don't know about being able to resize the BEGINNING of the partition, which is typically where windows likes to be (first partition on drive)

You also have the more extreme option, if all else fails: Backup your entire partition, then format your drive and install windows on it first. (You can specify a partition during windows installation so you can give it only a portion of the drive - that way you don't have to resize the partition later)

After you've installed windows you can restore your Ubuntu partition. (Make sure you restore or recreate the swap partition as well) The exact procedure for that depends on what you use for backup, so make sure to read the documentation.

Finally you can restore GRUB so you can double boot. 

If you do decide to do this you should keep in mind that it takes a while, so make sure you've got a couple of free hours handy.

Good luck.

---

### Post by ledzeppelin on 2008-06-30
thanks shiva, im gonna try some of that,i kind of like the third option and then i will dual boot. Im also glad that im not the only one that has had the poblem of losing windows to ubuntu

---

