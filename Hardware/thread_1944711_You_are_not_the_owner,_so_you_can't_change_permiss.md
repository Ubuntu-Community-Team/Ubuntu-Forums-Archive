---
title: "You are not the owner, so you can't change permissions"
date: 2012-03-21
forum: Hardware
---

### Post by Photobuddha on 2012-03-21
"You are not the owner, so you can't change permissions". &#8211; ubuntu 11.10 
 First off I am not an idiot and I have been trying to search throughout the forum for 2 days to find my answer and ether post is too old or to vague and assume you know more than you do. If ubuntu ever wants to actually be a viable replacement for windows it has to stop acting like it's so important. I am only running it on my desktop pc. If I wanted server software/security I would download server software. If I screw something up on my PC I am the only one that's affected. 
How could it be so difficult to add additional storage?
 
Now that I pissed off all the ubuntu rules no matter what people, here is my problem;
 
I need to set permission on ubuntu 11.10 64 bit, so I can copy or even use my additional raid storage. I just need to know how to do this. There should be a simple command, it should be like a switch&#8230;I'm betting it&#8217;s not. Thanks in advance if you know how to fix my issue. 
 
The partition is created and mounted I just can&#8217;t use it. 
 
I love the help button that says set file permissions and then tells me I don&#8217;t have permission to do just what it told me would fix the problem.

---

### Post by Iowan on 2012-03-21
**sudo** might be able to help with the permissions problems.

---

### Post by Bucky Ball on 2012-03-21
> **iowan said:**
> **sudo** might be able to help with the permissions problems.

+1.

---

### Post by MasterGamerJK on 2012-03-21
"sudo -i"  should work too, be sure to "su your_user_name" when your done :P

---

### Post by critin on 2012-03-21
> **Photobuddha said:**
> "You are not the owner, so you can't change permissions". &#8211; ubuntu 11.10 
 First off I am not an idiot and I have been trying to search throughout the forum for 2 days to find my answer and ether post is too old or to vague and assume you know more than you do. If ubuntu ever wants to actually be a viable replacement for windows it has to stop acting like it's so important. I am only running it on my desktop pc. If I wanted server software/security I would download server software. If I screw something up on my PC I am the only one that's affected. 
How could it be so difficult to add additional storage?
 
Now that I pissed off all the ubuntu rules no matter what people, here is my problem;
 
I need to set permission on ubuntu 11.10 64 bit, so I can copy or even use my additional raid storage. I just need to know how to do this. There should be a simple command, it should be like a switch&#8230;I'm betting it&#8217;s not. Thanks in advance if you know how to fix my issue. 
 
The partition is created and mounted I just can&#8217;t use it. 
 
I love the help button that says set file permissions and then tells me I don&#8217;t have permission to do just what it told me would fix the problem.

To share over the network you'll  need something like Samba.  (I use Samba, others use something else)  Go to the file/folder you need share, right click and click Properties.  At the bottom of list.  It will open so you give permissions read/write, etc.  I allow others without acct to open mine and it adds a share app if you tell it to.  If I remember right, this share app is Samba.

Files/folders in other disks/partitions will have to be set to share too, of course.


There's a lot more to it, but this will give you the idea.

---

