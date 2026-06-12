---
title: "Does this guy have any idea what he's talking about?"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by jamieh on 2009-03-31
Okay, I'm running a school's computer lab which consists of about 12 Ubuntu PCs and an Ubuntu server. The server is used to host files via SFTP (Nautilus) for the workstations. The students are told to save their work on their account's SFTP share (its a small school consisting of ~20 kids, each 11 or 12 years old). Everything works fine and dandy. (The ssh is LAN-only)

The admin of the school hires a second computer guy just for "another opinion" on the setup. (It used to be WinME till last week). He looks all pissed and says that I shouldn't be using SFTP because it is insecure and Sambo is better. Sure, whatever. Shouldn't be that hard to change it.

Later that evening, I do a google search for Sambo, and I couldn't find ANYTHING related to linux. Is this guy just making up words? He seemed to know what he was talking about - apparently he admins a 60-computer network and everything is shared by Sambo on BSD Linux.

I don't consider myself a "noob", but I'm not a genius either.

I guess my question is what is the best way to share files between multiple computers. Sambo (?) or SSH?

Thanks

---

### Post by Meson on 2009-03-31
I think you mean Samba, not Sambo.

Samba is convenient for having linux file servers that windows computers can access.  I'm not security expert, but I'd say SFTP is more secure than Samba because SSH is a wonderful tool and extremely secure if used properly.

NFS can also be quite secure if used properly.

But in the end, it all depends on what you mean by security.  Are you talking about authentication or authorization - there is a difference, you might want to look those up and come back.

---

### Post by bgerlich on 2009-03-31
1. Sambo is a racial slur.

2. He meant SAMBA.

3. Walk away, the guy doesn't know what he is talking about. Samba puts less strain on the network but is way (way with 26 "a"s) less secure. There is no such thing as BSD Linux - it is almost an oxymoron.

**EDIT:**
Damn insomnia, come to think of it are you sure you remembered all the terms right?

---

### Post by Cybie257 on 2009-03-31
In my opinion, Samba (not Sambo), would be easier to share files among computers. As for security, it all depends on what type of security. SSH is for encryption, usually used on the Internet, but for a classroom setting and small network, not necessary. 

SFTP probably is overkill, but again, not sure what your exact security requirements are. If it's file permissions so that others can't delete or change data, then Samba would provide what you need for easy file sharing and being able to set such permissions. 

-Cybie

---

### Post by lykwydchykyn on 2009-03-31
I would suggest sitting down with this guy and picking his brain; could be a good learning opportunity. I wouldn't just accept someone telling me "X is less secure than Y, you need to switch it all over to Y".  Ask him why he thinks this, and what security threats he envisions you are at risk for.  And check out what he says to make sure he has his head on straight.

Like meson said, there are different aspects to security.  SFTP is encrypted traffic, but by default things aren't chrooted and your users have shell access to the server (I believe both of these can be locked down).  So from the standpoint of someone sniffing packets and finding user's passwords or what have you, you're secure; but as far as users poking around where they have no business, that might be an issue.

SAMBA is pretty deep as far as being able to specify what users can and cannot do/see/change.  It can also be needlessly complex in many situations (especially where you don't need Windows compatibility).

---

### Post by Meson on 2009-03-31
Let me ask an important question to elaborate on what I was saying above:

By security, do you mean you don't want students interfering with other students' files, and teachers' files, etc?

---

### Post by jamieh on 2009-04-01
I remember the terms right. After a bit of research, "BSD Linux" makes no sense, and he definitely was saying "Sambo".

I'll have a look at Samb**a** and consider switching.

It's just a small school, the student account on each computer has an SFTP bookmark for "/school/students", and the staff account has a bookmark for "/school/staff". Each account has a password. Permissions are set so the student account cannot open the staff folder one level up.

I guess by security, he means remote hackers. Since the entire thing is LAN-only it seems like a nonissue.

I'll see how it goes when he comes next.

---

### Post by Meson on 2009-04-01
You mean all of your students share an account?  That's probably your biggest problem right there.  Samba is not only overkill but if all of your computers are Linux, it's not really necessary.

The fact that Nautilus can browse SFTP automatically makes it a perfectly viable solution for you.  I'd look into having a separate account for each student though, and a separate directory on the file server with separate permissions.  (And of course you can have public folders, or a public teachers-only folder, etc.)

In the end, whatever is easiest to administer from year-to-year and expands well with increasing school size is the BEST solution.

---

### Post by bgerlich on 2009-04-01
> **jamieh said:**
> 
I guess by security, he means remote hackers. Since the entire thing is LAN-only it seems like a nonissue.

If the guy uses terms like "Bsd Linux" and "Sambo" there is no point in talking with him.

As lykwydchykyn has mentioned, you should think about chrooting users and maybe create separate accounts for every user, but besides that (because of the internal network, separated phisically form the internet) - use whatever works the best for you and the users.

---

### Post by LxQual on 2009-04-01
Sambo is also martial art developed in USSR (Russia) ;)

---

