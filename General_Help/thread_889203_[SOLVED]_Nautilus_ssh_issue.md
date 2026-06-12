---
title: "[SOLVED] Nautilus ssh issue"
date: 2008-08-13
forum: General Help
---

### Post by jambroo on 2008-08-13
The error read:
> Couldn't display "sftp://user@hostname/public_html/path".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

I have seen other posts on this issue- like this [one]("http://ubuntuforums.org/showthread.php?t=99343") - which people suggest to delete ~/.ssh/known_hosts and files in ~/.nautilus/metafiles then log out and log in.

This does fix it - but I can't be constantly logging in and out when i'm at work.

It usually disconnect/times out when I leave the nautilus window open for a period of time. I often need to work straight off the web server so it would be ideal to be able to stay open for long periods of time.

I tried to open it and get a file then close it and work on the file then save it to the webserver - but even doing that doesn't fix the issue.

The server was added using 'Places' > 'Connect to Server...'. When I open it in nautilus the Location bar reads: 'sftp://username@serveraddress/path'.

I have tried using IP addresses and putting the server name in my hosts file - to prevent DNS issues - but with no avail. ssh works fine using the terminal - but the seemless ssh connections was what attracted me to linux in the first place. In older versions (im not sure which one) I could stay connected to an ftp in nautilus for a full day - editing files directly off the web server.

Thanks in advance.

-Jamie

---

### Post by jambroo on 2008-08-14
I believe I have fixed the problem by editing /etc/ssh/ssh_conf and putting
```
TCPKeepAlive yes
ServerAliveInterval 120
Protocol 2,1
```
at the bottom of it (with help from "man ssh_config").

I don't know why this problem only started happening recently - but you'd think it would send keep alive packets out by default.

-Jamie

---

### Post by Russianspi on 2008-11-19
Thanks!

---

### Post by phelge on 2009-05-02
I had exactly the same issue with Nautilus in Jaunty and your suggestion fixed the problem.Thank you very much.

---

### Post by Primefalcon on 2010-09-25
I know old topic but I have recently been having issues myself with this since I work for long periods of time, and working natively if you like from a nautilus shell without being forced to use filezilla, to upload/download all the time really is useful....

And having a default short timeout is kinda a pain.

Anyhow I just wanted to say thank you too jambroo

---

