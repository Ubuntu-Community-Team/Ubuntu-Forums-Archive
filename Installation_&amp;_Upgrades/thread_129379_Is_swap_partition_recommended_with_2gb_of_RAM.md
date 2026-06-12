---
title: "Is swap partition recommended with 2gb of RAM?"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by orangedoor on 2006-02-13
I have 2gb of RAM in my computer. And I understand that the K7 kernel (any kernel except 386) has high-mem support (more than 1gb). From what I know about the swap partition, it seems like it's not necessary. I have the hard-drive space to spare for a swap partition, just wondering if there would by any increase in performance or stability from having one.

---

### Post by Nulani on 2006-02-13
I'm pretty sure you have to have a swap partition, no matter how much ram you have.

---

### Post by Ghetto_Smurf on 2006-02-13
normally, you should calculate your sawp like this

swap:=1gb-(your ram)

you have 2gb, that should not be a problem. still you can create some 256mb for safety.

---

### Post by orangedoor on 2006-02-13
Nulani, read [https://wiki.ubuntu.com/SwapFaq](https://wiki.ubuntu.com/SwapFaq)

It's not required, and right now I'm running without it, but I'm going to reformat my computer and start from scratch anyway and was curious as to what people recommend.

Would people who have used linux for a while recommend I create 2-4 gigs of swap space? I do plan on working/editing with large image files (100+Mb) as well as large audio and video files.

---

### Post by taurus on 2006-02-13
I guess it depends on what you plan to do with your system!  If all you do is surf the web, read some mails, and play music, then 2BG of RAM is plenty!  But if you start encoding videos, editing pictures or movies, gaming, etc., then it's probably a good idea to have some RAM...  If you have space on your harddrive, why not create a 2GB of swap to be safe and you don't have to think or worry about it later, no matter what you plan to do in the near furture.  :)

---

### Post by Ghetto_Smurf on 2006-02-13
i use my Linux just for the basics: no need for flurry desktops and cedega, wine , etc. i currently have 128mb RAM (will have 512mb), and i have 1gb swap for security reasons. 

when i get those 512, ill reduce the swap to 512mb, acording to the swap calculation method (already shown):

swap:=1gb-(your ram)

---

### Post by orangedoor on 2006-02-13
How do I set my swap size to negative? According to that calculation I should set mine to -1gb.

Seriously though the calculators don't really make sense to me (neither the one above or the swap = 2xRAM). It does seem like the ideal SWAP size depends on how you use the computer. But assuming that I'm a power user, who does do a fair bit of video, image, and sound editing does it make sense to have 2 gigs swap? Or 4 gigs? or 8 gigs? If the OS is going to try to fill it all up will it just be putting more stress on my HD than is necessary? Or could it even be detrimental to performance?

---

### Post by siorai on 2006-02-13
[QUOTE=orangedoor]How do I set my swap size to negative? According to that calculation I should set mine to -1gb.

Seriously though the calculators don't really make sense to me (neither the one above or the swap = 2xRAM). It does seem like the ideal SWAP size depends on how you use the computer. But assuming that I'm a power user, who does do a fair bit of video, image, and sound editing does it make sense to have 2 gigs swap? Or 4 gigs? or 8 gigs? If the OS is going to try to fill it all up will it just be putting more stress on my HD than is necessary? Or could it even be detrimental to performance?[/QUOTE]

Set your swap to 0 and take out one of your 1GB sticks of ram? ;)

---

### Post by orangedoor on 2006-02-13
[QUOTE=siorai]Set your swap to 0 and take out one of your 1GB sticks of ram? ;)[/QUOTE]
That's what I was thinking too, but my linux guru friend just told me that the calculation above is complete bollocks, and he's been using *nix for nearly 30 years.

He basically said that if you're using swap you're probably doing something wrong, or need more RAM. The exception being certain programs that swap themselves, or other unique circumstances.

He's also always done swap = 2xRAM, so I'll make mine 4gb and shrink it later if need be, I'm guessing that I can shrink the partition later without a problem? Or maybe I should make a 2gb partition, and add a 2gb swap file?

---

### Post by o_fortuna on 2006-02-13
If you're not using the AMD64 kernel/AMD64(EM64T) processor, you can't have more than 4 GB of addressable memory (generally, you'll never need that much anyway). I generally say that if you have plenty of hard drive space, 4GB - your RAM is way more than enough. I have 1GB of RAM, and even with tons of stuff running I rarely use more than 100MB of swap.

---

