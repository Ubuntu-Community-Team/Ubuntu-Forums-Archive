---
title: "Replace CD/DVD drive with second HDD...?"
date: 2008-11-14
forum: Hardware
---

### Post by icanfly0307 on 2008-11-14
Hi,
   I have an old laptop (Sony Vaio PCG FX370) that is currently running Kubuntu 8.04. I'm coping along on the hard drive requirements; however, it is a bit annoying to see that Kubuntu uses approx. 5 GB of HDD space. I'm unwilling to switch over to another flavor of Ubuntu or any other distro for that matter. I do, however, have a spare HDD that I'm not really using right now. My DVD/CD drive is also dead which makes it useless, really.

So, my question is: Is it possible to remove the DVD/CD drive and replace it with my spare HDD? I'm not worried about taking my lappy apart as I've already done it several times before. Getting Kubuntu to recognize the second HDD is another matter that I'll try to sort out AFTER plugging in my second HDD. Does anyone have any clue on this matter. I really want to upgrade my HDD space from 20 GB to 40 GB... (20GB x 2 HDDs)...

Any help would be appreciated... :)

---

### Post by cariboo on 2008-11-14
If your sony has usb ports it would be easier and safer to buy a hard drive encloseure and use that instead of trying to haywire a connection to your extra hard drive.

Jim

---

### Post by icanfly0307 on 2008-11-14
Hi,
       Thanks for your reply. I really don't want to keep my second HDD outside the lappy's chassis because that would make it look weird and I'll have to carry it along with the laptop. So do you know any way that I can replace my CD drive with the second HDD? I'll do a bit of googling around for now.

Thanks! :)

---

### Post by Mardoct909 on 2008-11-14
Assuming they both use the same bus type, yes. It should work. Whether it is recommended or not... I'm not sure I'd recommend it unless you're confident in your abilities with messing around in there.

I added a second hard drive fairly easily to my install. Turn everything off, plug it in, turn it on, use Gparted to put a filesystem on it and now it appears in the Places->Computer screen... Or whatever the equivalent is with KDE, presumably. Just mount it when you need it.

I did run into some trouble with permissions being weird with an ext3 FS on it, but if you get the ntfs-3g package, you can just as easily put NTFS on it, which I had no problem with.

---

### Post by solitaire on 2008-11-14
With the cost of IDE 2.5" drives it might be easier to buy a larger laptop drive and copy the install over into it using something like 'remastersys'!

Saying that.... 

It also it depends if the CD/DVD bay can accept a HDD. You'll probably have to buy a caddy or an adapter (if Sony or Ebay still has one!) to fit the HDD into the media bay.

In the end you'll have to see which is cheeper:
A new larger HDD and copy your installover.
or
A new caddy for the spare HDD and dump the CD/DVD

---

### Post by icanfly0307 on 2008-11-15
I'll try it out today and see if it works. Oh and by the way, my BIOS DOES allow a second HDD to be inserted into the CD drive bay. Thanks for all your help!

---

