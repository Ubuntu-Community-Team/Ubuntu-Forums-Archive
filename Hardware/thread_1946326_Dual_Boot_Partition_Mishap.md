---
title: "Dual Boot Partition Mishap"
date: 2012-03-24
forum: Hardware
---

### Post by Muswell on 2012-03-24
I just got a new laptop (Dell XPS 15) which I bought with the intention of dual booting Ubuntu and Windows. I'm a complete noob at this sort of thing and am also new to linux. While Trying to set up my partition scheme, Instead of shrinking my Windows partition (sda3 I believe) I reformatted it to ext4 and now I can't get windows to boot properly.

Can anyone help me figure out how to get my harddrive back in a working order so I can boot windows again?

Thanks

---

### Post by ahallubuntu on 2012-03-24
Shall we assume you did not get a Dell re-installation disc with this laptop, so you could boot that disc to re-install Windows?  

If you have access to any Dell Windows 7 disc (friend?) of the same type that matches the product key type on your COA sticker (probably under the battery), that disc will probably work and install on your Dell without even requiring activation - all you'll need is to download drivers from Dell's website specifically for your model.  Dell Windows discs are somewhat interchangeable between models.

There may also be a Windows factory restore partition on your hard drive in a different partition; typically you boot and hit F8 to get a "Repair" option for that but you probably can't anymore.   Could be a creative way to find a way to boot that up and then you could do a factory restore of your laptop.  Assuming the laptop is under a year old, it's still under warranty, so try calling Dell and asking them for help in doing a factory restore of your laptop, saying you erased the original partition by mistake.  If they can't come up with a way to get you going on your own, perhaps they'll just ship you a Windows 7 disc that will work.

---

### Post by Muswell on 2012-03-24
I did make a recovery disk. I was having trouble getting windows to read it. Then I did a little research and discovered that I should boot directly from that disk (seems like it should have been obvious to me. Didn't have my coffee this morning). Any way I had just started reformatting when you replied. I was going to wait until it finished before I marked the thread as solved. Thanks for you help though.

---

