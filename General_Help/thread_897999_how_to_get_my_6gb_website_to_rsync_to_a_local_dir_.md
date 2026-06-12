---
title: "how to get my 6gb website to rsync to a local dir on my ubuntu?"
date: 2008-08-22
forum: General Help
---

### Post by srossnz on 2008-08-22
Hi, I currently have my website rsyncing to rsync.net and this works great.  I figured there should be a way I can rsync it to my local machine as well but being a linux noob I am unsure how to do it.  I am guessing something to do with running ssh on my local machine, designating a folder to that, then issuing the rsync command to whatever dynamic ip my local machine has?  Thanks for any tips!

---

### Post by pytheas22 on 2008-08-22
What might make more sense (because of dynamic-IP issues etc.) is to run rsync from your local machine and tell it to grab files from your server, which presumably has a fixed IP.  You would need an ssh server running on your server; hopefully you can do this (if your server runs Ubuntu, you can install an ssh server with "sudo apt-get install ssh").  After that, just issue a command on your local machine like:
```

rsync -av username@server-ip:remote/dirs/to/backup /location/of/backup/on/local/machine
```

If you can't run an ssh server on your server, you could do it the other way, as you suggest.  In that case, you'd need to install an ssh server on your Ubuntu machine, and then issue a command like this from your server:
```

rsync -av /dirs/to/transfer/on/server username@ip-of-desktop-machine:/path/to/backup/dir/on/desktop
```

If you did that and your Ubuntu desktop is behind a router/firewall, you'd need to make sure that ssh ports are forwarded correctly.

Hope it helps.

---

### Post by srossnz on 2008-08-22
> **pytheas22 said:**
> What might make more sense (because of dynamic-IP issues etc.) is to run rsync from your local machine and tell it to grab files from your server, which presumably has a fixed IP.  You would need an ssh server running on your server; hopefully you can do this (if your server runs Ubuntu, you can install an ssh server with "sudo apt-get install ssh").  After that, just issue a command on your local machine like:
```

rsync -av username@server-ip:remote/dirs/to/backup /location/of/backup/on/local/machine
```

If you can't run an ssh server on your server, you could do it the other way, as you suggest.  In that case, you'd need to install an ssh server on your Ubuntu machine, and then issue a command like this from your server:
```

rsync -av /dirs/to/transfer/on/server username@ip-of-desktop-machine:/path/to/backup/dir/on/desktop
```

If you did that and your Ubuntu desktop is behind a router/firewall, you'd need to make sure that ssh ports are forwarded correctly.

Hope it helps.

That gives me a lot to go on, thanks :)

I guess my server is running ssh since I can ssh to it?

---

### Post by pytheas22 on 2008-08-23
> I guess my server is running ssh since I can ssh to it?

Yeah, that would be indicative of an ssh server :)  Most lower-end hosting companies don't offer ssh access, though, so I wanted to make sure yours does.

---

### Post by srossnz on 2008-08-23
pulling down my site now via your command above (7+gigs), it's working like a charm.  Almost seems too good to be true so easily cloning and keep my data in sync.  Very cool :)

---

### Post by pytheas22 on 2008-08-23
> pulling down my site now via your command above (7+gigs), it's working like a charm. Almost seems too good to be true so easily cloning and keep my data in sync. Very cool 

Yeah, rsync is an amazing thing.

---

### Post by srossnz on 2008-08-23
Is it fairly solid?  I mean should I re-do a full rsync every now and then?  Can it become out of whack over time?  Thanks

---

### Post by pytheas22 on 2008-08-23
> Is it fairly solid? I mean should I re-do a full rsync every now and then? Can it become out of whack over time? Thanks

rsync should be very solid; it does a good job of checking and double-checking to make sure that the file transfers are successful and uncorrupted.

In terms of running it again: you should understand that one of the greatest features of rsync is that it only copies what's different between two directories...so any files that have already been transferred between your server and Ubuntu machine won't be needlessly recopied.  Because of that, you could run rsync every day or hour if you wanted and it would keep your local backup completely in sync with your server, and you won't have to worry about wasting bandwidth or disk space.  If you run rysnc a second time, it should go very quickly unless a lot of things on your server have changed.

---

