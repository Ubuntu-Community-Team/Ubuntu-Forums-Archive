---
title: "Installing"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by Jenzuko on 2009-05-17
Everytime I try to install (keeping windows) it gives me this error:
I thought it was the CD, so I got a new blank CD and burned Ubuntu onto it.
Same error.
Help please?

[click here for the image]("http://img266.imageshack.us/img266/540/screenshoty.png")

PS: Ubuntu rocks!

EDIT: Should I burn it at 10x?

---

### Post by zeex on 2009-05-17
> **Jenzuko said:**
> Everytime I try to install (keeping windows) it gives me this error:
I thought it was the CD, so I got a new blank CD and burned Ubuntu onto it.
Same error.
Help please?

[click here for the image]("http://img266.imageshack.us/img266/540/screenshoty.png")

PS: Ubuntu rocks!

EDIT: Should I burn it at 10x?

Hi, 

I don't think there is anything wrong with your CD or CD drive. It used to happen to me too. My drives used to freez all the time and same Input/Output error. What I did is rather different I switched to Debian Lenny. It's been more awesome than ever. I searched for this when i was using ubuntu. It has something to do with hard disk drivers. ubuntu shows IDE drives as SCSI (/dev/sda )drives and feels like there is bugs. My system hasn't hanged once after debian and debian uses IDE (/dev/hda) drivers.

---

### Post by Jenzuko on 2009-05-17
What exactly should I do?
Sorry, I pretty much don't understand what you're saying.

---

### Post by zeex on 2009-05-17
> **Jenzuko said:**
> What exactly should I do?
Sorry, I pretty much don't understand what you're saying.

well one thing you can try is that start installation right from the main menu right after you select the language. Right now you are letting the live CD boot up and then double clicking on install. This is a temporary solution though. Input/Output error is usually the result of hardware problem or hardware driver problems. You might experience system hang ups after installation

---

### Post by Jenzuko on 2009-05-17
> **zeex said:**
> well one thing you can try is that start installation right from the main menu right after you select the language. Right now you are letting the live CD boot up and then double clicking on install. This is a temporary solution though. Input/Output error is usually the result of hardware problem or hardware driver problems. You might experience system hang ups after installation

I get the same error when I try installing from the Ubuntu CD boot screen.

---

### Post by zeex on 2009-05-18
> **Jenzuko said:**
> I get the same error when I try installing from the Ubuntu CD boot screen.

Make sure that your BIOS is detecting your hard drives. It seems like BIOS is not detecting your HDD.

---

