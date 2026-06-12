---
title: "I need fstab line for  ntfs extended partition please?"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by handy on 2005-11-28
I've mounted the primary ntfs as:-

/dev/hdc1 /windows ntfs umask=0222 0 0

In /etc/fstab

Then in the shell:

Shell> mkdir /root/windows

This works fine.

My problem is with the extended partition as follows:-

As per previously used strategy above:

Shell> mkdir /root/winwork

fstab entry below is my trouble:

/dev/hdc2 /winwork ntfs umask=0222 0 0

The following command then typed at the Shell prompt:

Shell>  mount -a

Brings about error re: extended partition.

So, if some wise soul out there could spare me a few minutes, I can then go looking for my next problem to solve?

Thanks for your time:-  handy

---

### Post by tonym on 2005-11-28
Some suggestions to try.

Fistly,  are you sure that the extended partition is /dev/hdc2?  Try using

cfdisk /dev/hdc

to check on partition names.

According to the fstab entries above you have got both partitions mounted at /windows.  Is that a typo?

Again accoring to the fstab entries you are mounting at /windows but you refer to mkdir /root/windows.  To match your fstab you should mkdir /windows etc.

Regards

Tony Middleton

---

### Post by handy on 2005-11-28
Thanks Tony,
My primary ntfs partition is hdc1, so I thought that the extended partition on the same drive would be hdc2 ?
& yes that is a typo (sorry) it is supposed to be "winwork" I've fixed that now.
I have looked in wikis & guides all over, many talk of primary partitions but no info' on extended!?
I am in winxp now, I will shut down & put the linux drive in the draw, to run "cfdisk /dev/hdc" as you suggested, I'll get back in about 15 minutes I'd reckon.
Thanks again:  handy

---

### Post by handy on 2005-11-28
Thanks Tony that command "cfdisk /dev/hdc" gave me the info':-

My interpretation is that partition type "5" is for extended (logical) partitions.  The linux swap file on my machine is "hda5".  It does beg the next question though:-

What would I call the 3rd, & 4th partitions on the same drive if I had them?

If someone knows I would certainly be interested in the answer?

Or if there is complete information on ALL of the drive mounting parameters somewhere? 
A link to that info' would be magic. :-)

Wonderful community

Thankyou:  handy

---

