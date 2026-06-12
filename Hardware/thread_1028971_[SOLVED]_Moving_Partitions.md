---
title: "[SOLVED] Moving Partitions"
date: 2009-01-02
forum: Hardware
---

### Post by vancedus on 2009-01-02
Hi,

I have recently decided to take Windows XP off of my partitioned hard drive.  I have deleted the XP partition with GParted on a live boot and it is now shown as unallocated space.  How do I extend/move my ubuntu partition (sda5) to the remaining space?  I (hopefully) have attached screen shots.  Thanks for the help.

---

### Post by vancedus on 2009-01-02
screen shots, I can't figure out how to put a photo in the post, sorry.  

[IMG]

http://www.flickr.com/photos/31078045@N08/3162184340/[/IMG]

---

### Post by 2hot6ft2 on 2009-01-02
It's at the bottom when making a post. Manage attachments > browse to the pic > upload, when it's done uploading it close window and finish your post it will be attached.

---

### Post by 2hot6ft2 on 2009-01-02
Using the livecd System>Administration>Partition Editor
click on the drive you want to resize/move click on move/resize and use the sliders to do what you want then apply the changes.

---

### Post by 2hot6ft2 on 2009-01-03
You have it inside an extended partition so you'll need to right click on each and make sure they are unmounted.

If you have a mount option then it is unmounted otherwise it will be grayed out.

Especially the swap since it may mount it automatically then you'll have to resize the extended partition /dev/sda2 and apply before you can do the other one.

Once you resized sda2 then you can resize /dev/sda5 and apply the reason is that sda5 is inside sda2 so sda2 has to be done first.

---

### Post by logos34 on 2009-01-03
> **2hot6ft2 said:**
> Using the livecd System>Administration>Partition Editor
click on the drive you want to resize/move click on move/resize and use the sliders to do what you want then apply the changes.

ok, here's another example of what I just mentioned in another thread: you can't manipulate the extended or the root partition until you first disable the /swap.  When you boot the live cd it often uses it.   if you look closely you'll see the keys on both, while / is unmounted.

So right-click on the /swap and do swapoff.

Now you'll be able to expand sda2 left to the front of the disk, then sda5 similarly

---

### Post by 2hot6ft2 on 2009-01-03
> **logos34 said:**
> 
So right-click on the /swap and do swapoff.

So there's a swapoff option instead of unmount for the swap partition?

I never noticed... cool I just learned something I didn't know.

Thanks logos34

---

### Post by logos34 on 2009-01-03
> **2hot6ft2 said:**
> So there's a swapoff option instead of unmount for the swap partition?

I never noticed...

I think its called that (that's the terminal command at least). lemme double check...

---

### Post by logos34 on 2009-01-03
yep, the rightclick option in gparted says 'swapoff'

---

### Post by 2hot6ft2 on 2009-01-03
See that's something that I simply never noticed. I'm so used to windows where there is no swap partition. And I never had to try and move or resize a partition that had a swap partition in it in almost 20 years.

---

### Post by vancedus on 2009-01-03
Thanks Everyone.  It was the swapoff that was giving me the trouble.  I appreciate the help.

---

