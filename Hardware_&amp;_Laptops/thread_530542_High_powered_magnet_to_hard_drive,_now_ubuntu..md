---
title: "High powered magnet to hard drive, now ubuntu."
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by Mnemonica on 2007-08-20
Ok. So, I just got into college and got everything set up. I pull out my laptop and theres a high-powered magnet stuck to the back of it, right on the hard drive. Apparently some kid back home thought it'd be a nice going away present. I WAS running Windows Vista (Blarg... Don't even get me started.) but all of that is gone now and the laptop -sometimes- says that there is a hard drive with nothing on it or that is corrupt... Or it says that there isn't a hard drive at all.

I've already downloaded the Ubuntu install CD and am able to get that up and running fine from my CD drive. But when I go to install it on my laptop's hard drive everything works perfectly 'til step seven. Then all of a sudden it starts giving me crap about the hard drive not even being there. I can even format the drive into different partitions, delete and edit existing partitions... All of that fun stuff.

So needless to say, I'm stumped. Is my hard drive completely screwed over? Can I recover my hard drive? Is there a work around or something... I don't know. It's a 120gig hard drive. And I've got no money to replace it. So being able to get my laptop back, with linux, would be great.

Oh! And by the way (sorry I didn't mention this earlier) I'm running a Dell Inspiron 640m. Basically brand new.

---

### Post by kipman725 on 2007-08-20
try a low level format using the drives manufacturers utility's, but if it's not been detected in the bios thats generally a sign the electronics are damaged.  IF you need a system that will get you on the web etc. while you save up for a new hard disk try damm small linux as that runs very well of a usb flash disk.

---

### Post by kostkon on 2007-08-20
> **Mnemonica said:**
> Ok. So, I just got into college and got everything set up. I pull out my laptop and theres a high-powered magnet stuck to the back of it, right on the hard drive. Apparently some kid back home thought it'd be a nice going away present.

Ouch! It was a younger brother/sister eh? What can you say? I sympathize with you.
 
Now about your disk. I think you need to do a low-level formating. Maybe I am wrong. Anyway, there are some Linux live CDs specific for these purposes.

 I hope that someone that knows more about these things will stumble on this thread and be able to help you more.

---

### Post by Mnemonica on 2007-08-20
Low level format... How would I get to that? I'm fairly familiar with what you're referring to (I think). Press F2 while everything is booting up. But I don't believe I've ever seen where I can format any drive from that interface.

---

### Post by Robbie Pence on 2007-08-20
Most systems don't have low-level formating tools built in.
You will need a disk, such as Acronis Disk director suite.

Personally, I suggest you pay for a new hard drive. Magnets are usually
permanent damage.

---

### Post by Mnemonica on 2007-08-20
Suggestion duly noted. But I'd like to try every option that I can before I go out and try to get money to spend (cause I definitely don't have it right now...) on a new HDD. So any and all info on where to and how to get this low level format thingie would be great.

Thanks very very much for the help so far people. Very quick response and very useful concise information is GREATLY appreciated. I'll give everyone a cookie or something in the end. ;)

---

### Post by AbredPeytr on 2007-08-20
You should also go after the "friend" who placed the magnet on your laptop and get them to buy a new hard drive should a low level format not function.

---

### Post by Mnemonica on 2007-08-20
Yeah... I would do that... But I think the **** that did it is under the ever loving protection of his adoring parents.

---

### Post by CowzRule on 2007-08-20
Sue 'em :)

---

### Post by gletob on 2007-08-20
you could return the magnet to the person

---

### Post by Calash on 2007-08-20
Googling "Low Level Format CD" came up with some results, but nothing I am familiar enough with to recommend.

What type of drive is it?  Your best bet may be going to the manufacturers website and seeing if they have a utility there.

---

### Post by Mnemonica on 2007-08-20
Ok.... So now I've done the low level format (I think). And it couldn't erase anything because it said there wasn't anything on the drive... I mean it erased stuff on all drives, but it didn't actually delete any info.

And now I'm getting a "Failed to create a file system" error when I get to the 5% mark of the "Installing system" portion of the install. The error message reads as follows: "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."

Does that help anyone to understand what might be the problem?

I would assume since the BIOS can read the drive (or at least recognize it as a drive) I SHOULD be able to install an os on it...

I have both partitions set up, one for / and one for swap.

---

### Post by Spartan.II.117 on 2007-08-21
if you want to pay for shipping i could send you a 20 gig drive to use (permanently or until you can afford a new one.) pm me with your address and i'll tall you how much shipping would be.

---

### Post by fourthdimension on 2007-10-11
I know this thread's old, but this might work:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
unless your hard drive is actually physically currupted.

---

