---
title: "Support for USB encryption keys?"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by Fry-kun on 2006-12-28
Hi,

I can't seem to find [m]any references to USB encryption key support in Ubuntu, and even Linux in general. I must be searching badly or something because I know people have those keys and I think I've heard some stories of people using hardware encryption keys to encrypt their whole harddrives.

So here's my question: **what kind of support does Ubuntu (or Linux in general) offer for USB encryption keys?**

The reason I'm asking is, recently these keys have been going down in price and now cost in the vicinity of $5-10; I even got one for free after rebate recently. here are two that caught my eye recently because of the price: [Kensington PCKey LE]("http://www.amazon.com/Kensington-PCKey-USB-security-64088/dp/B0003QE3MW"), [Meritline USB PC Security]("http://meritline.stores.yahoo.net/usb-securilock-data-protection-key.html").

Any info appreciated!

Thanks and Happy New Year!

---

### Post by kidders on 2006-12-28
Hi there,

It sounds like you want to find a way to encrypt the contents of your hard drive in such a way that your PC is ... well ... one giant paperweight ... unless you boot it with a particular USB key plugged in a port.

I don't know if this will be a helpful comment, but the only times I've ever tried to do anything like this, I've always "made" the encryption key myself. It's a pretty straightforward thing to do on most distros.

---

### Post by Fry-kun on 2006-12-28
Are these encryption keys completely useless, then? I was thinking a hardware encryption module would offload some CPU usage.. Maybe such a key can at least be used as part of a 2-factor authentication.
As for losing the key, most hardware systems allow you to bypass the security if you've lost the key. The ones I listed actually make you register and get a key from the manufacturer's website, but I was thinking a long key can be created and stored in a safe-deposit box or something...

You guessed m main reason for getting one of these: I am thinking about encrypting a reasonably large portion of my HD. I know CPUs are pretty powerful nowadays, but hardware encryption/decryption would still take off some serious CPU cycles. Plus, if there's some way to retrieve my data if the key is lost, it all works out.

Another possibility is remote access to my home network. Again, two-factor encryption would be great. In this case, if the key is lost, I just need to alter the encryption scheme to bypass the key until I get another one.

Yet another possible application is speedup for SSH encryption. I've noticed that SCPing a large file starts thrashing the CPU (not to 100% but definitely enough to notice). Would be nice :)

---

### Post by kidders on 2006-12-28
Hmmm...

I wouldn't be too hopeful about Linux support for hardware encryption keys, I'm afraid. :-( I haven't been able to find one with explicit support for much more than Windoze ... I guess maybe there's no reason to sell them for OSX/Linux, when DIY jobs are so easy on those platforms. :-k I'll keep looking though.

I've been encrypting certain filesystems for a while now, so I'm quite curious about this thread. Two questions:

> Plus, if there's some way to retrieve my data if the key is lost, it all works out.I would *hate* to be using encryption that any sort of "back door" into it ... if you lose your key, surely you would expect (hope?) that the data would be irretrievable.

In practical terms, I can't quite picture how passing all data written to a hard disk through a USB bus would improve I/O performance. Even if no encryption was taking place at all, wouldn't doing that just slow things down?

Perhaps it might be worth testing a custom-built filesystem encryption solution, just to see if the performance is tolerable. I haven't had much trouble with mine, but having said that, my encrypted filesystems aren't very highly loaded.

---

### Post by TheWizzard on 2006-12-28
i'm using truecrypt for this. 
with truecrypt you can encrypt an entire partition or create a container. the latter makes it easier for making backups. you can just mount the truecrypt partition/file wherever you want. there is also a windows version, so you can use it to exchange secured information between linux and windows. 

truecrypt can be used with one or more keyfiles (which you can store on an usb or other place). 

for installation, see: 
[http://www.ubuntuforums.org/showthread.php?t=199367](http://www.ubuntuforums.org/showthread.php?t=199367)

---

### Post by Fry-kun on 2007-01-03
kidders:
I would hope that a private key backup could be generated - you would print it (or store on some media) and keep it in a safe place (like a safe deposit box in your bank). If  you lose your hardware key, the program will ask you to enter the private key you have backed up. You probably wouldn't mind going through the trouble of going to the bank and retrieving it if your data is lost otherwise.
It doesn't qualify as a backdoor since everyone will have a different key.

TheWizzard:
Sounds like truecrypt uses software encryption/decryption - just that the key is stored on a USB stick. unfortunately, the file on the USB key is not secure.. someone can steal the drive, duplicate it, and place the drive back - you wouldn't know that it was stolen. That would defeat the purpose of 2-factor authentication (in other words, this is only as safe as using password-only authentication)

I now think that these encryption keys are made for 2-factor authentication, not hardware encryption - which is still a welcome addition to the overall security... if only they're implemented correctly :)

---

