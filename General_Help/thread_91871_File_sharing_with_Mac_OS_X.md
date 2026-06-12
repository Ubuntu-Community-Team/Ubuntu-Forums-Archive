---
title: "File sharing with Mac OS X"
date: 2005-11-18
forum: General Help
---

### Post by patonw on 2005-11-18
Hi,

I've installed Ubuntu on an old x86 (which previously had windows then mandriva then debian). I'm having a problem with connecting to smbd from a powerbook running 10.4 to the Ubuntu machine. 

On the powerbook i'm using "Connect to Folder..." from Finder. On the Ubuntu side it shows that a connection is established from the Powerbook, however the PB shows the "Connecting to ...." status dialog indefinitely (well at least until cancelled).


/var/log/samba/log.powerbook shows
> [2005/11/18 03:04:18, 0] rpc_server/srv_pipe.c:api_pipe_bind_req(919) api_pipe_bind_req: unable to unmarshall RPC_HDR_RB struct.
a few times. Connection from a windows machine works fine. 

Now I've had this problem in Debian too, but not from Mandriva, which is understandable considering Ubuntu's heritage. I could mount my home directory via samba without any hiccups when running Mandriva on the server.

What is the difference between mandriva's samba package and ubuntu's? I remember that there were some issues with Tiger's smb functionality when it was first rolling out. Where those ever fixed? Could they be causing this current problem.

I've considered alternative protocols but samba makes the most sense given my needs (if it played well with my Mac). Is there a newer version of smbd available that bypasses this problem or some way to fix the client on my powerbook?

Thanks,
patonw

---

### Post by patonw on 2005-11-18
Well I bit the bullet and configured NFS which was a royal pain but it's working unlike SMB.

Any ideas would still be appreciated.

---

### Post by megamania on 2005-11-18
[QUOTE=patonw]Well I bit the bullet and configured NFS which was a royal pain but it's working unlike SMB.
[/QUOTE]

I have the same problem (connecting a Mac OS X machine to an Ubuntu machine.

Can you tell me how you configured NFS on both sides? That would definitely help me.

---

### Post by patonw on 2005-11-19
[QUOTE=megamania]I have the same problem (connecting a Mac OS X machine to an Ubuntu machine.

Can you tell me how you configured NFS on both sides? That would definitely help me.[/QUOTE]

The only complication I had was that file permissions over NFS use your user and group id instead of authentication information. You'll have to synchronize your user:uid and group:gid on both sides for every single user for every machine you want to connect to NFS. I think NIS would help there on a larger network but for a few computers the problem can be managed manually.

Most distros i've seen give uids and gids starting at 501, which is what my mac does, but Ubuntu starts at 1000, which caused me not to be able to write from the Mac.

Anyhow, what I did was 
1) give root a password via sudo
2) logout of my account then log in as root
3) change the uid in /etc/passwd and gid in /etc/group to the values on your mac
4) chown -R username.group /home/username to update your home directory
5) do the same for any directories and files that you own

That was the annoying part. Setting up a share is much easier.

On the linux side I added the share information to /etc/exports and restarted nfsd. On the Mac side I just used "Connect to Server..." from Finder.

Not sure how your computers are set up but generally you'll want 
> 
/path/to/share          host(options)


If your laptop has a static ip in the network then just use that, or better yet if there's a local dns server, use the hostname. If you want to export to a subnet you can use x.x.x.x/255.255.255.0.

Options I used were rw,root_squash,insecure.

Think i'm gonna work on getting my router to work as a dns next. What I really want is SMB to just work! :rolleyes: 

Good luck,
patonw

---

### Post by megamania on 2005-11-20
thanks a lot, patonw! that's useful information!

---

### Post by arphe_el on 2005-11-22
is there a step by step guidelines for making nfs to work? our set-up is a peer to peer sharing local files all of it are ubuntu linux 4 computers.

i already try to run the portmap, rpc.statd, rpc.lockd to run and already configured the etc/exports, allow.host, and deny.host

there's an instruction that found in [http://nfs.sourceforge.net/nfs-howto/client](http://nfs.sourceforge.net/nfs-howto/client) on how to mount but a bit confuse about the server name since our set up is peer to peer.

any suggestions?

---

### Post by Sonicred on 2005-11-27
I just discovered a workaround for this bug on a mailing list through a Google search. Adding the username and the path gets the authentication box to come up correctly.

So instead of:
smb://192.168.1.101
It's:
smb://username@192.168.1.101/public/

I'm currently connected to my Ubuntu Samba share through OS X 10.4.3!

---

### Post by arphe_el on 2005-11-27
Dear Sonicred,

Is it applicable to linux to linux ubuntu computers?

I already try it but still no fortune in my case I have my folder in desktop and i'm using root 

so i type to the file browser the ff:

smb://root@192.168.1.101/root/Desktop/rowel/

still hoping to make this things right through this forums. Thank you and GODspeed!

Best regards

---

### Post by rob_gendreau@yahoo.com on 2005-12-03
I'm having the same problem. I keep getting an error message that the password login is wrong.

Rob

---

