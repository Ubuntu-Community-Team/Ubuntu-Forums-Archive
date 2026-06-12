---
title: "Resizeing current home partition"
date: 2008-05-27
forum: Hardware
---

### Post by raveash on 2008-05-27
Hello, I had first installed Ubuntu with a seprate home parition. A month after i realized that needed more space.This is how my parition looks:

[IMG]http://i109.photobucket.com/albums/n51/carlos_reynosa/paritionsShot.jpg[/IMG]

The the logical partition before my home partition is just for extra space. I want to some how acquire more of this space for use in my home partition.

Thanks for the help!

---

### Post by logos34 on 2008-05-27
shrink / (sda eight) and expand /home (sda6) to the left into the freed space.  

You'll need to use gparted on the ubuntu livecd because root cannot be mounted.

If you need a lot more space for home, you might consider deleting that fat32 sda7 partition and transfering home there

---

### Post by raveash on 2008-05-28
Thanks, But do you know if it is safe for my info in the current home partition?

---

### Post by logos34 on 2008-05-28
shouldn't be a problem.  Might want to run fsck on it afterwards if it doesn't automatically.

Sometimes when you resize root, though, it throws off grub

---

