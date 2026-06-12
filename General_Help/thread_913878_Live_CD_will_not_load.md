---
title: "Live CD will not load"
date: 2008-09-08
forum: General Help
---

### Post by fredrito on 2008-09-08
Hello. I have three really basic questions. But first, some background.

I have been using ubuntu (version 6.06, or something...) for a while, but am not very computer savvy. My hard drive has been on the blink for a while. I realise that I should get a new one ASAP.

Three times in the past six months, during startup, I have got the message that there are errors on my drive. A forced file check begins, but about halfway through I am informed that I must perform a manual file check. To do this, I must type in my root password.

For some reason, my root password does not work.

Anyway, what I have done the past two times is load a live CD (of another distro, not Ubuntu - just bought what was available in the magazine shop), opened the terminal and run a manual fsck, i.e. I type:

sudo /sbin/e2fsck -y -f -v /dev/sda3

(which I discovered how to do thanks to you good people...)

All well and good - this has solved the problem the last two times. But this time, the live CD does not load. I have not ever had any issues with the CD drive and the light flashes when I put the CD in, etc.

So my first question is ... why is it not loading? Is there something I am supposed to do - a key I am supposed to press - something really obvious - to get the live CD to load?

Or am I correct in assuming that it should, if in the drive, load automatically on the computer being turned on? 

Sorry, I just can't remember if it loaded automatically last time or if I had to press an F key or something...

And my second question is: if it is the case that it should load automatically, should I assume that the problem is with this CD (which I keep well protected and have used only twice previously) and that, therefore I should buy/download a new live CD?

My third question: I downloaded Ubuntu 7.10 for when I buy a new hard drive - will this function as a live CD? Or is that a different thing altogether?

Thanks for your patience!

---

### Post by rraj.be on 2008-09-08
> **fredrito said:**
> 
sudo /sbin/e2fsck -y -f -v /dev/sda3

You can do this manual fsck using ubuntu live cd itself using the following command

```
sudo fsck
```

> 
So my first question is ... why is it not loading? Is there something I am supposed to do - a key I am supposed to press - something really obvious - to get the live CD to load?



If the first boot device is cdrom in your bios then it will load automaticaly or else you might want to change the boot device order using BIOS SETTINGS by pressing F10 or DEL key

[qoute]
And my second question is: if it is the case that it should load automatically, should I assume that the problem is with this CD (which I keep well protected and have used only twice previously) and that, therefore I should buy/download a new live CD?
[/quote]

i think its not the problem with CD as it was already used succesfully

> 
My third question: I downloaded Ubuntu 7.10 for when I buy a new hard drive - will this function as a live CD? Or is that a different thing altogether?
Thanks for your patience!

Sorry, i cant get what you are asking. .  ..are you asking whether your CD will be same live cd in new hard disk! ! !

---

### Post by fredrito on 2008-09-09
Yes! Thankyou!

I just had to change the boot device order in the BIOS settings.

What I meant by the third question was whether the Ubuntu I downloaded to install in my future new hard drive would also work as just a live CD. But no matter.

Once again, thank you very much.

---

### Post by rraj.be on 2008-09-10
> **fredrito said:**
> Yes! Thank you!

I just had to change the boot device order in the BIOS settings.

What I meant by the third question was whether the Ubuntu I downloaded to install in my future new hard drive would also work as just a live CD. But no matter.

Once again, thank you very much.

Much happy that your problem is solved. . . 

If you have downloaded Ubuntu ISO and burned to a CD it will be a Live Cd for ever. . . 

you can use it to installation or for working as a live cd itself. .

---

