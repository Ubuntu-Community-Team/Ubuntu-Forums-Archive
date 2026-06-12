---
title: "connect to file server"
date: 2008-10-15
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-10-15
To say it up front, I'm not a network expert but I can make my way through when I know what I need to do.
So here is my question / problem.

I have a Linux server here in the office and want to connect to it (mainly from Macs) for file sharing. I know that I would need Samba when I come with a Windows PC. But do I need to install/configure something to get a Mac connected? After all they're somewhat based on *nix.

If, then, I have the (theoretical) capability to connect it all, how can I make a shortcut in Finder on the Macs to easily connect to the server? Right now in Finder I can see other Macs but not the server. It would be cool to have just an easy shortcut to the network share.
Connecting from a Linux Desktop should be rather easy to setup, I believe.

Thanks for any advise.

Cheers.

---

### Post by jerome1232 on 2008-10-16
I'm not familiar with macs so I'm going off a google for this.

I like to use scp (ssh) for transferring files, it's out of the box secure and every os seems to have nice gui's for it. A quick google search showed me this client for mac, it's called fugu.

[http://rsug.itd.umich.edu/software/fugu/](http://rsug.itd.umich.edu/software/fugu/)
screenshots of it in action.
[http://rsug.itd.umich.edu/software/fugu/screens.html](http://rsug.itd.umich.edu/software/fugu/screens.html)

another client was cyber duck, they both work for ftp as well as sftp and scp.
[http://cyberduck.ch/](http://cyberduck.ch/)

On the Linux (I'm assuming a debian based distro) box all you have to do is:
```
sudo apt-get install openssh-server
```

Another option is ftp/sftp (more dificult to configure *securely*) or using apache to serve up files.

---

### Post by Linux&amp;Gsus on 2008-10-16
Hi Jerome,
thank you very much. That definitely is the right direction. Secure file transfer is of course preferred. I actually also thought about FTP. However, my concern is that the folks here are not necessarily the most computer savvy people. So, I would like to try to avoid introducing a new program with a somewhat unfamiliar interface, if anyhow possible.

I remember, from back in the day, on Windows I could add a network share to the Windows Explorer. I was hoping for something like that on Mac with using Finder. Then one could log on like connecting directly to another computers shared files.
Not that I don't have faith in people. But I have some around me who refer to "that blue cable" (all our network cables happen to be blue) as the internet.

Anyways, I bookmarked that website you posted in case it's not going to work out like I was hoping to.

Thanks again.
Cheers.

---

