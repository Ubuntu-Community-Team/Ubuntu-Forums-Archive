---
title: "SVN settings"
date: 2008-09-05
forum: General Help
---

### Post by doomstone on 2008-09-05
Hello out there.
I'm having some problems keeping my program source code and school worke files managed.
The reason for this is that i switch alot between computer, my home pc, laptop and school pc.
So i thought that using an svn server might would help me manage my program source code and my school papers. But the truth is that i don't realy know much about svn, and even less how to set it up.
So i where hoping the one of you guys might be able to point me in the right direction.

---

### Post by dmartin on 2008-09-05
My SVN setup is this.  First, you should have openssh-server and subversion 
```
sudo apt-get install subversion openssh-server
```

Then, I create a user and group svn, and place yourself in the group.  

```
sudo adduser svn
sudo addgroup svn
sudo adduser YOUR_USERNAME svn
```

By adding the user svn, you should have /home/svn now.  This is where I suggest placing your repositories.  The reason I like to place all my SVN repos in /home/svn is because when I do backups, I only back up /home /etc and /opt.  I keep all my "dynamic" content in one of those places.  The rest of my system doesn't really need to be backed up.

So, you might create a repo to hold your documents like so:
```
cd /home/svn
sudo svnadmin create documents
```

Unfortunately, root now owns that repo, and we don't want that, so:
```
sudo chown svn:svn /home/svn/documents -R
```

Now, since you already added yourself to the SVN group, you should have the rights to the repo.  Your repo URL is:
```
svn+ssh://yourserver.com/home/svn/documents/
```

Of course, ssh must be running before accessing it, so you may need to do this before accessing it the first time:
```
sudo /etc/init.d/ssh start
```

Hope that helps.

---

### Post by dmartin on 2008-09-05
I should add, I use a dynamic DNS through ZoneEdit so my server URL stays constant.  Otherwise you can use your IP address in the SVN url.

---

### Post by doomstone on 2008-09-06
Thanks for the help, it is working perfect :D

---

