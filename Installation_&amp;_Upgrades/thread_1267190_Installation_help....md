---
title: "Installation help..."
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by Lewicide on 2009-09-15
I'm sure this is asked here on a daily basis, so I'm sorry if this is annoying you.

But I want to ask anyway.

I have partitioned my hard-drive already (so I can dual boot), but what I want to know is when I choose "custom" and select what part of the partition I want to use do I only need a "/" partition? As I know in fedora it requires 2 partitions (one for "/" and one for "/boot" or "/root" or something similar) and when I only choose one partition a box pops up telling me about a swap partition (an explanation on that would also be useful :P). I don't want to continue when there couldbe a potential problem.

Sorry for the newbiness of the question but I don't really want to cock this up. :)

---

### Post by tachuela on 2009-09-15
You don't need /boot

---

### Post by stlsaint on 2009-09-15
At least your coming for info prior to installing. Good step. 
1) for ubuntu you will need two partitions (/) & swap
2) rule of thumb make the swap partition about twice the size of your ram...ie ram=512 than swap=1024!
thats is why you get that box that pops up requiring you to do a swap partition. 

so yes make a root(/) and a swap.
If you really want to do some configs than you can make a seperate /home partition...but not unless you feel comfortable in what you are doing! please see signature for more resources.

Welcome to Ubuntu

---

### Post by Lewicide on 2009-09-15
> **stlsaint said:**
> At least your coming for info prior to installing. Good step. 
1) for ubuntu you will need two partitions (/) & swap
2) rule of thumb make the swap partition about twice the size of your ram...ie ram=512 than swap=1024!
thats is why you get that box that pops up requiring you to do a swap partition. 

so yes make a root(/) and a swap.
If you really want to do some configs than you can make a seperate /home partition...but not unless you feel comfortable in what you are doing! please see signature for more resources.

Welcome to Ubuntu

I have 6gig 'o ram. Will I really need to make the swap partition 12gb?

---

### Post by Lewicide on 2009-09-16
> **Lewicide said:**
> I have 6gig 'o ram. Will I really need to make the swap partition 12gb?

Sorry to "bump" this. But would I need 12gb for my swap partition or would a lower amount be okay?

---

### Post by presence1960 on 2009-09-16
> **Lewicide said:**
> I have 6gig 'o ram. Will I really need to make the swap partition 12gb?

6 GB will be fine if you want to hibernate. otherwise you won't need that much swap. With 6 Gb of RAM it is unlikely you will ever use your swap, unless you are doing some intensive work that requires major resources to run.

---

### Post by Lewicide on 2009-09-16
> **presence1960 said:**
> 6 GB will be fine if you want to hibernate. otherwise you won't need that much swap. With 6 Gb of RAM it is unlikely you will ever use your swap, unless you are doing some intensive work that requires major resources to run.
That sounds like good news to me. Does this mean I wont need to create a swap partition? And only need one partition? :D

---

### Post by presence1960 on 2009-09-16
> **Lewicide said:**
> That sounds like good news to me. Does this mean I wont need to create a swap partition? And only need one partition? :D
probably Ok, but if you don't want to use the hibernate function I would create a small swap partition just to be safe. Maybe 512 MB to 1 GB

---

### Post by alojarteya on 2009-09-16
I need my pc start with ubuntu, install it and win under normal installation and gives me this screen in both cases would give me a hand?[IMG]http://www.memory-srl.com.ar/img/como/ubuntu_error.jpg[/IMG]

---

### Post by Lewicide on 2009-09-16
> **presence1960 said:**
> probably Ok, but if you don't want to use the hibernate function I would create a small swap partition just to be safe. Maybe 512 MB to 1 GB
Okay I have created that partition. Wish me luck, I can see it saying something about the two partitions being on the same extension or something. Q_Q

---

### Post by presence1960 on 2009-09-16
> **alojarteya said:**
> I need my pc start with ubuntu, install it and win under normal installation and gives me this screen in both cases would give me a hand?[IMG]http://www.memory-srl.com.ar/img/como/ubuntu_error.jpg[/IMG]

Please start your own thread. That way the OP here and you get the best help possible. it becomes confusing trying to solve two different problems on the same thread. it is not fair to the OP, you or us trying to help both of you. Thank you for your understanding.

---

### Post by Lewicide on 2009-09-17
I have now stumbled across another problem. I have created my swap partition and that works out fine. But no matter what "hard drive type" I choose it always brings up an error and stops the installation for the "/" drive.

I'm trying to choose; ext2, ext3 or ext4. And every single one of those brings up some kind of error.

---

### Post by presence1960 on 2009-09-17
> **Lewicide said:**
> I have now stumbled across another problem. I have created my swap partition and that works out fine. But no matter what "hard drive type" I choose it always brings up an error and stops the installation for the "/" drive.

I'm trying to choose; ext2, ext3 or ext4. And every single one of those brings up some kind of error.

Please give specific details about the error(s). Are they during the install. When you create the Ubuntu (/) partition are you using the drop down box on mount point to specify / as mount point?

More specific details will be helpful to pinpoint your exact problem and the the solution.

---

### Post by Lewicide on 2009-09-18
> **presence1960 said:**
> Please give specific details about the error(s). Are they during the install. When you create the Ubuntu (/) partition are you using the drop down box on mount point to specify / as mount point?

More specific details will be helpful to pinpoint your exact problem and the the solution.
It happens when I install. It stops the installation and goes back to the partition selecting.

---

### Post by Lewicide on 2009-09-21
> **Lewicide said:**
> It happens when I install. It stops the installation and goes back to the partition selecting.
I know bumping is probably frowned upon hear. But there's no other ways I'll get an answer to this without another topic. So bump!

---

### Post by presence1960 on 2009-09-21
Did you try the alternate text based installer? get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Lewicide on 2009-09-21
> **presence1960 said:**
> Did you try the alternate text based installer? get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")
I'm sure that the reason is not a graphical issue.

---

### Post by presence1960 on 2009-09-21
> **Lewicide said:**
> I'm sure that the reason is not a graphical issue.
The alternate text based installer works a lot of times when the Live Cd will not. Did you try it or will you keep repeating the same thing over & over expecting different results?

---

### Post by Lewicide on 2009-09-22
> **presence1960 said:**
> The alternate text based installer works a lot of times when the Live Cd will not. Did you try it or will you keep repeating the same thing over & over expecting different results?
I suppose that's my only option then. I thought it would only sort it out if the issue was graphical, sorry.

---

### Post by presence1960 on 2009-09-22
> **Lewicide said:**
> I suppose that's my only option then. I thought it would only sort it out if the issue was graphical, sorry.

No biggie lewicide, just want you to get it installed. You've tried the Live CD with no success, trying the alternate won't hurt.

---

