---
title: "[SOLVED] SSH pwd changed???"
date: 2008-10-24
forum: General Help
---

### Post by SiHa on 2008-10-24
I've probably done something stupid, but I''ll be buggered if I know what it is.

I have a Mythtv remote Backend / frontend in my loft, and a frontend in the lounge. Neither has a keyboard or mouse attached.

I generally do any maintenance etc. remotely from the main desktop PC via VNC / SSH.

Now VNC is fine, but as of last week, if I try and launch an SSH session to the backend:
```
ssh backend@192.168.1.152
```
My password is refused, and after three attempts the session chucks me out.

I'm a simple guy, so I the same password for **everything**. The pwd for VNC and SSH were originally the same, but it looks like my SSH password has become corrupted somehow. 
It's not a killer, but sometimes it's useful to be able to open a Terminal without disturbing the desktop (like when my wife is watching TV!). 

Can anyone tell me how I can change my SSH pwd back please?

---

### Post by Pro-reason on 2008-10-24
An ssh password is the same as a normal log-in password.

---

### Post by SiHa on 2008-10-24
Thanks - yes, it was....

But now it's not. And that's what's confusing me..?

Previously I was connecting an SSH session using the login pwd for that machine, but now it's being refused.

Would re-installing SSH fix things perhaps?

---

### Post by matey3 on 2008-10-24
try ssh -lusername then ip address.
also upon applying updates I cant log in as root onto remote machines any more!
I use the other login (ie localadmin) and then when i get in i do su.

---

### Post by Dr Small on 2008-10-24
pwd != password
Try typing "pwd" in the terminal sometime ;)

Ok, on subject.
You didn't happen to make a new account on the client machine, did you? If so, (and you are logged in as the different user on the client machine) then you need to specifiy the "username" of the account on the SSH server you are attempting to login to. Example:
```
ssh user2@host
```

I have found that I will be on my sister's computer sometimes logged in as her, then attempt to ssh to my server, and get the same type of response. The problem is, I am logged in as *her*, so it is trying to login as her on the server end.

Here's a quick way to tell, just by checking your prompt:
```
user1@hostname:~$ ssh user2@host
```

Some more questions.
Did you happen to setup SSH keys? Is this system directly connected to the internet? Is root enabled? Is there any other users on the system that you could try to SSH to?

---

### Post by SiHa on 2008-10-24
pwd = Print Working Directory. Hmm, yes. Sorry - don't use that one often, and to be honest, I still think in DOS half the time. I even typed 'cd\' the other day...

Anyway back to the matter at hand. DrSmall, Matey3, thank you both for your answers but I've fixed the problem.

The problem was that I was being an @rse - I'll explain.

When I set the remote system up, I called it, for want of a better name 'Mythbox' because that's what it is. Now when I use Vinagre to remote access the desktop, I called the bookmarks for the two machines 'backend' and 'frontend', so I've been trying to access```
backend@192.168.1.152
``` when it should be```
mythbox@192.168.1.152
```.

It all came flooding back to me five minutes ago...

I'll get my coat.

---

