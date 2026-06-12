---
title: "git http methods not using netrc after upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by crustymonkey on 2009-11-02
I just upgraded my workstation to Kubuntu 9.10 last week and I've noticed something odd when I use git (version control system) now.  I'm accessing a couple of webdav repositories and have a .netrc file set up to handle the authentication.  Ever since the 9.10 upgrade which, I think, upgraded git from 1.5.x to 1.6.3, I get prompted for my password as if git is ignoring my netrc file.

Has anyone else run into this?  Is there a fix/workaround?  Google has led me pretty much nowhere on this one.  It's not the end of the world, but it gets a little annoying when I'm pushing to multiple repos.

Thanks,

Jay

---

### Post by crustymonkey on 2009-11-03
I figured out what the problem was.  The remote "url" spec in .git/config was of the form "https://username@example.host.com/repo.git".  Apparently, having the "username@" for the host causes git to skip the .netrc file check.

---

### Post by J. Adam Moore on 2009-11-05
I'm having this problem, but I don't see how it's [SOLVED]. I'm trying to set up a git repo and it keeps asking for my password no matter what I do. I have installed a fresh system just to set this up, followed every tutorial online precisely, and it still does not work. This is the only post regarding Karmic and ssh asking for password when it shouldn't.

---

### Post by crustymonkey on 2009-11-05
> **J. Adam Moore said:**
> This is the only post regarding Karmic and ssh asking for password when it shouldn't.
I'm not sure if you really noticed it, but my problem was with access via WEBDAV, not ssh.  Although you wouldn't necessarily think so, it's actually a very apples and oranges type of difference between access via the 2 different protocols.

However, I can probably still tell you what you need to do to fix your problem if you are using ssh as your access method.  The first thing you need to do is generate an ssh keypair on the client machine (if you don't know how to do this, or what I'm even talking about, do say so).  Verify that you can log into the remote machine via ssh without a password prompt.  Note that you will have probably have to log into the remote machine once before using git so you can accept the remote server's public key into your known hosts.  After you can log in without a pass prompt, you should be able to clone the remote repos:

```

$ git clone username@git.example.com:/home/username/test.git

```

Git, in my opinion, is actually way easier (and faster) to set up and use 
via ssh than it is over http.  I, however, came from SVNland where it's the http integration is very, very good (and usually preferred) and really like the fact that the authorized users for my version control don't have to have a full on system account.

If the above isn't enough info, let me know and I'll see what I can do about helping you out.

Jay Deiman

---

