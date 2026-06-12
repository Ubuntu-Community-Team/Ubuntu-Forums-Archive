---
title: "how to change the mbr to detect my internal hd"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by fofoporra on 2009-06-05
hello guys....

heres my situation...
i use to  have win xp on my laptop i was bored so i try ubuntu....
well i was a newbie and i manage to wipe all my xp partition and installed ubuntu on the entire hd. well, my cd rom its broke so i tire to boot xp via usb but when it get to the part where u select the partition of xp it only show me the external hd and not my internal hd. i tired to create a partition in ubuntu via gparted converted to ntfs...and nothing the installer still only showing me the external hd....



heres the question:do i have to delete ubuntu partition in order to installer to show my internal partition??

or i gotta change sometin on the mbr... pls tell me im lost now...


Ps:i did search but i didnt find a situation like mine......;)

---

### Post by logos34 on 2009-06-05
> **fofoporra said:**
> but when it get to the part where u select the partition of xp it only show me the external hd and not my internal hd. 

huh? can't imagine why it's doing that---technically you're not even supposed to be able to install XP on usb...

It shouldn't have anything to do with mbr.

Try this:

Boot the ubuntu live cd and use Gparted (System>admin>partition editor) to shrink ubuntu /.  Don't format the free space--just leave it 'unallocated' (gray)

Now reboot the XP cd and try again--try to point it to the unallocated space.

---

### Post by fofoporra on 2009-06-06
> **logos34 said:**
> huh? can't imagine why it's doing that---technically you're not even supposed to be able to install XP on usb...

It shouldn't have anything to do with mbr.

Try this:

Boot the ubuntu live cd and use Gparted (System>admin>partition editor) to shrink ubuntu /.  Don't format the free space--just leave it 'unallocated' (gray)

Now reboot the XP cd and try again--try to point it to the unallocated space.

nothing change...but thx anyway maybe its because im booting from usb ill see if i can buy a external cd drive and see if anything change...

---

