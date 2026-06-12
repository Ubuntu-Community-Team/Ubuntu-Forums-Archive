---
title: "Best way to upload files to server over the net?"
date: 2008-11-17
forum: General Help
---

### Post by falconed7 on 2008-11-17
Hey everyone. I'm currently planning my home file server and am new to ubuntu server edition.

I am wondering what is the best way to upload files (mainly photos) onto my server via the internet (browser). As this would be very handy as I'm going overseas soon. Would this be done by apache?

I know about webmin but as far as I know that it's just the administration of the server.

Any help would be great!

---

### Post by baeksu on 2008-11-17
If you also want to have a photo gallery, the most popular would be, oddly enough [gallery](http://gallery.menalto.com/). It supports several upload methods, including browser based, webdav, and ftp. [(Ubuntu package)](http://packages.ubuntu.com/intrepid/gallery)

Other way to upload and show your photos would be to set up a blog, like wordpress or simplephpblog.

If you just want to upload files using your browser and apache, there are several php-based file managers out there. Have a look at [sourceforge](http://sourceforge.net/search/?type_of_search=soft&words=php+file+manager) for a few.

---

### Post by falconed7 on 2008-11-17
> **baeksu said:**
> If you also want to have a photo gallery, the most popular would be, oddly enough [gallery](http://gallery.menalto.com/). It supports several upload methods, including browser based, webdav, and ftp. [(Ubuntu package)](http://packages.ubuntu.com/intrepid/gallery)

Other way to upload and show your photos would be to set up a blog, like wordpress or simplephpblog.

If you just want to upload files using your browser and apache, there are several php-based file managers out there. Have a look at [sourceforge](http://sourceforge.net/search/?type_of_search=soft&words=php+file+manager) for a few.

Thanks for that I'll definitely check those out.

I don't really need a gallery so I think the PHP way would be the best as I would probably also upload files from uni as well. Also am I right in assuming I can also download something from my server if I need it remotely using the PHP based method?

---

### Post by porchrat on 2008-11-17
why not use OpenSSH?  Easy to use and it is encrypted.

OpenSSH client should already be installed, I'm not sure if the server is pre-installed, but if not you can get it off the repositories.

It can be setup to use either password authentication or key authentication.  It is much simpler than running an apache server.

---

### Post by geirha on 2008-11-17
+1 for openssh. Install [apt://openssh-server](apt://openssh-server) on the server, then on the client, go to Places -> Connect to Server. Choose ssh as server type, then fill in the correct values for host and username.

---

### Post by falconed7 on 2008-11-17
Thanks guys.

So OpenSSH is the way to go. Just to clarify would this work outside of my home network and could I use dyndns instead of writing in my IP adress as I have a dynamic IP?

---

### Post by geirha on 2008-11-17
Yes, that's what I use whenever I need to upload/download things to my server which have a dyndns name. You can also connect to your server from the terminal and run commands on the server. For example, if you want to install updates on the server from another machine:
```

ssh username@myserver.dyndns.org
# Asks for your password, and then gives you a shell on the server
sudo aptitude update && sudo aptitude safe-upgrade

```

EDIT: Oh, wait. If your server is behind a NAT/router, you'll need to forward the ssh port of course. The port is 22 by default. [http://portforward.com](http://portforward.com) can help you with that.

---

### Post by porchrat on 2008-11-17
you can also add "User " followed by your username you will be using to login then you don't even have to specify a username everytime.  If you really want to keep it secure then use a public and private key system.

You can generate a RSA key using this command on the client machine:

```
ssh keygen
```

You then use the "ssh-copy-id" command to move the pubic key over to the server machines /home/ssh-client-user/.ssh/authorized_keys file.  The command sorts everything out for you, it adds the public key and sets all the permissions.  It is really easy and is more secure than a password authentication system.

use "man ssh-copy-id" to see the usage for that command.

---

