---
title: "Partition definitions"
date: 2008-07-13
forum: General Help
---

### Post by JR Tyner on 2008-07-13
I'm getting ready to install Ubuntu or Kubuntu. I want to do an advanced install. I know how to partition, but I can't find any definitions about what each partition is for.

Can I get a list of each partition type, what it's for, what it should be partitioned as, how big it needs to be, and anything else I need to know.

---

### Post by VMC on 2008-07-13
> **JR Tyner said:**
> I'm getting ready to install Ubuntu or Kubuntu. I want to do an advanced install. I know how to partition, but I can't find any definitions about what each partition is for.

Can I get a list of each partition type, what it's for, what it should be partitioned as, how big it needs to be, and anything else I need to know.

This [HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") might be able to answer your questions.

---

### Post by mikewhatever on 2008-07-13
/ - root partition - that's where the system is.
swap - swap is similar to Windows page file, and is used to extend RAM.
/home - that's where users' settings and files are. (doesn't have to be a partition)

[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by JR Tyner on 2008-07-13
> **VMC said:**
> This [HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") might be able to answer your questions.

Those are things I already know from past Linux installs.

I've been just making a root and swap partition, but now I want to do more.

---

### Post by mikewhatever on 2008-07-13
> **JR Tyner said:**
> Those are things I already know from past Linux installs.

I've been just making a root and swap partition, but now I want to do more.

Then, you may want to look at some of these:
[http://www.google.co.il/search?hl=iw&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Qbu&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=linux+directory+structure&spell=1](http://www.google.co.il/search?hl=iw&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Qbu&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=linux+directory+structure&spell=1)

---

### Post by JR Tyner on 2008-07-14
> **mikewhatever said:**
> Then, you may want to look at some of these:
[http://www.google.co.il/search?hl=iw&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Qbu&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=linux+directory+structure&spell=1](http://www.google.co.il/search?hl=iw&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Qbu&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=linux+directory+structure&spell=1)

Yeah, that helps. I tried using google myself before posting but I could only find the same information for first timer Linux users on how to have the live CD do it for you, the only difference was the ads.

---

### Post by JR Tyner on 2008-07-14
So this is what I understand so far:
  
Partition | what it's for ___ | partitioned as | size ______________ | other
/ _______ | system storage __ | EXT3 __________ | 3GB? ______________ | ?
swap ____ | extend RAM ______ | SWAP __________ | 3GB _______________ | ?
/home ___ | files ___________ | EXT3 __________ | As big as it can be?| ?
/boot ___ | boot loader _____ | EXT3 __________ | 200mb _____________ | ?
/usr ____ | for more users __ | _______________ | I won't need this _ | ?
/var ____ | variable data ___ | EXT3 __________ | 1000mb? ___________ | ?
/opt ____ | software packages | _______________ | ? _________________ | ?
/tmp ____ | temporary files _ | EXT3 __________ | 500mb? ____________ | ?
/export _ | _________________ | _______________ | ? _________________ | ?

---

### Post by bodhi.zazen on 2008-07-14
Well, it almost begs the question why ???

If you do not know what all the partitions are for, how do you know you need to put them on a separate partition, what are you hoping to accomplish ?

At any rate :

[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html)

[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

---

### Post by JR Tyner on 2008-07-14
> **bodhi.zazen said:**
> Well, it almost begs the question why ???

Knowledge for the sake of knowledge. I guess it's an out dated concept now. 

> **bodhi.zazen said:**
> If you do not know what all the partitions are for, how do you know you need to put them on a separate partition, what are you hoping to accomplish ?

If I do not know what all the partitions are for, how do I know what needs to be put on a separate partition? 

For example, I know I need to start making home partitions to make updating easier.

I'm hoping to accomplish a better understanding of Linux.

---

### Post by bodhi.zazen on 2008-07-14
OK, well best understand what they are first.

You can also look at these links :

[http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2](http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2)

[http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ap-checklist.en.html](http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ap-checklist.en.html)

See the short partitioning section on that second link.

If you do not understand fstab options :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Knowledge for knowledge sake is fine, making your system complex is another, :lolflag:

---

### Post by JR Tyner on 2008-07-14
> **bodhi.zazen said:**
> OK, well best understand what they are first.

You can also look at these links :

[http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2](http://www.debian.org/doc/manuals/securing-debian-howto/ch3.en.html#s3.2)

[http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ap-checklist.en.html](http://www.linuxsecurity.com/resource_files/host_security/securing-debian-howto/ap-checklist.en.html)

See the short partitioning section on that second link.

If you do not understand fstab options :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

Knowledge for knowledge sake is fine, making your system complex is another, :lolflag:


That really helps :biggrin:

So I don't missunderstand something, I'll post what I think I learned, and if I missunderstood anything, someone please let me know...

---

### Post by JR Tyner on 2008-07-14
Intelligent partition scheme

> Any directory tree which a user has write permissions to, such as e.g. /home, /tmp and /var/tmp/, should be on a separate partition. 

I knew I needed to start making a /home partition, I was tired of losing things when I update the system.

I had heard that you should make a /tmp partition and a /var partition for security reasons. I am installing on my laptop that I use for personal banking and for work, so security is a concern. If you are not worried about security on your laptop, read this: [http://blogs.techrepublic.com.com/hiner/?p=747&tag=rbxccnbtr1]("http://blogs.techrepublic.com.com/hiner/?p=747&tag=rbxccnbtr1")

> Any partition which can fluctuate, e.g. /var (especially /var/log) should also be on a separate partition. On a Debian system, you should create /var a little bit bigger than on other systems, because downloaded packages (the apt cache) are stored in /var/cache/apt/archives. 

So should I make a /var partition, a /var/log partition, and a /var/cache partition?

> Any partition where you want to install non-distribution software should be on a separate partition. According to the File Hierarchy Standard, this is /opt or /usr/local. If these are separate partitions, they will not be erased if you (have to) reinstall Debian itself.
 
"If these are separate partitions, they will not be erased if you (have to) reinstall Debian itself." :biggrin:

So I whould make one for my games and another for the programs I need for work? Will I need to install WINE on each?

> From a security point of view, it makes sense to try to move static data to its own partition, and then mount that partition read-only. Better yet, put the data on read-only media. See below for more details. 

:confused:

> In the case of a mail server it is important to have a separate partition for the mail spool. Remote users (either knowingly or unknowingly) can fill the mail spool (/var/mail and/or /var/spool/mail). If the spool is on a separate partition, this situation will not render the system unusable. Otherwise (if the spool directory is on the same partition as /var) the system might have important problems: log entries will not be created, packages cannot be installed, and some programs might even have problems starting up (if they use /var/run). 

That's something I should have been doing a long time ago. :)

> Also, for partitions in which you cannot be sure of the needed space, installing Logical Volume Manager (lvm-common and the needed binaries for your kernel, this might be either lvm10, lvm6, or lvm5). Using lvm, you can create volume groups that expand multiple physical volumes. 

:confused:

---

### Post by JR Tyner on 2008-07-14
How do you delete a post? I accidently posted the same thing twice.

---

### Post by JR Tyner on 2008-07-14
[IMG]http://img.photobucket.com/albums/v617/bluefrogk0e/bumpjar.gif[/IMG]

---

### Post by Vivaldi Gloria on 2008-07-14
Watch 

[http://www.archive.org/details/HampshireLinuxUserGroup_15](http://www.archive.org/details/HampshireLinuxUserGroup_15)

and read "Linux Filesystem Hierarchy" from

[http://tldp.org/guides.html](http://tldp.org/guides.html)

to learn more about filesystem hierarchy.

In a regular desktop install there is no point in having extra partitions for everything in root. Just make partitions for swap, /home, and /.

---

### Post by bodhi.zazen on 2008-07-14
I would not make a separate partition for /var/log and /var cache.

As long as you are learning, you could alwaus look at LVM too. LVM allows you to resize partitions.

As far as static == ro, you will have to determine what content you have that is static. The how-to's you are reading are geared @ servers, so content for web pages or ftp downloads ....

To some extent you will need to proceed by trial and error.

---

### Post by JR Tyner on 2008-07-17
Ok, I've been studying and I'm ready to start practicing. 

Here's what I got so far:

---

### Post by bodhi.zazen on 2008-07-17
40 Gb is wayyyyyyyyyyyyyyyyyyy tooooooooooooooooo bigggggggggggggggggg

for /root

/root is root's $HOME

/root on my system is less then 150 Kb

and /usr, 0 is 2 small. usr = unix system resources

/usr on my system is 1.9 Gb

15 Gb is way too big for /var/mail, unless you are running a mail server.

lol

---

### Post by JR Tyner on 2008-07-17
> **bodhi.zazen said:**
> 40 Gb is wayyyyyyyyyyyyyyyyyyy tooooooooooooooooo bigggggggggggggggggg

for /root

/root is root's $HOME

/root on my system is less then 150 Kb

I thought root was for programs.

> **bodhi.zazen said:**
> 
and /usr, 0 is 2 small. usr = unix system resources

/usr on my system is 1.9 Gb


I put 0 because I wasn't going to make a /usr because I thought it was only needed for multiple users.

> **bodhi.zazen said:**
> 
15 Gb is way too big for /var/mail, unless you are running a mail server.


It will in part function as a Mail server.

> **bodhi.zazen said:**
> 
lol


This is one of the reasons I'm trying to learn this.

---

### Post by bodhi.zazen on 2008-07-17
"root" has many hats. Of course root is the ultimate administrative user.

/ = root = base of file system (similar to C:\ if you have a windows background).

/root = root's home

To see the location of binaries :

```
echo $PATH
```

Yes, usr != user (that is a common mistake)

If you like, post your new partition scheme and we can look at it some more.

---

### Post by JR Tyner on 2008-07-17
> **bodhi.zazen said:**
> "root" has many hats. Of course root is the ultimate administrative user.

/ = root = base of file system (similar to C:\ if you have a windows background).

/root = root's home

To see the location of binaries :

```
echo $PATH
```

Yes, usr != user (that is a common mistake)

If you like, post your new partition scheme and we can look at it some more.

Thanks. I'm going to buy a book on Ubuntu with my next check. What do you suggest?

What about:
/export
/bin
/var/spool/mail
/var/tmp

---

### Post by Vivaldi Gloria on 2008-07-17
> **JR Tyner said:**
> I'm going to buy a book on Ubuntu with my next check. What do you suggest?


A Practical Guide to Ubuntu Linux (Sobell)

Unix Power Tools, Third Edition (Powers, Peek, O'Reilly, Loukides)

Guides at [www.tldp.org](www.tldp.org)

---

### Post by Vivaldi Gloria on 2008-07-17
I attach a list showing the actual space usage in Hardy system. Home is low because I keep my things in a file server.

So you need to increase the size of some of your partitions like usr and var.

But then I suggest again that you don't make all these partitions. Not needed in a desktop system.

---

### Post by JR Tyner on 2008-07-18
What partition should I put downloads in that may contain a virus or other malicious code?

---

### Post by bodhi.zazen on 2008-07-18
> **JR Tyner said:**
> What partition should I put downloads in that may contain a virus or other malicious code?

/dev/null :lolflag:

---

### Post by JR Tyner on 2008-07-18
> **bodhi.zazen said:**
> /dev/null :lolflag:

That won't help.

---

### Post by Vivaldi Gloria on 2008-07-18
> **bodhi.zazen said:**
> /dev/null :lolflag:

:-)

He's right of course.

---

### Post by JR Tyner on 2008-07-18
> **Vivaldi Gloria said:**
> :-)

He's right of course.

No. 

Any file that I didn't make myself could be dangerous.

---

### Post by avtolle on 2008-07-18
The point that is being made with good humor is that this is something that one must worry about in Windows constantly, but is not anything to be concerned about in Linux. The reasons are manifold. Perhaps the best security is, after all, the user him/herself not blindly copying code to execute, etc., but as a practical matter, any malicious code that might try to attack your system, given the way Linux works, would need to be run as "root", and unless you allow it to run, it cannot attack your system. There's a whole lot more to this, and the above is overly general and simplistic, but hopefully it makes the point.

---

### Post by JR Tyner on 2008-07-18
I just thought if I had a secure/encrypted partition for downloads and testing code, I'd feel better trying new programs and code that people post.

The thing about new programs is that they could be posted in good faith, but the author doesn't realize that it can cause trouble on some systems.

---

### Post by Vivaldi Gloria on 2008-07-18
avtolle explained it nice. You are safe as long as you don't run malicious scripts with your own hands. Look here:

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by Vivaldi Gloria on 2008-07-18
> **JR Tyner said:**
> I just thought if I had a secure/encrypted partition for downloads and testing code, I'd feel better trying new programs and code that people post.

The thing about new programs is that they could be posted in good faith, but the author doesn't realize that it can cause trouble on some systems.

If you want to play with fire you can always do it safely in a virtual system. Install for example virtual box and ubuntu in it and test whatever you want.

A couple of weeks ago forestpixie destroyed a xubuntu in a virtual system using a command you should never use in a real system. Read here:

[http://ubuntuforums.org/showthread.php?t=851377&highlight=chmod](http://ubuntuforums.org/showthread.php?t=851377&highlight=chmod)

So your system should not be a playground for dangerous commands. But you can have all the fun in a virtual system. :)

---

### Post by bodhi.zazen on 2008-07-18
> **JR Tyner said:**
> I just thought if I had a secure/encrypted partition for downloads and testing code, I'd feel better trying new programs and code that people post.

The thing about new programs is that they could be posted in good faith, but the author doesn't realize that it can cause trouble on some systems.

An encrypted partition will not help you much here. Encryption keeps people from accessing information without the keys. Once an encrypted partition is mounted however it is no more or less secure then any other partition.

Put this kind of code on a partition mounted with the options noexec,nosuid

---

### Post by bodhi.zazen on 2008-07-18
> **Vivaldi Gloria said:**
> So your system should not be a playground for dangerous commands. But you can have all the fun in a virtual system. :)

Or a (jailed) chroot ;)

---

### Post by Vivaldi Gloria on 2008-07-18
> **bodhi.zazen said:**
> Or a (jailed) chroot ;)

Hmm. I don't know about chroot. I did a man chroot just now. How can you use it to test scripts etc?

[]("http://wiki.mandriva.com/en/Development/Howto/Chroot")

---

### Post by bodhi.zazen on 2008-07-18
> **Vivaldi Gloria said:**
> Hmm. I don't know about chroot. I did a man chroot just now. How can you use it to test scripts etc?



Yes. chroot can be used for development or isolating servers. You can also chroot into an installed Linux. For example, you can run Fedora, chroot into Ubuntu, apt-get upgrade ubuntu, do some development or test some packages, all without booting ubutnu. You can forward X applicaions from a chroot as well.

You might also like openvz

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

(I ssh in and forward X to Xephyr)

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)

---

### Post by Vivaldi Gloria on 2008-07-18
> **bodhi.zazen said:**
> Yes. chroot can be used for development or isolating servers. You can also chroot into an installed Linux. For example, you can run Fedora, chroot into Ubuntu, apt-get upgrade ubuntu, do some development or test some packages, all without booting ubutnu. You can forward X applicaions from a chroot as well.

You might also like openvz

[http://wiki.openvz.org/Main_Page](http://wiki.openvz.org/Main_Page)

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

(I ssh in and forward X to Xephyr)

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)

Thanks a lot mate. :) Reading the links now.

---

### Post by JR Tyner on 2008-07-18
> **bodhi.zazen said:**
> Or a (jailed) chroot ;)

Can you explain that to me?

---

### Post by JR Tyner on 2008-07-18
> **bodhi.zazen said:**
> An encrypted partition will not help you much here. Encryption keeps people from accessing information without the keys. Once an encrypted partition is mounted however it is no more or less secure then any other partition.

Put this kind of code on a partition mounted with the options noexec,nosuid

So we're dealing with the fstab file here. 

If I understand this right, then I'd be configuring my system to not run any binaries on this partition.

Could someone explain the "nosuid" option to me?

---

### Post by Vivaldi Gloria on 2008-07-18
> **JR Tyner said:**
> Can you explain that to me?

I said that you can run any script you want safely in a virtaul sytem and bodhi.zazen said that there is also an alternative method using the chroot command. But it's a bit more advanced stuff and I don't know it either yet. See the links bodhi.zazen gave.

I suggest you install ubuntu in virtualbox to try out scripts and programs in it. It is really simple.

---

### Post by JR Tyner on 2008-07-18
Sorry, I'm still trying to understand this.

Virtualbox is a program I can run to test code right?

---

### Post by Vivaldi Gloria on 2008-07-18
> **JR Tyner said:**
> So we're dealing with the fstab file here. 

If I understand this right, then I'd be configuring my system to not run any binaries on this partition.

Could someone explain the "nosuid" option to me?


Quoted from bodhi.zazen's fstab guide:

> exec / noexec - Permit/Prevent the execution of binaries from the filesystem.
suid/nosuid - Permit/Block the operation of suid, and sgid bits.

which can be found here:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

So what are these suid, and sgid bits?

> If I set the SUID or SGID bit for a file, this causes any persons or processes that run the file to have access to system resources as though they are the owner of the file. So an executable which has the SUID set runs with the ownership of the program owner. That is, if you own an executable, and another person issues the executable, then it runs with your permission and not his. The default is that a program runs with the ownership of the person executing the binary.

See

[http://www.howtoforge.com/linux_setting_suid_sgid_bits](http://www.howtoforge.com/linux_setting_suid_sgid_bits)
[http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)
[http://www.linuxquestions.org/questions/linux-general-1/what-is-sticky-bit-mode-suid-sgid-258719/](http://www.linuxquestions.org/questions/linux-general-1/what-is-sticky-bit-mode-suid-sgid-258719/)

Now I'm going to sleep. Good night boys and girls. :-)

---

### Post by Vivaldi Gloria on 2008-07-18
> **JR Tyner said:**
> Sorry, I'm still trying to understand this.

Virtualbox is a program I can run to test code right?

Virtualbox is a program which you can install a complete ubuntu (or any other OS) in it independent of your system. An OS installed in it never sees or knows of your system. People like trying out OSes in virtualbox since it doesn't disturb your system in any way. Have a look at virtualbox subforums here. Or better, first install it and then have a look at virtualbox subforums.

Now I'm really off to sleep. :-)

---

### Post by JR Tyner on 2008-07-18
> **Vivaldi Gloria said:**
> I attach a list showing the actual space usage in Hardy system. Home is low because I keep my things in a file server.

So you need to increase the size of some of your partitions like usr and var.

But then I suggest again that you don't make all these partitions. Not needed in a desktop system.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78022&d=1216292258[/IMG]


You don't have a "/".

---

### Post by supershin on 2008-07-19
Interesting thread. I've followed along pretty well but I have some questions. 
 So the purpose of having separate partitions is because its a big advantage, easier to update, in a multi-user environment which has many users and doesn't provide much benefit in a single desktop environment? 
 chroot changes the root, so you can access a root directory or a kernel? Basically allowing you to run as though you're in ubuntu whereas you're really in fedora? 
 Virtualbox sounds awesome! I take it i can execute the forbidden rm -rf in there and have all my XP and linux data safe. I wonder how it would crash? Black screen? Error code galore? popup with "this program terminated unexpectedly. Send report?"  lol.

---

### Post by JR Tyner on 2008-07-19
Is this better?

What do you think of me editing the fstab file so that the /usr/local partition is mounted with the options noexec and nosuid? Can I install my P2P and BitTorrent here?

---

### Post by JR Tyner on 2008-07-19
[IMG]http://img.photobucket.com/albums/v617/bluefrogk0e/bumpjar.gif[/IMG]

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> You don't have a "/".

Yeah, I copied and pasted the contents of my / (other than /mnt) there. 

I actually have two partitions: / and swap. I keep my music, videos etc on different disks and I mount them in /mnt and put symlinks in my home folder.

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> Is this better?


I cannot comment on the size of /var because I've never used email programs in my system.

**/export** - What is that?

**/bin and /sbin** - You cannot make seperate partitions for these. They have to be in the root partition. They are fundamental for boot and mounting other partitions. 

**/** - There are lot of folders in /: The following five /bin, /dev, /sbin, /lib, /proc, take 1.5GB in my system. So 2GB could be enough but increase a bit to be on the safe side.

**/boot**  When there are kernel updates the old kernels are not deleted and they are in /boot. After 4 or 5 updates the size will go over 80 MBs. Then you can delete the old kernels using synaptic to keep /boot size smaller. You should really keep at least two different kernels as a failsafe. I don't bother deleting kernels at all. If one they they go over 300 MBs then I'll delete older ones for sure, but before that happens the new ubuntu comes out and I'll install it. 

So 80 MB is not enough in the following scenario: You'll keep your ubuntu installation for at least a few months and you don't intend to delete old kernels.

**/etc** Make it 30 MB to be on the safe side.

**/tmp** The first time I installed linux I put in a /tmp partition of size 10GB. Why? Bacause a double layer dvd is about 9GBs. If you use a video editor or dvd maker then they use /tmp by default and the size of /tmp can reach that big. Now you can of course change the default settings of every one of the video editors, sound rippers, dvd makers etc to use another folder, say in your home folder. But I didn't want to go through each of them one by one and change their settings so I put a 10GB /tmp. But 10GB /tmp is a lot of waste of space as the system normally uses about 100 MBs. 

Actually this is one of the reasons why I suggested you make partitions only for /, swap, and /home. Then the rest of them are in the partition of / and they can share everything between them. You don't have to think about what each will get. They will arrange space among themselves. /tmp will use 100MB during normal operation and use 700MBs when you rip a cd. More on making partitions in the below post.

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> Is this better?

What do you think of me editing the fstab file so that the /usr/local partition is mounted with the options noexec and nosuid? Can I install my P2P and BitTorrent here?

I'm not sure I understand you.

P2P programs themselves - these should be executable,

Things downloaded using P2P programs - better not executable. 

/usr/local - there are a lot of programs there so you cannot mount it with noexec, nosuid.

---

### Post by Vivaldi Gloria on 2008-07-19
Most of these separate partitions don't make any sense in a desktop system. You should think of mainframes with a lot of users to make sense of them. There are two independent properties of filesystems: shareable vs. unshareable and static vs. dynamic. These are explained in the Filesystem Hierarchy Standard (link below). Shareable resources can be used by different users, unshareable ones cannot. Static folder/files do not change without sysadmin intervention but dynamic ones do. Examples:

/usr - shareable, static
/boot - unshareable, static

etc. So sysadmins put different type of filesystem in different file servers.

But a desktop is generally used by a single person at a time and users are admins. So there is no point in making all these different partitions in general. 

The only point of a seperate partiton in a desktop system is if you intend to keep the contents of that partition intact from one install to another. Are you going to keep the contents of the following directories /tmp, /usr, /var (other than /var/mail), /etc, /boot from one install to another? No! So what is the point of having extra partitions for them? 

By making less partitions you get the benefit I mentioned above - different top directories (/etc, /tmp, /usr so on) will share the space between them automatically and you don't have the problem of allocating space for them explicitly.

So I suggest you don't make unnecessary partitions for top system directories. But I understand you that making these partitions is fun. :-)  Still there is a lot of other fun things in linux that you can play with.

Filesystem Hierarchy Standard
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by Vivaldi Gloria on 2008-07-19
> **supershin said:**
>  So the purpose of having separate partitions is because its a big advantage, easier to update, in a multi-user environment which has many users and doesn't provide much benefit in a single desktop environment? 

Well, I think I answered this in my above post. I agree that partitioning doesn't provide much benefit in a single desktop environment.

> chroot changes the root, so you can access a root directory or a kernel? Basically allowing you to run as though you're in ubuntu whereas you're really in fedora? 

As far as I understand, yes. 

>  Virtualbox sounds awesome! I take it i can execute the forbidden rm -rf in there and have all my XP and linux data safe. 

Yes you can do rm -rf / in vbox without damaging your real OS.

> I wonder how it would crash? Black screen? Error code galore? popup with "this program terminated unexpectedly. Send report?"  lol.

Well, forestpixie destroyed a xubuntu in a vbox system with another code and during boot it gave a lame error. Just that. See one of my above posts to find the link.

---

### Post by JR Tyner on 2008-07-19
> **Vivaldi Gloria said:**
> I'm not sure I understand you.

P2P programs themselves - these should be executable,

Things downloaded using P2P programs - better not executable. 

/usr/local - there are a lot of programs there so you cannot mount it with noexec, nosuid.

I don't download executables using P2P, so no problem.

---

### Post by JR Tyner on 2008-07-19
Here's some things I need clearing up on:

/var/mail/  I want to protect my mail and Thunderbird settings. 

/var/spool/  This is supose to be for unread mail. 

/var/spool/mail/  Deprecated location for users' mailboxes.
 
/var/tmp/  Temporary files to be preserved between reboots, which can be important since I'm using a laptop that can lose power. This is also why I chose the XFS journaling system. I did chose the ext3 system for home since it works better during installation.

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> Here's some things I need clearing up on:


1) /var/spool & /var/spool/mail 

These contain no mail in ubuntu. Actually /var/spool/mail links to /var/mail. So forget about them.

2) /var/tmp Temporary files to be preserved between reboots ...

But hardly any program uses that folder. 10 MB is more than enough. Besides they are preserved between reboots whether or not you make a partition for it. There is absolutely no reason for making a separate partition for it. If you do, you'll be the first in history. :-)

3) Why do you want a separate partition for /usr/local?

4) I suggest you use this partitioning:

```
/ - 15GB or 20GB
/var/mail - 1GB
swap - 2 times your RAM
/home - the rest

```

and you don't make any more partitions at all.

---

### Post by JR Tyner on 2008-07-19
> **Vivaldi Gloria said:**
> 1) /var/spool & /var/spool/mail 

These contain no mail in ubuntu. Actually /var/spool/mail links to /var/mail. So forget about them.

2) /var/tmp Temporary files to be preserved between reboots ...

But hardly any program uses that folder. 10 MB is more than enough. Besides they are preserved between reboots whether or not you make a partition for it. There is absolutely no reason for making a separate partition for it. If you do, you'll be the first in history. :-)

3) Why do you want a separate partition for /usr/local?

4) I suggest you use this partitioning:

```
/ - 15GB or 20GB
/var/mail - 1GB
swap - 2 times your RAM
/home - the rest

```

and you don't make any more partitions at all.


Why is "/" that big?

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> Why is "/" that big?

Because I make no separate partitions for /usr, /etc, /tmp, /var, /opt, /boot etc. and they are all in /.

---

### Post by JR Tyner on 2008-07-19
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Says I only need 5GB. I'm trying to get away with as much space for my programs as possible.

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> ... Says I only need 5GB. 

My / is 11.2 GB. But I have a lot of things installed (including the full texlive > 1GB and 2GB of google earth cache). So may be something less than 10GB is OK.

> I'm trying to get away with as much space for my programs as possible.

But all programs will be in /. All your personal data (videos, music, pix etc) will be in /home.

---

### Post by JR Tyner on 2008-07-19
```

/ - 26GB
/var/mail - 1GB
swap - 3GB
/home - 70GB

```

---

### Post by Vivaldi Gloria on 2008-07-19
> **JR Tyner said:**
> ```

/ - 26GB
/var/mail - 1GB
swap - 3GB
/home - 70GB

```

26 GB is a bit excessive but other than that it looks good. Do you really have so many programs to install that requires 26GB? I suggest you take some from / and give to /home.

---

### Post by JR Tyner on 2008-07-19
> **Vivaldi Gloria said:**
> 26 GB is a bit excessive but other than that it looks good. Do you really have so many programs to install that requires 26GB? I suggest you take some from / and give to /home.

Ahh. I was using the reverse thinking in that 70GB was plenty for my home.

I'd still like to have a small partition to set as the download location for my P2P. The only thing I download are documents and graphics packs. These are the safest files being manly .txt, .pdf, and various image files. The problem is that some of them come archived and others with an installer. I would feel better if I had a small partition to download to and decompress in. That way I can scan it first.

---

### Post by bab1 on 2008-07-19
Okay,. I'll bite.  This is a great discussion.  How about we add that not all partitions need to be "on the same spindle".  Huh????  Some of the reasons for putting things on different partitions is for relability.  This can be achieved with mounting the partitions from multiple hard drives.  Hard drives are physical things and partitions are virtual things.  You can mount, for example /home on a separate hard drive and to the user it looks the same.

Think of the various filesystems that start at / (like /usr) as mount points for other partitions.  They may be...or not.

---

### Post by JR Tyner on 2008-07-19
Maybe this thread should be moved to security now.

---

### Post by lswb on 2008-07-20
I would advise that it is unnecessary to have all these separate partitions. Just have a / , a swap , and maybe a separate partition for data or for experimenting with later. If you think you may be dual or multi-booting with other operations systems or distributions later, a small partition for the grub bootloader might be helpful, maybe 500MB or so. Note I am NOT talking about a /boot partition.

---

### Post by Vivaldi Gloria on 2008-07-20
> **bab1 said:**
> Okay,. I'll bite.  This is a great discussion.  How about we add that not all partitions need to be "on the same spindle". 

Sure. I considered the case when one has only one disk like the op does. The more disks, the more possibilities.

---

### Post by Vivaldi Gloria on 2008-07-20
> **JR Tyner said:**
> I'd still like to have a small partition to set as the download location for my P2P. The only thing I download are documents and graphics packs. These are the safest files being manly .txt, .pdf, and various image files. The problem is that some of them come archived and others with an installer. I would feel better if I had a small partition to download to and decompress in. That way I can scan it first.

How much do you need? You can make a partition of size say 10GBs to keep downloads. You can mount it in /mnt/download and put a symlink where ever you want.

How about this:

```
/ - 15GB
/var/mail - 1GB
swap - 3GB
/home - 70GB
/mnt/download - 11GB
```

I don't know how much downloads you make. So you decide.

But you're thinking too much. Install it and start using it. :-)

---

### Post by JR Tyner on 2008-07-20
> **Vivaldi Gloria said:**
> How much do you need? You can make a partition of size say 10GBs to keep downloads. You can mount it in /mnt/download and put a symlink where ever you want.

How about this:

```
/ - 15GB
/var/mail - 1GB
swap - 3GB
/home - 70GB
/mnt/download - 11GB
```


Ok, I like that. This is what I'll do. 

```

/ - 15GB - XFS
/var/mail - 1GB - XFS
swap - 3GB - SWAP
/home - 70GB - EXT
/mnt/download - 11GB - XFS  

```

What if I had decided to dual boot? Out of curiousity, could I do this:

```

Windows - 35 GB
/ - 15GB - XFS
/var/mail - 1GB - XFS
swap - 3GB - SWAP
/home - 35GB - EXT
/mnt/download - 11GB - FAT32 or NTFS 

```

In case of a dual boot, I'd partition /mnt/download as NTFS so that Windows can add files to it for sharing. 

Will I have any problems editing fstab so /mnt/download has the noexec and nosuid options?

---

### Post by JR Tyner on 2008-07-20
[IMG]http://img.photobucket.com/albums/v617/bluefrogk0e/bumpjar.gif[/IMG]

---

### Post by Vivaldi Gloria on 2008-07-20
> **JR Tyner said:**
> In case of a dual boot, 

It's more easy to first install windows and then install ubuntu. Ubuntu recognizes windows and installs a boot loader that asks you which system you want to boot during boot.

On the other hand if you install first ubuntu and second windows then windows cannot put a bootloader which gives you options of booting windows or ubuntu. But it's not hard to fix it and there are a lot threads in this forum telling how.

So if you are sure that you'll install both then first install windows.

> **JR Tyner said:**
> I'd partition /mnt/download as NTFS so that Windows can add files to it for sharing. 

Windows can also read ext3 once you install this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

So both ext3 and NTFS are possible. I suggest you format according to which system you'll use more.


> **JR Tyner said:**
> Will I have any problems editing fstab so /mnt/download has the noexec and nosuid options?

If it's ext3 then you'll have no problems. I don't know enough about NTSF so I cannot comment on that.

---

### Post by JR Tyner on 2008-07-20
The install won't let me make the "/mnt/download" mount point, it only gives me /dos or /windows.

---

### Post by Vivaldi Gloria on 2008-07-21
> **JR Tyner said:**
> The install won't let me make the "/mnt/download" mount point, it only gives me /dos or /windows.

You know that partitioning deletes all the things, right? Just wanted to make sure you know. So backup your files.

Now start the ubuntu 8.04 live cd. Do not install anything yet. Just start ubuntu on the live cd. There is an application called partition editor (or gparted) in the menu

System > Admin. > Partition editor.

There is also another live cd which contains nothing but that program and it's available from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You download it, burn it, put it in and then boot up using it.

Or if you have the ubuntu 8.04 desktop cd then the partition editor is already there as I said above.

Start the partition editor. Choose the disk from the drop down menu on the top right if it's not already chosen.

Now it'll list all the partitions on that disk in the below list. If there are any partitions then right click on them and choose delete. Now when you are left with no partitions on that disk you can create your own partitions as you want.

The way you make new partitions is to right click the unused (unpartitioned) line and choose new. Then you'll enter the size and type info of your partition there.

At this point you do NOT tell the mountpoints. You just make partitions of this and that size. Mountpoints will be added when you install ubuntu. Now we are only dividing the disk into partitions of your choice.

Actually, why don't you tell me what partitioning scheme you've decided so that I can tell exactly what to do. I'm waiting for your answer. More importantly, do you already have Windows on that disk and do you want to keep it?

---

### Post by JR Tyner on 2008-07-21
> **Vivaldi Gloria said:**
> You know that partitioning deletes all the things, right? Just wanted to make sure you know. So backup your files.

Yeah. I learned that the hard way a long time ago...

> **Vivaldi Gloria said:**
> 
Actually, why don't you tell me what partitioning scheme you've decided so that I can tell exactly what to do. I'm waiting for your answer. More importantly, do you already have Windows on that disk and do you want to keep it? 

I was going to do Ubuntu only. But after my failed attempt last night, and not being able to get online with the LiveCD, I figured I should learn a little more before switching. I use to use a Knoppix Live CD and I had no problem connecting.

I knew before hand to back up, and I just reinstalled Windows and used the restore point I had saved to DVDs.

> **Vivaldi Gloria said:**
> 
The way you make new partitions is to right click the unused (unpartitioned) line and choose new. Then you'll enter the size and type info of your partition there. 

It limited me to only making 4 primary partitions.

> **Vivaldi Gloria said:**
> 
At this point you do NOT tell the mountpoints. You just make partitions of this and that size. Mountpoints will be added when you install ubuntu. Now we are only dividing the disk into partitions of your choice.


I guess something simular to this:

Windows - 35 GB - NTFS
/ - 15GB - EXT3
/var/mail - 1GB - XFS
swap - 3GB - SWAP
/home - 35GB - XFS
/mnt/download - 11GB - NTFS

I might enlarge the /mnt/download by shrinking the Windows partition, and use /mnt/download as my shared data partition.

Edit: I changed / to EXT3. I've heard that XFS is better for partitions on laptops that can loose power, but I have trouble installing if /boot is not EXT3. I could make a partition for /boot that is EXT3, but I'll await your thoughts on it.

---

### Post by Vivaldi Gloria on 2008-07-21
> **JR Tyner said:**
> It limited me to only making 4 primary partitions.

I guess something simular to this:

Windows - 35 GB - NTFS
/ - 15GB - EXT3
/var/mail - 1GB - XFS
swap - 3GB - SWAP
/home - 35GB - XFS
/mnt/download - 11GB - NTFS


Bios can detect only 4 primary partitions so you cannot make more than 4. But the OS can see as many as you want. So you make the forth an extended partition and put the remaining partitions in it as logical partitions. 

Something like this would work:

First - Primary Partition:
Windows - 35 GB - NTFS

Second - Primary Partition:
/ - 15GB - EXT3

Third - Primary Partition:
/mnt/download - 11GB - NTFS

Fourth - Extended Partition containing the logical partitions:
/var/mail - 1GB - XFS
swap - 3GB - SWAP
/home - 35GB - XFS

You arrange these with partition manager. Again, At this point you do NOT tell the mountpoints. You just make partitions of this and that size. Mountpoints will be added when you install ubuntu. Now we are only dividing the disk into partitions of your choice.

After you make these partitions you can install windows & ubuntu. When the partitioning option in ubuntu comes choose the guided option to give the mountpoints you want.

About different filesystems. I tried xfs once. But I didn't see any differences in daily usage. So I use only ext3 now. Ubuntu's bootloader GRUB works with them without any problems. So it's a matter of personal choice.

Are you sure that net connection fails with the live ubuntu cd? That's worrying.

---

### Post by JR Tyner on 2008-07-21
> **Vivaldi Gloria said:**
> Are you sure that net connection fails with the live ubuntu cd? That's worrying.

It won't pick up my wireless connection at all. I'm using a Dell Inspiron 1521 with a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card.

---

### Post by Vivaldi Gloria on 2008-07-21
> **JR Tyner said:**
> It won't pick up my wireless connection at all. I'm using a Dell Inspiron 1521 with a Dell Wireless 1505 Draft 802.11n WLAN Mini-Card.

If I were you I'd search these forums for your card. If nothing comes up then start a new thread in harwdare & laptop subforums about it. I have never used wireless so I cannot help you there.

---

