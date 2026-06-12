---
title: "I/O Error - Error reading boot CD."
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by ShadowMage on 2009-10-29
Hello,

I downloaded Ubuntu 9.10 today from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), and burned the ISO onto a CD. Upon booting from the disc, I select my language (English), so far so good.

But then, when I try to select an item from the menu, such as "Check disc for defects", I get a message box titled "I/O error" with the message "Error reading boot CD." and a "Reboot" button. This is not a result of the check because if I select a different item, such as "Install Ubuntu", I get the same error.

Previous versions of Ubuntu have never given me this problem, although I have used different types of CD's for those. I don't know if this has anything to do with it, but just in case, I will give the info. It seems all my previous versions were burned on SONY CD-R, and the disc I used this time is a PRODISC CD-R.

Now, if I run md5sum on the .iso file from which I burned the CD, I get
728cf46cc5668557896e291cb8aaa99a
but I have no idea whether or not this is the correct sum; I tried searching for what it should be but I couldn't find it. But I'm downloading the .iso again in case I get a different sum this time.

If anyone has any idea what the problem is or can help steer my in the right direction, I would appreciate it very much! :)

Thanks in advance.

---

### Post by joewski on 2009-10-29
> **ShadowMage said:**
> 

Now, if I run md5sum on the .iso file from which I burned the CD, I get
728cf46cc5668557896e291cb8aaa99a
but I have no idea whether or not this is the correct sum; 

When you download an ISO there is usually a hash5 or shm1 value to compare your iso file to. It happens quite often that downloads or burns can become corrupt.

Other problems with install include:
-defective CD's (yes even silver production type)
-defective/weak lazers in the cd rom reader

---

### Post by RJARRRPCGP on 2009-10-29
> **ShadowMage said:**
> 

But then, when I try to select an item from the menu, such as "Check disc for defects", I get a message box titled "I/O error" with the message "Error reading boot CD." and a "Reboot" button. 

I started getting that for like no reason with a good Jaunty Jackalope (IIRC) CD, with my Adaptec 29160 SCSI card and Plextor SCSI CD drives.

---

### Post by ShadowMage on 2009-10-29
> **joewski said:**
> When you download an ISO there is usually a hash5 or shm1 value to compare your iso file to.

Sorry, but can you tell me where/how to find this value to compare it with? I'm a bit new with this stuff because I never ran into this type of problem before.

Also, I mentioned I was downloading it again. The download is complete, and I got a different sum this time. Is this normal? This time, I got 8790491bfa9d00f283ed9dd2d77b3906

Hopefully the difference is because the previous one was corrupt and this one isn't *crosses fingers*. I guess I'll try burning this new ISO download and see what happens.

By the way, thanks for your reply.

---

### Post by hawkeye2777 on 2009-10-29
> **ShadowMage said:**
> Sorry, but can you tell me where/how to find this value to compare it with? I'm a bit new with this stuff because I never ran into this type of problem before.

Also, I mentioned I was downloading it again. The download is complete, and I got a different sum this time. Is this normal? This time, I got 8790491bfa9d00f283ed9dd2d77b3906

Hopefully the difference is because the previous one was corrupt and this one isn't *crosses fingers*. I guess I'll try burning this new ISO download and see what happens.

By the way, thanks for your reply.

Here's the list of Ubuntu 9.10 MD5 sums:

[http://noncdn.releases.ubuntu.com/releases/9.10/MD5SUMS](http://noncdn.releases.ubuntu.com/releases/9.10/MD5SUMS)

---

### Post by ShadowMage on 2009-10-29
Thank you hawkeye2777. According to that page, it seems the first one I downloaded does not match, but the new one I downloaded does. So, it seems likely that this was the problem. I'm burning the new ISO now so I'll let you guys know if it works.

---

### Post by ShadowMage on 2009-10-30
Well it seems that the first ISO was corrupt. Not only did the md5 sum not match, but when I went to delete it I noticed that it was only approx. 500 MB! Weird.

Anyway, now with my new ISO, that message box is gone. But when I "Check disc for defects", once it completes I keep getting the message
"Check finished: errors found in 1 files!"
or the message
"Check finished: errors found in 2 files!"

I tried this new ISO with 2 discs so far. Are my discs defective? Should I try burning one more disc? Should I try downloading one more ISO? Or should I wait until I can try a different type of CD and/or from a different pack?

---

### Post by raven01 on 2009-10-30
i had that problem. i took off the buffer protection and burned at 4x. then it worked.  i wish that lil weird problem would just go away lol

---

### Post by ShadowMage on 2009-10-30
Woot!

"Check finished: no errors found"

While the slowest speed I was able to select in my burning software is 8x, I took your advice and took off the buffer protection and slowed the speed down (to 8x), and finally I have a disc that passed the defects check!

Much thanks raven01 and everyone else who contributed to this thread!

---

### Post by ShadowMage on 2009-10-30
SUMMARY:

For reference purposes, I'll summarize that the "Error reading boot CD" problem was fixed by downloading a new ISO, because the first ISO was corrupted; and the "Check finished: errors found in 1 files!" problem was fixed by in the burning software taking off buffer protection and slowing down the burning speed.

---

