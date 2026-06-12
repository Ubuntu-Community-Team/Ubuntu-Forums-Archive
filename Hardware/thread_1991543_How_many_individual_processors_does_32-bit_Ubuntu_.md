---
title: "How many individual processors does 32-bit Ubuntu 11.10 support?"
date: 2012-05-30
forum: Hardware
---

### Post by dkzhaos on 2012-05-30
Hi,
 
I installed 32 bit Ubuntu 11.10 on two Servers, which each one has a 6-core Xeon X5675 3.07GHz cpu. I suppose to have 12 processors for each 6-core cpu, but I only can see 8 processors. I knew Ubuntu 11.10 kernel will detect the number of processors (or processor cores) . I don't have any idea why I cannot see all 12 processors. I really appreciate your reply. Thanks!

---

### Post by Slim Odds on 2012-05-30
> **dkzhaos said:**
> Hi,
 
I installed 32 bit Ubuntu 11.10 on two Servers, which each one has a 6-core Xeon X5675 3.07GHz cpu. I suppose to have 12 processors for each 6-core cpu, but I only can see 8 processors. I knew Ubuntu 11.10 kernel will detect the number of processors (or processor cores) . I don't have any idea why I cannot see all 12 processors. I really appreciate your reply. Thanks!
You should most certainly use the 64 bit version of Ubuntu.

More info: [https://answers.launchpad.net/ubuntu/+question/9820](https://answers.launchpad.net/ubuntu/+question/9820)

---

### Post by dkzhaos on 2012-05-30
> **Slim Odds said:**
> You should most certainly use the 64 bit version of Ubuntu.
 
Thank you for your reply! Yes, I know. But for some performance issues, I have to use 32 bit version for now. I don't find any offical documents talk about the maximum number of individual processors the 32-bit Ubuntu support, and I don't think 32 bit version of Ubuntu only support 8 processors.

---

### Post by Slim Odds on 2012-05-30
> **dkzhaos said:**
> Thank you for your reply! Yes, I know. But for some performance issues, I have to use 32 bit version for now. I don't find any offical documents talk about the maximum number of individual processors the 32-bit Ubuntu support, and I don't think 32 bit version of Ubuntu only support 8 processors.

Please see link added to my previous post

---

### Post by dkzhaos on 2012-05-30
> **Slim Odds said:**
> Please see link added to my previous post
 
Your link did not answer the question.

---

### Post by dkzhaos on 2012-05-30
Hi,

I installed 32 bit Ubuntu 11.10 on two Servers, which each one has a 6-core Xeon X5675 3.07GHz cpu. I suppose to have 12 processors for each 6-core cpu, but I only can see 8 processors. I knew Ubuntu 11.10 kernel will detect the number of processors (or processor cores) . I don't have any idea why I cannot see all 12 processors. I really appreciate your reply. Thanks!

---

### Post by howefield on 2012-05-30
Threads merged.

Please do not post duplicate threads.

---

### Post by Slim Odds on 2012-05-31
It looks like Ubuntu limits the 32 bit version to 8 cores....

[http://ubuntuforums.org/showthread.php?t=1226102](http://ubuntuforums.org/showthread.php?t=1226102)

Again, for a server you should really be using 64 bit.

Your other choice is to compile a custom kernel

---

