---
title: "Xubuntu on Laptop Failure. Please Help"
date: 2008-12-07
forum: Hardware
---

### Post by Spongejerk89 on 2008-12-07
Well, I have an old Toshiba Satellite laptop with a 1.3ghz Intel Celeron CPU and 192mb of RAM and I decided to put Xubuntu on it. I downloaded the first link on [THIS](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/) page, burnt it to a CD-R, and installed it on to my HDD. At first I thought it was successful by I soon realized I was wrong. It won't boot into Xubuntu. 

Here's an example of what happens.
> 
1. I turn it on and it shows the words TOSHIBA.
2. It goes to a black screen and says grub loading.
3. It shows the Xubuntu loading screen
4. After it's done loading it shows tons of words in DOS again like "Mp table errors detected, "##########(numbers) does not exist)", "Dropping to a shell", "this is not a compatible chip".

5. If I push enter it says (initramfs).

Can anyone help me?

---

### Post by Spongejerk89 on 2008-12-07
Oh yeah thanks. You guys helped a lot:(

---

### Post by Pantera116 on 2008-12-07
Question: did you try it as a live cd prior to installing to hard drive?
If it can be booted from cd it should boot from hard drive.

---

### Post by jesermay on 2008-12-07
> **Spongejerk89 said:**
> Well, I have an old Toshiba Satellite laptop with a 1.3ghz Intel Celeron CPU and 192mb of RAM and I decided to put Xubuntu on it. I downloaded the first link on [THIS](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04.1/release/) page, burnt it to a CD-R, and installed it on to my HDD. At first I thought it was successful by I soon realized I was wrong. It won't boot into Xubuntu. 

Here's an example of what happens.


Can anyone help me?

I would try a reinstall. Or try it on a live cd prior to installation. If the live cd does not work then you know its a faulty iso/disk

---

### Post by Spongejerk89 on 2008-12-07
I booted it from the Cd before I installed it and it worked but it was extremely slow. Every once in a while it will boot in but only when I restart it over, and over all day. I'll try reinstalling it. Thanks.

---

### Post by Spongejerk89 on 2008-12-07
I can't reinstall it because it won't boot from a cd and it won't boot in.

---

### Post by bdoe on 2008-12-07
What do you mean, it won't boot from a CD? Does the option not even come up?

If it doesn't, then either your BIOS settings are faulty or corrupt, or the CD you burned is corrupt.

Check your BIOS settings and confirm that your CD drive is higher on the boot-order list than your hard drive. If your BIOS is correct, then try redownloading the Xubuntu disk image and burning a new CD.

---

### Post by Spongejerk89 on 2008-12-07
> **bdoe said:**
> What do you mean, it won't boot from a CD? Does the option not even come up?

The option comes up and I've done that. Whether I boot from the HDD or the CD it still fails.

---

### Post by bdoe on 2008-12-07
That's a good sign that your CD is corrupt. Try burning another copy from a fresh download (in other words, do not use the ISO you used to burn the last CD).

---

### Post by Spongejerk89 on 2008-12-07
**Ok, I finally got it to boot in but it won't last for long. What can I do from here to fix it?**

---

### Post by Spongejerk89 on 2008-12-07
Never mind it failed.

---

### Post by Spongejerk89 on 2008-12-08
Bump.

---

### Post by Spongejerk89 on 2008-12-08
Well, it confirmed. It was a fault in the Live CD. I downloaded  Knoppix via Bitorrent instead and burnt it at only 4x speeds but it won't work. For some reason the laptop just isn't getting the boot options right.

---

### Post by Spongejerk89 on 2008-12-11
Bump.

---

