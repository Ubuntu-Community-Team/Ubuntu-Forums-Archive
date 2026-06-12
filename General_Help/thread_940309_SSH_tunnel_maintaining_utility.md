---
title: "SSH tunnel maintaining utility"
date: 2008-10-06
forum: General Help
---

### Post by Régis B. on 2008-10-06
Hi all,

Each morning when I boot my PC at work I setup an SSH tunnel that routes traffic from port 5555 through a server in a democratic country. Something like this:
```
ssh -D 5555 user@host
```
Then my FoxyProxy extension redirects HTTP traffic (including DNS requests) for certain whitelisted websites from port 80 to port 5555 and I get uncensored news from home.

My (admittedly small) problem is that the connection to my server gets frequently interrupted during the day and thus I have to re-login quite often. I wonder if there is a utility/program/daemon that could
[LIST=3]
[*]establish the connection when I boot 
[*]check periodically the connection for interruptions
[*]Reconnect when necessary
[/LIST]

Thanks

---

### Post by strider1551 on 2008-10-08
> I wonder if there is a utility/program/daemon that could

   1. establish the connection when I boot
   2. check periodically the connection for interruptions
   3. Reconnect when necessary


I don't think you need that complex of a solution.  Have you tried [editing the config file]("https://help.ubuntu.com/community/SSHHowto#Tip:%20Keep%20Alive") to keep ssh sessions alive?  Edit /etc/ssh/ssh_config and modify/add the following lines.

```

ServerAliveInterval 120

```

[I gather]("http://madphilosopher.ca/2005/07/an-ssh-keep-alive-tip/#comment-106") that the same thing may be possible from the server end by modifying /etc/ssh/sshd_config.

```

KeepAlive yes
ClientAliveInterval 120

```

---

### Post by Régis B. on 2008-10-08
Hi strider1551, thanks for your answer,
In practice I wonder if there is a difference between your solution and the use of [autossh]("http://www.digipedia.pl/man/autossh.1.html") instead of ssh?

---

### Post by strider1551 on 2008-10-08
Interesting.  Gut instinct says there must be a difference, or else there would be little point in maintaining autossh.

I did some research and came up with [an article]("http://www.linux.com/feature/134133") from linux.com.
> Some readers will be familiar with the TCPKeepAlive, ServerAliveInterval, and ServerAliveCountMax options to SSH itself. TCPKeepAlive causes TCP keepalive messages to be sent to the server, allowing SSH to detect if it can no longer contact the server. ServerAliveCountMax and ServerAliveInterval cause the SSH client to send traffic through the encrypted link to the server, and can be used both the avoid a connection being closed due to inactivity and to have the SSH client exit if traffic cannot be returned from the server for a specified amount of time. The default action if TCPKeepAlive messages are ignored or ServerAliveCountMax messages are not returned in time is for the SSH client to exit.

While you can disable TCPKeepAlive and ServerAliveInterval if you are using SSH for port forwarding, you will then not get messages informing you that the port forwarding is inactive due to the network or server being unresponsive. Using autossh to control your SSH client means you can turn on TCPKeepAlive and ServerAliveInterval so transmission failures are detected and have autossh attempt to reestablish your SSH connections automatically when this happens.

I think the gist of what Ben Martin is saying is that autossh will try to reconnect in the event of a disconnect, while TCPKeepAlive, ServerAliveInterval, and ServerAliveCountMax try to prevent the disconnection from happening in the first place.  So ideally, the best solution would be to use both: prevent a disconnect, and automatically reconnect if it happens.

Personally, I prefer making things less complex.  I would first try TCPKeepAlive, ServerAliveInterval, and ServerAliveCountMax and see if my problem is solved.  If not, then I would try using autossh as well.

---

