---
title: "Sharing confusion and how best to do it"
date: 2008-07-23
forum: General Help
---

### Post by NoOne2 on 2008-07-23
I'm getting a bit lost on how to setup this share for our house.

I originally was going this off of Win2K3 but was running into little problems here and there so I decided to try Ubuntu again since it seemed perfect for what we were doing.

I have 4 computers and a PS3.  One PC is mine, a laptop for my wife, a HTPC in the bedroom, the PS3 in the living room, and of course the server that Ubuntu is installed on.

The reason I went away from Win2K3 was a problem with having multiple users with the same name attached to the same share...there were ways around it but I figured this is a good chance to move into Linux.

I created a user called Common.  In Common I stored all of our media, vid, pic, and music.  I shared Common and sometimes this Vista error comes up that again too many users logging into the same share.

I mapped the My Pictures, My Video's, and My Music folders within Vista to the shares I created on the server.

I also mapped Documents for my wife's laptop and my computer to another folder I created.

What we want is all of our data going to the same place and sharing it between.  When she takes pics off her camera they go onto the server, same with me.  When she does iTunes, or I do, we want a common local.

That all works great....then last night I get the too many users error again.  ITs a Vista issue, not Ubuntu.

So today I had all this working, common iTunes library, everything.

Next step create multiple users and then give permissions to that folder.

I stored everything in 

/home/common/music
/home/common/video
/home/common/pictures
/home/common/documents

The user is common.  Today I created 3 more ID's

eric
tina
htpc

But all the data is under /home/common....can I share that with the other users the way I want to?

My better thought was to create a folder mapped to the partition with all the data but can't seem to do that either.

I have 3 partitions.  One 25 gig for apps/OS, one for swap, 4 gigs, and the rest of the 750 mapped to /home.

When I double click on Mediaserver, the name of the server in Network Places it asks me to login.  I type in common and the password and it lets me go right in.

When I try to login as tina, eric, or htpc it says that is cannot find the account even though I've tried MEDIASERVER\tina or any combo.

I'm applying too much Windows though to this.

Give the criteria of having all of our data in ONE place...everything we dump wants to go to the same place and pick it up from the same place, how would you do it?


Thanks

---

### Post by cariboo on 2008-07-23
what does your /etc/samba/smb.conf file look like.it should look something like this:

```
[music]
	comment = Audio Directory
	path = /home/storage/Mp3
	read only = No
	guest ok = Yes
	locking = No
```

With smb.conf setup like this I can access the files from any computer.

Jim

---

