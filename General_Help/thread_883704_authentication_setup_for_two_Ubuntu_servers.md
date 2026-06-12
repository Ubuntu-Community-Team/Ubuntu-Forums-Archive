---
title: "authentication setup for two Ubuntu servers"
date: 2008-08-08
forum: General Help
---

### Post by nehsa on 2008-08-08
Hello,

This is my first post (and I'm fairly new with linux).  I tried searching for this topic but was unable to find anything matching what I'm looking for.

As a hobby, I have setup two Ubuntu Servers.  

Both servers are running Samba and OpenVPN.  Later, I plan on adding MySql to one of them as well.  And a Shoutcast type application.

My first question is, what is the best way to handle authentication?  What I would like would be to setup 1 centralized place where both servers use for authenication (MySql maybe)?  For Linux/Samba/OpenVPN/Everything.

My problem is that I don't know where to start with an implementation like this.  Currently, my process is as followed to add a user to my VPN:

sudo adduser <name>
sudo passwd <change password>
sudo smbpasswd <name>
sudo smbpasswd -e
sudo chgrp <special group for VPN users> <name>
<remove users ability to SSH>

I then repeat this process on the 2nd server to try and keep everything in sync.  Even with this approach there are issues, a user will change their Linux password but OpenVPN will still require they're old password (which is shouldn't as it's using PAM authentication).  

I hope this post gets the gist of what I'm trying to do.

-Nehsa

---

### Post by nehsa on 2008-08-11
Hopefully, I don't get in trouble for bumping my own post by my intention is to provide more information.

What I'm after is a way to simply adding users.  What I would like to do is be able to do the following in 1 place (preferrably a SQL statement in MySQL):

1) Determine which groups a user has access to.  These groups will be for Samba so that I can cater Samba shares to my audience.

2) Determine whether the user is able to SSH into the system or only connect via VPN. (Like 0 = SSH, 1 = VPN, 2 = Both)

3) Lock down the file system so non-sudo users cannot get to places like /etc.

I've research MySQL and the results didn't look promising and I've researched LDAP and it looks extremely convuluted.  Do most users develop their own scripts for accomplishing tasks like this?

I only have 2 Ubuntu servers (may add 1 more) and 1 Kubuntu desktop.  There has to be a better way to manage users than how I currently am doing it (repeating the add steps for each machine, having the user login through SSH to change their password then locking them out when they're finished.

I don't expect step-by-step guidance in this but more of a push in the right direction.  Examples of ways other Ubuntu users manage multiple systems would be great.

-Nehsa

---

### Post by nehsa on 2008-08-28
I still haven't received any responses to this thread.  I'm thinking this either means a) what I'm doing is stupid or b) no one has any knowledege to assist me.

In a nutshell, what I'd like is to combine ALL servers on my Ubuntu server machine into a MySQL database.  Note, they do not need to be in the same database but all in MySQL.  This is so that I can build interaces to extract data over various parts of my server from 1 central location and also to simplfy user create.

This includes:
  Shell access
  SSH access
  VPN access
  Mumble access
  Group access
  Sudo access

I'm curious if anyone has attempted anything like this.  I am new to Linux and understand that most of this will require custom scripting on my part and I have no problems trying to use Python/Perl (not sure which would be best suited) to create a script to populate these databases.

For example:

The script would look a lot like the useradd script but would include additional sections:

SSH Access?
VPN Access?
Mumble Access?
Which groups? <space dilimited>  Samba would then be configured using only groups for shares so I could easily indicate which shares are available during user creating.

I've scoured the Internet and the only thing I can find is how to connect OpenVPN and Samba to MySQL.  Mumble eludes to being able to switch from SQLite to MySQL but I cannot find directions anywhere.

I'm mainly looking for advice here.  

Which packages would you need to do this?  

What scripting language would you use for creating the user creation script?  

Has anyone taught the initial login (shell?), SSH, sudo, or Mumble to utilize a MySQL?

After I get this initial functionality working it would be a snap to continue to add functionality and improve user management in Linux (for me anyways).

Are there any "Gotchas" to this idea that I haven't seen?

Thanks for any guidance you can provide!

Nehsa

---

### Post by nehsa on 2008-09-01
I'm hoping to dumb this down so that it's manageable for 1 person to respond to.

I've been researching different technologies for integrating all aspects of Linux into a central repository.  Does anyone have any idea on this?

LDAP?

MySQL/PostgreSQL?

Radius?

What I want is really pretty simple.  One place that I add a new user to the system.  I want a user to login to the system and whatever technology authenticated him determine what services he has access to.  (Radius/LDAP?)

OR 

If a technology like this doesn't exist, then I would like to manually teach each service to refer to a SQL database when a user logs in (much more work probably).

The services I would like integrated are:

Direct shell access (Believe is using PAM now?)
SSH access
OpenVPN access
Samba Access
Docuwiki access
Mumble/Murmur access
Hula (maybe)

Thanks for any feedback on this topic!  I would also like to hear if there's a legitimate reason why Ubuntu is not already setup like this.  Are there downsides I am not considering?

-Nehsa

---

### Post by cariboo on 2008-09-01
Yu might be better off asking this question in the server forums, the link is under Main Support Catagories on the far right. There are really smart people on that forum that never check any of the other forums.

Jim

---

