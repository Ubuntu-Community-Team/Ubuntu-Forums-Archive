---
title: "[SOLVED] Ubuntu File Server / Access Rights"
date: 2008-08-06
forum: General Help
---

### Post by toolzen on 2008-08-06
Ok, this is a long one. I have a new project at work - my bosses (I have four... whoopie!!) want me to build a new file server, or set up our existing one to operate in a way that enforces compliance for certain rules we have regarding file organization. Here is our current set up:

We have an all-windows network (yuck!), our file server has windows 2003 OS. All of our client xp pro computers connect to a "G Drive" on this server (meaning on each computer there is a mapped network drive set up on g:\).

On the shared drive we store all of the document we do here (we're a law firm) and the way they are supposed to be organized is as follows:

G:--
----|
----Folder Called:"Client A"
--------Subfolder Called: Albertson, John  ##This is the client
-----------Subfolder Called: Albertson Power of Attorney  ##This is a matter for that client
------------------Document 1   ##This is a document for that matter for that client
------------------Document 2
------------------Document 3
-----------Subfolder Called: Alberstons v. Smith
------------------Document 1
------------------Document 2
etc.

But, some of our employees are not getting the whole hierarchy thing, so they just save files to the client folder rather than the specific matter folder, like so:

G:
-----Folder Called "Client B"
---------Subfolder called "Bears, John"
-------------Will Document 1
-------------Will Document 2
-------------Bears v. Smith document 1
-------------Bears v. Smith document 2
-------------Subfolder called "Will"
-----------------Will Document 3
-------------Subfolder called "Bears v. Smith"
-----------------Bears v. Smith Document 3

Basically, depending on what legal assistant is saving the file, they will save it on a different level of the hierarchy, which drives me mad.

What I would like to do is set up an Ubuntu file server, have a windows-accessible share (samba? nds?) that will allow people to save files within "subfolder called Bears v. Smith" but not allow them to save files in "subfolder called Bears, John." This is because the documents we make are matter-specific rather than client-specific (one client may have many matters that we are working on for them).

I was thinking of making an admin group on Ubuntu (me and select others) and a secretary group. People in the admin group could make the folders necessary when we get a new matter for a particular client, but people in the secretary group could not.

Even better, I would like to make it were the secretaries themselves ~can~ make new ~folders~, but not new ~files~, in certain directories. That would save me from making a new folder every time we get a new matter from a client.

Even double better, I would like to simply mount our existing file server's shared drive across the network and let the Ubuntu server simply handle the permissions and make it a samba/nds share for the windows xp users.

I think I know how I could do this, but would love some feedback on how others might set that up.

I suppose some things that I'm worried about (as I have never done this before) are:

* I don't want there to be any issues with files saving in the wrong format - I have no idea why they would, but paranoia is needed when you're talking about legal documents and the fact we bill 200 an hour (so an hour of lost work costs us).

* I don't want any issues with people not being able to save their work at all

* I don't want our data corrupted in any way

* I don't want any significant network slow-down

given those concerns, what would you do, and how would you do it? I'm thinking the way to go would be mounting the drive over the network, and sharing the mount point. The mount point could have username/password access and depending on how you logged on from your windows client you would have different access rights.

Feedback?

---

### Post by ilrudie on 2008-08-06
This is a complicated question to answer and if you have to ask it its probably something you should hire someone to setup and manage but heres my first pass:

The best way to manage the folders/files would be:
1) Install a base Linux system in on a relatively small drive. 32gb scsi would be plenty. Ubuntu is fine but for reliability I would recommend looking into Debian (Ubuntu's parent distro), Redhat or CentOS (free Redhat).
2) Install SAMBA
3) Add a mirrored pair of larger drives for you samba share mounted on say /samba
4) chown root:root /samba
5) chmod 771 /samba
6)  create a group for all the secretaries, call it what you want in the example i'll call it sec
7) create any subdirectories and chown/chmod as follows

    if you want secretaries to be able to read but not write
    chown root:sec <folder>
    chmod 750 <folder>

    if you want secretaries to be able to read and write
    chown root:sec <folder>
    chmod 770 <folder>

Some problems with this (I'm sure there are plenty I have missed): 
I'm not sure of an easy way to allow users to make folders and not files in a directory without them logging onto a system.  If they can ssh into the system which is probably a lot for a windows user to be expected to do you could setup sudo to allow them to use only the mkdir command.  If you wanted to do this perhaps the best way to chown the folders would be more like chown secu:secg folder.  In this case secu will be a user with login disabled so the only way to "be" the user is with sudo.  This way you can set them up to be able to run mkdir as secu but there normal access would be through secg.  aka when using sudo they have 7 (rwx) but when connected through samba they have 5 (r-x).  This of course is mostly irrelevant because they wont want to learn or ssh into the box when its sooo much easier to just complain to you.  You could also make a website where they could go to create new clients/matters which would be more "user friendly" than ssh but that's a whole other thing.

Mounting the existing file server is not a good idea because ntfs has different permissions than ext3 and ntfs is not Linux native.  You could of course just change the permissions on the existing file server to be similar. 

Managing users will be a pain with this system and integrating anything non-M$ with AD is also a pain so pick your poison there.

You can also look into a company called Interwoven which specializes in doing exactly what you are trying to do: enforcing strict auditable version controlled file permissions on windows network shares.  Hate to mention proprietary software on a Linux forum (which I believe is the 8th mortal sin) but I have not seen a FOSS product like what Interwoven offers.  I'm sure there is one out there so someone help me out here and let us know what it is.

Hope that gets you started.

---

### Post by toolzen on 2008-08-21
I did this, and it was actually a lot easier than I was thinking it was going to be. Here is what I did.

Step 1 - Mount the NTFS drive over the network:

mount -t cifs -o usersname=username@dowmain.local //195.168.254.x/share  /mnt/share

* plan on setting this up in fstab of course, but got it working and wanted to post while I'm still excited.*

Step 2 - Create groups

Group "allaccess" contains those people who should have unrestricted access to all files

Group "restricted" contains all users

Step 3 - Modify folder/file Permission:

chmod -R ug+rwx,o-w /mnt/share

Step 4 - change group ownership

For restricted folders:

chown -R root:allaccess <foldername>

For unrestrcted folders:

chown -R root:restricted <foldername>

Now, people can be in one level of the hierarchy and not be able to save files or create folders, but ~I~ can create the subfolder for them, change the group ownership of that folder, and then they can save in there - where they're supposed to, even though higher up on the hierarchy they cannot.

Samba setup is pretty straightforward, so I won't go into that to much, but basically the samba setup is just guest ok = no and I have added samba users that match up with system users and the samba share is read/write, but the actual Linux system permissions is what controls the access, not samba.

Anyone foresee any problems with this?

Also - are the file permissions for the folders and files stored as some sort of meta-data in the file itself, or is it stored somewhere on the linux machine? i.e. does changing the file permission of a file actually modify that file in doing so, or does it modify something in the linux kernel/system/etc?

I would think think it is the latter - when I access the folder by going though network neighborhood, I can do whatever I want regardless of who I am signed in as, but when I map a drive to the samba share on the linux machine then the restrictions work as intended.

---

