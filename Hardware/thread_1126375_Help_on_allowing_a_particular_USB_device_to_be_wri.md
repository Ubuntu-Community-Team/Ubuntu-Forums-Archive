---
title: "Help on allowing a particular USB device to be written"
date: 2009-04-15
forum: Hardware
---

### Post by Zanoah on 2009-04-15
Hello

I have a little problem with my Western Digital Passport 250 GB USB HD. Since I am doing my PhD on History of Art, I got 200 GB of very important files on that HD, which I cannot afford to lose (I collect that files over 7 years, copying all data, which I loss over the years, on this HD). but I cannot seem to start it in Windows, it is blocked by the Passport program which is set to start immediately upon plug in. Anyhow, I succeed to start it in Ubuntu :), but I got a problem, Ubuntu wont let me write on it, I can only read, and I need to delete that silly Passport software to start HD in Windows, since on my Academy, only viable software and presentation system is set to work only in Windows :(.

So I really need help on this one, and since i am Ubuntu - xtra-n00b - 
Thanks in Advance :)

---

### Post by taurus on 2009-04-15
What filesystem is that external drive, ntfs or fat32?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Zanoah on 2009-04-15
it's FAT32 system on WD HD

---

### Post by CrunchyDoodle on 2009-04-15
Can we also assume that you've already bought a second USB HDD to make a copy of your 7 years of work?    :rolleyes:

This somehow reminds me of the story of an important paper I was writing while in the Master's program at Loyola. It was 1981 and I was using the Data General computer at work. With the paper virtually done, there was a major lay-off because my employer suddenly lost an important contract. I was out of work and my paper was stuck on that Data General computer inside a secure facility. Well, that Saturday morning, I managed to con the security guard to let me in to retrieve my paper. On my way out, the head of security passed me in the hallway and noticed I shouldn't be there. I decided that the truth would set me free. It did. I turned in my paper that Monday.    ):P

So, let that be a lesson for ya'

Bye.   :cool:

---

### Post by Zanoah on 2009-04-15
Thanks all, for sfiwt reply.

---

