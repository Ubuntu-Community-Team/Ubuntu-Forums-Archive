---
title: "Questions concerning dual booting without CD or USB"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Alski1234 on 2009-05-14
My CD burner is broken, and my computer doesnt boot off of a USB. So I figure I could use Unetbootin  to boot from my harddrive. Is this a good way? Will I be able to keep my data and my Windows XP? Do I have to make a partition before? Or just go through the unetbootin setup? I dont want to lose data, or lose XP, and I am pretty new to all of this :P. Thanks

---

### Post by logos34 on 2009-05-14
Unetbootin is a great idea. I don't think you have many other options.

Try [this guide.]("http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora_p2")  Should work fine.

---

### Post by Alski1234 on 2009-05-14
So, would I need to do a partition first? Or can I just go through the directions like i was going to install it off CD?

---

### Post by logos34 on 2009-05-14
no, you don't have to do anything beforehand.  It will shrink XP for you to make room for ubuntu partition.

Choose either option

'Guided--Resize...'

or

'Guided--Use largest continuous free space' 

if you have empty space on the disk

[IMG]http://images.howtoforge.com/images/unetbootin_windows_linux/18.png[/IMG]

---

### Post by Alski1234 on 2009-05-14
Hmm, I used it. And I went straight to Ubuntu without ANY setup! Well, Im back on my Windows, but is Ubuntu installed succesfully?!

---

### Post by Alski1234 on 2009-05-14
Hmm, Im on Ubuntu now. When I went to boot, there was something like (OEM (or some series of letters like that :P) Install (for manufacturers)
Should I have used that? I was given the choices

Unetbootin
Help
??? Install (for Manufacturers)

Unetbootin gives me the Ubuntu splash page, and a REALLY long pause, and then it verifies some stuff on its own and brings me to Ubuntu's desktop.

---

### Post by logos34 on 2009-05-15
You must be using the ubuntu live cd iso instead of the text-based alternate install (as in the link I gave).

Sounds like you're just loading the live desktop session.  It's not installed.

[http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)

Remember to uninstall unetbootin afterward (required for hard drive installation mode)

---

### Post by Alski1234 on 2009-05-15
Would this be the 

[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors](http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors) (first option)

ubuntu-9.04-alternate-i386.iso

?

Plus, it said something about (for specialist installations) or something.

[http://mirror.its.uidaho.edu/pub/ubuntu-releases/jaunty/](http://mirror.its.uidaho.edu/pub/ubuntu-releases/jaunty/)

Is this the one?

---

### Post by logos34 on 2009-05-15
yep, that's it, ubuntu-9.04-alternate-i386.iso

---

### Post by Alski1234 on 2009-05-15
Thank you, Im off to do it. Thanks for all of the help! :)

---

### Post by Alski1234 on 2009-05-15
Ok, went to do it. And it failed. I got to the partition part, and it said I dont have enough space to do the (continuous free space) one. So I went to do it manually. It said that the minimum amount of gigs to partition was 99 GB, which is impossible for me, I dont have that much free space. And then it said that I would be at risk of having my system be unusable if I abort, which scared me. But I did abort, and im fine and safe back on Windows. 

What should I do? Why was 99 gigs the minimum? Am I safe to abort like that if needed? Thanks

---

### Post by logos34 on 2009-05-15
Then try the 'Guided--resize' option.  It will shrink windows to make room.  back up your files.

But first boot back into to XP and prep it as described [here.]("http://www.linuxdevcenter.com/lpt/a/6554")

---

