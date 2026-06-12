---
title: "help with selecting a partition?"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-01-26
I currently run a windows machine with 3 partitions
I want to install ubuntu on drive C
Which option do I select in the installer?

---

### Post by castor_troy on 2009-01-26
When you say C: drive, I presume that it is the drive on which WIndows is installed. 

Now, as you want to install Ubuntu on the same drive you have to select the "Resize existing the Windows partition" in the installer.

Then allocate the desired sapce you want for Ubuntu.

You don't need a huge amount of space for Ubuntu. You will need enough space for the following:

1.Root partition - where Ubuntu is installed. This should be at least 4GB.
2.Home partition - where your files are kept.
3.Swap partition - this need only be twice the size of your memory.

Now, if you dont want to, you need not create two seperate partitions for "Home" and "Root". But it is advisable to create allocate "swap".

---

### Post by mahela007 on 2009-01-26
No. windows is not installed on my C drive
Windows in installed on F. In installed windows on F for this very purpose.. (installing ubuntu on C)

---

### Post by russu52 on 2009-01-26
when you are on windows, keep a mental note of the partition sizes (unless they are equal) installer will tell you if you have an existing operating system in that partition. select that partition and direct ubuntu to use it all. should do

---

### Post by mahela007 on 2009-01-26
> **russu52 said:**
> when you are on windows, keep a mental note of the partition sizes (unless they are equal) installer will tell you if you have an existing operating system in that partition. select that partition and direct ubuntu to use it all. should do
Could you please give me more details? I am a bit confused and I don't wan to mess up my hard drive

---

