---
title: "[SOLVED] Best way to send large files over the internet?"
date: 2008-11-20
forum: General Help
---

### Post by nickpick on 2008-11-20
Hi!

My friend and I are working on a project that requires us to send each other pretty large .wav files. We're talking about 200~500mb range here, i.e. email's completely out of question and, no, converting it to .mp3s is not an option for us either. I'm looking for a way to easily send these files back and forth. What I'd like would be (in order of priority):

- Ability to restore upload/download if the connection breaks down
- Encrypted transfer
- Easy config and use
- Ability to share folders on each other's PCs for easy grabbing

I know there are torrents for this sort of thing, but a somewhat less tedious alternative would also be very welcome.

Any ideas would be greatly welcome!

---

### Post by tvtech on 2008-11-20
SET UP AN SSH SERVER it's encrypted by default, you can authenticate to eachothers computers and set user permissions to specific directories for each user you plan to let log in.

---

### Post by wersdaluv on 2008-11-20
yousendit.com?

Dropbox?

---

### Post by tvtech on 2008-11-20
also you can mount the ssh servers/shares as a local file system on your computer and treat it as such as long as your friends have given the proper permissions to you on the linked folder.  

i.e. I have a an ssh server that I log into it is sftp://username@xyz.com/filefolder.   

my buddies and I share HUGE volumes of DATA this way.

---

### Post by sauce345 on 2008-11-20
Most definetly set up ssh, it is by far the best, most secure, and easiest.

sudo apt-get install openssh-server

add a user for your friend or let him use yours if your trust him(this would be very risky)

---

### Post by tvtech on 2008-11-20
no third party, it's super easy to do and easier to maintain,  if your worried about ip address changes on dynamic ip hosts just use a service like dyndns  or the like. that way if one changes and you can't access the server you'll know and you and all your buddies can have access to that account. very easy, very simple ssh is the way to go for this seriously

---

### Post by nickpick on 2008-11-20
> **tvtech said:**
> no third party, it's super easy to do and easier to maintain,  if your worried about ip address changes on dynamic ip hosts just use a service like dyndns  or the like. that way if one changes and you can't access the server you'll know and you and all your buddies can have access to that account. very easy, very simple ssh is the way to go for this seriously

SSH sounds great!

I know that this will disqualify me from the ranks of cool guys for the next couple of years, but are there any GUI tools that help you setting up and maintaining the server? I'm really no fan of the commandline.

---

### Post by lifestream on 2008-11-20
Can you resume file transfers, with SSH, if it is interrupted?
Do you need a specific ssh client to do it? 

Thanks in advance.

---

### Post by nickpick on 2008-11-20
> **lifestream said:**
> Can you resume file transfers, with SSH, if it is interrupted?
Do you need a specific ssh client to do it? 

Thanks in advance.

Alright, setting it up really was a pretty easy.

Now about file transfers. Which client would support resuming?

---

### Post by Kain000 on 2008-11-21
How about SFTP?    from what I can see here everyone prefers SSH but  isnt SFTP using ssh?      is it a faster transfer?


why SSH is my question.

---

### Post by rubberglove on 2008-11-21
> **nickpick said:**
> Alright, setting it up really was a pretty easy.

Now about file transfers. Which client would support resuming?

I don't think SSH (SCP or SFTP, which are the file transfer tools for SSH) has any built-in resume features, but you can do it with rsync (over SSH): [http://joen.dk/wordpress/?p=34]("http://joen.dk/wordpress/?p=34"). That blog post has come in handy quite a few times...

Also, I don't know about GUI SCP/SFTP clients (I spend half my computer time on the command-line), but you can use SSHFS to mount the remote folder like a drive, so you'll be able to browse to it in nautilus (or whatnot). 
[http://en.wikipedia.org/wiki/SSHFS]("http://en.wikipedia.org/wiki/SSHFS")

Finally, if you're using SSH, make your life more convenient (and also secure) by setting up public-key encryption! This way you won't need to type in your passwords every time you login. The ssh-keygen comand will generate your public/private keypair for you (you might have one already) and ssh-copy-id is a handy command to put your public key in the right location on the remote computer.

---

### Post by rubberglove on 2008-11-21
> **Kain000 said:**
> How about SFTP?    from what I can see here everyone prefers SSH but  isnt SFTP using ssh?      is it a faster transfer?


why SSH is my question.

As an over-simplification, when people are talking about using SSH for file transfer they are talking about SFTP (or SCP), as SSH doesn't transfer files otherwise.  
SFTP is like FTP+SSH and SCP is like CP+SSH.

---

### Post by ju2wheels on 2008-11-21
You can use Filezilla as a GUI for downloading over sftp. It will ask you if you want to resume or start a download over as long as you download it to the same location when resuming and dont delete the partially downloaded file.

---

### Post by beercz on 2008-11-22
How about using rsync?

rsync works over secure connections using ssh protocol, and only copies new and modified files once the first transfer is complete.

Therefore the transfere continues where it left off should the connection be lost.

rsync is in the repos.

When installed look at it's man page:
> 
man rsyncUse it all the time - wonderful tool for backup/syncing/copying files over networks (including the internet)

---

### Post by Kain000 on 2008-11-22
> **rubberglove said:**
> As an over-simplification, when people are talking about using SSH for file transfer they are talking about SFTP (or SCP), as SSH doesn't transfer files otherwise.  
SFTP is like FTP+SSH and SCP is like CP+SSH.

thankyou for the clairfcation

---

### Post by nickpick on 2008-11-29
Working perfectly with public keys. Thanks everybody!

---

### Post by modmadmike on 2008-12-18
I use NFS server and a NFS client ([sudo apt-get nfs-common] then [mount <IP/HOSTNAME>/<FOLDER> <MOUNT FOLDER>]).
i have gotten up to 25mps with a HDD that won't go above that speed.

---

### Post by Tim Parker on 2009-10-26
Hi Nickpick,

A web browser based solution is going to be the easiest one, because you won't have to setup any software.  Obviously security is important.  Some of the web based services offer some encryption while files are transferred, but then their own staff can still open your files.  I used [www.sendtoperson.com]("http://www.sendtoperson.com") because they actually use the optional extra file password to custom encrypt your file.  I called the other companies mentioned on this thread and asked if they do that and they said they don't.  Since I am sending my customer data around, I need this feature or I'm putting my clients at risk; you should consider that also.  FTP can do the trick but has no security and it's a pain in the neck to administer... for example you have to keep going back and cleaning up unused files to free space back up.

Tim

> **nickpick said:**
> Hi!

My friend and I are working on a project that requires us to send each other pretty large .wav files. We're talking about 200~500mb range here, i.e. email's completely out of question and, no, converting it to .mp3s is not an option for us either. I'm looking for a way to easily send these files back and forth. What I'd like would be (in order of priority):

- Ability to restore upload/download if the connection breaks down
- Encrypted transfer
- Easy config and use
- Ability to share folders on each other's PCs for easy grabbing

I know there are torrents for this sort of thing, but a somewhat less tedious alternative would also be very welcome.

Any ideas would be greatly welcome!

---

### Post by The Cog on 2009-10-26
Tim,

I don't know how you found that thread, but until you posted to it, it had been dead for 11 months. It is probably worth checking the age of any threads you find that way before replying to them.

Oh, and rsync has a gui called grsync apparently, and I think rsync can do something a bit like a resume in that it checksums segments of a large file and only transfers the differing segments.

---

