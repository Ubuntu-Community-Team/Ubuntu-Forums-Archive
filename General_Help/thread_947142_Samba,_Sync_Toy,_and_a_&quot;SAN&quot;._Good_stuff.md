---
title: "Samba, Sync Toy, and a &quot;SAN&quot;. Good stuff."
date: 2008-10-14
forum: General Help
---

### Post by Roasted on 2008-10-14
I just figured I'd stir up conversation here. Has anybody ever used Sync Toy in conjunction with Samba? 

I really must admit, this makes a unique combination in terms of XP/Ubuntu networking backups.

Let me explain my situation a little bit...

I run Ubuntu exclusively, with the exception of me gaming in XP Pro. After a series of blue screens and whatnot with my brothers computer, causing him to lose his stuff, I decided to research some networking information with Samba. So, I set up Samba. I also have a 250gb SATA drive in my computer I use exclusively for Samba.

On this hard drive, I have 3 folders. Pam, Curt, Tyler. My mother and brothers. They all run XP Pro on their computers.

I configured my smb.conf file for Samba to make it so only Pam can get into Pam's folder, and Curt into Curt's folder, and Tyler into Tyler's folder. That way it's just a 1 to 1 backup and nobody can snoop around in each other's documents. 

I set up a static IP on my Ubuntu machine. Then, on the XP Pro computers, I mapped a network drive for my IP + their share.

Example:
\\192.168.1.111\pam

Then, that mapped network drive is routed out to my Ubuntu computer. That way, they can back up their stuff there. Thing is, until now they've just simply copied/pasted whatever they wanted to back up.

After learning about Sync Toy, I tried a little experiment. Sync Toy is free and available on download.com, btw. I set up their entire My Documents folder to get synchronized to their share, which is mapped to the Z drive.

It works like a charm. Now, since it's set up, the users simply have to click "run" and BAM... everything from their my documents folder gets synchronized. That include their my music and my pictures folders.

I just wanted to share my ideas... maybe somebody reading this is like, man, I really need a good backup solution to a spare computer I have laying around...

Well, try this! Samba, Sync Toy... good stuff! 

Note - I also have a 2nd 250gb HDD that I use in conjunction with the 250gb Samba hard drive. What I do is I rsync the 1st drive to the 2nd drive. Therefore, that leaves my local computer with 2 copies of everybody's "My Documents" folder from their computer. So the only way we're going to lose data is if both of my 250gb drives go down + their computer goes down at the same time. Ahhh... redundancy at its best.

:guitar:

---

### Post by BCboy on 2010-01-05
I was thinking about using Unison but this looks interesting. Thanks for the post.

---

### Post by Roasted on 2010-01-06
Not sure if you'll see this but I figured it's worth noting. I no longer use SyncToy. Instead I use SyncBack SE Free Edition. It has a scheduler built in, which is why I like it.

I set everybody's backups to be 10 minutes apart (even though synchronizing only takes a minute or two unless they have a couple gig of new stuff). At 3 am is when the backups start - however I'll probably be changing that since we're turning computers off at night to save power, and since we have 5 desktops that normally run 247 it may help us out. I'm considering on trying to figure out if I can set SyncBack to re-probe the connection every hour, and if the connection is available (server turned on) then it syncs.

But anyway, it's a good setup to have. So far my one brother's computer crashed twice, another brother crashed once, and my mom accidentally deleted something one time she didn't mean to (emptied recycle bin too) but I had the backup of it.

It's very handy. Highly recommended. Even when I move out of here, I'm leaving a linux box behind to run samba on a lower powered machine to be on 247 since my main desktop (server) would come with me.

---

### Post by gtr32 on 2010-01-06
> **BCboy said:**
> I was thinking about using Unison but this looks interesting. Thanks for the post.

If you only want to do backups, I would suggest running rsync. Then a simple script on the server side that creates hardlinks in case you want snapshot style backups. I you want bidirectional sync then Unison.

---

