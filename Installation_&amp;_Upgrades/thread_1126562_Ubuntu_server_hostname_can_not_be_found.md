---
title: "Ubuntu server hostname can not be found"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Malcrow on 2009-04-15
I installed server to learn command line linux for a new job I just started. And all their servers are run from command line.

So I figured I would start with what I think is probably an easy problem and move from there.

I set up 8.10 server a few weeks ago.
It was working great for a few days but now I can only access the machine from the ip.

My d-link router always seems to find the name.

When I try to ssh into the box using the machine name it says unable to open connection.

If I type hostname I get the right name.

Please help
Malcrow

---

### Post by mckenna1977 on 2009-04-15
using the ip address and you can always connect/contact. if you want to use the name to connect from other machines you need to register the machine name with those machines. if using windows register the name and ip in dns to enable name resolution from the network.

if not registering in dns but just on a windows pc register ip and name in the windows hosts file (c:\windows\system32\drivers\etc\hosts)

machine_name    ip_address

if from another linux machine you've the name already in the hostname file

also register this and other hosts whose names you need to resolve in the hosts file (/etc/hosts)

---

### Post by MaindotC on 2009-04-15
You can just log into the d-link router and see the list of attached devices.  The hostname (as the d-link reads it) will appear here.  It's probably different than what you are typing.

---

### Post by Malcrow on 2009-04-20
Thanks for the replies!

I am a newbie at this but I found the problem.

I had Shorewall installed and removed it or so I thought.  I recently relocated the server and when shut it down I noticed it saying shutting down shorewall.

I went back to my notes and this time I used the autoremove command.  After that everything came up working like it used to.

My server doesn't need to be out on the web anyways.  So since it is behind my router with no forwarded ports I think it is safe to not have the firewall

---

