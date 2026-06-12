---
title: "[brainstorm] partitioning multi OS scheme"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by caue.rego on 2009-06-27
I've read many posts about partitioning, but no solution with what I'm looking for. I've also tried many schemes, but still haven't got one that I consider good.

Think of it as an user. I hate partitions, I don't care how it is written on the disk, I just want data to be there for me. That's it.

Unfortunately each OS needs to be installed in its own partition, so there goes at least 2 just for that.

So I want opinions and suggestions from people who have at least 2 OS installed and what scheme worked for you.

And I'll edit this first post with my scheme up to the point where I get one I can be satisfied.

--

My current (ideal) scheme, as of 2009-06-27

If I use 10gb for each OS, that might not be enough for installing big programs, but it's a start. Linux can take up to 20gb as far as i know, windows go way beyond of 50gb counting with games and heavy applications, but fine with 30gb. Mac is the same. So, ideally, I would install all programs, and files and anything not directly related to the Operation System itself, in one big partition. So I could leave 10 or 15gb for each different one.

The problem is: which one? Is this even possible? If it's not possible, there would still be a question of which partition would be best for sharing files. I bet this is the most common scheme, using NTFS for the "local/common/data" partition (names I like to use).

I guess it's probably safe to discard all other partitions, and stick between ext3 and ntfs.

I know there are programs for both mac and windows to read ext3, but I can't get Mac to work, and I doubt windows would be all that good supporting as well.

The most evident choice again would be NTFS, but I want ubuntu's /home to go on it. And mac's /Applications, if possible. Maybe my question would go better on each plataform's NTFS supporting software.

Anyway, sorry for dumping this here. But I still hope this discussion can go on and get to a good common point.

---

### Post by merlinus on 2009-06-27
You can certainly use ntfs for sharing data between windows and linux, but I doubt that programs meant for one would work on the filesystem of the other.

For example, linux cannot use .exe files.

/home would have to be on ext3 for it to work properly.

I did read a post awhile ago claimng a fat32 usb flash drive could be used for running ubuntu.  You would have to search for it.

If you have the system resources, however, you could run one or the other os in a VM.

---

### Post by caue.rego on 2009-06-27
Yeah, I know that. But that'd be just a matter of using the different folders within the partition. No big deal. Ubuntu is already all about directories, even with just one big ext3, isn't it?

Maybe I forgot to mention I also know a little bit about the permission issues on using NTFS for ubuntu, specially as /home. Keep in mind the main argument here is: the less partitions the easier for the user.

Perhaps I'm missing an universal partition that just doesn't (or can't) exist.

---

### Post by Herman on 2009-06-27
I agree with you, caue.rego, I think one single partition would be best.

One idea is to install Ubuntu inside Windows with wubi. I haven't tried that, but I think it's quite a popular thing to do. 
Every time I'm working on a Windows computer though, I always miss may 'workspace switcher', down in the bottom taskbar on the right.

Another idea would be to install an emulator in Ubuntu like [VirtualBox]("http://www.virtualbox.org/") or something similar. With VirtualBox a person can run Windows inside Ubuntu. It's great because we can have Windows running in one workspace and easily switch workspaces for doing all our work or having fun in Linux.
Some people still need Windows just for one or two programs they can't run in Linux, which they claim there's no Linux equivalent for. 'MYOB is one such program, it's an accounting program that's very popular here in Australia, and almost every accountant can take data from that program and process it in their own MYOB program. I'm not sure if it's really true there's no Linux equivalent, but so I''m told.
If Windows is run in an emulator inside Linux, a user can run both OSes at once, so they can watch a movie in Ubuntu, and switch to Windows when a customer comes and wants to buy something and they need to enter the transaction in MYOB.
The downside is, they need a powerful computer with a lot of RAM, or both operating systems will run very slowly.

EDIT: It's also possible to install Ubuntu with no swap area, and make a swap file inside the Ubuntu partition later on. That's a good idea because then you can resize it more easily if you decide you want it larger or smaller later on, [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile") - by iva2k

---

