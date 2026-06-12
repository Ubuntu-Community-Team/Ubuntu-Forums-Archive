---
title: "perfect hard drive reported 'Disk has many Bad sectors&quot;"
date: 2010-04-08
forum: Hardware
---

### Post by jfaberna on 2010-04-08
I've seen other posts that are similar, but wanted to add to it based on my testing.  With either Ubuntu 9.10 or Fedora 12, I get the Palimpsest Disk utility reporting "Disk Has Many Bad Sectors" as soon as I boot the first time after installation. It's only on a Seagate Barracuda 7200.9 300GB drive. I have other WD and Seagate drives were I don't have the problem. 

SO, you'd think the drive is suspect. I ran Seatools on it and it passed, then I ran Spinrite 6.0 from GRC.COM for a recovery run then a low-level maintenance run. The drive has no bad sectors anywhere on the drive. In fact the spare sectors that could be used to replace a bad sector, should one occur, still remain at 100 out of 100 available.

I can only believe that the drive is good and Palimpsest is bad or at least confused on certain drives :)

---

### Post by jsp21c on 2010-04-09
Hi, I had the same notification with a 500GB Seagate ST7200.11 drive.
This drive did actually fail under Windows Vista even though it passed all the error checks including Acronis Disk Manager. The drive just suddenly slowed right down and shortly afterwards wouldn't boot but I was able to put it in an external dock and read off the information very slowly. Then while trying to reformat the disk it stalled at 75%. I'm pretty certain the disk was dead and was planning to break it up prior to taking it to the tip (recycling centre) along with some other computer junk.

A few weeks ago I tried Mint on the drive and it immediately signalled a bad drive with many bad sectors, however only yesterday while booting into Mint the bad disk notification from the takbar has gone. 
Perhaps the disk has sorted itself out, it definately did fail once, however it has been relegated to just a test disk and will still be junked at my next trip to the tip.

---

### Post by AlexanderDGreat on 2010-08-09
@jfaberna - I believe Palimpsest is Ubuntu's virus. That's a sh*^tY heLL of a program.

I have a NEW LAPTOP. OK? NEW Laptop! And it has already 377020 BAD Sectors.

I have a New 1 TB Seagate SATA Hard disk and it has already 9 BAD Sectors.

Now, tell if it's Sh&TY or what? I'm starting to hate Ubuntu, +1 year user here.

---

### Post by Fafler on 2010-08-09
I think it's a known issue with Palimpsest. Just ignore it.

I have the same issue with a Seagate drive on Debian, but all other tools says the drive is alright.

---

### Post by AlexanderDGreat on 2010-08-10
> I have the same issue with a Seagate drive on Debian, but all other tools says the drive is alright. - Yeah I know, but it's still there, just like I said, it's a VIRUS.

Can anyone help me? How do you use the launchpad.net website?

It's so ... confusing there.

There's a subscriber, but I don't see it when I want to go back to the list of bugs I'm subscribed at.

Also, it says, sometimes, FIXED RELEASED, so how do you apply the fix?

Please, please, help!

Here's the link of the bug of the palimpsest with Fixed Released. 

[https://bugs.launchpad.net/ubuntu/lucid/+source/libatasmart/+bug/438136]("https://bugs.launchpad.net/ubuntu/lucid/+source/libatasmart/+bug/438136")

---

