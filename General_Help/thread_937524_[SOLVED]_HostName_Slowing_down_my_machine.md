---
title: "[SOLVED] HostName Slowing down my machine"
date: 2008-10-03
forum: General Help
---

### Post by weasello on 2008-10-03
Hi everyone,

Longtime fan, first time installer.

I know just enough about computers to be dangerous. I had to setup a hostname to get my laptop to work in the office at one point, but I've long since not required it. When using my laptop from home now, before any SUDO command (which is a lot of them) I get "Could not find host" after about a 20 second delay.

As you can imagine this significantly slows down my boot up, shut down, and any terminal window time.

I try erasing the hostname out of my network properties, but when I close the window and reopen it it's still there (even if I hit the save icon). I can rename it though, and that sticks. I renamed it to "localhost" which seems to have resolved the problem...

Surely localhost isn't the default though, is it? Should I be on a domain instead? What's a good default for a random no-security network?

---

### Post by cariboo on 2008-10-04
What does your /etc/hosts file look like? In a terminal type:

```
cat /etc/hosts
```

and post the output in your next post. Hostname is the name of your computer, if you don't know what he host name is in a terminal type:

```
hostname
```

If there is a problem with your /etc/hosts file it could lead to problems logging and using sudo.

Jim

---

### Post by weasello on 2008-10-04
```
127.0.0.1 localhost
127.0.1.1 weasel-laptop.Company.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Hostname is:
```
localhost
```

---

### Post by jerome1232 on 2008-10-04
edit: You posted while I was typing this, and that was what I was talking about

Sounds to me what was happening is the computers hostname had an incorrect entry in your /etc/hosts file. When you named the computer localhost, well that just happens to be in that file by default and will get rid of the error message.

Usually you just name your computer whatever the heck it is you want.

If you'd like to change your hostname again you could do it like this:

```
gksudo gedit /etc/hostname, change what's in here to some name
gksudo gedit /etc/hosts, edit the line that says 127.0.1.1 somenamehere to match the new name you put in /etc/hostname.
```

logout then logback in and everything should be happy again

---

### Post by weasello on 2008-10-04
Perfect, that did the trick! thanks so much.

---

