---
title: "How does Ubuntu Boot?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by smacfarl on 2009-11-07
Is there a good text on this?

It seems pretty clear to me that the Vista boot loader even modified by EasyBCD does not work with the way Ubuntu installs grub2 by default. 

I would love to talk to someone in the Ubuntu Community that understands these issues, and/or read all the books/docs necessary to understand this myself. 

It's been almost a week since I posted my first question about the 9.10 install. Are there people in these forums that know these things?

And if the solution is that I need to pay for 1 year support to get the damn thing installed properly, it would be nice for someone from Ubuntu Corporate to indicate that in the forums, on a regular basis, rather than letting questions languish for very long periods of time.

---

### Post by jheaton5 on 2009-11-07
I found your original post.  It seems that most of the problems with dual booting windows and ubuntu has to do with using wubi as the means to install ubuntu. I have never used wubi so I can't help with that.  I have also never had a problem with an install because I download the iso image from the ubuntu download site.  I burn the image to the disk, check the md5sum and boot from the cd. I get a chance to play around with the new ubuntu to see if it works on my system.  Then I elect to install.  The ubuntu installer handles everything, including a proper installation of grub2 that works.

[wubi known bugs]("http://sourceforge.net/tracker/?group_id=198355&atid=965144")

---

### Post by smacfarl on 2009-11-08
After messing around with several other linuxes, I got Suse 11.2 to load.

Suse has a very elaborate boot loader analysis, which showed me the problem Ubuntu had. Turns out I installed my vista boot loader to drive D even though vista was running from drive C. Ubuntu's default installation of grub just totally screwed up. Suse on the other hand pointed out the problem in very thorough detail and asked me what I wanted to do.

I then exited suse, booted vista and used the easybcd console tools to move the mbr and the windows bootmgr to my drive C:, as well as reconstruct BCD.

I then loaded 9.10 Live-CD blew away my other install from the CD, and then reinstalled 9.10 from CD. This time 9.10 runs successfully. However it did stomp on the windows bootloader and replace it with grub2. 

So I would definitely say Ubuntu has a lot to learn from the Suse installer. 

However Suse did not identify, my graphics card or or my monitor correctly, and while Yast seems pretty cool, Ubuntu 9.10 got the display right and offer to install the latest nvidia drivers. So I am happily running 9.10 again. 

I think before 10.4 Team Ubuntu better spend some serious time with the installer process.

---

### Post by QIII on 2009-11-08
Just for the record...

I've been multi-booting for years and used GRUB2 in Jaunty without issue.

Unfortunately, the installation process for Ubuntu cannot possibly account for every possible combination of OSs and hardware millions of people can cobble together.

Suse can't either, but it worked in your case -- and good for it.

If you would like to help the Lucid team, it might help them if you communicated your concerns to them now, rather than expecting it to be right without your input.

We are all in this together.

---

